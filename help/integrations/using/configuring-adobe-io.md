---
solution: Campaign Classic
product: campaign
title: 為 Adobe Experience Cloud 觸發器配置 Adobe I/O
description: 瞭解如何為Adobe Experience Cloud觸發器配置Adobe I/O
audience: integrations
content-type: reference
topic-tags: adobe-experience-manager
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0abdbbc33350cf6ec85488483dadb177e685818b
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 5%

---


# 為 Adobe Experience Cloud 觸發器配置 Adobe I/O {#configuring-adobe-io}

>[!CAUTION]
>
>如果您使用舊版的觸發器透過驗證整合，**您需要移至Adobe I/O，如下所述**。 舊版驗證模式將於2021年4月30日淘汰。 [進一步瞭解](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)

## 必要條件 {#adobe-io-prerequisites}

此整合僅適用於&#x200B;**Campaign Classic 20.3發行版**&#x200B;起。

開始此實作前，請檢查您有：

* 有效的IMSOrgID:身分管理系統(IMS)組織識別碼是Adobe Experience Cloud中的唯一識別碼，例如VisitorID服務和IMS單一登入(SSO),
* a開發人員存取IMS組織。

>[!NOTE]
>
>如果您需要申請IMS組織的系統管理員權限，請依照本頁[中詳細說明的程式，為所有產品設定檔提供此存取權。](https://helpx.adobe.com/ca/enterprise/admin-guide.html/ca/enterprise/using/manage-developers.ug.html)


## 步驟1:建立／更新Adobe I/O專案{#creating-adobe-io-project}

1. 存取Adobe I/O，並與系統管理員登入IMSorg。

   >[!NOTE]
   >
   > 請確定您已登入正確的IMSorg入口網站。

1. 從例項設定檔案ims/authIMSTAClientId擷取現有整合用戶端ID。 非現有或空屬性表示未配置客戶端ID。

   >[!NOTE]
   >
   >如果您的用戶端ID為空白，您可以直接在Adobe I/O中&#x200B;**[!UICONTROL Create a New project]**。

1. 使用擷取的用戶端ID來識別現有專案。 尋找與前一步驟中擷取的用戶端ID相同的現有專案。

   ![](assets/do-not-localize/adobe_io_8.png)

1. 選擇&#x200B;**[!UICONTROL + Add to Project]**&#x200B;並選擇&#x200B;**[!UICONTROL API]**。

   ![](assets/do-not-localize/adobe_io_1.png)

1. 在&#x200B;**[!UICONTROL Add an API]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Adobe Analytics]**。

   ![](assets/do-not-localize/adobe_io_2.png)

1. 選擇&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;作為驗證類型。

   ![](assets/do-not-localize/adobe_io_3.png)

1. 如果您的用戶端ID空白，請選取&#x200B;**[!UICONTROL Generate a key pair]**&#x200B;以建立公用和私用鑰匙對。

   ![](assets/do-not-localize/adobe_io_4.png)

1. 上傳您的公開金鑰，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/do-not-localize/adobe_io_5.png)

1. 選擇名為&#x200B;**Analytics-&lt;組織名稱>**&#x200B;的產品設定檔，然後按一下&#x200B;**[!UICONTROL Save configured API]**。

   ![](assets/do-not-localize/adobe_io_6.png)

1. 從您的專案中，選擇&#x200B;**[!UICONTROL Service Account (JWT)]**&#x200B;並複製下列資訊：
   * **[!UICONTROL Client ID]**
   * **[!UICONTROL Client Secret]**
   * **[!UICONTROL Technical account ID]**
   * **[!UICONTROL Organization ID]**

   ![](assets/do-not-localize/adobe_io_7.png)

## 步驟2:在Adobe Campaign {#add-credentials-campaign}中新增專案認證

若要在Adobe Campaign中新增專案認證，請在Adobe Campaign執行個體的所有容器上，以&#39;neolane&#39;使用者身分執行下列命令，將&#x200B;**[!UICONTROL Technical Account]**&#x200B;認證插入執行個體設定檔。

```
nlserver config -instance:<instance name> -setimsjwtauth:Organization_Id/Client_Id/Technical_Account_ID[/Client_Secret[/Base64_encoded_Private_Key]]
```

>[!NOTE]
>
>您應將私密金鑰編碼為base64 UTF-8格式。 請記得在編碼新行之前，先從索引鍵中移除新行，但私密金鑰除外。 私密金鑰必須與用來建立整合的金鑰相同。

## 步驟3:更新流水線標籤{#update-pipelined-tag}

若要更新[!DNL pipelined]標籤，您需要將配置檔案&#x200B;**config-&lt; instance-name >.xml**&#x200B;中的驗證類型更新為Adobe I/O項目，如下所示：

```
<pipelined ... authType="imsJwtToken"  ... />
```
