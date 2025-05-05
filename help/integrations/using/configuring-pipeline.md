---
product: campaign
title: 設定管道
description: 瞭解如何設定Campaign — 觸發器整合的管道
feature: Triggers
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 1%

---

# 設定管道 {#configuring-pipeline}

在執行個體設定檔案中設定驗證引數，例如，客戶ID、私密金鑰和驗證端點。

要處理的觸發程式清單是在JSON格式的選項中設定。

這些觸發程式由傳送電子郵件的行銷活動工作流程用於鎖定目標。 行銷活動的設定方式是讓具有兩個觸發事件的客戶收到電子郵件。

## 先決條件 {#prerequisites}

開始此設定前，請檢查您是否擁有：

* Adobe Developer專案
* 有效的組織ID — 若要尋找您的組織ID，請參閱[此頁面](https://experienceleague.adobe.com/zh-hant/docs/core-services/interface/administration/organizations#concept_EA8AEE5B02CF46ACBDAD6A8508646255){_blank}
* 開發人員對貴組織的存取權
* Adobe Analytics中的有效觸發器設定

由於管道託管於Adobe Experience Cloud，因此需要驗證。 它會透過Adobe Developer專案使用支援的驗證。

## 步驟1：建立/更新您的Adobe Developer專案 {#creating-adobe-io-project}

您必須使用用於觸發器整合的Adobe Developer帳戶權杖來啟用組織。

在[此頁面](../../integrations/using/oauth-technical-account.md)中瞭解如何建立您的Adobe技術帳戶。 請注意，將API新增至Adobe Developer認證時，您必須選取&#x200B;**[!UICONTROL Adobe Analytics]**。

## 步驟2：設定管道選項 {#configuring-nmspipeline}

設定驗證後，管道將擷取事件。 它只會處理在Adobe Campaign中設定的觸發程式。 觸發程式必須從Adobe Analytics產生，並推送至管道，而管道只會處理Adobe Campaign中設定的觸發程式。

也可以使用萬用字元來設定選項，以便擷取所有觸發程式（不論名稱為何）。

1. 在Adobe Campaign中，存取&#x200B;**[!UICONTROL Explorer]**&#x200B;中&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下的選項功能表。

1. 選取 **[!UICONTROL NmsPipeline_Config]** 選項。

1. 在&#x200B;**[!UICONTROL Value (long text)]**&#x200B;欄位中，您可以貼上下列JSON程式碼，這會指定兩個觸發程式。 請確定移除註解。

   ```json
   {
   "topics": [ // list of "topics" that the pipelined is listening to.
      {
           "name": "triggers", // Name of the first topic: triggers.
           "consumer": "customer_dev", // Name of the instance that listens.  This value can be found on the monitoring page of Adobe Campaign.
           "triggers": [ // Array of triggers.
               {
                   "name": "3e8a2ba7-fccc-49bb-bdac-33ee33cf02bf", // TriggerType ID from Analytics 
                   "jsConnector": "cus:triggers.js" // Javascript library holding the processing function.
               }, {
                   "name": "2da3fdff-13af-4c51-8ed0-05802a572e94", // Second TriggerType ID 
                   "jsConnector": "cus:triggers.js" // Can use the same JS for all.
               },
           ]
       }
   ]
   }
   ```

1. 您也可以選擇貼上會擷取所有觸發程式的下列JSON程式碼。

   ```json
   {
   "topics": [
     {
       "name": "triggers",
       "consumer":  "customer_dev",
       "triggers": [
         {
           "name": "*",
           "jsConnector": "cus:pipeline.js"
         }
       ]
     }
   ]
   }
   ```

### 設定Consumer引數 {#consumer-parameter}

管線的運作方式與供應商和消費者模型類似。 訊息僅供個別消費者使用：每位消費者各有專屬的訊息副本。

**Consumer**&#x200B;引數會將執行個體識別為這些使用者之一。 執行個體的身分將呼叫管道。 您可以在「從屬端主控台」的「監督」頁面中，找到執行處理名稱。

管道服務會追蹤每個取用者擷取的訊息。 針對不同的執行個體使用不同的消費者，可讓您確定每個訊息都傳送至每個執行個體。

### 管道選項建議 {#pipeline-option-recommendation}

若要設定管道選項，您應遵循下列建議：

* 在&#x200B;**[!UICONTROL Triggers]**&#x200B;下新增或編輯觸發程式。
* 請確定JSON有效。
* **Name**&#x200B;引數對應到觸發程式識別碼。 萬用字元「*」將接住所有觸發器。
* **Consumer**&#x200B;引數對應到呼叫執行個體或應用程式的名稱。
* `pipelined`處理程式也支援「別名」主題。
* 進行變更後，您應該一律重新啟動`pipelined`程式。

## （選用）步驟3：其他設定 {#step-optional}

您可以根據負載需求變更某些內部引數，但請務必在將引數套用至生產環境之前先測試這些引數。

選擇性引數清單為：

| 選項 | 說明 |
|:-:|:-:|
| appName（舊版） | 在上傳公開金鑰的舊版Oath應用程式中註冊的OAuth應用程式的AppID。 如需關於此項目的詳細資訊，請參閱此[頁面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint（舊版） | 取得閘道權杖的URL。 預設： ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | 私密金鑰、舊版Oath應用程式中上傳的公開部分、以XtkKey選項加密的AES： ```cryptString("PRIVATE_KEY")``` |
| disableAuth（舊版） | 停用驗證，只有某些開發管道端點接受沒有閘道權杖的連線。 |
| discoverPipelineEndpoint | 用於尋找要用於此租使用者的管道服務端點的URL。 預設： ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | 在```var/INSTANCE/pipelined.json.``` <br>中內部狀態處理序的兩個傾印之間的期間，也可以在此隨選存取內部狀態： ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 停用偵測PipelineServicesEndpoint以強制執行 |
| monitorServerPort | 管線處理序將在此連線埠上接聽，以提供內部狀態處理序： ```http://INSTANCE:PORT/pipelined/status```。 <br>預設為7781 |
| pointerFlushMessageCount | 處理此數量的訊息時，位移會儲存在資料庫中。 <br>預設為1000 |
| pointerFlushPeriodSec | 在此期間之後，位移會儲存在資料庫中。 <br>預設為5 （秒） |
| processingJSThreads | 使用自訂JS聯結器處理訊息的專用執行緒數量。 <br>預設為4 |
| processingThreads | 使用內建程式碼處理訊息的專用執行緒數目。 <br>預設為4 |
| retryPeriodSec | 發生處理錯誤時重試之間的延遲。 <br>預設為30 （秒） |
| retryValiditySec | 如果在此期間之後未成功處理訊息（重試次數過多），請捨棄訊息。 <br>預設為300 （秒） |

### 管線處理序自動啟動 {#pipelined-process-autostart}

`pipelined`處理序需要自動啟動。

為此，請將設定檔案中的`<`pipelined`>`元素設定為autostart=&quot;true&quot;：

```sql
 <pipelined autoStart="true" ... "/>
```

### 管線處理序重新啟動 {#pipelined-process-restart}

必須重新啟動變更才會生效：

```sql
nlserver restart pipelined@instance
```

## 步驟4：驗證 {#step-validation}

要驗證用於布建的管道設定，請執行以下步驟：

* 確定`pipelined`處理序正在執行。
* 檢查`pipelined.log`以取得管道連線記錄。
* 驗證連線以及是否收到Ping。 託管客戶可使用使用者端主控台中的監視。
