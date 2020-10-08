---
title: 設定 整合
seo-title: 設定 整合
description: 設定 整合
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1145'
ht-degree: 1%

---


# 觸發事件 {#events}

## 在JavaScript中處理事件 {#events-javascript}

### JavaScript檔案 {#file-js}

管線使用JavaScript函式來處理每個訊息。 此函式是用戶定義的。

它是在「JSConnector」 **[!UICONTROL NmsPipeline_Config]** 屬性下的選項中配置的。 每次收到事件時都會呼叫此javascript。 它由流程運 [!DNL pipelined] 行。

範例JS檔案為cus:triggers.js。

### JavaScript函式 {#function-js}

Javascript [!DNL pipelined] 必須以特定函式開頭。

每個事件都會呼叫此函式一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它應以

```
<undefined/>
```

編輯 [!DNL pipelined] JS後重新啟動。

### 觸發資料格式 {#trigger-format}

資料 [!DNL trigger] 會傳遞至JS函式。 它是XML格式。

* 屬 **[!UICONTROL @triggerId]** 性包含的名稱 [!DNL trigger]。
* JSON格 **式的** enrichments元素包含Analytics產生的資料，並附加至觸發器。
* **[!UICONTROL @offset]** 是訊息的「指針」。 它指示隊列中消息的順序。
* **[!UICONTROL @partitio]*n是佇列中訊息的容器。 偏移相對於分區。 <br>隊列中大約有15個分區。

範例:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 擴充資料格式 {#enrichment-format}

>[!NOTE]
>
>它是各種可能實作的特定範例。

內容是在Analytics中針對每個觸發器定義的。 它是JSON格式。
例如，在觸發器中，LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** 可以包含用於與促銷活動收件者協調的購物者ID。 它是字串格式。 <br>必須協調以尋找主要金鑰的購物者ID。

* **[!UICONTROL timeGMT]** 可包含Analytics端觸發器的時間。 其格式為UTC Epoc（自1970年1月1日起的秒數）。

範例:

```
{
 "analyticsHitSummary": {
 "dimensions": {
 "eVar01": {
 "type": "string",
 "data": ["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],
 "name": " eVar01",
 "source": "session summary"
 },
 "timeGMT": {
 "type": "int",
 "data": [1469164186, 1469164195],
 "name": "timeGMT",
 "source": "session summary"
 }
 },
 "products": {}
 }
 }
```

### 事件處理順序 {#order-events}

事件會依偏移順序一次處理一次。 每個線程處理 [!DNL pipelined] 不同的分區。

上次檢索的事件的「偏移」儲存在資料庫中。 因此，如果進程停止，則從最後一條消息重新啟動。 此資料儲存在內建模式xtk:pipelineOffset中。

此指針是每個實例和每個消費者的專用指針。 因此，當許多實例與不同的用戶訪問相同的管道時，它們會以相同的順序獲得所有消息。

管線選項的&quot;consumer&quot;參數可識別呼叫例項。

目前，無法針對不同的環境（如「測試」或「開發」）使用不同的佇列。

### 記錄和錯誤處理 {#logging-error-handling}

日誌(如logInfo())被定向到日 [!DNL pipelined] 志。 將logError()等錯誤寫入日 [!DNL pipelined] 志，並導致事件放入重試隊列。 檢查流水線日誌。
在選項中設定的持續時間內，會多次重試出錯的 [!DNL pipelined] 消息。

為了調試和監控，將完整的觸發器資料寫入觸發器表中。 它位於XML格式的「資料」欄位中。 或者，包含觸發器資料的logInfo()也有相同的用途。

### 剖析資料 {#data-parsing}

此範例JS程式碼會剖析eVar01在元素中。

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var shopper_id = ""
 if (xmlTrigger.enrichments.length() > 0)
 {
 if (xmlTrigger.enrichments.toString().match(/eVar01/) != undefined)
 {
 var enrichments = JSON.parse(xmlTrigger.enrichments.toString())
 shopper_id = enrichments.analyticsHitSummary.dimensions. eVar01.data[0]
 }
 }
 (…)
 }
