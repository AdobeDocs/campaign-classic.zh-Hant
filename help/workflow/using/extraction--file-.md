---
title: 資料擷取 (檔案)
description: 進一步瞭解資料擷取（檔案）工作流程活動。
page-status-flag: never-activated
uuid: c1e3fde3-183c-4602-9cef-760e4648fcf7
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: fe4e6f64-eb0a-44bc-8221-6c9bfb99871f
translation-type: tm+mt
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---


# 資料擷取 (檔案){#extraction-file}

您可以使用活動從外部檔案中的工作流表中提取 **[!UICONTROL Data extraction (file)]** 資料。

>[!CAUTION]
>
>此活動必須始終具有包含要提取資料的入站過渡。

若要設定資料擷取，請套用下列步驟：

1. 指定輸出檔案的名稱：此名稱可包含變數，可透過欄位右側的個人化按鈕插入。
1. 按一 **[!UICONTROL Edit the file format...]** 下以選取要擷取的資料。

   ![](assets/s_advuser_extract_file_param.png)

   此選 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 項會新增額外步驟，以篩選匯總的最終結果，例如對特定採購單類型、訂購超過10次的客戶等。

1. 如有必要，您可以將新欄新增至輸出檔案，例如計算或處理結果。 若要這麼做，請按一下 **[!UICONTROL Add]** 圖示。

   ![](assets/s_advuser_extract_file_add_col.png)

   在其他行中，按一下 **[!UICONTROL Edit expression]** 表徵圖以定義新列的內容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然後，您將訪問選擇窗口。 按一 **[!UICONTROL Advanced selection]** 下以選擇要套用至資料的程式。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   從清單中選擇所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定義在資料擷取期間要執行的後置程式，讓您壓縮或加密檔案。 若要這麼做，必須在活動的標籤中新 **[!UICONTROL Script]** 增所需的命令。

如需更多相關資訊，請參閱本節： [壓縮或加密檔案](../../workflow/using/how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

![](assets/postprocessing_dataextraction.png)

## List of aggregate functions {#list-of-aggregate-functions}

以下是可用集合函式的清單：

* **[!UICONTROL Count]** 計算要聚合的欄位的所有非空值，包括重複值（聚合欄位）,

   **[!UICONTROL Distinct]** 要計算要聚合的欄位的不同值和非空值的總數（在計算之前排除重複值），請執行以下操作：

* **[!UICONTROL Sum]** 計算數值域的值總和，
* **[!UICONTROL Minimum value]** 計算欄位的最小值（數字或其他）,
* **[!UICONTROL Maximum value]** 計算欄位的最大值（數字或其他）,
* **[!UICONTROL Average]** 來計算數值欄位的平均值。

