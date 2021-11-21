---
product: campaign
title: 更新資料庫結構
description: 更新資料庫結構
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6c1e061b-8636-4285-8d83-97474544d252
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 8%

---

# 更新資料庫結構{#updating-the-database-structure}

![](../../assets/v7-only.svg)

若要將修改套用至結構，請啟動資料庫更新精靈。 此精靈可透過 **[!UICONTROL Tools > Advanced > Update database structure]** . 它檢查資料庫的物理結構是否與其邏輯描述匹配，並執行SQL更新指令碼。

![](assets/d_ncs_integration_schema_update.png)

資料庫中的模組會自動填入並啟動。

![](assets/d_ncs_integration_schema_update_select.png)

此 **[!UICONTROL Add stored procedures]** 和 **[!UICONTROL Import initialization data]** 選項用於啟動初始SQL指令碼和建立資料庫時執行的資料包。

您可以從外部資料包導入一組資料。 要執行此操作，請選取 **[!UICONTROL Import a package]** 並輸入包的XML檔案。

請按照以下步驟查看資料庫更新SQL指令碼：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>這位於編輯欄位中，可以修改以刪除或新增SQL程式碼。

接下來，啟動資料庫更新：

![](assets/d_ncs_integration_schema_update3.png)
