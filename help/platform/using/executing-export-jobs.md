---
product: campaign
title: 設定匯出工作
description: 瞭解如何在Campaign中設定和執行匯出作業
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: platform
content-type: reference
topic-tags: importing-and-exporting-data
exl-id: 94fc473a-dc49-41e8-b572-51c162b09996
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '925'
ht-degree: 45%

---

# 設定匯出作業 {#executing-export-jobs}



匯出作業可讓您存取及擷取資料庫的資料：連絡人、使用者端、清單、區段等。

例如，使用行銷活動追蹤資料（追蹤歷史記錄等）會很有用。 在試算表中。 輸出資料可以是 txt、CSV、TAB 或 XML 格式。

匯出精靈可讓您設定匯出、定義其選項並啟動執行。 這是一系列畫面，其內容取決於匯出型別（簡單或多重）和操作員的許可權。

建立新的匯出作業後會顯示匯出精靈(請參閱 [建立匯入和匯出工作](../../platform/using/creating-import-export-jobs.md).

## 步驟1 — 選擇匯出範本 {#step-1---choosing-the-export-template}

啟動匯出精靈時，首先必須選擇範本。例如，要配置最近註冊的收件者的匯出，請按照以下步驟操作：

1. 選取 **[!UICONTROL Profiles and Targets > Job > Generic imports and exports]** 資料夾。
1. 點擊&#x200B;**新建**，然後點擊&#x200B;**匯出**&#x200B;以建立匯出範本。

   ![](assets/s_ncs_user_export_wizard01.png)

1. 按一下右側的箭頭 **[!UICONTROL Export template]** 欄位以選取您的範本，或按一下 **[!UICONTROL Select link]** 以瀏覽樹狀結構。

   原生範本為 **[!UICONTROL New text export]**. 不得修改此範本，但您可以復制它以配置新範本。匯出範本預設會儲存在 **[!UICONTROL Resources > Templates > Job templates]** 節點。

1. 在中輸入要匯出的名稱 **[!UICONTROL Label]** 欄位。 您可以添加描述。
1. 選擇匯出類型。有兩種可能的匯出型別： **[!UICONTROL Simple export]** 僅匯出一個檔案，以及 **[!UICONTROL Multiple export]** 以從一或多個型別的來原始檔一次匯出多個檔案。

## 第 2 步 - 要匯出的檔案類型 {#step-2---type-of-file-to-export}

選擇要匯出的文件類型，即要匯出的資料架構。

根據預設，當匯出從 **[!UICONTROL Jobs]** 節點資料來自收件者表格。 從資料清單啟動匯出時(從 **[!UICONTROL right click > Export]** 功能表)，則資料所屬的表格會自動填入 **[!UICONTROL Document type]** 欄位。

![](assets/s_ncs_user_export_wizard02.png)

* 根據預設， **[!UICONTROL Download the file generated on the server after the export]** 選項時才會選擇此選項。 在 **[!UICONTROL Local file]** 欄位，填寫要建立之檔案的名稱和路徑，或按一下欄位右側的資料夾來瀏覽您的本機磁碟。 您可以取消選擇此選項以輸入伺服器輸出檔案的存取路徑和名稱。

   >[!NOTE]
   >
   >始終在伺服器上執行自動匯入和匯出作業。
   >
   >若要僅匯出部分資料，請按一下 **[!UICONTROL Advanced parameters]** 並在適當的欄位中輸入要匯出的行數。

* 您可以建立差分匯出以僅匯出自上次執行以來已修改的記錄。若要這麼做，請按一下 **[!UICONTROL Advanced parameters]** 連結，然後按一下 **[!UICONTROL Differential export]** 索引標籤，然後選取 **[!UICONTROL Activate differential export]**.

   ![](assets/s_ncs_user_export_wizard02_b.png)

   您必須輸入上次修改的日期。它可以從欄位中檢索或計算。

## 步驟3 — 定義輸出格式 {#step-3---defining-the-output-format}

選擇匯出檔案的輸出格式。可以使用以下格式：文字、固定行文字、CSV 和 XML。

![](assets/s_ncs_user_export_wizard03.png)

* 對象 **[!UICONTROL Text]** 格式，選取分隔符號來分隔欄（定位字元、逗號、分號或自訂）和字串（單引號、雙引號或無）。
* 對象 **[!UICONTROL text]** 和 **[!UICONTROL CSV]**，您可以選取選項 **[!UICONTROL Use first lines as column titles]**.
* 指示日期格式和數字格式。若要這麼做，請按一下 **[!UICONTROL Edit]** 相關欄位的按鈕，並使用編輯器。
* 對於包含列舉值的欄位，您可以選取 **[!UICONTROL Export labels instead of internal values of enumerations]**. 例如，標題可以儲存在表單中 **1=先生**， **2=未命中**， **3=Mrs.**. 如果選擇此選項，將匯出&#x200B;**先生**、**小姐**&#x200B;和&#x200B;**太太**。

## 第 4 步 - 資料選擇 {#step-4---data-selection}

選擇要匯出的欄位。操作步驟：

1. 連按兩下 **[!UICONTROL Available fields]** 清單以將它們新增至 **[!UICONTROL Output columns]** 區段。
1. 使用清單右側的箭頭定義輸出檔案中欄位的順序。

   ![](assets/s_ncs_user_export_wizard04.png)

1. 按一下 **[!UICONTROL Add]** 按鈕以呼叫函式。 有關詳細資訊，請參閱 [函式清單](../../platform/using/defining-filter-conditions.md#list-of-functions).

## 步驟5 — 排序欄 {#step-5---sorting-columns}

選擇行的排序順序。

![](assets/s_ncs_user_export_wizard05.png)

## 第 6 步 - 篩選條件 {#step-6---filter-conditions-}

您可以添加篩選條件以避免匯出所有資料。此篩選的配置與傳遞精靈中的收件者定位相同。請參見[此頁面](../../delivery/using/steps-defining-the-target-population.md)。

![](assets/s_ncs_user_export_wizard05_b.png)

## 第 7 步 – 設定資料格式 {#step-7---data-formatting}

您可以修改輸出檔案的欄位順序和標籤，並將轉換應用於源資料。

* 要更改要匯出的行的順序，請選擇相關行，然後使用表右側的藍色箭頭。
* 若要變更欄位的標籤，請按一下 **[!UICONTROL Label]** 欄中符合要修改的欄位，並輸入新標籤。 按鍵盤上的 Enter 確認。
* 若要將案例轉換套用至欄位的內容，請從 **[!UICONTROL Transformation]** 欄。 您可以選擇：

   * 切換到小寫
   * 切換到大寫
   * 第一個字母大寫

   ![](assets/s_ncs_user_export_wizard06.png)

* 按一下 **[!UICONTROL Add a calculated field]** 如果您想要建立新的計算欄位（例如，包含姓氏+名字的欄）。 有關詳細資訊，請參閱 [計算欄位](../../platform/using/executing-import-jobs.md#calculated-fields).

如果要匯出元素集合 (例如，收件者的訂閱，它們所屬的清單等) ，則必須指定要匯出的集合中的元素數量。

![](assets/s_ncs_user_export_wizard06_c.png)

## 第 8 步 - 資料預覽 {#step-8---data-preview}

按一下 **[!UICONTROL Start the preview of the data]** 以預覽匯出結果。 按照預設，顯示前 200 行。若要變更此值，請按一下右側的箭頭 **[!UICONTROL Lines to display]** 欄位。

![](assets/s_ncs_user_export_wizard07.png)

點擊精靈底部的標籤，從行中結果的預覽切換到 XML 中的結果。您還可以查看生成的 SQL 查詢。

## 步驟9 — 啟動匯出 {#step-9---launching-the-export}

按一下 **[!UICONTROL Start]** 以啟動資料匯出。

![](assets/s_ncs_user_export_wizard08.png)

然後您可以監視匯入工作的執行(請參閱 [監視工作執行](../../platform/using/monitoring-jobs-execution.md).
