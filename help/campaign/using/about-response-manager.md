---
title: 關於回應管理器
seo-title: 關於回應管理器
description: 關於回應管理器
seo-description: null
page-status-flag: never-activated
uuid: 3087a96d-50fb-488a-9b76-70eb5c67deed
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: a4669fee-4512-455f-b495-ebd5a0746b76
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 關於回應管理器{#about-response-manager}

## 目標 {#objectives}

Adobe Campaign提供回應管理應用程式（回應管理員），可讓您評估行銷活動的成功與獲利能力，或為所有通訊通道（電子郵件、行動裝置、電話、直效郵件、傳真、代理商等）提供建議。

## 假設概念 {#hypothesis-concept}

可以在從接觸日期開始的給定期間內配置假設，以推斷在接收到遞送之後被定位的假設的行為。 這些假設是以儲存購 **買項目** ，以及這些購買項目詳細資訊的交易表格為基礎。

假設在時間上是有限的，可以應用到控制組以與目標種群進行比較。 假設結果由計算完 **成後** ，自動更新的指標提供。 連結至假設的ROI將會納入促銷活動報表。

此外，隨 **「回應管理** 」提供的報表可讓您總結與營業額增加、利潤計算以及交付或優惠的投資報酬率相關的資訊。

此外，由於購買詳細資訊行，您可以指定假設，以便只專注於某個特定產品。

例如，在促銷項目的傳送後，我們希望評估產生的收入。 我們套用假設，即任何在觸發傳送後的一個月內購買了至少一項商品的收件者，都已對此動作做出反應。 回應管理會根據此假設，決定應將哪些採購請求行指派給該請求行。 然後，根據此，將可確定產生的收入作為這些行的總和。

>[!CAUTION]
>
>響應管理器是一個 **[!UICONTROL Campaign]** 選項。 請檢查您的授權合約。

您也可以計算收到交貨或優惠的收件者家庭的所有反應。

每個假設都會連結至單一交易表。 一個交付或提供可以連結到多個假設。

## 方法 {#method}

開始使用「響應管理器」之前，請參 [閱「配置](../../campaign/using/configuration.md) 」並執行必要的配置。

為了在傳送或選件上啟動假設，您必須在範本中定義其內容，以用於您建立的每個假設。

要定義和建立測量假設，請應用以下過程：

1. 定義假設模型。 請參閱 [建立假設模型](../../campaign/using/hypothesis-templates.md#creating-a-hypothesis-model)。
1. 在現有傳送上建立一或多個假設。 請參閱 [參考促銷活動傳送中的假設](../../campaign/using/creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)。

   或

   建立選件的一或多個假設。 請參閱 [建立選件的假設](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-an-offer)。

1. 檢查假設結果。 請參閱假 [說追蹤](../../campaign/using/hypothesis-tracking.md)。
1. 如有必要，重新啟動假設。 請參 [閱「在傳送時即時建立假設」](../../campaign/using/creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)。

