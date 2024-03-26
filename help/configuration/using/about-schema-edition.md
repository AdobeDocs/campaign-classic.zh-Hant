---
product: campaign
title: 關於方案版本
description: 開始使用結構描述版本
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Schema Extension
role: Data Engineer, Developer
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 7%

---

# 關於方案版本{#about-schema-edition}

Adobe Campaign採用資料結構描述來：

* 定義應用程式內資料物件與基礎資料庫表的連結方式。
* 定義 Campaign 應用程式中不同資料物件之間的連結。
* 定義及描述每個物件中包含的個別欄位。

若要更瞭解Campaign內建表格及其互動，請參閱 [本節](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html).

## 擴充或建立方案 {#extending-or-creating-schemas}

若要將欄位或索引或其他元素新增至Campaign的其中一個核心資料結構，例如收件者表格(nms：recipient)，您必須擴充該結構。 有關詳細資訊，請參閱 [擴充綱要](../../configuration/using/extending-a-schema.md) 區段。

若要新增不存在於Adobe Campaign中的現成全新資料型別（例如合約表格），您可以直接建立自訂結構描述。 有關詳細資訊，請參閱 [資料結構描述](../../configuration/using/data-schemas.md) 區段。

![](assets/schemaextension_getting_started_1.png)

當您擴充或建立要在中運作的結構描述後，最佳實務便是以其XML內容元素在下面出現的順序來定義其XML內容元素。

## 分項清單 {#enumerations}

分項清單會先定義，在結構描述的主要元素之前。 它們可讓您在清單中顯示值，以限制使用者在指定欄位中的選擇。

例如：

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

定義欄位時，您可以使用此分項清單，如下所示：

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>您也可以使用使用者管理的分項清單(通常位於 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** )，指定指定欄位的值。 這些實際上是全域分項清單，如果您可在您使用的特定結構描述之外使用分項清單，這是較好的選擇。

若要進一步瞭解分項清單，請參閱 [分項清單](../../configuration/using/schema-structure.md#enumerations) 和 [`<enumeration>` 元素](../../configuration/using/schema/enumeration.md) 區段。

## 索引 {#index}

索引是在結構描述的主要元素中宣告的第一個元素。

它們可以唯一或不唯一，並參考一個或多個欄位。

範例：

```
<dbindex name="email" unique="true">
  <keyfield xpath="@email"/>
</dbindex>
```

```
<dbindex name="lastNameAndZip">
  <keyfield xpath="@lastName"/>
  <keyfield xpath="location/@zipCode"/>
</dbindex>
```

此 **xpath** 屬性會指向您要在結構描述中編制索引的欄位。

>[!IMPORTANT]
>
>請務必記住，索引提供的SQL查詢讀取效能提升也會在寫入記錄時帶來效能點選。 因此，應謹慎使用索引。

有關索引的詳細資訊，請參閱 [索引欄位](../../configuration/using/database-mapping.md#indexed-fields) 區段。

## 金鑰 {#keys}

每個資料表都必須至少有一個索引鍵，而且通常會在結構描述的主要元素中使用 **@autopk=true** 屬性設為「true」。

主索引鍵也可使用定義 **內部** 屬性。

例如：

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

在此範例中，請不要讓 **@autopk** 屬性會建立名為「id」的預設主索引鍵，我們指定自己的「householdId」主索引鍵。

>[!IMPORTANT]
>
>建立新結構描述或在結構描述擴充期間，您需要為整個結構描述保留相同的主要索引鍵序列值(@pkSequence)。

如需金鑰的詳細資訊，請參閱 [金鑰管理](../../configuration/using/database-mapping.md#management-of-keys) 區段。

## 屬性（欄位） {#attributes--fields-}

屬性可讓您定義組成資料物件的欄位。 您可以使用 **[!UICONTROL Insert]** 結構描述版本工具列中的按鈕，將空的屬性範本拖放至游標所在的XML中。 有關詳細資訊，請參閱 [資料結構描述](../../configuration/using/data-schemas.md) 區段。

![](assets/schemaextension_getting_started_2.png)

完整的屬性清單可在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 區段。 以下是一些較常用的屬性：

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@name**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

  若要檢視Adobe Campaign針對不同資料庫管理系統產生之資料型別對應清單，請參閱 [對應Adobe Campaign/DBMS資料型別](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 區段。

如需每個屬性的詳細資訊，請參閱 [屬性說明](../../configuration/using/schema/attribute.md) 區段。

### 範例 {#examples}

定義預設值的範例：

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

針對也標籤為必要欄位使用通用屬性作為範本的範例：

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

使用隱藏的計算欄位範例 **@advanced** 屬性：

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

同樣儲存在SQL欄位中的XML欄位範例，此欄位具有 **@dataPolicy** 屬性。

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>雖然大多數屬性都是根據1-1基數連結到資料庫的實體欄位，但XML欄位或計算欄位則不是這種情況。\
>XML欄位儲存在表格的備忘錄欄位(「mData」)中。\
>但是，計算欄位在每次查詢啟動時都會動態建立，因此只存在於應用程式層中。

## 連結 {#links}

連結是結構描述中主要元素的最後幾個元素。 它們定義您執行個體中所有不同的結構描述如何相互關聯。

在包含下列專案的架構中宣告連結： **外部索引鍵** 連結至的資料表。

基數有三種型別：1-1、1-N和N-N。這是預設使用的1-N型別。

### 範例 {#examples-1}

收件者表格（現成可用的綱要）與自訂交易表格之間的1-N連結範例：

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

自訂方案「Car」（位於「cus」名稱空間）與收件者表格之間的1-1連結範例：

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

收件者表格和位址表格之間的外部聯結範例（根據電子郵件地址而非主索引鍵）：

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

此處「xpath-dst」對應於目標架構中的主索引鍵，「xpath-src」對應於來源架構中的外部索引鍵。

## 稽核軌跡 {#audit-trail}

架構底部可能想要包含一個實用元素，即追蹤元素（稽核軌跡）。

使用下列範例來包含與建立日期、建立資料的使用者、日期和表格中所有資料的上次修改作者相關的欄位：

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 更新資料庫結構 {#updating-the-database-structure}

完成並儲存變更後，任何可能影響SQL結構的變更都必須套用至資料庫。 要執行此操作，請使用資料庫更新精靈。

![](assets/schemaextension_getting_started_3.png)

有關詳細資訊，請參閱[更新資料庫結構](../../configuration/using/updating-the-database-structure.md)區段。

>[!NOTE]
>
>當修改不會影響資料庫結構時，您只需要重新產生結構描述。 若要這麼做，請選取要更新的結構描述，按一下滑鼠右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** . 有關詳細資訊，請參閱 [重新產生方案](../../configuration/using/regenerating-schemas.md) 區段。
