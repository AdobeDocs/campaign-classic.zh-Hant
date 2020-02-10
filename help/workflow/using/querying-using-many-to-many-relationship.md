---
title: 使用多對多關係進行查詢
description: 瞭解如何使用多對多關係來執行查詢
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


# 使用多對多關係進行查詢 {#querying-using-a-many-to-many-relationship}

在此範例中，我們想要復原過去7天內未連絡的收件者。 此查詢涉及所有交貨。

此範例也說明如何設定與系列元素（或橘色節點）選擇相關的篩選。 「收集」元素可在窗口中 **[!UICONTROL Field to select]** 使用。

* 需要選擇哪個表？

   收件者表(**nms:recipient**)

* 要為輸出列選擇的欄位

   主鍵、姓氏、名字和電子郵件

* 根據篩選的資訊是哪個標準

   根據收件者在今天前7天的傳送記錄

應用以下步驟：

1. 開啟「一般查詢編輯器」(Generic query editor)，然後選擇「收件者」(Recipient)表 **[!UICONTROL (nms:recipient)]**&#x200B;格。
1. 在窗口 **[!UICONTROL Data to extract]** 中，選擇 **[!UICONTROL Primary key]**、 **[!UICONTROL First name]**&#x200B;和 **[!UICONTROL Last name]****[!UICONTROL Email]**。

   ![](assets/query_editor_nveau_33.png)

1. 在排序窗口中，按字母順序對名稱排序。

   ![](assets/query_editor_nveau_34.png)

1. 在窗口 **[!UICONTROL Data filtering]** 中，選擇 **[!UICONTROL Filtering conditions]**。
1. 在視窗 **[!UICONTROL Target element]** 中，擷取過去7天沒有追蹤記錄的描述檔的篩選條件包含兩個步驟。 您需要選取的元素是多對多連結。

   * 首先，為第一 **[!UICONTROL Recipient delivery logs (broadlog)]** 欄選取收集元素(橘色節 **[!UICONTROL Value]** 點)。

      ![](assets/query_editor_nveau_67.png)

      選擇運算 **[!UICONTROL do not exist as]** 元。 無需在此行中選擇第二個值。

   * 第二過濾條件的內容取決於第一過濾條件。 在這裡， **[!UICONTROL Event date]** 由於有此表的連結，因 **[!UICONTROL Recipient delivery logs]** 此該欄位直接在表中提供。

      ![](assets/query_editor_nveau_36.png)

      使用 **[!UICONTROL Event date]** 運算元 **[!UICONTROL greater than or equal to]** 選取。 選擇 **[!UICONTROL DaysAgo (7)]** 值。 若要這麼做，請按一 **[!UICONTROL Edit expression]** 下欄位中 **[!UICONTROL Value]** 的。 在窗 **[!UICONTROL Formula type]** 口中，選 **[!UICONTROL Process on dates]** 擇 **[!UICONTROL Current date minus n days]**&#x200B;並指定&quot;7&quot;作為值。

      ![](assets/query_editor_nveau_37.png)

      篩選條件已設定。

      ![](assets/query_editor_nveau_38.png)

1. 在窗口 **[!UICONTROL Data formatting]** 中，將姓氏切換為大寫。 按一 **[!UICONTROL Last name]** 下欄中的 **[!UICONTROL Transformation]** 行，然後 **[!UICONTROL Switch to upper case]** 在下拉式選單中選取。

   ![](assets/query_editor_nveau_39.png)

1. 使用函 **[!UICONTROL Add a calculated field]** 數將列插入資料預覽窗口。

   在此範例中，在單一欄中新增包含收件者名字和姓氏的計算欄位。 按一下 **[!UICONTROL Add a calculated field]** 函式。 在窗口 **[!UICONTROL Export calculated field definition]** 中，輸入標籤和內部名稱，然後選擇類 **[!UICONTROL JavaScript Expression]** 型。 然後輸入以下表達式：

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   按一下 **[!UICONTROL OK]**. 窗口 **[!UICONTROL Data formatting]** 已配置。

   如需有關新增計算欄位的詳細資訊，請參閱本節。

1. 結果顯示在窗口 **[!UICONTROL Data preview]** 中。 過去7天內未連絡的收件者會以字母順序顯示。 名稱以大寫顯示，且已建立具有名字和姓氏的列。

   ![](assets/query_editor_nveau_41.png)
