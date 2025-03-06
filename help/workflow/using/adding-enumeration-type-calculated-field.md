---
product: campaign
title: 新增分項清單型別計算欄位
description: 瞭解如何新增列舉型別計算欄位
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
hide: true
hidefromtoc: true
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 1%

---

# 新增分項清單型別計算欄位 {#adding-an-enumeration-type-calculated-field}



在此處，我們要建立具有&#x200B;**[!UICONTROL Enumerations]**&#x200B;型別計算欄位的查詢。 此欄位將在資料預覽視窗中產生額外的欄。 此欄會指定每個收件者（0、1和2）傳回的結果數值。 會將性別指派給新欄中的每個值：如果值等於「0」，則會將「男性」指派給「1」，將「女性」指派給「2」，或將「未指示」指派給「0」。

* 需要選取哪個表格？

  收件者表格(nms：recipient)

* 要在輸出欄中選取的欄位？

  姓氏、名字、性別

* 要根據哪些條件篩選資訊？

  收件者語言

應用以下步驟：

1. 開啟一般查詢編輯器並選取收件者資料表(**[!UICONTROL nms:recipient]**)。
1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;視窗中，選取&#x200B;**[!UICONTROL Last name]**、**[!UICONTROL First name]**&#x200B;和&#x200B;**[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**：此範例不需要排序。
1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。
1. 在&#x200B;**[!UICONTROL Target element]**&#x200B;視窗中，設定篩選條件以收集會說英語的收件者。

   ![](assets/query_editor_nveau_74.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Add a calculated field]**。

   ![](assets/query_editor_nveau_75.png)

1. 前往&#x200B;**[!UICONTROL Export calculated field definition]**&#x200B;視窗的&#x200B;**[!UICONTROL Type]**&#x200B;視窗並選取&#x200B;**[!UICONTROL Enumerations]**。

   定義新計算欄位必須參考的欄。 若要這麼做，請在&#x200B;**[!UICONTROL Source column]**&#x200B;欄位的下拉式選單中選取&#x200B;**[!UICONTROL Gender]**&#x200B;欄：目的地值將與&#x200B;**[!UICONTROL Gender]**&#x200B;欄一致。

   ![](assets/query_editor_nveau_76.png)

   定義&#x200B;**Source**&#x200B;和&#x200B;**目的地**&#x200B;值：目的地值可讓查詢結果更易於讀取。 此查詢應傳回收件者性別，結果將為0、1或2。

   對於要輸入的每個「來源 — 目的地」行，按一下&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中的&#x200B;**[!UICONTROL Add]**：

   * 在&#x200B;**[!UICONTROL Source]**&#x200B;欄中，在新行中輸入每個性別(0,1，2)的來源值。
   * 在&#x200B;**[!UICONTROL Destination]**&#x200B;欄中，輸入值：行「0」為「未指示」，行「1」為「男性」，行「2」為「女性」。

   選取&#x200B;**[!UICONTROL Keep the source value]**&#x200B;函式。

   按一下&#x200B;**[!UICONTROL OK]**&#x200B;以核准計算欄位。

   ![](assets/query_editor_nveau_77.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**。
1. 在預覽視窗中，**[!UICONTROL start the preview of the data]**。

   額外的欄定義了0、1和2的性別：

   * 0表示「未指示」
   * 1表示「男性」
   * 2表示「女性」

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在&#x200B;**[!UICONTROL List of enumeration values]**&#x200B;中輸入性別「2」，而已選取&#x200B;**[!UICONTROL In other cases]**&#x200B;欄位的&#x200B;**[!UICONTROL Generate a warning and continue]**&#x200B;函式，您將會收到警告記錄。 此記錄指出尚未輸入性別「2」（女性）。 它顯示在資料預覽視窗的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;欄位中。

   ![](assets/query_editor_nveau_79.png)

   再舉一個例子，說明沒有輸入列舉值「2」。 選取&#x200B;**[!UICONTROL Generate an error and reject the line]**&#x200B;函式：所有性別「2」收件者都會提出異常，且行中的其他資訊（名字和姓氏等）不會匯出。 資料預覽視窗的&#x200B;**[!UICONTROL Logs generated during export]**&#x200B;欄位中顯示錯誤記錄。 此記錄表示未輸入列舉值「2」。

   ![](assets/query_editor_nveau_80.png)
