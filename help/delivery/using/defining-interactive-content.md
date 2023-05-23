---
product: campaign
title: 在Adobe Campaign Classic定義互動式內容
description: 瞭解如何通過Adobe Campaign的AMP定義互動式和動態電子郵件內容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email Design, Dynamic Content
exl-id: 3110c371-bbf2-4ab2-a701-3f348b5c1e7f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1499'
ht-degree: 4%

---

# 定義互動式內容{#defining-interactive-content}



Adobe Campaign使您能夠 [電子郵件的AMP](https://amp.dev/about/email/) 格式，它允許在特定條件下發送動態電子郵件。

使用AMP for E-mail，您可以：
* Test將AMP電子郵件發送到適當配置的特定地址。
* 在向相應的提供商註冊後，將AMP電子郵件發送到Gmail或Mail.ru地址。

有關測試和發送AMP電子郵件的詳細資訊，請參見 [此部分](#targeting-amp-email)。

此功能可通過Adobe Campaign的專用軟體包獲得。 根據您的權限和部署模式，您可以安裝此包或聯繫Adobe以為您安裝它。

>[!NOTE]
>
> 對於混合和托管體系結構，必須在所有伺服器上安裝軟體包，包括 [中間採購伺服器](../../installation/using/mid-sourcing-server.md) 和 [執行實例](../../message-center/using/configuring-instances.md#execution-instance)。


## 關於電子郵件的AMP {#about-amp-for-email}

使用 **電子郵件的AMP** 新格式，將AMP元件包含在您的郵件中，並通過豐富且可操作的內容改善電子郵件體驗。 透過直接在電子郵件中提供的現代化應用程式功能，收件者可以與訊息本身內容進行動態互動。

例如：
* 使用AMP編寫的電子郵件可以包含交互元素，如影像線索。
* 內容在郵件中保持最新。
* 收件人可以在不離開收件箱的情況下回復表單。

AMP for Email與現有電子郵件相容。 除HTML和/或純文字檔案外，郵件的AMP版本作為新的MIME部分嵌入到電子郵件中，確保所有電子郵件客戶端的相容性。

有關電子郵件格式、規範和要求的AMP的詳細資訊，請參見 [AMP開發人員文檔](https://amp.dev/documentation/guides-and-tutorials/learn/email-spec/amp-email-format/?format=email)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#amp-email-video)

## 將AMP用於電子郵件與Adobe Campaign {#key-steps-to-use-amp}

要成功test並向Adobe Campaign發送AMP電子郵件，請執行以下步驟：
1. 安裝 **[!UICONTROL AMP support]** 檔案。 請參閱 [安裝活動內置包](../../installation/using/installing-campaign-standard-packages.md)。
1. 在Adobe Campaign內建立電子郵件並生成AMP內容。 請參閱 [使用Adobe Campaign構建AMP電子郵件內容](#build-amp-email-content)。
1. 確保遵循支援AMP格式的電子郵件提供商的所有傳遞要求。 請參閱 [AMP以滿足電子郵件傳遞要求](#amp-for-email-delivery-requirements)。
1. 定義目標時，請確保選擇能夠顯示AMP格式的收件人。 請參閱 [瞄準AMP電子郵件](#targeting-amp-email)。

   >[!NOTE]
   >
   >目前，您只能將AMP電子郵件發送到 [特定電子郵件地址](#testing-amp-delivery-for-selected-addresses) （用於測試目的）或之後 [登記](#delivering-amp-emails-by-registering) 支援的電子郵件客戶端。

1. 按照通常的方式發送電子郵件。 請參閱 [發送AMP電子郵件](#sending-amp-email)。

## 在Adobe Campaign構建AMP電子郵件內容 {#build-amp-email-content}

要使用AMP格式生成電子郵件，請執行以下步驟。

>[!IMPORTANT]
>
>確保您遵循AMP ，瞭解電子郵件要求和規範，詳見 [AMP開發人員文檔](https://amp.dev/documentation/guides-and-tutorials/learn/email_fundamentals/?format=email)。 您還可以 [AMP用於電子郵件最佳做法](https://amp.dev/documentation/guides-and-tutorials/develop/amp_email_best_practices/?format=email)。

1. 建立電子郵件傳遞時，選擇任何模板。

   >[!NOTE]
   >
   >特定的AMP模板包含您可以使用的主要容量的示例：產品清單、旋轉盤、雙選擇加入、調查和高級伺服器請求。

1. 按一下 **[!UICONTROL AMP content]** 頁籤。

   ![](assets/amp_tab.png)

1. 編輯AMP內容以滿足您的需要。

   >[!NOTE]
   >
   >有關生成第一封AMP電子郵件的詳細資訊，請參閱 [AMP開發人員文檔](https://amp.dev/documentation/guides-and-tutorials/start/create_email/?format=email)。

   例如，您可以使用AMP模板中的產品清單元件，並維護第三方系統甚至Adobe Campaign內部的產品清單。 無論何時您調整價格或其他要素，當收件人從其郵箱開啟電子郵件時，系統會自動反映它。

1. 根據需要對AMP內容進行個性化，就像您通常在Adobe Campaign使用HTML格式時使用個性化欄位和個性化塊時那樣。

   ![](assets/amp_tab_perso.png)

1. 完成編輯後，選擇整個AMP內容並將其複製貼上到 [基於AMP Web的驗證器](https://validator.ampproject.org) 或類似網站。

   >[!NOTE]
   >
   >確保您選擇 **AMP4電子郵件** 的子菜單。

   ![](assets/amp_validator.png)

   錯誤標籤為內聯。

   >[!NOTE]
   >
   >Adobe CampaignAMP編輯器不是為內容驗證而設計的。 使用外部網站，如 [基於AMP Web的驗證器](https://validator.ampproject.org) 檢查內容是否正確。

1. 在AMP內容通過驗證之前根據需要進行修改。

   ![](assets/amp_validator_pass.png)

1. 要預覽您的內容，請將已驗證的內容複製貼上到 [AMP遊樂場](https://playground.amp.dev) 或類似網站。

   >[!NOTE]
   >
   >確保您選擇 **電子郵件的AMP** 的子菜單。

   ![](assets/amp_playground.png)

   >[!NOTE]
   >
   >您不能直接在Adobe Campaign預覽AMP內容。 使用外部網站，如 [AMP遊樂場](https://playground.amp.dev)。

1. 返回Adobe Campaign，將您已驗證的內容複製貼上到 **[!UICONTROL AMP content]** 頁籤。

1. 切換到 **[!UICONTROL HTML content]** 或 **[!UICONTROL Text content]** ，並為這兩種格式中的至少一個定義內容。

   >[!IMPORTANT]
   >
   >如果您的電子郵件除了AMP內容之外不包含HTML或純文字檔案版本，則無法發送它。

## AMP以滿足電子郵件傳遞要求 {#amp-for-email-delivery-requirements}

在Adobe Campaign構建AMP內容時，必須符合要傳遞的動態電子郵件的條件，這些條件特定於收件人的電子郵件提供商。

目前有兩個電子郵件提供商支援測試此格式：Gmail和Mail.ru。

在Gmail帳戶上testAMP格式傳送所需的所有步驟和規格在相應的 [Gmail](https://developers.google.com/gmail/ampemail?), [郵件.ru](https://postmaster.mail.ru/amp) 開發者文檔。

特別是，必須滿足以下要求：
* 遵循特定於的AMP安全要求 [Gmail](https://developers.google.com/gmail/ampemail/security-requirements), [郵件.ru](https://postmaster.mail.ru/amp/#howto)。
* AMP MIME部分必須包含 [有效的AMP文檔](https://amp.dev/documentation/guides-and-tutorials/learn/validation-workflow/validate_emails/?format=email)。
* AMP MIME部分必須小於100KB。

您還可以 [Gmail的提示和已知限制](https://developers.google.com/gmail/ampemail/tips) 文檔。

## 瞄準AMP電子郵件 {#targeting-amp-email}

目前，您可以嘗試分兩步發送AMP電子郵件：

1. Adobe Campaign使您能夠test向經過適當配置的選定電子郵件地址發送基於AMP的動態電子郵件，以驗證其內容和行為。 請參閱 [正在測試所選地址的AMP電子郵件傳遞](#testing-amp-delivery-for-selected-addresses)。

1. 測試後，您可以向相關電子郵件提供商註冊，將發件人域添加到允許清單中，從而作為電子郵件AMP程式的一部分發送遞送或活動。 請參閱 [通過向電子郵件提供商註冊來傳遞AMP電子郵件](#delivering-amp-emails-by-registering)。

### 正在測試所選地址的AMP電子郵件傳遞 {#testing-amp-delivery-for-selected-addresses}

您可以test將動態郵件從Adobe Campaign發送到選定的電子郵件地址。

>[!NOTE]
>
>只有Gmail和Mail.ru支援測試AMP格式。

對於Gmail，必須先將您正在使用的發件人地址添加到允許清單中，以便從Adobe Campaign為您目標的Gmail帳戶發送郵件。

操作步驟：
1. 確保為相關電子郵件提供程式選中啟用動態電子郵件的選項。
1. 複製交貨中顯示的發件人地址 **[!UICONTROL From]** 欄位並將其貼上到電子郵件提供商帳戶設定的相應部分。

有關詳細資訊，請參閱 [Gmail](https://developers.google.com/gmail/ampemail/testing-dynamic-email) 開發人員文檔。

![](assets/amp_from_field.png)

要test將AMP電子郵件發送到Mail.ru地址，請按照 [Mail.ru開發人文檔](https://postmaster.mail.ru/amp/#howto) (**如果您是用戶** )的正平方根。

### 通過向電子郵件提供商註冊來傳遞AMP電子郵件 {#delivering-amp-emails-by-registering}

您可以嘗試通過向受支援的電子郵件提供程式註冊來傳遞動態電子郵件，以便將您的發件人域添加到允許清單。

>[!NOTE]
>
>只有Gmail和Mail.ru支援AMP格式。

經過幾個地址的測試後，您可以向任何Gmail地址發送AMP電子郵件。 要做到這一點，你必須向Google註冊，等待他們的答案。 按照中介紹的步驟操作 [Gmail](https://developers.google.com/gmail/ampemail/register) 開發人員文檔。 註冊成功後，您將成為授權發件人。

要將AMP電子郵件發送到Mail.ru地址，請遵循中列出的要求和步驟 [Mail.ru開發人文檔](https://postmaster.mail.ru/amp/#howto) (**如果您是電子郵件發件人** )的正平方根。

## 發送AMP電子郵件 {#sending-amp-email}

一旦AMP內容和備用準備就緒，並且定義了相容目標後，您就可以像通常一樣發送電子郵件。

目前，在某些條件下，只有Gmail和Mail.ru支援AMP格式。 您可以瞄準來自其他電子郵件提供商的地址，但他們將接收您的電子郵件的HTML或純文字檔案版本。

>[!IMPORTANT]
>
>如果您的電子郵件除了AMP內容之外不包含HTML或純文字檔案版本，則無法發送它。

匹配的收件人的郵箱中將顯示電子郵件的AMP版本。

例如，如果您在電子郵件中包含產品清單，則在編輯第三方系統中的價格時，每次收件人在其郵箱中再次開啟電子郵件時，價格將自動調整。

>[!NOTE]
>
>您可以建立郵件處理規則，以阻止特定域接收AMP電子郵件。 請參閱 [管理電子郵件格式](../../installation/using/email-deliverability.md#managing-email-formats)。
>
>預設情況下， **[!UICONTROL AMP inclusion]** 選項設定為 **[!UICONTROL No]**。

## 教程視頻 {#amp-email-video}

以下影片說明如何在 Adobe Campaign 啟動 AMP，並展示其使用情形。

>[!VIDEO](https://video.tv.adobe.com/v/29940?quality=12&learn=on)

還提供了其他市場活動操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
