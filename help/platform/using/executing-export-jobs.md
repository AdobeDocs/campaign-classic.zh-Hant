---
product: campaign
title: 設定匯出工作
description: 瞭解如何在Campaign中設定並執行匯出作業
feature: Overview
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 29%

---

# 設定匯出作業 {#executing-export-jobs}



匯出作業可讓您存取及擷取資料庫的資料：連絡人、使用者端、清單、區段等。

例如，使用行銷活動追蹤資料（追蹤歷史記錄等）會很有用 在試算表中。 輸出資料可以是 txt、CSV、TAB 或 XML 格式。

匯出精靈可讓您設定匯出、定義其選項並啟動執行。 這是一系列畫面，其內容取決於匯出型別（簡單或多重）和操作者的權利。

建立新的匯出作業後，匯出精靈便會顯示（請參閱[建立匯入及匯出作業](../../platform/using/creating-import-export-jobs.md)）。

## 步驟1 — 選擇匯出範本 {#step-1---choosing-the-export-template}

啟動匯出精靈時，您必須先選取範本。 例如，要配置最近註冊的收件者的匯出，請按照以下步驟操作：

1. 選取&#x200B;**[!UICONTROL Profiles and Targets > Job > Generic imports and exports]**&#x200B;資料夾。
1. 點擊&#x200B;**新建**，然後點擊&#x200B;**匯出**&#x200B;以建立匯出範本。

   ![](assets/s_ncs_user_export_wizard01.png)

1. 按一下&#x200B;**[!UICONTROL Export template]**&#x200B;欄位右側的箭頭以選取您的範本，或按一下&#x200B;**[!UICONTROL Select link]**&#x200B;以瀏覽樹狀結構。

   原生範本為&#x200B;**[!UICONTROL New text export]**。 此範本不可修改，但您可以複製它以設定新範本。 匯出範本預設會儲存在&#x200B;**[!UICONTROL Resources > Templates > Job templates]**&#x200B;節點中。

1. 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入匯出名稱。 您可以添加描述。
1. 選取匯出型別。 有兩種可能的匯出型別：**[!UICONTROL Simple export]**&#x200B;只匯出一個檔案，以及&#x200B;**[!UICONTROL Multiple export]**&#x200B;從一或多個型別的來原始檔，在單一執行中匯出數個檔案。

## 第 2 步 - 要匯出的檔案類型 {#step-2---type-of-file-to-export}

選擇要匯出的文件類型，即要匯出的資料架構。

根據預設，從&#x200B;**[!UICONTROL Jobs]**&#x200B;節點啟動匯出時，資料會來自收件者表格。 從資料清單（從&#x200B;**[!UICONTROL right click > Export]**&#x200B;功能表）啟動匯出時，資料所屬的表格會自動填入&#x200B;**[!UICONTROL Document type]**&#x200B;欄位。

![](assets/s_ncs_user_export_wizard02.png)

* 依預設，已選取&#x200B;**[!UICONTROL Download the file generated on the server after the export]**&#x200B;選項。 在&#x200B;**[!UICONTROL Local file]**&#x200B;欄位中，填寫要建立之檔案的名稱和路徑，或按一下欄位右側的資料夾來瀏覽您的本機磁碟。 您可以取消選擇此選項以輸入伺服器輸出檔案的存取路徑和名稱。

  >[!NOTE]
  >
  >始終在伺服器上執行自動匯入和匯出作業。
  >
  >若要僅匯出部分資料，請按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;並在適當的欄位中輸入要匯出的行數。

* 您可以建立差異匯出，以僅匯出自上次執行以來修改的記錄。 若要這麼做，請按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結，再按一下&#x200B;**[!UICONTROL Differential export]**&#x200B;標籤，然後選取&#x200B;**[!UICONTROL Activate differential export]**。

  ![](assets/s_ncs_user_export_wizard02_b.png)

  您必須輸入上次修改的日期。 它可以從欄位中檢索或計算。

## 步驟3 — 定義輸出格式 {#step-3---defining-the-output-format}

選取匯出檔案的輸出格式。 可以使用以下格式：文字、固定行文字、CSV 和 XML。

![](assets/s_ncs_user_export_wizard03.png)

