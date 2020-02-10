---
title: 查詢收件人表
description: 瞭解如何查詢收件者表格
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
source-git-commit: ab2c133aaa2f754e56fe8fdfc76d10526d4d1ce2

---


# 查詢收件人表 {#querying-recipient-table}

在此範例中，我們想要復原電子郵件網域為「orange.co.uk」且不住在倫敦的收件者的姓名和電子郵件。

* 我們應該選擇哪張表？

   收件者表(nms:recipient)

* 要選為輸出列的欄位

   電子郵件、姓名、城市和帳號

* 收件者的篩選條件為何？

   城市與電子郵件網域

* 排序是否已配置？

   是，基於 **[!UICONTROL Account number]** 和 **[!UICONTROL Last name]**

若要建立此範例，請套用下列步驟：

1. 按一下 **[!UICONTROL Tools > Generic query editor...]** 並選擇「 **Recipients** (**nms:recipient**)」表。 然後按一 **[!UICONTROL Next]**&#x200B;下。
1. 選擇： **[!UICONTROL Last name]**、 **[!UICONTROL First name]****[!UICONTROL Email]**、 **[!UICONTROL City]** 和 **[!UICONTROL Account number]**。 這些欄位會新增至 **[!UICONTROL Output columns]**。 然後按一 **[!UICONTROL Next]**&#x200B;下。

   ![](assets/query_editor_03.png)

1. 排序欄，以正確順序顯示欄。 在這裡，我們要以遞減順序對帳戶編號排序，並以字母順序對名稱排序。 然後按一 **[!UICONTROL Next]**&#x200B;下。

   ![](assets/query_editor_04.png)

1. 在視窗中 **[!UICONTROL Data filtering]** 調整您的搜尋：選擇並 **[!UICONTROL Filtering conditions]** 按一下 **[!UICONTROL Next]**。
1. 視窗 **[!UICONTROL Target element]** 可讓您輸入篩選設定。

   定義下列篩選條件：電子郵件網域等於「orange.co.uk」的收件者。 若要這麼做，請在欄中選 **擇「電子郵件網域(@email)** 」, **[!UICONTROL Expression]** 在欄中選 **擇「等於** 」, **[!UICONTROL Operator]** 並在欄中輸入「orange.co.uk」 **[!UICONTROL Value]** 。

   ![](assets/query_editor_05.png)

1. 如有需要，按一 **[!UICONTROL Distribution of values]** 下按鈕以根據潛在客戶的電子郵件網域檢視散發。 資料庫中每個電子郵件網域都有一個百分比。 除「orange.co.uk」以外的網域會顯示，直到套用篩選器為止。

   查詢的摘要顯示在窗口底部：電 **子郵件網域等於&#39;orange.co.uk&#39;**。

1. 按一 **[!UICONTROL Preview]** 下以瞭解查詢結果：只會顯示「orange.co.uk」電子郵件網域。

   ![](assets/query_editor_nveau_17.png)

1. 我們現在將更改查詢，以查找不住在倫敦的聯繫人。

   在列 **[!UICONTROL City (location/@city)]** 中選擇 **[!UICONTROL Expression]** 作為運 **[!UICONTROL different from]** 算符並在列中 **[!UICONTROL London]** 輸 **[!UICONTROL Value]** 入。

   ![](assets/query_editor_08.png)

1. 這會帶你去窗 **[!UICONTROL Data formatting]** 戶。 檢查列順序。 在「帳戶編號」欄下方向上移動「城市」欄。

   取消勾選「名字」欄，將其從清單中移除。

   ![](assets/query_editor_nveau_15.png)

1. 在窗口 **[!UICONTROL Data preview]** 中，按一下 **[!UICONTROL Start the preview of the data]**。 此函式計算查詢的結果。

   該選 **[!UICONTROL Column results]** 項卡在列中顯示查詢結果。

   結果會顯示所有擁有「orange.co.uk」電子郵件網域且不住在倫敦的收件者。 「名字」欄未顯示，因為在上一階段中未勾選。 帳號會以遞減順序排序。

   ![](assets/query_editor_nveau_12.png)

   該選 **[!UICONTROL XML result]** 項卡以XML格式顯示結果。

   ![](assets/query_editor_nveau_13.png)

   該選 **[!UICONTROL Generated QSL queries]** 項卡以SQL格式顯示查詢結果。

   ![](assets/query_editor_nveau_14.png)
