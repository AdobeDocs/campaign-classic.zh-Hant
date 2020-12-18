---
solution: Campaign Classic
product: campaign
title: 查詢收件人資料表
description: 瞭解如何查詢收件者表格
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 3%

---


# 查詢收件人資料表 {#querying-recipient-table}

在此範例中，我們想要復原電子郵件網域為「orange.co.uk」且不住在倫敦的收件者的姓名和電子郵件。

* 我們應該選擇哪張表？

   收件者表(nms:recipient)

* 要選為輸出列的欄位

   電子郵件、姓名、城市和帳號

* 收件者的篩選條件為何？

   城市與電子郵件網域

* 排序是否已配置？

   是，基於&#x200B;**[!UICONTROL Account number]**&#x200B;和&#x200B;**[!UICONTROL Last name]**

若要建立此範例，請套用下列步驟：

1. 按一下&#x200B;**[!UICONTROL Tools > Generic query editor...]**&#x200B;並選擇&#x200B;**Recipients**(**nms:recipient**)表。 然後按一下 **[!UICONTROL Next]**。
1. 選擇：**[!UICONTROL Last name]**、**[!UICONTROL First name]**、**[!UICONTROL Email]**、**[!UICONTROL City]**&#x200B;和&#x200B;**[!UICONTROL Account number]**。 這些欄位會新增至&#x200B;**[!UICONTROL Output columns]**。 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_03.png)

1. 排序欄，以正確順序顯示欄。 在這裡，我們要以遞減順序對帳戶編號排序，並以字母順序對名稱排序。 然後按一下 **[!UICONTROL Next]**。

   ![](assets/query_editor_04.png)

1. 在&#x200B;**[!UICONTROL Data filtering]**&#x200B;視窗中，調整您的搜尋：選擇&#x200B;**[!UICONTROL Filtering conditions]**&#x200B;並按一下&#x200B;**[!UICONTROL Next]**。
1. **[!UICONTROL Target element]**&#x200B;視窗可讓您輸入篩選設定。

   定義下列篩選條件：電子郵件網域等於「orange.co.uk」的收件者。 若要這麼做，請在&#x200B;**[!UICONTROL Expression]**&#x200B;欄中選擇&#x200B;**電子郵件網域(@email)**，在&#x200B;**[!UICONTROL Operator]**&#x200B;欄中選擇&#x200B;**等於**，並在&#x200B;**[!UICONTROL Value]**&#x200B;欄中輸入&quot;orange.co.uk&quot;。

   ![](assets/query_editor_05.png)

1. 如有需要，按一下&#x200B;**[!UICONTROL Distribution of values]**&#x200B;按鈕，以根據潛在客戶的電子郵件網域來檢視散發。 資料庫中每個電子郵件網域都有一個百分比。 除「orange.co.uk」以外的網域會顯示，直到套用篩選器為止。

   查詢的摘要顯示在窗口底部：**電子郵件網域等於&#39;orange.co.uk&#39;**。

1. 按一下&#x200B;**[!UICONTROL Preview]**&#x200B;以瞭解查詢結果：只會顯示「orange.co.uk」電子郵件網域。

   ![](assets/query_editor_nveau_17.png)

1. 我們現在將更改查詢，以查找不住在倫敦的聯繫人。

   在&#x200B;**[!UICONTROL Expression]**&#x200B;列中選擇&#x200B;**[!UICONTROL City (location/@city)]**&#x200B;作為運算子，並在&#x200B;**[!UICONTROL Value]**&#x200B;列中輸入&#x200B;**[!UICONTROL London]**。**[!UICONTROL different from]**

   ![](assets/query_editor_08.png)

1. 這將帶您進入&#x200B;**[!UICONTROL Data formatting]**&#x200B;窗口。 檢查列順序。 在「帳戶編號」欄下方向上移動「城市」欄。

   取消勾選「名字」欄，將其從清單中移除。

   ![](assets/query_editor_nveau_15.png)

1. 在&#x200B;**[!UICONTROL Data preview]**&#x200B;窗口中，按一下&#x200B;**[!UICONTROL Start the preview of the data]**。 此函式計算查詢的結果。

   **[!UICONTROL Column results]**&#x200B;標籤以列顯示查詢結果。

   結果會顯示所有擁有「orange.co.uk」電子郵件網域且不住在倫敦的收件者。 「名字」欄未顯示，因為在上一階段中未勾選。 帳號會以遞減順序排序。

   ![](assets/query_editor_nveau_12.png)

   **[!UICONTROL XML result]**&#x200B;標籤以XML格式顯示結果。

   ![](assets/query_editor_nveau_13.png)

   **[!UICONTROL Generated QSL queries]**&#x200B;頁籤以SQL格式顯示查詢結果。

   ![](assets/query_editor_nveau_14.png)
