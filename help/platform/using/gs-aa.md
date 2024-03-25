---
product: campaign
title: 使用Adobe Campaign和Adobe Analytics
description: 使用Adobe Campaign和Adobe Analytics
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Analytics Integration
role: User, Admin
level: Beginner
source-git-commit: 59156851156338c9462781d31ce81a651362f2da
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 26%

---

# 使用Adobe Campaign和Adobe Analytics {#adobe-analytics-connector-gs}

Adobe Analytics 連接器可讓 Adobe Campaign 和 Adobe Analytics 透過 **[!UICONTROL Web Analytics connectors]** 套件互動。 它會以關於行銷活動後使用者行為的區段形式，將資料轉送至Adobe Campaign。 相反地，它會將Adobe Campaign所傳遞行銷活動的指標和屬性傳送至Adobe Analytics。

## 護欄和先決條件 {#adobe-analytics-connector-guardrails}

開始使用Adobe Campaign-Adobe Analytics聯結器之前，請考量下列護欄和先決條件。

* 針對此整合，需要使用AdobeIdentity Management系統(IMS)連線至Campaign。 [了解更多](../../integrations/using/about-adobe-id.md)。

* Adobe Analytics 連接器與異動訊息 (訊息中心) 不相容。

* 必須透過專用套件將Web Analytics聯結器附加元件安裝在您的環境中。

   * 針對混合部署和內部部署實作，請務必遵循此[頁面](../../platform/using/adobe-analytics-provisioning.md)中詳述的佈建步驟。
   * 請以「主機」或「受管理的Cloud Service」使用者身分聯絡Adobe，將Campaign與Adobe Experience Cloud服務和解決方案連結。


## 設定與使用 {#adobe-analytics-connector-usage}

瞭解如何在中使用Adobe Campaign和Adobe Analytics [Adobe Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}.

