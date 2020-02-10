---
title: 開始和結束
seo-title: 開始和結束
description: 開始和結束
seo-description: null
page-status-flag: never-activated
uuid: ec0c818c-c307-4f50-908c-507bce0ea27b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 8b239d5e-2317-42c8-9fee-7d40bea624da
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 開始和結束{#start-and-end}

使用 **[!UICONTROL Start]** 和 **[!UICONTROL End]** 活動，您可以以圖形方式標籤工作流的開始和結束。 這些活動沒有功能影響，因此是可選的。

* **[!UICONTROL Start]**

   執行工作流以活動開始，沒有傳入的轉移和「開始」類型活動。

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   您可以配置活 **[!UICONTROL End]** 動以中斷正在進行的所有任務。 若要這麼做，請連按兩下活動以顯示其屬性，並勾選適當的選項。

   ![](assets/s_user_segmentation_end.png)

   當結束活動啟用時，工作台中的資料會自動刪除。 如果不需要，並且為了避免不必要的載荷，您可以選擇在最後一次活動輸出時禁用轉換。 例如，在傳送輸出時，如果沒有排程，請取消勾選相關選項，如下所示：

   ![](assets/s_advuser_delivery_option_no_output.png)

