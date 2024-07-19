---
product: campaign
title: 關於回應管理員
description: 關於回應管理員
feature: Campaigns
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: b5c0e960-2afe-4a98-b82c-d47a74659703
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 4%

---

# 開始使用Campaign回應管理員{#about-response-manager}



Adobe Campaign提供回應管理附加功能，讓您可以衡量行銷活動的成功和盈利能力，或為跨通訊頻道（例如：電子郵件、行動裝置、直接郵件等）提供建議。

## 假設 {#hypothesis-concept}

您可以設定假設在從聯絡日期開始的指定期間內以推斷接收傳遞後目標對象的行為。 這些假設是以&#x200B;**交易**&#x200B;資料表為基礎，該資料表儲存購買和這些購買的詳細資料。

假設在時間上受到限制，可套用至控制組，以便與目標人口進行比較。 假設結果由&#x200B;**指標**&#x200B;提供，計算完成後會自動更新。 行銷活動報告會考慮與假設連結的ROI。

此外，回應管理員提供的&#x200B;**報表**&#x200B;可讓您彙總與營業額增加、利潤計算相關的資訊，以及傳遞或優惠的ROI。

此外，有了購買詳細資料行，您可以指定假設以僅專注於一種特定產品，例如。

例如，促銷某個專案的傳遞後，我們想評估產生的收入。 我們套用以下假設，即任何在觸發傳遞後一個月內購買至少一個專案的收件者已對此動作做出反應。 回應管理會根據此假設，決定應將哪些購買請求明細指派給它。 然後，根據此結果，將可以確定產生的收入是這些行的總和。

>[!CAUTION]
>
>回應管理員是&#x200B;**[!UICONTROL Campaign]**&#x200B;選項。 請檢查您的授權合約。

您也可以計算收到傳遞或優惠方案的收件者整個家庭的所有回應。

每個假設都與單一交易表連結。 一個傳遞或選件可以連結到多個假設。

## 實施步驟 {#method}

開始使用回應管理員之前，請參閱[設定](configuration.md)並執行必要的設定。

為了針對傳遞或優惠方案啟動假設，您需要在範本中定義其內容，該範本將用於您建立的每個假設。

若要定義與建立測量假設，請套用下列程式：

1. 定義假設模型。 [了解更多](hypothesis-templates.md#creating-a-hypothesis-model)
1. 在現有傳遞上建立一或多個假設。 [了解更多](creating-hypotheses.md#referencing-a-hypothesis-in-a-campaign-delivery)

   或

   在優惠方案上建立一或多個假設。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-an-offer)

1. 檢查假設結果。 [了解更多](hypothesis-tracking.md)
1. 如有必要，請重新啟動假設。 [了解更多](creating-hypotheses.md#creating-a-hypothesis-on-the-fly-on-a-delivery)
