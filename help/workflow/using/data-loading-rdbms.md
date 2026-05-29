---
product: campaign
title: 資料載入 (RDBMS)
description: 深入瞭解資料載入(RDBMS)工作流程活動
feature: Workflows, Data Management Activity
hide: true
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
TQID: https://experienceleague.adobe.com/w7MFQZpUw-a0SIp634sptKz2VKm2MTZisjmN3VLDt2g
product_v2: id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a658c786-869b-4194-a780-2594d663adda
topic_v2: id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
subfeature_v2: id: ee25c34b-ea50-427b-9369-ba0a160f7d70id: b5f0aaf4-1e48-400d-95ac-6eb3078cf22fid: d1110311-2ca4-442b-be37-088a6db845ee
source-git-commit: 38eab6b8da73163e4476e91c0ef73f25c3f57546
workflow-type: tm+mt
source-wordcount: 187
ht-degree: 3%

---

# 資料載入 (RDBMS){#data-loading-rdbms}



**[!UICONTROL Data loading (RDBMS)]**&#x200B;活動可讓您直接存取此外部資料庫，並僅收集定位所需的資料。

若要改善效能，我們建議使用查詢活動（可在其中使用外部資料庫的資料）。 如需詳細資訊，請參閱[存取外部資料庫(FDA)](accessing-an-external-database-fda.md)。

操作如下：

1. 從清單中選取資料來源，然後輸入包含要擷取之資料的表格名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在對應欄位中輸入的表格名稱會作為範本使用，以便在外部資料庫中收集資料。 工作流程處理的表格名稱，可由資料載入活動的入站轉變計算或傳送。 若要選取要使用的資料表，請按一下&#x200B;**[!UICONTROL Advanced..]**。 連結並選取&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;或&#x200B;**[!UICONTROL Explicit]**&#x200B;選項。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下&#x200B;**[!UICONTROL Select the columns to extract...]**&#x200B;連結以選擇要收集到資料庫中的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以在此資料上定義篩選器。 若要這麼做，請按一下&#x200B;**[!UICONTROL Edit query....]**&#x200B;連結。

   如此收集的資料可在整個工作流程生命週期中使用。
