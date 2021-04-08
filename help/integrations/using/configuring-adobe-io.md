---
solution: Campaign Classic
product: campaign
title: 為 Adobe Experience Cloud 觸發器配置 Adobe I/O
description: 瞭解如何為Adobe Experience Cloud Triggers配置Adobe I/O
audience: integrations
content-type: reference
index: y
internal: n
snippet: y
exl-id: ab30f697-3022-4a29-bbdb-14ca12ec9c3e
translation-type: tm+mt
source-git-commit: f3ca92325f70cb3b9cca1ec5f6b7ddb5a02f9159
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 4%

---

# 為 Adobe Experience Cloud 觸發器配置 Adobe I/O {#configuring-adobe-io}

>[!CAUTION]
>
>如果您使用舊版的觸發器整合（透過oAuth驗證）,**您必須依照**&#x200B;下方所述移至Adobe I/O。 含促銷活動的舊版驗證模式將於2021年11月30日淘汰。 [了解更多](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)
>
>請注意，在移至[!DNL Adobe I/O]期間，有些傳入的觸發器可能會遺失。

## 必要條件 {#adobe-io-prerequisites}

此整合僅適用於&#x200B;**Campaign Classic20.3、20.2.4、19.1.8和[!DNL Gold Standard] 11版**&#x200B;的開始。

開始此實作前，請檢查您有：

* 有效的&#x200B;**組織識別碼**:Identity Management系統(IMS)組織識別碼是Adobe Experience Cloud內的唯一識別碼，用於VisitorID服務和IMS單一登入(SSO)。 [了解更多](https://experienceleague.adobe.com/docs/core-services/interface/manage-users-and-products/organizations.html)
* a **您組織的開發人員存取權**。  如果您需要申請IMS組織的系統管理員權限，請依照本頁](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-developers.ug.html)中詳細說明的程式，為所有產品設定檔提供此存取權。[

## 步驟1:建立／更新Adobe I/O項目{#creating-adobe-io-project}

1. 存取[!DNL Adobe I/O]並使用系統管理員權限登入IMS組織。

   >[!NOTE]
   >
   > 請確定您已登入正確的組織入口網站。

1. 從例項設定檔案ims/authIMSTAClientId擷取現有整合用戶端識別碼（用戶端ID）。 非現有或空屬性表示未配置客戶機標識符。

   >[!NOTE]
   >
   >如果您的客戶識別碼為空，則可以直接在Adobe I/O中&#x200B;**[!UICONTROL Create a New project]**。

1. 使用擷取的用戶端識別碼來識別現有專案。 尋找與上一步驟中擷取的用戶端識別碼相同的現有專案。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 選擇&#x200B;**[!UICONTROL + Add to Project]**&#x200B;並選擇&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在&#x200B;**[!UICONTROL Add an API]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Adobe Analytics]**。

   ![](assets/do-not-localize/adobe_io_2.png)

1. 選擇&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作為驗證類型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的客戶端ID為空，請選擇&#x200B;**[!UICONTROL Generate a key pair]**&#x200B;以建立公用密鑰對和專用密鑰對。

   然後，系統會自動下載索引鍵，預設到期日為365天。 到期後，您將需要建立新的金鑰對，並更新設定檔中的整合。 使用選項2，您可以選擇手動建立並上傳期限較長的&#x200B;**[!UICONTROL Public key]**。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 按一下 **[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 選擇任何現有的&#x200B;**[!UICONTROL Product profile]**，或視需要建立新的。 此&#x200B;**[!UICONTROL Product profile]**&#x200B;不需要權限。 有關[!DNL Analytics] **[!UICONTROL Product Profiles]**&#x200B;的更多資訊，請參閱[Adobe Analytics文檔](https://experienceleague.adobe.com/docs/analytics/admin/admin-console/home.html#admin-console)。

   然後，按一下&#x200B;**[!UICONTROL Save configured API]**。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 在您的項目中，選擇&#x200B;**[!UICONTROL Adobe Analytics]**&#x200B;並複製&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;下面的以下資訊：

   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

>[!CAUTION]
>
>Adobe I/O憑證將於12個月後到期。 您每年需要產生新的索引鍵對。

## 步驟2:在Adobe Campaign添加項目憑據{#add-credentials-campaign}

要在Adobe Campaign添加項目憑據，請以「neolane」用戶身份在Adobe Campaign實例的所有容器上運行以下命令，以在實例配置檔案中插入&#x200B;**[!UICONTROL Technical Account]**&#x200B;憑據。

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID/<Client_Secret>/<Base64_encoded_Private_Key>
```

私密金鑰應編碼為base64 UTF-8格式。 若要這麼做：

1. 使用在[步驟1中生成的私鑰：建立／更新Adobe I/O項目部分](#creating-adobe-io-project)。 私密金鑰必須與用來建立整合的私密金鑰相同。

1. 使用下列命令編碼私密金鑰：```base64 ./private.key```。

   >[!NOTE]
   >
   >複製／貼上私密金鑰時，有時可自動新增額外的行。 請記得在編碼私密金鑰之前先移除它。

1. 使用您新產生的以base64 UTF-8格式編碼的私密金鑰來執行上述命令。

## 步驟3:更新流水線標籤{#update-pipelined-tag}

若要更新[!DNL pipelined]標籤，您需要將驗證類型更新為Adobe I/O配置檔案&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的項目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```
