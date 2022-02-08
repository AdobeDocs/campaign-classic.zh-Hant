---
product: campaign
title: 現場營銷、混合和托管能力矩陣
description: 瞭解托管部署和內部部署之間的主要區別
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 20%

---

# 每個模型的能力矩陣{#capability-matrix-per-model}

![](../../assets/v7-only.svg)

Adobe Campaign Classic 隨附了一套模組和選項。這些模組的可用性及其使用取決於安裝的部署類型。 本文分享了完全托管(Managed Services)和內部部署之間某些功能的主要區別。

本頁顯示托管(Managed Services)和本地部署之間的主要區別。 混合部署的具體性取決於由Adobe托管並托管在您的辦公場所中的元素。

介紹了不同的托管模式 [此部分](../../installation/using/hosting-models.md)。

## 每個部署模型的可用性 {#capability-matrix}

| 功能 | 托管 | 混合 | 內部部署 | 詳細資訊 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定 Campaign 伺服器 | 按需 | 可用 | 可用 | [了解更多](../../installation/using/the-server-configuration-file.md) |
| 電子郵件密件抄送 | 按需 | 按需 | 可用 | [了解更多](../../installation/using/email-archiving.md) |
| 管理消息中心執行實例 | 按需 | 按需 | 可用 | [了解更多](../../message-center/using/about-transactional-messaging.md) |
| 管理中間採購平台 | 按需 | 按需 | 可用 | [了解更多](../../installation/using/mid-sourcing-server.md) |
| 通過Litmus呈現收件箱 | 按需 | 按需 | 可用 | [了解更多](../../delivery/using/inbox-rendering.md) |
| 與IMS(Adobe ID)整合 | 按需 | 按需 | 按需 | [了解更多](../../integrations/using/about-adobe-id.md) |
| 對檔案傳輸的資料進行加密/解密 | 按需 | 可用 | 可用 | [了解更多](../../platform/using/unzip-decrypt.md) |
| 壓縮/解壓縮檔案 | 按需 | 可用 | 可用 | [了解更多](../../platform/using/unzip-decrypt.md) |
| 域名委派 | 按需 | 按需 | 不可用 | [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hant) |
| 安裝SpamAssassin | 按需 | 可用 | 可用 | [了解更多](../../delivery/using/spamassassin.md) |
| 訪問可交付性報告 | 可用 | 按需 | 可用 | [了解更多](../../delivery/using/monitoring-deliverability.md) |
| 配置LDAP身份驗證 | 不可用 | 可用 | 可用 | [了解更多](../../installation/using/connecting-through-ldap.md) |


## 同盟資料存取{#fda}

Adobe Campaign提供 **聯合資料存取** (FDA)選項，用於處理儲存在一個或多個外部資料庫中的資訊：您可以訪問外部資料，而無需更改Adobe Campaign資料的結構。 [了解更多](../../installation/using/about-fda.md)

>[!CAUTION]
>
>相容的外部資料庫系統取決於您的主機模型。 瞭解詳情 [市場活動相容性清單](../../rn/using/compatibility-matrix.md)。

**另請參閱**

* [相容性比較表](../../rn/using/compatibility-matrix.md)
* [發行說明](../../rn/using/latest-release.md)
* [Campaign Classic升級](../../rn/using/rn-overview.md)
* [已棄用及已移除的功能](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] 版本](../../rn/using/gold-standard.md)
