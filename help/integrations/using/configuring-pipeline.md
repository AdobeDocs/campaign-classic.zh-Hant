---
product: campaign
title: 設定管道
description: 了解如何設定管道
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 6a5253c1aa35e904635919f6c863930d376b473f
workflow-type: tm+mt
source-wordcount: '915'
ht-degree: 1%

---

# 設定管線 {#configuring-pipeline}

驗證參數（如客戶ID、私密金鑰和驗證端點）是在執行個體設定檔中設定。
要處理的觸發器清單會以JSON格式的選項設定。
觸發器用於傳送電子郵件的行銷活動工作流程鎖定目標。 已設定促銷活動，讓同時觸發事件的客戶收到電子郵件。

>[!CAUTION]
>
>若是混合部署，請確定管道是在中繼執行個體上設定。

## 先決條件 {#prerequisites}

開始此配置之前，請檢查您是否使用：

* 至少，下列其中一個Adobe Campaign組建：
   * 19.1.8.9039
   * 19.1.4.9032 - Gold Standard 11
   * 20.2.4.9187
   * 20.3.1
* Adobe Analytics Standard版本

您也需要：

* Adobe I/O專案驗證
* 有效的IMSOrgID，該ID是添加了Adobe Analytics的Experience Cloud客戶的標識符
* 開發人員存取IMS組織
* 觸發在Adobe Analytics完成的設定

## 驗證和配置檔案 {#authentication-configuration}

由於管道是在Adobe Experience Cloud中托管，因此需要驗證。
它使用一對公開和私密金鑰。 此程式的功能與使用者/密碼相同，但更安全。
Marketing Cloud支援透過Adobe I/O專案進行驗證。

## 步驟1:建立/更新Adobe I/O專案 {#creating-adobe-io-project}

對於托管客戶，您可以建立客戶服務票證，以透過Adobe I/O技術帳戶代號來啟用您的組織，以進行觸發器整合。

若為內部部署客戶，請參閱[為Adobe Experience Cloud Triggers](../../integrations/using/configuring-adobe-io.md)設定Adobe I/O頁面。 請注意，在將API新增至Adobe I/O憑證時，您需要選取&#x200B;**[!UICONTROL Adobe Analytics]**。

## 步驟2:配置NmsPipeline_Config管線選項 {#configuring-nmspipeline}

一旦設定驗證，管道將擷取事件。 它只會處理在Adobe Campaign中設定的觸發器。 觸發器必須從Adobe Analytics產生，並推送至管道，而管道只會處理Adobe Campaign中設定的觸發器。
選項也可以設定萬用字元，以便無論名稱為何都能擷取所有觸發器。

1. 在Adobe Campaign中，存取&#x200B;**[!UICONTROL Explorer]**&#x200B;中&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下的選項功能表。

1. 選擇&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;選項。

1. 在&#x200B;**[!UICONTROL Value (long text)]**&#x200B;欄位中，您可以貼上下列JSON程式碼，其中指定兩個觸發器。 您需要確保刪除注釋。

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

1. 您也可以選擇貼上下列JSON程式碼，以便擷取所有觸發器。

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

### 消費者參數 {#consumer-parameter}

管道的運作方式就像供應商和消費者模型。 訊息僅供個別消費者使用：每個消費者都有各自的訊息副本。

**Consumer**&#x200B;參數會將執行個體識別為其中一個使用者。 例項的身分會呼叫管道。 您可以填入執行個體名稱，該名稱可在用戶端主控台的「監控」頁面中找到。

管道服務可追蹤每個消費者擷取的訊息。 針對不同的例項使用不同的使用者，可讓您確定每個訊息都會傳送至每個例項。

### 管道選項建議 {#pipeline-option-recommendation}

若要設定管道選項，您應遵循下列建議：

* 在&#x200B;**[!UICONTROL Triggers]**&#x200B;下添加或編輯觸發器，您不應編輯其餘的。
* 確定JSON有效。 您可以使用JSON驗證器，例如，請參閱此[website](http://jsonlint.com/)。
* &quot;name&quot;對應至觸發器ID。 萬用字元「*」會擷取所有觸發器。
* 「消費者」對應至呼叫例項或應用程式的名稱。
* 管道也支援「別名」主題。
* 進行更改後，應始終重新啟動流水線。

## 步驟3:可選配置 {#step-optional}

您可以根據負載需求變更一些內部參數，但請務必先測試這些參數，再投入生產。

可從以下找到選用參數清單：

| 選項 | 說明 |
|:-:|:-:|
| appName（舊版） | 在上傳公開金鑰的舊版Oath應用程式中註冊的OAuth應用程式的AppID。 如需關於此項目的詳細資訊，請參閱此[頁面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint（舊版） | 取得閘道權杖的URL。 預設值：```https://api.omniture.com``` |
| authPrivateKey（舊版） | 私密金鑰（舊版Oath應用程式中上傳的公開部分）AES使用XtkKey選項加密：```cryptString("PRIVATE_KEY")``` |
| disableAuth（舊版） | 停用驗證，不使用閘道權杖進行連線只會被某些開發管道端點接受。 |
| discoverPipelineEndpoint | 尋找要用於此租用戶的Pipeline Services端點的URL。 預設值：```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | ```var/INSTANCE/pipelined.json.``` <br>中內部狀態進程的兩個轉儲之間的期間內，內部狀態也可按需訪問：```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 禁用PipelineServicesEndpoint的檢測以強制其 |
| monitorServerPort | 管道化進程將監聽此埠，以便在此處提供內部狀態進程：```http://INSTANCE:PORT/pipelined/status```。 <br>預設為7781 |
| pointerFlushMessageCount | 處理此數量的訊息時，位移會儲存在資料庫中。 <br> 預設為1000 |
| pointerFlushPeriodSec | 在此期間後，偏移將保存在資料庫中。 <br>預設為5（秒） |
| processingJSThreads | 使用自訂JS連接器處理訊息的專用執行緒數目。 <br> 預設為4 |
| processingThreads | 使用內建代碼處理消息的專用線程數。 <br>預設為4 |
| retryPeriodSec | 處理錯誤時重試之間的延遲。 <br>預設為30（秒） |
| retryValiditySec | 如果此時段後未成功處理訊息（重試次數太多），請捨棄訊息。 <br>預設為300（秒） |

### 流水線處理自動啟動 {#pipelined-process-autostart}

管道化進程需要自動啟動。

為此，將設定檔案中的&lt; pipelined >元素設為autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### 流水線處理重啟 {#pipelined-process-restart}

要使更改生效，需要重新啟動：

```
nlserver restart pipelined@instance
```

## 步驟4:驗證 {#step-validation}

要驗證用於布建的管道設定，請執行以下步驟：

* 確保[!DNL pipelined]進程正在運行。
* 檢查pipelined.log中是否有管線連線記錄。
* 驗證連線，以及是否收到Ping。 托管客戶可從用戶端主控台使用監控。
