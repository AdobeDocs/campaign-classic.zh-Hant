---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic中設定電子郵件參數
description: 瞭解電子郵件傳送的特定選項和設定。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: e84387c7c396c60c429c3f625870a97a7fdaef5a
workflow-type: tm+mt
source-wordcount: '888'
ht-degree: 8%

---


# 電子郵件參數{#email-parameters}

本節介紹電子郵件傳送的特定選項和參數。

## 電子郵件密件副本{#email-bcc}

Adobe Campaign可讓您透過密件副本將電子郵件儲存在外部系統上，只需將密件副本電子郵件地址新增至訊息目標即可。

在啟動選項後，所有已傳送訊息的完整副本都會保留在此傳送中。

有關電子郵件密件副本配置和最佳實踐的詳細資訊，請參閱[本節](../../installation/using/email-archiving.md)。

>[!NOTE]
>
>電子郵件密件副本是一項可選功能。 請檢查您的授權合約，並聯絡您的帳戶管理員以啟用它。

在建立新的傳送或傳送範本時，預設不會啟用電子郵件密件副本。 您必須在電子郵件傳送或傳送範本層級手動啟用它。

若要啟用電子郵件傳送範本的電子郵件密件副本，請遵循下列步驟：

1. 前往&#x200B;**[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]**&#x200B;或&#x200B;**[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**。
1. 選擇您選擇的傳送或複製現成可用的&#x200B;**電子郵件傳送**&#x200B;範本，然後選取複製的範本。
1. 按一下&#x200B;**屬性**&#x200B;按鈕。
1. 選取 **[!UICONTROL Delivery]** 索引標籤。
1. 選中&#x200B;**電子郵件密件副本**&#x200B;選項。 根據此範本，每個傳送的所有已傳送訊息副本都會傳送至已設定的電子郵件密件副本地址。

   ![](assets/s_ncs_user_wizard_archiving.png)

>[!NOTE]
>
>如果已開啟並點進傳送至密件副本位址的電子郵件，則會在傳送分析的&#x200B;**[!UICONTROL Total opens]**&#x200B;和&#x200B;**[!UICONTROL Clicks]**&#x200B;中考慮此問題，這可能會造成一些誤算。

## 選擇消息格式{#selecting-message-formats}

您可以變更傳送的電子郵件格式。 若要這麼做，請編輯傳送屬性，然後按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤。

![](assets/s_ncs_user_wizard_email_param.png)

在窗口的下半部選擇電子郵件格式：

* **[!UICONTROL Use recipient preferences]** （預設模式）

   消息格式根據儲存在收件人配置檔案中的資料定義，並預設儲存在&#x200B;**[!UICONTROL email format]**&#x200B;欄位(@emailFormat)中。 如果收件者希望以特定格式接收郵件，則此格式為傳送的格式。如果未填入欄位，則會傳送多部分替代訊息（請參閱下文）。

* **[!UICONTROL Let recipient mail client choose the most appropriate format]**

   訊息包含兩種格式：文字和HTML。 接收上顯示的格式取決於收件人郵件軟體的配置（多部分替代）。

   >[!IMPORTANT]
   >
   >此選項包括文檔的兩個版本。 因此，它會影響傳送率，因為訊息大小較大。

* **[!UICONTROL Send all messages in text format]**

   訊息會以文字格式傳送。 HTML格式不會傳送，但只有在收件者點按訊息時，才會用於鏡像頁面。

>[!NOTE]
>
>如需定義電子郵件內容的詳細資訊，請參閱[本節](../../delivery/using/defining-the-email-content.md)。

## 生成鏡像頁{#generating-mirror-page}

鏡像頁是可通過Web瀏覽器線上上訪問的HTML頁。 其內容與電子郵件相同。

預設情況下，如果連結插入郵件內容中，將生成鏡像頁。 有關個人化塊插入的詳細資訊，請參閱[個人化塊](../../delivery/using/personalization-blocks.md)。

在傳送屬性中， **[!UICONTROL Validity]**&#x200B;標籤的&#x200B;**[!UICONTROL Mode]**&#x200B;欄位可讓您修改此頁面的產生模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!IMPORTANT]
>
>必須已定義HTML內容，才能傳送要建立的鏡像頁面。

除了預設模式外，還提供下列選項：

* **[!UICONTROL Force the generation of the mirror page]**:即使傳送中未插入鏡像頁面的連結，也會建立鏡像頁面。
* **[!UICONTROL Do not generate the mirror page]**:不會產生任何鏡像頁面，即使連結存在於傳送中亦然。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]**:此選項可讓您在傳送記錄視窗中存取包含個人化資訊的鏡像頁面內容。若要這麼做，請在傳送結束後，按一下&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤，並選取您要檢視其鏡像頁面的收件者行。 按一下&#x200B;**[!UICONTROL Display the mirror page for this message...]**&#x200B;連結。

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 字元編碼{#character-encoding}

在傳送參數的&#x200B;**[!UICONTROL SMTP]**&#x200B;標籤中， **[!UICONTROL Character encoding]**&#x200B;區段可讓您設定特定編碼。

預設編碼為UTF-8。 如果某些收件者的電子郵件提供者不支援UTF-8標準編碼，您可能想要設定特定編碼，以正確顯示特殊字元給電子郵件的收件者。

例如，您想傳送包含日文字元的電子郵件。 為確保所有字元都能正確顯示給日本的收件者，您可能想要使用支援日文字元的編碼，而非標準UTF-8。

若要這麼做，請在&#x200B;**[!UICONTROL Character encoding]**&#x200B;區段中選取&#x200B;**[!UICONTROL Force the encoding used for messages]**&#x200B;選項，然後從顯示的下拉式清單中選擇編碼。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 管理反彈電子郵件{#managing-bounce-emails}

傳送參數的&#x200B;**[!UICONTROL SMTP]**&#x200B;標籤可讓您設定彈回郵件的管理。

依預設，已拒絕的電子郵件會在平台的預設錯誤方塊中收到，但您可以定義傳送的特定錯誤位址。

您也可以從此螢幕定義特定位址，以調查當應用程式無法自動限定反彈電子郵件的原因。 對於這些欄位，**新增個人化欄位**&#x200B;圖示可讓您新增個人化參數。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

有關彈回郵件管理的詳細資訊，請參閱[本節](../../delivery/using/understanding-delivery-failures.md#bounce-mail-management)。

## 添加SMTP標頭{#adding-smtp-headers}

可以將SMTP標頭添加到您的交貨中。 若要這麼做，請使用傳送中&#x200B;**[!UICONTROL SMTP]**&#x200B;標籤的相關章節。

在此窗口中輸入的指令碼必須引用以下格式的每行一個標題：**name:value**。

如有必要，會自動對值編碼。

>[!IMPORTANT]
>
>會為進階使用者保留新增指令碼，以便插入其他 SMTP 標題。
>
>此指令碼的語法必須符合以下內容類型的要求：沒有未使用的空間，沒有空行等。
