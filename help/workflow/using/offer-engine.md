---
product: campaign
title: 優惠引擎
description: 優惠引擎
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 8db4b04f-7754-4a49-ab72-afc916888ebb
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 4%

---

# 優惠引擎{#offer-engine}

![](../../assets/common.svg)

此 **[!UICONTROL Offer engine]** 活動可讓您在傳送前定義對優惠方案引擎的呼叫。

此活動的運作原則與引擎呼叫的擴充活動相同，方法是在傳送前使用引擎計算的選件擴充入站母體資料。

![](assets/int_offerengine_activity2.png)

設定查詢後(請參閱 [節](query.md)):

1. 新增並開啟 **[!UICONTROL Offer engine]** 活動。
1. 填寫各種可用欄位，以指定對優惠方案引擎參數（優惠方案空間、類別或主題、聯絡日期、要保留的優惠方案數量）的呼叫。 引擎會自動計算要根據這些參數新增的選件。

   >[!CAUTION]
   >
   >如果您使用此活動，則只會儲存傳送中使用的優惠方案。

   ![](assets/int_offerengine_activity1.png)

1. 然後設定與您選擇的通道相對應的傳送活動。 請參閱 [跨通道傳遞](cross-channel-deliveries.md).
