---
product: campaign
title: 使用多對多關係進行查詢
description: 瞭解如何使用多對多關係執行查詢
feature: Query Editor
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---

# 使用多對多關係進行查詢 {#querying-using-a-many-to-many-relationship}

![](../../assets/v7-only.svg)

在本示例中，我們希望恢復過去7天內未聯繫的收件人。 此查詢涉及所有交貨。

此示例還說明如何配置與選擇集合元素（或橙色節點）相關的篩選器。 集合元素在 **[!UICONTROL Field to select]** 的子菜單。

* 需要選擇哪個表？

   收件人表(**nms：收件人**)

* 要為輸出列選擇的欄位

   主鍵、姓氏、名字和電子郵件

* 根據篩選的資訊所依據的標準

   基於收件人的發送日誌，此日期早於7天

應用以下步驟：

1. 開啟「一般查詢編輯器」(Generic query editor)，然後選擇「收件人」(Recipient)表 **[!UICONTROL (nms:recipient)]**。
1. 在 **[!UICONTROL Data to extract]** 窗口，選擇 **[!UICONTROL Primary key]**。 **[!UICONTROL First name]**。 **[!UICONTROL Last name]** 和 **[!UICONTROL Email]**。

   ![](assets/query_editor_nveau_33.png)

1. 在排序窗口中，按字母順序對名稱進行排序。

   ![](assets/query_editor_nveau_34.png)

1. 在 **[!UICONTROL Data filtering]** 窗口，選擇 **[!UICONTROL Filtering conditions]**。
1. 在 **[!UICONTROL Target element]** 窗口中，在過去7天內沒有跟蹤日誌的情況下提取配置檔案的過濾條件包括兩個步驟。 需要選擇的元素是多對多連結。

   * 從選擇 **[!UICONTROL Recipient delivery logs (broadlog)]** 第一個集合元素（橙色節點） **[!UICONTROL Value]** 的雙曲餘切值。

      ![](assets/query_editor_nveau_67.png)

      選擇 **[!UICONTROL do not exist as]** 運算子。 無需在此行中選擇第二個值。

   * 第二過濾條件的內容取決於第一過濾條件。 這裡， **[!UICONTROL Event date]** 欄位直接在 **[!UICONTROL Recipient delivery logs]** 表，因為有指向此表的連結。

      ![](assets/query_editor_nveau_36.png)

      選擇 **[!UICONTROL Event date]** 和 **[!UICONTROL greater than or equal to]** 運算子。 選擇 **[!UICONTROL DaysAgo (7)]** 值。 要執行此操作，請按一下 **[!UICONTROL Edit expression]** 的 **[!UICONTROL Value]** 的子菜單。 在 **[!UICONTROL Formula type]** 窗口，選擇 **[!UICONTROL Process on dates]** 和 **[!UICONTROL Current date minus n days]**，將「7」作為值。

      ![](assets/query_editor_nveau_37.png)

      已配置篩選器條件。

      ![](assets/query_editor_nveau_38.png)

1. 在 **[!UICONTROL Data formatting]** 的下界。 按一下 **[!UICONTROL Last name]** 行 **[!UICONTROL Transformation]** 列和選擇 **[!UICONTROL Switch to upper case]** 的下界。

   ![](assets/query_editor_nveau_39.png)

1. 使用 **[!UICONTROL Add a calculated field]** 函式將列插入資料預覽窗口。

   在此示例中，在單個列中添加一個包含收件人的名字和姓氏的計算欄位。 按一下 **[!UICONTROL Add a calculated field]** 的子菜單。 在 **[!UICONTROL Export calculated field definition]** ，輸入標籤和內部名稱，然後選擇 **[!UICONTROL JavaScript Expression]** 的雙曲餘切值。 然後輸入以下表達式：

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   按一下 **[!UICONTROL OK]**。的 **[!UICONTROL Data formatting]** 窗口。

   有關添加計算欄位的詳細資訊，請參閱本節。

1. 結果顯示在 **[!UICONTROL Data preview]** 的子菜單。 過去7天內未聯繫的收件人按字母順序顯示。 名稱以大寫顯示，並且已建立具有名字和姓氏的列。

   ![](assets/query_editor_nveau_41.png)
