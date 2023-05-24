---
product: campaign
title: 執行設定
description: 執行設定
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# 執行設定{#execution-settings}



建立模擬時，您可以視需要指定執行設定。 這些設定可讓您根據其優先順序，在活動較少期間執行模擬，或在記錄中記錄SQL查詢。 此階段為選擇性。

這些設定稍後可在以下位置變更： **[!UICONTROL General]** 「模擬」視窗的頁標。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** ：可讓您根據所選的優先順序（低、平均或高）排程模擬，以最佳化Adobe Campaign效能。
* **[!UICONTROL Priority]** ：這是套用至模擬以排程它的層級。 當 **[!UICONTROL Schedule execution for a time of low activity]** 選項已核取，行銷活動處理工作流程會選取低活動時間以開始行銷活動。
* **[!UICONTROL Log SQL queries in the journal]** ：此功能僅供專家使用者使用。 它可讓您在顯示SQL查詢的記錄中新增索引標籤，以在模擬完成時發生錯誤時偵測可能的故障。
