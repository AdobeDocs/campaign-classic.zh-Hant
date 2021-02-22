---
solution: Campaign Classic
product: campaign
title: 配置管線
description: 瞭解如何設定管線
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---


# 設定管線 {#configuring-pipeline}

驗證參數（如客戶ID、私密金鑰和驗證端點）是在實例配置檔案中配置的。
要處理的觸發器清單會以JSON格式的選項設定。
觸發程式可用於透過傳送電子郵件的促銷活動工作流程進行定位。 促銷活動已設定，讓同時具有觸發事件的客戶收到電子郵件。

>[!CAUTION]
>
>如果是混合部署，請確定管道是在中間實例上配置的。

## 必要條件 {#prerequisites}

在開始此配置之前，請檢查您使用的是：

* 最少20.3、20.2.4、19.1.8或Gold Standard 11
* Adobe Analytics Standard版本

您還需要：

* Adobe I/O專案驗證
* 有效的IMSOrgID,Experience Cloud客戶的識別碼，並新增Adobe Analytics
* a開發人員存取IMS組織
* 觸發器設定在Adobe Analytics中完成

## 驗證和配置檔案{#authentication-configuration}

驗證是必要的，因為管道是由Adobe Experience Cloud代管。
它使用一對公鑰和私鑰。 此程式與用戶／密碼功能相同，但更安全。
透過Adobe I/O專案的Marketing Cloud支援驗證。

## 步驟1:建立／更新Adobe I/O專案{#creating-adobe-io-project}

對於代管客戶，您可以建立客戶服務票證，以便透過Adobe I/O技術帳戶Token為「觸發器」整合啟用您的組織。

若為On Premise客戶，請參閱[為Adobe Experience Cloud觸發器設定Adobe I/O頁面](../../integrations/using/configuring-adobe-io.md)。 請注意，在將API新增至Adobe I/O憑證時，您必須選取&#x200B;**[!UICONTROL Adobe Analytics]**。

## 步驟2:配置NmsPipeline_Config管線選項{#configuring-nmspipeline}

一旦設定了驗證，管線將檢索事件。 它只會處理在Adobe Campaign中設定的觸發程式。 觸發器必須是從Adobe Analytics產生，並推送至管線，而管線僅會處理在Adobe Campaign中設定的觸發器。
也可以使用通配符配置該選項，以便捕獲所有觸發器（無論其名稱如何）。

1. 在Adobe Campaign中，存取&#x200B;**[!UICONTROL Explorer]**&#x200B;中&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;下的選項功能表。

1. 選擇&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;選項。

1. 在&#x200B;**[!UICONTROL Value (long text)]**&#x200B;欄位中，您可貼上下列JSON程式碼，指定兩個觸發器。 您必須確定移除注釋。

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

1. 您也可以選擇貼上下列會擷取所有觸發器的JSON程式碼。

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

### Consumer參數{#consumer-parameter}

管道的運作方式類似於供應商和消費者模型。 消息僅用於單個消費者：每個消費者都會收到自己的訊息。

**Consumer**&#x200B;參數將實例標識為其中一個使用者。 實例的標識將調用pipeline。 您可以用實例名稱來填充它，該名稱可在「客戶端控制台」的「監視」頁上找到。

流水線服務跟蹤每個消費者檢索的消息。 針對不同的例項使用不同的使用者，可讓您確定每個訊息都會傳送至每個例項。

### 管線選項建議{#pipeline-option-recommendation}

若要設定「管線」選項，您應遵循下列建議：

* 在&#x200B;**[!UICONTROL Triggers]**&#x200B;下新增或編輯觸發器，您不應編輯其餘的。
* 請確定JSON有效。 您可以使用JSON驗證器，例如請參閱此[website](http://jsonlint.com/)。
* &quot;name&quot;對應於觸發器ID。 萬用字元&quot;*&quot;會擷取所有觸發器。
* &quot;Consumer&quot;對應至呼叫例項或應用程式的名稱。
* 流水線還支援「別名」主題。
* 在進行更改後，應始終重新啟動流水線。

## 步驟3:可選配置{#step-optional}

您可以根據負載需求變更某些內部參數，但請務必先加以測試，再投入生產。

可在以下找到可選參數清單：

| 選項 | 說明 |
|:-:|:-:|
| appName（舊版） | 已在上傳公開金鑰的舊版誓言應用程式中註冊的OAuth應用程式的AppID。 如需詳細資訊，請參閱此[頁面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md.) |
| authGatewayEndpoint（舊版） | 取得閘道Token的URL。 預設值：```https://api.omniture.com``` |
| authPrivateKey（舊版） | 私密金鑰、Legacy Fond應用程式中上傳的公用部分、使用XtkKey選項加密的AES:```cryptString("PRIVATE_KEY")``` |
| disableAuth（舊版） | 停用驗證時，若未使用閘道Token進行連線，只有某些開發管道端點才會接受。 |
| discoverPipelineEndpoint | URL，以尋找要用於此租用戶的Pipeline Services端點。 預設值：```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | ```var/INSTANCE/pipelined.json.``` <br>內部狀態中兩個轉儲的內部狀態進程之間的期間也可在以下位置按需訪問：```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 禁用對PipelineServicesEndpoint的檢測以強制其 |
| monitorServerPort | 流水線進程將偵聽此埠，以在以下位置提供內部狀態進程：```http://INSTANCE:PORT/pipelined/status```。 <br>預設為7781 |
| pointerFlushMessageCount | 處理此數量的消息時，偏移將保存在資料庫中。 <br> 預設值為1000 |
| pointerFlushPeriodSec | 在此期間後，偏移將保存在資料庫中。 <br>預設值為5（秒） |
| processingJSThreads | 使用自訂JS連接器處理訊息的專用執行緒數。 <br> 預設值為4 |
| processingThreads | 使用內建代碼處理消息的專用線程數。 <br>預設值為4 |
| retryPeriodSec | 處理錯誤時，重試之間會延遲。 <br>預設值為30（秒） |
| retryValiditySec | 如果消息在此時段後未成功處理（重試次數過多），請捨棄該消息。 <br>預設值為300（秒） |

### 流水線進程自動啟動{#pipelined-process-autostart}

需要自動啟動流水線處理。

為此，請將配置檔案中的&lt; pipelineed >元素設定為autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### 流水線進程重啟{#pipelined-process-restart}

要使更改生效，需要重新啟動：

```
nlserver restart pipelined@instance
```

## 步驟4:驗證{#step-validation}

要驗證為置備設定的管線，請執行以下步驟：

* 確保[!DNL pipelined]進程正在運行。
* 檢查pipelined.log中的管線連接日誌。
* 驗證連接是否已收到ping。 代管客戶可從用戶端主控台使用監控。
