---
title: 「使用案例：建立電子郵件傳送」
seo-title: 「使用案例：建立電子郵件傳送」
description: 「使用案例：建立電子郵件傳送」
seo-description: null
page-status-flag: never-activated
uuid: 7cd6329c-63d5-4cf0-9451-f0b4c2eaf0dd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: editing-html-content
discoiquuid: 4ec34980-62a2-47b9-b103-de4290925624
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 36beb1eca48c698634c7548e0f931ab3fe17c021

---


# 使用案例：建立電子郵件傳送{#use-case-creating-an-email-delivery}

在此使用案例中，您將學習使用Adobe Campaign數位內容編輯器(DCE)來設計電子郵件傳送的步驟。

我們的最終目標是使用包含下列內容的個人化範本來建立傳送內容：

* 收件者的直接位址（使用第一名和第二名）
* 外部URL的兩種連結類型
* 鏡像頁
* Web應用程式的連結

>[!NOTE]
>
>在開始之前，您必須至少設定一個 **HTML範本** ，以代管未來傳送的內容。
>
>在傳送 **[!UICONTROL Properties]** 中，請確定 **[!UICONTROL Content editing mode]** (在標籤 **[!UICONTROL Advanced]** 中)已設為 **[!UICONTROL DCE]**。 為確保編輯器的最佳操作，請參閱「內容編輯」 [最佳實踐方案](../../web/using/content-editing-best-practices.md)。

## 步驟1 —— 建立傳送 {#step-1---creating-a-delivery}

若要建立新的傳送，請將游標置於「促銷活動」標 **簽中** ，然後按一 **下「傳送」**。 接著，按一 **下現有** 「傳送」清單上方的「建立」按鈕。 For more on creating deliveries, refer to [this page](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 步驟2 —— 選擇範本 {#step-2---selecting-a-template}

選取傳送範本，然後為傳送命名。 此名稱只會顯示給Adobe Campaign主控台的使用者，而收件者不會顯示，不過，此標題會顯示在您的傳送清單中。 按一下 **[!UICONTROL Continue]**.

![](assets/dce_delivery_model.png)

## 步驟3 —— 選擇內容 {#step-3---selecting-a-content}

數位內容編輯器隨附各種現成可用範本，其結構各異（欄、文字區域等）。

選取您要使用的內容範本，然後按一下按 **[!UICONTROL Start with the selected content]** 鈕，在建立的傳送中顯示範本。

![](assets/dce_select_model.png)

您也可以透過選取來匯入在Adobe Campaign以外建立的HTML內容 **[!UICONTROL From a file]**。

![](assets/dce_select_from_file_template.png)

您可將此內容儲存為範本，以供日後使用。 建立個人化內容範本後，您就可以從範本清單中預覽。 For more on this, refer to [Template management](../../web/using/template-management.md).

>[!CAUTION]
>
>如果您使用 **Adobe Campaign網頁介面**，您必須匯入包含HTML內容和相關影像的。zip檔案。

## 步驟4 —— 設計訊息 {#step-4---designing-the-message}

* 顯示收件者的名字和名字

   若要將收件者的名字和名字插入傳送中的文字欄位，請按一下您選擇的文字欄位，然後將游標置於您要顯示的位置。 按一下快顯工具列中的第一個圖示，然後按一下 **[!UICONTROL Personalization block]**。 選取 **[!UICONTROL Greetings]**，然後按一下 **[!UICONTROL OK]**。

   ![](assets/dce_personalizationblock_greetings.png)

* 將連結插入影像

   若要透過影像將傳送收件者帶到外部位址，請按一下相關影像以顯示快顯工具列，將游標置於第一個圖示上，然後按一下 **[!UICONTROL Link to an external URL]**。 有關詳細資訊，請參閱 [添加連結](../../web/using/editing-content.md#adding-a-link)。

   ![](assets/dce_externalpage.png)

   在 **URL欄位中輸入連結的** URL **，使用下列格式** https://www.myURL.com，然後確認。

   您可隨時使用視窗右側的區段來變更連結。

* 將連結插入文字

   若要將外部連結整合到傳送中的文字中，請選取某些文字或文字區塊，然後按一下快顯工具列中的第一個圖示。 按一 **[!UICONTROL Link to an external URL]**&#x200B;下，在欄位中輸入連結地 **[!UICONTROL URL]** 址。 有關詳細資訊，請參閱 [添加連結](../../web/using/editing-content.md#adding-a-link)。

   您可隨時使用視窗右側的區段來變更連結。

   >[!CAUTION]
   >
   >在欄位中輸入的文 **[!UICONTROL Label]** 字會取代原始文字。

* 添加鏡像頁

   若要讓收件者在網頁瀏覽器中檢視您的傳送內容，您可以將鏡像頁面的連結整合到傳送中。

   按一下您想要在其中看到已張貼連結的文字欄位。 按一下快顯工具列中的第一個圖示，然後選 **[!UICONTROL Personalization block]**&#x200B;取，然後 **[!UICONTROL Link to Mirror Page (MirrorPage)]**。 Click **[!UICONTROL Save]** to confirm.

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >個人化區塊標籤會自動取代您傳送中的原始文字。

* 整合Web應用程式的連結

   數位內容編輯器可讓您從Adobe Campaign主控台（例如登陸頁面或表單頁面）整合網路應用程式的連結。 如需詳細資訊，請參 [閱連結至Web應用程式](../../web/using/editing-content.md#link-to-a-web-application)。

   為Web應用程式的連結選取文字欄位，然後按一下第一個圖示。 選 **[!UICONTROL Link to a Web application]**&#x200B;擇，然後按一下「Web應用程式」欄位結尾的圖示，以選 **取所需應用程式** 。

   ![](assets/dce_webapp.png)

   按一 **下「儲存** 」以確認。

   >[!NOTE]
   >
   >此步驟需要您事先儲存至少一個Web應用程式。 這些可在控制台的選 **[!UICONTROL Campaigns > Web applications]** 項卡中找到。

## 步驟5 —— 儲存傳送 {#step-5---saving-the-delivery}

整合內容後，按一下「儲存」儲存傳送 **內容**。 它現在會顯示在您的傳送清單中，位於標籤 **[!UICONTROL Campaigns > Deliveries]** 中。
