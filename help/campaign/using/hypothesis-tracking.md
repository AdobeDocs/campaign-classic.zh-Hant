---
title: 假設追蹤
seo-title: 假設追蹤
description: 假設追蹤
seo-description: null
page-status-flag: never-activated
uuid: cb949a9d-8bbe-446b-b5b4-22234a91a68b
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: response-manager
discoiquuid: 4452bfc6-9ac4-4d81-a63c-879a163c13ee
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b47dcfa0e4ee2e5e43e7aa14b94e12fd70ff9c2d

---


# 假設追蹤{#hypothesis-tracking}

假設計算的結果適用於Adobe Campaign平台的不同層級：由假設和目標群體反應計算的指標可通過實際假設以及通過促銷活動和交付獲得的假設報告中可見。

## 假設結果 {#hypothesis-results}

### 指標 {#indicators}

一旦計算了假設，就會自動更新多個測量指標。 這些可在假設的 **[!UICONTROL General]** 標籤中找到。

![](assets/response_hypothesis_delivery_example_010.png)

這些指標有：

* **回應者聯絡人數**:與假設相符的接觸個體數目。
* **聯繫的回應率**:回應者聯絡人數／傳送期間聯絡的總人數。
* **回應者控制群組聯絡人數**:符合假設的控制群組數。
* **控制組的響應率**:回應者控制群組數量／傳送控制群組總數。
* **反應次數**:表中包含個人、假設和事務表之間關係的記錄數。

如需指標的完整清單，請按一下 **[!UICONTROL Display the list]** 連結：

![](assets/response_hypothesis_indicators_002.png)

指標提供了以下資訊：

* **已聯絡的人口總收入**:總金額超過所聯絡的個人數。
* **控制組之總收益**:總金額超過控制群組數目。
* **每個連絡人的平均收入**:總金額／已聯絡。
* **控制組平均收入**:總金額／控制組。
* **每位連絡人的總利潤**:已聯絡的總利潤。
* **控制組毛利總額**:控制組的毛利總額。
* **每位連絡人的平均利潤**:總利潤／已聯絡。
* **控制群組的平均毛利**:總利潤／控制組。
* **額外收入**:（已聯繫的平均收入——控制組的平均收入）*已聯繫的數量
* **額外利潤**:（已聯繫的平均利潤——控制組的平均利潤）/已聯繫的數量
* **每位連絡人的平均成本**:計算的傳送成本／聯絡人數。
* **投資報酬**:交貨的計算成本／每位連絡人的毛利總計
* **有效的投資報酬率**:計算交貨成本／額外利潤。
* **重要性**:包含0到3的值，視促銷活動重要性而定。

### 反應 {#reactions}

您可以透過標籤來檢視收件者對假設的反 **[!UICONTROL Reactions]** 應。

1. 假設計算完成後，請前往Adobe **[!UICONTROL Campaign management > Measurement hypotheses]** Campaign樹狀結構的節點。
1. 選取所要的假設，然後按一下標 **[!UICONTROL Reactions]** 簽，以檢視可能在行銷活動後購買某些內容的收件者清單。

   ![](assets/response_hypothesis_reactions_001.png)

## 報表 {#reports}

可 **[!UICONTROL Hypothesis report]** 讓您檢視在促銷活動和傳送上執行之假設的結果。 此報表包含由假設計算的指標(如需詳細資訊，請參閱 [指標](#indicators))。

* **在促銷活動層級**:按一下 **[!UICONTROL Reports]** 相關促銷活動的連結，然後選取 **[!UICONTROL Hypothesis report]**。 此報表包含促銷活動傳送的清單，以及針對每個傳送計算的假設。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在傳送層級**:若要存取報表，請開啟相關的傳送，按一下標 **[!UICONTROL Reports]** 簽中的 **[!UICONTROL Summary]** 並選取 **[!UICONTROL Hypothesis report]**。 如果針對相同傳送計算了數個假設，報表將包含所有假設。

   ![](assets/response_hypothesis_delivery_report_001.png)
