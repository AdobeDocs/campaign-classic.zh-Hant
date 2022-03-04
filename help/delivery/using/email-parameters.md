---
product: campaign
title: 電子郵件參數
description: 瞭解特定於電子郵件傳遞的選項和設定
feature: Email
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 8%

---

# 電子郵件參數 {#email-parameters}

![](../../assets/common.svg)

本節介紹特定於電子郵件傳遞的選項和參數。

## 電子郵件密件抄送 {#email-bcc}

Adobe Campaign允許您通過密件抄送將電子郵件儲存在外部系統上，只需將密件抄送電子郵件地址添加到郵件目標。

激活該選項後，將保留所有已發送郵件的準確副本，以用於此傳遞。

有關電子郵件密件抄送配置和最佳實踐的詳細資訊，請參閱 [此部分](../../installation/using/email-archiving.md)。

>[!NOTE]
>
>電子郵件密件抄送是可選功能。 請檢查您的授權合約，並聯絡您的帳戶管理員以啟用它。

建立新交貨或交貨模板時，預設情況下不啟用「電子郵件密件抄送」。 您需要在電子郵件傳遞或傳遞模板級別手動啟用它。

>[!NOTE]
>
>如果您正在將「電子郵件密件抄送」與「增強的MTA」一起使用，則會自動為所有交貨啟用此選項。

要為電子郵件傳遞模板啟用電子郵件密件抄送，請執行以下步驟：

1. 轉到 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 或 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**。
1. 選擇您選擇的交貨或複製現成的 **電子郵件傳遞** ，然後選擇複製的模板。
1. 按一下 **屬性** 按鈕
1. 選取 **[!UICONTROL Delivery]** 索引標籤。
1. 檢查 **電子郵件密件抄送** 的雙曲餘切值。 基於此模板的每個傳遞的所有已發送郵件的副本將發送到已配置的電子郵件密件抄送地址。

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>如果開啟並按一下發送到密件抄送地址的電子郵件，則在 **[!UICONTROL Total opens]** 和 **[!UICONTROL Clicks]** 從發送分析中得出，這可能會導致一些錯誤計算。

## 選擇消息格式 {#selecting-message-formats}

您可以更改發送的電子郵件的格式。 為此，請編輯交貨屬性，然後按一下 **[!UICONTROL Delivery]** 頁籤。

![](assets/s_ncs_user_wizard_email_param.png)

在窗口的下半部分選擇電子郵件的格式：

* **[!UICONTROL Use recipient preferences]** （預設模式）

   消息格式根據儲存在接收者簡檔中並預設儲存在 **[!UICONTROL email format]** 欄位(@emailFormat)。 如果收件者希望以特定格式接收郵件，則此格式為傳送的格式。如果未填入該欄位，則會發送多部分替代消息（請參閱下文）。

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   消息包含兩種格式：文本和HTML。 接收時顯示的格式取決於收件人的郵件軟體（多部件替代）的配置。

   >[!IMPORTANT]
   >
   >此選項包括文檔的兩個版本。 因此，它會影響傳遞率，因為消息大小更大。

* **[!UICONTROL Send all messages in text format]**

   消息以文本格式發送。 HTML格式將不會發送，但僅在收件人按一下消息時用於鏡像頁。

>[!NOTE]
>
>有關定義電子郵件內容的詳細資訊，請參閱 [此部分](defining-the-email-content.md)。

## 生成鏡像頁 {#generating-mirror-page}

鏡像頁是通過Web瀏覽器線上訪問的HTML頁。 其內容與電子郵件相同。

預設情況下，如果連結插入郵件內容中，則會生成鏡像頁面。 有關個性化塊插入的詳細資訊，請參閱 [個性化塊](personalization-blocks.md)。

在交貨屬性中， **[!UICONTROL Mode]** 的 **[!UICONTROL Validity]** 頁籤中，您可以修改此頁的生成模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>必須為要建立的鏡像頁面的傳遞定義HTML內容。

除了預設模式，還提供以下選項：

* **[!UICONTROL Force the generation of the mirror page]**:即使在傳遞中未插入到鏡像頁的連結，也會建立鏡像頁。
* **[!UICONTROL Do not generate the mirror page]**:即使連結存在於傳遞中，也不會生成鏡像頁。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**:此選項允許您在傳遞日誌窗口中訪問鏡像頁的內容，其中包含個性化資訊。 要執行此操作，請在交貨結束後按一下 **[!UICONTROL Delivery]** 頁籤，然後選擇要查看其鏡像頁的收件人的行。 按一下&#x200B;**[!UICONTROL Display the mirror page for this message...]**&#x200B;連結。

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 字元編碼 {#character-encoding}

在 **[!UICONTROL SMTP]** 的子菜單。 **[!UICONTROL Character encoding]** 部分可設定特定編碼。

預設編碼為UTF-8。 如果某些收件人的電子郵件提供程式不支援UTF-8標準編碼，您可能需要設定特定編碼以正確向電子郵件收件人顯示特殊字元。

例如，您要發送包含日文字元的電子郵件。 為確保所有字元都正確顯示給您在日本的收件人，您可能希望使用支援日文字元的編碼，而不是標準UTF-8。

要執行此操作，請選擇 **[!UICONTROL Force the encoding used for messages]** 的上界 **[!UICONTROL Character encoding]** ，然後從顯示的下拉清單中選擇編碼。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 管理退回電子郵件 {#managing-bounce-emails}

的 **[!UICONTROL SMTP]** 的子菜單。

預設情況下，在平台的預設錯誤框中接收已跳轉的電子郵件，但您可以為傳遞定義特定錯誤地址。

您還可以從此螢幕定義特定地址，以便調查在應用程式無法自動限定這些郵件時退回郵件的原因。 對於每個欄位， **添加個性化欄位** 表徵圖，用於添加個性化參數。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

有關彈出郵件管理的詳細資訊，請參閱 [此部分](understanding-delivery-failures.md#bounce-mail-management)。

## 添加SMTP標頭 {#adding-smtp-headers}

可以將SMTP頭添加到您的交貨中。 為此，請使用 **[!UICONTROL SMTP]** 的子菜單。

在此窗口中輸入的指令碼必須引用以下格式的每行一個標題： **名稱：值**。

如有必要，會自動對值編碼。

>[!IMPORTANT]
>
>會為進階使用者保留新增指令碼，以便插入其他 SMTP 標題。
>
>此指令碼的語法必須符合以下內容類型的要求：沒有未使用的空間，沒有空行等。
