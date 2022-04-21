---
product: campaign
title: 市場活動 — MicrosoftDynamics CRM連接器
description: 瞭解如何連接活動和Microsoft動態
feature: Microsoft CRM Integration
exl-id: 26737940-b3ce-425c-9604-f4cefd19afaa
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 3%

---

# 連接市場活動和MicrosoftDynamics 365{#connect-to-msdyn}

![](../../assets/v7-only.svg)

在此頁中，您將學習如何將Campaign Classic連接到 **MicrosoftCRM 365**。

可能的部署通過 **Web API** （推薦）。 請參閱 [下面一節](#microsoft-dynamics-implementation-step) 瞭解與Microsoft動力建立聯繫的步驟。

資料同步通過專用工作流活動執行。 [了解更多資訊](../../platform/using/crm-data-sync.md)。

## 實施步驟{#microsoft-dynamics-implementation-steps}

將MicrosoftDynamics 365連接到Adobe Campaign **Web API**，您需要應用以下步驟：

在MicrosoftDynamics CRM中：
1. 獲取MicrosoftDynamics客戶端ID
1. 生成MicrosoftDynamics證書密鑰標識符和密鑰ID
1. 配置權限
1. 建立應用用戶
1. 對私鑰進行編碼

[在本節了解更多資訊](#config-crm-microsoft)

在Campaign Classic:
1. 新建外部帳戶
1. 使用MicrosoftDynamics設定配置外部帳戶
1. 使用配置嚮導映射表並同步枚舉
1. 建立同步工作流

[在本節了解更多資訊](#configure-acc-for-microsoft)


>[!CAUTION]
> 將Adobe Campaign與Microsoft動力公司連接時，不能：
> * 安裝可更改CRM行為並導致與Adobe Campaign的相容性問題的插件
> * 選擇多個枚舉


## 配置MicrosoftDynamics CRM {#config-crm-microsoft}

要生成訪問令牌和密鑰以設定帳戶，您需要登錄到 [MicrosoftAzure目錄](https://portal.azure.com) 使用 **全局管理員** 憑據。 然後按照下面介紹的步驟操作。

### 獲取MicrosoftDynamics客戶端ID {#get-client-id-microsoft}

若要獲取客戶端ID，您需要在Azure Active Directory中註冊應用。 客戶端ID與應用程式ID相同。

1. 導航到 **Azure Active Directory >應用程式註冊**，然後按一下  **新申請註冊**。
1. 指定可幫助標識實例的唯一名稱，如 **阿多貝卡姆`<instance identifier>`**。
1. 選擇 **應用程式類型** 如 **Web應用/API**。
1. 使用 `http://localhost` 為 **登錄URL**。

一旦你救了，你 **應用程式ID** 即市場活動的客戶端標識符。

在[本頁](https://docs.microsoft.com/powerapps/developer/common-data-service/walkthrough-register-app-azure-active-directory)中瞭解更多。

### 生成MicrosoftDynamics證書密鑰標識符和密鑰ID {#config-certificate-key-id}

獲取 **證書密鑰標識符(customKeyIdentifier)** 和 **密鑰ID(keyId)**，請執行以下步驟：

1. 導航到 **Azure Active Directory >應用程式註冊** 並選擇之前建立的應用程式。
1. 按一下 **證書和密碼**。
1. 按一下 **上載證書** 然後瀏覽並上載生成的公共證書。
1. 要生成證書，可以使用openssl。

   例如：

   ```
   - openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout '<'private key name'>' -out '<'public certificate name'>
   ```

   >[!NOTE]
   >
   >您可以更改天數，此處 `-days 365`，在代碼樣本中顯示較長的證書有效期。

1. 然後，需要將其編碼為base64。 為此，可以使用Base64編碼器的幫助或使用命令行 `base64 -w0 private.key` Linux。

1. 按一下 **清單** 連結以獲取 **證書密鑰標識符(customKeyIdentifier)** 和 **密鑰ID(keyId)**。

的 **證書密鑰標識符(customKeyIdentifier)** 和 **密鑰ID(keyId)** 以後需要使用證書配置您的MicrosoftDynamics CRM外部帳戶 **[!UICONTROL CRM O-Auth type]**。

### 配置權限 {#config-permissions-microsoft}

**步驟1**:配置 **所需權限** 建立的應用。

1. 導航到 **Azure Active Directory >應用程式註冊** 並選擇之前建立的應用程式。
1. 按一下 **設定** 左上角。
1. 開 **所需權限**&#x200B;按一下 **添加** 和 **選擇API > Dynamics CRM Online**。
1. 按一下 **選擇**&#x200B;啟用 **以組織用戶身份訪問Dynamics 365** 複選框，然後按一下 **選擇**。
1. 然後，從您的應用中，選擇 **清單** 下 **管理** 的子菜單。

1. 從 **清單** 編輯器，設定 `allowPublicClient` 屬性 `null` 至 `true` 按一下 **保存**。

**步驟2**:授予管理員許可

1. 導航到 **Azure Active Directory >企業應用程式**。

1. 選擇要向其授予租戶範圍管理員許可的應用程式。

1. 從左窗格菜單中，選擇 **權限** 在 **安全**。

1. 按一下 **授予管理員許可**。

有關此項的詳細資訊，請參閱 [Azure文檔](https://docs.microsoft.com/azure/active-directory/manage-apps/grant-admin-consent#grant-admin-consent-from-the-azure-portal)。

### 建立應用用戶 {#create-app-user-microsoft}

>[!NOTE]
>
> 此步驟是可選的 **[!UICONTROL Password credentials]** 驗證。

App用戶是上面註冊的應用程式將使用的用戶。 使用上述註冊的應用對Microsoft動態進行的任何更改都將通過此用戶完成。

**步驟1**:在azure active directory上建立非互動式用戶

1. 按一下 **Azure Active Directory >用戶** 按一下 **新用戶**。
1. 指定要使用的正確名稱，用戶名應為電子郵件格式。
1. 選擇 **Dynamics 365管理員** 的 **目錄角色**。

**步驟2**:為建立的用戶分配適當的許可證

1. 從 [MicrosoftAzure](https://portal.azure.com)，按一下 **管理應用**。
1. 轉到 **用戶>活動用戶** 並按一下新建立的用戶。
1. 按一下 **編輯產品許可證** 的 **Dynamics 365客戶接洽計畫**。
1. 按一下 **關閉**。

**步驟3**:在Dynamics CRM上建立應用程式用戶

1. 從 [MicrosoftAzure](https://portal.azure.com)，導航 **設定>安全性>用戶**。
1. 按一下下拉框，選擇 **應用程式用戶** 按一下 **新建**。
1. 使用與上面在Active Directory上建立的用戶相同的用戶名

   >[!NOTE]
   >
   >使用相同名稱會引發重複的密鑰錯誤，因此，在我們確認是否需要此步驟之前，請使用其他用戶名並繼續。

1. 分配 **應用程式ID** 為 [您之前建立的應用程式](#get-client-id-microsoft)。
1. 按一下 **管理角色** 選擇 **系統管理員** 角色。

## 設定 Campaign {#configure-acc-for-microsoft}

>[!NOTE]
>
> 將 [MicrosoftRDS](https://docs.microsoft.com/previous-versions/dynamicscrm-2016/developers-guide/dn281891%28v=crm.8%29#microsoft-dynamics-crm-2011-endpoint)，本地和Office 365類型的CRM部署不再與市場活動相容。 Adobe Campaign現在僅支援CRM版本的Web API部署 **動態CRM 365**。 [了解更多資訊](../../rn/using/deprecated-features.md#crm-connectors)。

要連接MicrosoftDynamics 365和市場活動，您需要建立和配置專用 **[!UICONTROL External Account]** 在競選中。

1. 導航到 **[!UICONTROL Administration > Platform > External accounts]**。

1. 選擇 **[!UICONTROL Microsoft Dynamics CRM]** 外部帳戶。 核取 **[!UICONTROL Enabled]** 選項。

1. 填寫連接MicrosoftDynamics 365和市場活動所需的資訊。

   >[!NOTE]
   >
   >MicrosoftDynamics CRM外部帳戶配置 **[!UICONTROL CRM O-Auth type]** 詳細 [此部分](../../installation/using/external-accounts.md#microsoft-dynamics-crm-external-account)。

   ![](assets/crm-ms-dynamics-ext-account.png)

1. 按一下&#x200B;**[!UICONTROL Microsoft CRM configuration wizard...]**&#x200B;連結。Adobe Campaign自動從Microsoft動態資料模板中檢測表。

   ![](assets/crm_connectors_msdynamics_02.png)

1. 選擇要恢復的表。

   ![](assets/crm_connectors_msdynamics_03.png)

1. 按一下 **[!UICONTROL Next]** 以開始建立相應的架構。

   ![](assets/crm_connectors_msdynamics_04.png)

   >[!NOTE]
   >
   >要批准配置，必須斷開/重新連接到Adobe Campaign控制台。

   您可以檢查匹配的資料架構是否在Adobe Campaign可用。

   ![](assets/crm_connectors_msdynamics_05.png)

1. 按一下 **[!UICONTROL Synchronizing enumerations...]** 連結以開始同步Adobe Campaign和Microsoft動態之間的枚舉。

   ![](assets/crm_connectors_msdynamics_06.png)

競選活動和Microsoft動力公司現在已建立聯繫。 可以設定兩個系統之間的資料同步。 在 [資料同步](../../platform/using/crm-data-sync.md) 的子菜單。

>[!NOTE]
>
> 您需要確保添加到允許清單中的兩個URL:伺服器URL和 `login.microsoftonline.com` 的子菜單。 有關如何配置URL權限的詳細資訊，請參閱此 [頁](../../installation/using/url-permissions.md)。

## 支援的欄位資料類型 {#ms-dyn-supported-types}

對於MicrosoftDynamics 365，下面列出了支援/不支援的屬性類型：


| 屬性類型 | 支援 |
| --------------------------------------------------------------------------------- | --------- |
| 基本類型：boolean，日期時間， decimal，浮點， double，雙精度， integer, bigint，字串 | 是 |
| 貨幣（雙倍） | 是 |
| memo、entityname、primarykey、uniqueidentifier（作為字串） | 是 |
| 狀態、選擇清單（我們將可能的值儲存在枚舉中）、狀態（字串） | 是 |
| owner（字串） | 是 |
| 查找（僅單個實體引用查找） | 是 |
| 客戶 | 否 |
| 關於 | 否 |
| 交易方清單 | 否 |
| 托管屬性 | 否 |
