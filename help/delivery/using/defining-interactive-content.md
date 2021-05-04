---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic定義互動式內容
description: 瞭解如何使用Adobe Campaign Classic的AMP來定義互動式和動態電子郵件內容。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# 定義互動式內容{#defining-interactive-content}

Adobe Campaign可讓您使用新的互動式[AMP for Email](https://amp.dev/about/email/)格式，可在特定條件下傳送動態電子郵件。

有了AMP for Email，您可以：
* 測試將AMP電子郵件傳送至正確設定的特定位址。
* 在向對應的提供者註冊後，將AMP電子郵件傳送至Gmail、Outlook或Mail.ru地址。

有關測試和發送AMP電子郵件的詳細資訊，請參閱[定位AMP電子郵件](#targeting-amp-email)。

此功能可透過Adobe Campaign的專屬套件取得。 若要使用，必須安裝此套件。 完成後，重新啟動伺服器，以便將包納入考慮範圍。

>[!NOTE]
>
> 對於混合型和托管型體系結構，軟體包必須安裝在所有伺服器上，包括[mid-sourcing伺服器](../../installation/using/mid-sourcing-server.md)和[執行實例](../../message-center/using/creating-a-shared-connection.md#execution-instance)。 請洽詢您的客戶經理。

## 關於電子郵件{#about-amp-for-email}的AMP

**適用於電子郵件的AMP**&#x200B;新格式可讓您在訊息中加入AMP元件，以運用豐富且可操作的內容來增強電子郵件體驗。 透過直接在電子郵件中提供的現代化應用程式功能，收件者可以動態地與訊息本身的內容互動。

例如：
* 使用AMP撰寫的電子郵件可包含互動式元素，例如影像轉盤。
* 訊息中的內容會保持最新狀態。
* 收件者可以採取類似回應表單的動作，而不需離開收件匣。

AMP for Email與現有電子郵件相容。 除了HTML和／或純文字外，訊息的AMP版本會以新的MIME部分嵌入電子郵件中，以確保所有電子郵件用戶端的相容性。

有關AMP for Email格式、規格和要求的詳細資訊，請參閱[AMP開發人員文檔](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#amp-email-video)

## 將AMP用於電子郵件的關鍵步驟與Adobe Campaign{#key-steps-to-use-amp}一起使用

若要成功測試並傳送AMP電子郵件給Adobe Campaign，請遵循下列步驟：
1. 安裝&#x200B;**[!UICONTROL AMP support]**&#x200B;軟體包。 請參閱[安裝促銷活動內建套件](../../installation/using/installing-campaign-standard-packages.md)。
1. 在Adobe Campaign建立電子郵件並建立您的AMP內容。 請參閱[使用Adobe Campaign](#build-amp-email-content)建立AMP電子郵件內容。
1. 請務必遵循支援AMP格式之電子郵件提供者的所有傳送要求。 請參閱[電子郵件傳送需求的AMP](#amp-for-email-delivery-requirements)。
1. 定義目標時，請確定您選擇了能夠顯示AMP格式的收件者。 請參閱[定位AMP電子郵件](#targeting-amp-email)。

   >[!NOTE]
   >
   >目前，您只能將AMP電子郵件傳送至[特定電子郵件地址](#testing-amp-delivery-for-selected-addresses)（用於測試用途）或在[註冊](#delivering-amp-emails-by-registering)後，支援的電子郵件用戶端。

1. 以您平常的方式傳送電子郵件。 請參閱[發送AMP電子郵件](#sending-amp-email)。

## 在Adobe Campaign建立AMP電子郵件內容{#build-amp-email-content}

若要使用AMP格式建立電子郵件，請遵循下列步驟。

>[!IMPORTANT]
>
>請務必遵循[AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)中詳細說明的AMP電子郵件要求和規格。 您也可以參考[AMP for Email best practices](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)。

1. 建立電子郵件傳送時，請選取任何範本。

   >[!NOTE]
   >
   >特定AMP模板包含您可以使用的主要容量示例：產品清單、轉盤、雙重加入、調查和進階伺服器要求。

1. 按一下&#x200B;**[!UICONTROL AMP content]**&#x200B;頁籤。

   ![](assets/amp_tab.png)

1. 編輯AMP內容以符合您的需求。

   >[!NOTE]
   >
   >如需有關建立第一封AMP電子郵件的詳細資訊，請參閱[AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)。

   例如，您可以使用AMP範本中的產品清單元件，並維護來自協力廠商系統的產品清單，甚至在Adobe Campaign。 每當您調整價格或其他元素時，收件者從其郵箱再次開啟電子郵件時，就會自動反映價格或其他元素。

1. 視需要個人化您的AMP內容，就像您通常在Adobe Campaign使用HTML格式、個人化欄位和個人化區塊一樣。

   ![](assets/amp_tab_perso.png)

1. 編輯完成後，請選取整個AMP內容，並將它複製貼至[AMP網路驗證器](https://validator.ampproject.org)或類似的網站。

   >[!NOTE]
   >
   >請務必從螢幕頂部的下拉清單中選擇&#x200B;**AMP4 EMAIL**。

   ![](assets/amp_validator.png)

   任何錯誤都會以內嵌方式標幟。

   >[!NOTE]
   >
   >Adobe CampaignAMP編輯器不適用於內容驗證。 使用外部網站（例如[AMP web-based validator](https://validator.ampproject.org)）來檢查您的內容是否正確。

1. 視需要進行修正，直到AMP內容通過驗證為止。

   ![](assets/amp_validator_pass.png)

1. 將您已驗證的內容複製貼至[AMP Playround](https://playground.amp.dev)或類似的網站，以預覽您的內容。

   >[!NOTE]
   >
   >請務必從螢幕頂部的下拉清單中選擇&#x200B;**電子郵件** AMP。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >您無法直接在Adobe Campaign預覽AMP內容。 使用外部網站，例如[AMP Playround](https://playground.amp.dev)。

1. 返回Adobe Campaign，將驗證的內容複製並貼上到&#x200B;**[!UICONTROL AMP content]**&#x200B;頁籤。

1. 切換至&#x200B;**[!UICONTROL HTML content]**&#x200B;或&#x200B;**[!UICONTROL Text content]**&#x200B;標籤，並為這兩種格式中的至少一種定義內容。

   >[!IMPORTANT]
   >
   >如果您的電子郵件除了AMP內容以外不包含HTML或純文字版本，則無法傳送。

## AMP for Email delivery requirements {#amp-for-email-delivery-requirements}

在Adobe Campaign建立AMP內容時，您必須符合傳送動態電子郵件的條件，而傳送動態電子郵件的條件是您收件人的電子郵件提供者專屬的。

目前有三家電子郵件供應商支援測試此格式：Gmail、Outlook和Mail.ru。

Gmail帳戶上使用AMP格式測試傳送所需的所有步驟和規格，詳見相應的[Gmail](https://developers.google.com/gmail/ampemail?)、[Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/)和[Mail.ru](https://postmaster.mail.ru/amp)開發人員檔案。

尤其必須符合下列要求：
* 遵循[Gmail](https://developers.google.com/gmail/ampemail/security-requirements)、[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements)和[Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto)的特定AMP安全性要求。
* AMP MIME部分必須包含[有效的AMP文檔](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)。
* AMP MIME部分必須小於100KB。

您也可以參閱[Tips和Gmail](https://developers.google.com/gmail/ampemail/tips)的已知限制，以及[ Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices)的AMP最佳實踐。

## 定位AMP電子郵件{#targeting-amp-email}

目前，您可以嘗試透過兩個步驟傳送AMP電子郵件：

1. Adobe Campaign可讓您測試將AMP支援的動態電子郵件傳送至已正確設定的選定電子郵件地址，以驗證其內容和行為。 請參閱[測試所選地址的AMP電子郵件傳送](#testing-amp-delivery-for-selected-addresses)。

1. 一旦經過測試，您就可以向相關電子郵件提供者註冊，將您的傳送者網域加入允許清單中，以便將傳送或促銷活動作為AMP for Email計畫的一部分傳送。 請參閱[向電子郵件提供者註冊以傳送AMP電子郵件](#delivering-amp-emails-by-registering)。

### 測試選定地址{#testing-amp-delivery-for-selected-addresses}的AMP電子郵件傳送

您可以測試從Adobe Campaign傳送動態訊息至選取的電子郵件地址。

>[!NOTE]
>
>目前只有Gmail、Outlook和Mail.ru支援測試AMP格式。

對於Gmail和Outlook，您必須先將您使用的發件人地址添加到允許清單中，以便從Adobe Campaign為目標Gmail和Outlook帳戶發送郵件。

操作步驟：
1. 請確定已勾選啟用動態電子郵件的選項，以找出相關的電子郵件提供者。
1. 複製傳送&#x200B;**[!UICONTROL From]**&#x200B;欄位中顯示的寄件者位址，並貼至您的電子郵件提供者帳戶設定的適當區段。

如需詳細資訊，請參閱[Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email)和[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration)開發人員檔案。

![](assets/amp_from_field.png)

要測試向Mail.ru地址發送AMP電子郵件，請遵循[Mail.ru開發人員文檔](https://postmaster.mail.ru/amp/?lang=en#howto)（**如果您是用戶**&#x200B;部分）中的步驟。

### 向電子郵件提供者{#delivering-amp-emails-by-registering}註冊以傳送AMP電子郵件

您可以嘗試向支援的電子郵件提供者註冊，以便將傳送者網域新增至允許清單，借此傳送動態電子郵件。

>[!NOTE]
>
>目前只有Gmail、Outlook和Mail.ru支援AMP格式。

使用幾個地址測試後，您就可以將AMP電子郵件傳送至任何Gmail或Outlook地址。 若要這麼做，您必須向Google或Microsoft註冊，並等待他們的回答。 請遵循[Gmail](https://developers.google.com/gmail/ampemail/register)和[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration)開發人員檔案中的步驟。 成功註冊後，您即成為授權寄件者。

要向Mail.ru地址發送AMP電子郵件，請遵循[Mail.ru開發人員文檔](https://postmaster.mail.ru/amp/?lang=en#howto)（**如果您是電子郵件發件人**&#x200B;部分）中列出的要求和步驟。

## 發送AMP電子郵件{#sending-amp-email}

一旦您的AMP內容和備援準備就緒，並定義相容目標後，您就可像平常一樣傳送電子郵件。

目前，在某些情況下，只有Gmail、Outlook和Mail.ru支援AMP格式。 您可以鎖定其他電子郵件提供者的位址，但他們會收到您電子郵件的HTML或純文字版本。

>[!IMPORTANT]
>
>如果您的電子郵件除了AMP內容以外不包含HTML或純文字版本，則無法傳送。

相符的收件者會將電子郵件的AMP版本顯示在其郵箱中。

例如，如果您在電子郵件中包含產品清單，在編輯協力廠商系統中的價格時，每次收件者在郵箱中再次開啟電子郵件時，價格都會自動調整。

>[!NOTE]
>
>您可以建立郵件處理規則，以防止特定網域收到AMP電子郵件。 請參閱[管理電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats)。
>
>預設情況下，**[!UICONTROL AMP inclusion]**&#x200B;選項設定為&#x200B;**[!UICONTROL No]**。

## 教學課程影片{#amp-email-video}

以下影片說明如何在Adobe Campaign 啟動 AMP，並展示其使用情形。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

其他促銷活動操作影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
