---
product: campaign
title: 最新版本
description: 最新 Campaign Classic v7 版本注意事項
feature: Release Notes
role: User
level: Beginner
exl-id: d65869ca-a785-4327-8e8d-791c28e4696c
source-git-commit: d31aa28da06e65664da655b6b082563767b35f7a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 最新版本 {#latest-release}

本頁面列出&#x200B;**最新 Campaign Classic v7 版本**&#x200B;的新功能、改善和修正。每個新版本都會提供以顏色具體化的狀態。 請於[本頁](rn-overview.md)進一步了解 Campaign Classic v7 版本編號狀態。

## 版本 7.4.1 - 版本編號 9383 {#release-7-4-1}

[!BADGE 一般可用性]{type=Positive url="https://experienceleague.adobe.com/docs/campaign-classic/using/release-notes/rn-overview.html?lang=zh-Hant#rn-statuses" tooltip="一般可用性"}

_2024年6月18日_

### 變更和改良 {#release-7-4-1-changes}

* 由於Adobe已棄用服務帳戶(JWT)認證，因此Campaign與Adobe解決方案和應用程式的輸出整合現在需依賴OAuth伺服器對伺服器認證。 如果您已實作輸出整合(例如Campaign-Analytics整合或Experience Cloud Triggers整合)，則您必須在2025年1月27日之前將Campaign環境升級至v7.4.1，並將您的技術帳戶移轉至oAuth。 [了解更多](../../integrations/using/oauth-technical-account.md)

* 一旦您擁有 [已將Campaign技術運運算元移轉至開發人員主控台](../../technotes/using/ims-migration.md) 和 [已轉換為IMS以進行一般使用者驗證](../../technotes/using/migrate-users-to-ims.md)，您現在可以啟用使用者介面和API限制，移除原生驗證特有的選項和功能。 [了解更多](../../technotes/using/impact-ims-migration.md)



### 相容性更新 {#release-7-4-1-compat}

此 [Adobe Campaign相容性矩陣](compatibility-matrix.md) 已更新此新版本的變更，如下所列。

* Adobe Campaign現在相容於 **Microsoft Server 2022** 和 **RHEL 9** 作為作業系統。

* Adobe Campaign現在相容於 **Microsoft SQL Server 2022** 和 **oracle23c** 做為關係資料庫管理系統，以及同盟資料存取(FDA)。

* Adobe Campaign現在至少需要Java開發套件(JDK) 11。 在Windows上，必須如所述提供JRE [本節](../../installation/using/application-server.md#jdk).

* 適用於行動應用程式的Campaign (Neolane) SDK現已棄用。 您現在必須轉換至Adobe Experience Platform SDK。 [了解更多](deprecated-features.md)。

  同時，為確保服務持續性，Campaign v7.4提供：

   * 適用於iOS的全新Campaign SDK 1.0.27，與iOS 16和17相容，並提供最新版本 [Apple iOS隱私權請求需求](https://developer.apple.com/news/?id=r1henawx){target="_blank"}.
   * 適用於Android 14的新Campaign SDK。


### 修補程式 {#release-7-4-1-patches}

此版本隨附下列修正：

NEO-74754、NEO-73174、NEO-72504、NEO-71534、NEO-71473、NEO-70195、NEO-69663、NEO-69651、NEO-67620、NEO-67235、NEO-66797、NEO-64680、NEO-63706、NEO-63657、NEO-62964、NEO-62575、NEO-58734、NEO-40531、NEO-36189、NEO-29592

