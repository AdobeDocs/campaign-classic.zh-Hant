---
product: campaign
title: 新增分項清單型別計算欄位
description: 瞭解如何新增列舉型別計算欄位
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: workflow
content-type: reference
topic-tags: use-cases
feature: Workflows, Data Management
exl-id: 3f606d3a-0af5-4315-bb08-1b21a71f1721
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 1%

---

# 新增分項清單型別計算欄位 {#adding-an-enumeration-type-calculated-field}



在此處，我們要建立查詢 **[!UICONTROL Enumerations]** 輸入計算欄位。 此欄位將在資料預覽視窗中產生額外的欄。 此欄會指定每個收件者（0、1和2）作為結果所傳回的數值。 會為新欄中的每個值指派性別：「男性」代表「1」，「女性」代表「2」，如果值等於「0」，「未指示」。

* 需要選取哪個表格？

   收件者表格(nms：recipient)

* 要在輸出欄中選取的欄位？

   姓氏、名字、性別

* 要根據哪些條件篩選資訊？

   收件者語言

應用以下步驟：

1. 開啟一般查詢編輯器並選取收件者表格(**[!UICONTROL nms:recipient]**)。
1. 在 **[!UICONTROL Data to extract]** 視窗，選取 **[!UICONTROL Last name]**， **[!UICONTROL First name]** 和 **[!UICONTROL Gender]**.

   ![](assets/query_editor_nveau_73.png)

1. 在 **[!UICONTROL Sorting]** 視窗，按一下 **[!UICONTROL Next]**：此範例不需要排序。
1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。
1. 在 **[!UICONTROL Target element]** 視窗，設定篩選條件以收集講英語的收件者。

   ![](assets/query_editor_nveau_74.png)

1. 在 **[!UICONTROL Data formatting]** 視窗，按一下 **[!UICONTROL Add a calculated field]**.

   ![](assets/query_editor_nveau_75.png)

1. 前往 **[!UICONTROL Type]** 視窗 **[!UICONTROL Export calculated field definition]** 視窗並選取 **[!UICONTROL Enumerations]**.

   定義新計算欄位必須參考的欄。 若要這麼做，請選取 **[!UICONTROL Gender]** 欄（位於的下拉式功能表中） **[!UICONTROL Source column]** 欄位：目的地值將與 **[!UICONTROL Gender]** 欄。

   ![](assets/query_editor_nveau_76.png)

   定義 **來源** 和 **目的地** 值：目的地值可讓查詢結果更易於讀取。 此查詢應傳回收件者性別，結果將為0、1或2。

   對於要輸入的每個「source-destination」行，按一下 **[!UICONTROL Add]** 在 **[!UICONTROL List of enumeration values]**：

   * 在 **[!UICONTROL Source]** 欄，在新行中輸入每個性別(0、1、2)的來源值。
   * 在 **[!UICONTROL Destination]** 欄，輸入值： 「未指示」代表行「0」，「男性」代表行「1」，「女性」代表行「2」。

   選取 **[!UICONTROL Keep the source value]** 函式。

   按一下 **[!UICONTROL OK]** 以核准計算欄位。

   ![](assets/query_editor_nveau_77.png)

1. 在 **[!UICONTROL Data formatting]** 視窗，按一下 **[!UICONTROL Next]**.
1. 在預覽視窗中， **[!UICONTROL start the preview of the data]**.

   額外的欄會定義0、1和2的性別：

   * 0表示「未指示」
   * 1表示「男性」
   * 2表示「女性」

   ![](assets/query_editor_nveau_78.png)

   例如，如果您未在 **[!UICONTROL List of enumeration values]**，以及 **[!UICONTROL Generate a warning and continue]** 的功能 **[!UICONTROL In other cases]** 欄位中選取時，您會看到警告記錄。 此記錄指出尚未輸入性別「2」（女性）。 它會顯示在 **[!UICONTROL Logs generated during export]** 資料預覽視窗的欄位。

   ![](assets/query_editor_nveau_79.png)

   再舉一個例子，說明列舉值「2」並未輸入。 選取 **[!UICONTROL Generate an error and reject the line]** 函式：所有性別「2」收件者都會提出異常和行中的其他資訊（名字和姓氏等） 將不會匯出。 錯誤記錄會顯示在 **[!UICONTROL Logs generated during export]** 資料預覽視窗的欄位。 此記錄指出未輸入列舉值「2」。

   ![](assets/query_editor_nveau_80.png)
