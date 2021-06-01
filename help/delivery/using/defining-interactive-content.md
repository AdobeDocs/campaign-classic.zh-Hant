---
product: campaign
title: 在Adobe Campaign Classic中定義互動式內容
description: 了解如何在Adobe Campaign Classic中使用AMP定義互動式和動態電子郵件內容。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 3%

---

# 定義互動式內容{#defining-interactive-content}

Adobe Campaign可讓您使用新的互動式[ AMP for Email](https://amp.dev/about/email/)格式，這可讓您在特定條件下傳送動態電子郵件。

使用AMP for Email，您可以：
* 測試將AMP電子郵件傳遞至適當設定的特定地址。
* 向對應的提供者註冊後，將AMP電子郵件傳送至Gmail、Outlook或Mail.ru地址。

如需測試和傳送AMP電子郵件的詳細資訊，請參閱[定位AMP電子郵件](#targeting-amp-email)。

此功能可透過Adobe Campaign中的專用套件取得。 若要使用，必須安裝此套件。 完成後，重新啟動伺服器以考慮包。

>[!NOTE]
>
> 對於混合架構和托管架構，需要在所有伺服器上安裝該軟體包，包括[中間來源伺服器](../../installation/using/mid-sourcing-server.md)和[執行實例](../../message-center/using/configuring-instances.md#execution-instance)。 請連絡您的客戶經理。

## 關於電子郵件{#about-amp-for-email}的AMP

**Email適用的AMP**&#x200B;新格式可讓您在訊息中加入AMP元件，以運用豐富且可操作的內容提升電子郵件體驗。 透過直接在電子郵件中提供的現代化應用程式功能，收件者可以動態地與訊息本身的內容互動。

例如：
* 使用AMP撰寫的電子郵件可包含互動式元素，例如影像輪播。
* 訊息中的內容保持最新。
* 收件者無需離開收件匣即可採取回應表單之類的動作。

AMP for Email與現有電子郵件相容。 除了HTML和/或純文字，AMP版本的訊息會以新MIME部分的形式內嵌至電子郵件中，確保所有電子郵件用戶端的相容性。

如需電子郵件格式、規格和需求的更多資訊，請參閱[AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#amp-email-video)

## 搭配Adobe Campaign使用AMP for Email的關鍵步驟{#key-steps-to-use-amp}

若要使用Adobe Campaign成功測試並傳送AMP電子郵件，請遵循下列步驟：
1. 安裝&#x200B;**[!UICONTROL AMP support]**&#x200B;軟體包。 請參閱[安裝Campaign內建套件](../../installation/using/installing-campaign-standard-packages.md)。
1. 在Adobe Campaign中建立電子郵件並建置AMP內容。 請參閱[使用Adobe Campaign](#build-amp-email-content)建立AMP電子郵件內容。
1. 請務必遵循支援AMP格式之電子郵件提供者提供的所有傳送需求。 請參閱[AMP以了解電子郵件傳送需求](#amp-for-email-delivery-requirements)。
1. 定義目標時，請務必選取可顯示AMP格式的收件者。 請參閱[定位AMP電子郵件](#targeting-amp-email)。

   >[!NOTE]
   >
   >目前您只能傳送AMP電子郵件至[特定電子郵件地址](#testing-amp-delivery-for-selected-addresses)（用於測試用途）或在[註冊](#delivering-amp-emails-by-registering)後，向支援的電子郵件用戶端傳送。

1. 照常發送電子郵件。 請參閱[傳送AMP電子郵件](#sending-amp-email)。

## 在Adobe Campaign中建立AMP電子郵件內容{#build-amp-email-content}

若要使用AMP格式建立電子郵件，請遵循下列步驟。

>[!IMPORTANT]
>
>請務必遵循[AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)中詳述的AMP for Email要求和規格。 您也可以參閱[ AMP for Email最佳實務](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)。

1. 建立電子郵件傳送時，請選取任何範本。

   >[!NOTE]
   >
   >特定AMP範本包含您可使用的主要容量範例：產品清單、輪播、雙重加入、調查和進階伺服器要求。

1. 按一下&#x200B;**[!UICONTROL AMP content]**&#x200B;標籤。

   ![](assets/amp_tab.png)

1. 編輯AMP內容以符合您的需求。

   >[!NOTE]
   >
   >如需建立第一封AMP電子郵件的詳細資訊，請參閱[AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)。

   例如，您可以使用AMP範本的產品清單元件，並維護協力廠商系統的產品清單，甚至是Adobe Campaign內部。 每當您調整價格或其他元素時，收件者從其信箱再次開啟電子郵件時，就會自動反映價格或其他元素。

1. 視需要個人化您的AMP內容，如同您通常在Adobe Campaign中使用HTML格式，並搭配個人化欄位和個人化區塊。

   ![](assets/amp_tab_perso.png)

1. 完成編輯後，選取您的整個AMP內容，並複製並貼至[AMP網頁型驗證器](https://validator.ampproject.org)或類似的網站。

   >[!NOTE]
   >
   >請務必從畫面上方的下拉式清單中選取&#x200B;**AMP4 EMAIL**。

   ![](assets/amp_validator.png)

   系統會內嵌標籤任何錯誤。

   >[!NOTE]
   >
   >Adobe Campaign AMP編輯器並非專為內容驗證而設計。 使用外部網站（例如[AMP網頁型驗證器](https://validator.ampproject.org)）來檢查您的內容是否正確。

1. 視需要進行修正，直到AMP內容通過驗證為止。

   ![](assets/amp_validator_pass.png)

1. 將已驗證的內容複製貼上至[ AMP Pleardy](https://playground.amp.dev)或類似的網站，以預覽您的內容。

   >[!NOTE]
   >
   >請務必從畫面上方的下拉式清單中選取&#x200B;**電子郵件適用的AMP**。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >您無法直接在Adobe Campaign中預覽AMP內容。 使用外部網站，如[AMP Pleargoy](https://playground.amp.dev)。

1. 返回Adobe Campaign，並將驗證的內容複製貼到&#x200B;**[!UICONTROL AMP content]**&#x200B;標籤。

1. 切換到&#x200B;**[!UICONTROL HTML content]**&#x200B;或&#x200B;**[!UICONTROL Text content]**&#x200B;頁簽，並為這兩種格式中的至少一種定義內容。

   >[!IMPORTANT]
   >
   >若您的電子郵件除AMP內容外，不含HTML或純文字版本，則無法傳送。

## 電子郵件傳送需求AMP {#amp-for-email-delivery-requirements}

在Adobe Campaign中建置AMP內容時，您必須符合動態電子郵件的傳送條件，這是您收件者的電子郵件提供者專屬的條件。

目前有三個電子郵件提供者支援測試此格式：Gmail、Outlook和Mail.ru。

在Gmail帳戶上測試使用AMP格式傳送所需的所有步驟和規格，在對應的[Gmail](https://developers.google.com/gmail/ampemail?)、[Outlook ](https://docs.microsoft.com/en-gb/outlook/amphtml/)和[Mail.ru](https://postmaster.mail.ru/amp)開發人員檔案中詳細說明。

特別是，必須滿足以下要求：
* 請遵循[Gmail](https://developers.google.com/gmail/ampemail/security-requirements)、[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/security-requirements)和[Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto)的特定AMP安全要求。
* AMP MIME部分必須包含[有效的AMP文檔](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)。
* AMP MIME部分必須小於100KB。

您也可以參閱[Gmail](https://developers.google.com/gmail/ampemail/tips)的提示與已知限制，以及Outlook[AMP最佳作法](https://docs.microsoft.com/en-gb/outlook/amphtml/best-practices)。

## 定位AMP電子郵件{#targeting-amp-email}

目前，您可以嘗試透過兩個步驟來傳送AMP電子郵件：

1. Adobe Campaign可讓您測試將AMP支援的動態電子郵件傳遞至已適當設定的選定電子郵件地址，以驗證其內容和行為。 請參閱[測試所選地址的AMP電子郵件傳送](#testing-amp-delivery-for-selected-addresses)。

1. 測試後，您可以向相關電子郵件提供者註冊，將您的寄件者網域新增至允許清單，即可傳送內容或行銷活動，作為AMP for Email計畫的一部分。 請參閱[向電子郵件提供者註冊以傳送AMP電子郵件](#delivering-amp-emails-by-registering)。

### 測試所選地址{#testing-amp-delivery-for-selected-addresses}的AMP電子郵件傳送

您可以測試將動態訊息從Adobe Campaign傳送至選取的電子郵件地址。

>[!NOTE]
>
>目前僅Gmail、Outlook和Mail.ru支援測試AMP格式。

若是Gmail和Outlook，您必須先將您使用的寄件者地址新增至允許清單，以便從Adobe Campaign傳送您目標定位的Gmail和Outlook帳戶。

操作步驟：
1. 請確定已針對相關電子郵件提供者勾選啟用動態電子郵件的選項。
1. 複製傳送&#x200B;**[!UICONTROL From]**&#x200B;欄位中顯示的寄件者地址，並貼到您的電子郵件提供者帳戶設定的適當區段中。

如需詳細資訊，請參閱[Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email)和[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#individual-mailbox-registration)開發人員檔案。

![](assets/amp_from_field.png)

若要測試傳送AMP電子郵件至Mail.ru地址，請遵循[Mail.ru開發人員檔案](https://postmaster.mail.ru/amp/?lang=en#howto)（**若您是使用者**&#x200B;區段）中的步驟。

### 向電子郵件提供者{#delivering-amp-emails-by-registering}註冊以傳送AMP電子郵件

您可以向支援的電子郵件提供者註冊，以將您的寄件者網域新增至允許清單，借此試驗傳送動態電子郵件。

>[!NOTE]
>
>目前僅Gmail、Outlook和Mail.ru支援AMP格式。

只要用幾個地址測試，您就可以傳送AMP電子郵件至任何Gmail或Outlook地址。 為此，您必須恭敬地向谷歌或微軟註冊，並等待他們的答案。 請依照[Gmail](https://developers.google.com/gmail/ampemail/register)和[Outlook](https://docs.microsoft.com/en-gb/outlook/amphtml/register-outlook#global-registration)開發人員檔案中提供的步驟操作。 註冊成功後，您會成為授權寄件者。

若要傳送AMP電子郵件至Mail.ru地址，請遵循[Mail.ru開發人員檔案](https://postmaster.mail.ru/amp/?lang=en#howto)（**如果您是電子郵件寄件者**&#x200B;區段）中所列的要求和步驟。

## 傳送AMP電子郵件{#sending-amp-email}

一旦AMP內容和備援準備就緒，而定義相容目標後，您就可以像平常一樣傳送電子郵件。

目前，在特定條件下，僅Gmail、Outlook和Mail.ru支援AMP格式。 您可以鎖定來自其他電子郵件提供者的地址，但他們會收到您電子郵件的HTML或純文字版本。

>[!IMPORTANT]
>
>若您的電子郵件除AMP內容外，不含HTML或純文字版本，則無法傳送。

相符的收件者會在其信箱中顯示電子郵件的AMP版本。

例如，如果您在電子郵件中包含產品清單，在編輯協力廠商系統中的價格時，每當您的收件者在其信箱中再次開啟電子郵件時，價格就會自動調整。

>[!NOTE]
>
>您可以建立郵件處理規則，以防止特定網域收到AMP電子郵件。 請參閱[管理電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats)。
>
>預設情況下，**[!UICONTROL AMP inclusion]**&#x200B;選項設定為&#x200B;**[!UICONTROL No]**。

## 教學課程影片{#amp-email-video}

以下影片說明如何在Adobe Campaign 啟動 AMP，並展示其使用情形。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

您可以在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得其他促銷活動作法影片。
