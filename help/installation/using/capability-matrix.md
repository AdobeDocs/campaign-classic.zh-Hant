---
title: 內部部署促銷活動、混合型和代管功能矩陣
description: 瞭解代管與內部部署之間的主要差異
page-status-flag: never-activated
uuid: d1c786a1-2691-4966-9108-059004050464
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
discoiquuid: 582f7ac6-cebe-4b47-8730-bbc16fd6b1bd
translation-type: tm+mt
source-git-commit: c2e1b4cf7051b7f1b9d5f2db0d9f51a733ca2abc
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 10%

---


# 每個代管模型的能力矩陣 {#capability-matrix-per-model}

Adobe Campaign Classic 隨附了一套模組和選項。這些模組的可用性和使用取決於安裝的部署類型。 本文分享了有關完全托管（托管服務）和內部部署之間某些功能的主要差異。

本頁顯示托管（托管服務）和內部部署之間的主要差異。 混合式部署的特定性取決於由Adobe代管並由您所在地代管的元素。

本節將介紹不同的 [代管模型](../../installation/using/hosting-models.md)。

## 能力矩陣{#capability-matrix}

| 功能 | 代管 | 混合 | 內部部署 | 詳細資訊 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定促銷活動伺服器 | 隨選 | 可用 | 可用 | Adobe[只能針對代管客戶](../../installation/using/the-server-configuration-file.md)，修改伺服器設定檔。 |
| 電子郵件密件副本 | 隨選 | 隨選 | 可用 | 若是代管和混合式架構，請連絡您的帳戶主管以啟用電子郵件密件副本。 對於現場安裝，請遵循說明檔案中的准則。 [進一步瞭解](../../installation/using/email-archiving.md) |
| 管理消息中心執行實例 | 隨選 | 隨選 | 可用 | 對於代管部署，某些設定（例如在執行例項上建立使用者）只能由Adobe執行。 [進一步瞭解](../../message-center/using/about-transactional-messaging.md) |
| 管理中端採購平台 | 隨選 | 隨選 | 可用 | Adobe代管的中端來源平台只能由Adobe設定。 |
| 透過Litmus轉換收件匣 | 隨選 | 隨選 | 可用 | 你需要一個利特摩斯賬戶。 您必須聯絡Adobe以取得必要的詳細資訊或執行「收件匣」轉譯設定。 [進一步瞭解](../../delivery/using/inbox-rendering.md) |
| 與IMS整合(Adobe ID) | 隨選 | 隨選 | 隨選 | IMS布建由Adobe執行。 此整合是Adobe Experience Cloud整合的先決條件。 [進一步瞭解](../../integrations/using/about-adobe-id.md) |
| 加密／解密檔案傳輸的資料 | 隨選 | 可用 | 可用 | 若要啟用檔案前或後處理，必須在Adobe Campaign伺服器上安裝必要的公用程式。 代管客戶可使用促銷活動控制面板。 [進一步瞭解](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 壓縮／解壓縮檔案 | 隨選可用 | 可用 | 若要啟用檔案前或後處理，必須在Adobe Campaign伺服器上安裝必要的公用程式。 代管客戶可使用促銷活動控制面板。 [進一步瞭解](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 域名委派 | 隨選 | 隨選 | 不可用 | [進一步瞭解](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html) |
| 安裝SpamAssassin | 隨選 | 可用 | 可用 | 安裝SpamAssassin需要編輯伺服器配置檔案。 [進一步瞭解](../../delivery/using/spamassassin.md) |
| 存取傳送能力報表 | 可用 | 隨選 | 可用 | 在某些混合部署中，無法從行銷例項存取傳送能力報表。 |
| 配置LDAP身份驗證 | 不可用 | 可用 | 可用 | LDAP配置僅可用於內部部署或混合安裝。 [進一步瞭解](../../installation/using/connecting-through-ldap.md) |


## Federated Data Access{#fda}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data. [進一步瞭解](../../platform/using/about-fda.md)

>[!CAUTION]
>
>除了 [Snowflake連接器外，只有內部部署或混合安裝才能透過FDA存取外部資料庫](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)。


**另請參閱**

* [相容性矩陣](../../rn/using/compatibility-matrix.md)
* [發行說明](../../rn/using/latest-release.md)
* [Campaign Classic升級](../../rn/using/rn-overview.md)
* [已棄用及已移除的功能](../../rn/using/deprecated-features.md)
* [Gold Standard版本](../../rn/using/gold-standard.md)
* [金本位計畫](https://helpx.adobe.com/tw/campaign/kb/gold-standard.html)。
