---
product: campaign
title: 使用分組管理進行查詢
description: 瞭解如何使用分組管理執行查詢
feature: Query Editor
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# 使用分組管理進行查詢 {#querying-using-grouping-management}

![](../../assets/common.svg)

在本示例中，我們要運行查詢，以查找在先前交貨期間目標超過30次的所有電子郵件域。

* 需要選擇哪個表？

   收件人表（nms：收件人）

* 要在輸出列中選擇的欄位？

   電子郵件域和主鍵（帶計數）

* 資料分組？

   基於主鍵數超過30的電子郵件域。 此操作與 **[!UICONTROL Group by + Having]** 的雙曲餘切值。 **[!UICONTROL Group by + Having]** 允許您對資料進行分組（「分組依據」），並選擇分組內容（「有」）。

要建立此示例，請應用以下步驟：

1. 開啟 **[!UICONTROL Generic query editor]** 並選擇「收件人」表(**nms：收件人**)。

   ![](assets/query_editor_02.png)

1. 在 **[!UICONTROL Data to extract]** ，選擇 **[!UICONTROL Email domain]** 和 **[!UICONTROL Primary key]** 的子菜單。 對 **[!UICONTROL Primary key]** 的子菜單。

   有關主鍵計數的詳細資訊，請參閱 [此部分](../../platform/using/defining-filter-conditions.md#building-expressions)。

1. 檢查 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 框。

   ![](assets/query_editor_nveau_29.png)

1. 在 **[!UICONTROL Sorting]** 按降序對電子郵件域進行排序。 要執行此操作，請檢查 **[!UICONTROL Yes]** 的 **[!UICONTROL Descending sort]** 的雙曲餘切值。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。轉到 **[!UICONTROL Target elements]** 的 **[!UICONTROL Next]**。
1. 在 **[!UICONTROL Data grouping]** ，選擇 **[!UICONTROL Email domain]** 按一下 **[!UICONTROL Add]**。

   僅當 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**)。

   ![](assets/query_editor_blocklist_04.png)

1. 在 **[!UICONTROL Grouping condition]** 的子菜單。

   當 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 複選框：這是過濾分組結果(HAVING)的位置。

   ![](assets/query_editor_blocklist_05.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，按一下 **[!UICONTROL Next]**:此處不需要格式設定。
1. 在資料預覽窗口中，按一下 **[!UICONTROL Launch data preview]**:這裡，將返回三個目標超過30次的電子郵件域。

   ![](assets/query_editor_blocklist_06.png)
