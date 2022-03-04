---
product: campaign
title: 查詢收件者表格
description: 瞭解如何查詢收件人表
feature: Query Editor
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# 查詢收件者表格 {#querying-recipient-table}

![](../../assets/common.svg)

在本示例中，我們希望恢復電子郵件域為「orange.co.uk」且不住在倫敦的收件人的姓名和電子郵件。

* 我們應選擇哪個表？

   收件人表（nms：收件人）

* 要選擇為輸出列的欄位

   電子郵件、名稱、城市和帳號

* 收件人的篩選條件是什麼？

   城市和電子郵件域

* 是否配置了排序？

   是，根據 **[!UICONTROL Account number]** 和 **[!UICONTROL Last name]**

要建立此示例，請應用以下步驟：

1. 按一下 **[!UICONTROL Tools > Generic query editor...]** 選擇 **收件人** (**nms：收件人**)。 然後按一下 **[!UICONTROL Next]**。
1. 選擇： **[!UICONTROL Last name]**。 **[!UICONTROL First name]**。 **[!UICONTROL Email]**。 **[!UICONTROL City]** 和 **[!UICONTROL Account number]**。 這些欄位將添加到 **[!UICONTROL Output columns]**。 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 對列進行排序以按正確的順序顯示它們。 在這裡，我們要按降序對帳號進行排序，按字母順序對名稱進行排序。 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在 **[!UICONTROL Data filtering]** 窗口，細化搜索：選擇 **[!UICONTROL Filtering conditions]** 按一下 **[!UICONTROL Next]**。
1. 的 **[!UICONTROL Target element]** 窗口中輸入篩選器設定。

   定義以下篩選條件：電子郵件域等於「orange.co.uk」的收件人。 要執行此操作，請選擇 **電子郵件域(@email)** 的 **[!UICONTROL Expression]** 列，選擇 **等於** 的 **[!UICONTROL Operator]** 列，並在 **[!UICONTROL Value]** 的雙曲餘切值。

   ![](assets/query_editor_05.png)

1. 如果需要，請按一下 **[!UICONTROL Distribution of values]** 按鈕，查看基於潛在客戶的電子郵件域的分發。 資料庫中每個電子郵件域都有一個百分比。 除「orange.co.uk」以外的域將一直顯示，直到應用篩選器。

   查詢摘要顯示在窗口底部： **電子郵件域等於「orange.co.uk」**。

1. 按一下 **[!UICONTROL Preview]** 獲取查詢結果的概念：只顯示&quot;orange.co.uk&quot;電子郵件域。

   ![](assets/query_editor_nveau_17.png)

1. 現在，我們將更改查詢，以查找不住在倫敦的聯繫人。

   選擇 **[!UICONTROL City (location/@city)]** 的 **[!UICONTROL Expression]** 列， **[!UICONTROL different from]** 輸入 **[!UICONTROL London]** 的 **[!UICONTROL Value]** 的雙曲餘切值。

   ![](assets/query_editor_08.png)

1. 這將帶您 **[!UICONTROL Data formatting]** 的子菜單。 檢查列順序。 在「帳號」列下向上移動「城市」列。

   取消選中「名」列，將其從清單中刪除。

   ![](assets/query_editor_nveau_15.png)

1. 在 **[!UICONTROL Data preview]** 窗口，按一下 **[!UICONTROL Start the preview of the data]**。 此函式計算查詢的結果。

   的 **[!UICONTROL Column results]** 頁籤以列的形式顯示查詢結果。

   結果顯示所有不住在倫敦的電子郵件域為&quot;orange.co.uk&quot;的收件人。 不顯示「名」列，因為在上一階段未選中該列。 帳號按降序排序。

   ![](assets/query_editor_nveau_12.png)

   的 **[!UICONTROL XML result]** 頁籤顯示XML格式的結果。

   ![](assets/query_editor_nveau_13.png)

   的 **[!UICONTROL Generated QSL queries]** 頁籤顯示SQL格式的查詢結果。

   ![](assets/query_editor_nveau_14.png)
