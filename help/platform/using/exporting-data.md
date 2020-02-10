---
title: 匯出資料
seo-title: 匯出資料
description: 匯出資料
seo-description: null
page-status-flag: never-activated
uuid: 818de79a-587f-4735-b333-4bc702c3b450
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
discoiquuid: fecadb66-b81d-4fb6-9971-7bfd024d70b7
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 0ce6e5277c32bc18c20dca62e5b276f654d1ace5

---


# 匯出資料{#exporting-data}

## 匯出精靈 {#export-wizard}

匯出參數通過精靈記錄。通用匯出模組作為標準提供，允許您從資料庫存取和提取資料：聯繫人、客戶、清單、細分等。例如，在試算表中使用廣告系列追蹤資料 (追蹤歷史記錄等) 非常有用。輸出資料可以是 txt、CSV、TAB 或 XML 格式。

### 第 1 步 - 選擇匯出範本 {#step-1---choosing-the-export-template}

啟動匯出精靈時，首先必須選擇範本。例如，要配置最近註冊的收件者的匯出，請按照以下步驟操作：

1. 選擇文 **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** 件夾。
1. 點擊&#x200B;**新建**，然後點擊&#x200B;**匯出**&#x200B;以建立匯出範本。

   ![](assets/s_ncs_user_export_wizard01.png)

1. Click the arrow to the right of the **[!UICONTROL Export template]** field to select your template, or click **[!UICONTROL Select link]** to browse the tree.

   原生範本為 **[!UICONTROL New text export]**。 不得修改此範本，但您可以復制它以配置新範本。By default, export templates are saved in the **[!UICONTROL Resources > Templates > Job templates]** node.

1. Enter a name for export in the **[!UICONTROL Label]** field. 您可以添加描述。
1. 選擇匯出類型。匯出有兩種可能類型：只 **[!UICONTROL Simple export]** 要從一種或多種源文檔 **[!UICONTROL Multiple export]** 中導出一個檔案，並在單次執行中導出多個檔案。

### 第 2 步 - 要匯出的檔案類型 {#step-2---type-of-file-to-export}

選擇要匯出的文件類型，即要匯出的資料架構。

By default, when the export is launched from the **[!UICONTROL Jobs]** node the data comes from the recipient table. When the export is launched from a list of data (from the **[!UICONTROL right click > Export]** menu), the table to which the data belongs is automatically filled in in the **[!UICONTROL Document type]** field.

![](assets/s_ncs_user_export_wizard02.png)

* 依預設，會選 **[!UICONTROL Download the file generated on the server after the export]** 取選項。 In the **[!UICONTROL Local file]** field, fill in the name and path of the file to be created, or browse your local disk by clicking the folder to the right of the field. 您可以取消選擇此選項以輸入伺服器輸出檔案的存取路徑和名稱。

   >[!NOTE]
   >
   >始終在伺服器上執行自動匯入和匯出作業。
   >
   >To export only some of the data, click **[!UICONTROL Advanced parameters]** and enter the number of lines to be exported in the appropriate field.

* 您可以建立差分匯出以僅匯出自上次執行以來已修改的記錄。若要這麼做，請按一下 **[!UICONTROL Advanced parameters]** 連結，然後按一下 **[!UICONTROL Differential export]** 標籤，然後選取 **[!UICONTROL Activate differential export]**。

   ![](assets/s_ncs_user_export_wizard02_b.png)

   您必須輸入上次修改的日期。它可以從欄位中檢索或計算。

### 第 3 步 - 定義輸出格式 {#step-3---defining-the-output-format}

選擇匯出檔案的輸出格式。可以使用以下格式：文字、固定行文字、CSV 和 XML。

![](assets/s_ncs_user_export_wizard03.png)

