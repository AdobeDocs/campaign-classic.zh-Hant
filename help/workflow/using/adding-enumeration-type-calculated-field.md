---
solution: Campaign Classic
product: campaign
title: 添加枚舉類型計算欄位
description: 瞭解如何新增列舉類型計算欄位
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---


# 添加枚舉類型計算欄位{#adding-an-enumeration-type-calculated-field}

在此，我們要建立具有&#x200B;**[!UICONTROL Enumerations]**&#x200B;類型計算欄位的查詢。 此欄位將在資料預覽視窗中產生其他欄。 此欄會指定每個收件者（0、1和2）的結果傳回的數值。 新欄中的每個值都會指派性別：「男性」代表「1」,「女性」代表「2」，或「未指出」（如果值等於「0」）。

* 需要選擇哪個表？

   收件者表(nms:recipient)

* 要在輸出欄中選取的欄位？

   姓氏、名字、性別

* 要根據哪些標準篩選資訊？

   收件者語言

應用以下步驟：

1. 開啟「一般查詢編輯器」並選取「收件者」表格(**[!UICONTROL nms:recipient]**)。
1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Last name]**、**[!UICONTROL First name]**&#x200B;和&#x200B;**[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:此示例不需要排序。
1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;視窗中，設定篩選條件以收集會說英語的收件者。

   ![](assets/query_editor_nveau_74.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Add a calculated field]**。

   ![](assets/query_editor_nveau_75.png)

1. 轉到&#x200B;**[!UICONTROL Export calculated field definition]**&#x200B;窗口的&#x200B;**[!UICONTROL Type]**&#x200B;窗口，然後選擇&#x200B;**[!UICONTROL Enumerations]**。

   定義新計算欄位必須引用的列。 若要這麼做，請在&#x200B;**[!UICONTROL Source column]**&#x200B;欄位的下拉式選單中選取&#x200B;**[!UICONTROL Gender]**&#x200B;欄：目標值與&#x200B;**[!UICONTROL Gender]**&#x200B;列一致。

   ![](assets/query_editor_nveau_76.png)

   定義&#x200B;**Source**&#x200B;和&#x200B;**Destination**&#x200B;值：目標值使查詢結果更易於讀取。 此查詢應返回收件者性別，結果為0、1或2。

   對於要輸入的每行&quot;source-destination&quot;，按一下&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中的&#x200B;**[!UICONTROL Add]** :

   * 在&#x200B;**[!UICONTROL Source]**&#x200B;欄中，在新行中輸入每個性別(0,1,2)的來源值。
   * 在&#x200B;**[!UICONTROL Destination]**&#x200B;欄中，輸入以下值：行&quot;0&quot;的&quot;未指示&quot;、行&quot;1&quot;的&quot;男性&quot;和行&quot;2&quot;的&quot;女性&quot;。

   選擇&#x200B;**[!UICONTROL Keep the source value]**&#x200B;函式。

   按一下&#x200B;**[!UICONTROL OK]**&#x200B;以核准計算欄位。

   ![](assets/query_editor_nveau_77.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Next]**。
1. 在預覽窗口中， **[!UICONTROL start the preview of the data]**。

   附加一欄定義0、1和2的性別：

   * 0表示「未指示」
   * 1代表「男性」
   * 2: 「女性」

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中輸入性別&quot;2&quot;，而且已選取&#x200B;**[!UICONTROL In other cases]**&#x200B;欄位的&#x200B;**[!UICONTROL Generate a warning and continue]**&#x200B;函式，則會收到警告記錄。 此日誌表示未輸入性別&quot;2&quot;（女性）。 它顯示在資料預覽視窗的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;欄位中。

   ![](assets/query_editor_nveau_79.png)

   讓我們舉另一個例子，說明未輸入枚舉值&quot;2&quot;。 選擇&#x200B;**[!UICONTROL Generate an error and reject the line]**&#x200B;函式：所有性別&quot;2&quot;的收件者都會引發異常，以及行中的其他資訊（名字和姓氏等） 將不導出。 在資料預覽窗口的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;欄位中顯示錯誤日誌。 此日誌表示未輸入枚舉值&quot;2&quot;。

   ![](assets/query_editor_nveau_80.png)
