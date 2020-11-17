---
title: 擴展綱要
description: 瞭解如何擴充架構
page-status-flag: never-activated
uuid: 1767b9de-1d72-4ece-aeec-87f83862d81c
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: editing-schemas
discoiquuid: 1c9af980-4e6b-44dc-af61-dd284863ec7d
translation-type: tm+mt
source-git-commit: 30eaabba8962c518c734cc4e9ad27065cfe9d467
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 5%

---


# 擴展綱要{#extending-a-schema}

>[!IMPORTANT]
>
>某些內建結構不能擴展：主要是已定義下列設定者：\
>**dataSource=&quot;file&quot;** 和 **mappingType=&quot;xmlFile&quot;**。\
>不得擴展以下結構： **x:BackupNew**, **xtk:entityBackupOriginal**, **xorignal,Xoriginal:form**,Xchema:TkXtk,NackPublishingSc:Throg,PublishingShongTTk: **************************************************::userRules,AgentXtk:tk:Xtk連接XtkBlider,XtkBliderXtk連接XtkXbLixbListXkfunc,XtkXtkFusion:tkXtk,Xtk:Xk。jst**, **xxtree:navtree**, **xx:queryDef:** xresource **, xxXresource,XxMenu:XadXThodXadoming:TakXchema:tkTkTkTkXtkXtk:tkxtk**********************。
>這份清單並非完整無遺。

擴展現有模式有兩種方法：

1. 直接修改源模式。
1. 建立具有相同名稱但不同名稱空間的另一個架構。 優點是，您無需修改原始模式即可擴展表。

   架構的根元素必須包含 **extendedSchema** 屬性，其名稱必須擴展為其值。

   擴展模式沒有其自己的模式：源模式生成的模式將填充擴展模式的欄位。

   >[!IMPORTANT]
   >
   >不允許修改應用程式的內置模式，而是模式擴展機制。 否則，修改的架構將不會在應用程式日後升級時更新。 這可能會導致Adobe Campaign的使用失誤。

   **範例**:nms:recipient模式 **的擴展** 。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   在 **nms:recipient** extended架構中填入擴展架構中填入的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   方案 **的根元素上的dependingSchemas** 屬性引用擴展方案上的相關性。

   字 **段上的tersesTo** 屬性會填入宣告該屬性的架構。

>[!IMPORTANT]
>
>要考慮修改，您需要重新生成結構。 For more on this, refer to the [Regenerating schemas](../../configuration/using/regenerating-schemas.md) section.\
>如果修改影響資料庫結構，則需要運行更新。 有關詳細資訊，請參閱[更新資料庫結構](../../configuration/using/updating-the-database-structure.md)區段。

