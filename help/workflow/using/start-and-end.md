---
solution: Campaign Classic
product: campaign
title: 開始和結束
description: 進一步瞭解開始和結束工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---


# 開始和結束{#start-and-end}

**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活動可讓您以圖形方式標籤工作流的開始和結束。 這些活動沒有功能影響，因此是可選的。

* **[!UICONTROL Start]**

   執行工作流以活動開始，沒有傳入的轉移和「開始」類型活動。

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   您可以配置&#x200B;**[!UICONTROL End]**&#x200B;活動以中斷正在進行的所有任務。 若要這麼做，請連按兩下活動以顯示其屬性，並勾選適當的選項。

   ![](assets/s_user_segmentation_end.png)

   當結束活動啟用時，工作台中的資料會自動刪除。 如果不需要，並且為了避免不必要的載荷，您可以選擇在最後一次活動輸出時禁用轉換。 例如，在傳送輸出時，如果沒有排程，請取消勾選相關選項，如下所示：

   ![](assets/s_advuser_delivery_option_no_output.png)

