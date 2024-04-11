---
product: campaign
title: 模擬範圍
description: 模擬範圍
feature: Interaction, Offers
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 2%

---

# 模擬範圍{#simulation-scope}



## 範圍的定義 {#definition-of-the-scope}

開啟 **[!UICONTROL Scope]** 標籤以選擇您的設定。

下列專案為必要專案：

* 環境或優惠方案類別。
* 優惠方案空間。
* 聯絡日期。 在聯絡日期不符合資格的優惠方案不會納入考量。
* 目標母體。

  如果您未在目標上設定篩選器，則會考慮整個收件者表格。

* 每個目標要模擬的建議數量。

  收件者將收到這麼多建議。 例如，如果您輸入5，則每個收件者最多會收到5個優惠方案主張。

  ![](assets/offer_simulation_009.png)

若要調整要納入模擬考量的優惠方案，您可以新增一或多個主題（在類別中預先指定）。

您也可以選擇對所有優惠方案執行模擬，或僅對線上優惠方案執行模擬。 某些篩選器可讓您變更您想要的選取專案。

>[!NOTE]
>
>您必須指定聯絡日期。 這可讓互動引擎排序所選環境或類別中的優惠方案。 如果未設定日期，模擬將會引發錯誤。

## 新增報告軸 {#adding-reporting-axes}

您可以透過在目標上新增報告軸或選件本身，來增強模擬分析 **[!UICONTROL Calculations]** 標籤。

若要這麼做，請按一下 **[!UICONTROL Add]** 按鈕並選擇適當的欄位。 軸將用於計算模擬，並顯示在分析報告中。 有關詳細資訊，請參閱 [模擬追蹤](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)
