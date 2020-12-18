---
solution: Campaign Classic
product: campaign
title: 使用案例——建立電子郵件傳送
description: 建立電子郵件傳送使用案例
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 46aa896929c960abeb501642a5ffbbb56de4802e
workflow-type: tm+mt
source-wordcount: '734'
ht-degree: 0%

---


# 使用案例：建立電子郵件傳遞{#use-case-creating-an-email-delivery}

在此使用案例中，您將學習使用Adobe Campaign數位內容編輯器(DCE)來設計電子郵件傳送的步驟。

我們的最終目標是使用包含下列內容的個人化範本來建立傳送內容：

* 收件者的直接位址（使用第一名和第二名）
* 外部URL的兩種連結類型
* 鏡像頁
* Web應用程式的連結

>[!NOTE]
>
>在開始之前，您必須至少配置一個&#x200B;**HTML範本**，以代管未來傳送的內容。
>
>在傳送&#x200B;**[!UICONTROL Properties]**&#x200B;中，請確定&#x200B;**[!UICONTROL Content editing mode]**（在&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中）已設為&#x200B;**[!UICONTROL DCE]**。 為確保編輯器的最佳操作，請參閱[內容編輯最佳實踐](../../web/using/content-editing-best-practices.md)。

## 步驟1 —— 建立傳送{#step-1---creating-a-delivery}

若要建立新的傳送，請將游標置於&#x200B;**促銷活動**&#x200B;標籤中，然後按一下&#x200B;**傳送**。 接著按一下現有傳送清單上方的&#x200B;**建立**&#x200B;按鈕。 如需建立傳送的詳細資訊，請參閱[本頁](../../delivery/using/about-email-channel.md)。

![](assets/delivery_step_1.png)

## 步驟2 —— 選擇模板{#step-2---selecting-a-template}

選取傳送範本，然後為傳送命名。 此名稱只會顯示給Adobe Campaign主控台的使用者，而收件者不會顯示，不過，此標題會顯示在您的傳送清單中。 按一下 **[!UICONTROL Continue]**。

![](assets/dce_delivery_model.png)

## 步驟3 —— 選擇內容{#step-3---selecting-a-content}

數位內容編輯器隨附各種現成可用範本，其結構各異（欄、文字區域等）。

選取您要使用的內容範本，然後按一下&#x200B;**[!UICONTROL Start with the selected content]**&#x200B;按鈕，在建立的傳送中顯示範本。

![](assets/dce_select_model.png)

您也可以選取&#x200B;**[!UICONTROL From a file]**，匯入在Adobe Campaign外部建立的HTML內容。

![](assets/dce_select_from_file_template.png)

您可將此內容儲存為範本，以供日後使用。 建立個人化內容範本後，您就可以從範本清單中預覽。 有關詳細資訊，請參閱[模板管理](../../web/using/template-management.md)。

>[!CAUTION]
>
>如果您使用&#x200B;**Adobe Campaign網頁介面**，您必須匯入包含HTML內容和相關影像的。zip檔案。

## 步驟4 —— 設計消息{#step-4---designing-the-message}

* 顯示收件者的名字和名字

   若要將收件者的名字和名字插入傳送中的文字欄位，請按一下您選擇的文字欄位，然後將游標置於您要顯示的位置。 按一下快顯工具列中的第一個圖示，然後按一下&#x200B;**[!UICONTROL Personalization block]**。 選擇&#x200B;**[!UICONTROL Greetings]** ，然後按一下&#x200B;**[!UICONTROL OK]**。

   ![](assets/dce_personalizationblock_greetings.png)

* 將連結插入影像

   若要透過影像將傳送收件者傳送至外部位址，請按一下相關影像以顯示快顯工具列，將游標置於第一個圖示上，然後按一下&#x200B;**[!UICONTROL Link to an external URL]**。 有關詳細資訊，請參閱[添加連結](../../web/using/editing-content.md#adding-a-link)。

   ![](assets/dce_externalpage.png)

   在&#x200B;**URL**&#x200B;欄位中輸入連結的URL，使用下列格式&#x200B;**https://www.myURL.com**，然後確認。

   您可隨時使用視窗右側的區段來變更連結。

* 將連結插入文字

   若要將外部連結整合到傳送中的文字中，請選取某些文字或文字區塊，然後按一下快顯工具列中的第一個圖示。 按一下&#x200B;**[!UICONTROL Link to an external URL]** ，在&#x200B;**[!UICONTROL URL]**&#x200B;欄位中輸入連結地址。 有關詳細資訊，請參閱[添加連結](../../web/using/editing-content.md#adding-a-link)。

   您可隨時使用視窗右側的區段來變更連結。

   >[!CAUTION]
   >
   >在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入的文字會取代原始文字。

* 添加鏡像頁

   若要讓收件者在網頁瀏覽器中檢視您的傳送內容，您可以將鏡像頁面的連結整合到傳送中。

   按一下您想要在其中看到已張貼連結的文字欄位。 按一下快顯工具列中的第一個圖示，選擇&#x200B;**[!UICONTROL Personalization block]**，然後選擇&#x200B;**[!UICONTROL Link to Mirror Page (MirrorPage)]**。 按一下&#x200B;**[!UICONTROL Save]**&#x200B;進行確認。

   ![](assets/dce_mirrorpage.png)

   >[!CAUTION]
   >
   >個人化區塊標籤會自動取代您傳送中的原始文字。

* 整合Web應用程式的連結

   數位內容編輯器可讓您從Adobe Campaign主控台（例如登陸頁面或表單頁面）整合網路應用程式的連結。 有關詳細資訊，請參閱[連結到Web應用程式](../../web/using/editing-content.md#link-to-a-web-application)。

   為Web應用程式的連結選取文字欄位，然後按一下第一個圖示。 選擇&#x200B;**[!UICONTROL Link to a Web application]**，然後按一下&#x200B;**Web應用程式**&#x200B;欄位結尾的圖示，以選擇所要的應用程式。

   ![](assets/dce_webapp.png)

   按一下&#x200B;**保存**&#x200B;進行確認。

   >[!NOTE]
   >
   >此步驟需要您事先儲存至少一個Web應用程式。 這些可在控制台的&#x200B;**[!UICONTROL Campaigns > Web applications]**&#x200B;標籤中找到。

## 步驟5 —— 保存傳送{#step-5---saving-the-delivery}

整合內容後，按一下「儲存」以儲存傳送內容。 ****&#x200B;它現在會顯示在您的傳送清單中，位於&#x200B;**[!UICONTROL Campaigns > Deliveries]**&#x200B;標籤中。
