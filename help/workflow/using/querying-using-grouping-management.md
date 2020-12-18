---
solution: Campaign Classic
product: campaign
title: 使用分組管理進行查詢
description: 瞭解如何使用群組管理執行查詢
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 4%

---


# 使用分組管理進行查詢 {#querying-using-grouping-management}

在此範例中，我們想執行查詢，以尋找在先前傳送期間鎖定超過30次的所有電子郵件網域。

* 需要選擇哪個表？

   收件者表(nms:recipient)

* 要在輸出欄中選擇的欄位？

   電子郵件網域和主要金鑰（含計數）

* 資料分組？

   根據主鍵數超過30的電子郵件網域。 此操作使用&#x200B;**[!UICONTROL Group by + Having]**&#x200B;選項執行。 **[!UICONTROL Group by + Having]** 可讓您將資料分組（「分組依據」），並選取已分組的項目（「有」）。

若要建立此範例，請套用下列步驟：

1. 開啟&#x200B;**[!UICONTROL Generic query editor]**&#x200B;並選擇「Recipient（收件人）」表(**nms:recipient（收件人）**)。

   ![](assets/query_editor_02.png)

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;窗口中，選擇&#x200B;**[!UICONTROL Email domain]**&#x200B;和&#x200B;**[!UICONTROL Primary key]**&#x200B;欄位。 在&#x200B;**[!UICONTROL Primary key]**&#x200B;欄位上執行計數。

   有關主鍵計數的詳細資訊，請參閱[本節](../../platform/using/defining-filter-conditions.md#building-expressions)。

1. 選中&#x200B;**[!UICONTROL Handle groupings (GROUP BY + HAVING)]**&#x200B;框。

   ![](assets/query_editor_nveau_29.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;視窗中，以遞減順序排序電子郵件網域。 若要這麼做，請勾選&#x200B;**[!UICONTROL Descending sort]**&#x200B;欄中的&#x200B;**[!UICONTROL Yes]**。 按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_nveau_70.png)

1. 在 **[!UICONTROL Data filtering]** 中選取 **[!UICONTROL Filtering conditions]**。轉至&#x200B;**[!UICONTROL Target elements]**&#x200B;窗口，然後按一下&#x200B;**[!UICONTROL Next]**。
1. 在&#x200B;**[!UICONTROL Data grouping]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;選擇&#x200B;**[!UICONTROL Email domain]**。

   此資料分組窗口僅在選中&#x200B;**[!UICONTROL Handle groupings (GROUP BY + HAVING]**&#x200B;框時顯示。

   ![](assets/query_editor_blocklist_04.png)

1. 在&#x200B;**[!UICONTROL Grouping condition]**&#x200B;視窗中，指出主鍵數大於30，因為我們只希望將電子郵件網域定位在超過30次後傳回為結果。

   選中&#x200B;**[!UICONTROL Manage groupings (GROUP BY + HAVING)]**&#x200B;框時，將顯示此窗口：這是篩選分組結果(HAVING)的地方。

   ![](assets/query_editor_blocklist_05.png)

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:這裡不需要格式設定。
1. 在資料預覽視窗中，按一下&#x200B;**[!UICONTROL Launch data preview]**:在此，會傳回3個以上30次為目標的不同電子郵件網域。

   ![](assets/query_editor_blocklist_06.png)
