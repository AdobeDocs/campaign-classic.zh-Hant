---
product: campaign
title: 為 Adobe Experience Cloud 觸發器配置 Adobe I/O
description: 了解如何為Adobe Experience Cloud Triggers設定Adobe I/O
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 966da123b30278817ca465ac5dfe1f733c4d6c5c
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 3%

---

# 為 Adobe Experience Cloud 觸發器配置 Adobe I/O {#configuring-adobe-io}

![](../../assets/v7-only.svg)

>[!CAUTION]
>
>如果您透過oAuth驗證使用舊版觸發器整合， **您需要依照下列說明移至Adobe I/O**.
>請注意，在此移至 [!DNL Adobe I/O]，某些傳入的觸發器可能會遺失。
>
>使用Campaign的舊版oAuth驗證模式已於 **2021年10月20日**. 托管環境可從擴充功能中獲益，直到 **2022年5月25日**. 身為內部部署或混合式客戶，請聯絡Adobe客戶服務以將支援延伸至 **2022年5月**. 您必須 [提供OAuth應用程式的AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) Adobe。

## 先決條件 {#adobe-io-prerequisites}

此整合僅適用於開始 **Campaign Classic20.2.4及更新版本、 19.1.8及Gold Standard 11版**.

開始實施前，請檢查您有：

* 有效 **組織識別碼**:Identity Management系統(IMS)組織識別碼是Adobe Experience Cloud內的唯一識別碼，用於訪客ID服務和IMS單一登入(SSO)。 [了解更多](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **開發人員存取** 加入您的組織。 IMS組織的系統管理員需要遵循 **將開發人員新增至單一產品設定檔** 詳細程式 [在本頁](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) 提供開發人員的存取權 `Analytics - {tenantID}` 與觸發器相關聯之Adobe Analytics產品的產品設定檔。

## 步驟1:建立/更新Adobe I/O專案 {#creating-adobe-io-project}

1. 存取 [!DNL Adobe I/O] 並使用IMS組織的開發人員存取權登入。

   >[!NOTE]
   >
   > 請確定您已登入正確的組織入口網站。

1. 從執行個體設定檔案ims/authIMSTAClientId中擷取現有的整合用戶端識別碼（用戶端ID）。 非現有或空屬性表示未配置客戶端標識符。

   >[!NOTE]
   >
   >如果用戶端識別碼為空，您可以直接 **[!UICONTROL Create a New project]** Adobe I/O。

1. 使用擷取的用戶端識別碼來識別現有專案。 尋找與先前步驟擷取的專案具有相同用戶端識別碼的現有專案。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 選擇 **[!UICONTROL + Add to Project]** 選擇 **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在 **[!UICONTROL Add an API]** 窗口，選擇 **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. 選擇 **[!UICONTROL Service Account (JWT)]** 作為驗證類型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的用戶端ID為空，請選取 **[!UICONTROL Generate a key pair]** 來建立公開和私密金鑰組。

   接著，系統會自動下載金鑰，預設到期日為365天。 到期後，您需要建立新金鑰組並更新設定檔案中的整合。 使用選項2，您可以選擇手動建立和上傳 **[!UICONTROL Public key]** 具有較長的到期日。

   >[!CAUTION]
   >
   >下載提示出現時，您應儲存config.zip檔案，因為您將無法再次下載。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 選擇任何現有 **[!UICONTROL Product profile]** 或視需要建立新的。 不需要權限 **[!UICONTROL Product profile]**. 如需 [!DNL Analytics] **[!UICONTROL Product Profiles]**，請參閱 [Adobe Analytics檔案](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   然後，按一下 **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. 從專案中選取 **[!UICONTROL Adobe Analytics]** 並複製下列資訊 **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O憑證將在12個月後到期。 您每年需要產生新的金鑰組。

## 步驟2:在Adobe Campaign中新增專案認證 {#add-credentials-campaign}

>[!NOTE]
>
>若您的用戶端識別碼在 [步驟1:建立/更新Adobe I/O專案](#creating-adobe-io-project).

私密金鑰應以base64 UTF-8格式編碼。 若要這麼做：

1. 使用在 [步驟1:建立/更新Adobe I/O專案區段](#creating-adobe-io-project). 私密金鑰必須與用來建立整合的金鑰相同。

1. 使用下列命令對私密金鑰進行編碼： `base64 ./private.key > private.key.base64`. 這會將base64內容儲存至新檔案 `private.key.base64`.

   >[!NOTE]
   >
   >複製/貼上私密金鑰時，有時可自動新增額外的行。 請記得在對私密金鑰進行編碼前將其移除。

1. 從檔案複製內容 `private.key.base64`.

1. 透過SSH登入安裝Adobe Campaign執行個體的每個容器，並執行下列命令以新增Adobe Campaign中的專案憑證 `neolane` 使用者。 這會插入 **[!UICONTROL Technical Account]** 執行個體設定檔案中的憑證。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## 步驟3:更新流水線標籤 {#update-pipelined-tag}

>[!NOTE]
>
>若您的用戶端識別碼在 [步驟1:建立/更新Adobe I/O專案](#creating-adobe-io-project).

更新 [!DNL pipelined] 標籤，您需要更新驗證類型，以Adobe I/O設定檔案中的專案 **config-&lt; instance-name >.xml** 如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然後，執行 `config -reload` 並重新開始 [!DNL pipelined] ，以便考慮變更。
