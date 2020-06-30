---
title: 設定整合
seo-title: 設定整合
description: 設定整合
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 39d6da007d69f81da959660b24b56ba2558a97ba
workflow-type: tm+mt
source-wordcount: '650'
ht-degree: 0%

---


# 管道疑難排解 {#pipeline-troubleshooting}

**流水線失敗，錯誤為「沒有任務與掩碼流水線」**

您的Adobe Campaign Classic版本不支援管道。

1. 檢查配置檔案中是否存在流水線元素。 否則表示不支援。
1. 升級至版本6.11 build 8705或更高版本。

**Pipelined失敗，出現&quot;aurait duj commencer par &#39;[&#39; ou &#39;{&#39;(iRc=16384)&quot;**

未 **設定NmsPipeline_Config** 選項。 實際上是JSON剖析錯誤。
在選項 **NmsPipeline_Config中設定JSON設定**。 請參閱本頁的「路由選項」。

**流水線失敗，但「主題必須是有效的組織或客戶」**

IMSOrgid配置無效。

1. 檢查serverConf.xml中是否已設定IMSOrgId。
1. 在實例配置檔案中查找可以覆蓋預設值的空IMSOrgId。 如果是，請將其刪除。
1. 檢查IMSOrgId是否與Experience Cloud中的客戶相符。

**流水線失敗，密鑰無效**

實例配置檔案的@authPrivateKey參數不正確。

1. 檢查authPrivateKey是否已設定。
1. 檢查authPrivateKey: 開頭為@，結尾為=，長度約為4000個字元。
1. 尋找原始金鑰並檢查其是否為： 以RSA格式，長4096位，開頭為—BEGIN RSA PRIVATE KEY —。
   <br> 如有必要，請重新建立索引鍵並在Adobe Analytics中註冊。 請參閱本 [節](../../integrations/using/configuring-pipeline.md#oauth-client-creation)。
1. 檢查索引鍵是否編碼在與流水線相同的例項中。 <br>如有必要，請使用範例JavaScript或工作流程重做編碼。

**流水線失敗，「在驗證期間無法讀取代號」**

私密金鑰的格式無效。

1. 在此頁上運行密鑰加密的步驟。
1. 檢查該密鑰是否在同一實例上加密。
1. 檢查設定檔案中的authPrivateKey是否與產生的金鑰相符。 <br>請確定使用OpenSSL產生金鑰對。 例如，PuttyGen不會產生正確的格式。

**未擷取任何觸發器**

當流水線處理正在運行且未檢索任何觸發器時：

1. 請確定觸發器在Analytics中處於作用中，且正在產生事件。
1. 請確定流水線進程正在運行。
1. 在流水線日誌中查找錯誤。
1. 在流水線狀態頁面中查找錯誤。 觸發器丟棄，觸發器故障應為零。
1. 檢查在選項中是否配置了觸發器 **[!UICONTROL NmsPipeline_Config]** 名稱。 如果有疑問，請使用通配符選項。
1. 檢查Analytics是否有作用中的觸發器，且正在產生事件。 在Analytics中進行設定後，可能會延遲數小時，才會啟動。

**事件未連結至客戶**

當某些事件未連結至客戶時：

1. 檢查協調工作流是否正在運行（如果適用）。
1. 檢查事件是否包含客戶ID。
1. 使用客戶ID對客戶表進行查詢。
1. 檢查客戶匯入的頻率。 新客戶會透過工作流程匯入Adobe Campaign。

**事件處理中的延遲**

當Analytics時間戳記比促銷活動中事件的建立日期早得多時。

一般而言，觸發器可能需要15-90分鐘才能啟動行銷促銷活動。 這視資料收集的實作、在管線上載入、定義觸發器的自訂設定，以及Adobe Campaign中的工作流程而定。

1. 檢查流水線進程是否已運行。
1. 在pipelined.log中查找可能導致重試的錯誤。 修正錯誤（如果適用）。
1. 檢查隊列大小的流水線狀態頁。 如果佇列大小較大，請改善JS的效能。
1. 由於延遲似乎隨卷增加，所以使用較少的訊息在Analytics上設定觸發器。
附件

**如何使用金鑰加密JavaScript**

執行JavaScript以加密私密金鑰。 管線配置需要它。

以下是可用於運行cryptString函式的代碼示例：

```
/*
USAGE:
  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
*/
 
function usage()
{
  return "USAGE:\n" +
    '  nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js\n'
}
 
var fn = application.arg;
if( fn == "" )
  logError("Missing key file file\n" + usage());
 
//open the pem file
plaintext = loadFile(fn)
 
if( !plaintext.match(/^-----BEGIN RSA PRIVATE KEY-----/) )
  logError("File should be an rsa private key")
 
logInfo("Encrypted key:\n" + cryptString(plaintext, <xtkSecretKey>))
```

在伺服器上，執行Javascript:

```
nlserver javascript -instance:<instancename> -file -arg:"<private_key.pem file>" -file encryptKey.js
```

從輸出複製編碼的索引鍵並貼至主控台。