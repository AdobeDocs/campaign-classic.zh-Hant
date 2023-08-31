---
product: campaign
title: 擴充綱要
description: 瞭解如何擴充方案
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Schema Extension
exl-id: 6e3e666d-6ab3-4346-93ca-fb0155a4660d
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 6%

---

# 擴充綱要{#extending-a-schema}

>[!IMPORTANT]
>
>有些內建方案不可擴充：主要是針對已定義下列設定的方案：\
>**dataSource=&quot;file&quot;** 和 **mappingType=&quot;xmlFile&quot;**.\
>下列結構描述不可延伸： **xtk：entityBackupNew**， **xtk：entityBackupOriginal**， **xtk：entityOriginal**， **xtk：form**， **xtk：srcSchema**， **ncm：publishing**， **nl：monitoring**， **nms：calendar**， **nms：remoteTracking**， **nms：userAgentRules**， **xtk：builder**， **xtk：連線**， **xtk：dbInit**， **xtk：funcList**， **xtk：fusion**， **xtk： jst**， **xtk：navtree**， **xtk：queryDef**， **xtk：resourceMenu**， **xtk：schema**， **xtk：scriptContext**， **xtk：session**， **xtk：sqlSchema**， **xtk：strings**.
>此清單並非詳盡無遺。

擴充現有方案的方法有兩種：

1. 直接修改來源結構描述。
1. 建立具有相同名稱但不同名稱空間的另一個結構描述。 優點在於您可以擴充表格而無需修改原始架構。

   結構描述的根元素必須包含 **extendedSchema** 具有要擴充之綱要名稱作為值的屬性。

   擴充功能結構描述沒有自己的結構描述：從來源結構描述產生的結構描述會填入擴充功能結構描述的欄位。

   >[!IMPORTANT]
   >
   >您不得修改應用程式的內建方案，而只能修改方案擴充機制。 否則，修改後的結構描述將不會在應用程式未來升級時更新。 這可能會導致Adobe Campaign的使用發生問題。

   **範例**：擴充功能 **nms：recipient** 綱要。

   ```
   <srcSchema extendedSchema="nms:recipient" name="recipient" namespace="cus">
     <element name="recipient">
       <attribute name="code" label="Branch code" type="long"/>
     </element>
   </srcSchema>
   ```

   此 **nms：recipient** 擴充結構描述中，填入了擴充結構描述中的欄位：

   ```
   <schema dependingSchemas="cus:recipient" name="recipient" namespace="nms">
     ...
     <attribute belongsTo="cus:recipient" label="Branch code" name="code" sqlname="iCode" type="long"/>
     ...
   </schema>
   ```

   此 **相依綱要** 結構描述根元素上的屬性會參考擴充功能結構描述的相依性。

   此 **beystsTo** 欄位上的屬性會填入宣告該屬性的結構描述。

>[!IMPORTANT]
>
>若要將修改納入考量，您需要重新產生結構。 如需詳細資訊，請參閱[此頁面](../../configuration/using/regenerating-schemas.md)。\
>如果修改影響資料庫的結構，您必須執行更新。 如需詳細資訊，請參閱[此頁面](../../configuration/using/updating-the-database-structure.md)。
