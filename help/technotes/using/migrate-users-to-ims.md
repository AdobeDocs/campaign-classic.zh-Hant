---
title: 移轉Campaign運運算元至AdobeIdentity Management系統(IMS)
description: 瞭解如何將Campaign運運算元移轉至AdobeIdentity Management系統(IMS)
exl-id: f01948c7-b523-492d-a4e8-67f4adde5fc5
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 2%

---

# 移轉Campaign運運算元至AdobeIdentity Management系統(IMS) {#migrate-users-to-ims}

為了強化安全性和驗證程式，Adobe Campaign強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至AdobeIdentity Management系統(IMS)。 所有運運算元都應該實作[AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}以連線至Campaign。

在[此頁面](ac-ims.md)中進一步瞭解此移轉。

## 哪些部分有所變更？ {#move-to-ims-changes}

透過Campaign Classic，所有一般使用者都可以透過AdobeAdobe Campaign System (IMS)，使用其Adobe ID連線至Identity Management使用者端主控台。 但是，使用者/密碼連線仍然可用。 Campaign v8將不再允許此行為。

此外，為了強化安全性和驗證程式，Adobe Campaign使用者端應用程式現在直接使用IMS技術帳戶權杖呼叫Campaign API。 技術運運算元的移轉作業在專用文章中有詳細說明，可在[此頁面](ims-migration.md)取得。

此變更已適用於Campaign Classic v7，且將為&#x200B;**強制性**&#x200B;才能移至Campaign v8。

Adobe可協助您進行這項移轉工作。 您可在下文中找到詳細的上下文和逐步指引。

## 您有受到影響嗎？{#migrate-ims-impacts}

此程式適用於尚未使用Adobe ID連線至Campaign的所有Campaign使用者。

如果貴組織中的操作員使用其登入/密碼（亦即）連線至Campaign使用者端主控台， 原生驗證)，您會受到影響，應將這些運運算元移轉至Adobe IMS，如下所述。

移轉至[AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}是安全必要條件，可讓您的環境安全且標準化，因為大部分其他Adobe Experience Cloud解決方案和應用程式已位於IMS上。

