---
solution: Campaign Classic
product: campaign
title: 模擬範圍
description: 模擬範圍
audience: interaction
content-type: reference
topic-tags: simulating-offers
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 2%

---


# 模擬範圍{#simulation-scope}

## 範圍定義 {#definition-of-the-scope}

開啟標 **[!UICONTROL Scope]** 簽以選擇您的設定。

下列項目為必備項目：

* 環境或選件類別。
* 提供空間。
* 聯絡日期。 在聯絡日期不符合資格的選件不會納入考量。
* 目標人口。

   如果您未在目標上設定篩選器，則會考慮整個收件者表格。

* 每個目標要模擬的命題數。

   收件者將會收到許多建議。 例如，如果您輸入5，則每位收件者最多會收到5份優惠方案。

   ![](assets/offer_simulation_009.png)

若要細化要納入模擬的選件，您可以新增一或多個主題（在類別中預先指定）。

您也可以選擇對所有選件或僅對線上選件進行模擬。 有些篩選器可讓您視需要變更選取範圍。

>[!NOTE]
>
>您必須指定聯絡日期。 這可讓互動引擎將選取環境或類別中的選件排序。 如果未設定日期，則模擬會引發錯誤。

## 新增報表軸 {#adding-reporting-axes}

您可以透過標籤在目標或選件本身上新增報告軸，以增強模擬分 **[!UICONTROL Calculations]** 析。

若要這麼做，請按一下按 **[!UICONTROL Add]** 鈕並選擇適當的欄位。 軸將用於計算模擬，並顯示在分析報告中。 For more on this, refer to [Simulation tracking](../../interaction/using/simulation-tracking.md).

![](assets/offer_simulation_011.png)

