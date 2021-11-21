---
product: campaign
title: 使用多對多關係進行查詢
description: 了解如何使用多對多關係執行查詢
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---

# 使用多對多關係進行查詢 {#querying-using-a-many-to-many-relationship}

![](../../assets/common.svg)

在此範例中，我們想要復原過去7天未聯絡的收件者。 此查詢涉及所有傳送。

此範例也說明如何設定與選擇集合元素（或橘色節點）相關的篩選器。 集合元素可在 **[!UICONTROL Field to select]** 窗口。

* 需要選取哪個表格？

   收件者表格(**nms:recipient**)

* 要為輸出列選擇的欄位

   主鍵、姓氏、名字和電子郵件

* 根據篩選的資訊是哪個標準

   根據收件者的傳送記錄，今天之前7天

應用以下步驟：

1. 開啟「一般查詢編輯器」並選取「收件者」表格 **[!UICONTROL (nms:recipient)]**.
1. 在 **[!UICONTROL Data to extract]** 窗口，選擇 **[!UICONTROL Primary key]**, **[!UICONTROL First name]**, **[!UICONTROL Last name]** 和 **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. 在排序視窗中，依字母排序名稱。

   ![](assets/query_editor_nveau_34.png)

1. 在 **[!UICONTROL Data filtering]** 窗口，選擇 **[!UICONTROL Filtering conditions]**.
1. 在 **[!UICONTROL Target element]** 視窗中，擷取過去7天沒有追蹤記錄之設定檔的篩選條件涉及兩個步驟。 您需要選取的元素是多對多連結。

   * 從選取 **[!UICONTROL Recipient delivery logs (broadlog)]** 第一個的集合元素（橘色節點） **[!UICONTROL Value]** 欄。

      ![](assets/query_editor_nveau_67.png)

      選擇 **[!UICONTROL do not exist as]** 運算元。 不需要在此行中選取第二個值。

   * 第二篩選條件的內容取決於第一個。 這裡， **[!UICONTROL Event date]** 欄位直接在 **[!UICONTROL Recipient delivery logs]** 表格，因為有此表格的連結。

      ![](assets/query_editor_nveau_36.png)

      選擇 **[!UICONTROL Event date]** 和 **[!UICONTROL greater than or equal to]** 運算元。 選取 **[!UICONTROL DaysAgo (7)]** 值。 要執行此操作，請按一下 **[!UICONTROL Edit expression]** 在 **[!UICONTROL Value]** 欄位。 在 **[!UICONTROL Formula type]** 窗口，選擇 **[!UICONTROL Process on dates]** 和 **[!UICONTROL Current date minus n days]**，提供&quot;7&quot;作為值。

      ![](assets/query_editor_nveau_37.png)

      篩選條件已設定。

      ![](assets/query_editor_nveau_38.png)

1. 在 **[!UICONTROL Data formatting]** 窗口，將姓氏切換為大寫。 按一下 **[!UICONTROL Last name]** 行 **[!UICONTROL Transformation]** 欄和選取 **[!UICONTROL Switch to upper case]** 的下拉式清單。

   ![](assets/query_editor_nveau_39.png)

1. 使用 **[!UICONTROL Add a calculated field]** 函式將欄插入資料預覽視窗中。

   在此範例中，在單一欄中新增包含收件者名字和姓氏的計算欄位。 按一下 **[!UICONTROL Add a calculated field]** 函式。 在 **[!UICONTROL Export calculated field definition]** 窗口，輸入標籤和內部名稱，然後選擇 **[!UICONTROL JavaScript Expression]** 類型。 然後輸入下列運算式：

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   按一下 **[!UICONTROL OK]**。此 **[!UICONTROL Data formatting]** 視窗已設定。

   如需新增計算欄位的詳細資訊，請參閱本區段。

1. 結果顯示在 **[!UICONTROL Data preview]** 窗口。 過去7天內未與收件者聯絡的收件者會以字母順序顯示。 名稱會以大寫顯示，且已建立包含名字和姓氏的欄。

   ![](assets/query_editor_nveau_41.png)
