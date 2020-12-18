---
solution: Campaign Classic
product: campaign
title: 匯出資料
description: 匯出資料
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 59%

---


# 匯出資料{#exporting-data}

## 匯出精靈 {#export-wizard}

匯出參數通過精靈記錄。通用匯出模組作為標準提供，允許您從資料庫存取和提取資料：聯繫人、客戶、清單、細分等。例如，在試算表中使用廣告系列追蹤資料 (追蹤歷史記錄等) 非常有用。輸出資料可以是 txt、CSV、TAB 或 XML 格式。

### 第 1 步 - 選擇匯出範本 {#step-1---choosing-the-export-template}

啟動匯出精靈時，首先必須選擇範本。例如，要配置最近註冊的收件者的匯出，請按照以下步驟操作：

1. 選擇&#x200B;**[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**&#x200B;資料夾。
1. 點擊&#x200B;**新建**，然後點擊&#x200B;**匯出**&#x200B;以建立匯出範本。

   ![](assets/s_ncs_user_export_wizard01.png)

1. 按一下&#x200B;**[!UICONTROL Export template]**&#x200B;欄位右側的箭頭以選擇模板，或按一下&#x200B;**[!UICONTROL Select link]**&#x200B;以瀏覽樹。

   原生範本為&#x200B;**[!UICONTROL New text export]**。 不得修改此範本，但您可以復制它以配置新範本。預設情況下，導出模板保存在&#x200B;**[!UICONTROL Resources > Templates > Job templates]**&#x200B;節點中。

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入匯出名稱。 您可以添加描述。
1. 選擇匯出類型。匯出有兩種可能類型：**[!UICONTROL Simple export]**&#x200B;僅導出一個檔案，而&#x200B;**[!UICONTROL Multiple export]**&#x200B;從一個或多個類型的源文檔中在單次執行中導出多個檔案。

### 第 2 步 - 要匯出的檔案類型 {#step-2---type-of-file-to-export}

選擇要匯出的文件類型，即要匯出的資料架構。

預設情況下，當從&#x200B;**[!UICONTROL Jobs]**&#x200B;節點啟動導出時，資料將來自收件者表。 從資料清單啟動導出時（從&#x200B;**[!UICONTROL right click > Export]**&#x200B;菜單），資料所屬的表將自動填入&#x200B;**[!UICONTROL Document type]**&#x200B;欄位。

![](assets/s_ncs_user_export_wizard02.png)

* 預設情況下，將選擇&#x200B;**[!UICONTROL Download the file generated on the server after the export]**&#x200B;選項。 在&#x200B;**[!UICONTROL Local file]**&#x200B;欄位中，填寫要建立的檔案的名稱和路徑，或按一下欄位右側的資料夾，瀏覽您的本機磁碟。 您可以取消選擇此選項以輸入伺服器輸出檔案的存取路徑和名稱。

   >[!NOTE]
   >
   >始終在伺服器上執行自動匯入和匯出作業。
   >
   >要僅導出某些資料，請按一下&#x200B;**[!UICONTROL Advanced parameters]** ，然後在相應欄位中輸入要導出的行數。

* 您可以建立差分匯出以僅匯出自上次執行以來已修改的記錄。若要這麼做，請按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Differential export]**&#x200B;標籤，然後選取&#x200B;**[!UICONTROL Activate differential export]**。

   ![](assets/s_ncs_user_export_wizard02_b.png)

   您必須輸入上次修改的日期。它可以從欄位中檢索或計算。

### 第 3 步 - 定義輸出格式 {#step-3---defining-the-output-format}

選擇匯出檔案的輸出格式。可以使用以下格式：文字、固定行文字、CSV 和 XML。

![](assets/s_ncs_user_export_wizard03.png)

