---
product: campaign
title: '管線疑難排解 '
description: '管線疑難排解 '
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

**管道化失敗，出現錯誤「沒有任務與掩碼管道化@&lt;實例>對應」**

您的Adobe Campaign Classic版本不支援該管道。

1. 檢查 [!DNL pipelined] 配置檔案中存在元素。 如果不支援，則表示不支援。
1. 升級到市場活動20.3 / [!DNL Gold Standard] 11或更高。

**管道失敗，並顯示「 aurait dü commencer par 」 `[` 歐 `{` (iRc=16384)」**

的 **NmsPipeline_Config** 選項。 實際上是JSON分析錯誤。
在選項中設定JSON配置 **NmsPipeline_Config**。 請參閱此頁中的「路由選項」。

**管道化失敗，但「主題必須是有效的組織或客戶端」**

組織ID配置無效。

1. 檢查是否在serverConf.xml中設定了組織ID(ImsOrgId)。
1. 檢查實例配置檔案中的空組織ID是否可以覆蓋預設組織ID。 如果是，請將其刪除。
1. 檢查組織ID是否正確。 要查找組織ID，請參閱 [此頁](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant){_blank}

**管道化失敗，出現「無效鍵」**

實例配置檔案@authPrivateKey參數不正確。

1. 檢查是否已設定authPrivateKey。
1. 檢查authPrivateKey:以@開頭，以=結尾，大約4000個字元長。
1. 查找原始密鑰，並檢查它是否為：以RSA格式，4096位長，以 `-----BEGIN RSA PRIVATE KEY-----`。
   <br> 如有必要，請重新建立密鑰並在Adobe Analytics註冊。
1. 檢查密鑰是否在與 [!DNL pipelined]。 <br>如有必要，請使用示例JavaScript或工作流重做編碼。

**管道化失敗，「無法在驗證期間讀取令牌」**

私鑰的格式無效。

1. 在此頁上運行密鑰加密步驟。
1. 檢查該密鑰是否在同一實例上加密。
1. 檢查配置檔案中的authPrivateKey是否與生成的密鑰匹配。 <br>確保使用OpenSSL生成密鑰對。 例如，PuttyGen未生成正確的格式。

**流水線失敗，「不再允許獲取訪問令牌」**

日誌應如下：

```
2021-05-31T08:42:18.124Z        66462   66501   1       error   log     Listener: JWT Token is empty. (iRc=16384)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     Unknown authentication mode: 'Bearer realm="Adobe Analytics"'. (iRc=-55)
2021-05-31T08:42:18.210Z        66462   66501   1       error   log     BAS-010007 Function not implemented (iRc=-55)
2021-05-31T08:42:48.582Z        66462   66501   1       warning log     Connection seems to have been lost. Attempting to reconnect.
2021-05-31T08:43:09.156Z        66462   66501   1       error   log     INT-150012 The HTTP query returned a 'Forbidden' type error (403) (iRc=-53)
2021-05-31T08:43:09.160Z        66462   66501   1       error   log     Error while authenticating: '{"error":"This client: df73c224e5-triggers-test is no longer allowed to get access token."}' (iRc=16384)
```

此錯誤消息表示驗證是使用舊版Omniture基OAuth配置的。 請參閱 [為Adobe Experience Cloud Triggers配置Adobe I/O](../../integrations/using/configuring-adobe-io.md) 文檔以升級驗證。

**未檢索任何觸發器**

當 [!DNL pipelined] 進程正在運行，並且未檢索任何觸發器：

1. 確保觸發器在分析中處於活動狀態並正在生成事件。
1. 確保 [!DNL pipelined] 進程正在運行。
1. 查找 [!DNL pipelined] 日誌。
1. 查找 [!DNL pipelined] 的子菜單。 觸發器丟棄，觸發器故障應為零。
1. 檢查觸發器名稱是否在 **[!UICONTROL NmsPipeline_Config]** 的雙曲餘切值。 如果有疑問，請使用通配符選項。
1. 檢查分析是否具有活動觸發器並且正在生成事件。 在Analytics中進行配置後，在其處於活動狀態之前可能會延遲幾個小時。

**事件未連結到客戶**

當某些事件未連結到客戶時：

1. 檢查協調工作流是否正在運行（如果適用）。
1. 檢查事件是否包含客戶ID。
1. 使用客戶ID對客戶表進行查詢。
1. 檢查客戶導入的頻率。 新客戶將通過工作流導入Adobe Campaign。

**事件處理中的延遲**

當分析時間戳比市場活動中事件的建立日期早得多時。

通常，啟動營銷活動可能需要15到90分鐘。 這取決於資料收集的實現、流水線上的載入、定義的觸發器的自定義配置以及Adobe Campaign的工作流程。

1. 檢查 [!DNL pipelined] 進程已運行。
1. 在pipelined.log中查找可能導致重試的錯誤。 修復錯誤（如果適用）。
1. 檢查 [!DNL pipelined] 隊列大小的狀態頁。 如果隊列大小較大，請提高JS的效能。
1. 由於延遲似乎隨卷而增加，因此請使用較少的消息在分析上配置觸發器。

**將階段實例從舊式身份驗證升級到AdobeIO身份驗證**

更改階段實例上的整合身份驗證不會影響生產實例的配置。 您可以選擇升級階段實例，然後將身份驗證更新為AdobeIO，並在階段實例上test觸發器。

您的生產實例將繼續使用舊式身份驗證，不會受此更改的影響。
