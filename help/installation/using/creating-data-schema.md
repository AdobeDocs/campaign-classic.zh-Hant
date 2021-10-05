---
product: campaign
title: 存取外部資料庫
description: 存取外部資料庫
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: d2d0ff575edbee18febb5ec895fcec1e0ae34de7
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 6%

---

# 建立資料結構綱要 {#creating-the-data-schema}

![](../../assets/v7-only.svg)

要在外部資料庫上建立架構：

1. 按一下資料架構清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 為架構輸入&#x200B;**[!UICONTROL Namespace]**&#x200B;和&#x200B;**[!UICONTROL Name]**，並選擇&#x200B;**[!UICONTROL External account]**，以啟用與資料庫的連接。 這允許訪問外部資料庫中可用的表清單。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 從&#x200B;**[!UICONTROL Table name]**&#x200B;欄位中，選擇包含要收集的資料的表。

   使用Snowflake，如果資料庫用戶已獲得正確權限，則可以在此處選擇視圖。 請注意，使用檢視時，Adobe Campaign無法自動產生XML架構，您必須自行建立。 如需檢視的詳細資訊，請參閱[Snowflake檔案](https://docs.snowflake.com/en/user-guide/views-introduction.html)。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 按一下&#x200B;**[!UICONTROL OK]**&#x200B;以確認。 Adobe Campaign會自動偵測所選表格的結構，並產生邏輯架構。 請注意，Adobe Campaign不會產生連結。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以確認建立。

   >[!CAUTION]
   >
   >使用Snowflake時，主鍵為必填。

   ![](assets/wf_new_schema_generate_fda.png)

對應表格（標準或FDA對應）時會自動建立索引。
