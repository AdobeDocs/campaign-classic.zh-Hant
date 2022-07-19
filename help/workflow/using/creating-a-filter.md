---
product: campaign
title: 建立篩選器
description: 瞭解如何在執行查詢時建立篩選器
feature: Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# 建立篩選器 {#creating-a-filter}

![](../../assets/v7-only.svg)

在Adobe Campaign可用的篩選器是通過使用與查詢相同的操作模式建立的篩選條件來定義的。

>[!NOTE]
>
>有關建立篩選器的詳細資訊，請參閱 [此部分](../../platform/using/filtering-options.md)。

的 **[!UICONTROL Administration > Configuration > Predefined filters]** 節點包含清單和概述中使用的所有篩選器。

例如，可以按 **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

匹配篩選器包含 **[!UICONTROL Account disabled]** 值 **[!UICONTROL Operators]** 架構：

![](assets/query_editor_filter_sample_2.png)

對於同一清單， **[!UICONTROL By login or label]** filter允許您根據在filter欄位中輸入的值來過濾清單中的資料：

![](assets/query_editor_filter_sample_3.png)

其建立如下：

![](assets/query_editor_filter_sample_4.png)

要匹配篩選條件，運算子帳戶必須檢查以下條件之一：

* 其標籤包含輸入欄位中輸入的字元，
* 運算子名稱包含輸入欄位中輸入的字元，
* 說明區域的內容包含輸入欄位中輸入的字元。

>[!NOTE]
>
>的 **[!UICONTROL Upper]** 函式，可以停用區分大小寫的函式。

的 **[!UICONTROL Taken into account if]** 欄，用於定義這些篩選條件的應用程式條件。 這裡， **$(/tmp/@text)** 字元表示連結到篩選器的輸入欄位的內容：

![](assets/query_editor_filter_sample_5.png)

給， **$(/tmp/@text)=&#39;agency&#39;**

的 **$(/tmp/@text!=&quot;** 當輸入欄位不為空時，表達式將應用每個條件。
