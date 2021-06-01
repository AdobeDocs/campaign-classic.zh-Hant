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
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 4%

---

# 為 Adobe Experience Cloud 觸發器配置 Adobe I/O {#configuring-adobe-io}

>[!CAUTION]
>
>如果您透過oAuth驗證使用舊版Triggers整合，**您需要依照**&#x200B;下方所述移至Adobe I/O。 使用Campaign的舊版oAuth驗證模式(Campaign)將於2021年11月30日淘汰。 [瞭解更多](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>請注意，在移至[!DNL Adobe I/O]期間，某些傳入的觸發器可能會遺失。

## 必要條件 {#adobe-io-prerequisites}

此整合僅適用於&#x200B;**Campaign Classic20.3、20.2.4、19.1.8和[!DNL Gold Standard] 11版**。

開始實施前，請檢查您有：

* 有效的&#x200B;**組織標識符**:Identity Management系統(IMS)組織識別碼是Adobe Experience Cloud內的唯一識別碼，用於訪客ID服務和IMS單一登入(SSO)。 [瞭解更多](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **開發人員存取**&#x200B;至您的組織。  如果您需要要求IMS組織的系統管理員權限，請依照本頁](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)中詳細的[程式，為所有產品設定檔提供此存取權。

## 步驟1:建立/更新Adobe I/O項目{#creating-adobe-io-project}

1. 存取[!DNL Adobe I/O]並使用IMS組織的系統管理員權限登入。

   >[!NOTE]
   >
   > 請確定您已登入正確的組織入口網站。

1. 從執行個體設定檔案ims/authIMSTAClientId中擷取現有整合用戶端識別碼（用戶端ID）。 非現有或空屬性表示未配置客戶端標識符。

   >[!NOTE]
   >
   >如果您的用戶端識別碼為空，您可以直接在Adobe I/O中&#x200B;**[!UICONTROL Create a New project]**。

1. 使用擷取的用戶端識別碼來識別現有專案。 尋找與先前步驟擷取的用戶端識別碼相同的現有專案。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 選擇&#x200B;**[!UICONTROL + Add to Project]**，然後選擇&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在&#x200B;**[!UICONTROL Add an API]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Adobe Analytics]**。

   ![](assets/do-not-localize/adobe_io_2.png)

1. 選擇&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作為身份驗證類型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的用戶端ID空白，請選取&#x200B;**[!UICONTROL Generate a key pair]**&#x200B;以建立公開和私密金鑰組。

   接著，系統會自動下載金鑰，預設到期日為365天。 到期後，您需要建立新金鑰組並更新設定檔案中的整合。 使用選項2，您可以選擇手動建立並上傳到期日較長的&#x200B;**[!UICONTROL Public key]**。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 按一下 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 選擇任何現有的&#x200B;**[!UICONTROL Product profile]**，或視需要建立新的。 此&#x200B;**[!UICONTROL Product profile]**&#x200B;不需要權限。 有關[!DNL Analytics] **[!UICONTROL Product Profiles]**&#x200B;的詳細資訊，請參閱[Adobe Analytics檔案](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console)。

   然後，按一下&#x200B;**[!UICONTROL Save configured API]**。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 從您的專案中，選取&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;並複製&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;下的下列資訊：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O憑證將在12個月後到期。 您每年需要產生新的金鑰組。

## 步驟2:在Adobe Campaign {#add-credentials-campaign}中新增專案認證

若要在Adobe Campaign中新增專案認證，請在Adobe Campaign執行個體的所有容器上，以「neolane」使用者身分執行下列命令，以在執行個體設定檔案中插入&#x200B;**[!UICONTROL Technical Account]**&#x200B;認證。

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

私密金鑰應以base64 UTF-8格式編碼。 若要這麼做：

1. 使用在[步驟1中生成的私鑰：建立/更新Adobe I/O專案區段](#creating-adobe-io-project)。 私密金鑰必須與用來建立整合的金鑰相同。

1. 使用下列命令對私密金鑰進行編碼：```base64 ./private.key```。

   >[!NOTE]
   >
   >複製/貼上私密金鑰時，有時可自動新增額外的行。 請記得在對私密金鑰進行編碼前將其移除。

1. 使用以base64 UTF-8格式編碼的新產生私密金鑰執行上述命令。

## 步驟3:更新流水線標籤{#update-pipelined-tag}

要更新[!DNL pipelined]標籤，您需要更新身份驗證類型以Adobe I/O配置檔案&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的項目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```
