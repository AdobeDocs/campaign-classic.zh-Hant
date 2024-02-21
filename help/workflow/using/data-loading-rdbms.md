---
product: campaign
title: 資料載入 (RDBMS)
description: 深入瞭解資料載入(RDBMS)工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 6%

---

# 資料載入 (RDBMS){#data-loading-rdbms}



此 **[!UICONTROL Data loading (RDBMS)]** 活動可讓您直接存取此外部資料庫，並僅收集定位所需的資料。

若要改善效能，我們建議使用查詢活動（可在其中使用外部資料庫的資料）。 有關詳細資訊，請參閱 [存取外部資料庫(FDA)](accessing-an-external-database-fda.md).

操作如下：

1. 從清單中選取資料來源，然後輸入包含要擷取之資料的表格名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在對應欄位中輸入的表格名稱會作為範本使用，以便在外部資料庫中收集資料。 工作流程處理的表格名稱，可由資料載入活動的入站轉變計算或傳送。 若要選取要使用的表格，請按一下 **[!UICONTROL Advanced..]**. 連結並選取 **[!UICONTROL Specified in the transition]** 或 **[!UICONTROL Explicit]** 選項。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下 **[!UICONTROL Select the columns to extract...]** 此連結可選擇要收集到資料庫中的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以在此資料上定義篩選器。 若要這麼做，請按一下 **[!UICONTROL Edit query....]** 連結。

   如此收集的資料可在整個工作流程生命週期中使用。
