---
product: campaign
title: 使用案例 — 建立電子郵件傳送
description: 使用案例 — 建立電子郵件傳送
feature: Web Apps, Web Forms, Landing Pages
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 1%

---

# 使用實例：建立電子郵件傳遞{#use-case-creating-an-email-delivery}

![](../../assets/common.svg)

在此使用案例中，您將學習使用Adobe Campaign數位內容編輯器(DCE)來設計電子郵件傳送的步驟。

我們的最終目標是使用包含下列內容的個人化範本建立傳遞：

* 收件者的直接地址（使用名字和第二名字）
* 外部URL的兩種連結
* 鏡像頁面
* Web應用程式的連結

>[!NOTE]
>
>開始之前，您至少必須有一個 **HTML範本** 已設定為托管未來傳送的內容。
>
>傳遞 **[!UICONTROL Properties]**，請確定 **[!UICONTROL Content editing mode]** (在 **[!UICONTROL Advanced]** ) **[!UICONTROL DCE]**. 若要確保編輯器的最佳操作，請參閱 [內容編輯最佳實務](content-editing-best-practices.md).

## 步驟1 — 建立傳遞 {#step-1---creating-a-delivery}

若要建立新傳送，請將游標置於 **行銷活動** 按一下 **傳遞**. 下一步按一下 **建立** 按鈕。 如需建立傳送的詳細資訊，請參閱 [本頁](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 步驟2 — 選取範本 {#step-2---selecting-a-template}

選取傳送範本，然後為您的傳送命名。 此名稱只會顯示給Adobe Campaign Console的使用者，而不會顯示給收件者，不過傳送清單中會顯示此標題。 按一下&#x200B;**[!UICONTROL Continue]**。

![](assets/dce_delivery_model.png)

## 步驟3 — 選取內容 {#step-3---selecting-a-content}

數位內容編輯器隨附各種現成可用的範本，其結構各異（欄、文字區域等）。

選取您要使用的內容範本，然後按一下 **[!UICONTROL Start with the selected content]** 按鈕，在建立的傳送中顯示範本。

![](assets/dce_select_model.png)

您也可以選取 **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

您可以將此內容儲存為範本，以供日後使用。 建立個人化內容範本後，您就可以從範本清單中預覽。 有關詳細資訊，請參閱 [範本管理](template-management.md).

>[!CAUTION]
>
>如果您使用 **Adobe Campaign網頁介面**，您必須匯入包含HTML內容和相關影像的.zip檔案。

## 步驟4 — 設計訊息 {#step-4---designing-the-message}

* 顯示收件者的名字和名字

   若要將收件者的第一和第二名稱插入傳遞中的文字欄位，請按一下您選取的文字欄位，然後將游標置於您要顯示這些名稱的位置。 按一下快顯工具列中的第一個圖示，然後按一下 **[!UICONTROL Personalization block]**. 選擇 **[!UICONTROL Greetings]**，然後按一下 **[!UICONTROL OK]**.

   ![](assets/dce_personalizationblock_greetings.png)

* 將連結插入影像中

   若要透過影像將傳送收件者帶至外部地址，請按一下相關影像以顯示快顯工具列，將游標置於第一個圖示上，然後按一下 **[!UICONTROL Link to an external URL]**. 有關詳細資訊，請參閱 [新增連結](editing-content.md#adding-a-link).

   ![](assets/dce_externalpage.png)

   在 **URL** 欄位，使用下列格式 **https://www.myURL.com**，然後確認。

   您可以隨時使用視窗右側的區段來變更連結。

* 將連結插入文字

   若要將外部連結整合到您傳送的文字中，請選取一些文字或一組文字，然後按一下快顯工具列中的第一個圖示。 按一下 **[!UICONTROL Link to an external URL]**，請在 **[!UICONTROL URL]** 欄位。 有關詳細資訊，請參閱 [新增連結](editing-content.md#adding-a-link).

   您可以隨時使用視窗右側的區段來變更連結。

   >[!CAUTION]
   >
   >在 **[!UICONTROL Label]** 欄位會取代原始文字。

* 添加鏡像頁

   若要讓收件者在網頁瀏覽器中檢視您的傳遞內容，您可以將鏡像頁面的連結整合到您的傳遞中。

   按一下您要查看所張貼連結的文字欄位。 按一下彈出工具欄中的第一個表徵圖，選擇 **[!UICONTROL Personalization block]**，然後 **[!UICONTROL Link to Mirror Page (MirrorPage)]**. 按一下 **[!UICONTROL Save]** 確認。

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >個人化區塊標籤會自動取代傳送中的原始文字。

* 整合Web應用程式的連結

   數位內容編輯器可讓您整合從Adobe Campaign主控台（例如登錄頁面或表單頁面）指向Web應用程式的連結。 有關詳細資訊，請參閱 [連結到Web應用程式](editing-content.md#link-to-a-web-application).

   為連結至Web應用程式的文字欄位，然後按一下第一個圖示。 選擇 **[!UICONTROL Link to a Web application]**，然後按一下 **Web應用程式** 欄位。

   ![](assets/dce_webapp.png)

   按一下 **儲存** 確認。

   >[!NOTE]
   >
   >此步驟要求您預先儲存至少一個Web應用程式。 這些位於 **[!UICONTROL Campaigns > Web applications]** 標籤。

## 步驟5 — 儲存傳送 {#step-5---saving-the-delivery}

整合內容後，按一下以儲存傳送 **儲存**. 它現在會顯示在您的傳送清單中，位於 **[!UICONTROL Campaigns > Deliveries]** 標籤。
