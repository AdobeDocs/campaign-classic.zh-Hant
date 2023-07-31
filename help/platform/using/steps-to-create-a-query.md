---
product: campaign
title: 建立查詢的步驟
description: 建立查詢的步驟
feature: Query Editor
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: creating-queries
exl-id: cf914366-8bac-4d68-a0cc-2a43d102eef2
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 2%

---

# 建立查詢的步驟{#steps-to-create-a-query}



在Adobe Campaign中建立查詢的步驟如下：

1. 選取工作表。 請參閱 [步驟1 — 選擇表格](#step-1---choose-a-table).
1. 選取要擷取的資料。 請參閱 [步驟2 — 選擇要擷取的資料](#step-2---choose-data-to-extract).
1. 定義資料排序順序。 請參閱 [步驟3 — 排序資料](#step-3---sort-data).
1. 篩選資料。 請參閱 [步驟4 — 篩選資料](#step-4---filter-data).
1. 格式化資料。 請參閱 [步驟5 — 格式化資料](#step-5---format-data).
1. 顯示結果。 請參閱 [步驟6 — 預覽資料](#step-6---preview-data).

>[!NOTE]
>
>所有這些步驟都可在一般查詢編輯器中使用。 在另一個前後關聯中建立查詢時，可能會忽略某些步驟。\
>「查詢」活動顯示在中 [本節](../../workflow/using/query.md).

## 步驟1 — 選擇表格 {#step-1---choose-a-table}

選取包含您要查詢之資料的表格 **[!UICONTROL Document type]** 視窗。 如有必要，請使用篩選器欄位或 **[!UICONTROL Filters]** 按鈕。

![](assets/query_editor_nveau_21.png)

## 步驟2 — 選擇要擷取的資料 {#step-2---choose-data-to-extract}

在 **[!UICONTROL Data to extract]** 視窗中，選取要顯示的資料：這些欄位將構成輸出欄。

例如，選取 **[!UICONTROL Age]**， **[!UICONTROL Primary key]**， **[!UICONTROL Email domain]** 和 **[!UICONTROL City]**. 結果會根據此選取專案進行組織。 使用視窗右側的藍色箭頭來變更欄順序。

![](assets/query_editor_nveau_01.png)

您可以將公式插入運算式中，或對彙總函式執行程式，以編輯運算式。 若要這麼做，請按一下 **[!UICONTROL Expression]** 欄欄位，然後選取 **[!UICONTROL Edit expression]**.

![](assets/query_editor_nveau_97.png)

您可以將輸出欄資料分組：若要這麼做，請核取 **[!UICONTROL Yes]** 在 **[!UICONTROL Group]** 的欄 **[!UICONTROL Data to extract]** 視窗。 此函式產生關於核取之群組軸的結果。 具有分組的查詢範例可在 [本節](../../workflow/using/querying-delivery-information.md).

![](assets/query_editor_nveau_56.png)

* 此 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 函式可讓您「分組依據」並選取已分組的專案（「擁有」）。 此函式適用於輸出欄中的所有欄位。 例如，此選項可讓您將輸出欄的所有選擇分組，並復原特定型別的資訊，例如介於35到50之間的收件者。

  如需詳細資訊，請參閱[本章節](../../workflow/using/querying-using-grouping-management.md)。

* 此 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 函式可讓您去除重複輸出欄中取得的相同結果。 例如，如果您選取輸出欄中的「姓氏」、「名字」和「電子郵件」欄位來進行人口普查，資料相同的欄位將會被刪除，因為這意味著資料庫中已經多次輸入相同的連絡人：只會考慮一個結果。

## 步驟3 — 排序資料 {#step-3---sort-data}

此 **[!UICONTROL Sorting]** 視窗可讓您排序欄內容。 使用箭頭來變更欄順序：

* 此 **[!UICONTROL Sorting]** 欄可啟用簡單排序，並從A到Z或按遞增順序排列欄內容。
* 此 **[!UICONTROL Descending sort]** 將內容從Z到A並依遞減順序排列。 這對於檢視紀錄銷售非常有用，例如：最高數字會顯示在清單頂端。

在此範例中，資料會根據收件者年齡以遞增順序排序。

![](assets/query_editor_nveau_57.png)

## 步驟4 — 篩選資料 {#step-4---filter-data}

查詢編輯器可讓您篩選資料以縮小搜尋範圍。

提供的篩選器取決於查詢涉及的表格。

![](assets/query_editor_nveau_09.png)

一旦您選取 **[!UICONTROL Filtering conditions]** 您將存取 **[!UICONTROL Target elements]** 區段：這可讓您定義如何篩選要收集的資料。

* 若要建立新的篩選器，請選取建立要驗證的公式所需的欄位、運運算元和值，以便選取資料。 可結合數個條件(如需詳細資訊，請參閱 [定義篩選條件](../../platform/using/defining-filter-conditions.md))。
* 若要使用先前儲存的篩選器，請按一下 **[!UICONTROL Add]** 按鈕，按一下 **[!UICONTROL Predefined filter]** 並選取您想要的。

  ![](assets/query_editor_15.png)

* 在中建立的篩選器 **[!UICONTROL Generic query editor]** 可用於其他查詢應用程式，反之亦然。 若要儲存篩選器，請按一下 **[!UICONTROL Save]** 圖示。

  >[!NOTE]
  >
  >有關建立和使用篩選器的詳細資訊，請參閱 [篩選選項](../../platform/using/filtering-options.md).

如下列範例所示，若要復原所有說英語的收件者，請選取：「recipient language」 **等於** EN」。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以直接存取選項，方法是在 **值** 欄位： **$(options：OPTION_NAME)**.

按一下 **[!UICONTROL Preview]** 標籤來檢視篩選條件的結果。 在此情況下，所有說英語的收件者都會顯示其名稱、名字和電子郵件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL語言的使用者可以按一下 **[!UICONTROL Generate SQL query]** 以檢視SQL中的查詢。

![](assets/query_editor_nveau_99.png)

## 步驟5 — 格式化資料 {#step-5---format-data}

設定限制篩選器後，您將可存取 **[!UICONTROL Data formatting]** 視窗。 此視窗可讓您重新排列輸出欄、轉換資料，以及變更欄標籤的大寫/小寫。 它也可讓您使用計算欄位將公式套用至最終結果。

>[!NOTE]
>
>有關計算欄位型別的詳細資訊，請參閱 [建立計算欄位](../../platform/using/defining-filter-conditions.md#creating-calculated-fields).

未勾選的欄不會顯示在資料預覽視窗中。

![](assets/query_editor_nveau_10.png)

此 **[!UICONTROL Transformation]** 欄可讓您將欄標籤變更為大寫或小寫。 選取欄並按一下 **[!UICONTROL Transformation]** 欄。 您可以選擇：

* **[!UICONTROL Switch to lower case]**，
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 步驟6 — 預覽資料 {#step-6---preview-data}

此 **[!UICONTROL Data preview]** 視窗是最後一個階段。 按一下 **[!UICONTROL Start the preview of the data]** 以取得您的查詢結果。 它以欄或XML格式提供。 按一下 **[!UICONTROL Generated SQL queries]** 索引標籤以檢視SQL格式的查詢。

在此範例中，資料會根據收件者年齡以遞增順序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>依預設，只會顯示前200行 **[!UICONTROL Data preview]** 視窗。 若要變更，請在 **[!UICONTROL Lines to display]** 方塊並按一下 **[!UICONTROL Start the preview of the data]**.
