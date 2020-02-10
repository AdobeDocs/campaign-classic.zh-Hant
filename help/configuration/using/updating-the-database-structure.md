---
title: 更新資料庫結構
seo-title: 更新資料庫結構
description: 更新資料庫結構
seo-description: null
page-status-flag: never-activated
uuid: 084dcc7b-f890-4dff-a322-c9a8f1d614b8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: b82ae459-30b5-4a1c-91cc-5c7b8f128333
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 更新資料庫結構{#updating-the-database-structure}

要對方案應用修改，請啟動資料庫更新嚮導。 此精靈可透過 **[!UICONTROL Tools > Advanced > Update database structure]** 。 它檢查資料庫的物理結構是否與其邏輯說明匹配並執行SQL更新指令碼。

![](assets/d_ncs_integration_schema_update.png)

資料庫中的模組會自動填充和激活。

![](assets/d_ncs_integration_schema_update_select.png)

和 **[!UICONTROL Add stored procedures]** 選 **[!UICONTROL Import initialization data]** 項用於啟動初始SQL指令碼和建立資料庫時執行的資料包。

您可以從外部資料套件匯入一組資料。 要執行此操作，請選 **[!UICONTROL Import a package]** 擇並輸入包的XML檔案。

請按照以下步驟查看資料庫更新SQL指令碼：

![](assets/d_ncs_integration_schema_update2.png)

>[!NOTE]
>
>這位於編輯欄位中，可加以修改以刪除或新增SQL程式碼。

接下來，啟動資料庫更新：

![](assets/d_ncs_integration_schema_update3.png)

