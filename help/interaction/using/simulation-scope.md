---
product: campaign
title: 模擬範圍
description: 模擬範圍
audience: interaction
content-type: reference
topic-tags: simulating-offers
exl-id: 4f6b3de2-3fdf-441d-925d-476e20e75c6f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---

# 模擬範圍{#simulation-scope}

![](../../assets/v7-only.svg)

## 範圍的定義 {#definition-of-the-scope}

開啟&#x200B;**[!UICONTROL Scope]**&#x200B;標籤以選擇您的設定。

以下是必填項目：

* 環境或選件類別。
* 優惠方案空間。
* 聯繫日期。 在聯絡日期不符合資格的優惠方案則不會納入考量。
* 目標人口。

   如果您未在目標上設定篩選器，則會考慮整個收件者表格。

* 每個目標要模擬的命題數。

   接收方將收到許多建議。 例如，如果您輸入5，則每個收件者最多會收到5個優惠方案建議。

   ![](assets/offer_simulation_009.png)

若要精簡要納入模擬的選件，您可以新增一或多個主題（在類別中預先指定）。

您也可以選擇對所有選件或只對線上選件進行模擬。 有些篩選條件可讓您變更選取項目。

>[!NOTE]
>
>必須指定聯繫日期。 這可讓互動引擎對所選環境或類別中的選件進行排序。 如果未設定任何日期，則模擬會引發錯誤。

## 新增報表軸 {#adding-reporting-axes}

您可以透過&#x200B;**[!UICONTROL Calculations]**&#x200B;標籤在目標或選件本身上新增報表軸，以增強模擬分析。

要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並選擇相應欄位。 軸將用於計算模擬，並顯示在分析報告中。 如需詳細資訊，請參閱[模擬追蹤](../../interaction/using/simulation-tracking.md)。

![](assets/offer_simulation_011.png)
