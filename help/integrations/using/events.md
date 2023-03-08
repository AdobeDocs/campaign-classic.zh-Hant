---
product: campaign
title: 設定事件
description: 了解如何為自訂實作設定事件
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '1198'
ht-degree: 2%

---

# 配置自訂實施事件 {#events}

![](../../assets/common.svg)

此設定的部分是自訂開發，需要下列項目：

* Adobe Campaign中JSON、XML和Javascript剖析的實用知識。
* QueryDef和Writer API的使用知識。
* 使用私密金鑰進行加密和驗證的實用概念。

由於編輯Javascript程式碼需要技術技能，因此若未適當了解，請勿嘗試。

## 在JavaScript中處理事件 {#events-javascript}

### JavaScript檔案 {#file-js}

管道使用JavaScript函式來處理每則訊息。 此函式由使用者定義。

它設定於 **[!UICONTROL NmsPipeline_Config]** 選項。 每次收到事件時，都會呼叫此JavaScript。 由 [!DNL pipelined] 程式。

範例Javascript檔案為cus:triggers.js。

### JavaScript 函數 {#function-js}

此 [!DNL pipelined] Javascript必須以特定函式開頭。

每個事件會呼叫此函式一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它應傳回為

```
<undefined/>
```

您應該重新啟動 [!DNL pipelined] 編輯Javascript後。

### 觸發資料格式 {#trigger-format}

此 [!DNL trigger] 資料會以XML格式傳遞至JS函式。

* 此 **[!UICONTROL @triggerId]** 屬性包含 [!DNL trigger].
* 此 **擴充** JSON格式的元素包含Adobe Analytics產生的資料，並附加至觸發器。
* **[!UICONTROL @offset]** 是訊息的「指標」。 它會指出佇列中的訊息順序。
* **[!UICONTROL @partition]** 是佇列中訊息的容器。 偏移相對於分區。 <br>隊列中約有15個分區。

範例:

```
<trigger offset="1500435" partition="4" triggerId="LogoUpload_1_Visits_from_specific_Channel_or_ppp">
 <enrichments>{"analyticsHitSummary":{"dimensions":{" eVar01":{"type":"string","data":["PI4INE1ETDF6UK35GO13X7HO2ITLJHVH"],"name":" eVar01","source":"session summary"}, "timeGMT":{"type":"int","data":[1469164186,1469164195],"name":"timeGMT","source":"session summary"}},"products":{}}}</enrichments>
 <aliases/>
 </trigger>
```

### 資料格式擴充 {#enrichment-format}

>[!NOTE]
>
>這是各種可能實施的特定範例。

每個觸發器的內容都會在Adobe Analytics中以JSON格式定義。
例如，在觸發器LogoUpload_uploading_Visits中：

* **[!UICONTROL eVar01]** 可包含字串格式的購物者ID，用於調解Adobe Campaign收件者。 <br>必須調解以尋找主要金鑰購物者ID。

* **[!UICONTROL timeGMT]** 可以包含Adobe Analytics端觸發時間（UTC Epoc格式）(自01/01/1970 UTC起的秒數)。

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

事件會依位移順序一次處理一次。 每個線程 [!DNL pipelined] 處理不同的分區。

上次擷取的事件的「位移」會儲存在資料庫中。 因此，如果進程停止，則從最後一條消息重新啟動。 此資料會儲存在內建結構xtk:pipelineOffset中。

此指標專供每個例項和每個消費者使用。 因此，當許多執行個體以不同的使用者存取相同的管道時，會以相同的順序取得所有訊息。

此 **消費者** pipeline選項的參數標識調用實例。

目前，無法為「測試」或「開發」等不同環境設定不同的佇列。

### 記錄和錯誤處理 {#logging-error-handling}

記錄(如logInfo())會導向至 [!DNL pipelined] 記錄檔。 將logError()等錯誤寫入 [!DNL pipelined] 記錄並將事件放入重試佇列中。 在這種情況下，您應檢查管道記錄。
錯誤訊息會在 [!DNL pipelined] 選項。

為了偵錯和監控目的，完整的觸發程式資料會以XML格式寫入「資料」欄位的觸發程式表格中。 或者，包含觸發程式資料的logInfo()也有相同的用途。

