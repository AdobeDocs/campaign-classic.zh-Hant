---
product: campaign
title: 傳遞大綱
description: 進一步了解傳送大綱工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: b4dee085-ccc4-43fd-850d-1501a99272aa
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 1%

---

# 傳遞大綱{#delivery-outline}

![](../../assets/common.svg)

**傳遞大綱**&#x200B;可讓您在促銷活動工作流程中使用大綱。 大綱必須預先在促銷活動中建立。

如需Adobe Campaign中傳送大綱的詳細資訊，請參閱此[區段](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

要配置活動，您只需選擇所需的大綱以及計畫的聯繫日期。 您可以新增類型或類型規則，以新增篩選規則。

## 範例：透過傳遞大綱插入優惠方案 {#example--inserting-an-offer-via-a-delivery-outline}

**傳遞大綱**&#x200B;活動可在促銷活動工作流程中使用，讓您呈現在傳遞大綱中參考且來自目前進行中的促銷活動的選件。

>[!NOTE]
>
>必須安裝&#x200B;**Interaction**&#x200B;軟體包。

1. 在工作流程中，新增傳送大綱活動之前，請先新增傳送活動。
1. 在傳送大綱活動中，指定要使用的大綱。

   如需指定傳送大綱的詳細資訊，請參閱此[區段](../../campaign/using/marketing-campaign-deliveries.md#associating-and-structuring-resources-linked-via-a-delivery-outline)。

1. 根據您的傳送完成可用欄位。
1. 可能有兩種情況：

   * 如果您想要呼叫優惠方案引擎，請核取&#x200B;**[!UICONTROL Restrict the number of propositions selected]**&#x200B;方塊。 指定要在傳遞中呈現的優惠方案空間和主張數量。

      優惠方案引擎會考量優惠方案的權重和適用性規則。

   * 如果您未核取方塊，傳遞大綱中的所有選件都會呈現，而不需要呼叫選件引擎。

   預覽會考量傳送中指定的選件數量。 執行工作流程時，會考慮傳送大綱中指定的編號。

   ![](assets/int_compo_offre_wf1.png)
