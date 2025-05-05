---
product: campaign
title: Campaign - Microsoft Dynamics CRM聯結器
description: 瞭解如何連結Campaign和Microsoft Dynamics
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1104'
ht-degree: 2%

---

# 連線Campaign和Microsoft Dynamics 365{#connect-to-msdyn}



在此頁面中，您將瞭解如何將Campaign Classic連線至&#x200B;**Microsoft Dynamics CRM 365**。

可能的部署是透過&#x200B;**Web API** （建議使用）。 請參閱[下節](#microsoft-dynamics-implementation-step)以瞭解設定Microsoft Dynamics連線的步驟。

資料同步是透過專屬的工作流程活動來執行。 [了解更多](../../platform/using/crm-data-sync.md)。

## 實施步驟{#microsoft-dynamics-implementation-steps}

若要透過&#x200B;**Web API**&#x200B;連線Microsoft Dynamics 365以使用Adobe Campaign，您必須套用下列步驟：

在Microsoft Dynamics CRM中：
1. 取得Microsoft Dynamics使用者端ID
1. 產生Microsoft Dynamics憑證金鑰識別碼和金鑰ID
1. 設定許可權
1. 建立應用程式使用者
1. 編碼私密金鑰

[在本節中瞭解更多](#config-crm-microsoft)

Campaign Classic：
1. 建立新的外部帳戶
1. 使用Microsoft Dynamics設定設定外部帳戶
1. 使用組態輔助程式來對應表格並同步列舉
1. 建立同步工作流程

[在本節中瞭解更多](#configure-acc-for-microsoft)


>[!CAUTION]
> 將Adobe Campaign與Microsoft Dynamics連線時，您無法：
> * 安裝可變更CRM行為並導致與Adobe Campaign相容問題的外掛程式
> * 選取多個分項清單

## 設定Microsoft Dynamics CRM {#config-crm-microsoft}

若要產生存取權杖和金鑰以設定帳戶，您必須使用&#x200B;**全域系統管理員**&#x200B;認證登入[Microsoft Azure目錄](https://portal.azure.com)。 然後遵循以下概述的步驟。

### 取得Microsoft Dynamics使用者端ID {#get-client-id-microsoft}

若要取得使用者端ID，您必須在Azure Active Directory中註冊應用程式。 使用者端ID與應用程式ID相同。

1. 瀏覽至&#x200B;**Azure Active Directory >應用程式註冊**，然後按一下&#x200B;**新增應用程式註冊**。
1. 提供唯一的名稱，以協助識別執行個體，例如&#x200B;**adobecampaign`<instance identifier>`**。
1. 選擇&#x200B;**應用程式型別**&#x200B;做為&#x200B;**網頁應用程式/API**。
1. 使用`http://localhost`作為&#x200B;**登入URL**。

儲存之後，您會取得一個&#x200B;**應用程式識別碼**，此為促銷活動的使用者端識別碼。

在[本頁](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)中瞭解更多。

### 產生Microsoft Dynamics憑證金鑰識別碼和金鑰ID {#config-certificate-key-id}

若要取得&#x200B;**憑證金鑰識別碼(customKeyIdentifier)**&#x200B;和&#x200B;**金鑰識別碼(keyId)**，請遵循下列步驟：

1. 導覽至&#x200B;**Azure Active Directory >應用程式註冊**，然後選取先前建立的應用程式。
1. 按一下&#x200B;**憑證和密碼**。
1. 按一下&#x200B;**上傳憑證**，然後瀏覽並上傳您產生的公開憑證。
1. 若要產生憑證，您可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >您可以變更代碼範例中的天數（此處`-days 365`），以獲得較長的憑證有效期。

1. 接著，您需要以base64加以編碼。 若要這樣做，您可以使用Base64編碼器或使用Linux的命令列`base64 -w0 private.key`。

1. 按一下&#x200B;**資訊清單**&#x200B;連結以取得&#x200B;**憑證金鑰識別碼(customKeyIdentifier)**&#x200B;和&#x200B;**金鑰識別碼(keyId)**。

稍後將需要&#x200B;**憑證金鑰識別碼(customKeyIdentifier)**&#x200B;和&#x200B;**金鑰識別碼(keyId)**，才能使用憑證&#x200B;**[!UICONTROL CRM O-Auth type]**&#x200B;設定您的Microsoft Dynamics CRM外部帳戶。

### 設定許可權 {#config-permissions-microsoft}

**步驟1**：為已建立的應用程式設定&#x200B;**必要許可權**。

1. 導覽至&#x200B;**Azure Active Directory >應用程式註冊**，然後選取先前建立的應用程式。
1. 按一下左上方的&#x200B;**設定**。
1. 在&#x200B;**必要的許可權**&#x200B;上，按一下&#x200B;**新增**&#x200B;和&#x200B;**選取API > Dynamics CRM Online**。
1. 按一下&#x200B;**選取**，啟用&#x200B;**以組織使用者身分存取Dynamics 365**&#x200B;核取方塊，然後按一下&#x200B;**選取**。
1. 然後，從您的應用程式中，選取&#x200B;**管理**&#x200B;功能表下的&#x200B;**資訊清單**。

1. 從&#x200B;**資訊清單**&#x200B;編輯器中，將`allowPublicClient`屬性從`null`設定為`true`，然後按一下&#x200B;**儲存**。

**步驟2**：授予管理員同意

1. 瀏覽至&#x200B;**Azure Active Directory >企業應用程式**。

1. 選取您要授與租使用者範圍管理同意的應用程式。

1. 從左窗格功能表，選取&#x200B;**安全性**&#x200B;下的&#x200B;**許可權**。

1. 按一下&#x200B;**授予管理員同意**。

如需詳細資訊，請參閱[Azure檔案](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal)。

### 建立應用程式使用者 {#create-app-user-microsoft}

>[!NOTE]
>
> 此步驟是&#x200B;**[!UICONTROL Password credentials]**&#x200B;驗證的選用步驟。

應用程式使用者是上述註冊的應用程式將使用的使用者。 使用上述註冊的應用程式對Microsoft Dynamics所做的任何變更，都將透過此使用者完成。

**步驟1**：在azure active directory上建立非互動式使用者

1. 按一下&#x200B;**Azure Active Directory >使用者**，然後按一下&#x200B;**新增使用者**。
1. 提供您想要使用的適當名稱，且使用者名稱應為電子郵件格式。
1. 在&#x200B;**目錄角色**&#x200B;中選擇&#x200B;**Dynamics 365系統管理員**。

**步驟2**：將適當的授權指派給已建立的使用者

1. 從[Microsoft Azure](https://portal.azure.com)，按一下&#x200B;**管理應用程式**。
1. 前往&#x200B;**使用者>作用中的使用者**，然後按一下新建立的使用者。
1. 按一下&#x200B;**編輯產品授權**&#x200B;並選取&#x200B;**Dynamics 365客戶參與計畫**。
1. 按一下 **關閉**。

**步驟3**：在Dynamics CRM上建立應用程式使用者

1. 從[Microsoft Azure](https://portal.azure.com)，瀏覽至&#x200B;**設定>安全性>使用者**。
1. 按一下下拉式清單，選取&#x200B;**應用程式使用者**&#x200B;並按一下&#x200B;**新增**。
1. 使用與上述在Active Directory上建立的使用者相同的使用者名稱

   >[!NOTE]
   >
   >使用相同名稱會擲回重複的金鑰錯誤，因此在我們收到是否需要此步驟的確認之前，請使用不同的使用者名稱並繼續。
   >

1. 為您先前建立的[應用程式](#get-client-id-microsoft)指派&#x200B;**應用程式識別碼**。
1. 按一下&#x200B;**管理角色**&#x200B;並選擇使用者的&#x200B;**系統管理員**&#x200B;角色。

## 設定Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> 從Microsoft[&#128279;](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint)停用RDS後，內部部署和Office 365型別的CRM部署不再與Campaign相容。 Adobe Campaign現在只支援CRM版本&#x200B;**Dynamic CRM 365**&#x200B;的Web API部署。 [了解更多](../../rn/using/deprecated-features.md#crm-connectors)。

若要連線Microsoft Dynamics 365和Campaign，您需要在Campaign中建立並設定專用的&#x200B;**[!UICONTROL External Account]**。

1. 瀏覽至&#x200B;**[!UICONTROL Administration > Platform > External accounts]**。

1. 選取&#x200B;**[!UICONTROL Microsoft Dynamics CRM]**&#x200B;外部帳戶。 核取 **[!UICONTROL Enabled]** 選項。

1. 填寫連線Microsoft Dynamics 365和Campaign所需的資訊。

   >[!NOTE]
   >
   >本節[&#128279;](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)中詳細說明每個&#x200B;**[!UICONTROL CRM O-Auth type]**&#x200B;的Microsoft Dynamics CRM外部帳戶組態。

   ![](assets/crm-ms-dynamics-ext-account.png)

1. 按一下&#x200B;**[!UICONTROL Microsoft CRM configuration assistant...]**&#x200B;連結。 Adobe Campaign會自動從Microsoft Dynamics資料範本偵測表格。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 選取要復原的資料表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;開始建立對應的結構描述。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >若要核准設定，您必須中斷與Adobe Campaign主控台的連線/重新連線。

   您可以檢查相符的資料結構描述是否可以在Adobe Campaign中使用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 按一下&#x200B;**[!UICONTROL Synchronizing enumerations...]**&#x200B;連結，開始在Adobe Campaign和Microsoft Dynamics之間同步列舉。

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign與Microsoft Dynamics現已連線。 您可以設定兩個系統之間的資料同步。 在[資料同步處理](../../platform/using/crm-data-sync.md)一節中瞭解更多資訊。

>[!NOTE]
>
> 您必須確定將兩個URL新增至允許清單：伺服器URL和伺服器設定中的`login.microsoftonline.com`。 如需如何設定URL許可權的詳細資訊，請參閱此[頁面](../../installation/using/url-permissions.md)。

## 支援的欄位資料型別 {#ms-dyn-supported-types}

對於Microsoft Dynamics 365，支援/不支援的屬性型別列於下方：


| 屬性型別 | 支援 |
| --------------------------------------------------------------------------------- | --------- |
| 基本型別：布林值、日期時間、小數、浮點數、雙精度、整數、bigint 、字串 | 是 |
| 金錢（雙倍） | 是 |
| memo， entityname， primarykey， uniqueidentifier （字串） | 是 |
| 狀態、挑選清單（我們會將可能的值儲存在列舉中）、狀態（字串） | 是 |
| 所有者（字串） | 是 |
| 查詢（僅限單一實體參考查詢） | 是 |
| 客戶 | 否 |
| 相關 | 否 |
| PartyList | 否 |
| ManagedProperty | 否 |
| 多選選項集 | 否 |
