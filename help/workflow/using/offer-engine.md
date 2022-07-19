---
product: campaign
title: 優惠引擎
description: 優惠引擎
feature: Workflows, Interaction
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 4%

---

# 優惠引擎{#offer-engine}

![](../../assets/v7-only.svg)

的 **[!UICONTROL Offer engine]** 活動允許您在交貨前定義對供應引擎的呼叫。

此活動與引擎調用的富集活動具有相同的原則，方法是在交貨前用引擎計算的優惠來富集入站人口資料。

![](assets/int_offerengine_activity2.png)

配置查詢後（請參閱此） [節](query.md)):

1. 添加並開啟 **[!UICONTROL Offer engine]** 的子菜單。
1. 填寫各個可用欄位，以指定提供引擎參數（提供空間、類別或主題、聯繫日期、要保留的優惠數量）的呼叫。 引擎將根據這些參數自動計算要添加的報價。

   >[!CAUTION]
   >
   >如果您使用此活動，則只儲存交付中使用的優惠建議。

   ![](assets/int_offerengine_activity1.png)

1. 然後配置與所選渠道對應的傳遞活動。 請參閱 [跨渠道交付](cross-channel-deliveries.md)。
