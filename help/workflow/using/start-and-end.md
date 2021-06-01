---
product: campaign
title: 開始和結束
description: 進一步了解開始和結束工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---

# 開始和結束{#start-and-end}

**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;活動可讓您以圖形方式標示工作流程的開始和結束。 這些活動沒有功能影響，因此是可選活動。

* **[!UICONTROL Start]**

   執行工作流程會從沒有入站轉變的活動和開始類型活動開始。

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   您可以配置&#x200B;**[!UICONTROL End]**&#x200B;活動以中斷正在執行的所有任務。 若要這麼做，請連按兩下活動以顯示其屬性，然後核取適當的選項。

   ![](assets/s_user_segmentation_end.png)

   啟用結束活動時，工作表中的資料會自動刪除。 如果不需要，並且為了避免不必要的載入，您可以選取在最後一個活動輸出時停用轉變。 例如，在傳送輸出中，如果未排程任何程式，請取消勾選下列相關選項：

   ![](assets/s_advuser_delivery_option_no_output.png)