* 對於&#x200B;**[!UICONTROL Text]**&#x200B;格式，請選取分隔字元以分隔欄（標籤、逗號、分號或自訂）和字串（單引號或雙引號，或無）。
* 對於&#x200B;**[!UICONTROL text]**&#x200B;和&#x200B;**[!UICONTROL CSV]**，可以選擇&#x200B;**[!UICONTROL Use first lines as column titles]**&#x200B;選項。
* 指示日期格式和數字格式。若要這麼做，請按一下相關欄位的&#x200B;**[!UICONTROL Edit]**&#x200B;按鈕，然後使用編輯器。
* 對於包含枚舉值的欄位，可以選擇&#x200B;**[!UICONTROL Export labels instead of internal values of enumerations]**。 例如，標題可以以&#x200B;**1=Mr**、**2=Miss**、**3=Mrs的形式儲存。**.如果選擇此選項，將匯出&#x200B;**先生**、**小姐**&#x200B;和&#x200B;**太太**。

### 第 4 步 - 資料選擇 {#step-4---data-selection}

選擇要匯出的欄位。操作步驟：

1. 連按兩下&#x200B;**[!UICONTROL Available fields]**&#x200B;清單中所要的欄位，以新增至&#x200B;**[!UICONTROL Output columns]**&#x200B;區段。
1. 使用清單右側的箭頭定義輸出檔案中欄位的順序。

   ![](assets/s_ncs_user_export_wizard04.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以呼叫函式。 有關詳細資訊，請參閱[函式清單](../../platform/using/defining-filter-conditions.md#list-of-functions)。

### 第 5 步 - 對行進行排序 {#step-5---sorting-columns}

選擇行的排序順序。

![](assets/s_ncs_user_export_wizard05.png)

### 第 6 步 - 篩選條件 {#step-6---filter-conditions-}

您可以添加篩選條件以避免匯出所有資料。此篩選的配置與傳遞精靈中的收件者定位相同。請參見[此頁面](../../delivery/using/steps-defining-the-target-population.md)。

![](assets/s_ncs_user_export_wizard05_b.png)

### 第 7 步 – 設定資料格式 {#step-7---data-formatting}

您可以修改輸出檔案的欄位順序和標籤，並將轉換應用於源資料。

* 要更改要匯出的行的順序，請選擇相關行，然後使用表右側的藍色箭頭。
* 要更改欄位的標籤，請按一下與要修改的欄位匹配的&#x200B;**[!UICONTROL Label]**&#x200B;列的單元格，然後輸入新標籤。 按鍵盤上的 Enter 確認。
* 要將大小寫轉換應用於欄位的內容，請從&#x200B;**[!UICONTROL Transformation]**&#x200B;列中選擇該欄位。 您可以選擇：

   * 切換到小寫
   * 切換到大寫
   * 第一個字母大寫

   ![](assets/s_ncs_user_export_wizard06.png)

* 如果要建立新的計算欄位（例如，包含姓氏+名字的列），請按一下&#x200B;**[!UICONTROL Add a calculated field]**。 有關詳細資訊，請參閱[計算欄位](../../platform/using/importing-data.md#calculated-fields)。

如果要匯出元素集合 (例如，收件者的訂閱，它們所屬的清單等) ，則必須指定要匯出的集合中的元素數量。

![](assets/s_ncs_user_export_wizard06_c.png)

### 第 8 步 - 資料預覽 {#step-8---data-preview}

按一下&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;可預覽導出結果。 按照預設，顯示前 200 行。若要變更此值，請按一下&#x200B;**[!UICONTROL Lines to display]**&#x200B;欄位右側的箭頭。

![](assets/s_ncs_user_export_wizard07.png)

點擊精靈底部的標籤，從行中結果的預覽切換到 XML 中的結果。您還可以查看生成的 SQL 查詢。

### 第 9 步 - 啟動匯出 {#step-9---launching-the-export}

按一下&#x200B;**[!UICONTROL Start]**&#x200B;以啟動資料匯出。

![](assets/s_ncs_user_export_wizard08.png)

## 通過工作流程匯出資料 {#exporting-data-via-a-workflow}

在使用可用於轉換資料的一些可用資料管理活動之後，可以使用工作流程來自動執行某些匯出過程或匯出精確資料集。

要了解有關從工作流程匯出資料的更多資訊，請參見[本節](../../workflow/using/how-to-use-workflow-data.md)。
