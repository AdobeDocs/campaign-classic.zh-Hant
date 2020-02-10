---
title: 選件引擎
seo-title: 選件引擎
description: 選件引擎
seo-description: null
page-status-flag: never-activated
uuid: a8f6056a-80e6-4f9f-81f5-563c98d11d28
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: 08987595-e80c-4197-ad1e-9aa7cfc7c3eb
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 選件引擎{#offer-engine}

此活 **[!UICONTROL Offer engine]** 動可讓您在傳送前定義對選件引擎的呼叫。

此活動與引擎呼叫的富集活動具有相同的原則，即在傳送之前，使用引擎計算的選件來富集傳入人口資料。

![](assets/int_offerengine_activity2.png)

設定查詢後(請參閱本 [節](../../workflow/using/query.md)):

1. 新增並開啟活 **[!UICONTROL Offer engine]** 動。
1. 填寫各種可用欄位，以指定對選件引擎參數（選件空間、類別或主題、連絡日期、要保留的選件數）的呼叫。 引擎會根據這些參數自動計算要新增的選件。

   >[!CAUTION]
   >
   >如果您使用本活動，則只會儲存傳送中使用的選件主張。

   ![](assets/int_offerengine_activity1.png)

1. 然後設定與您所選渠道對應的傳送活動。 請參閱 [跨通道傳送](../../workflow/using/cross-channel-deliveries.md)。

