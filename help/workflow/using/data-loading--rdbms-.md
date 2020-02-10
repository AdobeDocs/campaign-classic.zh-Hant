---
title: 資料載入(RDBMS)
seo-title: 資料載入(RDBMS)
description: 資料載入(RDBMS)
seo-description: null
page-status-flag: never-activated
uuid: d5ec30f2-398a-4b16-9232-924437da146a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: a128caac-5740-4dac-b14d-1d2fcef3cc69
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 資料載入(RDBMS){#data-loading-rdbms}

此活 **[!UICONTROL Data loading (RDBMS)]** 動可讓您直接存取此外部資料庫，並僅收集定位所需的資料。

為改善效能，建議使用查詢活動（可使用外部資料庫的資料）。 有關詳細資訊，請參 [閱訪問外部資料庫(FDA)](../../workflow/using/accessing-an-external-database--fda-.md)。

操作如下：

1. 從清單中選擇資料源，然後輸入包含要提取資料的表的名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相應欄位中輸入的表的名稱用作在外部資料庫中收集資料的模板。 通過資料載入活動的入站過渡可以計算或傳送由工作流處理的表的名稱。 要選擇要使用的表，請按一下 **[!UICONTROL Advanced..]**。 連結並選取 **[!UICONTROL Specified in the transition]** 或選 **[!UICONTROL Explicit]** 項。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下該 **[!UICONTROL Select the columns to extract...]** 連結以選擇要在資料庫中收集的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 您可以定義此資料的篩選。 若要這麼做，請按一下 **[!UICONTROL Edit query....]** 連結。

   這樣收集的資料可在整個工作流程的生命週期中使用。

