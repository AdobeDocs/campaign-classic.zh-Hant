---
product: campaign
title: 關於方案版本
description: 開始使用架構版
feature: Schema Extension
exl-id: 9e10b24e-c4de-4e76-bbed-0d05f62120b7
source-git-commit: 8fa50d17a9ff36ccc310860ac93771590cfd76fd
workflow-type: tm+mt
source-wordcount: '1004'
ht-degree: 7%

---

# 關於方案版本{#about-schema-edition}

![](../../assets/v7-only.svg)

Adobe Campaign使用資料架構：

* 定義應用程式內資料物件與基礎資料庫表的連結方式。
* 定義 Campaign 應用程式中不同資料物件之間的連結。
* 定義及描述每個物件中包含的個別欄位。

要更好地瞭解活動內置表及其交互作用，請參閱 [此部分](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html)。

## 擴展或建立架構 {#extending-or-creating-schemas}

要將欄位或索引或其他元素添加到市場活動中的核心資料方案之一，如收件人表(nms:recipient)，必須擴展該方案。 有關詳細資訊，請參閱 [擴展架構](../../configuration/using/extending-a-schema.md) 的子菜單。

要添加在Adobe Campaign（例如合同表）中不現成的全新類型資料，您可以直接建立自定義架構。 有關詳細資訊，請參閱 [資料架構](../../configuration/using/data-schemas.md) 的子菜單。

![](assets/schemaextension_getting_started_1.png)

在擴展或建立要使用的架構後，最佳做法是按如下所示的順序定義其XML內容元素。

## 分項清單 {#enumerations}

先在架構的主元素之前定義枚舉。 它們允許您在清單中顯示值，以限制用戶對給定欄位的選擇。

範例:

```
<enumeration basetype="byte" name="exTransactionTypeEnum" default="store">
<value label="Website" name="web" value="0"/>
<value label="Call Center" name="phone" value="1"/>
<value label="In Store" name="store" value="2"/>
</enumeration>
```

在定義欄位時，您可以像這樣使用此枚舉：

```
<attribute desc="Type of Transaction" label="Transaction Type" name="transactionType" 
type="string" enum="exTransactionTypeEnum"/>
```

>[!NOTE]
>
>您還可以使用用戶管理的枚舉(通常在 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** )指定給定欄位的值。 這些實際上是全局枚舉，如果枚舉可能在您正在使用的特定架構之外使用，則是一個更好的選擇。

