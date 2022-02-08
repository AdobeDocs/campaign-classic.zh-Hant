---
product: campaign
title: 擴展架構
description: 瞭解如何擴展架構
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# 擴展架構{#extending-a-schema}

![](../../assets/v7-only.svg)

>[!IMPORTANT]
>
>某些內置架構不能擴展：主要是定義了以下設定的：\
>**dataSource=&quot;檔案&quot;** 和 **mappingType=&quot;xmlFile&quot;**。\
>不能擴展以下架構： **xtk:entityBackupNew**。 **xtk:entityBackupOriginal**。 **xtk：實體原始**。 **xtk：格式**。 **xtk:srcSchema**。 **ncm：發佈**。 **nl：監視**。 **nms：日曆**。 **nms:remoteTracking**。 **nms:userAgentRules**。 **xtk：生成器**。 **xtk：連接**。 **xtk:dbInit**。 **xtk:funcList**。 **xtk：融合**。 **xtk:只**。 **xtk：導航樹**。 **xtk:queryDef**。 **xtk：資源菜單**。 **xtk：架構**。 **xtk：指令碼上下文**。 **xtk：會話**。 **xtk:sqlSchema**。 **xtk：字串**。
>這份清單並非詳盡無遺。

擴展現有模式有兩種方法：

1. 直接修改源架構。
1. 建立具有相同名稱但不同命名空間的另一架構。 優點是可以擴展表，而無需修改原始架構。

   架構的根元素必須包含 **擴展架構** 將要擴展的架構名稱作為其值的屬性。

   擴展架構沒有其自己的架構：從源架構生成的架構將用擴展架構的欄位填充。

   >[!IMPORTANT]
   >
   >不允許修改應用程式的內置架構，而是模式擴展機制。 否則，在將來升級應用程式時，將不會更新修改的架構。 這可能導致Adobe Campaign的使用失靈。

   **示例**:擴展 **nms：收件人** 架構。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   的 **nms：收件人** 擴展架構中填充了擴展架構中填充的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   的 **取決於方案** 架構的根元素上的屬性引用擴展架構上的依賴項。

   的 **屬於** 欄位上的屬性將填充聲明該屬性的架構。

>[!IMPORTANT]
>
>要考慮修改，需要重新生成方案。 如需詳細資訊，請參閱[此頁面](../../configuration/using/regenerating-schemas.md)。\
>如果修改影響資料庫的結構，則需要運行更新。 如需詳細資訊，請參閱[此頁面](../../configuration/using/updating-the-database-structure.md)。
