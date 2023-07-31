---
product: campaign
title: 使用分組管理進行查詢
description: 瞭解如何使用分組管理執行查詢
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
feature: Query Editor, Workflows
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 4%

---

# 使用分組管理進行查詢 {#querying-using-grouping-management}



在此範例中，我們要執行查詢以尋找在先前傳送期間超過30次鎖定的所有電子郵件網域。

* 需要選取哪個表格？

  收件者表格(nms：recipient)

* 要在輸出欄中選取的欄位？

  電子郵件網域和主索引鍵（含計數）

* 資料分組？

  根據主要金鑰計數超過30的電子郵件網域。 此作業是使用 **[!UICONTROL Group by + Having]** 選項。 **[!UICONTROL Group by + Having]** 可讓您分組資料（「分組依據」），並選取要分組的專案（「擁有」）。

若要建立此範例，請套用下列步驟：

1. 開啟 **[!UICONTROL Generic query editor]** 並選擇收件者表格(**nms：recipient**)。

   ![](assets/query_editor_02.png)

1. 在 **[!UICONTROL Data to extract]** 視窗，選取 **[!UICONTROL Email domain]** 和 **[!UICONTROL Primary key]** 欄位。 在 **[!UICONTROL Primary key]** 欄位。

   如需主鍵計數的詳細資訊，請參閱 [本節](../../platform/using/defining-filter-conditions.md#building-expressions).

1. 檢查 **[!UICONTROL Handle groupings (GROUP BY + HAVING)]** 方塊。

   ![](assets/query_editor_nveau_29.png)

1. 在 **[!UICONTROL Sorting]** 視窗，以遞減順序排序電子郵件網域。 若要這麼做，請核取 **[!UICONTROL Yes]** 在 **[!UICONTROL Descending sort]** 欄。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。前往 **[!UICONTROL Target elements]** 視窗並按一下 **[!UICONTROL Next]**.
1. 在 **[!UICONTROL Data grouping]** 視窗，選取 **[!UICONTROL Email domain]** 按一下 **[!UICONTROL Add]**.

   此資料分組視窗僅在 **[!UICONTROL Handle groupings (GROUP BY + HAVING]**)方塊是否已勾選。

   ![](assets/query_editor_blocklist_04.png)

1. 在 **[!UICONTROL Grouping condition]** 時，表示主索引鍵計數大於30，因為我們只希望目標電子郵件網域作為結果傳回超過30次。

   此視窗會在 **[!UICONTROL Manage groupings (GROUP BY + HAVING)]** 方塊已核取：這是篩選群組結果(HAVING)的位置。

   ![](assets/query_editor_blocklist_05.png)

1. 在 **[!UICONTROL Data formatting]** 視窗，按一下 **[!UICONTROL Next]**：這裡不需要格式設定。
1. 在資料預覽視窗中，按一下 **[!UICONTROL Launch data preview]**：在此會傳回目標定位超過30次的三個不同電子郵件網域。

   ![](assets/query_editor_blocklist_06.png)
