---
product: campaign
title: 建立篩選器
description: 瞭解如何在執行查詢時建立篩選器
feature: Query Editor, Workflows
exl-id: 297ea1e1-39ef-4b99-aaaa-9e88611fb1bf
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 2%

---

# 建立篩選器 {#creating-a-filter}



Adobe Campaign中可用的篩選器是透過篩選條件來定義，這些條件是使用與查詢相同的作業模式建立的。

>[!NOTE]
>
>如需建立篩選的詳細資訊，請參閱[本節](../../platform/using/filtering-options.md)。

**[!UICONTROL Administration > Configuration > Predefined filters]**&#x200B;節點包含清單和概覽中使用的所有篩選器。

例如，運運算元清單可由&#x200B;**[!UICONTROL Active accounts]**&#x200B;篩選：

![](assets/query_editor_filter_sample_1.png)

符合的篩選器包含對&#x200B;**[!UICONTROL Operators]**&#x200B;結構描述的&#x200B;**[!UICONTROL Account disabled]**&#x200B;值的查詢：

![](assets/query_editor_filter_sample_2.png)

對於相同的清單，**[!UICONTROL By login or label]**&#x200B;篩選器可讓您根據在篩選器欄位中輸入的值來篩選清單上的資料：

![](assets/query_editor_filter_sample_3.png)

其建置方式如下：

![](assets/query_editor_filter_sample_4.png)

若要符合篩選條件，運運算元帳戶必須勾選下列其中一個條件：

* 其標籤包含在輸入欄位中輸入的字元，
* 運運算元名稱包含輸入欄位中所輸入的字元。
* 說明區域的內容包含在輸入欄位中輸入的字元。

>[!NOTE]
>
>**[!UICONTROL Upper]**&#x200B;函式可讓您停用區分大小寫的函式。

**[!UICONTROL Taken into account if]**&#x200B;欄可讓您定義這些篩選條件的應用程式條件。 在此，**$(/tmp/@text)**&#x200B;字元代表連結至篩選的輸入欄位內容：

![](assets/query_editor_filter_sample_5.png)

在這裡，**$(/tmp/@text)=&#39;機構&#39;**

**$(/tmp/@text)！=&quot;**&#x200B;運算式會在輸入欄位非空白時套用每個條件。
