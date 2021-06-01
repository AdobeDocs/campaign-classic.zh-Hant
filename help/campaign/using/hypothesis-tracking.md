---
product: campaign
title: 假設追蹤
description: 假設追蹤
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 1%

---

# 假設追蹤{#hypothesis-tracking}

假設計算的結果適用於Adobe Campaign平台的不同層級：由假設和目標群體反應計算的指標可透過實際假設以及透過促銷活動和傳送提供的假設報告中看到。

## 假設結果{#hypothesis-results}

### 指標 {#indicators}

計算假設後，會自動更新數個測量指標。 這些在假設的&#x200B;**[!UICONTROL General]**&#x200B;標籤中可用。

![](assets/response_hypothesis_delivery_example_010.png)

這些指標是：

* **回應者聯絡人數**:與假設相符的已聯絡個人數。
* **聯繫的回應率**:回應者聯絡人數/傳送期間聯絡的總人數。
* **回應者控制組聯繫人數**:符合假設的控制組數。
* **控制組的響應率**:回應者控制組數/傳送控制組總數。
* **反應次數**:表中包含個人、假設和事務表之間關係的記錄數。

如需指標的完整清單，請按一下&#x200B;**[!UICONTROL Display the list]**&#x200B;連結：

![](assets/response_hypothesis_indicators_002.png)

指標提供了以下資訊：

* **已聯繫的總人口收入**:所聯繫的個人總數。
* **控制組的總收入**:控制組數的總金額。
* **每個連絡的平均收入**:總額/已聯繫。
* **控制組的平均收入**:總金額/控制組。
* **每個連絡人的總利潤**:已聯繫的總利潤。
* **控制組的總利潤**:控制組的總利潤。
* **每次連絡的平均利潤**:總利潤/已聯繫。
* **控制組的平均裕度**:總利潤/控制組。
* **其他收入**:（已聯繫的平均收入 — 控制組的平均收入）*已聯繫的數量
* **其他利潤**:（已聯繫的平均裕度 — 控制組的平均裕度）/已聯繫的數量
* **每個聯繫人的平均成本**:計算的傳送成本/聯繫人數。
* **ROI**:傳送的計算成本/每個連絡的總利潤
* **有效ROI**:計算的交貨成本/附加利潤。
* **重要性**:根據促銷活動顯著性包含0到3的值。

### 反應 {#reactions}

您可以透過&#x200B;**[!UICONTROL Reactions]**&#x200B;標籤檢視收件者對假設的反應。

1. 假設計算完成後，前往Adobe Campaign樹的&#x200B;**[!UICONTROL Campaign management > Measurement hypotheses]**&#x200B;節點。
1. 選取所需的假設，然後按一下&#x200B;**[!UICONTROL Reactions]**&#x200B;標籤，以檢視行銷活動後可能購買項目的收件者清單。

   ![](assets/response_hypothesis_reactions_001.png)

## 報告 {#reports}

**[!UICONTROL Hypothesis report]**&#x200B;可讓您檢視行銷活動和傳送上所執行假設的結果。 此報表包含由假設計算的指標（如需詳細資訊，請參閱[指標](#indicators)）。

* **在促銷活動層級**:按一下 **[!UICONTROL Reports]** 相關促銷活動的連結，然後選取 **[!UICONTROL Hypothesis report]**。此報表包含行銷活動傳送的清單，以及針對每次傳送計算的假設。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在傳送層級**:若要存取報表，請開啟相關傳送，按一 **[!UICONTROL Reports]** 下索引 **[!UICONTROL Summary]** 標籤中的並選 **[!UICONTROL Hypothesis report]**&#x200B;取如果針對相同傳送計算了數個假設，報表將包含所有假設。

   ![](assets/response_hypothesis_delivery_report_001.png)
