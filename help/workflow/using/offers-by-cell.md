---
product: campaign
title: 依儲存格列出的優惠
description: 依儲存格列出的優惠
feature: Workflows, Targeting Activity, Interaction
exl-id: 72b17b48-093a-4eb9-a848-3c1570e49b61
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 8%

---

# 依儲存格列出的優惠{#offers-by-cell}

![](../../assets/v7-only.svg)

的 **[!UICONTROL Offers by cell]** 活動允許您將入站總量（例如從查詢）分配到多個段，並指定要為這些段中的每個段提供的優惠。

此活動只能與 **交互**。 有關詳細資訊，請參閱 [節](../../interaction/using/about-outbound-channels.md)。

操作步驟：

1. 添加 **[!UICONTROL Offers by cell]** 在指定目標人口後開啟該活動。
1. 在 **[!UICONTROL General]** 頁籤，選擇要在其上顯示聘用的聘用空間。
1. 在 **[!UICONTROL Cells]** 頁籤，使用 **[!UICONTROL Add]** 按鈕：

   * 使用可用過濾和限制規則指定子集填充。
   * 接下來，選擇要向子集顯示的優惠。 可用的優惠是那些在上一步選擇的優惠空間中符合條件的優惠。

      ![](assets/int_offer_per_cell1.png)

1. 然後配置與所選渠道對應的傳遞活動。 請參閱 [跨渠道交付](cross-channel-deliveries.md)。