此變更適用於Campaign Classicv7.4.1 （和最新的[IMS移轉相容版本](ac-ims.md#ims-versions)）開始，且&#x200B;**強制性**&#x200B;為移至Adobe Campaign v8。


## 如何移轉託管和Managed Services環境？ {#ims-migration-procedure}

### 先決條件 {#ims-migration-prerequisites}

在開始移轉程式之前，您必須聯絡您的Adobe轉換經理(適用於Managed Services客戶)，或Adobe客戶服務（適用於其他託管客戶），以便Adobe技術團隊可以移轉您現有的操作員群組和AdobeIdentity Management System (IMS)的已命名許可權。

### 主要步驟 {#ims-migration-steps}

以下列出此移轉的關鍵步驟：

1. Adobe會將您的環境升級至Campaign v7.4.1 （或[與IMS移轉相容的版本](ac-ims.md#ims-versions)）。
1. 升級後，您仍然可以透過兩種方法建立新使用者，以原生使用者身分或透過IMS。
1. 您的內部Campaign管理員必須向Campaign使用者端主控台上的所有原生使用者新增唯一電子郵件，並在完成後向您的Adobe代表/客戶服務確認。  此步驟在[此區段](#ims-migration-id)中有詳細說明。
1. 請與您的Adobe代表/客戶服務合作，確保Adobe的日期，以針對您的非技術使用者（操作員）和產品設定檔執行自動移轉。 此步驟需要一小時的時段，您的任何服務都不需要停機時間。
1. 您的內部Campaign管理員會驗證這些變更，並提供簽核服務。 移轉後，您再也不能建立任何以他的登入和密碼進行驗證的進一步運運算元。

您也可以將技術操作員移轉至Adobe Developer Console，如[此技術檔案](ims-migration.md)中所述。

移轉一旦完成，請洽詢您的Adobe轉換經理(適用於Managed Services使用者)，或Adobe客戶服務（適用於託管客戶）。 Adobe接著將移轉標籤為完成。 接著您的環境就會受到保護並標準化。


## 如何移轉混合及內部部署環境？ {#ims-migration-procedure-on-prem}

以下列出此移轉的關鍵步驟：

1. 將您的環境升級至Campaign v7.4.1 （或[與IMS移轉相容的版本](#ims-versions)）。
1. 升級後，您仍然可以透過兩種方法建立新使用者，以原生使用者身分或透過IMS。
1. 您的內部Campaign管理員必須設定Adobe IMS，如[本節](../../integrations/using/configuring-ims.md)所述。
1. 然後新增唯一電子郵件至Campaign使用者端主控台上的所有原生使用者。 此步驟在[此區段](#ims-migration-id)中有詳細說明。
1. 在Adobe Admin Console中建立使用者和產品設定檔，如[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/manage-permissions.html?lang=zh-Hant){target="_blank"}中所述。
1. 為所有運運算元啟用&#x200B;**與Adobe ID連線**&#x200B;選項。
1. 實作您連線的Adobe IMS，如[此頁面](../../integrations/using/implementing-ims.md)所詳述。

您也可以將技術操作員移轉至Adobe Developer Console，如[此技術檔案](ims-migration.md)中所述。


## 常見問題集 {#ims-migration-faq}

### 如何在移轉後建立使用者？ {#ims-migration-native}

Adobe建議在升級至Campaign Classic v7.4.1 （或[與IMS移轉相容的版本](#ims-versions)）後，僅建立IMS使用者。
從Campaign v7.4.1開始，您可以更新執行個體設定，以防止建立原生運運算元，如[此頁面](impact-ims-migration.md)所詳述。

身為Campaign管理員，您可以透過Adobe Admin Console和Campaign使用者端主控台將許可權授予組織的使用者。 使用者使用其Adobe ID登入Adobe Campaign。 在[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/admin/permissions/gs-permissions.html?lang=zh-Hant){target="_blank"}中瞭解如何使用IMS設定許可權。

### 如何為目前原生使用者新增電子郵件？ {#ims-migration-id}

身為Campaign管理員，您必須從使用者端主控台新增電子郵件ID至所有原生使用者。 若要執行此作業，請依照下列步驟操作：

1. 連線到使用者端主控台，並瀏覽至&#x200B;**管理>存取管理>操作員**。
1. 在運運算元清單中選取要更新的運運算元。
1. 在操作員表單的&#x200B;**聯絡點**&#x200B;區段中，輸入操作員的電子郵件。
1. 儲存您的變更。

<!--You can also import a CSV file to update all your operator profiles with their email.-->


### 如何透過IMS登入Campaign？ {#ims-migration-log}

在[本節](../../integrations/using/implementing-ims.md)中瞭解如何使用您的Adobe ID連線至Campaign。

### 此移轉期間是否會有停機時間？ {#ims-migration-downtime}

對於託管和Managed Services客戶，若要完成移轉（移轉使用者和產品設定檔），Adobe需要一小時的時間，您的任何執行個體（工作流程等）都不需要停機時間。

在這段時間內，所有Campaign使用者都必須登出，並在完成移轉至IMS後使用Adobe ID登回。

Adobe強烈建議所有使用者在移轉期間登出。

### 我組織中的使用者已在使用IMS，我仍需要執行IMS移轉嗎？{#ims-migration-needed}

此移轉包括兩個方面：一般使用者移轉（加上產品設定檔）和技術使用者移轉（用於自訂程式碼的API）。

如果您的所有使用者（Campaign運運算元）都在IMS上，您仍需要聯絡您的Adobe代表/客戶支援以計畫產品設定檔移轉。 您還需要移轉可能在自訂程式碼中使用的技術使用者。 在[本頁](ims-migration.md)中瞭解更多。

### 如何檢視您的操作員的驗證型別？

瞭解如何在Campaign中檢視您的操作員驗證型別：

1. 從&#x200B;**總管**，存取&#x200B;**管理** `>` **存取管理** `>` **操作員**。

1. 以滑鼠右鍵按一下標題列，並選取&#x200B;**設定清單**&#x200B;功能表。

   ![](assets/ims_2.png)

1. 將&#x200B;**已停用的帳戶**&#x200B;和&#x200B;**驗證型別**&#x200B;新增為&#x200B;**輸出資料行**。

   ![](assets/ims_1.png)

您現在可以看到&#x200B;**操作員**&#x200B;及其&#x200B;**驗證型別**&#x200B;的清單。

![](assets/ims_3.png)


>[!MORELIKETHIS]
>
>* [將技術使用者移轉至Adobe Developer主控台](ims-migration.md)
>* [Adobe Campaign Classic v7發行說明](../../rn/using/latest-release.md)
>* [什麼是AdobeIdentity Management系統(IMS)](https://helpx.adobe.com/tw/enterprise/using/identity.html){target="_blank"}
