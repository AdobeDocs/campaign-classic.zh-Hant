---
product: campaign
title: 使用案例 — 建立電子郵件傳遞
description: 使用案例 — 建立電子郵件傳遞
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Apps, Web Forms, Landing Pages, Email Design
exl-id: e2679f12-459b-466d-9c82-60a28363b104
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '746'
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
>開始之前，您必須先擁有至少一個 **HTML範本** 設定為託管您未來傳送的內容。
>
>在傳遞中 **[!UICONTROL Properties]**，確認 **[!UICONTROL Content editing mode]** (在 **[!UICONTROL Advanced]** 標籤)設為 **[!UICONTROL DCE]**. 若要確保編輯器可最佳化操作，請參閱 [內容編輯最佳實務](content-editing-best-practices.md).

## 步驟1 — 建立傳遞 {#step-1---creating-a-delivery}

若要建立新傳送，請將游標置於 **行銷活動** 標籤並按一下 **傳遞**. 接著，按一下 **建立** 按鈕。 有關建立傳送的詳細資訊，請參閱 [此頁面](../../delivery/using/about-email-channel.md).

![](assets/delivery_step_1.png)

## 步驟2 — 選取範本 {#step-2---selecting-a-template}

選取傳遞範本，然後為您的傳遞命名。 此名稱將僅對Adobe Campaign主控台的使用者可見，不會由您的收件者可見，不過此標題將顯示在您的傳遞清單中。 按一下&#x200B;**[!UICONTROL Continue]**。

![](assets/dce_delivery_model.png)

## 步驟3 — 選取內容 {#step-3---selecting-a-content}

數位內容編輯器提供各種現成可用的範本，其結構各異（欄、文字區域等）。

選取您要使用的內容範本，然後按一下 **[!UICONTROL Start with the selected content]** 按鈕，在建立傳遞中顯示範本。

![](assets/dce_select_model.png)

您也可以選取「 」，匯入在Adobe Campaign外部建立的HTML內容 **[!UICONTROL From a file]**.

![](assets/dce_select_from_file_template.png)

您可以將此內容儲存為範本以供日後使用。 建立個人化內容範本後，您可以從範本清單中預覽它。 有關詳細資訊，請參閱 [範本管理](template-management.md).

>[!CAUTION]
>
>如果您使用 **Adobe Campaign網頁介面**，您必須匯入包含HTML內容和相關影像的.zip檔案。

## 步驟4 — 設計訊息 {#step-4---designing-the-message}

* 顯示收件者的第一和第二個名稱

  若要將收件者的第一和第二個名稱插入傳遞中的文字欄位，請按一下您選擇的文字欄位，然後將游標放在您要顯示它們的位置。 按一下彈出式工具列中的第一個圖示，然後按一下 **[!UICONTROL Personalization block]**. 選取 **[!UICONTROL Greetings]**，然後按一下 **[!UICONTROL OK]**.

  ![](assets/dce_personalizationblock_greetings.png)

* 將連結插入影像中

  若要透過影像將傳遞收件者導向至外部地址，請按一下相關影像以顯示快顯工具列，將游標放在第一個圖示上，然後按一下 **[!UICONTROL Link to an external URL]**. 有關詳細資訊，請參閱 [新增連結](editing-content.md#adding-a-link).

  ![](assets/dce_externalpage.png)

  在「 」中輸入連結的URL **URL** 欄位使用下列格式 **https://www.myURL.com**，然後確認。

  您可以使用視窗右側的區段隨時變更連結。

* 在文字中插入連結

  若要將外部連結整合至傳遞中的文字，請選取一些文字或文字區塊，然後按一下彈出式工具列中的第一個圖示。 按一下 **[!UICONTROL Link to an external URL]**，請在中輸入連結位址 **[!UICONTROL URL]** 欄位。 有關詳細資訊，請參閱 [新增連結](editing-content.md#adding-a-link).

  您可以使用視窗右側的區段隨時變更連結。

  >[!CAUTION]
  >
  >在中輸入的文字 **[!UICONTROL Label]** 欄位會取代原始文字。

* 新增映象頁面

  若要讓收件者在網頁瀏覽器中檢視您的傳送內容，您可以將映象頁面的連結整合至您的傳送中。

  按一下您想要看到連結張貼到的文字欄位。 按一下彈出式工具列中的第一個圖示，選取 **[!UICONTROL Personalization block]**，然後 **[!UICONTROL Link to Mirror Page (MirrorPage)]**. 按一下 **[!UICONTROL Save]** 確認。

  ![](assets/dce_mirrorpage.png)

  >[!CAUTION]
  >
  >個人化區塊標籤會自動取代傳送中的原始文字。

* 將連結整合至網頁應用程式

  數位內容編輯器可讓您從Adobe Campaign主控台整合至Web應用程式的連結，例如登入頁面或表單頁面。 有關詳細資訊，請參閱 [連結至Web應用程式](editing-content.md#link-to-a-web-application).

  選取連結至Web應用程式的文字欄位，然後按一下第一個圖示。 選擇 **[!UICONTROL Link to a Web application]**，然後按一下「 」結尾的圖示，以選取所需的應用程式 **網頁應用程式** 欄位。

  ![](assets/dce_webapp.png)

  按一下 **儲存** 以確認。

  >[!NOTE]
  >
  >此步驟需要您預先儲存至少一個Web應用程式。 這些可在以下網址找到： **[!UICONTROL Campaigns > Web applications]** 標籤進行識別。

## 步驟5 — 儲存傳遞 {#step-5---saving-the-delivery}

內容整合後，按一下「 」以儲存傳送 **儲存**. 它現在會顯示在您的傳遞清單中，該清單可在以下位置找到： **[!UICONTROL Campaigns > Deliveries]** 標籤。
