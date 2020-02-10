---
title: 添加枚舉類型計算欄位
description: 瞭解如何新增列舉類型計算欄位
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 添加枚舉類型計算欄位 {#adding-an-enumeration-type-calculated-field}

在此，我們要建立具有類型計算欄位 **[!UICONTROL Enumerations]** 的查詢。 此欄位將在資料預覽視窗中產生其他欄。 此欄會指定每個收件者（0、1和2）的結果傳回的數值。 新欄中的每個值都會指派性別：「男性」代表「1」,「女性」代表「2」，或「未指出」（如果值等於「0」）。

* 需要選擇哪個表？

   收件者表(nms:recipient)

* 要在輸出欄中選取的欄位？

   姓氏、名字、性別

* 要根據哪些標準篩選資訊？

   收件者語言

應用以下步驟：

1. 開啟「一般查詢編輯器」並選取「收件者」表格(**[!UICONTROL nms:recipient]**)。
1. 在窗口 **[!UICONTROL Data to extract]** 中，選擇 **[!UICONTROL Last name]**, **[!UICONTROL First name]** 然後 **[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在視窗中 **[!UICONTROL Sorting]** ，按一下 **[!UICONTROL Next]**:此示例不需要排序。
1. 在中 **[!UICONTROL Data filtering]**，選擇 **[!UICONTROL Filtering conditions]**。
1. 在視窗 **[!UICONTROL Target element]** 中，設定篩選條件以收集會說英文的收件者。

   ![](assets/query_editor_nveau_74.png)

1. 在窗口 **[!UICONTROL Data formatting]** 中，按一下 **[!UICONTROL Add a calculated field]**。

   ![](assets/query_editor_nveau_75.png)

1. 轉到窗口 **[!UICONTROL Type]** 的窗口並 **[!UICONTROL Export calculated field definition]** 選擇 **[!UICONTROL Enumerations]**。

   定義新計算欄位必須引用的列。 若要這麼做，請在欄 **[!UICONTROL Gender]** 位的下拉式選單中選取欄 **[!UICONTROL Source column]** 位：目標值與列相 **[!UICONTROL Gender]** 符。

   ![](assets/query_editor_nveau_76.png)

   定義 **來源****和目** 標值：目標值使查詢結果更易於讀取。 此查詢應返回收件者性別，結果為0、1或2。

   對於要輸入的每行「源——目標」，請按一下 **[!UICONTROL Add]** 以下位 **[!UICONTROL List of enumeration values]**&#x200B;置：

   * 在列 **[!UICONTROL Source]** 中，在新行中輸入每個性別(0,1,2)的來源值。
   * 在列中 **[!UICONTROL Destination]** 輸入以下值：行&quot;0&quot;的&quot;未指示&quot;、行&quot;1&quot;的&quot;男性&quot;和行&quot;2&quot;的&quot;女性&quot;。
   選擇函 **[!UICONTROL Keep the source value]** 數。

   按一 **[!UICONTROL OK]** 下以核准計算欄位。

   ![](assets/query_editor_nveau_77.png)

1. 在窗口 **[!UICONTROL Data formatting]** 中，按一下 **[!UICONTROL Next]**。
1. 在預覽窗口中， **[!UICONTROL start the preview of the data]**。

   附加一欄定義0、1和2的性別：

   * 0表示「未指示」
   * 1代表「男性」
   * 2: 「女性」
   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在中輸入性別&quot;2&quot; **[!UICONTROL List of enumeration values]**，且選取了欄 **[!UICONTROL Generate a warning and continue]** 位的 **[!UICONTROL In other cases]** 函式，您將會收到警告記錄。 此日誌表示未輸入性別&quot;2&quot;（女性）。 它會顯示在資 **[!UICONTROL Logs generated during export]** 料預覽視窗的欄位中。

   ![](assets/query_editor_nveau_79.png)

   讓我們舉另一個例子，說明未輸入枚舉值&quot;2&quot;。 選擇函 **[!UICONTROL Generate an error and reject the line]** 數：所有性別&quot;2&quot;的收件者都會引發異常，以及行中的其他資訊（名字和姓氏等）將不導出。 在資料預覽窗口的字 **[!UICONTROL Logs generated during export]** 段中顯示錯誤日誌。 此日誌表示未輸入枚舉值&quot;2&quot;。

   ![](assets/query_editor_nveau_80.png)
