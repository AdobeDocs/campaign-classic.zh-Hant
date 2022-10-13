---
product: campaign
title: 追蹤假設
description: 了解如何在Campaign回應管理員中追蹤假設
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 878ba2b532d5cb59af77b6450b12ae5d2ff149b2
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 1%

---

# 假設追蹤{#hypothesis-tracking}

![](../../assets/common.svg)

假設計算的結果適用於Adobe Campaign平台的不同層級：由假設和目標群體反應計算的指標可透過實際假設以及透過促銷活動和傳送提供的假設報告中看到。

## 假設結果 {#hypothesis-results}

### 指標 {#indicators}

計算假設後，會自動更新數個測量指標。 這些可在 **[!UICONTROL General]** 的下方。

![](assets/response_hypothesis_delivery_example_010.png)

這些指標是：

* **回應者聯絡人數**:與假設相符的已聯絡個人數。
* **聯繫的響應率**:回應者聯絡人數/傳送期間聯絡的總人數。
* **回應者控制組聯繫人數**:符合假設的控制組數。
* **控制組的響應率**:回應者控制組數/傳送控制組總數。
* **反應數**:表中包含個人、假設和事務表之間關係的記錄數。

如需完整的指標清單，請按一下 **[!UICONTROL Display the list]** 連結：

![](assets/response_hypothesis_indicators_002.png)

指標提供了以下資訊：

* **聯繫的總人口收入**:所聯繫的個人總數。
* **控制組的總收入**:控制組數的總金額。
* **每個連絡的平均收入**:總額/已聯繫。
* **控制組平均收入**:總金額/控制組。
* **每個聯繫人的總利潤**:已聯繫的總利潤。
* **控制組的總利潤**:控制組的總利潤。
* **每個聯繫人的平均利潤**:總利潤/已聯繫。
* **控制組的平均裕度**:總利潤/控制組。
* **額外收入**:（聯繫的平均收入 — 控制組的平均收入）&#42;已聯繫的數量
* **其他利潤**:（已聯繫的平均裕度 — 控制組的平均裕度）/已聯繫的數量
* **每個聯繫人的平均成本**:計算的傳送成本/聯繫人數。
* **ROI**:傳送的計算成本/每個連絡的總利潤
* **有效ROI**:計算的交貨成本/附加利潤。
* **顯著性**:根據促銷活動顯著性包含0到3的值。

### 回應 {#reactions}

您可以透過 **[!UICONTROL Reactions]** 標籤。

1. 假設計算完成後，請前往 **[!UICONTROL Campaign management > Measurement hypotheses]** Adobe Campaign樹的節點。
1. 選取所需的假設，然後按一下 **[!UICONTROL Reactions]** 標籤來檢視行銷活動後可能購買某些內容的收件者清單。

   ![](assets/response_hypothesis_reactions_001.png)

## 報告 {#reports}

此 **[!UICONTROL Hypothesis report]** 可讓您檢視行銷活動和傳送上執行之假設的結果。 此報表包含由假設計算的指標(如需詳細資訊，請參閱 [指標](#indicators))。

* **在促銷活動層級**:按一下 **[!UICONTROL Reports]** 相關促銷活動的連結，並選取 **[!UICONTROL Hypothesis report]**. 此報表包含行銷活動傳送的清單，以及針對每次傳送計算的假設。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在傳送層級**:若要存取報表，請開啟相關的傳送，按一下 **[!UICONTROL Reports]** 在 **[!UICONTROL Summary]** 標籤，然後選取 **[!UICONTROL Hypothesis report]**. 如果針對相同傳送計算了數個假設，報表將包含所有假設。

   ![](assets/response_hypothesis_delivery_report_001.png)
