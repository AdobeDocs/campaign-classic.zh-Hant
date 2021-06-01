---
product: campaign
title: 資料載入 (RDBMS)
description: 進一步了解資料載入(RDBMS)工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# 資料載入 (RDBMS){#data-loading-rdbms}

**[!UICONTROL Data loading (RDBMS)]**&#x200B;活動可讓您直接存取此外部資料庫，並僅收集鎖定目標所需的資料。

為了改善效能，建議使用查詢活動（可使用外部資料庫的資料）。 有關詳細資訊，請參閱[存取外部資料庫(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。

操作如下：

1. 從清單中選擇資料源，並輸入包含要提取的資料的表的名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相應欄位中輸入的表的名稱用作在外部資料庫中收集資料的模板。 通過資料載入活動的入站轉變，可以計算或傳送由工作流處理的表的名稱。 要選擇要使用的表，請按一下&#x200B;**[!UICONTROL Advanced..]**。 連結並選取&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;或&#x200B;**[!UICONTROL Explicit]**&#x200B;選項。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下&#x200B;**[!UICONTROL Select the columns to extract...]**&#x200B;連結以選擇要在資料庫中收集的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以對此資料定義篩選。 要執行此操作，請按一下&#x200B;**[!UICONTROL Edit query....]**&#x200B;連結。

   像這樣收集的資料可在工作流程的整個生命週期中使用。
