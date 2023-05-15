---
product: campaign
title: 資料載入 (RDBMS)
description: 進一步了解資料載入(RDBMS)工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# 資料載入 (RDBMS){#data-loading-rdbms}



此 **[!UICONTROL Data loading (RDBMS)]** 活動可讓您直接存取此外部資料庫，並僅收集鎖定目標所需的資料。

為了改善效能，建議使用查詢活動（可使用外部資料庫的資料）。 有關詳細資訊，請參閱 [存取外部資料庫(FDA)](accessing-an-external-database--fda-.md).

操作如下：

1. 從清單中選擇資料源，並輸入包含要提取的資料的表的名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相應欄位中輸入的表的名稱用作在外部資料庫中收集資料的模板。 通過資料載入活動的入站轉變，可以計算或傳送由工作流處理的表的名稱。 若要選取要使用的表格，請按一下 **[!UICONTROL Advanced..]**. 連結，然後選取 **[!UICONTROL Specified in the transition]** 或 **[!UICONTROL Explicit]** 選項。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下 **[!UICONTROL Select the columns to extract...]** 連結以選擇要在資料庫中收集的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以對此資料定義篩選。 若要這麼做，請按一下 **[!UICONTROL Edit query....]** 連結。

   像這樣收集的資料可在工作流程的整個生命週期中使用。