### 剖析資料 {#data-parsing}

此範例Javascript程式碼會剖析擴充功能中的eVar01。

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
由於此程式碼用於所有觸發器，因此不需要大部分資料。 因此，若不存在，則可保留空白。

### 儲存觸發器 {#storing-triggers-js}

>[!NOTE]
>
>這是各種可能實施的特定範例。

此範例JS程式碼會將觸發程式儲存至資料庫。

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

此程式碼的效能必須最佳，因為它會以高頻率執行，而且可能會對其他行銷活動造成潛在負面影響。 尤其是如果在行銷伺服器上每小時處理超過100萬個觸發事件，或未正確調整時。

此Javascript的內容有限。 並非所有API功能皆可使用。 例如，getOption()或getCurrentdate()無法運作。

為了加快處理速度，此指令碼的多個執行緒會同時執行。 程式碼必須是執行緒安全狀態。

## 儲存事件 {#store-events}

>[!NOTE]
>
>這是各種可能實施的特定範例。

### 管道事件結構 {#pipeline-event-schema}

事件儲存在資料庫表中。 行銷活動使用它來鎖定客戶，並使用觸發器擴充電子郵件。
雖然每個觸發器可以有不同的資料結構，但所有觸發器都可放在單一表格中。
triggerType欄位標識資料的觸發源。

下表為此表格的范常式式碼：

| 屬性 | 類型 | 標籤 | 說明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 長整數 | 主要金鑰 | 觸發器的內部主鍵。 |
| 資料 | 備忘錄 | 觸發資料 | XML格式的觸發資料的完整內容。 用於偵錯和稽核。 |
| triggerType | 字串50 | TriggerType | 觸發器的名稱。 識別客戶在網站上的行為。 |
| shopper_id | 字串32 | shopper_id | 購物者的內部識別碼。 由調解工作流程設定。 如果為零，表示客戶在Campaign中為未知。 |
| shopper_key | 長整數 | shopper_key | 由Analytics擷取的購物者外部識別碼。 |
| 已建立 | 日期時間 | 已建立 | 在Campaign中建立事件的時間。 |
| lastModified | 日期時間 | 上次修改時間 | 上次在Adobe中修改事件的時間。 |
| timeGMT | 日期時間 | 時間戳記 | 在Analytics中產生事件的時間。 |

### 顯示事件 {#display-events}

事件可根據事件結構以簡單的形式顯示。

>[!NOTE]
>
>管道事件節點未內建，需要新增，且需在Campaign中建立相關表單。 這些操作僅限專家用戶使用。 如需詳細資訊，請參閱下列章節： [導覽階層](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy). 和 [編輯表單](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## 處理事件 {#processing-the-events}

### 調解工作流程 {#reconciliation-workflow}

調解是將客戶從Adobe Analytics比對至Adobe Campaign資料庫的程式。 例如，比對的條件可以是shopper_id。

基於效能原因，必須使用工作流在批處理模式下完成匹配。
頻率必須設定為15分鐘才能優化工作負載。 因此，Adobe Campaign中的事件接收與行銷工作流程處理之間的延遲最多為15分鐘。

### JavaScript中的單元協調選項 {#options-unit-reconciliation}

可以在JavaScript中為每個觸發器執行調解查詢。 它對效能的影響更大，而且效果更快。 當需要再活動時，可能需要它。

如果未在shopper_id上設定索引，則實施可能會很困難。 如果條件位於與市場營銷伺服器不同的單獨的資料庫伺服器上，則它使用資料庫連結，這會導致效能不佳。

### 清除工作流 {#purge-workflow}

觸發器會在一小時內處理。 音量可以是每小時100萬個觸發器。 它說明了清除工作流程必須到位的原因。 清除每天執行一次，並刪除超過三天的所有觸發器。

### 行銷活動工作流程 {#campaign-workflow}

觸發促銷活動工作流程通常類似於已使用的其他循環促銷活動。
例如，它可以從觸發器上的查詢開始，在最後一天尋找特定事件。 該目標用於傳送電子郵件。 擴充功能或資料可能來自觸發器。 行銷可安全地使用，因為不需要設定。
