---
product: campaign
title: 查詢收件人資料表
description: 了解如何查詢收件者表格
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# 查詢收件人資料表 {#querying-recipient-table}

![](../../assets/common.svg)

在此範例中，我們想要復原電子郵件網域為「orange.co.uk」且未居住在倫敦的收件者的姓名和電子郵件。

* 我們應選取哪個表格？

   收件者表格(nms:recipient)

* 要選作輸出列的欄位

   電子郵件、姓名、城市和帳號

* 收件者的篩選條件為何？

   城市和電子郵件網域

* 類型是否已設定？

   是，根據 **[!UICONTROL Account number]** 和 **[!UICONTROL Last name]**

若要建立此範例，請套用下列步驟：

1. 按一下 **[!UICONTROL Tools > Generic query editor...]** 並選擇 **收件者** (**nms:recipient**)表格。 然後按一下 **[!UICONTROL Next]**。
1. 選擇： **[!UICONTROL Last name]**, **[!UICONTROL First name]**, **[!UICONTROL Email]**, **[!UICONTROL City]** 和 **[!UICONTROL Account number]**. 這些欄位會新增至 **[!UICONTROL Output columns]**. 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 排序欄，以正確順序顯示。 在此，我們想依遞減順序排序帳戶號碼，並依字母順序排序名稱。 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在 **[!UICONTROL Data filtering]** 窗口，縮小搜索範圍選擇 **[!UICONTROL Filtering conditions]** 按一下 **[!UICONTROL Next]**.
1. 此 **[!UICONTROL Target element]** 視窗中輸入篩選設定。

   定義下列篩選條件：電子郵件網域等於「orange.co.uk」的收件者。 要執行此操作，請選擇 **電子郵件網域(@email)** 在 **[!UICONTROL Expression]** 欄，選擇 **等於** 在 **[!UICONTROL Operator]** 欄，並在 **[!UICONTROL Value]** 欄。

   ![](assets/query_editor_05.png)

1. 如有需要，請按一下 **[!UICONTROL Distribution of values]** 按鈕，根據潛在客戶的電子郵件網域檢視分發。 資料庫中每個電子郵件網域都有一個百分比。 在套用篩選器之前，會顯示「orange.co.uk」以外的網域。

   查詢的摘要會顯示在視窗底部： **電子郵件網域等於&#39;orange.co.uk&#39;**.

1. 按一下 **[!UICONTROL Preview]** 若要了解查詢結果：只會顯示「orange.co.uk」電子郵件網域。

   ![](assets/query_editor_nveau_17.png)

1. 我們現在將更改查詢，以查找不住在倫敦的聯繫人。

   選擇 **[!UICONTROL City (location/@city)]** 在 **[!UICONTROL Expression]** 欄， **[!UICONTROL different from]** 作為運算子，然後輸入 **[!UICONTROL London]** 在 **[!UICONTROL Value]** 欄。

   ![](assets/query_editor_08.png)

1. 這會帶您前往 **[!UICONTROL Data formatting]** 窗口。 檢查列順序。 將「帳號」欄下方的「城市」欄向上移動。

   取消勾選「名字」欄，將其從清單中移除。

   ![](assets/query_editor_nveau_15.png)

1. 在 **[!UICONTROL Data preview]** 按一下 **[!UICONTROL Start the preview of the data]**. 此函式會計算查詢的結果。

   此 **[!UICONTROL Column results]** 索引標籤會在欄中顯示查詢結果。

   結果會顯示所有收件者，其電子郵件網域為「orange.co.uk」，且不住在倫敦。 不會顯示「名字」欄，因為在上一個階段中未勾選該欄。 帳號會以遞減順序排序。

   ![](assets/query_editor_nveau_12.png)

   此 **[!UICONTROL XML result]** 頁簽以XML格式顯示結果。

   ![](assets/query_editor_nveau_13.png)

   此 **[!UICONTROL Generated QSL queries]** 頁簽以SQL格式顯示查詢結果。

   ![](assets/query_editor_nveau_14.png)
