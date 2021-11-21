---
product: campaign
title: 執行設定
description: 執行設定
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: e2dea4a0-9ed8-47b6-a16b-eeee653d2290
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---

# 執行設定{#execution-settings}

![](../../assets/v7-only.svg)

建立模擬時，您可以視需要指定執行設定。 這些設定可讓您根據活動優先順序在活動較低時執行模擬，或在記錄中記錄SQL查詢。 此階段為選填階段。

這些設定稍後可在 **[!UICONTROL General]** 頁簽。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** :可讓您根據選取的優先順序（低、平均或高）排程模擬，以最佳化Adobe Campaign效能。
* **[!UICONTROL Priority]** :這是用於模擬以計畫它的級別。 當 **[!UICONTROL Schedule execution for a time of low activity]** 選項，則促銷活動處理工作流程會選取低活動時間以啟動促銷活動。
* **[!UICONTROL Log SQL queries in the journal]** :此功能僅供專家使用者使用。 它可讓您在顯示SQL查詢的記錄檔中新增索引標籤，以在模擬完成錯誤時偵測可能的故障。
