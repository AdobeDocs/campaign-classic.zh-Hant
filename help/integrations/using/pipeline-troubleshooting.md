---
solution: Campaign Classic
product: campaign
title: 配置整合
description: 配置整合
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: b77a56a97e499f60c092fae45c7809f7bfd9f2ea
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---


# 管線疑難排解 {#pipeline-troubleshooting}

**流水線失敗，錯誤為「沒有任務與掩碼流水線@&lt;>」**

您的Adobe Campaign Classic版本不支援管道。

1. 檢查配置檔案中是否存在[!DNL pipelined]元素。 否則表示不支援。
1. 升級至Campaign 20.3或[!DNL Gold Standard] 11。

**Pipelined fails with &quot;aurait duj commencer par  `[` ou `{` (iRc=16384)&quot;**

未設定&#x200B;**NmsPipeline_Config**選項。 實際上是JSON剖析錯誤。
在選項**NmsPipeline_Config**&#x200B;中設定JSON配置。 請參閱本頁的「路由選項」。

**流水線失敗，但「主題必須是有效的組織或客戶」**

組織識別碼設定無效。

1. 檢查serverConf.xml中是否已設定IMSOrgId。
1. 在實例配置檔案中查找可以覆蓋預設值的空IMSOrgId。 如果是，請將其刪除。
1. 檢查IMSOrgId是否與Experience Cloud中的客戶相符。

**流水線失敗，密鑰無效**

實例配置檔案的@authPrivateKey參數不正確。

1. 檢查authPrivateKey是否已設定。
1. 檢查authPrivateKey:開頭為@，結尾為=，長度約為4000個字元。
1. 尋找原始金鑰並檢查其是否為：以RSA格式，長4096位，開頭為—BEGIN RSA PRIVATE KEY —。
   <br> 如有必要，請重新建立索引鍵並在Adobe Analytics註冊。
1. 檢查密鑰是否與[!DNL pipelined]在同一實例中編碼。 <br>如有必要，請使用範例JavaScript或工作流程重做編碼。

**流水線失敗，「在驗證期間無法讀取代號」**

私密金鑰的格式無效。

1. 在此頁上運行密鑰加密的步驟。
1. 檢查該密鑰是否在同一實例上加密。
1. 檢查設定檔案中的authPrivateKey是否與產生的金鑰相符。 <br>請確定使用OpenSSL產生金鑰對。例如，PuttyGen不會產生正確的格式。

**未擷取任何觸發器**

當[!DNL pipelined]進程正在運行且未檢索任何觸發器時：

1. 請確定觸發器在Analytics中處於作用中，且正在產生事件。
1. 確保[!DNL pipelined]進程正在運行。
1. 在[!DNL pipelined]日誌中查找錯誤。
1. 在[!DNL pipelined]狀態頁面中尋找錯誤。 觸發器丟棄，觸發器故障應為零。
1. 檢查觸發器名稱是否已在&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;選項中配置。 如果有疑問，請使用通配符選項。
1. 檢查Analytics是否有作用中的觸發器，且正在產生事件。 在Analytics中進行設定後，可能會延遲數小時，才會啟動。

**事件未連結至客戶**

當某些事件未連結至客戶時：

1. 檢查協調工作流是否正在運行（如果適用）。
1. 檢查事件是否包含客戶ID。
1. 使用客戶ID對客戶表進行查詢。
1. 檢查客戶匯入的頻率。 新客戶會透過工作流程匯入Adobe Campaign。

**事件處理中的延遲**

當Analytics時間戳記比促銷活動中事件的建立日期早得多時。

一般而言，觸發器可能需要15-90分鐘才能啟動行銷促銷活動。 這視資料收集的實作、在管道上載入、定義觸發器的自訂設定，以及Adobe Campaign的工作流程而定。

1. 檢查[!DNL pipelined]進程是否正在運行。
1. 在pipelined.log中查找可能導致重試的錯誤。 修正錯誤（如果適用）。
1. 檢查[!DNL pipelined]狀態頁面中的隊列大小。 如果佇列大小較大，請改善JS的效能。
1. 由於延遲似乎隨卷增加，所以使用較少的訊息在Analytics上設定觸發器。
