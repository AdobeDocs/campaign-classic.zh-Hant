---
product: campaign
title: 電子郵件參數
description: 瞭解電子郵件傳送的專屬選項和設定
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email
exl-id: 1bb36e71-9f1a-4553-b266-eca3f48688e2
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '900'
ht-degree: 14%

---

# 電子郵件參數 {#email-parameters}



本節介紹專用於電子郵件傳送的選項和引數。

## 電子郵件密件副本 {#email-bcc}

Adobe Campaign可讓您只要新增密件副本電子郵件地址至訊息目標，即可透過密件副本將電子郵件儲存在外部系統上。

一旦啟用選項，將會為此傳遞保留所有已傳送訊息的精確副本。

有關電子郵件密件副本設定和最佳實務的詳細資訊，請參閱 [本節](../../installation/using/email-archiving.md).

>[!NOTE]
>
>電子郵件密件副本為選購功能。 請檢查您的授權合約，並聯絡您的帳戶管理員以啟用它。

建立新傳遞或傳遞範本時，預設不會啟用電子郵件密件副本。 您必須在電子郵件傳遞或傳遞範本層級手動啟用。

>[!NOTE]
>
>如果您使用具有增強型MTA的電子郵件密件副本，此選項會自動針對所有傳送啟用。

若要為電子郵件傳遞範本啟用電子郵件密件副本，請遵循下列步驟：

1. 前往 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 或 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**.
1. 選取您選擇的傳遞專案或複製現成可用的傳遞專案 **電子郵件傳遞** 範本，然後選取複製的範本。
1. 按一下 **屬性** 按鈕。
1. 選取 **[!UICONTROL Delivery]** 索引標籤。
1. 檢查 **電子郵件密件副本** 選項。 系統會根據此範本，將每次傳遞的所有已傳送訊息副本傳送至已設定的電子郵件密件副本地址。

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>如果傳送至密件副本地址的電子郵件被開啟並按過，這將會在 **[!UICONTROL Total opens]** 和 **[!UICONTROL Clicks]** 傳送分析，這可能會導致某些計算錯誤。

## 選取訊息格式 {#selecting-message-formats}

您可以變更已傳送電子郵件訊息的格式。 若要這麼做，請編輯傳送屬性，然後按一下 **[!UICONTROL Delivery]** 標籤。

![](assets/s_ncs_user_wizard_email_param.png)

在視窗的下半部分選取電子郵件的格式：

* **[!UICONTROL Use recipient preferences]** （預設模式）

   訊息格式會根據儲存在收件者設定檔中的資料定義，並預設會儲存在 **[!UICONTROL email format]** 欄位(@emailFormat)。 如果收件者希望以特定格式接收郵件，則此格式為傳送的格式。如果未填入欄位，則會傳送替代的多重部分訊息（請參閱下文）。

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   訊息包含兩種格式：文字和HTML。 接收時顯示的格式取決於收件者的郵件軟體設定（替代的多重部分）。

   >[!IMPORTANT]
   >
   >此選項包含檔案的兩個版本。 因此，它會影響傳遞率，因為郵件大小較大。

* **[!UICONTROL Send all messages in text format]**

   訊息會以文字格式傳送。 不會傳送HTML格式，但只有當收件者按一下郵件時，才會用於映象頁面。

>[!NOTE]
>
>如需定義電子郵件內容的詳細資訊，請參閱 [本節](defining-the-email-content.md).

## 產生映象頁面 {#generating-mirror-page}

鏡像頁面是可透過網頁瀏覽器線上存取的 HTML 頁面。其內容與電子郵件相同。

依預設，如果將連結插入郵件內容中，則會產生鏡像頁面。如需個人化區塊插入的詳細資訊，請參閱 [個人化區塊](personalization-blocks.md).

在傳遞屬性中， **[!UICONTROL Mode]** 的欄位 **[!UICONTROL Validity]** 索引標籤可讓您修改此頁面的產生模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>必須已針對傳遞定義HTML內容，才能建立映象頁面。

除預設模式之外，還有提供以下選項：

* **[!UICONTROL Force the generation of the mirror page]**：即使傳送中未插入映象頁面的連結，也會建立映象頁面。
* **[!UICONTROL Do not generate the mirror page]**：不會產生任何映象頁面，即使傳送中存在連結亦然。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**：此選項可讓您在傳送記錄視窗中存取包含個人化資訊的映象頁面內容。 若要這麼做，請在傳送結束後，按一下 **[!UICONTROL Delivery]** 索引標籤並選取您要檢視其映象頁面的收件者行。 按一下&#x200B;**[!UICONTROL Display the mirror page for this message...]**&#x200B;連結。

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 字元編碼 {#character-encoding}

在 **[!UICONTROL SMTP]** 標籤中， **[!UICONTROL Character encoding]** 區段可讓您設定特定編碼。

預設編碼為UTF-8。 如果部分收件者的電子郵件提供者不支援UTF-8標準編碼，您可能想要設定特定編碼，以正確向電子郵件的收件者顯示特殊字元。

例如，您想要傳送包含日文字元的電子郵件。 為確保所有字元都能正確顯示給在日本的收件者，您可能想要使用可支援日文字元的編碼，而不是標準UTF-8。

若要這麼做，請選取 **[!UICONTROL Force the encoding used for messages]** 中的選項 **[!UICONTROL Character encoding]** 區段，然後從顯示的下拉式清單中選擇編碼。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 管理退信電子郵件 {#managing-bounce-emails}

此 **[!UICONTROL SMTP]** 傳遞引數的索引標籤可讓您設定退回郵件的管理。

依預設，會在平台的預設錯誤方塊中接收跳出的電子郵件，但您可以定義傳送的特定錯誤地址。

您也可以從此畫面定義特定地址，以便調查當應用程式無法自動限定這些郵件時退回郵件的原因。 對於每個欄位， **新增個人化欄位** 圖示可讓您新增個人化引數。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

有關退回郵件管理的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#bounce-mail-management).

## 新增SMTP標頭 {#adding-smtp-headers}

您可以將SMTP標頭新增至您的傳遞。 若要這麼做，請使用 **[!UICONTROL SMTP]** 索引標籤進行標籤。

在此視窗中輸入的指令碼必須參考下清單單中每行的一個標題： **name：value**.

如有必要，會自動對值編碼。

>[!IMPORTANT]
>
>會為進階使用者保留新增指令碼，以便插入其他 SMTP 標題。
>
>此指令碼的語法必須符合以下內容類型的要求：沒有未使用的空間，沒有空行等。
