---
product: campaign
title: 使用多對多關係進行查詢
description: 瞭解如何使用多對多關係執行查詢
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Query Editor
exl-id: e1d40ba1-2493-45c1-bd54-af9cb332028d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 1%

---

# 使用多對多關係進行查詢 {#querying-using-a-many-to-many-relationship}



在此範例中，我們要復原過去7天內未聯絡的收件者。 此查詢與所有傳遞有關。

此範例也說明如何設定與選取的收集元素（或橘色節點）相關的篩選器。 集合元素位於 **[!UICONTROL Field to select]** 視窗。

* 需要選取哪個表格？

   收件者表格(**nms：recipient**)

* 要為輸出欄選取的欄位

   主索引鍵、姓氏、名字和電子郵件

* 根據篩選資訊的條件

   根據今天之前7天的收件者傳遞記錄

應用以下步驟：

1. 開啟一般查詢編輯器並選取收件者表格 **[!UICONTROL (nms:recipient)]**.
1. 在 **[!UICONTROL Data to extract]** 視窗，選取 **[!UICONTROL Primary key]**， **[!UICONTROL First name]**， **[!UICONTROL Last name]** 和 **[!UICONTROL Email]**.

   ![](assets/query_editor_nveau_33.png)

1. 在排序視窗中，依字母順序排序名稱。

   ![](assets/query_editor_nveau_34.png)

1. 在 **[!UICONTROL Data filtering]** 視窗，選取 **[!UICONTROL Filtering conditions]**.
1. 在 **[!UICONTROL Target element]** 視窗中，擷取過去7天沒有追蹤記錄之設定檔的篩選條件涉及兩個步驟。 您需要選取的元素是多對多連結。

   * 從選取 **[!UICONTROL Recipient delivery logs (broadlog)]** 第一個收集要素（橘色節點） **[!UICONTROL Value]** 欄。

      ![](assets/query_editor_nveau_67.png)

      選擇 **[!UICONTROL do not exist as]** 運運算元。 不需要在此行中選取第二個值。

   * 第二個篩選條件的內容取決於第一個篩選條件。 在此， **[!UICONTROL Event date]** 欄位直接提供於 **[!UICONTROL Recipient delivery logs]** 表格，因為有此表格的連結。

      ![](assets/query_editor_nveau_36.png)

      選取 **[!UICONTROL Event date]** 使用 **[!UICONTROL greater than or equal to]** 運運算元。 選取 **[!UICONTROL DaysAgo (7)]** 值。 若要這麼做，請按一下 **[!UICONTROL Edit expression]** 在 **[!UICONTROL Value]** 欄位。 在 **[!UICONTROL Formula type]** 視窗，選取 **[!UICONTROL Process on dates]** 和 **[!UICONTROL Current date minus n days]**，將「7」作為值提供。

      ![](assets/query_editor_nveau_37.png)

      篩選條件已設定。

      ![](assets/query_editor_nveau_38.png)

1. 在 **[!UICONTROL Data formatting]** 視窗中，將姓氏切換為大寫。 按一下 **[!UICONTROL Last name]** 中的行 **[!UICONTROL Transformation]** 欄並選取 **[!UICONTROL Switch to upper case]** （在下拉式功能表中）。

   ![](assets/query_editor_nveau_39.png)

1. 使用 **[!UICONTROL Add a calculated field]** 函式以插入欄至資料預覽視窗。

   在此範例中，新增計算欄位，並將收件者的名字和姓氏加入單一欄中。 按一下 **[!UICONTROL Add a calculated field]** 函式。 在 **[!UICONTROL Export calculated field definition]** 視窗，輸入標籤和內部名稱，然後選擇 **[!UICONTROL JavaScript Expression]** 型別。 然後輸入下列運算式：

   ```
   var rep = source._firstName+" - "+source._lastName
   return rep
   ```

   ![](assets/query_editor_nveau_40.png)

   按一下 **[!UICONTROL OK]**。此 **[!UICONTROL Data formatting]** 視窗已設定。

   如需新增計算欄位的詳細資訊，請參閱本區段。

1. 結果顯示在 **[!UICONTROL Data preview]** 視窗。 過去7天未聯絡的收件者會依字母順序顯示。 名稱會以大寫顯示，而且已建立具有名字和姓氏的欄。

   ![](assets/query_editor_nveau_41.png)
