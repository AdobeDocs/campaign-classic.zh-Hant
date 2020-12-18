---
solution: Campaign Classic
product: campaign
title: 執行設定
description: 執行設定
audience: interaction
content-type: reference
topic-tags: simulating-offers
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '138'
ht-degree: 4%

---


# 執行設定{#execution-settings}

建立模擬時，可以根據需要指定執行設定。 這些設定允許您根據活動優先順序在活動較低時執行模擬，或在日誌中記錄SQL查詢。 此階段是可選的。

這些設定稍後可在模擬視窗的&#x200B;**[!UICONTROL General]**&#x200B;標籤中變更。

![](assets/offer_simulation_008.png)

* **[!UICONTROL Schedule execution for a time of low activity]** :可讓您根據選擇的優先順序（低、平均或高）排程模擬，以最佳化Adobe Campaign效能。
* **[!UICONTROL Priority]** :這是模擬所套用的層級，以排程它。勾選&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;選項時，促銷活動處理工作流程會選擇低活動時間來啟動促銷活動。
* **[!UICONTROL Log SQL queries in the journal]** :此功能僅供專家使用者使用。它可讓您在顯示SQL查詢的日誌中添加一個頁籤，以在模擬完成錯誤時檢測可能的故障。

