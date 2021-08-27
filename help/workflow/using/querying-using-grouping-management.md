---
product: campaign
title: 使用分組管理進行查詢
description: 了解如何使用分組管理執行查詢
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 23bccb48-60ab-46c9-be26-2fa35243d61e
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---

# 使用分組管理進行查詢 {#querying-using-grouping-management}

![](../../assets/common.svg)

在此範例中，我們想執行查詢，以尋找先前傳送中鎖定超過30次的所有電子郵件網域。

* 需要選取哪個表格？

   收件者表格(nms:recipient)

* 要在輸出列中選擇的欄位？

   電子郵件網域和主索引鍵（含計數）

* 資料分組？

   根據主鍵計數超過30的電子郵件網域。 此操作是使用&#x200B;**[!UICONTROL Group by + Having]**&#x200B;選項執行。 **[!UICONTROL Group by + Having]** 可讓您將資料分組（「分組依據」），並選取分組的項目（「有」）。

若要建立此範例，請套用下列步驟：

1. 開啟&#x200B;**[!UICONTROL Generic query editor]**&#x200B;並選擇「收件人」表(**nms:recipient**)。

   ![](assets/query_editor_02.png)

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Email domain]**&#x200B;和&#x200B;**[!UICONTROL Primary key]**&#x200B;欄位。 在&#x200B;**[!UICONTROL Primary key]**&#x200B;欄位上執行計數。

   有關主鍵計數的詳細資訊，請參閱[此部分](../../platform/using/defining-filter-conditions.md#building-expressions)。

1. 勾選&#x200B;**[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;方塊。

   ![](assets/query_editor_nveau_29.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;視窗中，以降序排序電子郵件網域。 要執行此操作，請檢查&#x200B;**[!UICONTROL Descending sort]**&#x200B;列中的&#x200B;**[!UICONTROL Yes]**。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。前往&#x200B;**[!UICONTROL Target elements]**&#x200B;視窗，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 在&#x200B;**[!UICONTROL Data grouping]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;選擇&#x200B;**[!UICONTROL Email domain]**。

   只有勾選&#x200B;**[!UICONTROL Handle groupings (GROUP BY + HAVING]**&#x200B;方塊時，才會顯示此資料分組視窗。

   ![](assets/query_editor_blocklist_04.png)

1. 在&#x200B;**[!UICONTROL Grouping condition]**&#x200B;視窗中，指出主要金鑰計數大於30，因為我們只想傳回目標定位超過30次的電子郵件網域作為結果。

   勾選&#x200B;**[!UICONTROL Manage groupings (GROUP BY + HAVING)]**&#x200B;方塊時，此視窗隨即顯示：這是篩選分組結果(HAVING)的位置。

   ![](assets/query_editor_blocklist_05.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:此處不需要格式設定。
1. 在資料預覽視窗中，按一下&#x200B;**[!UICONTROL Launch data preview]**:在此處，會傳回三個目標超過30次的不同電子郵件網域。

   ![](assets/query_editor_blocklist_06.png)
