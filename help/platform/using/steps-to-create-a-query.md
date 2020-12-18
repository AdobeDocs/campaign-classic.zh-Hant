---
solution: Campaign Classic
product: campaign
title: 建立查詢的步驟
description: 建立查詢的步驟
audience: platform
content-type: reference
topic-tags: creating-queries
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---


# 建立查詢的步驟{#steps-to-create-a-query}

在Adobe Campaign中建立查詢的步驟如下：

1. 選擇工作表。 請參閱[步驟1 —— 選擇表](#step-1---choose-a-table)。
1. 選擇要提取的資料。 請參閱[步驟2 —— 選擇要提取的資料](#step-2---choose-data-to-extract)。
1. 定義資料排序順序。 請參閱[步驟3 —— 排序資料](#step-3---sort-data)。
1. 篩選資料。 請參閱[步驟4 —— 篩選資料](#step-4---filter-data)。
1. 格式化資料。 請參閱[步驟5 —— 格式化資料](#step-5---format-data)。
1. 顯示結果。 請參閱[步驟6 —— 預覽資料](#step-6---preview-data)。

>[!NOTE]
>
>所有這些步驟都可在一般查詢編輯器中使用。 在其他上下文中建立查詢時，可以忽略某些步驟。\
>Query活動顯示在[此部分](../../workflow/using/query.md)中。

## 步驟1 —— 選擇表{#step-1---choose-a-table}

在&#x200B;**[!UICONTROL Document type]**&#x200B;窗口中選擇包含要查詢的資料的表。 如有必要，請使用篩選欄位或&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕來篩選資料。

![](assets/query_editor_nveau_21.png)

## 步驟2 —— 選擇要提取{#step-2---choose-data-to-extract}的資料

在&#x200B;**[!UICONTROL Data to extract]**&#x200B;視窗中，選取要顯示的資料：這些欄位將構成輸出列。

例如，選擇&#x200B;**[!UICONTROL Age]**、**[!UICONTROL Primary key]**、**[!UICONTROL Email domain]**&#x200B;和&#x200B;**[!UICONTROL City]**。 將根據此選擇來組織結果。 使用視窗右側的藍色箭頭來變更欄順序。

![](assets/query_editor_nveau_01.png)

通過在表達式中插入公式或在集合函式上運行進程，可以編輯表達式。 要執行此操作，請按一下&#x200B;**[!UICONTROL Expression]**&#x200B;列欄位，然後選擇&#x200B;**[!UICONTROL Edit expression]**。

![](assets/query_editor_nveau_97.png)

可以將輸出列資料分組：要執行此操作，請在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口的&#x200B;**[!UICONTROL Group]**&#x200B;列中選中&#x200B;**[!UICONTROL Yes]**。 此函式會圍繞所檢查的分組軸生成結果。 [本節](../../workflow/using/querying-delivery-information.md)中提供了具有分組的查詢示例。

![](assets/query_editor_nveau_56.png)

* **[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;函式可讓您「分組依據」，並選取已分組的項目（「已分組」）。 此函式適用於輸出列中的所有欄位。 例如，此選項可讓您將輸出欄的所有選擇分組，並復原特定類型的資訊，例如35到50的收件者。

   如需詳細資訊，請參閱[本章節](../../workflow/using/querying-using-grouping-management.md)。

* **[!UICONTROL Remove duplicate rows (DISTINCT)]**&#x200B;函式可讓您去除輸出欄中取得的相同結果重複。 例如，如果您在輸出欄中選擇姓氏、名字和電子郵件欄位進行人口普查，則會刪除資料相同的欄位，因為這表示在資料庫中輸入了多次相同的連絡人：只會考慮一個結果。

## 步驟3 —— 對資料{#step-3---sort-data}排序

**[!UICONTROL Sorting]**&#x200B;視窗可讓您排序欄內容。 使用箭頭更改列順序：

* **[!UICONTROL Sorting]**&#x200B;欄可啟用簡單排序，並依遞增順序排列從A到Z的欄內容。
* **[!UICONTROL Descending sort]**&#x200B;將內容從Z排列為A並以遞減順序排列。 這對於查看記錄銷售非常有用，例如：最高的數字顯示在清單的頂部。

在此範例中，資料會根據收件者年齡以升序排序。

![](assets/query_editor_nveau_57.png)

## 步驟4 —— 篩選資料{#step-4---filter-data}

查詢編輯器可讓您篩選資料以調整搜尋。

提供的篩選器取決於查詢所關心的表。

![](assets/query_editor_nveau_09.png)

選擇&#x200B;**[!UICONTROL Filtering conditions]**&#x200B;後，您將訪問&#x200B;**[!UICONTROL Target elements]**&#x200B;部分：這可讓您定義如何篩選要收集的資料。

* 要建立新篩選器，請選擇建立要驗證的公式以便選擇資料所需的欄位、運算子和值。 您可結合數個條件（如需詳細資訊，請參閱[定義篩選條件](../../platform/using/defining-filter-conditions.md)）。
* 若要使用先前儲存的篩選器，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以開啟下拉式清單，按一下&#x200B;**[!UICONTROL Predefined filter]**&#x200B;並選取您想要的篩選器。

   ![](assets/query_editor_15.png)

* 在&#x200B;**[!UICONTROL Generic query editor]**&#x200B;中建立的篩選器可用於其他查詢應用程式，反之亦然。 若要儲存篩選，請按一下&#x200B;**[!UICONTROL Save]**&#x200B;圖示。

   >[!NOTE]
   >
   >有關建立和使用篩選器的詳細資訊，請參閱[篩選選項](../../platform/using/filtering-options.md)。

如以下示例所示，要恢復所有講英語的收件人，請選擇：&quot;收件人語言&#x200B;**等於** EN&quot;。

![](assets/query_editor_nveau_89.png)

>[!NOTE]
>
>您可以在&#x200B;**Value**&#x200B;欄位中鍵入下列公式，直接存取選項：**$(options:OPTION_NAME)**。

按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤以檢視篩選條件的結果。 在這種情況下，所有會講英語的收件者都會顯示其姓名、名字和電子郵件地址。

![](assets/query_editor_nveau_98.png)

熟悉SQL語言的用戶可以按一下&#x200B;**[!UICONTROL Generate SQL query]**&#x200B;在SQL中查看查詢。

![](assets/query_editor_nveau_99.png)

## 步驟5 —— 格式化資料{#step-5---format-data}

配置限制過濾器後，將訪問&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。 此視窗可讓您重新排列輸出欄、轉換資料，並變更欄標籤的上／下大小寫。 它也可讓您使用計算欄位，將公式套用至最終結果。

>[!NOTE]
>
>有關計算欄位類型的詳細資訊，請參閱[建立計算欄位](../../platform/using/defining-filter-conditions.md#creating-calculated-fields)。

未勾選的欄不會顯示在資料預覽視窗中。

![](assets/query_editor_nveau_10.png)

**[!UICONTROL Transformation]**&#x200B;欄可讓您將欄標籤變更為大寫或小寫。 選擇該列，然後按一下&#x200B;**[!UICONTROL Transformation]**&#x200B;列中的。 您可以選擇：

* **[!UICONTROL Switch to lower case]**&#x200B;的
* **[!UICONTROL Switch to upper case]**&#x200B;的
* **[!UICONTROL First letter in upper case]**.

![](assets/query_editor_nveau_42.png)

## 步驟6 —— 預覽資料{#step-6---preview-data}

**[!UICONTROL Data preview]**&#x200B;視窗是最後一個階段。 按一下&#x200B;**[!UICONTROL Start the preview of the data]**&#x200B;獲取查詢結果。 它以列或XML格式提供。 按一下&#x200B;**[!UICONTROL Generated SQL queries]**&#x200B;頁籤以查看SQL格式的查詢。

在此範例中，資料會根據收件者年齡以升序排序。

![](assets/query_editor_nveau_11.png)

>[!NOTE]
>
>預設情況下，**[!UICONTROL Data preview]**&#x200B;窗口中只顯示前200行。 要更改此設定，請在&#x200B;**[!UICONTROL Lines to display]**&#x200B;框中輸入一個數字，然後按一下&#x200B;**[!UICONTROL Start the preview of the data]**。

