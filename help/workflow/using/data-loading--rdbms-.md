---
product: campaign
title: 資料載入 (RDBMS)
description: 瞭解有關資料載入(RDBMS)工作流活動的詳細資訊
feature: Workflows, Data Management Activity
exl-id: 6e24d5fe-4830-49b4-a0fe-624c5644c920
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 3%

---

# 資料載入 (RDBMS){#data-loading-rdbms}

![](../../assets/v7-only.svg)

的 **[!UICONTROL Data loading (RDBMS)]** 活動允許您直接訪問此外部資料庫，並僅收集目標所需的資料。

為了提高效能，我們建議使用查詢活動（其中可以使用外部資料庫的資料）。 有關此內容的詳細資訊，請參閱 [訪問外部資料庫(FDA)](accessing-an-external-database--fda-.md)。

操作如下：

1. 從清單中選擇資料源，然後輸入包含要提取的資料的表的名稱。

   ![](assets/s_advuser_wf_sgbd_sample_1.png)

   在相應欄位中輸入的表的名稱用作收集外部資料庫中資料的模板。 通過資料載入活動的入站轉換可以計算或傳送由工作流處理的表的名稱。 要選擇要使用的表，請按一下 **[!UICONTROL Advanced..]**。 連結並選擇 **[!UICONTROL Specified in the transition]** 或 **[!UICONTROL Explicit]** 的雙曲餘切值。

   ![](assets/s_advuser_wf_sgbd_sample_5.png)

1. 按一下 **[!UICONTROL Select the columns to extract...]** 連結，以選擇要在資料庫中收集的資料。

   ![](assets/s_advuser_wf_sgbd_sample_2.png)

1. 可以定義此資料的篩選器。 要執行此操作，請按一下 **[!UICONTROL Edit query....]** 的子菜單。

   這樣收集的資料可以在工作流的整個生命週期中使用。
