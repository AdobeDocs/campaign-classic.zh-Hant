---
product: campaign
title: 關於行銷活動態樣
description: 關於行銷活動態樣
audience: campaign
content-type: reference
topic-tags: campaign-optimization
exl-id: 6d5b8584-4aa1-4d9a-89d9-d41da75dd323
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 15%

---

# 關於行銷活動態樣{#about-campaign-typologies}

![](../../assets/v7-only.svg)

促銷活動最佳化是Adobe Campaign模組，可讓您控制、篩選及監控傳送的傳送。 為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這可確保傳送的訊息符合客戶的需求和期望，以及公司通訊政策。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#typologies-video)

>[!NOTE]
>
>視您的產品而定，可包含促銷活動最佳化或附加元件。 請檢查您的授權合約。

## 類型規則 {#typology-rules}

透過Adobe Campaign，您可以設計並套用四種類型規則：

* **** 篩選規則，可讓您根據條件排除部分目標。有關詳細資訊，請參閱[篩選規則](filtering-rules.md)。
* **** 壓力規則可讓您控制行銷疲勞。有關詳細資訊，請參閱[壓力規則](pressure-rules.md)。
* **** 容量規則，可讓您限制負載，以保證最佳處理條件。有關詳細資訊，請參閱[控制容量](consistency-rules.md#controlling-capacity)。
* **** 可讓您在傳送訊息之前檢查訊息有效性的控制規則。有關詳細資訊，請參閱[控制規則](control-rules.md)。

建立類型規則後，會將類型規則分組到行銷活動類型中，並在傳送中參考。 請參閱[套用類型](#applying-typologies)。

## 類型 {#typologies}

促銷活動類型可包含數個[類型規則](#typology-rules)，但傳送只能參考一個類型。

**[!UICONTROL Rules]**&#x200B;標籤可讓您新增、刪除或檢視要套用的類型規則。

![](assets/campaign_opt_rules_tab.png)

## 套用類型 {#applying-typologies}

建立類型並套用至傳送的步驟如下：

1. 建立類型規則。

   在&#x200B;**[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**&#x200B;節點中找到類型規則。

   以下小節將說明Campaign中可用的不同規則：[銷售壓力規則](pressure-rules.md)、[容量規則](consistency-rules.md#controlling-capacity)、[控制規則](control-rules.md)和[篩選規則](filtering-rules.md)。

1. 建立類型並參考您建立的規則。

   可透過&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;節點存取類型。

1. 設定您的傳送，以使用您建立的類型。 如需詳細資訊，請參閱[本章節](applying-rules.md#applying-a-typology-to-a-delivery)。
1. 透過行銷活動模擬來測試和控制行為。 如需促銷活動模擬的詳細資訊，請參閱[此區段](campaign-simulations.md)。

在準備傳送期間，當符合條件時，會排除收件者。 您可以檢查日誌以監控排除。[此頁面](pressure-rules.md#use-cases-on-pressure-rules)提供壓力類型規則的使用案例範例。

## 教學課程影片 {#typologies-video}

### 如何使用類型規則設定疲勞管理

此影片說明如何運用類型規則，在Adobe Campaign中實作疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用預先定義的篩選器來設定疲勞管理

疲勞管理控制傳訊的頻率和數量，以避免過度向收件者發送請求。 如果您的促銷活動例項中沒有促銷活動最佳化模組，您可以設定預先定義的篩選器，以依據收到的訊息數量篩選目標母體
此影片說明如何使用篩選器在Adobe Campaign Classic中實作疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

您可以在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得其他促銷活動作法影片。

**相關主題**

* [將自動業務規則套用至任何管道上的傳送](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [開始使用類型和疲勞管理](pressure-rules.md)
