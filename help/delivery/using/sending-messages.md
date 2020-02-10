---
title: 使用Adobe Campaign Classic傳送電子郵件
description: 瞭解Adobe Campaign Classic中傳送電子郵件的特定參數。
page-status-flag: never-activated
uuid: 791f7a54-3225-46ca-ad6f-6c32e9c62d75
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: e2dd8161-fe38-48bf-a288-8ec328b2660e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7c800c20fff89b97f6fa38b3c659ca765765e157

---


# 傳送電子郵件{#sending-an-email}

若要核准您的電子郵件並傳送給所建立傳送的收件者，請按一下 **[!UICONTROL Send]**。

驗證和傳送傳送時的詳細程式會列於以下各節：

* [驗證傳送](../../delivery/using/steps-validating-the-delivery.md)
* [傳送傳送](../../delivery/using/steps-sending-the-delivery.md)

以下各節將詳細說明傳送電子郵件的特定參數。

## 封存電子郵件 {#archiving-emails}

Adobe Campaign可讓您透過密件副本將電子郵件儲存在外部系統上，只需將密件副本電子郵件地址新增至訊息目標即可。 在啟動選項後，所有已傳送訊息的完整副本都會保留在此傳送中。

如需設定電子郵件密件副本的詳細資訊，請參 [閱本節](../../installation/using/email-archiving.md)。

>[!NOTE]
>
>此功能為選擇性。 請檢查您的授權合約，並聯絡您的帳戶管理員以啟用它。

在建立新的傳送或傳送範本時，即使已購買選項，依預設不會啟用電子郵件密件副本。 您必須在每個要使用的傳送或範本中手動啟用它。

要執行此操作，請遵循下列步驟：

1. 前往 **[!UICONTROL Campaign Management]** > **[!UICONTROL Deliveries]** 或 **[!UICONTROL Resources]** > **[!UICONTROL Templates]** > **[!UICONTROL Delivery templates]**。
1. 選擇您選擇的傳送方式或複製現成可用的 **電子郵件傳送** ，然後選取複製的範本。
1. Click the **Properties** button.
1. 選擇選 **[!UICONTROL Delivery]** 項卡。
1. 勾選「封 **存電子郵件** 」方塊，以保留所有已傳送訊息的復本，以供此傳送或依據此範本傳送。

   ![](assets/s_ncs_user_wizard_archiving.png)

   >[!NOTE]
   >
   >如果開啟並點進傳送至密件副本位址的電子郵件，則會在傳送分析中考慮 **[!UICONTROL Total opens]** 這 **[!UICONTROL Clicks]** 一點，這可能會造成一些誤算。

## 生成鏡像頁 {#generating-the-mirror-page}

鏡像頁是可通過Web瀏覽器線上上訪問的HTML頁。 其內容與電子郵件相同。

預設情況下，如果連結插入郵件內容中，將生成鏡像頁。 有關個人化區塊插入的詳細資訊，請參 [閱個人化區塊](../../delivery/using/personalization-blocks.md)。

在傳送屬性中，標 **[!UICONTROL Mode]** 簽欄位可 **[!UICONTROL Validity]** 讓您修改此頁面的產生模式。

![](assets/s_ncs_user_wizard_miror_page_mode.png)

>[!CAUTION]
>
>必須已定義HTML內容，才能傳送要建立的鏡像頁面。

除了預設模式外，還提供下列選項：

* **[!UICONTROL Force the generation of the mirror page]** :即使傳送中未插入鏡像頁面的連結，也會建立鏡像頁面。
* **[!UICONTROL Do not generate the mirror page]** :不會產生任何鏡像頁面，即使連結存在於傳送中亦然。
* **[!UICONTROL Generates a mirror page accessible using only the message identifier]** :此選項可讓您在傳送記錄視窗中存取包含個人化資訊的鏡像頁面內容。 若要這麼做，請在傳送結束後，按一下標 **[!UICONTROL Delivery]** 簽，並選取您要檢視其鏡像頁面的收件者行。 按一下 **[!UICONTROL Display the mirror page for this message...]** 連結。

   ![](assets/s_ncs_user_wizard_miror_page_link.png)

## 管理反彈電子郵件 {#managing-bounce-emails}

傳送 **[!UICONTROL SMTP]** 參數的標籤可讓您設定彈回郵件的管理。

![](assets/s_ncs_user_email_del_properties_smtp_tab.png)

依預設，已拒絕的電子郵件會在平台的預設錯誤方塊中收到，但您可以定義傳送的特定錯誤位址。

您也可以從此螢幕定義特定位址，以調查當應用程式無法自動限定反彈電子郵件的原因。 對於這些欄位，「新增個人化欄位」圖示可讓您新增個人化參數。

## 字元編碼 {#character-encoding}

在傳送 **[!UICONTROL SMTP]** 參數的標籤中，區段 **[!UICONTROL Character encoding]** 可讓您設定特定編碼。

預設編碼為UTF-8。 如果某些收件者的電子郵件提供者不支援UTF-8標準編碼，您可能想要設定特定編碼，以正確顯示特殊字元給電子郵件的收件者。

例如，您想傳送包含日文字元的電子郵件。 為確保所有字元都能正確顯示給日本的收件者，您可能想要使用支援日文字元的編碼，而非標準UTF-8。

若要這麼做，請選 **[!UICONTROL Force the encoding used for messages]** 取區段中的 **[!UICONTROL Character encoding]** 選項，然後從顯示的下拉式清單中選擇編碼。

![](assets/s_ncs_user_email_del_properties_smtp_tab_encoding.png)

## 添加SMTP標頭 {#adding-smtp-headers}

可以將SMTP標頭添加到您的交貨中。 若要這麼做，請使用傳送中標 **[!UICONTROL SMTP]** 簽的相關區段。

在此窗口中輸入的指令碼必須引用以下格式的每行一個標題： **名稱：值**。

如有必要，值會自動編碼。

>[!CAUTION]
>
>為高級用戶保留添加用於插入其他SMTP標頭的指令碼。
>
>此指令碼的語法必須符合以下內容類型的要求：沒有未使用的空間，沒有空行等。
