---
title: 排除
seo-title: 排除
description: 排除
seo-description: null
page-status-flag: never-activated
uuid: e4f54a0b-2fec-4415-986b-83c8928ed174
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: acab51f3-686b-4d2b-bb02-8fbfae36b1ba
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: ffee73b949a77343eaf23d0fb9a58a4283f4f87a
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 1%

---


# 排除{#exclusion}

排除 **類型活動**，根據從中提取一個或多個其他目標的主目標建立目標。

要配置此活動，請輸入其標籤並選擇主收件者集： 來自主集的人口族群可讓您建構結果。 將排除由主集和至少一個條目活動共用的配置檔案。

![](assets/s_user_segmentation_exclu.png)

>[!NOTE]
>
>如需設定和使用排除活動的詳細資訊，請參 [閱排除人口（排除）](../../workflow/using/targeting-data.md#excluding-a-population--exclusion-)。

如果您 **[!UICONTROL Generate complement]** 想利用剩餘人口，請勾選選項。 補充內容將包括主要的外來人口減去即將外來的人口。 然後，活動中將添加一個附加的輸出轉換，如下所示：

![](assets/s_user_segmentation_exclu_compl.png)

## 排除範例 {#exclusion-examples}

以下範例旨在匯編一份18至30歲的受助者名單，但不包括巴黎居民。

1. 插入並開啟 **[!UICONTROL Exclusion]** -type活動（在兩個查詢後）。 第一個查詢會針對居住在巴黎的收件者。 第二個查詢的目標年齡為18到30歲。
1. 輸入主集。 這裡的主集是 **18-30年前的查詢** 。 與第二組相關的元素將從最終結果中排除。
1. 如果您 **[!UICONTROL Generate complement]** 想要利用排除後仍保留的資料，請勾選此選項。 在這種情況下，補充是由居住在巴黎的18至30歲的受助者組成。
1. 批准排除設定，然後將更新清單活動插入結果。 您也可以視需要，將其他清單更新插入補充內容。
1. 執行工作流程。 在本例中，結果由18至30歲的受助者組成，但居住在巴黎的受助者被排除在外，並被送到補充品中。

   ![](assets/exclusion_example.png)

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這組三個值識別排除所產生的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補體相關的過渡具有相同的參數。
