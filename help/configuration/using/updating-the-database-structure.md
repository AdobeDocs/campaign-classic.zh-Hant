---
solution: Campaign Classic
product: campaign
title: 更新資料庫結構
description: 更新資料庫結構
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---


# 更新資料庫結構{#updating-the-database-structure}

要對方案應用修改，請啟動資料庫更新嚮導。 此嚮導可通過&#x200B;**[!UICONTROL Tools > Advanced > Update database structure]**&#x200B;訪問。 它檢查資料庫的物理結構是否與其邏輯說明匹配並執行SQL更新指令碼。

![](assets/d_ncs_integration_schema_update.png)

資料庫中的模組會自動填充和激活。

![](assets/d_ncs_integration_schema_update_select.png)

**[!UICONTROL Add stored procedures]**&#x200B;和&#x200B;**[!UICONTROL Import initialization data]**&#x200B;選項用於啟動初始SQL指令碼和建立資料庫時執行的資料包。

您可以從外部資料套件匯入一組資料。 要執行此操作，請選擇&#x200B;**[!UICONTROL Import a package]**&#x200B;並輸入包的XML檔案。

請按照以下步驟查看資料庫更新SQL指令碼：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>這位於編輯欄位中，可加以修改以刪除或新增SQL程式碼。

接下來，啟動資料庫更新：

![](assets/d_ncs_integration_schema_update3.png)

