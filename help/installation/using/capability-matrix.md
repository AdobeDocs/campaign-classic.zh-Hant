---
product: campaign
title: Campaign內部部署、混合及託管功能矩陣
description: 瞭解託管部署和內部部署之間的主要差異
feature: Installation, Architecture
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: a2c425a8-9bde-4259-9140-5ada5397ed5f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 28%

---

# 各型號的功能矩陣{#capability-matrix-per-model}



Adobe Campaign Classic 隨附了一套模組和選項。這些模組的可用性及其使用方式會視您安裝的部署型別而定。 本文將分享完全託管(Managed Services)和內部部署之間特定功能主要差異的詳細資訊。

此頁面顯示託管(Managed Services)和內部部署之間的主要差異。 混合部署特性取決於Adobe所託管並在您設施中託管的元素。

我們匯入了不同的託管模型 [在本節中](../../installation/using/hosting-models.md).

## 每個部署模式的可用性 {#capability-matrix}

| 功能 | 託管 | 混合式 | 內部部署 | 詳細資料 |
|-----------------------------------------------|------------------|-----------|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 設定 Campaign 伺服器 | 隨選 | 可用 | 可用 | [了解更多](../../installation/using/the-server-configuration-file.md) |
| 電子郵件密件副本 | 隨選 | 隨選 | 可用 | [了解更多](../../installation/using/email-archiving.md) |
| 管理訊息中心執行例項 | 隨選 | 隨選 | 可用 | [了解更多](../../message-center/using/about-transactional-messaging.md) |
| 管理中間來源平台 | 隨選 | 隨選 | 可用 | [了解更多](../../installation/using/mid-sourcing-server.md) |
| 透過Litmus的收件匣轉譯 | 隨選 | 隨選 | 可用 | [了解更多](../../delivery/using/inbox-rendering.md) |
| 與IMS整合(Adobe ID) | 隨選 | 隨選 | 隨選 | [了解更多](../../integrations/using/about-adobe-id.md) |
| 加密/解密檔案傳輸的資料 | 隨選 | 可用 | 可用 | [了解更多](../../platform/using/unzip-decrypt.md) |
| 壓縮/解壓縮檔案 | 隨選 | 可用 | 可用 | [了解更多](../../platform/using/unzip-decrypt.md) |
| 網域名稱委派 | 隨選 | 隨選 | 不適用 | [了解更多](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hant) |
| 安裝SpamAssassin | 隨選 | 可用 | 可用 | [了解更多](../../delivery/using/spamassassin.md) |
| 存取傳遞能力報告 | 可用 | 隨選 | 可用 | [了解更多](../../delivery/using/monitoring-deliverability.md) |
| 設定LDAP驗證 | 不可用 | 可用 | 可用 | [了解更多](../../installation/using/connecting-through-ldap.md) |


## 同盟資料存取{#fda}

Adobe Campaign提供 **同盟資料存取** (FDA)選項，以處理儲存在一或多個外部資料庫中的資訊：您不需要變更Adobe Campaign資料的結構即可存取外部資料。 [了解更多](../../installation/using/about-fda.md)

>[!CAUTION]
>
>相容的外部資料庫系統取決於您的託管模式。 進一步瞭解 [Campaign相容性矩陣](../../rn/using/compatibility-matrix.md).
>

**另請參閱**

* [相容性比較表](../../rn/using/compatibility-matrix.md)
* [發行說明](../../rn/using/latest-release.md)
* [Campaign Classic升級](../../rn/using/rn-overview.md)
* [已棄用及已移除的功能](../../rn/using/deprecated-features.md)
* [[!DNL Gold Standard] 版本](../../rn/using/gold-standard.md)