```

剖析時請務必小心，以避免錯誤。
由於此程式碼用於所有觸發器，因此大部分資料不是必要項目。 因此，當不存在時，可以留空。

### 儲存觸發器 {#storing-triggers-js}

>[!NOTE]
>
>它是各種可能實作的特定範例。

此範例JS程式碼會將觸發器儲存至資料庫。

```
function processPipelineMessage(xmlTrigger)
 {
 (…)
 var event = 
 <pipelineEvent
 xtkschema = "cus:pipelineEvent"
 _operation = "insert"
 created = {timeNow}
 lastModified = {timeNow}
 triggerType = {triggerType}
 timeGMT = {timeGMT}
 shopper_id = {shopper_id}
 data = {xmlTrigger.toXMLString()}
 />
 xtk.session.Write(event)
 return <undef/>; 
 }
```

### 限制 {#constraints}

此程式碼的效能必須最佳化，因為它會以高頻率執行。 其他行銷活動可能會有負面影響。 尤其是當在Marketing伺服器上每小時處理超過100萬個觸發事件時。 或者，如果調諧不當。

此Javascript的內容有限。 並非API的所有函式都可用。 例如，getOption()或getCurrentdate()無法運作。

為了加快處理速度，將同時執行此指令碼的多個線程。 代碼必須是線程安全的。

## 儲存事件 {#store-events}

>[!NOTE]
>
>它是各種可能實作的特定範例。

### 管線事件架構 {#pipeline-event-schema}

事件儲存在資料庫表中。 行銷活動使用它來鎖定客戶，並使用觸發器讓電子郵件更豐富。
雖然每個觸發器可以有不同的資料結構，但所有觸發器都可以放在單一表格中。
triggerType欄位可識別資料觸發的來源。

下面是此表的示例方案代碼：

| 屬性 | 類型 | 標籤 | 說明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 長 | 主鍵 | 觸發器的內部主鍵。 |
| 資料 | 備忘錄 | 觸發資料 | 觸發器資料的完整內容，以XML格式。 用於除錯和稽核。 |
| triggerType | 字串50 | TriggerType | 觸發器的名稱。 識別客戶在網站上的行為。 |
| shopper_id | 字串32 | shopper_id | 購物者的內部識別碼。 由協調工作流設定。 若為零，則表示客戶在Campaign中未知。 |
| shopper_key | 長 | shopper_key | Analytics擷取的購物者外部識別碼。 |
| 已建立 | 日期時間 | 已建立 | 在促銷活動中建立事件的時間。 |
| lastModified | 日期時間 | 上次修改日期 | 上次在Adobe中修改事件的時間。 |
| timeGMT | 日期時間 | 時間戳記 | 事件在Analytics中產生的時間。 |

### 顯示事件 {#display-events}

事件可以根據事件模式以簡單表單顯示。

>[!NOTE]
>
>Pipeline Event節點未內建，需要新增，以及相關表單需要在Campaign中建立。 這些操作僅限專家用戶使用。 如需更多相關資訊，請參閱以下章節： [導覽階層](../../configuration/using/about-navigation-hierarchy.md) 和 [編輯表單](../../configuration/using/editing-forms.md)。

![](assets/triggers_7.png)

## 處理事件 {#processing-the-events}

### 協調工作流程 {#reconciliation-workflow}

協調是將客戶從Analytics匹配至促銷活動資料庫的程式。 例如，符合的准則可以是shopper_id。

基於效能原因，必須由工作流在批次模式下完成匹配。
頻率必須設定為15分鐘才能優化工作負載。 因此，Adobe Campaign中的事件接收與行銷工作流程的處理之間的延遲最長為15分鐘。

### JavaScript中的裝置協調選項 {#options-unit-reconciliation}

理論上，您可以在JavaScript中針對每個觸發器執行協調查詢。 它對效能的影響更大，並且提供更快的結果。 當需要反應性時，可以要求在特定使用情況下使用。

如果未在shopper_id上設定索引，就很難做到。 如果標準位於與行銷伺服器不同的單獨資料庫伺服器上，則會使用效能不佳的資料庫連結。

### 清除工作流程 {#purge-workflow}

觸發器會在一小時內處理，因此沒有理由長時間保存。 卷可以是每小時100萬個觸發器。 它解釋了清除工作流必須到位的原因。 清除會刪除所有超過三天且每天執行一次的觸發器。

### 促銷活動工作流程 {#campaign-workflow}

觸發促銷活動工作流程通常與已使用的其他循環促銷活動類似。
例如，它可以從對觸發器的查詢開始，在最後一天尋找特定事件。 該目標用來傳送電子郵件。 加密或資料可能來自觸發器。 Marketing可安全地使用它，因為它不需要設定。
