---
product: campaign
title: Campaign - Microsoft Dynamics CRM聯結器
description: 瞭解如何連結Campaign和Microsoft Dynamics
feature: Microsoft CRM Integration
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '1111'
ht-degree: 3%

---

# 連線Campaign和Microsoft Dynamics 365{#connect-to-msdyn}



在本頁中，您將瞭解如何將Campaign Classic連結至 **Microsoft Dynamics CRM 365**.

可能的部署方式為透過 **Web API** （建議使用）。 請參閱 [下節](#microsoft-dynamics-implementation-step) 瞭解設定Microsoft Dynamics連線的步驟。

資料同步是透過專屬的工作流程活動來執行。 [了解更多](../../platform/using/crm-data-sync.md)。

## 實施步驟{#microsoft-dynamics-implementation-steps}

若要連線Microsoft Adobe Campaign Dynamics 365以透過 **Web API**，您必須套用下列步驟：

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
1. 使用設定精靈來對應表格並同步列舉
1. 建立同步工作流程

[在本節中瞭解更多](#configure-acc-for-microsoft)


>[!CAUTION]
> 將Adobe Campaign與Microsoft Dynamics連線時，您無法：
> * 安裝可變更CRM行為並導致與Adobe Campaign相容問題的外掛程式
> * 選取多個分項清單

## 設定Microsoft Dynamics CRM {#config-crm-microsoft}

若要產生存取權杖和金鑰以設定帳戶，您需要登入 [Microsoft Azure目錄](https://portal.azure.com) 使用 **全域管理員** 認證。 然後遵循以下概述的步驟。

### 取得Microsoft Dynamics使用者端ID {#get-client-id-microsoft}

若要取得使用者端ID，您必須在Azure Active Directory中註冊應用程式。 使用者端ID與應用程式ID相同。

1. 瀏覽至 **Azure Active Directory >應用程式註冊**，然後按一下  **新應用程式註冊**.
1. 提供唯一的名稱，以協助識別例項，例如 **adobecampaign`<instance identifier>`**.
1. 選擇 **應用程式型別** 作為 **網頁應用程式/API**.
1. 使用 `http://localhost` 的 **登入URL**.

儲存後，您會收到 **應用程式ID** 此專案為Campaign的使用者端識別碼。

在[本頁](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)中瞭解更多。

### 產生Microsoft Dynamics憑證金鑰識別碼和金鑰ID {#config-certificate-key-id}

若要取得 **憑證金鑰識別碼(customKeyIdentifier)** 和 **金鑰ID (keyId)**，請遵循下列步驟：

1. 瀏覽至 **Azure Active Directory >應用程式註冊** 並選取先前建立的應用程式。
1. 按一下 **憑證和密碼**.
1. 按一下 **上傳憑證** 然後瀏覽並上傳您產生的公開憑證。
1. 若要產生憑證，您可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >您可以在這裡變更天數 `-days 365`，在程式碼範例中取得較長的憑證有效期。

1. 接著，您需要以base64加以編碼。 要執行此操作，您可以使用Base64編碼器的說明或使用命令列 `base64 -w0 private.key` 適用於Linux。

1. 按一下 **資訊清單** 連結以取得 **憑證金鑰識別碼(customKeyIdentifier)** 和 **金鑰ID (keyId)**.

此 **憑證金鑰識別碼(customKeyIdentifier)** 和 **金鑰ID (keyId)** 稍後將需要使用憑證來設定您的Microsoft Dynamics CRM外部帳戶 **[!UICONTROL CRM O-Auth type]**.

### 設定許可權 {#config-permissions-microsoft}

**步驟1**：設定 **必要許可權** 針對已建立的應用程式。

1. 瀏覽至 **Azure Active Directory >應用程式註冊** 並選取先前建立的應用程式。
1. 按一下 **設定** 左上角。
1. 開啟 **必要許可權**，按一下 **新增** 和 **選取API > Dynamics CRM Online**.
1. 按一下 **選取**，啟用 **以組織使用者身分存取Dynamics 365** 核取方塊並按一下 **選取**.
1. 然後，從應用程式中選取 **資訊清單** 在 **管理** 功能表。

1. 從 **資訊清單** 編輯者，設定 `allowPublicClient` 屬性來源 `null` 至 `true` 並按一下 **儲存**.

**步驟2**：授予管理員同意

1. 瀏覽至 **Azure Active Directory >企業應用程式**.

1. 選取您要授與租使用者範圍管理同意的應用程式。

1. 從左窗格功能表中選取 **許可權** 在 **安全性**.

1. 按一下 **授予管理員同意**.

如需詳細資訊，請參閱 [Azure檔案](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal).

### 建立應用程式使用者 {#create-app-user-microsoft}

>[!NOTE]
>
> 此步驟是選填，適用於 **[!UICONTROL Password credentials]** 驗證。

應用程式使用者是上述註冊的應用程式將使用的使用者。 使用上述註冊的應用程式對Microsoft Dynamics所做的任何變更，都將透過此使用者完成。

**步驟1**：在azure active directory上建立非互動式使用者

1. 按一下 **Azure Active Directory >使用者** 並按一下 **新使用者**.
1. 提供您想要使用的適當名稱，且使用者名稱應為電子郵件格式。
1. 選擇 **Dynamics 365系統管理員** 在 **目錄角色**.

**步驟2**：將適當的授權指派給已建立的使用者

1. 從 [Microsoft Azure](https://portal.azure.com)，按一下 **管理應用程式**.
1. 前往 **使用者>作用中的使用者** 並按一下新建立的使用者。
1. 按一下 **編輯產品授權** 並選取 **Dynamics 365客戶參與計畫**.
1. 按一下 **關閉**。

**步驟3**：在Dynamics CRM上建立應用程式使用者

1. 從 [Microsoft Azure](https://portal.azure.com)，導覽至 **設定>安全性>使用者**.
1. 按一下下拉式清單，選取 **應用程式使用者** 並按一下 **新增**.
1. 使用與上述在Active Directory上建立的使用者相同的使用者名稱

   >[!NOTE]
   >
   >使用相同名稱會擲回重複的金鑰錯誤，因此在我們收到是否需要此步驟的確認之前，請使用不同的使用者名稱並繼續。
   >

1. 指派 **應用程式ID** 的 [您先前建立的應用程式](#get-client-id-microsoft).
1. 按一下 **管理角色** 並選擇 **系統管理員** 角色至使用者。

## 設定Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> 停止運作後 [Microsoft的RDS](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint)，內部部署和Office 365型別的CRM部署不再與Campaign相容。 Adobe Campaign現在僅支援CRM版本的Web API部署 **動態CRM 365**. [了解更多](../../rn/using/deprecated-features.md#crm-connectors)。

若要連線Microsoft Dynamics 365和Campaign，您需要建立並設定專用的 **[!UICONTROL External Account]** 在Campaign中。

1. 瀏覽至 **[!UICONTROL Administration > Platform > External accounts]**.

1. 選取 **[!UICONTROL Microsoft Dynamics CRM]** 外部帳戶。 核取 **[!UICONTROL Enabled]** 選項。

1. 填寫連線Microsoft Dynamics 365和Campaign所需的資訊。

   >[!NOTE]
   >
   >Microsoft Dynamics CRM外部帳戶設定，每個帳戶具有 **[!UICONTROL CRM O-Auth type]** 詳細資訊 [在本節中](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account).

   ![](assets/crm-ms-dynamics-ext-account.png)

1. 按一下 **[!UICONTROL Microsoft CRM configuration wizard...]** 連結。 Adobe Campaign會自動從Microsoft Dynamics資料範本偵測表格。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 選取要復原的資料表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 按一下 **[!UICONTROL Next]** 以開始建立對應的結構描述。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >若要核准設定，您必須中斷與Adobe Campaign主控台的連線/重新連線。

   您可以檢查相符的資料結構描述是否可以在Adobe Campaign中使用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 按一下 **[!UICONTROL Synchronizing enumerations...]** 開始在Adobe Campaign和Microsoft Dynamics之間同步分項清單的連結。

   ![](assets/crm_connectors_msdynamics_06.png)

Campaign與Microsoft Dynamics現已連線。 您可以設定兩個系統之間的資料同步。 進一步瞭解 [資料同步](../../platform/using/crm-data-sync.md) 區段。

>[!NOTE]
>
> 您必須確定將兩個URL新增至允許清單：伺服器URL和 `login.microsoftonline.com` 在伺服器設定中。 有關如何設定URL許可權的詳細資訊，請參閱此 [頁面](../../installation/using/url-permissions.md).

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
