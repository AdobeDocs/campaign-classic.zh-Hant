---
title: 關於促銷活動類型
seo-title: 關於促銷活動類型
description: 關於促銷活動類型
seo-description: null
page-status-flag: never-activated
uuid: ec89fb14-7e2f-4e9f-b7ab-3c2caf93a697
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: campaign-optimization
discoiquuid: 72c5151c-ce1e-425a-9aee-beefe9f21a67
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 44d8ba19f2e79d30229239312e6a5148d247fb28

---


# 關於促銷活動類型{#about-campaign-typologies}

「促銷活動最佳化」是Adobe Campaign模組，可讓您控制、篩選及監控傳送的傳送。 為了避免行銷活動之間發生衝突，Adobe Campaign 可以套用特定限制規則來測試各種組合。這可確保傳送的訊息符合客戶和公司通訊政策的需求和期望。

>[!NOTE]
>
>視您的產品而定，可以包含促銷活動最佳化或附加元件。 請檢查您的授權合約。

## 類型學規則 {#typology-rules}

有了Adobe Campaign，您可以設計並套用四種類型的排版規則：

1. **篩選規則** ，可讓您根據條件排除部分目標。 For more on this, refer to [Filtering rules](../../campaign/using/filtering-rules.md).
1. **壓力規則** ，可讓您控制行銷疲勞。 For more on this, refer to [Pressure rules](../../campaign/using/pressure-rules.md).
1. **容量規則** ，可讓您限制負載，以確保最佳處理條件。 For more on this, refer to [Controlling capacity](../../campaign/using/consistency-rules.md#controlling-capacity).
1. **控制規則** ，可讓您在傳送訊息之前先檢查訊息的有效性。 For more on this, refer to [Control rules](../../campaign/using/control-rules.md).

建立類型規則後，會將其分組為促銷活動類型，這些類型在傳送中參考。 請參 [閱套用類型](#applying-typologies)。

## 類型 {#typologies}

促銷活動類型學可以包含數 [種類型學規則](#typology-rules)，但傳送只能參照一種類型學。

此標 **[!UICONTROL Rules]** 簽可讓您新增、刪除或檢視要套用的排版規則。

![](assets/campaign_opt_rules_tab.png)

## 套用類型 {#applying-typologies}

建立並套用類型學至傳送的步驟如下：

1. 建立類型學規則。

   在節點中可找到類型學 **[!UICONTROL Administration > Campaign management > Typology management > Typology rules]** 規則。

   下列章節說明促銷活動中的不同規則：銷售 [壓力規則](../../campaign/using/pressure-rules.md)、 [能力規則](../../campaign/using/consistency-rules.md#controlling-capacity)、 [控制規則](../../campaign/using/control-rules.md) 和 [](../../campaign/using/filtering-rules.md)篩選規則。

1. 建立類型，並參考您建立的規則。

   您可透過>節點存 **[!UICONTROL Administration > Campaign Management > Typology management]** 取類 **[!UICONTROL Typologies]** 型。

1. 設定您的傳送方式，以使用您建立的排版。 如需詳細資訊，請參閱[本小節](../../campaign/using/applying-rules.md#applying-a-typology-to-a-delivery)。
1. 透過促銷活動模擬來測試和控制行為。 For more on campaign simulations, refer to [this section](../../campaign/using/campaign-simulations.md).

在準備交貨期間，當符合標準時，將排除收件者。 您可以檢查記錄檔以監控排除。 本頁提供壓力類型學規則的範例使 [用案例](../../campaign/using/pressure-rules.md#use-cases-on-pressure-rules)。

**相關主題**

* [將自動業務規則套用至任何渠道的傳送](https://helpx.adobe.com/campaign/kb/simplifying-campaign-management-acc.html#Applyautomaticbusinessrulestodeliveriesonanychannel)