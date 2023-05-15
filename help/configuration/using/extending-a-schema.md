---
product: campaign
title: 擴充結構
description: 了解如何擴充結構
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 4%

---

# 擴充結構{#extending-a-schema}

>[!IMPORTANT]
>
>某些內建結構不得延伸：主要是已定義下列設定的：\
>**dataSource=&quot;file&quot;** 和 **mappingType=&quot;xmlFile&quot;**.\
>不得擴充下列結構： **xtk:entityBackupNew**, **xtk:entityBackupOriginal**, **xtk:entityOriginal**, **xtk:form**, **xtk:srcSchema**, **ncm:publishing**, **nl：監視**, **nms:calendar**, **nms:remoteTracking**, **nms:userAgentRules**, **xtk:builder**, **xtk：連接**, **xtk:dbInit**, **xtk:funcList**, **xtk:fusion**, **xtk:js**, **xtk:navtree**, **xtk:queryDef**, **xtk:resourceMenu**, **xtk:schema**, **xtk:scriptContext**, **xtk:session**, **xtk:sqlSchema**, **xtk:strings**.
>這份清單並非詳盡無遺。

擴充現有結構的方法有兩種：

1. 直接修改源架構。
1. 使用相同名稱但不同命名空間建立其他架構。 其優點是，您無需修改原始架構即可擴展表。

   架構的根元素必須包含 **extendedSchema** 屬性，其名稱為要擴展的架構的值。

   擴充功能結構沒有其專屬的結構：從來源架構產生的架構將會填入擴充功能架構的欄位。

   >[!IMPORTANT]
   >
   >您不能修改應用程式的內建架構，而不能修改架構擴展機制。 否則，在將來升級應用程式時，修改的架構將不會更新。 這可能導致使用Adobe Campaign時發生故障。

   **範例**:延伸功能 **nms:recipient** 綱要。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   此 **nms:recipient** 擴充架構中會填入擴充架構中填入的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   此 **dependingSchemas** 架構的根元素上的屬性會參照擴充功能架構上的相依性。

   此 **屬於** 欄位上的屬性會填入宣告該屬性的架構中。

>[!IMPORTANT]
>
>若要考慮修改，您需要重新產生結構。 如需詳細資訊，請參閱[此頁面](../../configuration/using/regenerating-schemas.md)。\
>如果修改影響資料庫的結構，則需要運行更新。 如需詳細資訊，請參閱[此頁面](../../configuration/using/updating-the-database-structure.md)。
