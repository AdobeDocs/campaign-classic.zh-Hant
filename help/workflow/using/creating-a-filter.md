---
solution: Campaign Classic
product: campaign
title: 建立篩選
description: 瞭解如何在執行查詢時建立篩選
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---


# 建立篩選 {#creating-a-filter}

Adobe Campaign中可用的篩選條件是透過篩選條件來定義的，篩選條件是使用與查詢相同的作業模式建立的。

>[!NOTE]
>
>有關建立篩選器的詳細資訊，請參閱[本節](../../platform/using/filtering-options.md)。

**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點包含清單和概述中使用的所有篩選器。

例如，運算子清單可依&#x200B;**[!UICONTROL Active accounts]**&#x200B;篩選：

![](assets/query_editor_filter_sample_1.png)

匹配篩選器包含&#x200B;**[!UICONTROL Operators]**&#x200B;方案&#x200B;**[!UICONTROL Account disabled]**&#x200B;值的查詢：

![](assets/query_editor_filter_sample_2.png)

對於相同的清單，**[!UICONTROL By login or label]**&#x200B;篩選器可讓您根據在篩選欄位中輸入的值來篩選清單上的資料：

![](assets/query_editor_filter_sample_3.png)

其建置如下：

![](assets/query_editor_filter_sample_4.png)

若要符合篩選條件，運算子帳戶必須勾選下列其中一個條件：

* 其標籤包含輸入欄位中輸入的字元，
* 運算子名稱包含輸入欄位中輸入的字元，
* 說明區域的內容包含輸入欄位中輸入的字元。

>[!NOTE]
>
>**[!UICONTROL Upper]**&#x200B;函式可讓您停用區分大小寫的函式。

**[!UICONTROL Taken into account if]**&#x200B;欄可讓您定義這些篩選條件的應用程式條件。 這裡，**$(/tmp/@text)**&#x200B;字元代表連結至篩選器的輸入欄位內容：

![](assets/query_editor_filter_sample_5.png)

這裡，**$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;**&#x200B;運算式會在輸入欄位不空白時套用每個條件。
