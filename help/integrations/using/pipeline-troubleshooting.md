---
product: campaign
title: 管線疑難排解
description: 管線疑難排解
audience: integrations
content-type: reference
exl-id: 76645a6f-9536-49d6-b12a-fdd6113d31fa
source-git-commit: 02eebe83de49ee97e573b0c47ca1fddb2195b991
workflow-type: tm+mt
source-wordcount: '705'
ht-degree: 1%

---

# 管線疑難排解 {#pipeline-troubleshooting}

![](../../assets/common.svg)

**流水線失敗，錯誤為「沒有任務與掩碼流水線@&lt;實例>」**

您的Adobe Campaign Classic版本不支援管道。

1. 檢查 [!DNL pipelined] 元素存在於設定檔案中。 否則表示不支援。
1. 升級至Campaign 20.3 / [!DNL Gold Standard] 11或更高。

**管道失敗，出現「 aurait dü commencer par」 `[` 歐 `{` (iRc=16384)」**

此 **NmsPipeline_Config** 選項。 實際上是JSON剖析錯誤。
在選項中設定JSON設定 **NmsPipeline_Config**. 請參閱本頁的「路由選項」。

**管道失敗，顯示「主體必須是有效的組織或用戶端」**

組織ID配置無效。

1. 檢查組織ID(ImsOrgId)是否已在serverConf.xml中設定。
1. 檢查執行個體設定檔案中的空白組織ID是否可覆寫預設組織ID。 如果是，請將其移除。
1. 檢查組織ID是否正確。 若要尋找組織ID，請參閱 [本頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}

**管道失敗，出現「無效密鑰」**

執行個體設定檔案的@authPrivateKey參數不正確。

1. 檢查authPrivateKey是否已設定。
1. 檢查authPrivateKey:開頭為@，結尾為=，長度約為4000個字元。
1. 尋找原始金鑰，並確認其為：以RSA格式，長4096位，開頭為 `-----BEGIN RSA PRIVATE KEY-----`.
   <br> 如有必要，請重新建立金鑰並在Adobe Analytics上註冊。
1. 檢查金鑰是否在與 [!DNL pipelined]. <br>如有必要，請使用範例JavaScript或工作流程重做編碼。

**管道失敗，顯示「驗證期間無法讀取權杖」**

私密金鑰的格式無效。

1. 在本頁上運行密鑰加密步驟。
1. 檢查同一執行個體上是否加密金鑰。
1. 檢查設定檔案中的authPrivateKey是否符合產生的金鑰。 <br>請務必使用OpenSSL產生金鑰組。 例如，PuttyGen不會產生正確的格式。

**管道失敗，顯示「不再允許取得存取權杖」**

記錄應如下：

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

此錯誤訊息表示驗證是使用舊版Omniture基本OAuth來設定。 請參閱 [為Adobe Experience Cloud Triggers設定Adobe I/O](../../integrations/using/configuring-adobe-io.md) 升級驗證的檔案。

**未擷取觸發器**

當 [!DNL pipelined] 進程正在運行，且未檢索任何觸發器：

1. 確認觸發器在Analytics中處於作用中狀態且正在產生事件。
1. 請確定 [!DNL pipelined] 進程正在運行。
1. 尋找 [!DNL pipelined] 記錄檔。
1. 尋找 [!DNL pipelined] 狀態頁面。 觸發 — 捨棄，觸發 — 失敗應為零。
1. 檢查是否已在 **[!UICONTROL NmsPipeline_Config]** 選項。 如果有疑問，請使用通配符選項。
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

1. 檢查 [!DNL pipelined] 進程已運行。
1. 在pipelined.log中尋找可能導致重試的錯誤。 修正錯誤（如果適用）。
1. 檢查 [!DNL pipelined] 隊列大小的狀態頁。 如果佇列大小很大，請改善JS的效能。
1. 由於延遲似乎會隨著數量增加，因此請使用較少的訊息在Analytics上設定觸發器。

**將階段實例從舊式身份驗證升級為AdobeIO身份驗證**

變更預備執行個體上的整合驗證不會影響生產執行個體的設定。 您可以選擇升級您的階段實例，然後更新身份驗證以AdobeIO，並在您的階段實例上測試您的觸發器。

您的生產執行個體將繼續使用舊版驗證，不會受此變更影響。
