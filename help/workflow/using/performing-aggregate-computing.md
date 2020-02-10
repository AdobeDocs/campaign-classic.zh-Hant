---
title: 執行聚合計算
description: 瞭解如何在查詢中執行聚合計算
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


# 執行聚合計算 {#performing-aggregate-computing}

在此範例中，我們想根據性別來計算住在倫敦的收件者人數。

* 需要選擇哪個表？

   收件者表(**nms:recipient**)

* 輸出欄中應選取哪些欄位？

   主鍵（含計數）和性別

* 篩選資訊所依據的條件為何？

   根據住在倫敦的收件者

若要建立此範例，請套用下列步驟：

1. 在 **[!UICONTROL Data to extract]**&#x200B;中，定義主鍵的計數（如上例所示）。 在輸出 **[!UICONTROL Gender]** 欄中新增欄位。 勾選欄 **[!UICONTROL Group]** 中的選 **[!UICONTROL Gender]** 項。 這樣，收件者就會依性別分組。

   ![](assets/query_editor_nveau_27.png)

1. 在視窗中 **[!UICONTROL Sorting]** ，按一下 **[!UICONTROL Next]**:這裡不需要排序。
1. 設定資料篩選。 在這裡，您希望將選擇限制在居住在倫敦的聯繫人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值區分大小寫。 如果在條件中輸入「倫敦」值時沒有大寫字母，而收件人清單中包含帶有大寫字母的單字「倫敦」，查詢將失敗。

1. 在視窗中 **[!UICONTROL Data formatting]** ，按一下 **[!UICONTROL Next]**:此範例不需要格式設定。
1. 在預覽視窗中，按一下 **[!UICONTROL Launch data preview]**。

   每個排序依性別有三個不同的值：女 **性** 2人，男性 **1人，** 性別不 **** 明時0人。 在本例中，該清單包含10名婦女、16名男子和2名性別不詳的人。

   ![](assets/query_editor_agregat_04.png)
