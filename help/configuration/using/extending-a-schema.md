---
product: campaign
title: 擴展方案
description: 了解如何擴充結構
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---

# 擴展方案{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>某些內建結構不得延伸：主要是已定義下列設定的：\
>**dataSource=&quot;file&quot;** and  **mappingType=&quot;xmlFile&quot;**。\
>不得擴充下列結構：**xtk:entityBackupNew**、**xtk:entityBackupOriginal**、**xtk:entityOriginal**、**xtk:form**、**xtk:srcSchema**、**ncm:publishing**、**監控：a13/&lt;a4/5/>,** nms:remoteTracking **,** nms:userAgentRules **,** xtk:builder **,** xtk:connections **,** xtk:dbInit **, &lt;a26/:xtk**, **>xtk:fusion**, **xtk:jst**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **&lt;a4:a4/4/>xtk:sqlSchema**, **xtk:strings**。************
>這份清單並非詳盡無遺。

擴充現有結構的方法有兩種：

1. 直接修改源架構。
1. 使用相同名稱但不同命名空間建立其他架構。 其優點是，您無需修改原始架構即可擴展表。

   架構的根元素必須包含&#x200B;**extendedSchema**&#x200B;屬性，並且要擴展的架構的名稱為其值。

   擴充功能結構沒有其專屬的結構：從來源架構產生的架構將會填入擴充功能架構的欄位。

   >[!IMPORTANT]
   >
   >您不能修改應用程式的內建架構，而不能修改架構擴展機制。 否則，在將來升級應用程式時，修改的架構將不會更新。 這可能導致使用Adobe Campaign時發生故障。

   **範例**:nms: **recipientschema的** 擴充功能。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   **nms:recipient**&#x200B;擴展方案中填充了擴展方案中填充的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   架構的根元素上的&#x200B;**dependingSchemas**&#x200B;屬性會參考擴充功能架構的相依性。

   欄位上的&#x200B;**lecessTo**&#x200B;屬性會填入宣告該屬性的架構。

>[!IMPORTANT]
>
>若要考慮修改，您需要重新產生結構。 有關詳細資訊，請參閱[重新生成結構](../../configuration/using/regenerating-schemas.md)部分。\
>如果修改影響資料庫的結構，則需要運行更新。 有關詳細資訊，請參閱[更新資料庫結構](../../configuration/using/updating-the-database-structure.md)區段。
