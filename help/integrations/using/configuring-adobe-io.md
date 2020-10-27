---
title: 為Adobe Experience Cloud觸發器配置Adobe IO
seo-title: 為Adobe Experience Cloud觸發器配置Adobe IO
description: 為Adobe Experience Cloud觸發器配置Adobe IO
seo-description: null
page-status-flag: never-activated
uuid: e2db7bdb-8630-497c-aacf-242734cc0a72
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
discoiquuid: 1c20795d-748c-4f5d-b526-579b36666e8f
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d15e953740b0a4dd8073b36fd59b4c4e44906340
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# 為Adobe Experience Cloud觸發器配置Adobe IO {#configuring-adobe-io}

先決條件配置包括：

* Adobe Campaign Classic建置ACC-19.1.9或ACC-20.2.1及更新版本。
* 有效的IMSOrgID。
* a開發人員存取IMS組織。您必須要求IMS組織的系統管理員權限，才能遵循本頁中詳細說明的程 [序](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html) ，以提供所有產品設定檔的存取權。

## 步驟1:建立／更新Adobe IO專案 {#creating-adobe-io-project}

1. 存取Adobe IO並與系統管理員一起登入IMSorg。

   >[!NOTE]
   >
   > 請確定您已登入正確的IMSorg入口網站。

1. 從例項設定檔案ims/authIMSTAClientId擷取現有整合用戶端ID。 非現有或空屬性表示未配置客戶端ID。

   >[!NOTE]
   >
   >如果您的用戶端ID是空的，您可以直接 **[!UICONTROL Create a New project]** 在Adobe IO中。

1. 您現在需要使用解壓縮的用戶端ID來識別現有的專案。 尋找與前一步驟中擷取的用戶端ID相同的現有專案。

   ![](assets/adobe_io_8.png)

1. 選擇 **[!UICONTROL + Add to Project]** 並選擇 **[!UICONTROL API]**。

   ![](assets/adobe_io_1.png)

1. 在窗口中 **[!UICONTROL Add an API]**&#x200B;選擇 **[!UICONTROL Adobe Analytics]**。

   ![](assets/adobe_io_2.png)

1. 選擇 **[!UICONTROL Service Account (JWT)]** 作為驗證類型。

   ![](assets/adobe_io_3.png)

1. 如果您的用戶端ID為空，請選 **[!UICONTROL Generate a key pair]** 取以建立公用和私用鑰匙對。

   ![](assets/adobe_io_4.png)

1. 上傳您的公開金鑰，然後按一下 **[!UICONTROL Next]**。

   ![](assets/adobe_io_5.png)

1. 選擇名為 **Analytics-&lt;組織名稱>的產品設定檔** ，然後按一下 **[!UICONTROL Save configured API]**。

   ![](assets/adobe_io_6.png)

1. 從您的專案中，選 **[!UICONTROL Service Account (JWT)]** 取並複製下列資訊：
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/adobe_io_7.png)

## 步驟2:在Adobe Campaign中新增專案認證 {#add-credentials-campaign}

若要在Adobe Campaign中新增專案認證，請以Adobe Campaign執行個體所有容器的Neolane使用者身分執行下列命令，以便在執行個體設定檔中 **[!UICONTROL Technical Account]** 插入認證。

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>您應將私密金鑰編碼為base64 UTF-8格式。 請記得在編碼新行之前，先從索引鍵中移除新行，但私密金鑰除外。 私密金鑰必須與用來建立整合的金鑰相同。

## 步驟3:更新流水線標籤 {#update-pipelined-tag}

若要更 [!DNL pipelined] 新標籤，您必須依照下列方式，在設定檔 **config-&lt; instance-name >.xml** 中，將驗證類型更新為Adobe IO專案：

```
<pipelined ... authType="imsJwtToken"  ... />
```

>[!NOTE]
>
>如果您使用舊版的「觸發器整合」使用舊版JWT Token，您也應新增Adobe IO API，以在第一步中詳細說明，以自動移轉至新的「觸發器驗證」。 [!DNL Adobe Analytics]
