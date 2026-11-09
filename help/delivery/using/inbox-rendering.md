---
product: campaign
title: Campaign中的收件匣轉譯
description: 瞭解如何擷取電子郵件呈現，並提供在專用報告中
badge-v8: label="Also applies to v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Inbox Rendering, Monitoring, Email Rendering
role: User
exl-id: a3294e70-ac96-4e51-865f-b969624528ce
TQID: 'https://experienceleague.adobe.com/d0fFXi4Ma-PwY8vsSBOmvbhRD4631kUoagNXlf4Rmek'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: 2317b1ea-6db4-58c7-851f-717a69c0f5c0
    internal-label: Inbox Rendering
  - id: e519a22f-a06a-42fc-9d09-d78a3ab2c434
    internal-label: Monitoring guidelines
  - id: aef0b685-fc31-54d4-b831-a87fdb9d69de
    internal-label: Email Rendering
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
source-git-commit: 758d5159759b19f7ef32e8cc8f6237547599e727
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 8%
---
# 收件匣轉譯{#inbox-rendering}

Adobe Campaign運用[Litmus](https://litmus.com/email-testing)網頁式電子郵件測試解決方案來擷取電子郵件呈現，並將這些呈現呈現提供給專屬的報告使用。

>[!NOTE]
>
>作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要深入瞭解收件匣轉譯，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}。
>
>[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/deliverability-management/inbox-rendering){target=_blank}

## 正在啟用收件匣轉譯 {#activating-inbox-rendering}

[!BADGE 內部部署與混合式]{type=Caution url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"}

對於託管和混合型使用者端，收件匣轉譯會由Adobe技術支援和顧問在執行個體上設定。 如需詳細資訊，請聯絡您的Adobe客戶主管。

若為內部部署安裝，請依照下列步驟設定收件匣轉譯。

1. 透過&#x200B;**[!UICONTROL Tools]** > **[!UICONTROL Advanced]** > **[!UICONTROL Import package]**&#x200B;功能表安裝&#x200B;**[!UICONTROL Inbox rendering (IR)]**&#x200B;套件。 如需詳細資訊，請參閱[安裝Campaign Classic標準套件](../../installation/using/installing-campaign-standard-packages.md)。
1. 透過&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL External Accounts]**&#x200B;節點設定HTTP型別的外部帳戶。 如需詳細資訊，請參閱[建立外部帳戶](../../installation/using/external-accounts.md#creating-an-external-account)。
1. 設定外部帳戶引數，如下所示：
   * **[!UICONTROL Label]**：傳遞伺服器資訊
   * **[!UICONTROL Internal name]**： deliverabilityInstance
   * **[!UICONTROL Type]**： HTTP
   * **[!UICONTROL Server]**： https://deliverability-app.neolane.net/deliverability
   * **[!UICONTROL Encryption]**：無
   * 核取 **[!UICONTROL Enabled]** 選項。

   ![](assets/s_tn_inbox_rendering_external-account.png)

1. 前往&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Options]**&#x200B;節點。 搜尋&#x200B;**[!UICONTROL DmRendering_cuid]**&#x200B;選項並連絡支援人員，以取得需要複製到&#x200B;**[!UICONTROL Value (text)]**&#x200B;欄位的傳遞報告識別碼。
1. 編輯&#x200B;**serverConf.xml**&#x200B;檔案以允許呼叫Litmus伺服器。 將下列行加入`<urlPermission>`區段：

   ```
   <url dnsSuffix="deliverability-app.neolane.net" urlRegEx="https://.*"/>
   ```

1. 使用下列命令重新載入組態：

   ```
   nlserver config -reload
   ```

>[!NOTE]
>
>您可能需要從主控台登出並重新登入，才能使用收件匣轉譯。
