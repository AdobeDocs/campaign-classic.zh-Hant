---
product: campaign
title: 資料擷取 (檔案)
description: 深入了解資料擷取（檔案）工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 06eafedd-6386-498f-a80d-7f57ddcccad6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# 資料擷取 (檔案){#extraction-file}

![](../../assets/common.svg)

您可以使用&#x200B;**[!UICONTROL Data extraction (file)]**&#x200B;活動從外部檔案的工作流表中擷取資料。

>[!CAUTION]
>
>此活動必須一律具有入站轉變，其中包含要擷取的資料。

若要設定資料擷取，請套用下列步驟：

1. 指定輸出檔案的名稱：此名稱可包含變數，可透過欄位右側的個人化按鈕插入。
1. 按一下&#x200B;**[!UICONTROL Edit the file format...]**&#x200B;以選取要擷取的資料。

   ![](assets/s_advuser_extract_file_param.png)

   **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;選項新增了一個額外步驟，以篩選匯總的最終結果，例如，對於給定的採購訂單類型、已訂購超過10次的客戶等。

1. 如有必要，您可以將新欄新增至輸出檔案，例如運算或處理結果。 要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;圖示。

   ![](assets/s_advuser_extract_file_add_col.png)

   在其他行中，按一下&#x200B;**[!UICONTROL Edit expression]**&#x200B;圖示以定義新欄的內容。

   ![](assets/s_advuser_extract_file_add_exp.png)

   然後，您將訪問選擇窗口。 按一下&#x200B;**[!UICONTROL Advanced selection]**&#x200B;以選擇要套用至資料的程式。

   ![](assets/s_advuser_extract_file_advanced_selection.png)

   從清單中選擇所需的公式。

   ![](assets/s_advuser_extract_file_agregate_values.png)

您可以定義要在資料擷取期間執行的後續程式，讓您壓縮或加密檔案。 要執行此操作，必須在活動的&#x200B;**[!UICONTROL Script]**&#x200B;索引標籤中新增所需的命令。

如需詳細資訊，請參閱本區段：[壓縮或加密檔案](how-to-use-workflow-data.md#zipping-or-encrypting-a-file)。

![](assets/postprocessing_dataextraction.png)

## 匯總函式清單 {#list-of-aggregate-functions}

以下是可用匯總函式的清單：

* **[!UICONTROL Count]** 要計算要聚合的欄位的所有非空值，包括重複值（聚合欄位的）,

   **[!UICONTROL Distinct]** 要計算要聚合的欄位的不同值和非空值的總數（在計算之前排除重複值）,

* **[!UICONTROL Sum]** 計算數值域的值總和，
* **[!UICONTROL Minimum value]** 計算欄位的最小值（數值或其他）,
* **[!UICONTROL Maximum value]** 計算欄位的最大值（數值或其他）,
* **[!UICONTROL Average]** 來計算數值欄位的平均值。
