---
product: campaign
title: 建立FDA的資料結構
description: 瞭解如何為FDA建立資料結構
feature: Installation, Instance Settings, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 3%

---

# 建立資料結構描述 {#creating-the-data-schema}



若要在外部資料庫上建立綱要：

1. 按一下 **[!UICONTROL New]** 按鈕並選擇資料結構描述 **[!UICONTROL Access external data]**.

   ![](assets/wf_new_schema_fda.png)

1. 輸入 **[!UICONTROL Namespace]** 和  **[!UICONTROL Name]** ，並選取 **[!UICONTROL External account]** 這會啟用與資料庫的連線。 這可讓您存取外部基底中可用的表格清單。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 從 **[!UICONTROL Table name]** 欄位，選擇包含要收集之資料的表格。

   如果資料庫使用者已被授予正確的許可權，您可以使用Snowflake在此選取檢視。 請注意，使用檢視時，Adobe Campaign將無法自動產生XML結構描述，您必須自行建立。 有關檢視的詳細資訊，請參閱 [Snowflake檔案](https://docs.snowflake.com/en/user-guide/views-introduction.html).

   ![](assets/wf_new_schema_select_table_fda.png)

1. 按一下 **[!UICONTROL OK]** 以確認。 Adobe Campaign會自動偵測所選表格的結構，並產生邏輯架構。 請注意，Adobe Campaign不會產生連結。

1. 按一下 **[!UICONTROL Save]** 以確認建立。

   >[!CAUTION]
   >
   >若使用Snowflake，主索引鍵是必要的。

   ![](assets/wf_new_schema_generate_fda.png)

對應表格（標準或FDA對應）時，會自動建立索引。
