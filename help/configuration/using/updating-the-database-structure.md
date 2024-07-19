---
product: campaign
title: 更新資料庫結構
description: 更新資料庫結構
feature: Configuration
role: Data Engineer, Developer
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# 更新資料庫結構{#updating-the-database-structure}



若要套用對結構描述所做的修改，請啟動資料庫更新精靈。 此精靈可透過&#x200B;**[!UICONTROL Tools > Advanced > Update database structure]**&#x200B;存取。 它會檢查資料庫的實體結構是否符合其邏輯描述，並執行SQL更新指令碼。

![](assets/d_ncs_integration_schema_update.png)

資料庫中的模組會自動填入並啟動。

![](assets/d_ncs_integration_schema_update_select.png)

**[!UICONTROL Add stored procedures]**&#x200B;和&#x200B;**[!UICONTROL Import initialization data]**&#x200B;選項是用來啟動初始SQL指令碼以及建立資料庫時執行的資料套件。

您可以從外部資料包匯入一組資料。 若要這麼做，請選取&#x200B;**[!UICONTROL Import a package]**&#x200B;並輸入封裝的XML檔案。

請依照下列步驟操作，並檢視資料庫更新SQL指令碼：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>這是編輯欄位，可以修改以刪除或新增SQL程式碼。

接下來，啟動資料庫更新：

![](assets/d_ncs_integration_schema_update3.png)
