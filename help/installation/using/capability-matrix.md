---
solution: Campaign Classic
product: campaign
title: 內部部署促銷活動、混合型和代管功能矩陣
description: 瞭解代管與內部部署之間的主要差異
audience: installation
content-type: reference
topic-tags: architecture-and-hosting-models
translation-type: tm+mt
source-git-commit: 1cde12d33551206da12e03a7e8deb198d427ab3a
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 19%

---


# 功能矩陣 {#capability-matrix-per-model}

Adobe Campaign Classic 隨附了一套模組和選項。這些模組的可用性和使用取決於安裝的部署類型。 本文分享了有關完全托管（托管服務）和內部部署之間某些功能的主要差異。

本頁顯示托管（托管服務）和內部部署之間的主要差異。 混合式部署的特定性取決於由Adobe代管並由您所在地代管的元素。

本節](../../installation/using/hosting-models.md)介紹了不同的代管模型。[

## 每部署型號{#capability-matrix}的可用性

| 功能 | 代管 | 混合 | 內部部署 | 詳細資訊 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定促銷活動伺服器 | 隨選 | 可用 | 可用 | [進一步了解](../../installation/using/the-server-configuration-file.md) |
| 電子郵件密件副本 | 隨選 | 隨選 | 可用 | [進一步了解](../../installation/using/email-archiving.md) |
| 管理消息中心執行實例 | 隨選 | 隨選 | 可用 | [進一步了解](../../message-center/using/about-transactional-messaging.md) |
| 管理中端採購平台 | 隨選 | 隨選 | 可用 | [進一步了解](../../installation/using/mid-sourcing-server.md) |
| 透過Litmus轉換收件匣 | 隨選 | 隨選 | 可用 | [進一步了解](../../delivery/using/inbox-rendering.md) |
| 與IMS整合(Adobe ID) | 隨選 | 隨選 | 隨選 | [進一步了解](../../integrations/using/about-adobe-id.md) |
| 加密／解密檔案傳輸的資料 | 隨選 | 可用 | 可用 | [進一步了解](../../platform/using/unzip-decrypt.md) |
| 壓縮／解壓縮檔案 | 隨選 | 可用 | 可用 | [進一步了解](../../platform/using/unzip-decrypt.md) |
| 域名委派 | 隨選 | 隨選 | 不可用 | [進一步了解](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html) |
| 安裝SpamAssassin | 隨選 | 可用 | 可用 | [進一步了解](../../delivery/using/spamassassin.md) |
| 存取傳送能力報表 | 可用 | 隨選 | 可用 | [進一步了解](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份驗證 | 不可用 | 可用 | 可用 | [進一步了解](../../installation/using/connecting-through-ldap.md) |


## 同盟資料存取{#fda}

Adobe Campaign提供&#x200B;**同盟資料存取**(FDA)選項，以處理儲存在一或多個外部資料庫中的資訊：您可以存取外部資料，而不需變更Adobe Campaign資料的結構。 [進一步了解](../../installation/using/about-fda.md)

>[!CAUTION]
>
>通過FDA訪問外部資料庫僅可用於內部部署或混合安裝，但[雪花連接器](../../installation/using/configure-fda-snowflake.md)除外。


**另請參閱**

* [相容性矩陣](../../rn/using/compatibility-matrix.md)
* [發行說明](../../rn/using/latest-release.md)
* [Campaign Classic升級](../../rn/using/rn-overview.md)
* [已過時及已移除的功能](../../rn/using/deprecated-features.md)
* [Gold Standard 版本](../../rn/using/gold-standard.md)
* [Gold Standard計畫](https://helpx.adobe.com/tw/campaign/kb/gold-standard.html)
