---
product: campaign
title: 配置整合
description: 配置整合
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 1%

---

# 管線疑難排解 {#pipeline-troubleshooting}

**流水線失敗，錯誤為「沒有任務與掩碼流水線@&lt;>」**

您的Adobe Campaign Classic版本不支援管道。

1. 檢查設定檔案中是否存在[!DNL pipelined]元素。 否則表示不支援。
1. 升級至Campaign 20.3或[!DNL Gold Standard] 11。

**管道輸出失敗，出現「 `[` aurait duj commencer par  `{` ou(iRc=16384)」**

未設定&#x200B;**NmsPipeline_Config**選項。 實際上是JSON剖析錯誤。
在選項**NmsPipeline_Config**&#x200B;中設定JSON配置。 請參閱本頁的「路由選項」。

**管道失敗，顯示「主體必須是有效的組織或用戶端」**

組織標識符配置無效。

1. 檢查是否已在serverConf.xml中設定IMSOrgId。
1. 在實例配置檔案中查找可以覆蓋預設值的空IMSOrgId。 如果是，請將其移除。
1. 檢查IMSOrgId是否與Experience Cloud中的客戶匹配。

**管道失敗，出現「無效密鑰」**

執行個體設定檔案的@authPrivateKey參數不正確。

1. 檢查authPrivateKey是否已設定。
1. 檢查authPrivateKey:開頭為@，結尾為=，長度約為4000個字元。
1. 尋找原始金鑰，並確認其為：以RSA格式，長4096位，以 — 開始RSA私鑰 — 開頭。
   <br> 如有必要，請重新建立金鑰並在Adobe Analytics上註冊。
1. 檢查密鑰是否在與[!DNL pipelined]相同的實例內編碼。 <br>如有必要，請使用範例JavaScript或工作流程重做編碼。

**管道失敗，顯示「驗證期間無法讀取權杖」**

私密金鑰的格式無效。

1. 在本頁上運行密鑰加密步驟。
1. 檢查同一執行個體上是否加密金鑰。
1. 檢查設定檔案中的authPrivateKey是否符合產生的金鑰。 <br>請務必使用OpenSSL產生金鑰組。例如，PuttyGen不會產生正確的格式。

**未擷取觸發器**

當[!DNL pipelined]進程正在運行且未檢索任何觸發器時：

1. 確認觸發器在Analytics中處於作用中狀態且正在產生事件。
1. 確保[!DNL pipelined]進程正在運行。
1. 查找[!DNL pipelined]日誌中的錯誤。
1. 查找[!DNL pipelined]狀態頁面中的錯誤。 觸發 — 捨棄，觸發 — 失敗應為零。
1. 檢查&#x200B;**[!UICONTROL NmsPipeline_Config]**&#x200B;選項中是否配置了觸發器名稱。 如果有疑問，請使用通配符選項。
1. 檢查Analytics是否具有作用中的觸發器且正在產生事件。 在Analytics中進行設定後，可能會延遲數小時，才會開始使用。

**事件未連結至客戶**

某些事件未連結至客戶時：

1. 檢查調解工作流程是否正在執行（如果適用）。
1. 檢查事件是否包含客戶ID。
1. 使用客戶ID在客戶表上進行查詢。
1. 檢查客戶匯入的頻率。 新客戶會透過工作流程匯入至Adobe Campaign。

**事件處理中的延遲**

當Analytics時間戳記遠早於Campaign中事件的建立日期時。

一般而言，觸發器可能需要15到90分鐘才會啟動行銷活動。 視資料收集實作、管道負載、已定義觸發器的自訂設定，以及Adobe Campaign中的工作流程而定。

1. 檢查[!DNL pipelined]進程是否正在運行。
1. 在pipelined.log中尋找可能導致重試的錯誤。 修正錯誤（如果適用）。
1. 檢查[!DNL pipelined]狀態頁面中的隊列大小。 如果佇列大小很大，請改善JS的效能。
1. 由於延遲似乎會隨著數量增加，因此請使用較少的訊息在Analytics上設定觸發器。
