---
product: campaign
title: 資料擷取 (檔案)
description: 瞭解有關資料提取（檔案）工作流活動的詳細資訊
feature: Workflows, Data Management Activity
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# 資料擷取 (檔案){#extraction-file}

![](../../assets/v7-only.svg)

可以使用 **[!UICONTROL Data extraction (file)]** 的子菜單。

>[!CAUTION]
>
>此活動必須始終具有包含要提取的資料的入站轉換。

要配置資料提取，請應用以下步驟：

1. 指定輸出檔案的名稱：此名稱可包含變數，這些變數通過欄位右側的個性化按鈕插入。
1. 按一下 **[!UICONTROL Edit the file format...]** 的子菜單。

   ![](assets/s_advuser_extract_file_param.png)

   的 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** option添加了一個額外步驟來篩選聚合的最終結果，例如，在給定的採購訂單類型、訂購次數超過10次的客戶等。

1. 如有必要，可向輸出檔案添加新列，例如計算或處理結果。 要執行此操作，請按一下 **[!UICONTROL Add]** 表徵圖

   ![](assets/s_advuser_extract_file_add_col.png)

   在附加行中，按一下 **[!UICONTROL Edit expression]** 表徵圖以定義新列的內容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然後，您將訪問選擇窗口。 按一下 **[!UICONTROL Advanced selection]** 來修改選定線條的屬性。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   從清單中選擇所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定義在資料提取期間要執行的後處理，從而允許您壓縮或加密檔案。 為此，必須在 **[!UICONTROL Script]** 的子菜單。

有關詳細資訊，請參閱本節： [壓縮或加密檔案](how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

![](assets/postprocessing_dataextraction.png)

## 集合函式清單 {#list-of-aggregate-functions}

以下是可用集合函式的清單：

* **[!UICONTROL Count]** 計算要聚合的欄位的所有非空值，包括重複值（聚合欄位）,

   **[!UICONTROL Distinct]** 要計算要聚合的欄位的不同值和非空值的總數（在計算之前排除重複值）,

* **[!UICONTROL Sum]** 計算數值域的值之和，
* **[!UICONTROL Minimum value]** 計算欄位的最小值（數值或其他）,
* **[!UICONTROL Maximum value]** 計算欄位的最大值（數值或其他值）,
* **[!UICONTROL Average]** 來計算數值欄位的平均值。
