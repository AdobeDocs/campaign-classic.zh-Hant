---
product: campaign
title: 關於回應管理器
description: 關於回應管理器
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 3%

---

# 開始使用促銷活動回應管理員{#about-response-manager}

Adobe Campaign提供Response Management附加元件，可讓您衡量行銷活動的成功與獲利能力，或提供跨通訊管道的建議：電子郵件、行動裝置、直接郵件等。

## 假設{#hypothesis-concept}

可以在從聯繫日期開始的給定期間內配置假設，以在接收到傳送之後推斷那些目標的行為。 這些假設基於&#x200B;**transaction**&#x200B;表，該表保存了購買和這些購買的詳細資訊。

假設被限制在時間上，並且可以被應用到控制組以與目標群體進行比較。 假設結果由&#x200B;**indicators**&#x200B;提供，在計算完成後自動更新。 連結至假設的ROI將會納入行銷活動報表中。

此外，隨「回應管理員」提供的&#x200B;**報表**&#x200B;可讓您匯總與營業額增加、利潤計算以及傳送或優惠方案的ROI相關的資訊。

此外，由於購買詳細資訊行，您可以指定假設，以僅關注一個特定產品。

例如，在促銷項目的傳送後，我們想要評估產生的收入。 我們會套用假設，即任何在傳送觸發後的月份中購買至少一項的收件者，都已對此動作做出反應。 回應管理會根據此假設，決定應將哪些採購請求行指派給它。 然後，根據此，將可判斷產生的收入為這些行的總和。

>[!CAUTION]
>
>「響應管理器」是&#x200B;**[!UICONTROL Campaign]**&#x200B;選項。 請檢查您的授權合約。

您也可以計算收到送貨或優惠的收件人整個家庭的所有反應。

每個假設都連結至單一交易表。 一個傳遞或選件可以連結至多個假設。

## 實施步驟 {#method}

開始使用「響應管理器」之前，請參閱[Configuration](../../campaign/using/configuration.md)並執行必要的配置。

若要在傳送或選件上啟動假設，您必須在將用於建立之每個假設的範本中定義其內容。

要定義和建立測量假設，請應用以下過程：

1. 定義假設模型。 請參閱[建立假設模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 在現有傳送上建立一或多個假設。 請參閱[參考促銷活動傳送中的假設](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)。

   或

   對選件建立一或多個假設。 請參閱[在選件上建立假設](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)。

1. 檢查假設結果。 請參閱[假設追蹤](../../campaign/using/hypothesis-tracking.md)。
1. 如有必要，請重新啟動假設。 請參閱[在傳送時即時建立假設](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)。
