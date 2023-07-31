---
product: campaign
title: 為 Adobe Experience Cloud 觸發器配置 Adobe I/O
description: 瞭解如何設定Adobe Experience Cloud Triggers的Adobe I/O
feature: Triggers
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 4%

---

# 為 Adobe Experience Cloud 觸發器配置 Adobe I/O {#configuring-adobe-io}



>[!CAUTION]
>
>如果您透過oAuth驗證使用舊版的Triggers整合， **您必須依照下方所述移至Adobe I/O**.
>請注意，在此移動至期間 [!DNL Adobe I/O]，部分傳入的觸發程式可能會遺失。
>
>已淘汰具有Campaign的舊版oAuth驗證模式 **2021年10月20日**. 託管環境可從擴充功能受益，直到 **2022年5月25日**. 若為內部部署或混合客戶，請聯絡Adobe客戶服務，將支援延長至 **2022年5月**. 您必須 [提供Oauth應用程式的AppID](../../integrations/using/configuring-pipeline.md#step-optional) 以Adobe。

## 必要條件 {#adobe-io-prerequisites}

這項整合只適用於開始使用 **Campaign Classic 20.2.4及更高版本、19.1.8和Gold Standard 11版本**.

開始此實作前，請檢查您是否擁有：

* 有效的 **組織識別碼**：組織ID是Adobe Experience Cloud中的唯一識別碼，用於VisitorID服務和IMS單一登入(SSO)。 [了解更多](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=zh-Hant)
* a **開發人員存取權** 至您的組織。 組織的系統管理員需要遵循 **將開發人員新增至單一產品設定檔** 詳細程式 [在此頁面中](https://helpx.adobe.com/enterprise/using/manage-developers.html) 為提供開發人員存取權 `Analytics - {tenantID}` 與觸發器相關聯之Adobe Analytics產品的產品設定檔。

## 步驟1：建立/更新Adobe I/O專案 {#creating-adobe-io-project}

1. 存取 [!DNL Adobe I/O] 並使用貴組織的開發人員存取權登入。

   >[!NOTE]
   >
   > 請確定您已登入正確的組織入口網站。

1. 從執行個體設定檔案ims/authIMSTAClientId擷取現有的整合使用者端識別碼（使用者端ID）。 不存在或空白屬性表示未設定使用者端識別碼。

   >[!NOTE]
   >
   >如果您的使用者端識別碼為空白，您可以直接 **[!UICONTROL Create a New project]** 在Adobe I/O中。

1. 使用擷取的使用者端識別碼識別現有專案。 尋找使用者端識別碼與上一步驟所擷取者相同的現有專案。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 選取 **[!UICONTROL + Add to Project]** 並選擇 **[!UICONTROL API]**.

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在 **[!UICONTROL Add an API]** 視窗，選取 **[!UICONTROL Adobe Analytics]**.

   ![](assets/do-not-localize/adobe_io_2.png)

1. 選擇 **[!UICONTROL Service Account (JWT)]** 做為驗證型別。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的使用者端ID是空的，請選取 **[!UICONTROL Generate a key pair]** 以建立公開和私密金鑰組。

   之後，金鑰將會自動下載，預設到期日為365天。 到期後，您需要建立新的金鑰組並更新設定檔案中的整合。 使用選項2，您可以選擇手動建立並上傳 **[!UICONTROL Public key]** 到期日較長。

   有關如何替換即將到期的憑證金鑰組的逐步指南，請參閱 [此頁面](https://developer.adobe.com/developer-console/docs/guides/email-alerts/cert-expiry/#a-step-by-step-guide-to-replacing-expiring-certificate-key-pairs).


   >[!CAUTION]
   >
   >出現下載提示時，您應該儲存config.zip檔案，因為您將無法再次下載。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 選擇任何現有的 **[!UICONTROL Product profile]** 或視需要建立新檔案。 此許可權不需任何許可權 **[!UICONTROL Product profile]**. 如需詳細資訊，請參閱 [!DNL Analytics] **[!UICONTROL Product Profiles]**，請參閱 [Adobe Analytics檔案](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console).

   然後，按一下 **[!UICONTROL Save configured API]**.

   ![](assets/do-not-localize/adobe_io_6.png)

1. 在您的專案中，選取 **[!UICONTROL Adobe Analytics]** 並將下列資訊複製到 **[!UICONTROL Service Account (JWT)]**：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O憑證將在12個月後到期。 您需要每年產生新的金鑰組。

## 步驟2：在Adobe Campaign中新增專案認證 {#add-credentials-campaign}

>[!NOTE]
>
>如果您的使用者端識別碼在 [步驟1：建立/更新Adobe I/O專案](#creating-adobe-io-project).

私密金鑰應該以base64 UTF-8格式編碼。 若要這麼做：

1. 使用在中產生的私密金鑰 [步驟1：建立/更新Adobe I/O專案區段](#creating-adobe-io-project). 私密金鑰必須與用來建立整合的金鑰相同。

1. 使用下列命令編碼私密金鑰： `base64 ./private.key > private.key.base64`. 這會將base64內容儲存至新檔案 `private.key.base64`.

   >[!NOTE]
   >
   >複製/貼上私密金鑰時，有時會自動新增額外的行。 在編碼您的私密金鑰之前，請記得移除它。

1. 從檔案複製內容 `private.key.base64`.

1. 透過SSH登入已安裝Adobe Campaign執行個體的每個容器，並透過以下命令在Adobe Campaign中新增Project認證： `neolane` 使用者。 這將會插入 **[!UICONTROL Technical Account]** 執行個體組態檔中的認證。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## 步驟3：更新管線標籤 {#update-pipelined-tag}

>[!NOTE]
>
>如果您的使用者端識別碼在 [步驟1：建立/更新Adobe I/O專案](#creating-adobe-io-project).

更新 [!DNL pipelined] 標籤時，您必須更新驗證型別，才能將專案Adobe I/O在設定檔案中 **config-&lt; instance-name >.xml** 如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然後，執行 `config -reload` 以及重新啟動 [!DNL pipelined] 以納入變更。
