---
product: campaign
title: 傳遞大綱
description: 瞭解有關「交貨大綱」工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 傳遞大綱{#delivery-outline}

![](../../assets/common.svg)

的 **交付大綱** 允許您在市場活動工作流中使用大綱。 大綱必須事先在活動中建立。

有關Adobe Campaign交付大綱的詳細資訊，請參閱 [節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

要配置活動，您只需選擇您喜歡的大綱以及計畫的聯繫日期。 可以通過添加類型或類型規則來添加篩選規則。

## 示例：通過交貨大綱插入報價 {#example--inserting-an-offer-via-a-delivery-outline}

的 **交付大綱** 活動，可在市場活動工作流中提供，用於顯示當前市場活動中在交貨大綱中引用的優惠。

>[!NOTE]
>
>的 **交互** 必須安裝軟體包。

1. 在工作流中，在添加交貨活動之前添加交貨大綱活動。
1. 在交貨大綱活動中，指定要使用的大綱。

   有關指定交貨大綱的詳細資訊，請參閱 [節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

1. 根據您的交貨完成可用欄位。
1. 可能有兩種情況：

   * 如果您想呼叫聘用引擎，請檢查 **[!UICONTROL Restrict the number of propositions selected]** 框。 指定提供空間和將在交付中顯示的建議數。

      報價引擎將考慮報價權重和資格規則。

   * 如果未選中此框，則在不致電聘用引擎的情況下，將顯示交貨大綱中的所有聘用。

   預覽會考慮交貨中指定的優惠數量。 執行工作流時，將考慮交貨大綱中指定的編號。

   ![](assets/int_compo_offre_wf1.png)
