---
product: campaign
title: 執行設定
description: 執行設定
feature: Interaction, Offers
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '150'
ht-degree: 5%

---

# 執行設定{#execution-settings}



建立模擬時，您可以視需要指定執行設定。 這些設定可讓您在活動較少期間根據其優先順序執行模擬，或在記錄中記錄SQL查詢。 此階段為選填。

這些設定稍後可在 **[!UICONTROL General]** 「模擬」視窗的標籤。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** ：可讓您根據所選的優先順序（低、平均或高）排程模擬，以最佳化Adobe Campaign效能。
* **[!UICONTROL Priority]** ：這是套用至模擬以排程它的層級。 當 **[!UICONTROL Schedule execution for a time of low activity]** 選項已核取，促銷活動處理工作流程會選取低活動時間以開始促銷活動。
* **[!UICONTROL Log SQL queries in the journal]** ：此功能僅供專家使用者使用。 它可讓您新增標籤到顯示SQL查詢的記錄中，以在模擬完成時偵測可能的故障。
