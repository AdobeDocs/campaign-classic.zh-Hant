---
product: campaign
title: 開始和結束
description: 瞭解有關「開始」和「結束」工作流活動的詳細資訊
feature: Workflows
exl-id: 56dfbaf3-93de-4ade-b4ad-9b54d239c7a5
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 4%

---

# 開始和結束{#start-and-end}

![](../../assets/common.svg)

的 **[!UICONTROL Start]** 和 **[!UICONTROL End]** 活動允許您以圖形方式標籤工作流的開始和結束。 這些活動對職能沒有影響，因此是可選的。

* **[!UICONTROL Start]**

   執行工作流以沒有入站轉換和「開始」類型活動的活動開始。

   ![](assets/s_user_segmentation_start_stop.png)

* **[!UICONTROL End]**

   您可以配置 **[!UICONTROL End]** 活動，以中斷所有正在執行的任務。 為此，請按兩下該活動以顯示其屬性，並檢查相應的選項。

   ![](assets/s_user_segmentation_end.png)

   啟用結束活動後，工作表中的資料將自動刪除。 如果不必這樣做，並且要避免不必要的載入，您可以選擇在上次活動輸出時禁用轉換。 例如，在交貨輸出中，如果沒有計畫流程，請取消選中下面所示的相關選項：

   ![](assets/s_advuser_delivery_option_no_output.png)
