---
product: campaign
title: 使用案例 — 建立電子郵件傳遞
description: 使用案例 — 建立電子郵件傳遞
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '747'
ht-degree: 1%

---

# 使用實例：建立電子郵件傳遞{#use-case-creating-an-email-delivery}



在此使用案例中，您將瞭解使用Adobe Campaign數位內容編輯器(DCE)設計電子郵件傳送的步驟。

我們的最終目標是使用個人化範本建立傳遞，範本包含：

* 收件者的直接地址（使用第一和第二名稱）
* 外部URL的兩種連結型別
* 映象頁面
* 網頁應用程式的連結

>[!NOTE]
>
>開始之前，您必須至少設定一個&#x200B;**HTML範本**，以裝載您未來傳遞的內容。
>
>在傳遞&#x200B;**[!UICONTROL Properties]**&#x200B;中，確定&#x200B;**[!UICONTROL Content editing mode]** （在&#x200B;**[!UICONTROL Advanced]**&#x200B;索引標籤中）設定為&#x200B;**[!UICONTROL DCE]**。 若要確保編輯器的最佳操作，請參閱[內容編輯最佳實務](content-editing-best-practices.md)。

## 步驟1 — 建立傳遞 {#step-1---creating-a-delivery}

若要建立新的傳遞，請將游標置於&#x200B;**行銷活動**&#x200B;索引標籤中，然後按一下&#x200B;**傳遞**。 接著，按一下現有傳遞清單上方的&#x200B;**建立**&#x200B;按鈕。 如需建立傳遞的詳細資訊，請參閱[此頁面](../../delivery/using/about-email-channel.md)。

![](assets/delivery_step_1.png)

## 步驟2 — 選取範本 {#step-2---selecting-a-template}

選取傳遞範本，然後為您的傳遞命名。 此名稱將僅對Adobe Campaign主控台的使用者可見，不會由您的收件者可見，不過此標題將顯示在您的傳遞清單中。 按一下&#x200B;**[!UICONTROL Continue]**。

![](assets/dce_delivery_model.png)

## 步驟3 — 選取內容 {#step-3---selecting-a-content}

數位內容編輯器提供各種現成可用的範本，其結構各異（欄、文字區域等）。

選取您要使用的內容範本，然後按一下「**[!UICONTROL Start with the selected content]**」按鈕，以在建立的傳遞中顯示範本。

![](assets/dce_select_model.png)

您也可以選取&#x200B;**[!UICONTROL From a file]**，匯入在Adobe Campaign外部建立的HTML內容。

![](assets/dce_select_from_file_template.png)

您可以將此內容儲存為範本以供日後使用。 建立個人化內容範本後，您可以從範本清單中預覽它。 如需詳細資訊，請參閱[範本管理](template-management.md)。

>[!CAUTION]
>
>如果您使用&#x200B;**Adobe Campaign網頁介面**，您必須匯入包含HTML內容和相關影像的.zip檔案。

## 步驟4 — 設計訊息 {#step-4---designing-the-message}

* 顯示收件者的第一和第二個名稱

  若要將收件者的第一和第二個名稱插入傳遞中的文字欄位，請按一下您選擇的文字欄位，然後將游標放在您要顯示它們的位置。 按一下彈出式工具列中的第一個圖示，然後按一下&#x200B;**[!UICONTROL Personalization block]**。 選取&#x200B;**[!UICONTROL Greetings]**，然後按一下&#x200B;**[!UICONTROL OK]**。

  ![](assets/dce_personalizationblock_greetings.png)

* 將連結插入影像中

  若要透過影像將傳遞收件者帶往外部地址，請按一下相關影像以顯示快顯工具列，將游標放在第一個圖示上，然後按一下&#x200B;**[!UICONTROL Link to an external URL]**。 如需詳細資訊，請參閱[新增連結](editing-content.md#adding-a-link)。

  ![](assets/dce_externalpage.png)

  在&#x200B;**URL**&#x200B;欄位中，使用以下格式&#x200B;**https://www.myURL.com**&#x200B;輸入連結的URL，然後確認。

  您可以使用視窗右側的區段隨時變更連結。

* 在文字中插入連結

  若要將外部連結整合至傳遞中的文字，請選取一些文字或文字區塊，然後按一下彈出式工具列中的第一個圖示。 按一下&#x200B;**[!UICONTROL Link to an external URL]**，在&#x200B;**[!UICONTROL URL]**&#x200B;欄位中輸入連結位址。 如需詳細資訊，請參閱[新增連結](editing-content.md#adding-a-link)。

  您可以使用視窗右側的區段隨時變更連結。

  >[!CAUTION]
  >
  >在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入的文字會取代原始文字。

* 新增映象頁面

  若要讓收件者在網頁瀏覽器中檢視您的傳送內容，您可以將映象頁面的連結整合至您的傳送中。

  按一下您想要看到連結張貼到的文字欄位。 按一下彈出式工具列中的第一個圖示，選取&#x200B;**[!UICONTROL Personalization block]**，然後選取&#x200B;**[!UICONTROL Link to Mirror Page (MirrorPage)]**。 按一下 **[!UICONTROL Save]** 確認。

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >個人化區塊標籤會自動取代傳送中的原始文字。

* 將連結整合至網頁應用程式

  數位內容編輯器可讓您從Adobe Campaign主控台整合至Web應用程式的連結，例如登入頁面或表單頁面。 如需詳細資訊，請參閱[網頁應用程式的連結](editing-content.md#link-to-a-web-application)。

  選取連結至Web應用程式的文字欄位，然後按一下第一個圖示。 選擇&#x200B;**[!UICONTROL Link to a Web application]**，然後按一下&#x200B;**網頁應用程式**&#x200B;欄位結尾的圖示來選取所需的應用程式。

  ![](assets/dce_webapp.png)

  按一下&#x200B;**儲存**&#x200B;以確認。

  >[!NOTE]
  >
  >此步驟需要您預先儲存至少一個Web應用程式。 您可在主控台的&#x200B;**[!UICONTROL Campaigns > Web applications]**&#x200B;索引標籤中找到這些專案。

## 步驟5 — 儲存傳遞 {#step-5---saving-the-delivery}

內容整合後，按一下&#x200B;**儲存**&#x200B;以儲存傳遞。 它現在會顯示在您在&#x200B;**[!UICONTROL Campaigns > Deliveries]**&#x200B;索引標籤中找到的傳遞清單中。
