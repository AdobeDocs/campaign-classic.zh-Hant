---
product: campaign
title: 關於行銷活動態樣
description: 關於行銷活動態樣
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
feature: Typology Rules, Campaigns
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 19%

---

# 關於行銷活動態樣{#about-campaign-typologies}

Campaign Optimization是Adobe Campaign模組，可讓您控制、篩選及監控傳送的傳送。 為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這樣可確保傳送的訊息符合客戶和公司通訊政策的需求及期望。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#typologies-video)

>[!NOTE]
>
>根據您的產品，可包含Campaign Optimization或附加元件。 請檢查您的授權合約。

## 類型規則 {#typology-rules}

透過Adobe Campaign，您可以設計和套用四種型別的型別規則：

* **篩選** 可讓您根據條件排除部分目標的規則。 有關詳細資訊，請參閱 [篩選規則](filtering-rules.md).
* **壓力** 可讓您控制行銷疲勞的規則。 有關詳細資訊，請參閱 [壓力規則](pressure-rules.md).
* **容量** 可讓您限制載入以確保最佳處理條件的規則。 有關詳細資訊，請參閱 [控制容量](consistency-rules.md#controlling-capacity).
* **控制** 可讓您在傳送訊息之前檢查訊息是否有效的規則。 有關詳細資訊，請參閱 [控制規則](control-rules.md).

建立後，型別規則會依傳遞中參考的行銷活動型別分組。 另請參閱 [套用型別](#applying-typologies).

## 類型 {#typologies}

行銷活動型別可包含數個 [型別規則](#typology-rules)，但傳送只能參考一個型別。

此 **[!UICONTROL Rules]** 索引標籤可讓您新增、刪除或檢視要套用的型別規則。

![](assets/campaign_opt_rules_tab.png)

## 套用型別 {#applying-typologies}

建立並套用型別至傳送的步驟列示如下：

1. 建立型別規則。

   型別規則可在下列連結中找到： **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 節點。

   以下幾節將說明Campaign中可用的不同規則： [銷售壓力規則](pressure-rules.md)， [容量規則](consistency-rules.md#controlling-capacity)， [控制規則](control-rules.md) 和 [篩選規則](filtering-rules.md).

1. 建立型別並參考您建立的規則。

   型別可透過 **[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]** 節點。

1. 設定您的傳遞方式，以使用您建立的型別。 如需詳細資訊，請參閱[本章節](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 透過行銷活動模擬測試及控制行為。 如需促銷活動模擬的詳細資訊，請參閱 [本節](campaign-simulations.md).

在準備傳遞期間，符合條件時會排除收件者。 您可以檢查日誌以監控排除。有關壓力型別規則的範例使用案例，請參閱 [此頁面](pressure-rules.md#use-cases-on-pressure-rules).

## 教學課程影片 {#typologies-video}

### 如何使用型別規則設定疲勞管理

此影片說明如何運用型別規則，在Adobe Campaign中實施疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用預先定義的篩選器來設定疲勞管理

疲勞管理控制傳訊的頻率和數量，以避免過度向收件者發送請求。 如果您的行銷活動執行個體中沒有行銷活動最佳化模組，您可以設定預先定義的篩選器，以根據收到的訊息數量篩選目標母體。此影片說明如何使用篩選器在Adobe Campaign Classic中實施疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

提供其他Campaign操作說明影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).

**相關主題**

* [開始使用型別和疲勞管理](pressure-rules.md)

