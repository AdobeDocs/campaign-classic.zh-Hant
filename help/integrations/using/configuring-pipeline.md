---
product: campaign
title: 設定管道
description: 瞭解如何設定管道
feature: Triggers
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '920'
ht-degree: 1%

---

# 設定管線 {#configuring-pipeline}



在執行個體設定檔案中設定驗證引數，例如，客戶ID、私密金鑰和驗證端點。
要處理的觸發程式清單是在JSON格式的選項中設定。
這些觸發程式由傳送電子郵件的行銷活動工作流程用於鎖定目標。 行銷活動的設定方式是讓具有兩個觸發事件的客戶收到電子郵件。

## 先決條件 {#prerequisites}

開始此設定前，請檢查您是否使用：

* 最少，會建置下列其中一個Adobe Campaign：
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1
* Adobe Analytics Standard版本

您還需要：

* Adobe I/O專案驗證
* 有效的組織ID — 若要尋找您的組織ID，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}
* 開發人員對貴組織的存取權
* 在Adobe Analytics中完成觸發器設定

## 驗證和組態檔 {#authentication-configuration}

由於管道託管於Adobe Experience Cloud，因此需要驗證。
它使用一對公開和私密金鑰。 此程式與使用者/密碼具有相同的功能，但較安全。
支援透過Adobe I/O專案進行Marketing Cloud的驗證。

## 步驟1：建立/更新Adobe I/O專案 {#creating-adobe-io-project}

對於託管客戶，您可以建立客戶服務票證，讓您的組織能夠為Triggers整合Adobe I/O技術帳戶權杖。

若為內部部署客戶，請參閱 [設定Adobe Experience Cloud Triggers的Adobe I/O](../../integrations/using/configuring-adobe-io.md) 頁面。 請注意，您需要選取 **[!UICONTROL Adobe Analytics]** 新增API至Adobe I/O認證時。

## 步驟2：設定NmsPipeline_Config管線選項 {#configuring-nmspipeline}

設定驗證後，管道將擷取事件。 它只會處理在Adobe Campaign中設定的觸發程式。 觸發程式必須從Adobe Analytics產生，並推送至管道，而管道只會處理Adobe Campaign中設定的觸發程式。
也可以使用萬用字元來設定選項，以便擷取所有觸發程式（不論名稱為何）。

1. 在Adobe Campaign中，存取 **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** 在 **[!UICONTROL Explorer]**.

1. 選取 **[!UICONTROL NmsPipeline_Config]** 選項。

1. 在 **[!UICONTROL Value (long text)]** 欄位貼上下列JSON程式碼，這會指定兩個觸發程式。 您必須確定移除註解。

   ```
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

   ```
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

### Consumer引數 {#consumer-parameter}

管線的運作方式與供應商和消費者模型類似。 訊息僅供個別消費者使用：每位消費者各有專屬的訊息副本。

此 **消費者** 引數會將執行個體識別為這些取用者之一。 執行個體的身分將呼叫管道。 您可以在「從屬端主控台」的「監督」頁面中，找到執行處理名稱。

管道服務會追蹤每個取用者擷取的訊息。 針對不同的執行個體使用不同的消費者，可讓您確定每個訊息都傳送至每個執行個體。

### 管道選項建議 {#pipeline-option-recommendation}

若要設定管道選項，您應遵循下列建議：

* 新增或編輯下的觸發程式 **[!UICONTROL Triggers]**，您不應該編輯其餘的。
* 請確定JSON有效。 您可以使用JSON驗證器，請參閱此 [網站](https://jsonlint.com/) 例如。
* &quot;name&quot;會對應至觸發程式ID。 萬用字元「*」將接住所有觸發器。
* 「消費者」對應到呼叫執行個體或應用程式的名稱。
* 管線也支援「別名」主題。
* 進行變更後，您應該一律重新啟動管線化。

## 步驟3：可選設定 {#step-optional}

您可以根據負載要求變更某些內部引數，但請務必在投入生產之前先測試這些引數。

您可在下方找到選用引數清單：

| 選項 | 說明 |
|:-:|:-:|
| appName（舊版） | 在上傳公開金鑰的舊版Oath應用程式中註冊的OAuth應用程式的AppID。 如需關於此項目的詳細資訊，請參閱此[頁面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint（舊版） | 取得閘道權杖的URL。 預設： ```https://api.omniture.com``` |
| authPrivateKey(Legacy) | 在舊版Oath應用程式中上傳的私密金鑰、公開部分，以XtkKey選項加密的AES： ```cryptString("PRIVATE_KEY")``` |
| disableAuth（舊版） | 停用驗證，只有某些開發管道端點接受沒有閘道權杖的連線。 |
| discoverPipelineEndpoint | 用於尋找要用於此租使用者的管道服務端點的URL。 預設： ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | 中的兩個內部狀態處理序傾印之間的期間 ```var/INSTANCE/pipelined.json.``` <br> 您也可以在這裡隨選存取內部狀態： ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 停用偵測PipelineServicesEndpoint以強制執行 |
| monitorServerPort | 管線處理將在此連線埠上接聽，以提供內部狀態處理： ```http://INSTANCE:PORT/pipelined/status```. <br>預設為7781 |
| pointerFlushMessageCount | 處理此數量的訊息時，位移會儲存在資料庫中。 <br> 預設為1000 |
| pointerFlushPeriodSec | 在此期間之後，位移會儲存在資料庫中。 <br>預設為5 （秒） |
| processingJSThreads | 使用自訂JS聯結器處理訊息的專用執行緒數量。 <br> 預設值為4 |
| processingThreads | 使用內建程式碼處理訊息的專用執行緒數目。 <br>預設值為4 |
| retryPeriodSec | 發生處理錯誤時重試之間的延遲。 <br>預設為30 （秒） |
| retryValiditySec | 如果在此期間之後未成功處理訊息（重試次數過多），請捨棄訊息。 <br>預設為300 （秒） |

### 管線處理序自動啟動 {#pipelined-process-autostart}

管線處理需要自動啟動。

為此，請將設定檔案中的&lt;pipelined >元素設定為autostart=&quot;true&quot;：

```
 <pipelined autoStart="true" ... "/>
```

### 管線處理序重新啟動 {#pipelined-process-restart}

必須重新啟動變更才會生效：

```
nlserver restart pipelined@instance
```

## 步驟4：驗證 {#step-validation}

要驗證用於布建的管道設定，請執行以下步驟：

* 確定 [!DNL pipelined] 處理序正在執行。
* 檢查pipelined.log以取得管道連線記錄。
* 驗證連線以及是否收到Ping。 託管客戶可使用使用者端主控台中的監視。
