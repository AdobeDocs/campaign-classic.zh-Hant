---
product: campaign
title: 使用Adobe Campaign和Adobe Analytics
description: 使用Adobe Campaign和Adobe Analytics
feature: Analytics Integration
role: User, Admin
level: Beginner
exl-id: 985cf088-7546-4875-8e11-cafe5bd3e323
TQID: https://experienceleague.adobe.com/YuvP0m31wL-WlocUXU3rWovOiwLiA5XrEsnBLlW3nY8
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: d5ef99fa-df0c-4153-bf94-105ad0724167
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
subfeature_v2: id: cbcf4d90-26be-46e2-b16a-aebc529dc41eid: df0d6518-6f49-46e2-b46e-3bcc513f553fid: eb007b6d-6e57-46ab-9485-3f24d6102304id: b1fd1501-3105-4d6b-b4d4-9af53126df75
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 209
ht-degree: 12%

---

# 使用Adobe Campaign和Adobe Analytics {#adobe-analytics-connector-gs}

Adobe Analytics 連接器可讓 Adobe Campaign 和 Adobe Analytics 透過 **[!UICONTROL Web Analytics connectors]** 套件互動。 它會以關於行銷活動後使用者行為的區段形式，將資料轉送至Adobe Campaign。 相反地，它會將Adobe Campaign所傳遞行銷活動的指標和屬性傳送至Adobe Analytics。

## 護欄和先決條件 {#adobe-analytics-connector-guardrails}

開始使用Adobe Campaign-Adobe Analytics聯結器之前，請考量下列護欄和先決條件。

* 針對此整合，需要使用Adobe Identity Management System (IMS)連線至Campaign。 [了解更多資訊](../../integrations/using/about-adobe-id.md)。

* Adobe Analytics 連接器與異動訊息 (訊息中心) 不相容。

* 必須透過專用套件將Web Analytics聯結器附加元件安裝在您的環境中。

   * 對於混合式與內部部署實作，請務必遵循此[頁面](adobe-analytics-provisioning.md)中詳述的布建步驟。
   * 請以「主機」或「受管理的Cloud Services」使用者身分聯絡Adobe，將Campaign與Adobe Experience Cloud服務和解決方案連結。


## 設定與使用 {#adobe-analytics-connector-usage}

若要啟用這項整合，您必須建立您的Adobe技術帳戶，如[此頁面](oauth-technical-account.md)所詳述。

在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/connect/ac-aa){target="_blank"}中瞭解如何使用Adobe Campaign和Adobe Analytics。
