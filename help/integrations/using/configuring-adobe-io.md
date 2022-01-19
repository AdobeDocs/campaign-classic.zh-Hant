---
product: campaign
title: 為 Adobe Experience Cloud 觸發器配置 Adobe I/O
description: 瞭解如何為Adobe Experience Cloud Triggers配置Adobe I/O
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
>如果使用通過oAuth身份驗證的較舊版本的觸發器整合， **您需要移到Adobe I/O，如下所述**。
>請注意，在移動到 [!DNL Adobe I/O]，某些傳入觸發器可能丟失。
>
>具有市場活動的舊式身份驗證模式已在 **2021年10月20日**。 托管環境從擴展中受益，直到 **2022年5月25日**。 作為本地或混合型客戶，請與Adobe客戶服務部門聯繫，將支援範圍擴展到 **2022年5月**。 你必須 [提供OAuth應用程式的AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional) Adobe。

## 必要條件 {#adobe-io-prerequisites}

此整合僅應用於啟動 **Campaign Classic20.2.4及以上版本19.1.8和金標準11**。

在啟動此實施之前，請檢查您有：

* 有效 **組織標識符**:Identity Management系統(IMS)組織標識符是Adobe Experience Cloud內的唯一標識符，例如用於VisitorID服務和IMS單一登錄(SSO)。 [了解更多](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **開發人員訪問** 組織。 IMS組織的系統管理員需要 **將開發人員添加到單個產品配置檔案** 過程詳細 [此頁](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html) 為開發人員提供訪問 `Analytics - {tenantID}` 與觸發器關聯的Adobe Analytics產品的產品配置檔案。

## 步驟1:建立/更新Adobe I/O項目 {#creating-adobe-io-project}

1. 訪問 [!DNL Adobe I/O] 並使用IMS組織的開發人員訪問權限登錄。

   >[!NOTE]
   >
   > 確保您已登錄到正確的組織門戶。

1. 從實例配置檔案ims/authIMSTAClientId中提取現有整合客戶端標識符（客戶端ID）。 非現有或空屬性表示未配置客戶端標識符。

   >[!NOTE]
   >
   >如果客戶端標識符為空，則可以直接 **[!UICONTROL Create a New project]** Adobe I/O。

1. 使用提取的客戶端標識符標識現有項目。 查找具有與上一步提取的客戶端標識符相同的現有項目。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 選擇 **[!UICONTROL + Add to Project]** 選擇 **[!UICONTROL API]**。

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在 **[!UICONTROL Add an API]** 窗口，選擇 **[!UICONTROL Adobe Analytics]**。

   ![](assets/do-not-localize/adobe_io_2.png)

1. 選擇 **[!UICONTROL Service Account (JWT)]** 類型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果客戶端ID為空，請選擇 **[!UICONTROL Generate a key pair]** 建立公鑰和私鑰對。

   然後自動下載密鑰，預設到期日期為365天。 過期後，您需要建立新密鑰對並更新配置檔案中的整合。 使用選項2，您可以選擇手動建立和上載 **[!UICONTROL Public key]** 期限更長。

   >[!CAUTION]
   >
   >下載提示出現時，應保存config.zip檔案，因為您將無法再次下載該檔案。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 選擇任何現有 **[!UICONTROL Product profile]** 或根據需要建立新的。 無需對此權限 **[!UICONTROL Product profile]**。 有關 [!DNL Analytics] **[!UICONTROL Product Profiles]**，請參閱 [Adobe Analytics文檔](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console)。

   然後，按一下 **[!UICONTROL Save configured API]**。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 從項目中，選擇 **[!UICONTROL Adobe Analytics]** 並複製下列資訊 **[!UICONTROL Service Account (JWT)]**:

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O證書將在12個月後到期。 您每年需要生成新密鑰對。

## 步驟2:在Adobe Campaign添加項目憑據 {#add-credentials-campaign}

>[!NOTE]
>
>如果中的客戶端標識符不為空，則不需要此步驟 [步驟1:建立/更新Adobe I/O項目](#creating-adobe-io-project)。

私鑰應以base64 UTF-8格式編碼。 若要這麼做：

1. 使用中生成的私鑰 [步驟1:建立/更新Adobe I/O項目部分](#creating-adobe-io-project)。 私鑰必須與用於建立整合的私鑰相同。

1. 使用以下命令對私鑰進行編碼： `base64 ./private.key > private.key.base64`。 這將將base64內容保存到新檔案 `private.key.base64`。

   >[!NOTE]
   >
   >複製/貼上私鑰時，有時可以自動添加額外的行。 記住在對私鑰進行編碼之前將其刪除。

1. 從檔案複製內容 `private.key.base64`。

1. 通過SSH登錄到安裝Adobe Campaign實例的每個容器，並通過以下命令在Adobe Campaign添加項目憑據 `neolane` 。 這將插入 **[!UICONTROL Technical Account]** 實例配置檔案中的憑據。

   ```
   nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
   ```

## 第3步：更新流水線標籤 {#update-pipelined-tag}

>[!NOTE]
>
>如果中的客戶端標識符不為空，則不需要此步驟 [步驟1:建立/更新Adobe I/O項目](#creating-adobe-io-project)。

要更新 [!DNL pipelined] 標籤，您需要更新身份驗證類型以Adobe I/O配置檔案中的項目 **config-&lt;實例名>.xml** 如下：

```
<pipelined ... authType="imsJwtToken"  ... />
```

然後，運行 `config -reload` 然後重啟 [!DNL pipelined] 以便將更改考慮在內。
