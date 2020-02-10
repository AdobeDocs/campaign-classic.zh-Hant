---
title: 建立篩選
description: 瞭解如何在執行查詢時建立篩選
page-status-flag: never-activated
uuid: 0556d53e-0fdf-47b3-b1e0-b52e85e0c662
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 7e5605c8-78f2-4011-b317-96a59c699848
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: cf7c90f0ea9fbce3a4fd53f24189617cbd33fc40

---


# 建立篩選 {#creating-a-filter}

Adobe Campaign中可用的篩選條件是透過篩選條件來定義的，篩選條件是使用與查詢相同的作業模式建立的。

>[!NOTE]
>
>For more on creating filters, refer to [this section](../../platform/using/filtering-options.md).

節 **[!UICONTROL Administration > Configuration > Predefined filters]** 點包含清單和概觀中使用的所有篩選器。

例如，運算子清單可依下列方式篩選 **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

匹配篩選器包含對方案 **[!UICONTROL Account disabled]** 值的查 **[!UICONTROL Operators]** 詢：

![](assets/query_editor_filter_sample_2.png)

對於相同的清單，篩選 **[!UICONTROL By login or label]** 器可讓您根據在篩選欄位中輸入的值來篩選清單上的資料：

![](assets/query_editor_filter_sample_3.png)

其建置如下：

![](assets/query_editor_filter_sample_4.png)

若要符合篩選條件，運算子帳戶必須勾選下列其中一個條件：

* 其標籤包含輸入欄位中輸入的字元，
* 運算子名稱包含輸入欄位中輸入的字元，
* 說明區域的內容包含輸入欄位中輸入的字元。

>[!NOTE]
>
>此函 **[!UICONTROL Upper]** 數可讓您停用區分大小寫的函式。

欄可 **[!UICONTROL Taken into account if]** 讓您定義這些篩選條件的應用程式條件。 這裡， **$(/tmp/@text)** 字元代表連結至篩選器的輸入欄位內容：

![](assets/query_editor_filter_sample_5.png)

這裡， **$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;** expression在輸入欄位不空白時套用每個條件。
