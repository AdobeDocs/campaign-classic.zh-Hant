---
product: campaign
title: 附加檔案
description: 附加檔案
feature: Email
exl-id: db65e83e-276f-4163-98c3-3658a48acffc
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 2%

---

# 將檔案附加到電子郵件{#attaching-files}

![](../../assets/common.svg)

## 關於電子郵件附件 {#about-email-attachments}

您可以將一個或多個檔案附加到電子郵件傳遞。

>[!NOTE]
>
>為避免效能問題，建議每封電子郵件不要包含多個附件。 建議的閾值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery)。

可能有兩種情況：

* 選擇一個檔案，並按原樣將其附加到交貨。
* 個性化每個收件人的附件內容。 在這種情況下，您需要建立 **計算附件**:附件的名稱在每封郵件發送時計算，具體取決於收件人。 如果您具有以下功能，則還可以個性化內容並在交付時轉換為PDF格式 **可變數字打印** 的雙曲餘切值。

>[!NOTE]
>
>此類配置通常在交付模板中執行。 有關此內容的詳細資訊，請參閱 [關於模板](about-templates.md)。

## 附加本地檔案 {#attaching-a-local-file}

要將本地檔案附加到傳遞，請執行以下步驟。

>[!NOTE]
>
>您可以將多個檔案附加到傳遞。 附件可以採用任何格式，包括壓縮格式。

1. 按一下&#x200B;**[!UICONTROL Attachments]**&#x200B;連結。
1. 按一下 **[!UICONTROL Add]** 按鈕。
1. 按一下 **[!UICONTROL File...]** ，也請參見Wiki頁。

   ![](assets/s_ncs_user_wizard_email_attachement.png)

也可以直接將檔案拖放到傳遞中 **[!UICONTROL Attachments]** ，或使用 **[!UICONTROL Attach]** 表徵圖

![](assets/s_ncs_user_wizard_add_file_ico.png)

一旦選擇了該檔案，它就會立即上載到伺服器，以便在交付時可用。 它列在 **[!UICONTROL Attachments]** 的子菜單。

![](assets/s_ncs_user_wizard_email_attachement_e.png)

## 建立計算附件 {#creating-a-calculated-attachment}

建立計算的附件時，附件的名稱可以在分析或傳遞每封郵件時計算，並可以取決於收件人。 還可以個性化並轉換為PDF。

![](assets/s_ncs_user_wizard_attachment.png)

要建立個性化附件，請執行以下步驟：

1. 按一下&#x200B;**[!UICONTROL Attachments]**&#x200B;連結。
1. 按一下 **[!UICONTROL Add]** ，然後選擇 **[!UICONTROL Calculated attachment]**。
1. 從 **[!UICONTROL Type]** 下拉清單：

![](assets/s_ncs_user_wizard_email01_136.png)

可以使用以下選項：

* **建立傳遞模板時指定檔案名**
* **在傳送每個消息期間，檔案的內容被個性化並轉換為PDF**
* **檔案名是在傳遞分析期間計算的（它不能取決於收件人配置檔案）**
* **檔案名是在每個收件人（可能取決於收件人）交付時計算的**

### 附加本地檔案 {#attach-a-local-file}

如果附件是本地檔案，則選擇以下選項： **[!UICONTROL File name is specified when creating the delivery template]**。 檔案在本地選擇並上載到伺服器。 請遵循以下步驟：

1. 選擇要在 **[!UICONTROL Local file]** 的子菜單。
1. 如有必要，請指定標籤。 在消息傳遞系統中查看時，標籤將替換檔案名。 如果未指定任何內容，則預設使用檔案名。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_02.png)

1. 如有必要，請選擇 **[!UICONTROL Upload file on the server]**，然後按一下 **[!UICONTROL Update on server]** 來啟動傳輸。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_01.png)

然後，該檔案在伺服器上可用，可連接到從此模板建立的不同交貨。

### 附加個性化消息 {#attach-a-personalized-message}

選項 **[!UICONTROL The file content is personalized and converted into PDF format at the time of delivery for each message]** 允許您選擇具有個性化欄位的檔案，如目標收件人的姓和名。

![](assets/s_ncs_user_wizard_email_calc_attachement_06.png)

對於此類附件，應用以下配置步驟：

1. 選擇要上載的檔案。
1. 如有必要，請指定標籤。
1. 選擇 **[!UICONTROL Upload file on the server]**，然後按一下 **[!UICONTROL Update on server]** 來啟動傳輸。
1. 可以顯示預覽。 要執行此操作，請選擇收件人。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_07.png)

1. 分析您的交貨，然後開始。

   每個接收者接收附於遞送的個性化PDF。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_08.png)

>[!NOTE]
>
>為避免效能問題，如果您將從個性化URL動態下載的影像作為附件，則預設情況下每個影像大小不應超過100,000位元組。 此建議的閾值可從 [Campaign Classic選項清單](../../installation/using/configuring-campaign-options.md#delivery)。

### 附加計算檔案 {#attach-a-calculated-file}

在交付準備期間，可以計算附件名稱。 要執行此操作，請選擇選項 **[!UICONTROL The file name is calculated during delivery analysis (it cannot depend on the recipient)]**。

>[!NOTE]
>
>此選項僅在外部進程或工作流發送交貨時使用。

1. 指定要應用於附件的標籤。
1. 在定義窗口中指定檔案的訪問路徑及其確切名稱。

   >[!IMPORTANT]
   >
   >伺服器上必須存在該檔案。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_04.png)

1. 分析並開始交付。

   在分析日誌中可以看到檔案名計算。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_05.png)

### 附加個性化檔案 {#attach-a-personalized-file}

選擇附件時，可以選擇選項 **[!UICONTROL The file name is calculated during delivery for each recipient (it can depend on the recipient)]**。 然後，可以使用要發送的檔案的名稱映射收件人個性化資料。

>[!NOTE]
>
>此選項僅在外部進程或工作流發送交貨時使用。

1. 指定要應用於附件的標籤。
1. 在定義窗口中指定檔案的訪問路徑及其確切名稱。 如果檔案名是個性化的，則可以使用「個性化」欄位來獲取相關值。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_010.png)

   >[!IMPORTANT]
   >
   >伺服器上必須存在該檔案。

1. 分析並開始交付。

   在下例中，根據使用合併欄位定義的附件名稱選擇附件。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_011.png)

### 附件設定 {#attachment-settings}

對於前兩個選項，您可以 **[!UICONTROL Upload file on the server]** 的雙曲餘切值。 的 **[!UICONTROL Update the file on the server]** 連結可以開始上載。

![](assets/s_ncs_user_wizard_email01_137.png)

一條消息告訴您檔案已上載到伺服器：

![](assets/s_ncs_user_wizard_email01_1371.png)

對於檔案更改，將顯示一條警告消息：

![](assets/s_ncs_user_wizard_email01_1372.png)

的 **[!UICONTROL Advanced]** 頁籤中，您可以定義附加檔案的高級選項：

* 您可以定義篩選器選項，以避免將附加檔案發送到所有收件人。 選項 **[!UICONTROL Enable filtering of recipients who will receive the attachment]** 激活用於定義收件人選擇指令碼的輸入欄位，該指令碼必須在JavaScript中輸入。
* 您可以編寫檔案名稱的指令碼，以便對其進行個性化設定。

   在窗口中輸入文本，然後使用下拉清單中可用的個性化欄位。 在以下示例中，檔案名是個性化的，它包含今天的日期和收件人的名稱。

   ![](assets/s_ncs_user_wizard_email_calc_attachement_09.png)
