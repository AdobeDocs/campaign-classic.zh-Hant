---
product: campaign
title: 添加枚舉類型計算欄位
description: 瞭解如何添加枚舉類型計算欄位
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---

# 添加枚舉類型計算欄位 {#adding-an-enumeration-type-calculated-field}

![](../../assets/v7-only.svg)

在此，我們要建立一個 **[!UICONTROL Enumerations]** 類型計算欄位。 此欄位將在資料預覽窗口中生成附加列。 此列將為每個收件人（0、1和2）指定作為結果返回的數字值。 新欄中的每個值將分配一個性別：&quot;Male&quot;表示&quot;1&quot;,&quot;Male&quot;表示&quot;2&quot;,&quot;Not isded&quot;表示值等於&quot;0&quot;。

* 需要選擇哪個表？

   收件人表（nms：收件人）

* 要在輸出列中選擇的欄位？

   姓，名，性別

* 將根據哪些標準篩選資訊？

   收件人語言

應用以下步驟：

1. 開啟「一般查詢編輯器」(Generic query editor)，然後選擇「收件人」(Recipient)表(**[!UICONTROL nms:recipient]**)。
1. 在 **[!UICONTROL Data to extract]** 窗口，選擇 **[!UICONTROL Last name]**。 **[!UICONTROL First name]** 和 **[!UICONTROL Gender]**。

   ![](assets/query_editor_nveau_73.png)

1. 在 **[!UICONTROL Sorting]** 窗口，按一下 **[!UICONTROL Next]**:此示例無需排序。
1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。
1. 在 **[!UICONTROL Target element]** 窗口，設定篩選條件以收集說英語的收件人。

   ![](assets/query_editor_nveau_74.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，按一下 **[!UICONTROL Add a calculated field]**。

   ![](assets/query_editor_nveau_75.png)

1. 轉到 **[!UICONTROL Type]** 窗口 **[!UICONTROL Export calculated field definition]** 選擇 **[!UICONTROL Enumerations]**。

   定義新計算欄位必須引用的列。 要執行此操作，請選擇 **[!UICONTROL Gender]** 的 **[!UICONTROL Source column]** 欄位：目標值與 **[!UICONTROL Gender]** 的雙曲餘切值。

   ![](assets/query_editor_nveau_76.png)

   定義 **源** 和 **目標** 值：目標值使查詢結果更容易讀取。 此查詢應返回收件人性別，結果為0、1或2。

   對於要輸入的每行「源 — 目標」，按一下 **[!UICONTROL Add]** 的 **[!UICONTROL List of enumeration values]**:

   * 在 **[!UICONTROL Source]** 列，在新行中輸入每個性別(0,1,2)的源值。
   * 在 **[!UICONTROL Destination]** 列，輸入以下值：行&quot;0&quot;的&quot;未指明&quot;、行&quot;1&quot;的&quot;男性&quot;和行&quot;2&quot;的&quot;女性&quot;。

   選擇 **[!UICONTROL Keep the source value]** 的子菜單。

   按一下 **[!UICONTROL OK]** 以批准計算欄位。

   ![](assets/query_editor_nveau_77.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，按一下 **[!UICONTROL Next]**。
1. 在預覽窗口中， **[!UICONTROL start the preview of the data]**。

   附加一欄定義0、1和2的性別：

   * 0表示「未指明」
   * 1表示「男性」
   * 2表示&quot;女性&quot;

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在 **[!UICONTROL List of enumeration values]**&#x200B;的 **[!UICONTROL Generate a warning and continue]** 函式 **[!UICONTROL In other cases]** 欄位時，您將獲得警告日誌。 此日誌表明未輸入性別&quot;2&quot;（女性）。 顯示在 **[!UICONTROL Logs generated during export]** 的子菜單。

   ![](assets/query_editor_nveau_79.png)

   讓我們舉另一個示例，並說明未輸入枚舉值&quot;2&quot;。 選擇 **[!UICONTROL Generate an error and reject the line]** 函式：所有性別&quot;2&quot;的接受者都將引起異常和行中的其他資訊（名字和姓氏等）。 不導出。 錯誤日誌顯示在 **[!UICONTROL Logs generated during export]** 的子菜單。 此日誌表示未輸入枚舉值&quot;2&quot;。

   ![](assets/query_editor_nveau_80.png)
