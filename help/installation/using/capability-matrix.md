---
product: campaign
title: 內部部署、混合和托管功能矩陣
description: 了解托管部署和內部部署之間的主要差異
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 32f55d02920b0104198f809b1be0a91306a4d9e4
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 20%

---

# 每個模型的功能矩陣{#capability-matrix-per-model}

![](../../assets/v7-only.svg)

Adobe Campaign Classic 隨附了一套模組和選項。這些模組的可用性及其使用取決於安裝的部署類型。 本文分享完整托管(Managed Services)和內部部署之間，某些功能的主要差異。

本頁顯示托管(Managed Services)與內部部署之間的主要差異。 混合部署的具體性取決於由Adobe托管並在您的場所中托管的元素。

本節](../../installation/using/hosting-models.md)導入了不同的托管模型。[

## 每個部署模型的可用性 {#capability-matrix}

| 功能 | 托管 | 混合 | 內部部署 | 詳細資料 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定 Campaign 伺服器 | 隨選 | 可用 | 可用 | [了解更多](../../installation/using/the-server-configuration-file.md) |
| 電子郵件密件副本 | 隨選 | 隨選 | 可用 | [了解更多](../../installation/using/email-archiving.md) |
| 管理Message Center執行實例 | 隨選 | 隨選 | 可用 | [了解更多](../../message-center/using/about-transactional-messaging.md) |
| 管理中間來源平台 | 隨選 | 隨選 | 可用 | [了解更多](../../installation/using/mid-sourcing-server.md) |
| 透過Litmus呈現收件匣 | 隨選 | 隨選 | 可用 | [了解更多](../../delivery/using/inbox-rendering.md) |
| 與IMS整合(Adobe ID) | 隨選 | 隨選 | 隨選 | [了解更多](../../integrations/using/about-adobe-id.md) |
| 加密/解密檔案傳輸的資料 | 隨選 | 可用 | 可用 | [了解更多](../../platform/using/unzip-decrypt.md) |
| 壓縮/解壓縮檔案 | 隨選 | 可用 | 可用 | [了解更多](../../platform/using/unzip-decrypt.md) |
| 域名委派 | 隨選 | 隨選 | 不可用 | [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hant) |
| 安裝SpamAssassin | 隨選 | 可用 | 可用 | [了解更多](../../delivery/using/spamassassin.md) |
| 存取傳遞能力報表 | 可用 | 隨選 | 可用 | [了解更多](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份驗證 | 不可用 | 可用 | 可用 | [了解更多](../../installation/using/connecting-through-ldap.md) |


## 同盟資料存取{#fda}

Adobe Campaign提供&#x200B;**同盟資料存取**(FDA)選項，以處理儲存在一或多個外部資料庫中的資訊：您不需變更Adobe Campaign資料的結構，即可存取外部資料。 [了解更多](../../installation/using/about-fda.md)

>[!CAUTION]
>
>除了[Snowflake連接器](../../installation/using/configure-fda-snowflake.md)外，只有內部部署或混合安裝才能透過FDA存取外部資料庫。


**另請參閱**

* [相容性比較表](../../rn/using/compatibility-matrix.md)
* [發行說明](../../rn/using/latest-release.md)
* [Campaign Classic升級](../../rn/using/rn-overview.md)
* [已棄用及已移除的功能](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] 發行版本](../../rn/using/gold-standard.md)
* [[!DNL Gold Standard] 方案](../../rn/using/gs-overview.md)
