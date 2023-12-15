---
title: 移轉Campaign運運算元至AdobeIdentity Management系統(IMS)
description: 瞭解如何將Campaign運運算元移轉至AdobeIdentity Management系統(IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: bc9367d598474b7971f25c27980ff25dd93bf87a
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 2%

---

# 移轉Campaign運運算元至AdobeIdentity Management系統(IMS) {#migrate-users-to-ims}

為了強化安全性和驗證程式，Adobe Campaign強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至AdobeIdentity Management系統(IMS)。 所有運運算元都應該實作 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"} 以連線至Campaign。

請注意，在Campaign v8中，將不再允許連線使用者/密碼（亦稱為原生驗證）。 **Adobe建議在Campaign v7.3.5中執行此移轉，以便能夠順利移轉至Campaign v8。**

本文詳細說明將技術運運算元移轉至Adobe Developer主控台上的技術帳戶所需的步驟。

## 哪些部分有所變更？{#move-to-ims-changes}

透過Campaign Classic，所有一般使用者都可以透過AdobeAdobe Campaign System (IMS)，使用其Adobe ID連線至Identity Management使用者端主控台。 但是，使用者/密碼連線仍然可用。 Campaign v8將不再允許此行為。

此外，為了強化安全性和驗證程式，Adobe Campaign使用者端應用程式現在直接使用IMS技術帳戶權杖呼叫Campaign API。 技術操作員的移轉詳情請參閱中提供的專屬文章 [此頁面](ims-migration.md).

此變更已適用於Campaign Classic v7，並且將 **強制** 以移至Campaign v8。

## 您有受到影響嗎？{#migrate-ims-impacts}

此程式適用於尚未使用Adobe ID連線至Campaign的所有Campaign使用者。

如果貴組織中的操作員使用其登入/密碼（亦即）連線至Campaign使用者端主控台， 原生驗證)，您會受到影響，應將這些運運算元移轉至Adobe IMS，如下所述。

移轉至 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"} 是確保環境安全且標準化的安全性必要條件，因為大部分其他Adobe Experience Cloud解決方案和應用程式皆已在IMS上。

## 如何移轉託管和Managed Services環境？ {#ims-migration-procedure}

### 先決條件 {#ims-migration-prerequisites}

在開始移轉程式之前，您必須聯絡您的Adobe轉換經理(適用於Managed Services客戶)，或Adobe客戶服務（適用於其他託管客戶），以便Adobe技術團隊可以移轉您現有的操作員群組和AdobeIdentity Management System (IMS)的已命名許可權。

### 主要步驟 {#ims-migration-steps}

以下列出此移轉的關鍵步驟：

