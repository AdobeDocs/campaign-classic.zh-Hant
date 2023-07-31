---
product: campaign
title: 設定事件
description: 瞭解如何設定自訂實施的事件
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
exl-id: 13717b3b-d34a-40bc-9c9e-dcf578fc516e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1210'
ht-degree: 2%

---

# 配置自訂實施事件 {#events}



此設定的部分是自訂開發，需要以下專案：

* 在Adobe Campaign中掌握JSON、XML及Javascript剖析的實用知識。
* QueryDef和Writer API的實用知識。
* 使用私密金鑰進行加密和驗證的工作概念。

由於編輯Javascript程式碼需要技術技能，因此請勿在未經適當瞭解的情況下嘗試。

## 在JavaScript中處理事件 {#events-javascript}

### javascript檔案 {#file-js}

Pipeline會使用JavaScript函式來處理每則訊息。 此函式由使用者定義。

其設定於 **[!UICONTROL NmsPipeline_Config]** 選項（位於「JSConnector」屬性下）。 每次收到事件時都會呼叫此JavaScript。 執行者為 [!DNL pipelined] 程式。

範例Javascript檔案為cus：triggers.js。

### JavaScript 函數 {#function-js}

此 [!DNL pipelined] Javascript必須以特定函式開頭。

此函式會針對每個事件呼叫一次：

```
function processPipelineMessage(xmlTrigger) {}
```

它應該會傳回為

```
<undefined/>
```

您應該重新啟動 [!DNL pipelined] 編輯Javascript之後。

### 觸發資料格式 {#trigger-format}

此 [!DNL trigger] 資料會以XML格式傳遞至JS函式。

* 此 **[!UICONTROL @triggerId]** 屬性包含 [!DNL trigger].
* 此 **擴充功能** JSON格式的元素包含Adobe Analytics產生的資料，並附加至觸發器。
* **[!UICONTROL @offset]** 是訊息的「指標」。 其會指出佇列中訊息的順序。
* **[!UICONTROL @partition]** 是佇列中訊息的容器。 位移相對於分割區。 <br>佇列中有約15個分割區。

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
>這是各種可能實施作業中的特定範例。

對於每個觸發程式，內容會在Adobe Analytics中以JSON格式定義。
例如，在觸發器中LogoUpload_uploading_Visits：

* **[!UICONTROL eVar01]** 可包含字串格式的購物者ID，此ID可用來與Adobe Campaign收件者進行調解。 <br>必須對其進行調解才能找到購物者ID （主索引鍵）。

* **[!UICONTROL timeGMT]** 可在Adobe Analytics端包含UTC Epoch格式的觸發器時間（自01/01/1970 UTC以來的秒數）。

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

事件會依位移順序逐一處理。 每個對話串 [!DNL pipelined] 處理不同的資料分割。

擷取的最後一個事件的「offset」會儲存在資料庫中。 因此，如果流程停止，它會從最後一個訊息重新啟動。 此資料儲存在內建方案xtk：pipelineOffset中。

此指標是每個執行個體和每個取用者專屬的。 因此，當許多執行個體使用不同的消費者存取相同的管道時，他們每個人都會以相同的順序收到所有訊息。

此 **消費者** 配管選項的引數可識別呼叫的執行個體。

目前，對於不同的環境（例如「測試」或「開發」），無法擁有不同的佇列。

### 記錄與錯誤處理 {#logging-error-handling}

記錄檔(例如logInfo())會導向至 [!DNL pipelined] 記錄。 諸如logError()之類的錯誤會寫入 [!DNL pipelined] 記錄並將事件放入重試佇列中。 在此情況下，您應該檢查管線記錄。
錯誤的訊息會在中設定的期間內重試多次。 [!DNL pipelined] 選項。

為了偵錯和監控之目的，完整的觸發程式資料會以XML格式寫入「資料」欄位中的觸發程式表格中。 或者，包含觸發程式資料的logInfo()也可達到相同目的。

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

剖析時請小心，以免發生錯誤。
由於此程式碼用於所有觸發器，因此大部分資料並非必要。 因此，當不存在時，可以保留空白。