* For **[!UICONTROL Text]** format, select the delimiters to separate the columns (tabs, commas, semi-colons, or custom) and the strings (single or double quotes, or none).
* 對於 **[!UICONTROL text]** 和 **[!UICONTROL CSV]**，您可以選取選項 **[!UICONTROL Use first lines as column titles]**。
* 指示日期格式和數字格式。To do this, click the **[!UICONTROL Edit]** button for the field concerned and use the editor.
* 對於包含列舉值的欄位，您可以選取 **[!UICONTROL Export labels instead of internal values of enumerations]**。 For example, the title can be stored in the form **1=Mr.**, **2=Miss**,** 3=Mrs.**. 如果選擇此選項，將匯出&#x200B;**先生**、**小姐**&#x200B;和&#x200B;**太太**。

### 第 4 步 - 資料選擇 {#step-4---data-selection}

選擇要匯出的欄位。操作步驟：

1. Double-click the desired fields in the **[!UICONTROL Available fields]** list in order to add them to the **[!UICONTROL Output columns]** section.
1. 使用清單右側的箭頭定義輸出檔案中欄位的順序。

   ![](assets/s_ncs_user_export_wizard04.png)

1. Click the **[!UICONTROL Add]** button to call on functions. 有關詳細資訊，請參閱 [函式清單](../../platform/using/defining-filter-conditions.md#list-of-functions)。

### 第 5 步 - 對行進行排序 {#step-5---sorting-columns}

選擇行的排序順序。

![](assets/s_ncs_user_export_wizard05.png)

### 第 6 步 - 篩選條件 {#step-6---filter-conditions-}

您可以添加篩選條件以避免匯出所有資料。此篩選的配置與傳遞精靈中的收件者定位相同。請參見[此頁面](../../delivery/using/steps-defining-the-target-population.md)。

![](assets/s_ncs_user_export_wizard05_b.png)

### 第 7 步 – 設定資料格式 {#step-7---data-formatting}

您可以修改輸出檔案的欄位順序和標籤，並將轉換應用於源資料。

* 要更改要匯出的行的順序，請選擇相關行，然後使用表右側的藍色箭頭。
* To change the label of a field, click in the cell of the **[!UICONTROL Label]** column that matches the field to be modified, and enter the new label. 按鍵盤上的 Enter 確認。
* To apply a case transformation to the content of a field, select it from the **[!UICONTROL Transformation]** column. 您可以選擇：

   * 切換到小寫
   * 切換到大寫
   * 第一個字母大寫
   ![](assets/s_ncs_user_export_wizard06.png)

* Click **[!UICONTROL Add a calculated field]** if you want to create a new calculated field (for example, a column containing last name + first name). For more on this, refer to [Calculated fields](../../platform/using/importing-data.md#calculated-fields).

如果要匯出元素集合 (例如，收件者的訂閱，它們所屬的清單等) ，則必須指定要匯出的集合中的元素數量。

![](assets/s_ncs_user_export_wizard06_c.png)

### 第 8 步 - 資料預覽 {#step-8---data-preview}

按一 **[!UICONTROL Start the preview of the data]** 下可預覽匯出結果。 按照預設，顯示前 200 行。To change this value, click the arrows to the right of the **[!UICONTROL Lines to display]** field.

![](assets/s_ncs_user_export_wizard07.png)

點擊精靈底部的標籤，從行中結果的預覽切換到 XML 中的結果。您還可以查看生成的 SQL 查詢。

### 第 9 步 - 啟動匯出 {#step-9---launching-the-export}

按一 **[!UICONTROL Start]** 下以啟動資料匯出。

![](assets/s_ncs_user_export_wizard08.png)

## 通過工作流程匯出資料 {#exporting-data-via-a-workflow}

在使用可用於轉換資料的一些可用資料管理活動之後，可以使用工作流程來自動執行某些匯出過程或匯出精確資料集。

要了解有關從工作流程匯出資料的更多資訊，請參見[本節](../../workflow/using/how-to-use-workflow-data.md)。
