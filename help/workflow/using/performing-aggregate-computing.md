---
solution: Campaign Classic
product: campaign
title: 執行彙總計算
description: 瞭解如何在查詢中執行聚合計算
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---


# 執行彙總計算 {#performing-aggregate-computing}

在此範例中，我們想根據性別來計算住在倫敦的收件者人數。

* 需要選擇哪個表？

   收件者表(**nms:recipient**)

* 輸出欄中應選取哪些欄位？

   主鍵（含計數）和性別

* 篩選資訊所依據的條件為何？

   根據住在倫敦的收件者

若要建立此範例，請套用下列步驟：

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;中，定義主鍵的計數（如上例所示）。 在輸出欄中新增&#x200B;**[!UICONTROL Gender]**&#x200B;欄位。 選中&#x200B;**[!UICONTROL Gender]**&#x200B;列中的&#x200B;**[!UICONTROL Group]**&#x200B;選項。 這樣，收件者就會依性別分組。

   ![](assets/query_editor_nveau_27.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:這裡不需要排序。
1. 設定資料篩選。 在這裡，您希望將選擇限制在居住在倫敦的聯繫人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值區分大小寫。 如果在條件中輸入「倫敦」值時沒有大寫字母，而收件人清單中包含帶有大寫字母的單字「倫敦」，查詢將失敗。

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:此範例不需要格式設定。
1. 在預覽窗口中，按一下&#x200B;**[!UICONTROL Launch data preview]**。

   每個排序依性別有三個不同的值：女性&#x200B;**2**，男性&#x200B;**1**，性別未知時&#x200B;**0**。 在本例中，該清單包含10名婦女、16名男子和2名性別不詳的人。

   ![](assets/query_editor_agregat_04.png)
