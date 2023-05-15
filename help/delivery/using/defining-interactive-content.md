---
product: campaign
title: 在Adobe Campaign Classic中定義互動式內容
description: 了解如何在Adobe Campaign中使用AMP定義互動式和動態電子郵件內容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email Design, Dynamic Content
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1505'
ht-degree: 4%

---

# 定義互動式內容{#defining-interactive-content}



Adobe Campaign可讓您使用互動式 [電子郵件AMP](https://amp.dev/about/email/) 格式，可在特定條件下傳送動態電子郵件。

使用AMP for Email，您可以：
* 測試將AMP電子郵件傳遞至適當設定的特定地址。
* 向對應的提供者註冊後，將AMP電子郵件傳送至Gmail或Mail.ru地址。

如需測試和傳送AMP電子郵件的詳細資訊，請參閱 [本節](#targeting-amp-email).

此功能可透過Adobe Campaign中的專用套件取得。 您可以安裝此套件或聯絡Adobe，為您安裝，視您的權限和部署模式而定。

>[!NOTE]
>
> 對於混合和托管體系結構，該軟體包必須安裝在所有伺服器上，包括 [中間來源伺服器](../../installation/using/mid-sourcing-server.md) 和 [執行實例](../../message-center/using/configuring-instances.md#execution-instance).


## 關於電子郵件AMP {#about-amp-for-email}

使用 **電子郵件AMP** 新格式，可在您的訊息中加入AMP元件，並以豐富且可操作的內容改善電子郵件體驗。 透過直接在電子郵件中提供的現代化應用程式功能，收件者可以與訊息本身內容進行動態互動。

例如：
* 使用AMP撰寫的電子郵件可包含互動式元素，例如影像輪播。
* 訊息中的內容保持最新。
* 收件者無需離開收件匣即可回覆表單。

AMP for Email與現有電子郵件相容。 除了HTML和/或純文字，AMP版本的訊息會以新MIME部分的形式內嵌至電子郵件中，確保所有電子郵件用戶端的相容性。

有關AMP for Email格式、規格和要求的詳細資訊，請參閱 [AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email).

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#amp-email-video)

## 搭配Adobe Campaign使用AMP for Email的關鍵步驟 {#key-steps-to-use-amp}

若要使用Adobe Campaign成功測試並傳送AMP電子郵件，請遵循下列步驟：
1. 安裝 **[!UICONTROL AMP support]** 包。 請參閱 [安裝Campaign內建套件](../../installation/using/installing-campaign-standard-packages.md).
1. 在Adobe Campaign中建立電子郵件並建置AMP內容。 請參閱 [使用Adobe Campaign建立AMP電子郵件內容](#build-amp-email-content).
1. 請務必遵循支援AMP格式之電子郵件提供者提供的所有傳送需求。 請參閱 [AMP以滿足電子郵件傳送需求](#amp-for-email-delivery-requirements).
1. 定義目標時，請務必選取可顯示AMP格式的收件者。 請參閱 [定位AMP電子郵件](#targeting-amp-email).

   >[!NOTE]
   >
   >目前您只能傳送AMP電子郵件至 [特定電子郵件地址](#testing-amp-delivery-for-selected-addresses) （供測試之用）或之後 [註冊](#delivering-amp-emails-by-registering) 與支援的電子郵件用戶端。

1. 照常發送電子郵件。 請參閱 [傳送AMP電子郵件](#sending-amp-email).

## 在Adobe Campaign中建立AMP電子郵件內容 {#build-amp-email-content}

若要使用AMP格式建立電子郵件，請遵循下列步驟。

>[!IMPORTANT]
>
>請務必遵循AMP，以了解 [AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email). 您也可以參閱 [AMP for Email最佳作法](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email).

1. 建立電子郵件傳送時，請選取任何範本。

   >[!NOTE]
   >
   >特定AMP範本包含您可使用的主要容量範例：產品清單、輪播、雙重加入、調查和進階伺服器要求。

1. 按一下 **[!UICONTROL AMP content]** 標籤。

   ![](assets/amp_tab.png)

1. 編輯AMP內容以符合您的需求。

   >[!NOTE]
   >
   >如需建立第一個AMP電子郵件的詳細資訊，請參閱 [AMP開發人員檔案](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email).

   例如，您可以使用AMP範本的產品清單元件，並維護協力廠商系統的產品清單，甚至是Adobe Campaign內部。 每當您調整價格或其他元素時，收件者從其信箱開啟電子郵件時，就會自動反映價格或其他元素。

1. 視需要個人化您的AMP內容，如同您一般在Adobe Campaign中使用HTML格式，並搭配個人化欄位和個人化區塊。

   ![](assets/amp_tab_perso.png)

1. 完成編輯後，選取您的整個AMP內容，並複製並貼到 [AMP Web驗證器](https://validator.ampproject.org) 或類似的網站。

   >[!NOTE]
   >
   >請確定您選取 **AMP4電子郵件** 從畫面頂端的下拉式清單。

   ![](assets/amp_validator.png)

   系統會內嵌標籤錯誤。

   >[!NOTE]
   >
   >Adobe Campaign AMP編輯器並非專為內容驗證而設計。 使用外部網站，例如 [AMP Web驗證器](https://validator.ampproject.org) 來檢查內容是否正確。

1. 視需要進行修正，直到AMP內容通過驗證為止。

   ![](assets/amp_validator_pass.png)

1. 若要預覽內容，請將已驗證的內容複製並貼入 [AMP遊樂場](https://playground.amp.dev) 或類似的網站。

   >[!NOTE]
   >
   >請確定您選取 **電子郵件AMP** 從畫面頂端的下拉式清單。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >您無法直接在Adobe Campaign中預覽AMP內容。 使用外部網站，例如 [AMP遊樂場](https://playground.amp.dev).

1. 返回Adobe Campaign，將已驗證的內容複製貼到 **[!UICONTROL AMP content]** 標籤。

1. 切換至 **[!UICONTROL HTML content]** 或 **[!UICONTROL Text content]** 標籤，並定義這兩種格式中至少一個的內容。

   >[!IMPORTANT]
   >
   >若您的電子郵件除AMP內容外，不含HTML或純文字版本，則無法傳送。

## AMP以滿足電子郵件傳送需求 {#amp-for-email-delivery-requirements}

在Adobe Campaign中建置AMP內容時，您必須符合動態電子郵件的傳送條件，這是您收件者的電子郵件提供者專屬的條件。

目前有兩個電子郵件提供者支援測試此格式：Gmail和Mail.ru。

在Gmail帳戶上測試使用AMP格式傳送所需的所有步驟和規格，在對應的 [Gmail](https://developers.google.com/gmail/ampemail?)，和 [Mail.ru](https://postmaster.mail.ru/amp) 開發人員檔案。

特別是，必須滿足以下要求：
* 遵循 [Gmail](https://developers.google.com/gmail/ampemail/security-requirements)，和 [Mail.ru](https://postmaster.mail.ru/amp/?lang=en#howto).
* AMP MIME部分必須包含 [有效的AMP文檔](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email).
* AMP MIME部分必須小於100KB。

您也可以參閱 [Gmail的秘訣和已知限制](https://developers.google.com/gmail/ampemail/tips) 檔案。

## 定位AMP電子郵件 {#targeting-amp-email}

目前，您可以嘗試透過兩個步驟來傳送AMP電子郵件：

1. Adobe Campaign可讓您測試將AMP支援的動態電子郵件傳遞至已適當設定的選定電子郵件地址，以驗證其內容和行為。 請參閱 [測試所選地址的AMP電子郵件傳送](#testing-amp-delivery-for-selected-addresses).

1. 測試後，您可以向相關電子郵件提供者註冊，將您的寄件者網域新增至允許清單，即可傳送內容或行銷活動，作為AMP for Email計畫的一部分。 請參閱 [向電子郵件提供者註冊以傳送AMP電子郵件](#delivering-amp-emails-by-registering).

### 測試所選地址的AMP電子郵件傳送 {#testing-amp-delivery-for-selected-addresses}

您可以測試將動態訊息從Adobe Campaign傳送至選取的電子郵件地址。

>[!NOTE]
>
>只有Gmail和Mail.ru支援測試AMP格式。

若是Gmail，您必須先將您使用的寄件者地址新增至允許清單，才能針對您所定位的Gmail帳戶從Adobe Campaign傳送。

操作步驟：
1. 請確定已針對相關電子郵件提供者勾選啟用動態電子郵件的選項。
1. 複製傳送中顯示的寄件者地址 **[!UICONTROL From]** 欄位，並貼到電子郵件提供者帳戶設定的適當區段中。

如需詳細資訊，請參閱 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 開發人員檔案。

![](assets/amp_from_field.png)

若要測試傳送AMP電子郵件至Mail.ru地址，請遵循 [Mail.ru開發人員檔案](https://postmaster.mail.ru/amp/?lang=en#howto) (**如果您是使用者** 區段)。

### 向電子郵件提供者註冊以傳送AMP電子郵件 {#delivering-amp-emails-by-registering}

您可以向支援的電子郵件提供者註冊，以便將您的寄件者網域新增至允許清單，借此試驗傳送動態電子郵件。

>[!NOTE]
>
>只有Gmail和Mail.ru支援AMP格式。

只要用幾個地址測試，您就可以傳送AMP電子郵件至任何Gmail地址。 若要這麼做，您必須向Google註冊，並等待他們的回答。 請依照 [Gmail](https://developers.google.com/gmail/ampemail/register) 開發人員檔案。 註冊成功後，您會成為授權寄件者。

若要傳送AMP電子郵件至Mail.ru位址，請遵循 [Mail.ru開發人員檔案](https://postmaster.mail.ru/amp/?lang=en#howto) (**如果您是電子郵件寄件者** 區段)。

## 傳送AMP電子郵件 {#sending-amp-email}

一旦AMP內容和備援準備就緒，而定義相容目標後，您就可以像平常一樣傳送電子郵件。

目前，在特定條件下，僅Gmail和Mail.ru支援AMP格式。 您可以鎖定來自其他電子郵件提供者的地址，但他們會收到您電子郵件的HTML或純文字版本。

>[!IMPORTANT]
>
>若您的電子郵件除AMP內容外，不含HTML或純文字版本，則無法傳送。

相符的收件者會在其信箱中顯示電子郵件的AMP版本。

例如，如果您在電子郵件中包含產品清單，在編輯協力廠商系統中的價格時，每當您的收件者在其信箱中再次開啟電子郵件時，價格就會自動調整。

>[!NOTE]
>
>您可以建立郵件處理規則，以防止特定網域收到AMP電子郵件。 請參閱 [管理電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats).
>
>依預設， **[!UICONTROL AMP inclusion]** 選項設為 **[!UICONTROL No]**.

## 教學課程影片 {#amp-email-video}

以下影片說明如何在 Adobe Campaign 啟動 AMP，並展示其使用情形。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

提供其他Campaign作法影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