1. Adobe會將您的環境升級至Campaign v7.3.5。
1. 升級後，您仍然可以透過兩種方法建立新使用者，以原生使用者身分或透過IMS。
1. 您的內部Campaign管理員必須向Campaign使用者端主控台上的所有原生使用者新增唯一電子郵件，並在完成後向您的Adobe代表/客戶服務確認。  此步驟的詳細資訊，請參閱 [本節](#ims-migration-id).
1. 請與您的Adobe代表/客戶服務合作，確保Adobe的日期，以針對您的非技術使用者（操作員）和產品設定檔執行自動移轉。 此步驟需要一小時的時段，您的任何服務都不需要停機時間。
1. 您的內部Campaign管理員會驗證這些變更，並提供簽核服務。 移轉後，您再也不能建立任何以他的登入和密碼進行驗證的進一步運運算元。

您也可以將技術運運算元移轉至Adobe Developer主控台，詳情請參閱 [此技術檔案](ims-migration.md).

移轉一旦完成，請洽詢您的Adobe轉換經理(適用於Managed Services使用者)，或Adobe客戶服務（適用於託管客戶）。 Adobe接著將移轉標籤為完成。 接著您的環境就會受到保護並標準化。


## 如何移轉混合及內部部署環境？ {#ims-migration-procedure-on-prem}

以下列出此移轉的關鍵步驟：

1. 將您的環境升級至Campaign v7.3.5。
1. 升級後，您仍然可以透過兩種方法建立新使用者，以原生使用者身分或透過IMS。
1. 您的內部Campaign管理員必須設定Adobe IMS，如所述 [本節](../../integrations/using/configuring-ims.md).
1. 然後新增唯一電子郵件至Campaign使用者端主控台上的所有原生使用者。 此步驟的詳細資訊，請參閱 [本節](#ims-migration-id).
1. 在Adobe Admin Console中建立使用者和產品設定檔，如所述 [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html){target="_blank"}.
1. 啟用 **與Adobe ID連結** 所有運運算元的選項。
1. 為您的連線實作Adobe IMS，如所述 [此頁面](../../integrations/using/implementing-ims.md).

您也可以將技術運運算元移轉至Adobe Developer主控台，詳情請參閱 [此技術檔案](ims-migration.md).


## 常見問題集 {#ims-migration-faq}

### 何時可以開始移轉？ {#ims-migration-start}

移轉至「 」的建議 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"} 是將您的環境升級至Campaign Classicv7.3.5。

升級至Campaign Classicv7.3.5後，您就可以在Stage環境中開始IMS移轉，並據此規劃生產環境。

### 組建版本升級至Campaign Classic v7.3.5後會發生什麼事？ {#ims-migration-after-upgrade}

環境升級至Campaign Classicv7.3.5後，您就可以開始轉變至 [AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}.

### 移轉何時完成？ {#ims-migration-end}

使用者移轉及技術使用者移轉至AdobeIdentity Management System (IMS)後，您必須聯絡Adobe代表/客戶支援，讓Adobe將您的移轉標示為完成。

### 如何在移轉後建立使用者？ {#ims-migration-native}

Adobe建議升級至Campaign Classic v7.3.5後，僅建立IMS使用者。

身為Campaign管理員，您可以透過Adobe Admin Console和Campaign使用者端主控台將許可權授予組織的使用者。 使用者使用其Adobe ID登入Adobe Campaign。 瞭解如何在中使用IMS設定許可權 [Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html){target="_blank"}.

### 如何為目前原生使用者新增電子郵件？ {#ims-migration-id}

身為Campaign管理員，您必須從使用者端主控台新增電子郵件ID至所有原生使用者。 若要執行此作業，請依照下列步驟操作：

1. 連線到使用者端主控台並瀏覽至 **管理>存取管理>操作者**.
1. 在運運算元清單中選取要更新的運運算元。
1. 輸入操作員的電子郵件，在 **聯絡方式** 運運算元表單的區段。
1. 儲存您的變更。

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### 如何透過IMS登入Campaign？ {#ims-migration-log}

瞭解如何使用您的Adobe ID連線至Campaign，位於 [本節](../../integrations/using/implementing-ims.md).

### 此移轉期間是否會有停機時間？ {#ims-migration-downtime}

對於託管和Managed Services客戶，若要完成移轉（移轉使用者和產品設定檔），Adobe需要一小時的時間，您的任何執行個體（工作流程等）都不需要停機時間。

在這段時間內，所有Campaign使用者都必須登出，並在完成移轉至IMS後使用Adobe ID登回。

Adobe強烈建議所有使用者在移轉期間登出。

### 我組織中的使用者已在使用IMS，我仍需要執行IMS移轉嗎？{#ims-migration-needed}

此移轉包括兩個方面：一般使用者移轉（加上產品設定檔）和技術使用者移轉（用於自訂程式碼的API）。

如果您的所有使用者（Campaign運運算元）都在IMS上，您仍需要聯絡您的Adobe代表/客戶支援以計畫產品設定檔移轉。 您還需要移轉可能在自訂程式碼中使用的技術使用者。 在[本頁](ims-migration.md)中瞭解更多。

## 有用的連結 {#ims-useful-links}

* [將技術使用者移轉至Adobe Developer主控台](ims-migration.md)
* [Adobe Campaign v8發行說明](../../rn/using/latest-release.md)
* [什麼是AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/cn/enterprise/using/identity.html){target="_blank"}
