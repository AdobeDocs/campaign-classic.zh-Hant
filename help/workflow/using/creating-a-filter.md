---
product: campaign
title: 建立篩選器
description: 了解如何在執行查詢時建立篩選器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Query Editor, Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# 建立篩選器 {#creating-a-filter}



Adobe Campaign中可用的篩選器是透過篩選條件來定義，這些篩選條件是使用與查詢相同的作業模式建立。

>[!NOTE]
>
>如需建立篩選器的詳細資訊，請參閱 [本節](../../platform/using/filtering-options.md).

此 **[!UICONTROL Administration > Configuration > Predefined filters]** 節點包含清單和概述中使用的所有篩選器。

例如，運算子清單可依 **[!UICONTROL Active accounts]**:

![](assets/query_editor_filter_sample_1.png)

相符的篩選器包含 **[!UICONTROL Account disabled]** 值 **[!UICONTROL Operators]** 方案：

![](assets/query_editor_filter_sample_2.png)

若為同一份清單， **[!UICONTROL By login or label]** 篩選器可讓您根據在篩選欄位中輸入的值來篩選清單上的資料：

![](assets/query_editor_filter_sample_3.png)

其建置如下：

![](assets/query_editor_filter_sample_4.png)

若要符合篩選條件，運算子帳戶必須勾選下列其中一個條件：

* 其標籤包含輸入欄位中輸入的字元，
* 運算子名稱包含輸入欄位中輸入的字元，
* 說明區域的內容包含輸入欄位中輸入的字元。

>[!NOTE]
>
>此 **[!UICONTROL Upper]** 函式可讓您停用區分大小寫的函式。

此 **[!UICONTROL Taken into account if]** 欄可讓您定義這些篩選條件的應用程式條件。 這裡， **$(/tmp/@text)** 字元代表連結至篩選器的輸入欄位內容：

![](assets/query_editor_filter_sample_5.png)

這裡， **$(/tmp/@text)=&#39;agency&#39;**

此 **$(/tmp/@text)!=&quot;** 輸入欄位非空白時，運算式會套用每個條件。
