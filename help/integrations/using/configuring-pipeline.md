---
product: campaign
title: 配置管道
description: 瞭解如何配置管道
audience: integrations
content-type: reference
exl-id: 2d214c36-8429-4b2b-b1f5-fe2730581bba
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 2%

---

# 設定管線 {#configuring-pipeline}

![](../../assets/common.svg)

驗證參數（如客戶ID、私鑰和驗證終結點）在實例配置檔案中配置。
要處理的觸發器清單以JSON格式的選項配置。
觸發器用於由發送電子郵件的市場活動工作流進行瞄準。 設定市場活動，以便具有兩個觸發事件的客戶接收電子郵件。

## 必要條件 {#prerequisites}

在啟動此配置之前，請檢查您正在使用：

* 最少，以下Adobe Campaign構建之一：
   * 19.1.8.9039
   * 19.1.4.9032 — 金標11
   * 20.2.4.9187
   * 20.3.1
* Adobe Analytics Standard版本

您還需要：

* Adobe I/O項目身份驗證
* 有效的組織ID — 要查找組織ID，請參閱 [此頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}
* 開發人員訪問您的組織
* 觸發器配置在Adobe Analytics完成

## 驗證和配置檔案 {#authentication-configuration}

由於管道在Adobe Experience Cloud托管，因此需要身份驗證。
它使用一對公鑰和私鑰。 此進程與用戶/密碼具有相同的功能，但更安全。
通過Marketing Cloud項目支援Adobe I/O。

## 步驟1:建立/更新Adobe I/O項目 {#creating-adobe-io-project}

對於托管客戶，您可以建立客戶服務票證，以啟用您的組織，並使用Adobe I/O技術帳戶令牌進行觸發器整合。

對於現場客戶，請參閱 [為Adobe Experience Cloud Triggers配置Adobe I/O](../../integrations/using/configuring-adobe-io.md) 的子菜單。 請注意，您需要選擇 **[!UICONTROL Adobe Analytics]** 將API添加到Adobe I/O憑據。

## 步驟2:配置NmsPipeline_Config管線選項 {#configuring-nmspipeline}

一旦設定了驗證，管道將檢索事件。 它將僅處理在Adobe Campaign中配置的觸發器。 觸發器必須是從Adobe Analytics生成的，並被推入到管道，該管道將僅處理在Adobe Campaign配置的觸發器。
也可以使用通配符配置該選項，以捕獲所有觸發器，而不考慮其名稱。

1. 在Adobe Campaign，訪問 **[!UICONTROL Administration]** > **[!UICONTROL Platform]**  > **[!UICONTROL Options]** 的 **[!UICONTROL Explorer]**。

1. 選擇 **[!UICONTROL NmsPipeline_Config]** 的雙曲餘切值。

1. 在 **[!UICONTROL Value (long text)]** 欄位中，可以貼上以下JSON代碼，該代碼指定兩個觸發器。 您需要確保刪除注釋。

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

1. 您還可以選擇貼上以下捕獲所有觸發器的JSON代碼。

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

### Consumer參數 {#consumer-parameter}

管道的工作方式類似於供應商和消費者模型。 消息僅用於單個用戶：每個消費者都會得到自己的郵件副本。

的 **消費者** 參數將實例標識為這些使用者之一。 實例的標識將調用管道。 您可以使用實例名稱來填充它，該實例名稱可在客戶端控制台的「監視」頁上找到。

管道服務跟蹤每個使用者檢索到的消息。 對不同實例使用不同的使用者，可確保將每個消息發送到每個實例。

### 管道選項建議 {#pipeline-option-recommendation}

要配置「管線」(Pipeline)選項，您應遵循以下建議：

* 在下添加或編輯觸發器 **[!UICONTROL Triggers]**，則不應編輯其餘內容。
* 確保JSON有效。 可以使用JSON驗證程式，請參閱 [網站](https://jsonlint.com/) 例如。
* &quot;name&quot;對應於觸發器ID。 通配符「*」將捕獲所有觸發器。
* &quot;Consumer&quot;與調用實例或應用程式的名稱相對應。
* 流水線還支援「別名」主題。
* 在進行更改後，應始終重新啟動流水線。

## 第3步：可選配置 {#step-optional}

您可以根據負載要求更改一些內部參數，但是請確保在將它們投入生產之前對其進行test。

可以找到以下可選參數清單：

| Option | 說明 |
|:-:|:-:|
| appName（舊版） | 在上載公鑰的舊式宣誓應用程式中註冊的OAuth應用程式的AppID。 如需關於此項目的詳細資訊，請參閱此[頁面](https://www.adobe.io/authentication/auth-methods.html#!AdobeDocs/adobeio-auth/master/AuthenticationOverview/ServiceAccountIntegration.md) |
| authGatewayEndpoint（舊版） | 獲取網關令牌的URL。 預設: ```https://api.omniture.com``` |
| authPrivateKey（舊版） | 私鑰，在Legacy Oath應用程式中上傳的公共部件，AES使用XtkKey選項進行加密： ```cryptString("PRIVATE_KEY")``` |
| disableAuth（舊） | 禁用身份驗證，沒有網關令牌的連接將只被某些開發管道終結點接受。 |
| discoverPipelineEndpoint | 用於查找要用於此租戶的Pipeline Services終結點的URL。 預設: ```https://producer-pipeline-pnw.adobe.net``` |
| dumpStatePeriodSec | 中內部狀態進程的兩個轉儲之間的期間 ```var/INSTANCE/pipelined.json.``` <br> 內部狀態也可按需訪問： ```http://INSTANCE:7781/pipelined/status``` |
| forcedPipelineEndpoint | 禁用對PipelineServicesEndpoint的檢測以強制它 |
| monitorServerPort | 流水線進程將偵聽此埠，以便在此處提供內部狀態進程： ```http://INSTANCE:PORT/pipelined/status```。 <br>預設為7781 |
| 指針FlushMessageCount | 處理此數目的消息時，偏移將保存在資料庫中。 <br> 預設值為1000 |
| 指針FlushPeriodSec | 在此期間後，偏移將保存在資料庫中。 <br>預設值為5（秒） |
| 處理JSThreads | 使用自定義JS連接器處理消息的專用線程數。 <br> 預設值為4 |
| 處理線程 | 使用內置代碼處理消息的專用線程數。 <br>預設值為4 |
| retryPeriodSec | 處理錯誤時重試之間的延遲。 <br>預設值為30（秒） |
| retryValiditySec | 如果在此時間段後未成功處理該消息（重試次數過多），請放棄該消息。 <br>預設值為300（秒） |

### 流水線處理自動啟動 {#pipelined-process-autostart}

流水線處理需要自動啟動。

為此，將配置檔案中的&lt; pipelined >元素設定為autostart=&quot;true&quot;:

```
 <pipelined autoStart="true" ... "/>
```

### 流水線處理重啟 {#pipelined-process-restart}

要使更改生效，需要重新啟動：

```
nlserver restart pipelined@instance
```

## 第4步：驗證 {#step-validation}

要驗證管道設定以進行預配，請執行以下步驟：

* 確保 [!DNL pipelined] 進程正在運行。
* 檢查pipelined.log中的管道連接日誌。
* 驗證連接是否收到ping。 托管客戶可以從客戶端控制台使用監控。
