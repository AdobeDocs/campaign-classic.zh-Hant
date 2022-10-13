---
product: campaign
title: 關於回應管理器
description: 關於回應管理器
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 878ba2b532d5cb59af77b6450b12ae5d2ff149b2
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 13%

---

# 開始使用Campaign回應管理員{#about-response-manager}

![](../../assets/common.svg)

Adobe Campaign 提供 回應管理附加功能，讓您可以衡量行銷活動的成功和盈利能力，或為跨通訊頻道 (例如：電子郵件、行動裝置、直接郵件等) 提供建議。

## 假設 {#hypothesis-concept}

可以在從聯繫日期開始的給定期間內配置假設，以在接收到傳送之後推斷那些目標的行為。 這些假設是基於 **交易** 用於保存購買的表以及這些購買的詳細資訊。

假設被限制在時間上，並且可以被應用到控制組以與目標群體進行比較。 假設結果由提供 **指標** 計算完成後，就會自動更新。 連結至假設的ROI將會納入行銷活動報表中。

此外， **報告** 回應管理員提供，讓您匯總與營業額增加、利潤計算，以及傳送或優惠方案的投資報酬率相關的資訊。

此外，由於購買詳細資訊行，您可以指定假設，以僅關注一個特定產品。

例如，在促銷項目的傳送後，我們想要評估產生的收入。 我們會套用假設，即任何在傳送觸發後的月份中購買至少一項的收件者，都已對此動作做出反應。 回應管理會根據此假設，決定應將哪些採購請求行指派給它。 然後，根據此，將可判斷產生的收入為這些行的總和。

>[!CAUTION]
>
>回應管理員是 **[!UICONTROL Campaign]** 選項。 請檢查您的授權合約。

您也可以計算收到送貨或優惠的收件人整個家庭的所有反應。

每個假設都連結至單一交易表。 一個傳遞或選件可以連結至多個假設。

## 實施步驟 {#method}

開始使用「回應管理員」之前，請參閱 [設定](configuration.md) 並執行必要的配置。

若要在傳送或選件上啟動假設，您必須在將用於建立之每個假設的範本中定義其內容。

要定義和建立測量假設，請應用以下過程：

1. 定義假設模型。 [了解更多](hypothesis-templates.md#creating-a-hypothesis-model)
1. 在現有傳送上建立一或多個假設。 [了解更多](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   或

   對選件建立一或多個假設。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 檢查假設結果。 [了解更多](hypothesis-tracking.md)
1. 如有必要，請重新啟動假設。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
