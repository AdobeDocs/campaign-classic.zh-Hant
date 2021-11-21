---
product: campaign
title: Campaign - Microsoft Dynamics CRM Connector
description: 連線Campaign和Microsoft Dynamics
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: e719c8c94f1c08c6601b3386ccd99d250c9e606b
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 3%

---

# 連線Campaign和Microsoft Dynamics 365{#connect-to-msdyn}

![](../../assets/common.svg)

在本頁面中，您將學習如何將Campaign Classic連結至 **Microsoft Dynamics CRM 365**.

可能的部署是通過 **網頁API** （建議）。 請參閱 [下節](#microsoft-dynamics-implementation-step) 了解設定與Microsoft Dynamics連線的步驟。

資料同步是透過專用的工作流程活動執行。 [深入瞭解](../../platform/using/crm-data-sync.md)。

## 實施步驟{#microsoft-dynamics-implementation-steps}

連接Microsoft Dynamics 365以透過 **網頁API**，您必須套用下列步驟：

在Microsoft Dynamics CRM中：
1. 取得Microsoft Dynamics用戶端ID
1. 產生Microsoft Dynamics憑證金鑰識別碼和金鑰ID
1. 設定權限
1. 建立應用程式使用者
1. 為私密金鑰編碼

[在本節了解更多資訊](#config-crm-microsoft)

Campaign Classic:
1. 建立新的外部帳戶
1. 使用Microsoft Dynamics設定設定外部帳戶
1. 使用配置嚮導映射表並同步枚舉
1. 建立同步工作流程

[在本節了解更多資訊](#configure-acc-for-microsoft)


>[!CAUTION]
> 將Adobe Campaign與Microsoft Dynamics連線時，您無法：
> * 安裝可變更CRM行為並導致與Adobe Campaign相容問題的外掛程式
> * 選擇多個枚舉


## 配置Microsoft Dynamics CRM {#config-crm-microsoft}

若要產生存取權杖和金鑰以設定帳戶，您必須登入 [Microsoft Azure目錄](https://portal.azure.com) 使用 **全局管理員** 憑證。 然後，請依照下列步驟操作。

### 取得Microsoft Dynamics用戶端ID {#get-client-id-microsoft}

若要取得用戶端ID，您必須在Azure Active Directory中註冊應用程式。 用戶端ID與應用程式ID相同。

1. 導覽至 **Azure Active Directory >應用程式註冊**，然後按一下  **新申請註冊**.
1. 指定可協助識別例項的唯一名稱，例如 **adobecampaign`<instance identifier>`**.
1. 選擇 **應用程式類型** as **網頁應用程式/ API**.
1. 使用 `http://localhost` for **登入URL**.

儲存後，您會 **應用程式ID** 這是Campaign的用戶端識別碼。

在[本頁](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)中瞭解更多。

### 產生Microsoft Dynamics憑證金鑰識別碼和金鑰ID {#config-certificate-key-id}

若要取得 **憑證金鑰識別碼(customKeyIdentifier)** 和 **金鑰ID(keyId)**，請遵循下列步驟：

1. 導覽至 **Azure Active Directory >應用程式註冊** 並選擇先前建立的應用程式。
1. 按一下 **憑證和密碼**.
1. 按一下 **上傳憑證** 然後瀏覽並上傳產生的公開憑證。
1. 若要產生憑證，您可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >您可以在此處變更天數 `-days 365`，在程式碼範例中取得較長憑證有效期。

1. 然後，您需要將其編碼為base64。 要執行此操作，可以使用Base64編碼器的幫助或使用命令行 `base64 -w0 private.key` Linux版。

1. 按一下 **資訊清單** 連結以取得 **憑證金鑰識別碼(customKeyIdentifier)** 和 **金鑰ID(keyId)**.

此 **憑證金鑰識別碼(customKeyIdentifier)** 和 **金鑰ID(keyId)** 後續將需要，才能使用憑證來設定您的Microsoft Dynamics CRM外部帳戶 **[!UICONTROL CRM O-Auth type]**.

### 設定權限 {#config-permissions-microsoft}

**步驟1**:設定 **必要權限** 針對已建立的應用程式。

1. 導覽至 **Azure Active Directory >應用程式註冊** 並選擇先前建立的應用程式。
1. 按一下 **設定** 左上角。
1. 開啟 **必要權限**，按一下 **新增** 和 **選取API > Dynamics CRM Online**.
1. 按一下 **選擇**，啟用 **以組織使用者身分存取Dynamics 365** 核取方塊和按一下 **選擇**.
1. 然後，從您的應用程式中選取 **資訊清單** 在 **管理** 功能表。

1. 從 **資訊清單** 編輯器，設定 `allowPublicClient` 屬性來源 `null` to `true` 按一下 **儲存**.

**步驟2**:授予管理員同意

1. 導覽至 **Azure Active Directory >企業應用程式**.

1. 選取您要授予租用戶範圍管理員同意的應用程式。

1. 從左窗格菜單中，選擇 **權限** 在 **安全性**.

1. 按一下 **授予管理員同意**.

如需詳細資訊，請參閱 [Azure檔案](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### 建立應用程式使用者 {#create-app-user-microsoft}

>[!NOTE]
>
> 此步驟是選用的 **[!UICONTROL Password credentials]** 驗證。

應用程式使用者是上述註冊的應用程式將使用的使用者。 使用上述註冊的應用程式對Microsoft Dynamics所做的任何變更，都會透過此使用者完成。

**步驟1**:在azure active directory上建立非互動用戶

1. 按一下 **Azure Active Directory >用戶** 按一下 **新用戶**.
1. 請指定您要使用的正確名稱，使用者名稱應為電子郵件格式。
1. 選擇 **Dynamics 365管理員** 在 **目錄角色**.

**步驟2**:為已建立的用戶分配適當的許可證

1. 從 [Microsoft Azure](https://portal.azure.com)，按一下 **管理應用程式**.
1. 前往 **使用者>作用中使用者** 然後按一下新建立的使用者。
1. 按一下 **編輯產品授權** ，然後選取 **Dynamics 365客戶參與計畫**.
1. 按一下 **關閉**。

**步驟3**:在Dynamics CRM上建立應用程式使用者

1. 從 [Microsoft Azure](https://portal.azure.com)，導覽至 **設定>安全性>使用者**.
1. 按一下下拉式清單，選取 **應用程式使用者** 按一下 **新增**.
1. 使用與上面在active directory上建立的用戶相同的用戶名

   >[!NOTE]
   >
   >使用相同名稱會擲回重複金鑰錯誤，因此在獲得是否需要此步驟的確認之前，請使用不同的使用者名稱並繼續。

1. 指派 **應用程式ID** for [您先前建立的應用程式](#get-client-id-microsoft).
1. 按一下 **管理角色** 並選擇 **系統管理員** 角色。

## 設定 Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> 將 [MicrosoftRDS](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint)，內部部署和Office 365類型的CRM部署不再與Campaign相容。 Adobe Campaign現在僅支援CRM版本的Web API部署 **動態CRM 365**. [深入瞭解](../../rn/using/deprecated-features.md#crm-connectors)。

若要連線Microsoft Dynamics 365和Campaign，您需要建立並設定專用的 **[!UICONTROL External Account]** 在Campaign中。

1. 導覽至 **[!UICONTROL Administration > Platform > External accounts]**.

1. 選取 **[!UICONTROL Microsoft Dynamics CRM]** 外部帳戶。 核取 **[!UICONTROL Enabled]** 選項。

1. 填寫連線Microsoft Dynamics 365和Campaign所需的資訊。

   >[!NOTE]
   >
   >Microsoft Dynamics CRM外部帳戶設定，每個 **[!UICONTROL CRM O-Auth type]** 詳細 [在本節](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. 按一下&#x200B;**[!UICONTROL Microsoft CRM configuration wizard...]**&#x200B;連結。Adobe Campaign會自動從Microsoft Dynamics資料範本中偵測表格。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 選擇要恢復的表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 按一下 **[!UICONTROL Next]** 以開始建立對應的結構。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >若要核准設定，您必須中斷連線/重新連線至Adobe Campaign主控台。

   您可以檢查相符的資料結構是否可在Adobe Campaign中使用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 按一下 **[!UICONTROL Synchronizing enumerations...]** 連結以開始同步Adobe Campaign和Microsoft Dynamics之間的列舉。

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign與Microsoft Dynamics現已連線。 您可以在兩個系統之間設定資料同步。 了解更多 [資料同步](../../platform/using/crm-data-sync.md) 區段。

>[!NOTE]
>
> 您必須確定將兩個URL新增至允許清單：伺服器URL和 `login.microsoftonline.com` 在伺服器配置中。

## 支援的欄位資料類型 {#ms-dyn-supported-types}

下列為Microsoft Dynamics 365支援/不支援的屬性類型：


| 屬性類型 | 支援 |
| --------------------------------------------------------------------------------- | --------- |
| 基本類型：布林值，日期時間，小數，浮點數，雙精度，整數， bigint，字串 | 是 |
| 貨幣（雙倍） | 是 |
| memo, entityname , primarykey, uniqueidentifier（作為字串） | 是 |
| 狀態、選擇清單（我們將可能的值儲存在枚舉中）、狀態（字串） | 是 |
| 擁有者（作為字串） | 是 |
| 查閱（僅單一實體參考查閱） | 是 |
| 客戶 | 否 |
| 關於 | 否 |
| PartyList | 否 |
| ManagedProperty | 否 |
