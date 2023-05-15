---
product: campaign
title: 關於行銷活動態樣
description: 關於行銷活動態樣
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Typology Rules
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 19%

---

# 關於行銷活動態樣{#about-campaign-typologies}

促銷活動最佳化是Adobe Campaign模組，可讓您控制、篩選及監控傳送的傳送。 為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這樣可確保傳送的訊息符合客戶和公司通訊政策的需求及期望。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#typologies-video)

>[!NOTE]
>
>視您的產品而定，可包含促銷活動最佳化或附加元件。 請檢查您的授權合約。

## 類型規則 {#typology-rules}

透過Adobe Campaign，您可以設計並套用四種類型規則：

* **篩選** 規則，可讓您根據條件排除目標的一部分。 有關詳細資訊，請參閱 [篩選規則](filtering-rules.md).
* **壓力** 可讓您控制行銷疲勞的規則。 有關詳細資訊，請參閱 [壓力規則](pressure-rules.md).
* **容量** 可讓您限制負載以保證最佳處理條件的規則。 有關詳細資訊，請參閱 [控制容量](consistency-rules.md#controlling-capacity).
* **控制** 規則可讓您在傳送訊息之前檢查訊息的有效性。 有關詳細資訊，請參閱 [控制規則](control-rules.md).

建立類型規則後，會將類型規則分組到行銷活動類型中，並在傳送中參考。 請參閱 [套用類型](#applying-typologies).

## 類型 {#typologies}

行銷活動類型可包含數個 [類型規則](#typology-rules)，但傳送只能參考一個類型。

此 **[!UICONTROL Rules]** 索引標籤可讓您新增、刪除或檢視要套用的類型規則。

![](assets/campaign_opt_rules_tab.png)

## 套用類型 {#applying-typologies}

建立類型並套用至傳送的步驟如下：

1. 建立類型規則。

   在 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 節點。

   以下小節將說明Campaign中可用的不同規則： [銷售壓力規則](pressure-rules.md), [容量規則](consistency-rules.md#controlling-capacity), [控制規則](control-rules.md) 和 [篩選規則](filtering-rules.md).

1. 建立類型並參考您建立的規則。

   類型可透過 **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** 節點。

1. 設定您的傳送，以使用您建立的類型。 如需詳細資訊，請參閱[本章節](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 透過行銷活動模擬來測試和控制行為。 如需促銷活動模擬的詳細資訊，請參閱 [本節](campaign-simulations.md).

在準備傳送期間，當符合條件時，會排除收件者。 您可以檢查日誌以監控排除。有關壓力類型規則的範例使用案例，請參閱 [本頁](pressure-rules.md#use-cases-on-pressure-rules).

## 教學課程影片 {#typologies-video}

### 如何使用類型規則設定疲勞管理

此影片說明如何運用類型規則，在Adobe Campaign中實作疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用預先定義的篩選器來設定疲勞管理

疲勞管理控制傳訊的頻率和數量，以避免過度向收件者發送請求。 如果您的促銷活動例項中沒有促銷活動最佳化模組，您可以設定預先定義的篩選器，以依據收到的訊息數量篩選目標母體。此影片說明如何使用篩選器在Adobe Campaign Classic中實作疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

提供其他Campaign作法影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).

**相關主題**

* [開始使用類型和疲勞管理](pressure-rules.md)

