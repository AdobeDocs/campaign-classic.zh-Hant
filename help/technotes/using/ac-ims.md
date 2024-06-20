---
title: 移轉至Adobe Identity Management系統(IMS)
description: 瞭解如何將您的驗證流程移轉至AdobeIdentity Management系統(IMS)
source-git-commit: 106f0409f452595209f0e2aa2fa187a2e04338a9
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 1%

---

# 移轉至Adobe Identity Management系統(IMS) {#migrate-to-ims}

為了強化安全性和驗證流程，Adobe Campaign強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}.

此外，Adobe Campaign使用者端應用程式現在會直接使用IMS技術帳戶權杖呼叫Campaign API。 您必須將技術運運算元移轉至Adobe Developer Console。

>[!CAUTION]
>
>此變更已適用於Campaign Classic v7，並且將 **強制** 以移至Campaign v8。 Campaign v8中不允許原生使用者/密碼驗證。 **Adobe建議從Campaign v7.3.5開始執行此移轉，以便能夠順利移轉至Campaign v8。**
>

## 移轉步驟 {#ims-steps}

移轉至 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"} 是確保環境安全且標準化的安全性必要條件，因為大部分其他Adobe Experience Cloud解決方案和應用程式皆已在IMS上。

Adobe可協助您進行這項移轉工作。 您可在以下文章中找到詳細的內容和逐步指引：

* 有關使用者驗證的移轉詳情，請參閱 [此頁面](migrate-users-to-ims.md).
* 有關技術操作員驗證的移轉詳情，請參閱 [此頁面](ims-migration.md).
* 從Campaign v7.4.1開始，啟用使用者介面和API限制以移除原生驗證特有的選項和功能，如所述 [此頁面](impact-ims-migration.md).


## IMS移轉相容版本 {#ims-versions}

此移轉的先決條件是將您的環境升級至以下產品版本之一：

* Campaign v7.4.1 （建議）
* Campaign v7.3.5
* Campaign v7.3.3.IMS
* Campaign v7.3.2.IMS

下列Campaign版本將在 [發行說明](../../rn/using/latest-release.md).

## 常見問題集 {#ims-migration-faq}

### 何時可以開始移轉？ {#ims-migration-start}

移轉至「 」的建議 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"} 是將您的環境升級至Campaign Classicv7.4.1 (或 [IMS移轉相容版本](#ims-versions))。

升級至最新版本後，您就可以在Stage環境中開始IMS移轉，並據此規劃生產環境。

### 組建版本升級至Campaign Classic v7.4.1後會發生什麼事？ {#ims-migration-after-upgrade}

在您的環境升級至Campaign Classicv7.4.1之後(或 [IMS移轉相容版本](#ims-versions))，您可以開始轉換至 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}.

### 移轉何時完成？ {#ims-migration-end}

使用者移轉及技術操作員移轉至AdobeIdentity Management系統(IMS)後，您必須更新環境，移除原生驗證專用，且不再適用於IMS驗證的選項。 此更新僅可從Campaign v7.4.1開始使用。 [瞭解更多](impact-ims-migration.md)



## 有用的連結 {#ims-useful-links}

* [終端使用者移轉至IMS](migrate-users-to-ims.md)
* [技術運運算元移轉至Adobe Developer主控台](ims-migration.md)
* [Adobe Campaign Classic v7最新發行說明](../../rn/using/latest-release.md)
* [什麼是AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}
