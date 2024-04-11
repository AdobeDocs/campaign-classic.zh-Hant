---
product: campaign
title: 追蹤假設
description: 瞭解如何在Campaign回應管理員中追蹤假設
feature: Campaigns, Monitoring, Reporting
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: campaign
content-type: reference
topic-tags: response-manager
exl-id: 1dc6d03b-698c-4750-9563-0676fcd185df
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 1%

---

# 假設追蹤{#hypothesis-tracking}



假設計算的結果可在Adobe Campaign平台的各個層級取得：透過實際假設以及透過行銷活動和傳遞提供的假設報告中，可以看到由假設計算出的指標和目標母體反應。

## 假設結果 {#hypothesis-results}

### 指標 {#indicators}

計算假設後，會自動更新數個測量指標。 這些選項可在 **[!UICONTROL General]** 假設的索引標籤。

![](assets/response_hypothesis_delivery_example_010.png)

這些指標包括：

* **回應聯絡人的數量**：符合假設的聯絡個人數量。
* **聯絡的回應率**：回應聯絡人數量/傳送期間聯絡的總人數。
* **回應控制組聯絡人的數量**：符合假設的控制組數目。
* **控制組的回應率**：回應控制組數目/傳遞控制組總數。
* **回應數**：包含個人、假設和交易表之間關係的表格中的記錄數。

如需完整的指標清單，請按一下 **[!UICONTROL Display the list]** 連結：

![](assets/response_hypothesis_indicators_002.png)

下列資訊由指標提供：

* **已聯絡人口的總收入**：總數超過聯絡的個人數量。
* **控制組的總收入**：控制組總數中的金額。
* **每個聯絡人的平均收入**：總金額/已聯絡。
* **控制組的平均收入**：總金額/控制組。
* **每個聯絡人的總利潤**：聯絡的總利潤。
* **控制組的總利潤**：控制組的總利潤。
* **每個聯絡人的平均利潤**：總利潤/已聯絡。
* **控制組的平均利潤**：總邊界/控制組。
* **其他收入**：（聯絡的平均收入 — 控制組的平均收入）&#42;連絡人數
* **其他利潤**：（聯絡的平均利潤 — 控制組的平均利潤） /聯絡的數量
* **每次聯絡的平均成本**：計算的傳遞成本/聯絡人數量。
* **ROI**：計算的傳遞成本/每個聯絡人的總利潤
* **有效ROI**：計算的傳遞成本/其他利潤。
* **重要性**：包含0到3的值，視促銷活動重要性而定。

### 回應 {#reactions}

您可以透過以下方式檢視收件者對假設的反應 **[!UICONTROL Reactions]** 標籤。

1. 假設計算完成後，請前往 **[!UICONTROL Campaign management > Measurement hypotheses]** Adobe Campaign樹的節點。
1. 選取所需的假設，然後按一下 **[!UICONTROL Reactions]** 索引標籤以檢視行銷活動後可能購買的收件者清單。

   ![](assets/response_hypothesis_reactions_001.png)

## 報告 {#reports}

此 **[!UICONTROL Hypothesis report]** 可讓您檢視對行銷活動和傳遞執行的假設的結果。 此報表包含由假設計算的指標(如需詳細資訊，請參閱 [指標](#indicators))。

* **在行銷活動層級**：按一下 **[!UICONTROL Reports]** 相關行銷活動的連結，並選取 **[!UICONTROL Hypothesis report]**. 此報表包含行銷活動傳遞清單，以及針對每個傳遞計算的假設。

  ![](assets/response_hypothesis_campaign_report_001.png)

* **在傳遞層級**：若要存取報表，請開啟相關傳送，按一下 **[!UICONTROL Reports]** 在 **[!UICONTROL Summary]** 標籤並選取 **[!UICONTROL Hypothesis report]**. 如果針對相同傳遞計算數個假設，報表將包含所有假設。

  ![](assets/response_hypothesis_delivery_report_001.png)
