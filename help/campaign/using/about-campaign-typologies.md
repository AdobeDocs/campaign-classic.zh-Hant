---
solution: Campaign Classic
product: campaign
title: 關於行銷活動態樣
description: 關於行銷活動態樣
audience: campaign
content-type: reference
topic-tags: campaign-optimization
translation-type: tm+mt
source-git-commit: 87028ec81a8cae6793d45d7c840511b59cd0287c
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 12%

---


# 關於行銷活動態樣{#about-campaign-typologies}

「促銷活動最佳化」是Adobe Campaign模組，可讓您控制、篩選及監控傳送的傳送。 為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這可確保傳送的訊息符合客戶和公司通訊政策的需求和期望。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#typologies-video)

>[!NOTE]
>
>視您的產品而定，可以包含促銷活動最佳化或附加元件。 請檢查您的授權合約。

## 類型規則 {#typology-rules}

有了Adobe Campaign，您可以設計和套用四種類型的排版規則：

* **篩** 選規則，可讓您根據條件排除部分目標。有關詳細資訊，請參閱[過濾規則](../../campaign/using/filtering-rules.md)。
* **可** 讓您控制行銷疲勞的壓力規則。有關詳細資訊，請參閱[壓力規則](../../campaign/using/pressure-rules.md)。
* **能** 力規則，可讓您限制負載，以確保最佳處理條件。有關詳細資訊，請參閱[控制容量](../../campaign/using/consistency-rules.md#controlling-capacity)。
* **控** 制規則，可讓您在發送消息之前檢查消息的有效性。有關詳細資訊，請參閱[控制規則](../../campaign/using/control-rules.md)。

建立類型規則後，會將其分組為促銷活動類型，這些類型在傳送中參考。 請參閱[應用類型](#applying-typologies)。

## 類型 {#typologies}

促銷活動類型學可以包含數種[類型學規則](#typology-rules)，但傳送只能參考一種類型學。

**[!UICONTROL Rules]**&#x200B;標籤可讓您新增、刪除或檢視要套用的排版規則。

![](assets/campaign_opt_rules_tab.png)

## 應用類型{#applying-typologies}

建立並套用類型學至傳送的步驟如下：

1. 建立類型學規則。

   在&#x200B;**[!UICONTROL Administration > Campaign management > Typology management > Typology rules]**&#x200B;節點中可找到分類規則。

   下列章節說明促銷活動中的不同規則：[銷售壓力規則](../../campaign/using/pressure-rules.md)、[容量規則](../../campaign/using/consistency-rules.md#controlling-capacity)、[控制規則](../../campaign/using/control-rules.md)和[過濾規則](../../campaign/using/filtering-rules.md)。

1. 建立類型，並參考您建立的規則。

   通過&#x200B;**[!UICONTROL Administration > Campaign Management > Typology management]** > **[!UICONTROL Typologies]**&#x200B;節點訪問類型。

1. 設定您的傳送方式，以使用您建立的排版。 如需詳細資訊，請參閱[本章節](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 透過促銷活動模擬來測試和控制行為。 如需促銷活動模擬的詳細資訊，請參閱[本節](../../campaign/using/campaign-simulations.md)。

在準備交貨期間，當符合標準時，將排除收件者。 您可以檢查日誌以監控排除。有關壓力類型學規則的範例使用案例，請參閱[本頁](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)。

## 教學課程影片 {#typologies-video}

### 如何使用類型學規則建立疲勞管理

此視訊說明如何運用排版規則在Adobe Campaign實施疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25090?quality=12)

### 如何使用預先定義的篩選器來設定疲勞管理

疲勞管理控制訊息傳送的頻率和數量，以避免收件者過度招攬。 如果您的促銷活動例項中沒有促銷活動最佳化模組，您可以設定預先定義的篩選條件，以依據收到的訊息數量來篩選目標群體
本影片說明如何使用濾鏡在Adobe Campaign Classic實施疲勞管理。

>[!VIDEO](https://video.tv.adobe.com/v/25091?quality=12)

其他促銷活動操作影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。

**相關主題**

* [將自動業務規則套用至任何渠道的傳送](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)

* [關於行銷活動態樣](../../campaign/using/pressure-rules.md)

* [使用壓力規則管理行銷疲勞](https://docs.adobe.com/content/help/en/campaign-classic/using/orchestrating-campaigns/campaign-optimization/pressure-rules.html)