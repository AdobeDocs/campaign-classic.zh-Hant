---
solution: Campaign Classic
product: campaign
title: 設定事件
description: 瞭解如何設定自訂實作的事件
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 0%

---

# 配置自訂實施事件 {#events}

此配置的部分是自定義開發，需要以下各項：

* Adobe Campaign地區JSON、XML和Javascript剖析的使用知識。
* QueryDef和Writer API的使用知識。
* 使用私密金鑰進行加密和驗證的工作概念。

由於編輯Javascript程式碼需要技術技巧，因此若未適當瞭解，請勿嘗試。

## 在JavaScript {#events-javascript}中處理事件

### JavaScript檔案{#file-js}

管線使用JavaScript函式來處理每個訊息。 此函式是用戶定義的。

它是在&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;選項的&quot;JSConnector&quot;屬性下配置的。 每次收到事件時都會呼叫此javascript。 它由[!DNL pipelined]進程運行。

範例Javascript檔案為cus:triggers.js。

### JavaScript函式{#function-js}

[!DNL pipelined] Javascript必須以特定函式開頭。

每個事件都會呼叫此函式一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它應以

```
<undefined/>
```

編輯Javascript後，您應重新啟動[!DNL pipelined]。

### 觸發資料格式{#trigger-format}

[!DNL trigger]資料會以XML格式傳遞至JS函式。

* **[!UICONTROL @triggerId]**&#x200B;屬性包含[!DNL trigger]的名稱。
* JSON格式的&#x200B;**enrichments**&#x200B;元素包含由Adobe Analytics產生的資料，並附加至觸發器。
* **[!UICONTROL @offset]** 是訊息的「指針」。它指示隊列中消息的順序。
* **[!UICONTROL @partition]** 是隊列中消息的容器。偏移相對於分區。 <br>隊列中大約有15個分區。

範例:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 資料格式擴充{#enrichment-format}

>[!NOTE]
>
>它是各種可能實作的特定範例。

內容是以JSON格式定義，每個觸發器的Adobe Analytics。
例如，在觸發器中，LogoUpload_uploading_Visits:

* **[!UICONTROL eVar01]** 可以包含字串格式的購物者ID，用於與Adobe Campaign收件者協調。<br>必須協調以尋找主要金鑰的購物者ID。

* **[!UICONTROL timeGMT]** 可以以UTC Epoc格式包含Adobe Analytics側觸發器的時間（自UTC 01/01/1970以來的秒數）。

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

### 事件處理順序{#order-events}

事件會依偏移順序一次處理一次。 [!DNL pipelined]的每個線程處理不同的分區。

上次檢索的事件的「偏移」儲存在資料庫中。 因此，如果進程停止，則從最後一條消息重新啟動。 此資料儲存在內建模式xtk:pipelineOffset中。

此指針是每個實例和每個消費者的專用指針。 因此，當許多實例與不同的用戶訪問相同的管道時，它們會以相同的順序獲得所有消息。

管線選項的&#x200B;**consumer**&#x200B;參數標識調用實例。

目前，無法針對不同的環境（如「測試」或「開發」）使用不同的佇列。

### 記錄和錯誤處理{#logging-error-handling}

日誌(如logInfo())被定向到[!DNL pipelined]日誌。 將logError()等錯誤寫入[!DNL pipelined]日誌，並導致事件放入重試隊列。 在這種情況下，應檢查流水線日誌。
在[!DNL pipelined]選項中設定的持續時間內，錯誤消息會重試多次。

為了進行除錯和監控，完整的觸發器資料會寫入XML格式「資料」欄位中的觸發器表格。 或者，包含觸發器資料的logInfo()也有相同的用途。

### 剖析資料{#data-parsing}

此範例Javascript程式碼會剖析eVar01。

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

### 儲存觸發器{#storing-triggers-js}

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

### 約束{#constraints}

此程式碼的效能必須最佳，因為其執行頻率很高，而且可能會對其他行銷活動造成潛在的負面影響。 尤其是當在Marketing伺服器上每小時處理超過100萬個觸發事件，或未正確調整時。

此Javascript的內容有限。 並非API的所有函式都可用。 例如，getOption()或getCurrentdate()無法運作。

為了加快處理速度，將同時執行此指令碼的多個線程。 代碼必須是線程安全的。

## 儲存事件{#store-events}

>[!NOTE]
>
>它是各種可能實作的特定範例。

### 管線事件模式{#pipeline-event-schema}

事件儲存在資料庫表中。 行銷活動會使用它來鎖定客戶，並使用觸發器讓電子郵件更豐富。
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
| lastModified | 日期時間 | 上次修改日期 | 事件上次在Adobe中修改的時間。 |
| timeGMT | 日期時間 | 時間戳記 | 事件在Analytics中產生的時間。 |

### 顯示事件{#display-events}

事件可以根據事件模式以簡單表單顯示。

>[!NOTE]
>
>Pipeline Event節點未內建，需要新增，以及相關表單需要在Campaign中建立。 這些操作僅限專家用戶使用。 如需更多相關資訊，請參閱以下章節：[導覽階層](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。 和[編輯表單](../../configuration/using/editing-forms.md)。

![](assets/triggers_7.png)

## 處理事件{#processing-the-events}

### 協調工作流{#reconciliation-workflow}

協調是將Adobe Analytics的客戶匹配到Adobe Campaign資料庫的過程。 例如，符合的准則可以是shopper_id。

基於效能原因，必須由工作流在批次模式下完成匹配。
頻率必須設定為15分鐘才能優化工作負載。 因此，Adobe Campaign的事件接收與行銷工作流程處理之間的延遲最長為15分鐘。

### JavaScript {#options-unit-reconciliation}中設備協調的選項

可以在JavaScript中為每個觸發器運行協調查詢。 它對效能的影響更大，並且提供更快的結果。 當需要反應性時，可以要求在特定使用情況下使用。

如果未在shopper_id上設定索引，就很難實作。 如果標準位於與行銷伺服器不同的單獨資料庫伺服器上，則會使用效能不佳的資料庫連結。

### 清除工作流{#purge-workflow}

觸發器在一小時內處理。 卷可以是每小時100萬個觸發器。 它解釋了清除工作流必須到位的原因。 清除每天執行一次，並刪除所有超過三天的觸發器。

### 促銷活動工作流程{#campaign-workflow}

觸發促銷活動工作流程通常與已使用的其他循環促銷活動類似。
例如，它可以從對觸發器的查詢開始，在最後一天尋找特定事件。 該目標用來傳送電子郵件。 加密或資料可能來自觸發器。 Marketing可安全地使用它，因為它不需要設定。
