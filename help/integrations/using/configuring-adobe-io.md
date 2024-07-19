---
product: campaign
title: 為Adobe Experience Cloud Triggers設定Developer Console
description: 瞭解如何設定Developer Console Adobe Experience Cloud Triggers
feature: Triggers
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
hide: true
hidefromtoc: true
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 1%

---

# 為Adobe Experience Cloud Triggers設定Developer Console {#configuring-adobe-io}

<!--
>[!CAUTION]
>
>If you are using an older version of Triggers integration through oAuth authentication, **you need to move to Adobe I/O as described below**. 
>Note that during this move to [!DNL Adobe I/O], some incoming triggers may be lost.
>
>Legacy oAuth authentication mode with Campaign has been retired on **October 20, 2021**. Hosted environments benefit from an extension until **May 25, 2022**. As an on-premise or hybrid customer, contact Adobe Customer Care to extend support to **May 2022**. You must [provide the AppID of the OAuth application](../../integrations/using/configuring-pipeline.md#step-optional) to Adobe.
-->

## 先決條件 {#adobe-io-prerequisites}

<!--
This integration only applies starting **Campaign Classic 20.2.4 and above, 19.1.8 and Gold Standard 11 releases**.
-->

開始此實作前，請檢查您是否擁有：

* 有效的&#x200B;**組織識別碼**：組織ID是Adobe Experience Cloud中的唯一識別碼，例如VisitorID服務和IMS單一登入(SSO)。 [了解更多](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant)
* 您組織的&#x200B;**開發人員存取權**。 組織的系統管理員必須遵循&#x200B;**將開發人員新增至單一產品設定檔**&#x200B;程式（在此頁面](https://helpx.adobe.com/enterprise/using/manage-developers.html)中詳述[），以提供與觸發器相關聯之Adobe Analytics產品的`Analytics - {tenantID}`產品設定檔的開發者存取權。

## 步驟1：建立/更新OAuth專案 {#creating-adobe-io-project}

>[!AVAILABILITY]
>
> Adobe已棄用服務帳戶(JWT)認證，Campaign與Adobe解決方案和應用程式的整合現在必須依賴OAuth伺服器對伺服器認證。 </br>
>
> * 如果您已實作與Campaign的傳入整合，您必須移轉您的技術帳戶，如[本檔案](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/#_blank)所詳述。 現有的服務帳戶(JWT)認證將持續運作到2025年1月27日。</br>
>
> * 如果您已實作輸出整合(例如Campaign-Analytics整合或Experience Cloud Triggers整合)，則在2025年1月27日前都能正常運作。 不過，在該日期之前，您必須將您的Campaign環境升級至v7.4.1，並將您的技術帳戶移轉至oAuth。

若要繼續設定Adobe Analytics聯結器，請存取Adobe Developer主控台並建立您的OAuth伺服器對伺服器專案。

如需詳細檔案，請參閱[此頁面](oauth-technical-account.md#oauth-service)。

## 步驟2：在Adobe Campaign中新增專案認證 {#add-credentials-campaign}

請依照[此頁面](oauth-technical-account.md#add-credentials)中詳述的步驟操作，在Adobe Campaign中新增您的OAuth專案認證。

## 步驟3：更新管線標籤 {#update-pipelined-tag}

若要更新[!DNL pipelined]標籤，您必須將驗證型別更新至組態檔&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的Developer Console專案，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然後，執行`config -reload`並重新啟動[!DNL pipelined]，以將變更列入考量。
