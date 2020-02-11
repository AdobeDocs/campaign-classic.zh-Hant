---
title: 在Adobe Campaign Classic中定義互動式內容
description: 瞭解如何在Adobe Campaign Classic中使用AMP定義互動式和動態電子郵件內容。
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1815f9fc6063ec86d6c12ef492396e5afb82b3e1

---


# 定義互動式內容{#defining-interactive-content}

Adobe Campaign可讓您嘗試新的互動式 [AMP for Email](https://amp.dev/about/email/) ，讓您在特定條件下傳送動態電子郵件。

>[!IMPORTANT]
>
>* 此功能是Adobe Campaign的測試版功能。
>* AMP for Email是一種新的開放原始碼格式，可讓開發人員建立動態和互動式電子郵件。 目前，有數家電子郵件提供者支援：Gmail、Outlook和Mail.ru。


目前，您只能：
* 測試將AMP電子郵件傳送至正確設定的特定位址。
* 在向對應的提供者註冊後，將AMP電子郵件傳送至Gmail、Outlook或Mail.ru地址。

如需測試和傳送AMP電子郵件的詳細資訊，請參 [閱定位AMP電子郵件](#targeting-amp-email)。

此功能可透過Adobe Campaign中的專屬套件取得。 若要使用，必須安裝此套件。 完成後，重新啟動伺服器，以便將包納入考慮範圍。

對於混合式和托管式架構，此套件必須安裝在所有伺服器上，包括 [中端採購伺服器](../../installation/using/mid-sourcing-server.md) 和執 [行例項](../../message-center/using/creating-a-shared-connection.md#execution-instance)。 請洽詢您的客戶經理。

觀看此 [影片](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/sending-messages/email-channel/defining-interactive-email-content-with-amp.html) ，瞭解如何在Adobe Campaign中啟動AMP，並瞭解使用情形。

## 關於AMP for Email {#about-amp-for-email}

AMP for Email **** new format可讓訊息中加入AMP元件，以利用豐富且可操作的內容來增強電子郵件體驗。 透過直接在電子郵件中提供的現代化應用程式功能，收件者可以動態地與訊息本身的內容互動。

例如：
* 使用AMP撰寫的電子郵件可包含互動式元素，例如影像轉盤。
* 訊息中的內容會保持最新狀態。
* 收件者可以採取類似回應表單的動作，而不需離開收件匣。

AMP for Email與現有電子郵件相容。 除了HTML和／或純文字外，訊息的AMP版本會以新的MIME部分嵌入電子郵件中，以確保所有電子郵件用戶端的相容性。

如需有關AMP for Email格式、規格和需求的詳細資訊，請參閱 [AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)。

## 搭配Adobe Campaign使用AMP for Email的關鍵步驟 {#key-steps-to-use-amp}

若要使用Adobe Campaign成功測試並傳送AMP電子郵件，請遵循下列步驟：
1. 安裝包 **[!UICONTROL AMP support (Beta)]** 。 請參 [閱安裝Campaign標準套件](../../installation/using/installing-campaign-standard-packages.md)。
1. 在Adobe Campaign中建立電子郵件並建立AMP內容。 請參 [閱「使用Adobe Campaign建立AMP電子郵件內容」](#build-amp-email-content)。
1. 請務必遵循支援AMP格式之電子郵件提供者的所有傳送要求。 請參 [閱AMP以瞭解電子郵件傳送需求](#amp-for-email-delivery-requirements)。

   >[!NOTE]
   >
   >AMP for Email是測試版功能，可用於測試用途。 目前只有少數的電子郵件供應商支援測試此格式。

1. 定義目標時，請確定您選擇了能夠顯示AMP格式的收件者。 請參 [閱定位AMP電子郵件](#targeting-amp-email)。

   >[!NOTE]
   >
   >您目前只能測試將AMP電子郵件傳送至已正確設定的特定電子郵件地址，或在註冊加入AMP測試版程式的電子郵件供應商後，才能進行測試。

1. 以您平常的方式傳送電子郵件。 請參 [閱發送AMP電子郵件](#sending-amp-email)。

## 在Adobe Campaign中建立AMP電子郵件內容 {#build-amp-email-content}

若要使用AMP格式建立電子郵件，請遵循下列步驟。

>[!IMPORTANT]
>
>請確定您遵循AMP的電子郵件需求和規格，詳見 [AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)。 您也可以參考 [AMP for Email最佳實務](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)。

1. 建立電子郵件傳送時，請選取任何範本。

   >[!NOTE]
   >
   >特定AMP模板包含您可以使用的主要容量示例：產品清單、轉盤、雙重加入、調查和進階伺服器要求。

1. 按一下標 **[!UICONTROL AMP content]** 簽。

   ![](assets/amp_tab.png)

1. 編輯AMP內容以符合您的需求。

   >[!NOTE]
   >
   >如需有關建立第一封AMP電子郵件的詳細資訊，請參閱 [AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)。

   例如，您可以使用AMP範本中的產品清單元件，並維護來自協力廠商系統的產品清單，甚至是Adobe Campaign內部的產品清單。 每當您調整價格或其他元素時，收件者從其郵箱再次開啟電子郵件時，就會自動反映價格或其他元素。

1. 視需要個人化您的AMP內容，就像您通常在Adobe Campaign中使用HTML格式、個人化欄位和個人化區塊所做的一樣。

   ![](assets/amp_tab_perso.png)

1. 編輯完成後，請選取整個AMP內容，並將它複製貼至 [AMP網頁驗證器](https://validator.ampproject.org) 或類似網站。

   >[!NOTE]
   >
   >請務必從畫 **面上方的下拉式清單中選取AMP4 EMAIL** 。

   ![](assets/amp_validator.png)

   任何錯誤都會以內嵌方式標幟。

   >[!NOTE]
   >
   >Adobe Campaign AMP編輯器不適用於內容驗證。 使用外部網站(例如 [AMP網路驗證器)](https://validator.ampproject.org) ，檢查您的內容是否正確。

1. 視需要進行修正，直到AMP內容通過驗證為止。

   ![](assets/amp_validator_pass.png)

1. 將您已驗證的內容複製貼至 [AMP Playround](https://playground.amp.dev) 或類似的網站，以預覽您的內容。

   >[!NOTE]
   >
   >請務必從畫面 **上方的下拉式清單中選取「AMP for Email** 」。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >您無法直接在Adobe Campaign中預覽AMP內容。 使用外部網站，例如 [AMP Playround](https://playground.amp.dev)。

1. 返回Adobe Campaign，將驗證的內容複製貼至標 **[!UICONTROL AMP content]** 簽。

1. 切換至 **[!UICONTROL HTML content]** 或 **[!UICONTROL Text content]** 標籤，並定義這兩種格式的至少一種內容。

   >[!IMPORTANT]
   >
   >如果您的電子郵件除了AMP內容以外不包含HTML或純文字版本，則無法傳送。

## AMP以滿足電子郵件傳送需求 {#amp-for-email-delivery-requirements}

在Adobe Campaign中建立AMP內容時，您必須符合傳送動態電子郵件的條件，這是您收件者的電子郵件提供者專屬的條件。

目前有三家電子郵件供應商支援測試此格式：Gmail、Outlook和Mail.ru。

在Gmail帳戶上測試AMP格式傳送所需的所有步驟和規格，都詳見相應的 [Gmail](https://developers.google.com/gmail/ampemail?)、 [Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/) 和 [](https://postmaster.mail.ru/amp) Mail.ru開發人員檔案。

尤其必須符合下列要求：
* 遵循 [Gmail](https://developers.google.com/gmail/ampemail/security-requirements)、 [Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements) 和 [Mail.ru的AMP安全要求](https://postmaster.mail.ru/amp/?lang=en#howto)。
* AMP MIME部分必須包含有效 [的AMP文檔](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)。
* AMP MIME部分必須小於100KB。

您也可以參考Gmail的 [提示和已知限制](https://developers.google.com/gmail/ampemail/tips) ，以及 [AMP的Outlook最佳實務](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices)。

## 定位AMP電子郵件 {#targeting-amp-email}

AMP for Email是測試版功能，您目前可以嘗試透過兩個步驟傳送AMP電子郵件：

1. Adobe Campaign可讓您測試將AMP支援的動態電子郵件傳送至已正確設定的選定電子郵件地址，以驗證其內容和行為。 請參 [閱測試AMP電子郵件傳送以取得選定的位址](#testing-amp-delivery-for-selected-addresses)。
1. 測試完成後，您可向相關電子郵件提供者註冊，將您的傳送者網域列入白名單，以傳送傳送或促銷活動，作為AMP for Email測試版計畫的一部分。 請參 [閱向電子郵件供應商註冊來傳送AMP電子郵件](#delivering-amp-emails-by-registering)。

### 測試AMP電子郵件傳送的選定地址 {#testing-amp-delivery-for-selected-addresses}

您可以測試從Adobe Campaign傳送動態訊息至選取的電子郵件地址。

>[!NOTE]
>
>目前只有Gmail、Outlook和Mail.ru支援測試AMP格式。

若是Gmail和Outlook，您必須先將您用來從Adobe Campaign傳送的寄件者位址列入白名單，以取得您目標的Gmail和Outlook帳戶。

操作步驟：
1. 請確定已勾選啟用動態電子郵件的選項，以找出相關的電子郵件提供者。
1. 複製傳送欄位中顯示的寄件者位址， **[!UICONTROL From]** 並貼至您的電子郵件提供者帳戶設定的適當區段。

如需詳細資訊，請參閱 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 和 [Outlook開發人](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration) 員檔案。

![](assets/amp_from_field.png)

要測試向Mail.ru地址發送AMP電子郵件，請遵循 [Mail.ru開發人員文檔](https://postmaster.mail.ru/amp/?lang=en#howto) (**如果您是用戶部分** )中的步驟。

### 向電子郵件提供者註冊以傳送AMP電子郵件 {#delivering-amp-emails-by-registering}

您可以嘗試向參與AMP測試版程式的電子郵件提供者註冊，以便將傳送者網域列入白名單，借此提供動態電子郵件。

>[!NOTE]
>
>目前只有Gmail、Outlook和Mail.ru支援AMP格式。

使用幾個地址測試後，您就可以將AMP電子郵件傳送至任何Gmail或Outlook地址。 若要這麼做，您必須向Google或Microsoft註冊，並等待他們的回答。 請依照 [Gmail和](https://developers.google.com/gmail/ampemail/register) Outlook開發人 [員檔案中](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration) ，顯示的步驟進行。 成功註冊後，您即成為授權寄件者。

若要將AMP電子郵件傳送至Mail.ru位址，請遵循 [Mail.ru開發人員檔案中所列的要求和步驟](https://postmaster.mail.ru/amp/?lang=en#howto) (**** 如果您是「電子郵件傳送者」區段)。

## 傳送AMP電子郵件 {#sending-amp-email}

一旦您的AMP內容和備援準備就緒，並定義相容目標後，您就可像平常一樣傳送電子郵件。

目前，在某些情況下，只有Gmail、Outlook和Mail.ru支援AMP格式。 您可以鎖定其他電子郵件提供者的位址，但他們會收到您電子郵件的HTML或純文字版本。

>[!IMPORTANT]
>
>如果您的電子郵件除了AMP內容以外不包含HTML或純文字版本，則無法傳送。

相符的收件者會將電子郵件的AMP版本顯示在其郵箱中。

例如，如果您在電子郵件中包含產品清單，在編輯協力廠商系統中的價格時，每次收件者在郵箱中再次開啟電子郵件時，價格都會自動調整。

>[!NOTE]
>
>您可以建立郵件處理規則，以防止特定網域收到AMP電子郵件。 請參閱 [管理電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats)。
>
>依預設， **[!UICONTROL AMP inclusion]** 選項會設為 **[!UICONTROL No]**。
