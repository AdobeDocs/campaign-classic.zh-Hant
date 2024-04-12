---
product: campaign
title: 查詢收件者表格
description: 瞭解如何查詢收件者表格
feature: Query Editor, Workflows
exl-id: 5b037798-b092-4c98-9f6a-4af7fc7941c6
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---

# 查詢收件者表格 {#querying-recipient-table}



在此範例中，我們要復原其電子郵件網域為「orange.co.uk」且不在倫敦居住的收件者的名稱和電子郵件。

* 我們應該選取哪個表格？

  收件者表格(nms：recipient)

* 要選取作為輸出欄的欄位

  電子郵件、姓名、城市和帳號

* 收件者的篩選條件為何？

  城市和電子郵件網域

* 是否已設定排序？

  是，根據 **[!UICONTROL Account number]** 和 **[!UICONTROL Last name]**

若要建立此範例，請套用下列步驟：

1. 按一下 **[!UICONTROL Tools > Generic query editor...]** 並選擇 **收件者** (**nms：recipient**)表格。 然後按一下 **[!UICONTROL Next]**。
1. 選擇： **[!UICONTROL Last name]**， **[!UICONTROL First name]**， **[!UICONTROL Email]**， **[!UICONTROL City]** 和 **[!UICONTROL Account number]**. 這些欄位將新增至 **[!UICONTROL Output columns]**. 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 排序欄，以使用正確的順序顯示。 在此處，我們要以遞減順序排序帳號，並以字母順序排序名稱。 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在 **[!UICONTROL Data filtering]** 視窗，調整您的搜尋：選擇 **[!UICONTROL Filtering conditions]** 並按一下 **[!UICONTROL Next]**.
1. 此 **[!UICONTROL Target element]** 視窗可讓您輸入篩選設定。

   定義下列篩選條件：電子郵件網域等於「orange.co.uk」的收件者。 若要這麼做，請選擇 **電子郵件網域(@email)** 在 **[!UICONTROL Expression]** 欄，選擇 **等於** 在 **[!UICONTROL Operator]** orange.co.uk欄，並在 **[!UICONTROL Value]** 欄。

   ![](assets/query_editor_05.png)

1. 如有需要，請按一下 **[!UICONTROL Distribution of values]** 按鈕以根據潛在客戶的電子郵件網域檢視分佈。 資料庫中每個電子郵件網域都有百分比可用。 「orange.co.uk」以外的網域會一直顯示，直到套用篩選器為止。

   查詢摘要會顯示在視窗底部： **電子郵件網域等於「orange.co.uk」**.

1. 按一下 **[!UICONTROL Preview]** 若要瞭解查詢結果：只顯示「orange.co.uk」電子郵件網域。

   ![](assets/query_editor_nveau_17.png)

1. 我們現在將變更查詢，以尋找不在倫敦的聯絡人。

   選取 **[!UICONTROL City (location/@city)]** 在 **[!UICONTROL Expression]** 欄， **[!UICONTROL different from]** 作為運運算元並輸入 **[!UICONTROL London]** 在 **[!UICONTROL Value]** 欄。

   ![](assets/query_editor_08.png)

1. 這會將您帶至 **[!UICONTROL Data formatting]** 視窗。 檢查欄順序。 將「城市」欄向上移動到「帳號」欄下方。

   取消勾選「名字」欄，將其從清單中移除。

   ![](assets/query_editor_nveau_15.png)

1. 在 **[!UICONTROL Data preview]** 視窗，按一下 **[!UICONTROL Start the preview of the data]**. 此函式計算查詢的結果。

   此 **[!UICONTROL Column results]** 索引標籤以欄顯示查詢結果。

   該結果會顯示所有含有「orange.co.uk」電子郵件網域的收件者，他們並非住在倫敦。 「名字」欄未顯示，因為在上一個階段中它未被核取。 帳號會依遞減順序排序。

   ![](assets/query_editor_nveau_12.png)

   此 **[!UICONTROL XML result]** 標籤以XML格式顯示結果。

   ![](assets/query_editor_nveau_13.png)

   此 **[!UICONTROL Generated QSL queries]** 索引標籤以SQL格式顯示查詢結果。

   ![](assets/query_editor_nveau_14.png)
