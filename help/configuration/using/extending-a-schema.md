---
solution: Campaign Classic
product: campaign
title: 擴展綱要
description: 瞭解如何擴充架構
audience: configuration
content-type: reference
topic-tags: editing-schemas
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# 擴展綱要{#extending-a-schema}

>[!IMPORTANT]
>
>某些內建結構不能擴展：主要是已定義下列設定者：\
>**dataSource=&quot;file&quot;** and  **mappingType=&quot;xmlFile&quot;**。\
>不得擴展以下結構：**xtk:entityBackupNew**、**xtk:entityBackupOriginal**、**xtk:entityOriginal**、**xtk:form**、**xtk:srcSchema**、&lt;a10>ncm:publishing **、** nl:monitoring **、** nms:calendar **、** nms:remoteTracking **、** nms:userAgentRules **、** xtk:builder **、** xtk:connections **、** xtk:dbInit **、** xtk:funcList **、** xtk:fusion **,** xtk:jst **、** xtk:navtree **、** xtk:queryDef **、** xtk:resourceMenu **、** xtk:schema **、** xtk:scriptContext **、** xtk:session **、** xtk:sqlSchema **、** xtk:strings **。**
>這份清單並非完整無遺。

擴展現有模式有兩種方法：

1. 直接修改源模式。
1. 建立具有相同名稱但不同名稱空間的另一個架構。 優點是，您無需修改原始模式即可擴展表。

   架構的根元素必須包含&#x200B;**extendedSchema**&#x200B;屬性，其名稱必須擴展為其值。

   擴展模式沒有其自己的模式：源模式生成的模式將填充擴展模式的欄位。

   >[!IMPORTANT]
   >
   >不允許修改應用程式的內置模式，而是模式擴展機制。 否則，修改的架構將不會在應用程式日後升級時更新。 這可能會導致Adobe Campaign的使用失誤。

   **範例**:nms：收件 **方式的** 擴展。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   **nms:recipient**&#x200B;擴展模式中填充了擴展模式中填充的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   方案的根元素上的&#x200B;**dependingSchemas**&#x200B;屬性引用擴展方案的相關性。

   欄位上的&#x200B;**terspersTo**&#x200B;屬性填充聲明該屬性的架構。

>[!IMPORTANT]
>
>要考慮修改，您需要重新生成結構。 有關詳細資訊，請參閱[重新生成方案](../../configuration/using/regenerating-schemas.md)部分。\
>如果修改影響資料庫結構，則需要運行更新。 有關詳細資訊，請參閱[更新資料庫結構](../../configuration/using/updating-the-database-structure.md)區段。