* 針對&#x200B;**[!UICONTROL Text]**&#x200B;格式，選取分隔符號以分隔欄（定位字元、逗號、分號或自訂）和字串（單引號、雙引號或無）。
* 對於&#x200B;**[!UICONTROL text]**&#x200B;和&#x200B;**[!UICONTROL CSV]**，您可以選取選項&#x200B;**[!UICONTROL Use first lines as column titles]**。
* 指示日期格式和數字格式。 若要這麼做，請按一下相關欄位的&#x200B;**[!UICONTROL Edit]**&#x200B;按鈕，然後使用編輯器。
* 對於包含列舉值的欄位，您可以選取&#x200B;**[!UICONTROL Export labels instead of internal values of enumerations]**。 例如，標題可以以&#x200B;**1=Mr格式儲存。**，**2=小姐**，**3=夫人**。 如果選擇此選項，將匯出&#x200B;**先生**、**小姐**&#x200B;和&#x200B;**太太**。

## 第 4 步 - 資料選擇 {#step-4---data-selection}

選取要匯出的欄位。 操作步驟：

1. 連按兩下&#x200B;**[!UICONTROL Available fields]**&#x200B;清單中所需的欄位，以將它們新增至&#x200B;**[!UICONTROL Output columns]**&#x200B;區段。
1. 使用清單右側的箭頭定義輸出檔案中欄位的順序。

   ![](assets/s_ncs_user_export_wizard04.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以呼叫函式。 如需詳細資訊，請參閱[函式清單](../../platform/using/defining-filter-conditions.md#list-of-functions)。

## 步驟5 — 排序欄 {#step-5---sorting-columns}

選擇行的排序順序。

![](assets/s_ncs_user_export_wizard05.png)

## 第 6 步 - 篩選條件 {#step-6---filter-conditions-}

您可以新增篩選條件以避免匯出所有資料。 此篩選的設定與傳遞精靈中的收件者目標定位相同。 請參見[此頁面](../../delivery/using/steps-defining-the-target-population.md)。

![](assets/s_ncs_user_export_wizard05_b.png)

## 第 7 步 – 設定資料格式 {#step-7---data-formatting}

您可以修改輸出檔案的欄位順序和標籤，並將轉換應用於源資料。

* 要更改要匯出的行的順序，請選擇相關行，然後使用表右側的藍色箭頭。
* 若要變更欄位的標籤，請按一下符合要修改欄位的&#x200B;**[!UICONTROL Label]**&#x200B;欄儲存格，然後輸入新標籤。 在鍵盤上按Enter鍵以確認。
* 若要將案例轉換套用至欄位的內容，請從&#x200B;**[!UICONTROL Transformation]**&#x200B;欄中選取它。 您可以選擇：

   * 切換到小寫
   * 切換到大寫
   * 第一個字母大寫

  ![](assets/s_ncs_user_export_wizard06.png)

* 如果要建立新的計算欄位（例如，包含姓氏和名字的欄），請按一下&#x200B;**[!UICONTROL Add a calculated field]**。 如需詳細資訊，請參閱[計算欄位](../../platform/using/executing-import-jobs.md#calculated-fields)。

如果要匯出元素集合 (例如，收件者的訂閱，它們所屬的清單等) ，則必須指定要匯出的集合中的元素數量。

![](assets/s_ncs_user_export_wizard06_c.png)

## 第 8 步 - 資料預覽 {#step-8---data-preview}

按一下&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;以預覽匯出結果。 依預設，會顯示前200行。 若要變更此值，請按一下&#x200B;**[!UICONTROL Lines to display]**&#x200B;欄位右側的箭頭。

![](assets/s_ncs_user_export_wizard07.png)

按一下精靈底部的標籤，從欄中的結果預覽切換到XML中的結果。 您還可以查看生成的 SQL 查詢。

## 步驟9 — 啟動匯出 {#step-9---launching-the-export}

按一下&#x200B;**[!UICONTROL Start]**&#x200B;以啟動資料匯出。

![](assets/s_ncs_user_export_wizard08.png)

然後，您可以監視匯入工作的執行（請參閱[監視工作的執行](../../platform/using/monitoring-jobs-execution.md)）。
