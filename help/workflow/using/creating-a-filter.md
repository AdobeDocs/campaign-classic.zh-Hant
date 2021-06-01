---
product: campaign
title: 建立篩選
description: 了解如何在執行查詢時建立篩選器
audience: workflow
content-type: reference
topic-tags: use-cases
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 2%

---

# 建立篩選 {#creating-a-filter}

Adobe Campaign中可用的篩選器是透過篩選條件來定義，這些篩選條件是使用與查詢相同的作業模式建立。

>[!NOTE]
>
>有關建立篩選器的詳細資訊，請參閱[此區段](../../platform/using/filtering-options.md)。

**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點包含清單和概述中使用的所有篩選器。

例如，運算子清單可依&#x200B;**[!UICONTROL Active accounts]**&#x200B;篩選：

![](assets/query_editor_filter_sample_1.png)

匹配篩選器包含&#x200B;**[!UICONTROL Operators]**&#x200B;架構的&#x200B;**[!UICONTROL Account disabled]**&#x200B;值上的查詢：

![](assets/query_editor_filter_sample_2.png)

對於相同的清單，**[!UICONTROL By login or label]**&#x200B;篩選器允許您根據在篩選欄位中輸入的值篩選清單上的資料：

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

**[!UICONTROL Taken into account if]**&#x200B;欄可讓您定義這些篩選條件的應用程式條件。 此處，**$(/tmp/@text)**&#x200B;字元表示連結到篩選器的輸入欄位的內容：

![](assets/query_editor_filter_sample_5.png)

此處， **$(/tmp/@text)=&#39;agency&#39;**

**$(/tmp/@text)!=&quot;**&#x200B;運算式會在輸入欄位非空白時套用每個條件。