### 儲存觸發器 {#storing-triggers-js}

>[!NOTE]
>
>這是各種可能實施作業中的特定範例。

此JS程式碼範例將觸發器儲存至資料庫。

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

此程式碼的效能必須是最佳的，因為它會在高頻率執行，而且可能會對其他行銷活動造成潛在的負面影響。 特別是在行銷伺服器上每小時處理超過一百萬個觸發事件時，或是未正確調整時。

此Javascript的內容有限。 並非所有API函式都可使用。 例如，getOption()或getCurrentdate()無法運作。

為了啟用更快速的處理，此指令碼的多個執行緒會同時執行。 程式碼必須是執行緒安全。

## 儲存事件 {#store-events}

>[!NOTE]
>
>這是各種可能實施作業中的特定範例。

### 管道事件結構描述 {#pipeline-event-schema}

事件儲存在資料庫表格中。 行銷活動會使用它來鎖定客戶，並使用觸發器豐富電子郵件。
雖然每個觸發器可以有不同的資料結構，但所有觸發器都可儲存在單一表格中。
triggerType欄位會識別觸發資料來源的來源。

以下是此表格的結構描述程式碼範例：

| 屬性 | 類型 | 標籤 | 說明 |
|:-:|:-:|:-:|:-:|
| pipelineEventId | 長整數 | 主要金鑰 | 觸發器的內部主索引鍵。 |
| 資料 | 備忘錄 | 觸發資料 | 以XML格式觸發資料的完整內容。 用於偵錯和稽核目的。 |
| triggerType | 字串50 | TriggerType | 觸發器的名稱。 識別客戶在網站上的行為。 |
| shopper_id | 字串32 | shopper_id | 購物者的內部識別碼。 由調解工作流程設定。 如果為零，表示在Campaign中未知客戶。 |
| shopper_key | 長整數 | shopper_key | 購物者的外部識別碼，如Analytics所擷取。 |
| 已建立 | 日期時間 | 已建立 | 在Campaign中建立事件的時間。 |
| lastModified | 日期時間 | 上次修改時間 | 上次在Adobe中修改事件的時間。 |
| timeGMT | 日期時間 | 時間戳記 | 在Analytics中產生事件的時間。 |

### 顯示事件 {#display-events}

事件可以基於事件結構的簡單表單來顯示。

>[!NOTE]
>
>管道事件節點不是內建的，需要新增，並且需要在Campaign中建立相關表單。 這些操作僅限專家使用者執行。 如需詳細資訊，請參閱下列區段： [導覽階層](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy). 和 [編輯表單](../../configuration/using/editing-forms.md).

![](assets/triggers_7.png)

## 處理事件 {#processing-the-events}

### 調解工作流程 {#reconciliation-workflow}

調解是將客戶從Adobe Analytics對應到Adobe Campaign資料庫的程式。 例如，相符的標準可以是shopper_id。

基於效能考量，相符必須由工作流程以批次模式完成。
頻率必須設定為15分鐘以最佳化工作負載。 因此，在Adobe Campaign中接收事件與行銷工作流程處理事件之間的延遲最長為15分鐘。

### JavaScript中用於單元協調的選項 {#options-unit-reconciliation}

您可以在JavaScript中為每個觸發程式執行調解查詢。 效能影響更大，成果更快速。 在需要反應性的特定使用案例中，可能有此需要。

如果shopper_id上未設定索引，則可能很難實作。 如果條件位在與行銷伺服器不同的資料庫伺服器上，則會使用效能不佳的資料庫連結。

### 清除工作流程 {#purge-workflow}

觸發程式會在小時內處理。 音量大約為每小時100萬個觸發器。 它說明了必須建立清除工作流程的原因。 清除每天執行一次，並刪除所有超過三天的觸發器。

### 行銷活動工作流程 {#campaign-workflow}

觸發行銷活動工作流程通常與其他已使用的週期性行銷活動類似。
例如，它可以從對最後一天期間尋找特定事件的觸發器的查詢開始。 該目標用於傳送電子郵件。 擴充功能或資料可以來自觸發器。 行銷人員可以安全地使用它，因為它不需要設定。
