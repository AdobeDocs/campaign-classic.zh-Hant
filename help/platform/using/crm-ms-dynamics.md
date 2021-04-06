---
solution: Campaign Classic
product: campaign
title: Campaign - Microsoft Dynamics CRM Connector
description: Connect Campaign和Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
translation-type: tm+mt
source-git-commit: 37802e52f1d1d38d9c3d59c439f23114a594bfef
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 1%

---

# Connect Campaign和Microsoft Dynamics 365{#connect-to-msdyn}

在本頁中，您將學習如何將Campaign Classic連接至&#x200B;**Microsoft Dynamics CRM 365**。

可能的部署包括：

* 透過&#x200B;**Web API**（建議）。 請參閱下面的[部分，瞭解設定與Microsoft Dynamics連接的步驟。](#microsoft-dynamics-implementation-step)
* 具有&#x200B;**Office 365**。 請參閱[此視訊](#microsoft-dynamics-office-365)以瞭解設定此整合的關鍵步驟。
* 對於&#x200B;**內部部署**&#x200B;部署，請應用Office 365關鍵步驟。

資料同步通過專用的工作流活動執行。 [進一步瞭解](../../platform/using/crm-data-sync.md)。

## 實施步驟{#microsoft-dynamics-implementation-steps}

若要連接Microsoft Dynamics 365以透過&#x200B;**Web API**&#x200B;與Adobe Campaign合作，您必須套用下列步驟：

在Microsoft Dynamics CRM中：
1. 取得Microsoft Dynamics Client ID
1. 產生Microsoft Dynamics Client Secret
1. 設定權限
1. 建立應用程式使用者
1. 編碼私密金鑰

