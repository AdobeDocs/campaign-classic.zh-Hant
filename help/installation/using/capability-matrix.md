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
source-git-commit: c03e90b2e2f57606749c86cda343ce5756fec122
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 18%

---


# 能力矩陣 {#capability-matrix-per-model}

Adobe Campaign Classic 隨附了一套模組和選項。這些模組的可用性和使用取決於安裝的部署類型。 本文分享了有關完全托管（托管服務）和內部部署之間某些功能的主要差異。

本頁顯示托管（托管服務）和內部部署之間的主要差異。 混合式部署的特定性取決於由Adobe代管並由您所在地代管的元素。

本節將介紹不同的 [代管模型](../../installation/using/hosting-models.md)。

## 每部署模型的可用性 {#capability-matrix}

| 功能 | 代管 | 混合 | 內部部署 | 詳細資訊 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定促銷活動伺服器 | 隨選 | 可用 | 可用 | [進一步瞭解](../../installation/using/the-server-configuration-file.md) |
| 電子郵件密件副本 | 隨選 | 隨選 | 可用 | [進一步瞭解](../../installation/using/email-archiving.md) |
| 管理消息中心執行實例 | 隨選 | 隨選 | 可用 | [進一步瞭解](../../message-center/using/about-transactional-messaging.md) |
| 管理中端採購平台 | 隨選 | 隨選 | 可用 | [進一步瞭解](../../installation/using/mid-sourcing-server.md) |
| 透過Litmus轉換收件匣 | 隨選 | 隨選 | 可用 | [進一步瞭解](../../delivery/using/inbox-rendering.md) |
| 與IMS整合(Adobe ID) | 隨選 | 隨選 | 隨選 | [進一步瞭解](../../integrations/using/about-adobe-id.md) |
| 加密／解密檔案傳輸的資料 | 隨選 | 可用 | 可用 | [進一步瞭解](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 壓縮／解壓縮檔案 | 隨選 | 可用 | 可用 | [進一步瞭解](../../workflow/using/importing-data.md#unzipping-or-decrypting-a-file-before-processing) |
| 域名委派 | 隨選 | 隨選 | 不可用 | [進一步瞭解](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html) |
| 安裝SpamAssassin | 隨選 | 可用 | 可用 | [進一步瞭解](../../delivery/using/spamassassin.md) |
| 存取傳送能力報表 | 可用 | 隨選 | 可用 | [進一步瞭解](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份驗證 | 不可用 | 可用 | 可用 | [進一步瞭解](../../installation/using/connecting-through-ldap.md) |


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
* [Gold Standard計畫](https://helpx.adobe.com/tw/campaign/kb/gold-standard.html)
