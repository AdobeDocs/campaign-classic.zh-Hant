---
solution: Campaign Classic
product: campaign
title: 關於回應管理器
description: 關於回應管理器
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: dc3151a77350aa2b2acd989a57f5b489c1a98962
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 3%

---

# 開始使用促銷活動回應管理員{#about-response-manager}

Adobe Campaign公司提供回應管理附加元件，可讓您衡量行銷活動的成功與獲利能力，或提供跨通訊管道的建議：電子郵件、行動裝置、直效郵件等。

## 假設{#hypothesis-concept}

可以在從接觸日期開始的給定期間內配置假設，以推斷在接收到遞送之後被定位的假設的行為。 這些假設是以&#x200B;**transaction**&#x200B;表格為基礎，該表格儲存購買項目和這些購買項目的詳細資料。

假設在時間上是有限的，可以應用到控制組以與目標種群進行比較。 假設結果由&#x200B;**指示符**&#x200B;提供，這些指示符在計算完成後自動更新。 連結至假設的ROI將會納入促銷活動報表。

此外，「回應管理員」提供的&#x200B;**報表**&#x200B;可讓您匯總與營業額增加、利潤計算以及傳送或選件的投資報酬率相關的資訊。

此外，由於購買詳細資訊行，您可以指定假設，以便只專注於某個特定產品。

例如，在促銷項目的傳送後，我們希望評估產生的收入。 我們套用假設，即任何在觸發傳送後的一個月內購買了至少一項商品的收件者，都已對此動作做出反應。 回應管理會根據此假設，決定應將哪些採購請求行指派給該請求行。 然後，根據此，將可確定產生的收入作為這些行的總和。

>[!CAUTION]
>
>響應管理器是&#x200B;**[!UICONTROL Campaign]**&#x200B;選項。 請檢查您的授權合約。

您也可以計算收到交貨或優惠的收件者家庭的所有反應。

每個假設都會連結至單一交易表。 一個交付或提供可以連結到多個假設。

## 實施步驟 {#method}

開始使用Response Manager之前，請參閱[Configuration](../../campaign/using/configuration.md)並執行必要的配置。

為了在傳送或選件上啟動假設，您必須在範本中定義其內容，以用於您建立的每個假設。

要定義和建立測量假設，請應用以下過程：

1. 定義假設模型。 請參閱[建立假設模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 在現有傳送上建立一或多個假設。 請參閱[參考促銷活動傳送中的假設](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)。

   或

   建立選件的一或多個假設。 請參閱[建立選件的假設](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)。

1. 檢查假設結果。 請參閱[假設追蹤](../../campaign/using/hypothesis-tracking.md)。
1. 如有必要，重新啟動假設。 請參閱[在傳送時即時建立假設](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)。
