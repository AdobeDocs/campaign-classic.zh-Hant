---
product: campaign
title: 建立FDA的資料結構
description: 瞭解如何為FDA建立資料結構
feature: Installation, Instance Settings, Federated Data Access
exl-id: 8702499b-1700-4d1f-a0e0-f7a9dfb4b88f
TQID: https://experienceleague.adobe.com/eC7jDm92g943ymcfEQjaeevS7qzIJWJR0zCtnP2Ny7o
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 189
ht-degree: 1%

---

# 建立資料結構描述 {#creating-the-data-schema}



若要在外部資料庫上建立綱要：

1. 按一下資料結構清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，然後選擇&#x200B;**[!UICONTROL Access external data]**。

   ![](assets/wf_new_schema_fda.png)

1. 輸入結構描述的&#x200B;**[!UICONTROL Namespace]**&#x200B;和&#x200B;**[!UICONTROL Name]**，然後選取將啟用資料庫連線的&#x200B;**[!UICONTROL External account]**。 這可讓您存取外部基底中可用的表格清單。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 從&#x200B;**[!UICONTROL Table name]**&#x200B;欄位中，選擇包含要收集之資料的資料表。

   使用Snowflake時，如果資料庫使用者已被授予正確的許可權，您可以在此處選取檢視。 請注意，使用檢視時，Adobe Campaign將無法自動產生XML結構描述，您必須自行建立。 如需檢視的詳細資訊，請參閱[Snowflake檔案](https://docs.snowflake.com/en/user-guide/views-introduction.html)。

   ![](assets/wf_new_schema_select_table_fda.png)

1. 按一下 **[!UICONTROL OK]** 確認。 Adobe Campaign會自動偵測所選表格的結構，並產生邏輯架構。 請注意，Adobe Campaign不會產生連結。

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以確認建立。

   >[!CAUTION]
   >
   >使用Snowflake時，主索引鍵是必要的。

   ![](assets/wf_new_schema_generate_fda.png)

對應表格（標準或FDA對應）時，會自動建立索引。