[本節提供更多資訊](#config-crm-microsoft)

Campaign Classic:
1. 建立新的外部帳戶
1. 使用Microsoft Dynamics設定來設定外部帳戶
1. 使用配置嚮導來映射表並同步枚舉
1. 建立同步工作流

[本節提供更多資訊](#configure-acc-for-microsoft)


>[!CAUTION]
> 將Adobe Campaign與Microsoft Dynamics連接時，您無法：
> * 安裝可變更CRM行為並導致與Adobe Campaign相容問題的外掛程式
> * 選擇多個枚舉

>



## 配置Microsoft Dynamics CRM {#config-crm-microsoft}

若要產生存取Token和金鑰以設定帳戶，您必須使用&#x200B;**全域管理員**&#x200B;憑證登入[Microsoft Azure目錄](https://portal.azure.com)。 然後依照下列步驟進行。

### 取得Microsoft Dynamics Client ID {#get-client-id-microsoft}

若要取得用戶端ID，您必須在Azure Active Directory中註冊應用程式。 用戶端ID與應用程式ID相同。

1. 導覽至「**Azure Active Directory >應用程式註冊**」，然後按一下「新增應用程式註冊&#x200B;**」。**
1. 指定可協助識別例項的唯一名稱，例如&#x200B;**adobecampaign`<instance identifier>`**。
1. 選擇&#x200B;**應用程式類型**&#x200B;作為&#x200B;**網頁應用程式/API**。
1. 對&#x200B;**登入URL**&#x200B;使用`http://localhost`。

儲存後，您會取得&#x200B;**應用程式ID**，此為促銷活動的用戶端識別碼。

進一步瞭解[本頁](https://docs.microsoft.com/en-us/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)。

### 生成Microsoft Dynamics Client密碼{#config-client-secret-microsoft}

用戶端密碼是用戶端ID專屬的金鑰。 若要取得憑證金鑰識別碼，請遵循下列步驟：

1. 導覽至&#x200B;**Azure Active Directory > App Registrations**，然後選取先前建立的應用程式。
1. 按一下&#x200B;**證書和密碼**。
1. 按一下「上傳憑證&#x200B;**」，然後瀏覽並上傳產生的公開憑證。**
1. 若要產生憑證，您可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

1. 按一下&#x200B;**manifest**&#x200B;連結，取得&#x200B;**憑證金鑰識別碼**&#x200B;和&#x200B;**金鑰ID**。

### 配置權限{#config-permissions-microsoft}

您必須為已建立的應用程式設定&#x200B;**必要權限**。

1. 導覽至&#x200B;**Azure Active Directory > App Registrations**，然後選取先前建立的應用程式。
1. 按一下左上角的&#x200B;**Settings**。
1. 在&#x200B;**必要權限**&#x200B;上，按一下&#x200B;**新增**&#x200B;和&#x200B;**選擇API > Dynamics CRM Online**。
1. 然後，按一下「選擇&#x200B;****」，啟用「作為組織用戶訪問Dynamics 365」複選框，然後按一下「選擇&#x200B;****」。****

### 建立應用程式使用者{#create-app-user-microsoft}

應用程式使用者是上述註冊之應用程式將使用的使用者。 使用上述註冊的應用程式對Microsoft Dynamics所做的任何變更，都將透過此使用者完成。

**步驟1**:在azure Active Directory上建立非互動式使用者

1. 按一下「**Azure Active Directory >用戶**」 ，然後按一下「新用戶&#x200B;**」。**
1. 指定您要使用的正確名稱，且使用者名稱應為電子郵件格式。
1. 在&#x200B;**目錄角色**&#x200B;中選擇&#x200B;**Dynamics 365 Administrator**。

**步驟2**:為已建立的使用者指派適當的授權

1. 在[Microsoft Azure](https://portal.azure.com)中，按一下&#x200B;**管理應用程式**。
1. 前往「**使用者>作用中使用者**」，然後按一下新建立的使用者。
1. 按一下「編輯產品授權&#x200B;**」，然後選取「Dynamics 365客戶參與計畫**」。****
1. 按一下 **關閉**。

**步驟3**:在Dynamics CRM上建立應用程式使用者

1. 從[Microsoft Azure](https://portal.azure.com)導覽至&#x200B;**設定>安全性>使用者**。
1. 按一下下拉式清單，選擇&#x200B;**應用程式用戶** ，然後按一下&#x200B;**新建**。
1. 使用與上述Active Directory上建立的用戶相同的用戶名

   >[!NOTE]
   >
   >使用相同名稱會引發重複的金鑰錯誤，因此，在我們確認是否需要此步驟之前，請使用不同的使用者名稱並繼續。

1. 為[您先前建立的應用程式指派&#x200B;**應用程式ID**。](#get-client-id-microsoft)
1. 按一下&#x200B;**管理角色**&#x200B;並選擇&#x200B;**系統管理員**&#x200B;角色給用戶。

## 設定促銷活動{#configure-acc-for-microsoft}

若要連接Microsoft Dynamics 365和Campaign，您必須在Campaign中建立並設定專用的外部帳戶。

1. 導覽至&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。

1. 建立新外部帳戶，選擇類型&#x200B;**[!UICONTROL Microsoft Dynamics CRM]**&#x200B;和&#x200B;**[!UICONTROL Enable]**&#x200B;選項。

1. 選擇&#x200B;**[!UICONTROL Web API]**&#x200B;部署類型：

   Adobe Campaign Classic支援Dynamics 365 REST介面與OAuth通訊協定，以驗證&#x200B;**[!UICONTROL Certificate]**&#x200B;或&#x200B;**[!UICONTROL Password Credentials]**。

   使用Azure目錄中先前定義的[設定來設定外部帳戶。](#get-client-id-microsoft)

   ![](assets/crm-ms-dynamics-ext-account.png)

   >[!NOTE]
   >
   >Microsoft Dynamics CRM外部帳戶配置在本節](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)中詳細說明。[

1. 按一下&#x200B;**[!UICONTROL Microsoft CRM configuration wizard...]**&#x200B;連結：Adobe Campaign會自動從Microsoft Dynamics資料範本中偵測表格。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 選擇要恢復的表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;開始建立相應的模式。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >要批准配置，必須斷開／重新連接到Adobe Campaign控制台。

   您可以檢查相符的資料結構是否可在Adobe Campaign使用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 按一下&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;連結，開始同步Adobe Campaign和Microsoft Dynamics之間的枚舉。

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign和Microsoft Dynamics現在已連接。 您可以在兩個系統之間設定資料同步。 請參閱[資料同步](../../platform/using/crm-data-sync.md)一節，瞭解更多資訊。

## 設定Microsoft Dynamics CRM Office 365整合{#microsoft-dynamics-office-365}

觀看此影片，瞭解如何在部署Office 365時，將Dynamics 365與Adobe Campaign Classic整合。

>[!VIDEO](https://video.tv.adobe.com/v/23837?quality=12)


## 支援的欄位資料類型{#ms-dyn-supported-types}

對於Microsoft Dynamics 365，以下列出支援／不支援的屬性類型：


| 屬性類型 | 支援 |
| --------------------------------------------------------------------------------- | --------- |
| 基本類型：布爾型，日期時間，小數，浮點型，雙精度，整數， bigint，字串 | 是 |
| 金錢（雙倍） | 是 |
| memo, entityname, primarykey, uniqueidentifier（作為字串） | 是 |
| 狀態、選擇清單（我們將可能的值儲存在枚舉中）、狀態（字串） | 是 |
| 擁有者（作為字串） | 是 |
| 查閱（僅單一實體參考查閱） | 是 |
| 客戶 | 否 |
| 關於 | 否 |
| PartyList | 否 |
| ManagedProperty | 否 |
