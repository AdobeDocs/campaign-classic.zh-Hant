---
solution: Campaign Classic
product: campaign
title: 優惠方案引擎
description: 優惠方案引擎
audience: workflow
content-type: reference
topic-tags: targeting-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 4%

---


# 優惠方案引擎{#offer-engine}

**[!UICONTROL Offer engine]**&#x200B;活動可讓您在傳送前定義對選件引擎的呼叫。

此活動與引擎呼叫的富集活動具有相同的原則，即在傳送之前，使用引擎計算的選件來富集傳入人口資料。

![](assets/int_offerengine_activity2.png)

設定查詢後（請參閱此[section](../../workflow/using/query.md)）:

1. 新增並開啟&#x200B;**[!UICONTROL Offer engine]**&#x200B;活動。
1. 填寫各種可用欄位，以指定對選件引擎參數（選件空間、類別或主題、連絡日期、要保留的選件數）的呼叫。 引擎會根據這些參數自動計算要新增的選件。

   >[!CAUTION]
   >
   >如果您使用本活動，則只會儲存傳送中使用的選件主張。

   ![](assets/int_offerengine_activity1.png)

1. 然後設定與您所選渠道對應的傳送活動。 請參閱[跨通道遞送](../../workflow/using/cross-channel-deliveries.md)。