要瞭解有關枚舉的詳細資訊，請參閱 [枚舉](../../configuration/using/schema-structure.md#enumerations) 和 [`<enumeration>` 元素](../../configuration/using/schema/enumeration.md) 的下界。

## 索引 {#index}

索引是在架構的主元素中聲明的第一個元素。

它們可以是唯一的，也可以是非唯一的，並引用一個或多個欄位。

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

的 **xpath** 屬性指向您希望索引的架構中的欄位。

>[!IMPORTANT]
>
>必須記住，索引提供的SQL查詢讀取效能提升也會對寫入記錄產生效能衝擊。 因此，應謹慎使用這些指標。

有關索引的詳細資訊，請參閱 [索引欄位](../../configuration/using/database-mapping.md#indexed-fields) 的子菜單。

## 鍵 {#keys}

每個表必須至少有一個鍵，並且通常使用 **@autopk=true** 屬性設定為「true」。

還可以使用 **內部** 屬性。

範例:

```
<key name="householdId" internal="true">
  <keyfield xpath="@householdId"/>
</key>
```

在此示例中，不讓 **@autopk** 屬性建立名為「id」的預設主鍵，我們將指定自己的「householdId」主鍵。

>[!IMPORTANT]
>
>建立新架構或在架構擴展期間，需要為整個架構保留相同的主鍵序列值(@pkSequence)。

有關鍵的詳細資訊，請參閱 [密鑰管理](../../configuration/using/database-mapping.md#management-of-keys) 的子菜單。

## 屬性（欄位） {#attributes--fields-}

屬性允許您定義構成資料對象的欄位。 您可以使用 **[!UICONTROL Insert]** 按鈕，將空屬性模板拖放到游標所在的XML中。 有關詳細資訊，請參閱 [資料架構](../../configuration/using/data-schemas.md) 的子菜單。

![](assets/schemaextension_getting_started_2.png)

屬性的完整清單可在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 的子菜單。 以下是一些更常用的屬性：

* **@advanced**
* **@dataPolicy**
* **@default**
* **@desc**
* **@enum**
* **@expr**
* **@label**
* **@length**
* **@名稱**
* **@notNull**
* **@required**
* **@ref**
* **@xml**
* **@type**

   要查看列出Adobe Campaign為不同資料庫管理系統生成的資料類型的映射的表，請參閱 [映射Adobe Campaign/DBMS資料的類型](../../configuration/using/schema-structure.md#mapping-the-types-of-adobe-campaign-dbms-data) 的子菜單。

有關每個屬性的詳細資訊，請參閱 [屬性說明](../../configuration/using/schema/attribute.md) 的子菜單。

### 範例 {#examples}

定義預設值的示例：

```
<attribute name="transactionDate" label="Transaction Date" type="datetime" default="GetDate()"/>
```

將公共屬性用作模板的示例，該模板也標籤為必需：

```
<attribute name="mobile" label="Mobile" template="nms:common:phone" required="true" />
```

使用 **@advanced** 屬性：

```
<attribute name="domain" label="Email domain" desc="Domain of recipient email address" expr="GetEmailDomain([@email])" advanced="true" />
```

XML欄位的示例也儲存在SQL欄位中， **@dataPolicy** 屬性。

```
<attribute name="secondaryEmail" label="Secondary email address" length="100" xml="true" sql="true" dataPolicy="email" />
```

>[!IMPORTANT]
>
>雖然大多數屬性都根據1-1基數連結到資料庫的物理欄位，但XML欄位或計算欄位的情況並非如此。\
>XML欄位儲存在表的備注欄位(「mData」)中。\
>但是，每次啟動查詢時都動態地建立計算欄位，因此它只存在於應用層中。

## 連結 {#links}

連結是架構主元素中最後的一些元素。 它們定義實例中所有不同架構之間的關聯方式。

連結在包含 **外鍵** 連結的表。

基數有三種類型：1-1、1-N和N-N預設使用的是1-N類型。

### 範例 {#examples-1}

收件人表（現成模式）和自定義事務表之間1-N連結的示例：

```
<element label="Recipient" name="lnkRecipient" revLink="lnkTransactions" target="nms:recipient" type="link"/>
```

自定義架構「Car」（在「cus」命名空間中）與收件人表之間1-1連結的示例：

```
<element label="Car" name="lnkCar" revCardinality="single" revLink="recipient" target="cus:car" type="link"/>
```

基於電子郵件地址而不是主鍵的收件人表和地址表之間的外部聯接示例：

```
<element name="emailInfo" label="Email Info" revLink="recipient" target="nms:address" type="link" externalJoin="true">
  <join xpath-dst="@address" xpath-src="@email"/>
</element>
```

此處，&quot;xpath-dst&quot;對應於目標架構中的主鍵，而&quot;xpath-src&quot;對應於源架構中的外鍵。

## 稽核軌跡 {#audit-trail}

您可能希望在架構底部包括的一個有用元素是跟蹤元素（審計跟蹤）。

使用下面的示例可以包括與建立日期、建立資料的用戶、日期以及表中所有資料上次修改的作者相關的欄位：

```
<element aggregate="xtk:common:auditTrail" name="auditTrail"/>
```

## 更新資料庫結構 {#updating-the-database-structure}

完成並保存更改後，需要將可能影響SQL結構的任何更改應用到資料庫。 為此，請使用資料庫更新嚮導。

![](assets/schemaextension_getting_started_3.png)

有關詳細資訊，請參閱[更新資料庫結構](../../configuration/using/updating-the-database-structure.md)區段。

>[!NOTE]
>
>當修改不影響資料庫結構時，只需重新生成模式。 為此，請選擇要更新的架構，按一下右鍵並選擇 **[!UICONTROL Actions > Regenerate selected schemas...]** 。 有關詳細資訊，請參閱 [重新生成架構](../../configuration/using/regenerating-schemas.md) 的子菜單。
