---
product: campaign
title: Campaign Classic 2024 版本
description: 進一步瞭解 Campaign Classic 2024 版本
feature: Release Notes
role: User
level: Beginner
exl-id: 8e20391d-3628-4d0c-b413-c34e046ae810
source-git-commit: bf45c8bcdd41e614f9be09bc0fd6385707159841
workflow-type: ht
source-wordcount: '387'
ht-degree: 100%

---

# 2024 版本{#release-2024}

## 版本 7.4.1 - 版本編號 9383 {#release-7-4-1}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

_2024 年 6 月 18 日_

### 變更與改善 {#release-7-4-1-changes}

* Adobe 已棄用服務帳戶 (JWT) 認證，Campaign 與 Adobe 解決方案和應用程式的輸出整合現在需依賴 OAuth 伺服器對伺服器認證。 如果您已實作輸出整合 (例如 Campaign-Analytics 整合或 Experience Cloud 觸發器整合)，則必須在 2025 年 1 月 27 日之前，將 Campaign 環境升級至 v7.4.1，並將技術帳戶移轉至 oAuth。 [了解更多](../../integrations/using/oauth-technical-account.md)

* 在您已[將 Campaign 技術操作者移轉至 Developer Console](../../technotes/using/ims-migration.md)，並已[轉變為 IMS 以進行一般使用者驗證](../../technotes/using/migrate-users-to-ims.md)之後，您現在可以啟用使用者介面和 API 限制，移除原生驗證特有的選項和功能。 [了解更多](../../technotes/using/impact-ims-migration.md)


### 相容性更新 {#release-7-4-1-compat}

[Adobe Campaign 相容性矩陣](compatibility-matrix.md)已隨此新版本的變更來更新，如下所列。

* Adobe Campaign 現在相容於 **Microsoft Server 2022** 作業系統。
* Adobe Campaign 現已相容於 **RHEL 9** 作業系統。

  >[!CAUTION]
  >
  >作為使用 RHEL 9 的內部部署客戶，如果您想要使用 DKIM (網域金鑰識別郵件) 身分驗證，則必須更新系統設定，詳細資訊請參閱[本節](../../installation/using/installing-packages-with-linux.md#rhel-9-update)。


* Adobe Campaign 現在相容於 **Microsoft SQL Server 2022** 和 **Oracle 23c** 關聯資料庫管理系統，以及與同盟資料存取 (FDA) 相容。

* Adobe Campaign 現在至少需要 Java 開發套件 (JDK) 11。在 Windows 上，必須如[本節](../../installation/using/application-server.md#jdk)所述提供 JRE。

* 適用於行動應用程式的 Campaign (Neolane) SDK 現已棄用。您現在必須轉變為 Adobe Experience Platform SDK。 [了解更多](deprecated-features.md)。

  同時，為確保服務持續性，Campaign v7.4 隨附：

   * 適用於 iOS 的新 Campaign SDK 1.0.27，與 iOS 16 和 17 相容，並提供最新 [Apple iOS 隱私權請求需求](https://developer.apple.com/news/?id=r1henawx){target="_blank"}。
   * 適用於 Android 14 的新 Campaign SDK。

### 其他變更 {#release-7-4-1-other}

從 v7.4.1 版開始，Campaign 不再包含 RPM Linux 套件的 XML 資料庫。身為內部部署或混合客戶，您的管理員必須安裝這些資料庫。[了解更多](../../installation/using/installing-packages-with-linux.md)

### 修補程式 {#release-7-4-1-patches}

此版本隨附下列修正：

NEO-74754、NEO-73174、NEO-72504、NEO-71534、NEO-71473、NEO-70195、NEO-69663、NEO-69651、NEO-67620、NEO-67235、NEO-66797、NEO-64680、NEO-63706、NEO-63657、NEO-62964、NEO-62575、NEO-58734、NEO-40531、NEO-36189、NEO-29592


