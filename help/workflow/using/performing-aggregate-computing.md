---
product: campaign
title: 執行彙總計算
description: 了解如何在查詢中執行匯總計算
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 5b05788f-498b-4a84-bdde-2852900f0129
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 2%

---

# 執行彙總計算 {#performing-aggregate-computing}

在此範例中，我們想根據性別來計算住在倫敦的收件者人數。

* 需要選取哪個表格？

   收件者表格(**nms:recipient**)

* 輸出欄中應選取哪些欄位？

   主鍵（含計數）和性別

* 根據哪些條件篩選資訊？

   根據住在倫敦的收件者

若要建立此範例，請套用下列步驟：

1. 在&#x200B;**[!UICONTROL Data to extract]**&#x200B;中，定義主鍵的計數（如上例所示）。 在輸出欄中新增&#x200B;**[!UICONTROL Gender]**&#x200B;欄位。 檢查&#x200B;**[!UICONTROL Gender]**&#x200B;欄中的&#x200B;**[!UICONTROL Group]**&#x200B;選項。 這樣，收件者就會依性別分組。

   ![](assets/query_editor_nveau_27.png)

1. 在&#x200B;**[!UICONTROL Sorting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:此處不需要排序。
1. 設定資料篩選。 在此，您希望將選擇限制為居住在倫敦的聯繫人。

   ![](assets/query_editor_22.png)

   >[!NOTE]
   >
   >值區分大小寫。 如果在條件中輸入的「倫敦」值沒有大寫字母，且收件者清單中包含帶大寫字母的「倫敦」一詞，則查詢將失敗。

1. 在&#x200B;**[!UICONTROL Data formatting]**&#x200B;視窗中，按一下&#x200B;**[!UICONTROL Next]**:此示例不需要格式設定。
1. 在預覽視窗中，按一下&#x200B;**[!UICONTROL Launch data preview]**。

   依性別分類的每個排序有三個不同的值：女性為&#x200B;**2**，男性為&#x200B;**1**，性別未知時為&#x200B;**0**。 在本例中，該清單包含10名婦女、16名男子和2名性別不詳的人。

   ![](assets/query_editor_agregat_04.png)
