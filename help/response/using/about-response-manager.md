---
product: campaign
title: 關於回應管理器
description: 關於回應管理器
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 13%

---

# 開始使用市場活動響應管理器{#about-response-manager}

![](../../assets/common.svg)

Adobe Campaign 提供 回應管理附加功能，讓您可以衡量行銷活動的成功和盈利能力，或為跨通訊頻道 (例如：電子郵件、行動裝置、直接郵件等) 提供建議。

## 假設 {#hypothesis-concept}

可以在從接觸日期開始的給定期間上配置假設，以在接收到遞送之後推斷那些目標者的行為。 這些假設是基於 **交易記錄** 保存採購的表和這些採購的詳細資訊。

假設在時間上是有限的，並且可以應用於控制組以與目標種群進行比較。 假設結果由 **指標** 計算完成後自動更新。 活動報告將考慮與這些假設相關聯的投資回報率。

另外， **報告** 提供的響應管理器使您能夠匯總與營業額增加、毛利計算以及交付或優惠的ROI相關的資訊。

此外，由於採購詳細資訊行，您可以指定假設以僅關注一個特定產品。

例如，在促銷物料的交貨後，我們希望評估生成的收入。 我們採用的假設是，在觸發交貨後的一個月中，任何購買了至少一件物品的接收者都對此行為作出反應。 響應管理將根據這一假設確定應將哪些採購請求行分配給它。 然後，基於此，可以確定最終收入為這些行的總和。

>[!CAUTION]
>
>響應管理器是 **[!UICONTROL Campaign]** 的雙曲餘切值。 請檢查您的授權合約。

您還可以計算收到送貨或要約的受贈者整個家庭的所有反應。

每個假設都連結到單個事務表。 一個遞送或提供可以與多個假設相連結。

## 實施步驟 {#method}

開始使用響應管理器之前，請參閱 [配置](configuration.md) 並進行必要的配置。

為了在交貨或要約上啟動假說，您需要在模板中定義其上下文，該模板將用於您建立的每個假說。

要定義和建立測量假設，請應用以下過程：

1. 定義假設模型。 [了解更多](hypothesis-templates.md#creating-a-hypothesis-model)
1. 在現有交貨上建立一個或多個假設。 [了解更多](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   或

   建立關於提議的一個或多個假設。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 檢查假設結果。 [了解更多](hypothesis-tracking.md)
1. 如有必要，重新發射假設。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
