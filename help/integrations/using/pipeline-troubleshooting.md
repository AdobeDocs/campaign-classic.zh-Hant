---
product: campaign
title: 管線疑難排解
description: 管線疑難排解
feature: Triggers
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '713'
ht-degree: 0%

---

# 管線疑難排解 {#pipeline-troubleshooting}



**管線化失敗，錯誤為「沒有工作對應到遮色片管線化@&lt;執行個體>」**

您的Adobe Campaign Classic版本不支援管道。

1. 檢查 [!DNL pipelined] 元素會出現在設定檔案中。 如果沒有，表示不支援。
1. 升級至Campaign 20.3 / [!DNL Gold Standard] 11或更高。

**管道化失敗並出現「 aurait du commencer par 」 `[` ou `{` (iRc=16384)」**

此 **NmsPipeline_Config** 選項未設定。 這實際上是JSON剖析錯誤。
在選項中設定JSON設定 **NmsPipeline_Config**. 請參閱本頁面的「路由選項」。

**管線失敗，並顯示「主體必須是有效的組織或使用者端」**

組織ID設定無效。

1. 檢查組織ID (ImsOrgId)是否已在serverConf.xml中設定。
1. 檢查執行個體設定檔案中的空白組織ID能否覆寫預設組織ID。 若是如此，請將其移除。
1. 檢查組織ID是否正確。 若要尋找您的組織ID，請參閱 [此頁面](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}

**管線失敗，出現「無效金鑰」**

執行個體設定檔案的@authPrivateKey引數不正確。

1. 檢查是否已設定authPrivateKey。
1. 檢查authPrivateKey：開頭為@，結尾為=，並且長度約為4000個字元。
1. 尋找原始金鑰並檢查其是否為：在RSA格式中，4096位元長，開頭為 `-----BEGIN RSA PRIVATE KEY-----`.
   <br> 如有必要，請重新建立金鑰並在Adobe Analytics上註冊。
1. 檢查索引鍵是否編碼於與相同的執行個體中 [!DNL pipelined]. <br>如有必要，請使用範例JavaScript或工作流程重做編碼。

**管線失敗，因為「無法在驗證期間讀取權杖」**

私密金鑰的格式無效。

1. 執行此頁面上的金鑰加密步驟。
1. 檢查相同執行個體上的金鑰是否已加密。
1. 檢查設定檔案中的authPrivateKey是否符合產生的金鑰。 <br>請務必使用OpenSSL來產生金鑰組。 例如，PuttyGen不會產生正確的格式。

**管線失敗，因為「不再允許取得存取權杖」**

記錄應如下所示：

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

此錯誤訊息表示驗證是使用舊版Omniture基底OAuth進行設定。 請參閱 [設定Adobe Experience Cloud Triggers的Adobe I/O](../../integrations/using/about-triggers.md#implement) 說明檔案升級您的驗證。

**未擷取任何觸發程式**

當 [!DNL pipelined] 處理序正在執行，未擷取任何觸發程式：

1. 請確定Analytics中的觸發程式為作用中狀態，且正在產生事件。
1. 確定 [!DNL pipelined] 處理序正在執行。
1. 尋找 [!DNL pipelined] 記錄。
1. 尋找 [!DNL pipelined] 狀態頁面。 trigger-discarted， trigger-failures應為零。
1. 檢查觸發程式名稱是否設定於 **[!UICONTROL NmsPipeline_Config]** 選項。 如有疑問，請使用萬用字元選項。
1. 檢查Analytics是否有作用中的觸發程式且正在產生事件。 在Analytics中完成設定後，延遲數小時才會生效。

**事件未連結至客戶**

當部分事件未連結至客戶時：

1. 檢查調解工作流程是否正在執行（如果適用）。
1. 檢查事件是否包含客戶ID。
1. 使用客戶ID查詢客戶表格。
1. 檢查客戶匯入的頻率。 新客戶會使用工作流程匯入Adobe Campaign。

**事件處理中的延遲**

當Analytics時間戳記遠早於Campaign中事件的建立日期時。

一般而言，觸發器可能需要15到90分鐘的時間來啟動行銷活動。 所需時間會根據資料收集實作、管道上的負載、已定義觸發器的自訂設定，以及Adobe Campaign中的工作流程而有所不同。

1. 檢查 [!DNL pipelined] 處理序已在執行中。
1. 尋找pipelined.log中可能導致重試的錯誤。 修正錯誤（如果適用）。
1. 檢查 [!DNL pipelined] 佇列大小的狀態頁面。 如果佇列大小很大，請改善JS的效能。
1. 由於延遲似乎會隨著音量增加，請使用較少的訊息在Analytics上設定觸發程式。

**將階段執行個體從舊版驗證升級為AdobeIO驗證**

變更階段執行個體上的整合驗證不會影響生產執行個體的設定。 您可以選擇升級中繼執行個體，然後更新驗證以AdobeIO，並在中繼執行個體上測試您的觸發程式。

您的生產執行個體將繼續使用舊版驗證，此變更不會影響執行個體。
