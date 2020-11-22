---
solution: Campaign Classic
product: campaign
title: 傳遞大綱
description: 進一步瞭解「傳送大綱」工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---


# 傳遞大綱{#delivery-outline}

傳送 **大綱** ，可讓您在促銷活動工作流程中使用大綱。 必須事先在促銷活動中建立大綱。

如需Adobe Campaign中傳送大綱的詳細資訊，請參閱本 [節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

要配置活動，您只需選擇所需的大綱以及計畫的聯繫人日期。 您可以新增類型或類型學規則來新增篩選規則。

## 範例：透過傳送大綱插入選件 {#example--inserting-an-offer-via-a-delivery-outline}

促銷 **活動工作流程中提供的傳送大綱** ，可讓您顯示目前進行中促銷活動的傳送大綱中參考的選件。

>[!NOTE]
>
>必 **須安裝** Interaction包。

1. 在工作流程中，新增傳送大綱活動之前，先新增傳送大綱活動。
1. 在傳送大綱活動中，指定您要使用的大綱。

   有關指定傳送大綱的詳細資訊，請參閱本 [節](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

1. 根據您的傳送完成可用欄位。
1. 可能有兩種情況：

   * 如果您想要呼叫選件引擎，請核取方 **[!UICONTROL Restrict the number of propositions selected]** 塊。 指定選件空間和將在傳送中呈現的主張數目。

      選件引擎會考量到選件權重和資格規則。

   * 如果您未勾選此方塊，傳送大綱中的所有選件都會顯示，而不會呼叫選件引擎。

   預覽會考量傳送中指定的選件數。 執行工作流時，會考慮到在傳送大綱中指定的數字。

   ![](assets/int_compo_offre_wf1.png)

