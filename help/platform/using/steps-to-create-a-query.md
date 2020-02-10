---
title: 建立查詢的步驟
seo-title: 建立查詢的步驟
description: 建立查詢的步驟
seo-description: null
page-status-flag: never-activated
uuid: 9668f49c-2da7-42c8-8728-8d644c787935
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: creating-queries
discoiquuid: d538f489-f1ae-4682-9c21-d0300bd42b26
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 建立查詢的步驟{#steps-to-create-a-query}

在Adobe Campaign中建立查詢的步驟如下：

1. 選擇工作表。 請參閱 [步驟1 —— 選擇表格](#step-1---choose-a-table)。
1. 選擇要提取的資料。 請參閱 [步驟2 —— 選擇要擷取的資料](#step-2---choose-data-to-extract)。
1. 定義資料排序順序。 請參閱 [步驟3 —— 排序資料](#step-3---sort-data)。
1. 篩選資料。 請參閱 [步驟4 —— 篩選資料](#step-4---filter-data)。
1. 格式化資料。 請參閱 [步驟5 —— 格式化資料](#step-5---format-data)。
1. 顯示結果。 請參閱 [步驟6 —— 預覽資料](#step-6---preview-data)。

>[!NOTE]
>
>所有這些步驟都可在一般查詢編輯器中使用。 在其他上下文中建立查詢時，可以忽略某些步驟。\
>Query活動會顯示在此 [節中](../../workflow/using/query.md)。

## 步驟1 —— 選擇表格 {#step-1---choose-a-table}

選擇包含要在窗口中查詢的資料的 **[!UICONTROL Document type]** 表。 如有必要，請使用篩選欄位或按鈕來篩選 **[!UICONTROL Filters]** 資料。

![](assets/query_editor_nveau_21.png)

## 步驟2 —— 選擇要擷取的資料 {#step-2---choose-data-to-extract}

在視窗 **[!UICONTROL Data to extract]** 中，選取要顯示的資料：這些欄位將構成輸出列。

例如，選 **[!UICONTROL Age]**&#x200B;擇 **[!UICONTROL Primary key]**、 **[!UICONTROL Email domain]** 和 **[!UICONTROL City]**。 將根據此選擇來組織結果。 使用視窗右側的藍色箭頭來變更欄順序。

![](assets/query_editor_nveau_01.png)

通過在表達式中插入公式或在集合函式上運行進程，可以編輯表達式。 若要這麼做，請按一下欄 **[!UICONTROL Expression]** 位，然後選取 **[!UICONTROL Edit expression]**。

![](assets/query_editor_nveau_97.png)

可以將輸出列資料分組：要執行此操作，請 **[!UICONTROL Yes]** 在窗 **[!UICONTROL Group]** 口的列中選 **[!UICONTROL Data to extract]** 中。 此函式會圍繞所檢查的分組軸生成結果。 此部分提供了具有分組的查詢 [示例](../../workflow/using/querying-delivery-information.md)。

![](assets/query_editor_nveau_56.png)

* 此函 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 數可讓您「依群組」並選取已分組的項目（「已分組」）。 此函式適用於輸出列中的所有欄位。 例如，此選項可讓您將輸出欄的所有選擇分組，並復原特定類型的資訊，例如35到50的收件者。

   如需詳細資訊，請參閱[本小節](../../workflow/using/querying-using-grouping-management.md)。

* 此函 **[!UICONTROL Remove duplicate rows (DISTINCT)]** 數可讓您去重複輸出欄中取得的相同結果。 例如，如果您在輸出欄中選擇姓氏、名字和電子郵件欄位進行人口普查，則會刪除資料相同的欄位，因為這表示在資料庫中輸入了多次相同的連絡人：只會考慮一個結果。

## 步驟3 —— 排序資料 {#step-3---sort-data}

視窗 **[!UICONTROL Sorting]** 可讓您排序欄內容。 使用箭頭更改列順序：

* 該列 **[!UICONTROL Sorting]** 可以對列內容進行簡單排序，並按升序排列從A到Z的列內容。
* 將 **[!UICONTROL Descending sort]** 內容從Z排列為A並以遞減順序排列。 這對於查看記錄銷售非常有用，例如：最高的數字顯示在清單的頂部。

在此範例中，資料會根據收件者年齡以升序排序。

![](assets/query_editor_nveau_57.png)

## 步驟4 —— 篩選資料 {#step-4---filter-data}

查詢編輯器可讓您篩選資料以調整搜尋。

提供的篩選器取決於查詢所關心的表。

![](assets/query_editor_nveau_09.png)

在您選取要存 **[!UICONTROL Filtering conditions]** 取的區段後， **[!UICONTROL Target elements]** 請：這可讓您定義如何篩選要收集的資料。

* 要建立新篩選器，請選擇建立要驗證的公式以便選擇資料所需的欄位、運算子和值。 您可結合數個條件(如需詳細資訊，請參閱「定義篩 [選條件](../../platform/using/defining-filter-conditions.md)」)。
* 若要使用先前儲存的篩選，請按一下按鈕以開啟下拉式清 **[!UICONTROL Add]** 單，按一 **[!UICONTROL Predefined filter]** 下並選取您要的篩選。

   ![](assets/query_editor_15.png)

* 在中建立的篩選器可 **[!UICONTROL Generic query editor]** 以在其他查詢應用程式中使用，反之亦然。 若要儲存篩選，請按一下 **[!UICONTROL Save]** 圖示。

   >[!NOTE]
   >
   >如需建立和使用篩選器的詳細資訊，請參閱 [篩選選項](../../platform/using/filtering-options.md)。

如以下示例所示，要恢復所有講英語的收件人，請選擇：「收件者語 **言等於** EN」。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以在「值」欄位中輸入下列公式，直接存取 **選項** : **$（選項：OPTION_NAME）**。

按一下 **[!UICONTROL Preview]** 標籤以檢視篩選條件的結果。 在這種情況下，所有會講英語的收件者都會顯示其姓名、名字和電子郵件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL語言的用戶可以單 **[!UICONTROL Generate SQL query]** 擊以在SQL中查看查詢。

![](assets/query_editor_nveau_99.png)

## 步驟5 —— 格式化資料 {#step-5---format-data}

一旦您設定了限制篩選器，您就會存取該視 **[!UICONTROL Data formatting]** 窗。 此視窗可讓您重新排列輸出欄、轉換資料，並變更欄標籤的上／下大小寫。 它也可讓您使用計算欄位，將公式套用至最終結果。

>[!NOTE]
>
>有關計算欄位類型的詳細資訊，請參閱創 [建計算欄位](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)。

未勾選的欄不會顯示在資料預覽視窗中。

![](assets/query_editor_nveau_10.png)

欄可 **[!UICONTROL Transformation]** 讓您將欄標籤變更為大寫或小寫。 選擇該列，然後按一下該列中的 **[!UICONTROL Transformation]** 按鈕。 您可以選擇：

* **[!UICONTROL Switch to lower case]**,
* **[!UICONTROL Switch to upper case]**,
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 步驟6 —— 預覽資料 {#step-6---preview-data}

窗 **[!UICONTROL Data preview]** 口是最後一步。 按一 **[!UICONTROL Start the preview of the data]** 下以取得查詢結果。 它以列或XML格式提供。 按一下該 **[!UICONTROL Generated SQL queries]** 頁籤以查看SQL格式的查詢。

在此範例中，資料會根據收件者年齡以升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>預設情況下，窗口中只顯示前200行 **[!UICONTROL Data preview]** 。 要更改此選項，請在框中輸入一個 **[!UICONTROL Lines to display]** 數字並按一下 **[!UICONTROL Start the preview of the data]**。

