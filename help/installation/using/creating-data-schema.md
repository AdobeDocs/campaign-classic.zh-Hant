---
solution: Campaign Classic
product: campaign
title: 存取外部資料庫
description: 存取外部資料庫
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 9%

---


# 建立資料結構綱要 {#creating-the-data-schema}

要在外部資料庫上建立模式：

1. 按一下資料方案清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 輸入方案的名稱和說明，然後選擇將啟用與資料庫連接的外部帳戶。 這允許訪問外部基礎中可用的表清單。 選擇包含要收集之資料的表格。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;進行確認。 Adobe Campaign會自動偵測選取表格的結構並產生邏輯架構。 請注意，Adobe Campaign不會產生連結。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;確認建立。

   >[!CAUTION]
   >
   >有了雪花，主鍵是必備的。

   ![](assets/wf_new_schema_generate_fda.png)

在映射表（標準或FDA映射）時，會自動建立索引。
