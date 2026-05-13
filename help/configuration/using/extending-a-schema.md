---
product: campaign
title: 擴充綱要
description: 瞭解如何擴充方案
role: Developer
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
TQID: https://experienceleague.adobe.com/w-Pe9dOgxIRB0KnOggStMDqzaNkCFGsh-5sOISc-t2E
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b82389f8-9b5e-4083-8e3b-3cef299fb8b9
subfeature_v2:
  - id: a72a22e0-8c8d-4019-ba42-3f2644aa91a3
  - id: cfc95e9b-b035-4403-a6a9-b27a8a053a37
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
source-git-commit: 4c295c0dabae8aba298390a3da2422a3fa1219f9
workflow-type: tm+mt
source-wordcount: 304
ht-degree: 5%

---

# 擴充綱要{#extending-a-schema}

>[!IMPORTANT]
>
>有些內建方案不可擴充：主要是針對已定義下列設定的方案：\
>**dataSource=&quot;file&quot;**&#x200B;和&#x200B;**mappingType=&quot;xmlFile&quot;**。\
>下列結構描述不可延伸： **xtk:entityBackupNew**、**xtk:entityBackupOriginal**、**xtk:entityOriginal**、**xtk:form**、**xtk:srcSchema**、**ncm:publishing**、**nl:monitoring**、**nms:calendar**、**nms:remoteTracking**、**nms:userAgentRules**、**xtk:builder**、**xtk:connections**， **xtk:dbInit**，**xtk:funcList**，**xtk:fusion**，**xtk： jst**，**xtk:navtree**，**xtk:queryDef**，**xtk:resourceMenu**，**xtk:schema**，**xtk:scriptContext**，**xtk:session**，**xtk:sqlSchema**， **xtk:strings**。
>此清單並非詳盡無遺。

擴充現有方案的方法有兩種：

1. 直接修改來源結構描述。
1. 建立具有相同名稱但不同名稱空間的另一個結構描述。 優點在於您可以擴充表格而無需修改原始架構。

   結構描述的根專案必須包含&#x200B;**extendedSchema**&#x200B;屬性，並將要擴充的結構描述名稱當作其值。

   擴充功能結構描述沒有自己的結構描述：從來源結構描述產生的結構描述會填入擴充功能結構描述的欄位。

   >[!IMPORTANT]
   >
   >您不得修改應用程式的內建方案，而只能修改方案擴充機制。 否則，修改後的結構描述將不會在應用程式未來升級時更新。 這可能會導致Adobe Campaign的使用發生問題。

   **範例**： **nms:recipient**&#x200B;結構描述的延伸。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   **nms:recipient**&#x200B;擴充結構描述已填入擴充結構描述中填入的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   結構描述根專案上的&#x200B;**dependingSchemas**&#x200B;屬性會參考擴充功能結構描述的相依性。

   欄位上的&#x200B;**fallsTo**&#x200B;屬性會填入宣告它的結構描述。

>[!IMPORTANT]
>
>若要將修改納入考量，您需要重新產生結構。 如需詳細資訊，請參閱[此頁面](../../configuration/using/regenerating-schemas.md)。\
>如果修改影響資料庫的結構，您必須執行更新。 如需詳細資訊，請參閱[此頁面](../../configuration/using/updating-the-database-structure.md)。
