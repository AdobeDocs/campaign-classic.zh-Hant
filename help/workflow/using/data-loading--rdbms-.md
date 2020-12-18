---
solution: Campaign Classic
product: campaign
title: 資料載入 (RDBMS)
description: 進一步瞭解資料載入(RDBMS)工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---


# 資料載入 (RDBMS){#data-loading-rdbms}

**[!UICONTROL Data loading (RDBMS)]**&#x200B;活動可讓您直接存取此外部資料庫，並僅收集定位所需的資料。

為改善效能，建議使用查詢活動（可使用外部資料庫的資料）。 有關詳細資訊，請參閱[訪問外部資料庫(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。

操作如下：

1. 從清單中選擇資料源，然後輸入包含要提取資料的表的名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相應欄位中輸入的表的名稱用作在外部資料庫中收集資料的模板。 通過資料載入活動的入站過渡可以計算或傳送由工作流處理的表的名稱。 要選擇要使用的表，請按一下&#x200B;**[!UICONTROL Advanced..]**。 link並選擇&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;或&#x200B;**[!UICONTROL Explicit]**&#x200B;選項。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下&#x200B;**[!UICONTROL Select the columns to extract...]**&#x200B;連結以選擇要在資料庫中收集的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以定義此資料的篩選。 若要這麼做，請按一下&#x200B;**[!UICONTROL Edit query....]**&#x200B;連結。

   這樣收集的資料可在整個工作流程的生命週期中使用。

