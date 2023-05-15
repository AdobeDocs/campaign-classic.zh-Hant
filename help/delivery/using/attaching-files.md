---
product: campaign
title: 附加檔案
description: 附加檔案
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email
exl-id: db65e83e-276f-4163-98c3-3658a48acffc
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 5%

---

# 將檔案附加至電子郵件{#attaching-files}



## 關於電子郵件附件 {#about-email-attachments}

您可以將一或多個檔案附加至電子郵件傳送。

>[!NOTE]
>
>為避免出現效能問題，建議每封電子郵件不要包含多個附件。建議的臨界值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).

可能有兩種情況：

* 選取檔案，並依原樣將其附加至傳送。
* 為每個收件者個人化附件的內容。 在此情況下，您需要建立 **計算附件**:根據收件者，在傳送每則訊息時計算附件的名稱。 如果您有 **可變數字打印** 選項。

>[!NOTE]
>
>這類設定通常會在傳送範本中執行。 有關詳細資訊，請參閱 [關於範本](about-templates.md).

## 附加本地檔案 {#attaching-a-local-file}

若要將本機檔案附加至傳送，請遵循下列步驟。

>[!NOTE]
>
>您可以將數個檔案附加至傳送。 附件可以是任何格式，包括壓縮格式。

1. 按一下&#x200B;**[!UICONTROL Attachments]**&#x200B;連結。
1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 按一下 **[!UICONTROL File...]** 來選取要附加至傳送的檔案。

   ![](assets/s_ncs_user_wizard_email_attachement.png)

您也可以直接將檔案拖放至傳送中 **[!UICONTROL Attachments]** 欄位，或使用 **[!UICONTROL Attach]** 圖示，

![](assets/s_ncs_user_wizard_add_file_ico.png)

選取檔案後，會立即上傳至伺服器，供傳送時使用。 它會列於 **[!UICONTROL Attachments]** 欄位。

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## 建立計算附件 {#creating-a-calculated-attachment}

建立計算的附件時，可以在分析或傳送每則郵件時計算附件的名稱，而且取決於收件者。 您也可以個人化並轉換為PDF。

![](assets/s_ncs_user_wizard_attachment.png)

若要建立個人化附件，請遵循下列步驟：

1. 按一下&#x200B;**[!UICONTROL Attachments]**&#x200B;連結。
1. 按一下 **[!UICONTROL Add]** 按鈕，然後選取 **[!UICONTROL Calculated attachment]**.
1. 從 **[!UICONTROL Type]** 下拉式清單：

![](assets/s_ncs_user_wizard_email01_136.png)

可以使用以下選項：

* **建立傳遞範本時所指定的檔案名稱**
* **在傳送每則訊息期間，檔案的內容會個人化並轉換為PDF**
* **檔案名稱會在傳送分析期間計算（不能取決於收件者設定檔）**
* **檔案名稱是在每個收件者傳送時計算（取決於收件者）**

### 附加本機檔案 {#attach-a-local-file}

如果附件是本地檔案，請選取選項： **[!UICONTROL File name is specified when creating the delivery template]**. 檔案會在本機選取並上傳至伺服器。 請遵循以下步驟：

1. 選取要在 **[!UICONTROL Local file]** 欄位。
1. 視需要指定標籤。 在傳訊系統中檢視時，標籤會取代檔案名稱。 如果未指定任何內容，預設會使用檔案名稱。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. 如有必要，請選取 **[!UICONTROL Upload file on the server]**，然後按一下 **[!UICONTROL Update on server]** 開始轉移。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

然後，檔案便可在伺服器上附加至從此範本建立的不同傳送。

### 附加個人化訊息 {#attach-a-personalized-message}

選項 **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** 可讓您選取包含個人化欄位的檔案，例如預期收件者的姓氏和名字。

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

對於此類型的附件，應用以下配置步驟：

1. 選取要上傳的檔案。
1. 視需要指定標籤。
1. 選擇 **[!UICONTROL Upload file on the server]**，然後按一下 **[!UICONTROL Update on server]** 開始轉移。
1. 您可以顯示預覽。 若要這麼做，請選取收件者。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. 分析您的傳送內容，然後開始。

   每個收件者都會收到附加至傳送的個人化PDF。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

>[!NOTE]
>
>為避免效能問題，如果您包含從個人化URL即時下載的影像作為附件，則每個影像大小預設不應超過100,000位元組。 此建議的臨界值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery).

### 附加計算檔案 {#attach-a-calculated-file}

您可以在傳送準備期間計算附件名稱。 若要這麼做，請選取選項 **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**.

>[!NOTE]
>
>只有由外部程式或工作流程傳送傳遞時，才會使用此選項。

1. 指定要應用於附件的標籤。
1. 在定義視窗中指定檔案的存取路徑及其確切名稱。

   >[!IMPORTANT]
   >
   >檔案必須存在於伺服器上。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. 分析，然後開始傳送。

   檔案名計算可在分析日誌中查看。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### 附加個人化檔案 {#attach-a-personalized-file}

選取附件時，您可以選取選項 **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**. 然後，您可以將收件者個人化資料與要傳送的檔案名稱對應。

>[!NOTE]
>
>只有由外部程式或工作流程傳送傳遞時，才會使用此選項。

1. 指定要應用於附件的標籤。
1. 在定義視窗中指定檔案的存取路徑及其確切名稱。 如果檔案名稱是個人化的，您可以使用「個人化」欄位來取得相關值。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >檔案必須存在於伺服器上。

1. 分析，然後開始傳送。

   在以下示例中，根據使用合併欄位定義的檔案名稱選擇附加檔案。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### 附件設定 {#attachment-settings}

對於前兩個選項，您可以選取 **[!UICONTROL Upload file on the server]** ，方法是選取適當的選項。 此 **[!UICONTROL Update the file on the server]** 連結可讓您開始上傳。

![](assets/s_ncs_user_wizard_email01_137.png)

訊息會告訴您檔案已上傳至伺服器：

![](assets/s_ncs_user_wizard_email01_1371.png)

對於檔案的更改，將顯示一條警告消息：

![](assets/s_ncs_user_wizard_email01_1372.png)

此 **[!UICONTROL Advanced]** 索引標籤可讓您定義附加檔案的進階選項：

* 您可以定義篩選選項，以避免將附加的檔案傳送給所有收件者。 選項 **[!UICONTROL Enable filtering of recipients who will receive the attachment]** 啟用輸入欄位，用於定義收件者選擇指令碼，該指令碼必須在JavaScript中輸入。
* 您可以編寫檔案名稱的指令碼，以便個人化該檔案。

   在視窗中輸入文字，然後使用下拉式清單中可用的個人化欄位。 在下列範例中，檔案名稱會個人化，以包含今天的日期和收件者的名稱。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
