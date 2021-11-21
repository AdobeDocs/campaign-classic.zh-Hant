---
product: campaign
title: 關於方案版本
description: 開始使用綱要版本
audience: configuration
content-type: reference
topic-tags: editing-schemas
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# 關於方案版本{#about-schema-edition}

![](../../assets/v7-only.svg)

Adobe Campaign採用資料結構：

* 定義應用程式內資料物件與基礎資料庫表的連結方式。
* 定義 Campaign 應用程式中不同資料物件之間的連結。
* 定義及描述每個物件中包含的個別欄位。

如需深入了解Campaign內建表格及其互動，請參閱 [本節](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html).

## 擴充或建立結構 {#extending-or-creating-schemas}

若要將欄位、索引或其他元素新增至Campaign中的其中一個核心資料結構，例如收件者表格(nms:recipient)，您必須擴充該結構。 有關詳細資訊，請參閱 [擴充結構](../../configuration/using/extending-a-schema.md) 區段。

若要新增Adobe Campaign中不存在的全新資料類型（例如合約表格），您可以直接建立自訂結構。 有關詳細資訊，請參閱 [資料結構](../../configuration/using/data-schemas.md) 區段。

![](assets/schemaextension_getting_started_1.png)

擴展或建立結構以便使用後，最佳實務是按如下所示的順序定義其XML內容元素。

## 分項清單 {#enumerations}

先在架構的主要元素之前定義列舉。 它們可讓您在清單中顯示值，以限制使用者對指定欄位的選擇。

範例:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

定義欄位時，您就可以像這樣使用此分項清單：

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>您也可以採用使用者管理的列舉(通常位於 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** )來指定指定欄位的值。 這些實際上是全局枚舉，如果您的枚舉可能在您正在使用的特定架構之外使用，則可作為更好的選擇。

要了解有關枚舉的詳細資訊，請參閱 [列舉](../../configuration/using/schema-structure.md#enumerations) 和 [`<enumeration>` 元素](../../configuration/using/schema/enumeration.md) 區段。

## 索引 {#index}

索引是在架構的主要元素中宣告的第一個元素。

它們可以是唯一的，也可以參照一個或多個欄位。

範例:

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

此 **xpath** 屬性指向您要索引的架構中的欄位。

>[!IMPORTANT]
>
>請務必記住，索引提供的SQL查詢讀取效能增益還伴有寫入記錄時的效能點擊。 因此，索引應與預防搭配使用。

有關索引的詳細資訊，請參閱 [索引欄位](../../configuration/using/database-mapping.md#indexed-fields) 區段。

## 金鑰 {#keys}

每個表必須至少有一個鍵，並且通常會使用 **@autopk=true** 屬性設為「true」時，退出連結才會受到追蹤。

也可以使用 **內部** 屬性。

範例:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

在此範例中，請避免讓 **@autopk** 屬性會建立名為「id」的預設主索引鍵，我們會指定自己的「househId」主索引鍵。

>[!IMPORTANT]
>
>在建立新架構或架構擴充期間，您需要為整個架構保留相同的主鍵序列值(@pkSequence)。

若要進一步了解金鑰，請參閱 [密鑰管理](../../configuration/using/database-mapping.md#management-of-keys) 區段。

## 屬性（欄位） {#attributes--fields-}

屬性可讓您定義組成資料物件的欄位。 您可以使用 **[!UICONTROL Insert]** 按鈕，將空屬性模板放入游標所在的XML中。 有關詳細資訊，請參閱 [資料結構](../../configuration/using/data-schemas.md) 區段。

![](assets/schemaextension_getting_started_2.png)

屬性的完整清單可在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 區段。 以下是一些最常用的屬性：

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

   要查看列出Adobe Campaign為不同資料庫管理系統生成的資料類型映射的表，請參閱 [對應Adobe Campaign/DBMS資料的類型](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 區段。

如需每個屬性的詳細資訊，請參閱 [屬性說明](../../configuration/using/schema/attribute.md) 區段。

### 範例 {#examples}

定義預設值的範例：

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

將通用屬性作為欄位範本的範例，也標示為強制：

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

使用 **@advanced** 屬性：

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

XML欄位也儲存在SQL欄位中，且具有 **@dataPolicy** 屬性。

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>雖然大多數屬性都根據1-1基數連結到資料庫的物理欄位，但XML欄位或計算欄位的情況並非如此。\
>XML欄位儲存在表的備注欄位(「mData」)中。\
>但是，每次啟動查詢時都會動態建立計算欄位，因此它僅存在於應用層中。

## 連結 {#links}

連結是結構之主要元素中的最後一些元素。 它們定義您執行個體中所有不同結構彼此的關聯方式。

連結在包含 **外鍵** 連結的表格。

基數類型有三種：1-1、1-N和N-N。預設會使用1-N類型。

### 範例 {#examples-1}

收件者表格（現成可用結構）與自訂交易表格之間1-N連結的範例：

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

自訂結構「Car」（在「cus」命名空間中）與收件者表格之間1-1連結的範例：

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

根據電子郵件地址而非主鍵在收件人表和地址表之間進行外部聯接的示例：

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

其中，「xpath-dst」對應至目標架構中的主索引鍵，而「xpath-src」對應至來源架構中的外鍵。

## 稽核軌跡 {#audit-trail}

您可能想在結構底部加入的實用元素之一，是追蹤元素（稽核軌跡）。

請使用以下範例來包含與建立日期、建立資料的使用者、日期，以及表格中所有資料的上次修改作者相關的欄位：

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 更新資料庫結構 {#updating-the-database-structure}

完成並保存更改後，需要將任何可能影響SQL結構的更改應用到資料庫。 要執行此操作，請使用資料庫更新嚮導。

![](assets/schemaextension_getting_started_3.png)

有關詳細資訊，請參閱[更新資料庫結構](../../configuration/using/updating-the-database-structure.md)區段。

>[!NOTE]
>
>當修改不影響資料庫結構時，您只需重新產生結構即可。 要執行此操作，請選擇要更新的架構，按一下右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** . 有關詳細資訊，請參閱 [重新生成結構](../../configuration/using/regenerating-schemas.md) 區段。
