---
title: 交集
seo-title: 交集
description: 交集
seo-description: null
page-status-flag: never-activated
uuid: a8ff7a66-6c12-4e3c-ad45-d11b34ca64ff
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: d0dd9c74-aad5-452e-a11d-c231dacd2aec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 交集{#intersection}

Intersection ****-type活動會從接收的目標的交叉點建立目標。

交叉點可讓您只擷取所有傳入活動結果的共同人口。 目標建立時會收到所有結果：因此，在執行交叉點之前，必須完成所有先前活動。 要配置此活動，您需要為其輸入標籤以及與結果相關的選項。

![](assets/s_user_segmentation_inter.png)

有關配置和使用交叉點活動的詳細資訊，請參 [閱提取聯合資料（交叉點）](../../workflow/using/targeting-data.md#extracting-joint-data--intersection-)。

如果 **[!UICONTROL Generate complement]** 要處理剩餘人口，請選中該選項。 補語將包含所有傳入活動結果的並減去交叉點。 然後，活動中將添加一個額外的出站轉移，如下所示：

![](assets/s_user_segmentation_inter_compl.png)

## 交叉點示例 {#intersection-example}

在下列範例中，交集的目的是計算三個簡單查詢的常用收件者，以建立清單。

1. 在三個簡單查詢後，插入 **[!UICONTROL Intersection]** -type活動。

   在本例中，這些詢問分別針對男性、生活在巴黎的收件者和18至30歲的收件者。

1. 設定交叉點。 要執行此操作，請選擇協調方 **[!UICONTROL Keys only]** 法，因為由查詢產生的總體包含一致的資料。
1. 如果您已為查詢輸入其他資料，您可以選取相關方塊，選擇只保留由收件者共用的資料。
1. 如果希望使用其餘的資料（關於查詢，但不涉及其交集），請選中該 **[!UICONTROL Generate complement]** 框。
1. 在交叉點結果之後添加清單更新活動。 您也可以將清單更新新增至您想要使用的輔助項目。
1. 執行工作流程。 在這裡，兩個收件者同時套用至所有三個輸入的查詢。 補碼由5個收件者組成，他們只適用於3個查詢中的一或兩個。

   交集結果會傳送至第一個清單更新。 如果您選擇使用補充字，則也會傳送至第二個清單更新。

   ![](assets/intersection_example.png)

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這組三個值用於標識由交叉點生成的目標。 **[!UICONTROL tableName]** 是記錄目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式(通常 **[!UICONTROL nms:recipient]**) **[!UICONTROL recCount]** ，是表中的元素數。
