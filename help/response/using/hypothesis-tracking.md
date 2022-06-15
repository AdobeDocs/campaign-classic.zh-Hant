---
product: campaign
title: 軌跡假設
description: 瞭解如何跟蹤營銷活動響應經理中的假設
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: d36e1881726af6238c4e0caecb7b299b594691f2
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# 假設追蹤{#hypothesis-tracking}

![](../../assets/common.svg)

假設計算的結果可在Adobe Campaign平台的各個級別獲得：通過假設和目標群體反應計算的指標通過實際假設以及通過運動和交付提供的假設報告可見。

## 假設結果 {#hypothesis-results}

### 指標 {#indicators}

一旦計算了假設，就自動更新多個測量指標。 這些可在 **[!UICONTROL General]** 的下界。

![](assets/response_hypothesis_delivery_example_010.png)

這些指標是：

* **被申請人聯繫人數**:與假設相符的人數。
* **聯繫的響應率**:被申請人聯繫人數/交貨期間聯繫的總人數。
* **被申請者控制組聯繫人數**:與假設匹配的控制組數。
* **控制組的響應速率**:響應者控制組數/傳遞控制組總數。
* **反應數**:表中包含個體、假設和事務表之間關係的記錄數。

對於指示器的完整清單，按一下 **[!UICONTROL Display the list]** 連結：

![](assets/response_hypothesis_indicators_002.png)

指標提供了以下資訊：

* **聯繫的人口總收入**:所聯繫的個人總數。
* **控制組的總收入**:控制組數的總金額。
* **每個聯繫人的平均收入**:總金額/聯繫。
* **控制組的平均收入**:總金額/控制組。
* **每個聯繫人的毛利合計**:聯繫的總利潤。
* **控制組的毛利合計**:控制組的總毛利。
* **每個聯繫人的平均毛利**:總毛利/聯繫。
* **控制組的平均邊距**:總邊距/控制組。
* **額外收入**:（聯繫人的平均收入 — 控制組的平均收入）&#42;已聯繫的數量
* **附加利潤**:（平均聯繫邊距 — 控制組的平均聯繫邊距）/聯繫次數
* **每個聯繫人的平均成本**:計算的交貨成本/聯繫人數。
* **ROI**:交貨的計算成本/每個聯繫人的毛利總額
* **有效ROI**:計算的交貨成本/附加毛利。
* **意義**:包含值0到3，具體取決於市場活動重要性。

### 回應 {#reactions}

您可以通過 **[!UICONTROL Reactions]** 頁籤。

1. 假設計算完成後，轉到 **[!UICONTROL Campaign management > Measurement hypotheses]** Adobe Campaign樹的節點。
1. 選擇所需假設，然後按一下 **[!UICONTROL Reactions]** 頁籤，查看市場推廣活動後可能購買內容的收件人清單。

   ![](assets/response_hypothesis_reactions_001.png)

## 報告 {#reports}

的 **[!UICONTROL Hypothesis report]** 允許您查看對市場活動和交貨執行的假設的結果。 本報告包含由假設計算的指標(有關詳細資訊，請參閱 [指標](#indicators))。

* **在市場活動級別**:按一下 **[!UICONTROL Reports]** 相關市場活動的連結，並選擇 **[!UICONTROL Hypothesis report]**。 此報表包含市場活動交付的清單以及為每個交付計算的假設。

   ![](assets/response_hypothesis_campaign_report_001.png)

* **在交貨級別**:要訪問報告，請開啟相關的交付，按一下 **[!UICONTROL Reports]** 的 **[!UICONTROL Summary]** 的子菜單。 **[!UICONTROL Hypothesis report]**。 如果為同一交付計算了若干假設，報告將包含所有假設。

   ![](assets/response_hypothesis_delivery_report_001.png)
