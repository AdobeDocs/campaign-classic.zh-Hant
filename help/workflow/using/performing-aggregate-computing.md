---
product: campaign
title: 執行彙總計算
description: 瞭解如何在查詢中執行聚合計算
feature: Workflows
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# 執行彙總計算 {#performing-aggregate-computing}

![](../../assets/v7-only.svg)

在本例中，我們想根據性別來計算在倫敦生活的受助人數。

* 需要選擇哪個表？

   收件人表(**nms：收件人**)

* 應在輸出列中選擇哪些欄位？

   主鍵（含計數）和性別

* 根據什麼條件過濾資訊？

   根據住在倫敦的收件人

要建立此示例，請應用以下步驟：

1. 在 **[!UICONTROL Data to extract]**，定義主鍵的計數（如上例所示）。 添加 **[!UICONTROL Gender]** 的子菜單。 檢查 **[!UICONTROL Group]** 的上界 **[!UICONTROL Gender]** 的雙曲餘切值。 這樣，受援者將按性別分組。

   ![](assets/query_editor_nveau_27.png)

1. 在 **[!UICONTROL Sorting]** 窗口，按一下 **[!UICONTROL Next]**:這裡不需要分揀。
1. 配置資料篩選。 在此，您希望將選擇限制為住在倫敦的聯繫人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值區分大小寫。 如果「倫敦」值在沒有大寫字母的條件下輸入，並且收件人清單包含帶大寫字母的「倫敦」字樣，則查詢將失敗。

1. 在 **[!UICONTROL Data formatting]** 窗口，按一下 **[!UICONTROL Next]**:此示例不需要格式設定。
1. 在預覽窗口中，按一下 **[!UICONTROL Launch data preview]**。

   按性別分類的每種排序有三個不同的值： **2** 對於女性， **1** 為男性和 **0** 性別未知時。 在本例中，名單中有10名婦女、16名男子和2名性別不為人知的人。

   ![](assets/query_editor_agregat_04.png)
