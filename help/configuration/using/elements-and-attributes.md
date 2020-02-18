---
title: 元素和屬性
seo-title: 元素和屬性
description: 元素和屬性
seo-description: null
page-status-flag: never-activated
uuid: 72b0128a-a453-4646-93e5-b399914abb76
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5e24d94a-f9c1-4642-a881-dfc4b5492f14
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: dbff132e3bf88c408838f91e50e4b047947ee32a

---


# 元素和屬性 {#elements-and-attributes}

編輯架構時，可使用基於源架構(xtk:srcSchema)的批准系統。 使用「資料庫結構更新……」更新資料庫時，也可能發現一些錯誤。 嚮導說明。

依預設，在Adobe Campaign結構描述中，所有布林類型屬性都是「false」。 若要啟動這些屬性，您必須在結構中指定屬性，並將其值設為&quot;true&quot;。

## `<attribute>` 元素 {#attribute--element}

### 內容模型 {#content-model}

attribute:==help

### 屬性 {#attributes}

_operation（字串）、進階（布林）、appliableIf（字串）、autoIncrement（布林）、stringTo（字串）、dataPolicy（字串）、dbEnum（字串）、defOnDuplicate（布林）、default（字串）、desc（字串）、enum（字串）、expr（字串）、fegr(string(str)、feature(string)、be(string)、feateraturation(sing)、feature(string)、featureDate)、featureDeDatureDatureDateDateDate)、img（字串）、inout（字串）、標籤（字串）、長度（字串）、可本地化（布林）、名稱(MNTOKEN)、notNull（布林）、pkgStatus（字串）、ref（字串）、必要（布林）、sql（布林）、sqlDefault（字串）、sqltable（字串）、target(met（字串）、範本（字串）、translatedDefault（字串）、translatedExpr（字串）、type(MNTOKEN)、user(boolean)、userEnum（字串）、visibleIf（字串）、xml(boolean)

### 父母 {#parents}

`<element>`

### 兒童 {#children}

`<help>`

### 說明 {#description}

`<attribute>` 元素可讓您定義資料庫中的欄位。

### 使用與使用內容 {#use-and-context-of-use}

`<attribute>` 元素必須在元素中宣 `<element>` 告。

元素在中定 `<attribute>` 義的序列不 `<srcschema>` 會影響資料庫中的欄位建立序列。 建立順序將按字母順序排列。

### 屬性說明 {#attribute-description}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴展現成可用的架構。

   可存取的值包括：

   * 「無」:和解。 這表示Adobe Campaign將會復原元素，而不會更新元素，或在元素不存在時產生錯誤。
   * &quot;insertOrUpdate&quot;:使用插入進行更新。 這表示Adobe Campaign會更新元素，或在元素不存在時建立元素。
   * 「插入」:插入。 這表示Adobe Campaign將插入元素，而不檢查元素是否存在。
   * 「更新」:更新。 這表示Adobe Campaign會更新元素，或在元素不存在時產生錯誤。
   * 「刪除」:刪除。 這表示Adobe Campaign將會復原和刪除元素。

* **進階（布林值）**:啟用此選項(@advanced=&quot;true&quot;)時，它可讓您隱藏可用欄位清單中的屬性，這些欄位可用來設定表單中的清單。
* **appliableIf（字串）**:此屬性可讓您將欄位設為選用。 當 `<attribute>` 遵守約束時，在更新資料庫時將考慮元素。 &quot;appliableIf&quot;接收XTK運算式。
* **autoIncrement（布林值）**:如果此選項被激活，則欄位將變為計數器。 這可讓您增加值（大部分是ID）。 （外部使用）
* **terlessTo(string)**:使用共用該欄位的表的名稱和名稱空間，並填充聲明該屬性的架構。 (僅用於 `<schema>`)。
* **dataPolicy（字串）**:可讓您指定在SQL或XML欄位中允許的值的核准限制。 此屬性的值為：

   * 「無」:無值
   * &quot;smartCase&quot;:字母大寫
   * &quot;lowerCase&quot;:全部小寫
   * &quot;upperCase&quot;:全部大寫
   * 「電子郵件」:電子郵件位址
   * 「電話」:電話號碼
   * 「識別碼」:標識符名稱
   * &quot;resIdentifier&quot;:檔案名稱

* **dbEnum（字串）**:接收「已關閉」枚舉的內部名稱。 枚舉值必須在中定義 `<srcschema>`。
* **defOnDuplicate（布林值）**:如果激活了此屬性，則當記錄重複時，預設值（在@default中定義）會自動重新應用於記錄。
* **default(string)**:可讓您定義預設欄位的值（呼叫函式、預設值）。 此屬性接收XTK表達式。
* **desc（字串）**:可讓您插入屬性的說明。 此說明顯示在介面的狀態欄中。
* **edit(string)**:此屬性指定將以連結到方案的形式使用的輸入類型。
* **列舉（字串）**:接收連結到欄位的枚舉的名稱。 枚舉可以插入到同一模式或遠程模式中。
* **expr（字串）**:定義欄位預計算表達式。 此屬性接收Xpath或XTK表達式。
* **功能（字串）**:定義特徵欄位：這些欄位用於擴展現有表中的資料，但儲存在附件表中。 接受的值為：

   * 「共用」:內容儲存在每個資料類型的共用表格中
   * 「專用」:內容儲存在專用表格中
   SQL特徵表是根據特徵類型自動構建的：

   * 專屬： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   特徵欄位有兩種類型：簡單的à¹其中在特徵上授權單一值的欄位；另的¹多個選擇欄位，其中特徵連結至可包含數個值的收集元素。

   在模式中定義特徵時，此模式必須具有基於單個欄位的主鍵（組合鍵未授權）。

* **featureDate（布林值）**:屬性連結至「@feature」特徵欄位。 如果其值為&quot;true&quot;，則可讓您瞭解值上次更新的時間。
* **img(string)**:可讓您定義連結至欄位的影像路徑（namespace +影像名稱）(範例：img=&quot;cus:mypicture.jpg&quot;)。 實際上，映像必須導入到應用程式伺服器。
* **標籤（字串）**:連結至欄位的標籤，主要會寄送給介面中的使用者。 它可讓您避免命名限制。
* **長度（字串）**:max. 「字串」類型SQL欄位值的字元數。 如果未指定「@length」屬性，Adobe Campaign會自動建立255個字元的欄位。
* **可定位（布林值）**:如果已激活，此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:與表格中欄位名稱相符的屬性名稱。 「@name」屬性的值必須是短的，最好是英文，並符合XML命名限制。

   當架構寫入資料庫時，Adobe Campaign會自動將字首新增至欄位名稱：

   * 「i」:前置詞。
   * &quot;d&quot;:首碼。
   * &quot;s&quot;:首碼。
   * &quot;ts&quot;:首碼。
   要完全定義表中欄位的名稱，請在定義屬性時使用&quot;@sqlname&quot;選項。

* **notNull（布林值）**:可讓您重新定義Adobe Campaign在資料庫中管理NULL記錄的行為。 依預設，數值欄位不是null，字串和日期類型欄位可以是null。
* **pkgStatus（字串）**:在軟體包導出過程中，根據&quot;@pkgStatus&quot;的值，會考慮以下值：

   * 「always」:allowest
   * 「永不」:永遠不存在
   * &quot;default（或nothing）&quot;:值會導出，除非它是預設值，或者它不是與其他實例不相容的內部欄位。

* **ref(string)**:此屬性定義對由多個方案( `<attribute>` 定義分解)共用的元素的引用。 定義不會複製到目前的架構中。
* **必要（布林值）**:如果此屬性已啟用(@required=&quot;true&quot;)，則介面中會反白顯示此欄位。 欄位的標籤在表單中會顯示為紅色。
* **sql（布林值）**:如果激活此屬性(@sql=&quot;true&quot;)，則會強制儲存SQL屬性，即使包含該屬性的元素具有xml=&quot;true&quot;屬性。
* **sqlDefault（字串）**:此屬性允許您定義在激活@notNull屬性時更新資料庫時考慮的預設值。 如果在屬性建立後添加了此屬性，則即使對新記錄，架構行為也不會更改。 要更改方案並更新新記錄的值，需要刪除並再次建立屬性。
* **sqlname（字串）**:的子菜單。 如果未指定@sqlname，則預設情況下會使用&quot;@name&quot;屬性的值。 在資料庫中寫入模式時，會根據欄位類型自動添加前置詞。
* **範本（字串）**:此屬性定義對由多個方案共 `<attribute>` 享的元素的引用。 定義會自動複製到當前模式。
* **translatedDefault（字串）**:如果找到&quot;@default&quot;屬性，&quot;@translatedDefault&quot;將允許您重新定義表達式，以便與@default中定義的表達式匹配，由翻譯工具收集（內部使用）。
* **translatedExpr（字串）**:如果存在&quot;@expr&quot;屬性，則&quot;@translatedExpr&quot;屬性可讓您重新定義運算式，以符合@expr中定義的運算式，由轉換工具收集（內部使用）。
* **type(MNTOKEN)**:的雙曲餘切值。

   欄位類型為通用。 Adobe Campaign會根據安裝的資料庫類型，將定義的類型變更為結構更新期間所安裝資料庫的特定值。

   可用類型清單：

   * 任何
   * 賓
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datetimetz
   * datetimenotz
   * 日期
   * 雙倍
   * 列舉
   * 浮水
   * html
   * int64
   * link
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字串
   * 時間
   * 時間平移
   * uid
   如果「@type」屬性保留為空白，Adobe Campaign會依預設將長度為100的字元字串(STRING)連結至欄位。

   如果欄位為STRING類型，且欄位的名稱未由&quot;@sqlname&quot;屬性的存在指定，則資料庫中欄位的名稱將自動前面有&#39;s&#39;。 此操作模式與INTEGER(i)、DOUBLE(d)和DATES(ts)類型欄位類似。

* **userEnum（字串）**:接收&quot;open&quot;枚舉的內部名稱。 枚舉的值可由用戶在介面中定義。
* **visibleIf(string)**:定義XTK表達式形式的條件以顯示或隱藏屬性。

   >[!IMPORTANT]
   >
   >屬性已隱藏，但仍可存取其資料。

* **xml（布林值）**:如果激活此選項，則欄位的值沒有連結的SQL欄位。 Adobe Campaign會建立文字類型「mData」欄位以儲存記錄。 這表示這些欄位沒有篩選或排序。

### 範例 {#examples}

其值儲存在資料庫中的枚舉值示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

聲明XML欄位，其中「@datapolicy」:

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

帶有&quot;@appliableIf&quot;的示例：只有當國家數量大於20時，才會建立「包含」屬性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

「共用」類型的「@feature」範例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

「@feature」為「dedicated」類型的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```

## `<compute-string>` 元素 {#compute-string--element}

### 內容模型 {#content-model-1}

compute-string:==EMPTY

### 屬性 {#attributes-1}

@expr

### 父母 {#parents-1}

`<element>`

### 兒童 {#children-1}

無

### 說明 {#description-1}

元 `<compute-string>` 素可讓您根據XTK運算式產生字串，以根據數個值在介面中顯示「內建」標籤。

### 使用與使用內容 {#use-and-context-of-use-1}

未定 `<compute-string>` 義時，預設情況下， `<compute-string>` 將輸入一個元素，其中包含方案中主鍵的值。

### 屬性說明 {#attribute-description-1}

* **expr（字串）**:XTK和／或Xpath表達式

### 範例 {#examples-1}

```
<compute-string expr="@label + Iif(@code='','', ' (' + [folder/@label] + ')')"/>  
<compute-string expr="ToString([@centralCatalog-id]) + ',' + ToString([@localOrgUnit-id])" />
```

在收件者上計算的字串結果：「John Doe(john.doe@aol.com)」:

```
<element name="recipient">
<compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')'
"/>
...
</element>
```

## `<condition>` 元素 {#condition--element}

### 內容模型 {#content-model-2}

條件：==EMPTY

### 屬性 {#attributes-2}

* @boolOperator（字串）
* @enabledIf（字串）
* @expr（字串）

### 父母 {#parents-2}

`<sysfilter>`

### 兒童 {#children-2}

無

### 說明 {#description-2}

此元素可讓您定義篩選條件。

### 使用與使用內容 {#use-and-context-of-use-2}

一個 `<sysfiler>` 元素可包含數個篩選條件。

### 屬性說明 {#attribute-description-2}

* **boolOperator（字串）**:如果在相 `<conditions>` 同的元素中定義了數個元 `<sysfilter>` 素，此屬性可讓您組合它們。 依預設，元素之間的邏輯 `<condition>` 連結為&quot;AND&quot;。 「@boolOperator」屬性可讓您結合「OR」和「AND」類型連結。
* **enabledIf（字串）**:條件啟動測試。
* **expr（字串）**:XTK表達式。

### 範例 {#examples-2}

```
<sysfilter>
  <condition enabledIf="hasNamedRight('admin')=false" expr="@city=[currentOperator/location/@city]" />
</sysfilter>
```

## `<dbindex>` 元素 {#dbindex--element}

### 內容模型 {#content-model-3}

dbindex:==keyfield

### 屬性 {#attributes-3}

* @_operation（字串）
* @applicableIf（字串）
* @label（字串）
* @name(MNTOKEN)
* @unique（布林值）

### 父母 {#parents-3}

`<element>`

### 兒童 {#children-3}

`<keyfield>`

### 說明 {#description-3}

此元素可讓您定義連結至表格的索引。

### 使用與使用內容 {#use-and-context-of-use-3}

可以定義多個索引。 一個索引可以引用表的一個或多個欄位。 索引聲明通常遵循主模式元素的定義。

定義在中的 `<keyfield>` 元素順序 `<dbindex>` 非常重要。 第一 `<keyfield>` 個必須是查詢主要基於的索引標準。

資料庫中索引的名稱是通過串連表的名稱和索引的名稱來計算的。 例如：建立索引查詢期間索引欄位的表名「Sample」、名稱空間「Cus」、索引名「MyIndex」->名稱：&quot;CusSample_myIndex&quot;。

### 屬性說明 {#attribute-description-3}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴展現成可用的架構。

   可存取的值包括：

   * 「無」:和解。 這表示Adobe Campaign將會復原元素，而不會更新元素，或在元素不存在時產生錯誤。
   * &quot;insertOrUpdate&quot;:使用插入進行更新。 這表示Adobe Campaign會更新元素，或在元素不存在時建立元素。
   * 「插入」:插入。 這表示Adobe Campaign將插入元素，而不檢查元素是否存在。
   * 「更新」:更新。 這表示Adobe Campaign會更新元素，或在元素不存在時產生錯誤。
   * 「刪除」:刪除。 這表示Adobe Campaign將會復原和刪除元素。

* **appliableIf（字串）**:條件——接收XTK運算式。
* **標籤（字串）**:索引標籤。
* **名稱(MNTOKEN)**:唯一索引名。
* **唯一（布林）**:如果激活此選項(@unique=&quot;true&quot;)，則屬性保證索引在其欄位中的唯一性。

### 範例 {#examples-3}

在「id」欄位上建立索引。 (元素上的「@unique」屬性 `<dbindex>` 會觸發在資料庫（查詢）中建立索引時添加&quot;UNIQUE&quot; SQL關鍵字。

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

在「@mail」和「@phoneNumber」欄位上建立複合索引：

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```

## `<element>` 元素 {#element--element}

### 內容模型 {#content-model-4}

element:==(attribute)|計算字串| dbindex|預設|元素|說明|加入|密鑰| sysFilter| translatedDefault)

### 屬性 {#attributes-4}

_operation(string)、advanced(boolean)、aggregate(string)、appabliedIf(string)、autopk(boolean)、tessTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dbEnum(string)、defOnDuplicate(booliple)、deate(striate)、deac(s、de)、desc(stric(string)、desc(string(string)、desc(string)、desc(string)、desc(string)、desc(string)、duce)、desc(string)、desc(strinc(singDisplayAs)、displayAsAsDisplayAsAsAsDisplayAsfield(boolean)、doesNotSupportDiff(boolean)、edit(string)、emptyKeyValue(string)、enum(string)、enumImage(string)、expandSchemaTarget(string)、expr(string)、externalJoin(boolean)、featureDate(bate)、filterPath(s)、fulen)、filterPath(stringPh(string)、fonealPh(stingPath(string)、fone)、foryPh(string)、foreringPh(stringPh(string)、feringVen)、foleringPh(singLen)、folenFolenFolerLingLingLink(singL)、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hierarchicalPath(string)、img(string)、inout(string)、integrity(string)、labelSingular(string)、length(boolean)、name(boolean)、no索引鍵（布林）、有序（布林）、overflowtable（布林）、pkSequence(string)、pkgStatus(string)、ref(string)、revAdvanced（布林）、revCardinality(string)、revDesc(string)、revExternalJoin(boolean)、revIntegrity(string)、revLabel(string)、revLabel(string)、revStringlink(string)、revTarget(string)、revVisibleIf(string)、sql(boolean)、sqlname(string)、sqltable(string)、tableSpace(string)、tableSpaceIndex(string)、target(MNTOKEN)、temporaryTable(boolean)、translatedDefault(string)、translatedExpr(str(str(string)、typer(string)、type)、typeMNTOKEN)、未系結（布林）、user（布林）、userEnum（字串）、visibleIf（字串）、xml（布林）、xmlChildren（布林）

### 父母 {#parents-4}

`<srcschema>`

`<element>`

### 兒童 {#children-4}

* `<attribute>`
* `<compute-string>`
* `<dbindex>`
* `<default>`
* `<element>`
* `<help>`
* `<join>`
* `<key>`
* `<sysfilter>`
* `<translateddefault>`

### 說明 {#description-4}

Adobe Campaign中有四 `<element>` 種元素：

* 根 `<element>` :定義與方案匹配的SQL表的名稱。
* 結構 `<element>` :定義一組 `<element>` 或元 `<attribute>` 素。
* 連結 `<element>` :定義連結。 這些元素必須包含&quot;@type=link&quot;屬性。
* XML `<element>` :定義「mData」文字類型欄位。 此元素必須包含&quot;@type=xml&quot;屬性。

### 屬性說明 {#attribute-description-4}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴展現成可用的架構。

   可存取的值包括：

   * 「無」:和解。 這表示Adobe Campaign將會復原元素，而不會更新元素，或在元素不存在時產生錯誤。
   * &quot;insertOrUpdate&quot;:使用插入進行更新。 這表示Adobe Campaign會更新元素，或在元素不存在時建立元素。
   * 「插入」:插入。 這表示Adobe Campaign將插入元素，而不檢查元素是否存在。
   * 「更新」:更新。 這表示Adobe Campaign會更新元素，或在元素不存在時產生錯誤。
   * 「刪除」:刪除。 這表示Adobe Campaign將會復原和刪除元素。

* **進階（布林值）**:啟用此選項(@advanced=&quot;true&quot;)時，它可讓您隱藏可用欄位清單中的屬性，這些欄位可用來設定表單中的清單。
* **aggregate(string)**:可讓您透過其他架構復 `<element>` 制定義。 此屬性接收「namespace:name」形式的架構聲明。
* **appliableIf（字串）**:條件。 此屬性接收XTK表達式。
* **autopk（布林值）**:如果此選項已啟用(autopk=&quot;true&quot;)，則會自動定義唯一金鑰。 此選項只能用於架構的主要元素。 警告，Adobe Campaign只保證產生的金鑰是唯一的。 不保證密鑰值是連續的和增量的。
* **dataPolicy（字串）**:可以為SQL欄位中允許的值指定批准約束。 此屬性的值為：

   * 「無」:無值
   * &quot;smartCase&quot;:字母大寫
   * &quot;lowerCase&quot;:全部小寫
   * &quot;upperCase&quot;:全部大寫
   * 「電子郵件」:電子郵件位址
   * 「電話」:電話號碼
   * 「識別碼」:標識符名稱
   * &quot;resIdentifier&quot;:檔案名稱

* **dbEnum（字串）**:接收「已關閉」枚舉的內部名稱。 枚舉值必須在中定義 `<srcschema>`。
* **defOnDuplicate（布林值）**:如果激活了此屬性，則當記錄重複時，預設值（在@default中定義）會自動重新應用於記錄。
* **default(string)**:可讓您定義元素行為（對函式的呼叫，預設值）。 此屬性接收XTK表達式。
* **desc（字串）**:可讓您插入元素的說明。 此說明顯示在介面的狀態欄中。
* **displayAsField（布林值）**:如果激活了此屬性，則在結構 `<element>` 樹視圖（「結構」頁籤）中將顯示「連結」類型作為欄位。 這樣，就可以將連結顯示為本機欄位，並在查詢期間變更其行為。 在查詢的SELECT中找到元素時，將使用連結目標的值。 在查詢的WHERE中找到元素時，將使用連結的基礎鍵。
* **edit(string)**:此屬性指定將以連結到方案的形式使用的輸入類型。
* **列舉（字串）**:接收連結到欄位的枚舉的名稱。 枚舉可以插入到同一模式或遠程模式中。
* **expr（字串）**:此屬性定義一個計算欄位，該欄位的定義不儲存在表中。 它接收Xpath或XTK（字串）運算式。
* **externalJoin（布林值）**:「連結」類型元素中的外部連結。
* **功能（字串）**:定義特徵欄位：這些欄位用於擴展現有表中的資料，但儲存在附件表中。 接受的值為：

   * 「共用」:內容儲存在每個資料類型的共用表格中
   * 「專用」:內容儲存在專用表格中
   SQL特徵表是根據特徵類型自動構建的：

   * 專屬： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`
   特徵欄位有兩種類型：其中在特徵上授權單一值的簡單欄位，以及在多個選擇欄位中，特徵連結至可包含數個值的收集元素。

   在模式中定義特徵時，此模式必須具有基於單個欄位的主鍵（組合鍵未授權）。

* **featureDate（布林值）**:屬性連結至「@feature」特徵欄位。 如果其值為&quot;true&quot;，則可讓您瞭解值上次更新的時間。
* **filterPath（字串）**:此屬性會接收Xpath，並讓您在欄位上定義篩選。
* **folderLink（字串）**:此屬性接收連結的名稱，該名稱允許您恢復包含實體的檔案。
* **folderModel(string)**:定義啟用實體儲存的資料夾類型。 僅當存在&quot;@folderLink&quot;時才定義此屬性。
* **folderProcess（字串）**:定義實體模型實例儲存所在的連結。 僅當存在&quot;@folderLink&quot;時才定義此屬性。
* **fullLoad（布林值）**:此屬性強制在表單的欄位選擇期間顯示表中的所有記錄。
* **img(string)**:接收連結至元素的影像路徑。 此屬性的值為&quot;namespace:image name&quot;類型。 例如：img=&quot;cus:myImage.jpg&quot;。 實際上，映像必須導入到應用程式伺服器。
* **完整性（字串）**:源表對目標表的出現的參照完整性。

   可存取的值包括：

   * 「定義」:如果透過連結參考實體，Adobe Campaign不會將其刪除
   * 「正常」:刪除源實例將初始化目標實例上連結的鍵（預設模式），此類型的完整性將初始化所有外鍵
   * 「擁有」:刪除源實例會觸發刪除目標實例
   * 「下載」:類似「擁有」（若是刪除）或重複發生次數（若是重複）
   * 「中性」:不做任何事

* **標籤（字串）**:元素標籤。
* **labelSingular(string)**:介面的某些部分中使用的元素的標籤（奇異形式）。
* **長度（字串）**:max. 為「字串」類型SQL欄位的值授權的字元數。
* **可定位（布林值）**:如果已激活，此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:與表名稱匹配的元素的內部名稱。 「@name」屬性的值必須是短的，最好是英文，並符合連結至XML的命名限制。

   當架構寫入資料庫時，Adobe Campaign會自動將字首新增至欄位名稱。

   * 「i」:前置詞。
   * &quot;d&quot;:首碼。
   * &quot;s&quot;:首碼。
   * &quot;ts&quot;:首碼。
   要以自治方式定義表的名稱，需要在主模式元素的定義中使用&quot;@sqltable&quot;屬性。

* **noDbIndex（布林值）**:可讓您指定元素不會建立索引。
* **有序（布林值）**:如果屬性已啟用(ordered=&quot;true&quot;),Adobe Campaign會將元素宣告順序保留在XML收集元素中。
* **pkSequence（字串）**:接收用於計算自動增量密鑰的序列的名稱。 僅當在方案的根元素上定義了自動增量鍵時，才可以使用此屬性。
* **pkgStatus（字串）**:在包導出過程中，值將作為此屬性值的函式被考慮：

   * 「always」:元素將永遠存在
   * 「永不」:元素永遠不會出現
   * &quot;default（或nothing）&quot;:元素會匯出，除非它是預設元素，或者它不是內部欄位，而且與其他例項不相容

* **ref(string)**:此屬性定義對由多個結構（定義分解）共用的>element>元素的引用。 定義不會複製到目前的架構中。
* **必要（布林值）**:如果此屬性已啟用(@required=&quot;true&quot;)，則介面中會反白顯示此欄位。 欄位的標籤在表單中會顯示為紅色。
* **revAdvanced（布林值）**:啟用時，此屬性指定相反的連結為「進階」連結。
* **revCardinality（字串）**:此屬性定義兩個表之間連結的基數。 它用於「連結」類型 `<element>`。

   可能的值包括：

   * 「單一」:簡單1-1類型連結
   * 「未系結」:1-N類型系列連結
   依預設，如果在建立連結時未指定屬性，基數會是1-N。

* **revDesc（字串）**:此屬性接收連結到相反連結的說明。
* **revExternalJoin（布林值）**:啟動後，此屬性可讓您在相反的連結上強制外部連接。
* **revIntegrity(string)**:此屬性定義目標方案上的完整性。 授權的值與「@integrity」屬性相同。 依預設，Adobe Campaign會為此屬性提供「一般」值。
* **revLabel（字串）**:標籤。
* **revLink（字串）**:相反連結的名稱。 如果值為&quot;_NONE_&quot;，則不會在目標架構中建立相反的連結。
* **revTarget（字串）**:目標。
* **sql（布林值）**:如果此屬性被激活(@sql=&quot;true&quot;)，則會強制儲存SQL元素，即使該元素具有xml=&quot;true&quot;屬性。
* **sqlname（字串）**:表建立期間的欄位名稱。 如果未指定&quot;@sqlname&quot;，則預設情況下會使用&quot;@name&quot;屬性的值。 將模式寫入表時，會根據欄位類型自動添加前置詞。
* **sqltable（字串）**:對於方案的主要元素，此屬性會過載預設生成的SQL表的名稱。 如果未指定&quot;@sqltable&quot;，則預設名稱將按如下結構化：namespace（字母大寫），後面跟著SrcSchema &quot;@name&quot;的值。
* **tableSpace（字串）**:此屬性用於為表指定儲存表空間的新資料(在根上有 `<element>`效)。
* **tableSpaceIndex(string)**:此屬性用於為表指定新的索引儲存表空間(在根目錄上有 `<element>`效)。
* **target(MNTOKEN)**:在表之間建立連結時接收目標方案的名稱。 此屬性僅對&quot;link&quot;類型元素處於活動狀態。
* **範本（字串）**:此屬性定義對由多個方案共 `<element>` 享的元素的引用。 定義會自動複製到當前模式。
* **translatedDefault（字串）**:如果找到&quot;@default&quot;屬性，&quot;@translatedDefault&quot;將允許您重新定義表達式，以便與@default中定義的表達式匹配，由翻譯工具收集（內部使用）。
* **translatedExpr（字串）**:如果找到&quot;@expr&quot;屬性，「@translatedExpr」屬性可讓您重新定義與&quot;@expr&quot;中定義的運算式相符的運算式，該運算式將由轉換工具收集（內部使用）。
* **type(MNTOKEN)**:定義元素中儲存的資料類型。

   可用類型清單：

   * 任何
   * 賓
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datetimetz
   * datetimenotz
   * 日期
   * 雙倍
   * 列舉
   * 浮水
   * html
   * int64
   * link
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字串
   * 時間
   * 時間平移
   * uid

* **未綁定（布林）**:如果屬性已啟動(unbound=&quot;true&quot;)，連結會宣告為1-N基數的收集元素。
* **userEnum（字串）**:接收&quot;open&quot;枚舉的內部名稱。 枚舉值可由用戶在介面中定義。
* **xml（布林值）**:如果啟用此選項，元素中定義的所有值都會以XML格式儲存在TEXT類型&quot;mData&quot;欄位中。 這表示這些欄位將不會進行篩選或排序。
* **xmlChildren（布林值）**:強制儲存每個子系( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`

## `<enumeration>` 元素 {#enumeration--element}

### 內容模型 {#content-model-5}

枚舉：==(help| value)

### 屬性 {#attributes-5}

* @basetype（字串）
* @default（字串）
* @desc（字串）
* @label（字串）
* @name（字串）
* @template（字串）

### 父母 {#parents-5}

`<srcschema>`

### 兒童 {#children-5}

* `<help>`
* `<value>`

### 說明 {#description-5}

此元素可讓我們定義值列舉。 枚舉屬於它在中定義的模式，但可通過其他模式訪問它。

### 使用與使用內容 {#use-and-context-of-use-4}

枚舉是在架構開始時（在定義主元素之前）定義的。

### 屬性說明 {#attribute-description-5}

* **basetype(string)**:枚舉中儲存的值的類型。

   可用類型清單：

   * 任何
   * 賓
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
   * 雙倍
   * 列舉
   * 浮水
   * html
   * int64
   * link
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字串
   * 時間
   * 時間平移
   * uid

* **default(string)**:預設值。 預設值也可以是枚舉中定義的值之一。
* **desc（字串）**:枚舉說明。
* **標籤（字串）**:枚舉標籤。
* **name(string)**:枚舉的內部名稱。
* **範本（字串）**:此屬性定義對由多個方案共 `<enumeration>` 享的元素的引用。 定義會自動複製到當前模式。

### 範例 {#examples-4}

其值儲存在資料庫中的枚舉值示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>
```

定義具有預設值的枚舉：

```
 <enumeration basetype="byte" default="email" name="canal">
    <value label="Email" name="email" value="0"/> 
    <value label="Téléphone" name="phone" value="1"/>
    <value label="Call Center" name="callcenter" value="2"/>
 </enumeration>
```

## `<help>` 元素 {#help--element}

### 內容模型 {#content-model-6}

help:==EMPTY

### 屬性 {#attributes-6}

無

### 父母 {#parents-6}

`<srcschema>`  ,  `<element>`   ,   `<attribute>`    ,    `<enumeration>`     ,     `<value>`      ,     `<param />`,      `<method />`

### 兒童 {#children-6}

無

### 說明 {#description-6}

此元素可讓您說明 `<element>` 或元 `<attribute>` 素。 它只能包含文本，並儲存在資料庫中的XML中。

### 屬性說明 {#attribute-description-6}

此元素沒有屬性。

### 範例 {#examples-5}

```
<method name="CheckOperation" static="true"
      <helpchecks the validity of a campaign</help
...
</method> 
```

## `<join>` 元素 {#join--element}

### 內容模型 {#content-model-7}

join:==EMPTY

### 屬性 {#attributes-7}

* @dstFilterExpr（字串）
* @xpath-dst（字串）
* @xpath-src（字串）

### 父母 {#parents-7}

`<element>`

### 兒童 {#children-7}

無

### 說明 {#description-7}

可讓您定義在SQL表之間建立聯接的欄位。

### 使用與使用內容 {#use-and-context-of-use-5}

元 `<join>` 素只能在父元素為&#39;link&#39; `<element>` 類型時使用。 這表示父元素必須聲明&quot;@type=link&quot;屬性。

無需在元素中指定遠程表的名稱和名稱空 `<join>` 間。 必須在父項中指定這些值 `<element>`。

依慣例，連結會定義在架構的結尾。

如果在 `<join>` 定義連結類型元素時未指定該元素，則連結將自動放置在兩個表的主鍵上。

### 屬性說明 {#attribute-description-7}

* **dstFilterExpr（字串）**:此屬性可讓您限制遠端表格中符合資格的值數目。
* **xpath-dst（字串）**:此屬性接收遠程表的Xpath（@name屬性）。
* **xpath-src（字串）**:此屬性接收當前模式中的Xpath（@name屬性）。

### 範例 {#examples-6}

在當前表的「email」欄位和遠程表的「@compagny-id」欄位之間連結：

```
<join xpath-dst="@compagny-id" xpath-src="@email"/>
```

根據必須包含&#39;EN&#39;值的&quot;@country&quot;欄位內容，篩選指向&quot;cus:Country&quot;表格的連結：

```
<element name="StockEN" type="link" label="MyLink" target="cus:Stock">
   <join xpath-dst="@country" xpath-src="@code" dstFilterExpr="@country = 'EN'"/>
 </element>
```

## `<key>` 元素 {#key--element}

### 內容模型 {#content-model-8}

key:==keyfield

### 屬性 {#attributes-8}

* @allowEmptyPart（布林值）
* @applicableIf（字串）
* @internal（布林值）
* @label（字串）
* @name(MNTOKEN)
* @noDbIndex（布林）

### 父母 {#parents-8}

`<element>`

### 兒童 {#children-8}

`<keyfield>`

### 說明 {#description-8}

此元素可讓您定義用於識別表格中記錄的索引鍵。

表必須至少有一個鍵。

### 使用與使用內容 {#use-and-context-of-use-6}

作為規則，鍵在模式的主要元素和索引之後聲明。

如果密鑰包含多個欄位（即多個子欄位），則該密鑰稱為 `<keyfield>` 複合。 請勿使用複合鍵來定義主鍵。

如果架構的主要元素包含&quot;@autopk=true&quot;屬性，則主鍵是唯一的。 每個方案只能有一個主鍵。

保留前1000個標識符，因此如果需要為鍵定義一系列值，則從1000開始。

### 屬性說明 {#attribute-description-8}

* **allowEmptyPart（布林值）**:在複合鍵的情況下，如果此屬性被激活，則如果其至少一個鍵不為空，則它們的鍵被視為有效。 如果是這種情況，空的概念值是&quot;0&quot;（布林值或所有數值資料類型）。 預設情況下，需要輸入組成複合密鑰的所有密鑰。
* **appliableIf（字串）**:此屬性可讓您將索引鍵設為選用。 它定義了將應用密鑰定義的條件。 此屬性接收XTK表達式。
* **內部（布林值）**:如果啟用，此屬性可讓Adobe Campaign知道金鑰是主要金鑰。
* **標籤（字串）**:索引鍵標籤。
* **名稱(MNTOKEN)**:索引鍵的內部名稱。
* **noDbIndex（布林值）**:如果它已激活(noDbIndex=&quot;true&quot;)，則不對與鍵匹配的欄位編製索引。

### 範例 {#examples-------}

複合密鑰的聲明，該密鑰授權&quot;@expr&quot;或&quot;alias&quot;欄位為空：

```
<key name="node" allowEmptyPart="true">
  <keyfield xpath="@expr"/>
   <keyfield xpath="@alias"/>
 </key>
```

在STRING類型的&quot;Name&quot;欄位和匹配的SQL查詢中聲明 `<srcschema>` 主鍵：

```
 
<key name="PrimaryKey" internal="true">  
  <keyfield xpath="@name"/>
</key>

CREATE UNIQUE INDEX Schema_PrimaryKey ON Schema(sName);
```

## `<keyfield>` 元素 {#keyfield--element}

### 內容模型 {#content-model-9}

keyfield:==EMPTY

### 屬性 {#attributes-9}

* @xlink(MNTOKEN)
* @xpath(MNTOKEN)

### 父母 {#parents-9}

`<key>`  ,  `<dbindex />`

### 兒童 {#children-9}

無

### 說明 {#description-9}

此元素定義要整合到索引或鍵中的欄位。

### 屬性說明 {#attribute-description-9}

* **xlink(MNTOKEN)**:可讓您自動參照在關係表（N-N連結）的連接中定義的外鍵。
* **xpath(MNTOKEN)**:索引或元素上索引鍵的定 `<attribute>` 義。 此屬性接收一個Xpath ，它定義了用於定義索引或索引的架構屬性的路徑。

### 範例 {#examples-}

在「@name」上具有Xpath的索引中選擇「sName」欄位：

```
<keyfield xpath="@name"/>
```

## `<method>` 元素 {#method--element}

### 內容模型 {#content-model-10}

方法：==(help|參數)

### 屬性 {#attributes-10}

* @_operation（字串）
* @access（字串）
* @const（布林值）
* @hidden（布林值）
* @label（字串）
* @library（字串）
* @name(MNTOKEN)
* @pkonly（布林值）
* @static（布林值）

### 父母 {#parents-10}

`<methods>`  ,  `<interface />`

### 兒童 {#children-10}

* `<help>`
* `<parameters>`

### 說明 {#description-10}

此元素可讓您定義SOAP方法。

### 使用與使用內容 {#use-and-context-of-use-7}

SOAP方法可啟用應用程式程式。

宣告新方法（非原生）時，必須使用「@library」:namespace和用於庫的名稱獨立於聲明所在的架構的名稱空間和名稱。

### 屬性說明 {#attribute-description-10}

* **存取（字串）**:此屬性定義使用方法的訪問控制。 如果此屬性遺失，則必須進行識別。 可用值包括：&#39;anonymous&#39;、&#39;admin&#39;和&#39;sql&#39;。
* **const（布林值）**:如果激活了該屬性，則此屬性表示聲明的方法將改變實體
* **標籤（字串）**:標籤。
* **程式庫（字串）**:此方法不是應用程式的原生方法。 此屬性使用找到方法定義的方法庫(nms:mylibrary.js)的值。
* **名稱(MNTOKEN)**:唯一方法名稱。
* **靜態（布林值）**:如果激活了此屬性，則方法被視為自治，在調用該屬性時，必須將所有參數指定給該方法。

### 範例 {#examples-7}

「訂閱」現成可用方法的定義：

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```

## `<methods>` 元素 {#methods--element}

### 內容模型 {#content-model-11}

方法：==方法

### 屬性 {#attributes-11}

無

### 父母 {#parents-11}

`<srcschema>`

### 兒童 {#children-11}

方法

### 說明 {#description-11}

此元素可讓您定義元 `<method>` 素。 聲明方法是強制的。

### 屬性說明 {#attribute-description-11}

此元素沒有屬性。

### 範例 {#examples-8}

```
<methods async="true"
...// definition of one or more <method
</methods>
```

## `<param>` 元素 {#param--element}

### 內容模型 {#content-model-12}

param:==help

### 屬性 {#attributes-12}

* @_operation（字串）
* @desc（字串）
* @enum（字串）
* @inout（字串）
* @label（字串）
* @localized（字串）
* @name(MNTOKEN)
* @namespace(MNTOKEN)
* @type（字串）

### 父母 {#parents-12}

`<parameters>`

### 兒童 {#children-12}

`<help>`

### 說明 {#description-12}

此元素可讓您定義用於呼叫SOAP方法的參數。

### 屬性說明 {#attribute-description-12}

* **desc（字串）**:與元素相關的 `<param>` 說明。
* **inout（字串）**:此屬性定義參數是否在SOAP調用的輸入(in)或輸出(out)處。 如果未指定此屬性，則預設參數為input(&quot;@inout=in&quot;)。
* **標籤（字串）**:標籤 `<param>`
* **可定位（字串）**:如果已激活，此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:內部名稱 `<param>`
* **type(string)**:此屬性定義元素的類 `<param>` 型

   可用類型清單：

   * 任何
   * 賓
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datetimetz
   * datetimenotz
   * 日期
   * DOMDocument
   * DOMElement
   * 雙倍
   * 列舉
   * 浮水
   * html
   * int64
   * link
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * 短
   * 字串
   * 時間
   * 時間平移
   * uid

### 範例 {#examples-9}

字串類型&quot;serviceName&quot;入站設定的定義：

```
<param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string" inout="in"/>
```

## `<parameters>` 元素 {#parameters--element}

### 內容模型 {#content-model-13}

參數：==param

### 屬性 {#attributes-13}

無

### 父母 {#parents-13}

`<method>`

### 兒童 {#children-13}

`<param>`

### 說明 {#description-13}

此元素定義一組元 `<parameter>` 素。

### 使用與使用內容 {#use-and-context-of-use-8}

此元素是強制的，即使對於元素的單 `<param>` 個子元素也是 `<method>` 如此。

### 屬性說明 {#attribute-description-13}

無

### 範例 {#examples-10}

```
<parameters
... //definition of one or more <param
</parameters>
```

## `<srcschema>` 元素 {#srcschema--element}

### 內容模型 {#content-model-14}

srcSchema:==(attribute|建立者|資料|元素|枚舉|說明|介面|方法|修改者)

### 屬性 {#attributes-14}

created(datetime)、createdBy-id(long)、desc(string)、entitySchema(string)、extendedSchema(string)、img(string)、implements(string)、labelSingular(string)、lastModified(datetime)、library(string)、mappingBy-id(long)、name(string)、name(string)、nameste, useRecycleBin（布林值）, view（布林值）, xtkschema（字串）

### 父母 {#parents-14}

無

### 兒童 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

### 說明 {#description-14}

是 `<srcschema>` 方案的根元素。 它是模式定義的輸入點。

### 使用與使用內容 {#use-and-context-of-use-9}

結構表示法可在關於 [結構參考](../../configuration/using/about-schema-reference.md) 和 [結構中使用](../../configuration/using/schema-structure.md)。

### 屬性說明 {#attribute-description-14}

* **已建立（日期時間）**:此屬性提供了建立方案的日期和時間資訊。 它有「日期時間」表單。 顯示的值取自伺服器。 時間以UTC格式顯示。
* **createdBy-id(long)**:是建立架構的運算子的標識符。
* **desc（字串）**:架構描述
* **entitySchema（字串）**:基本架構，其語法和核准是以(Adobe Campaign的預設值：xtk:srcSchema)。 當您儲存目前的架構時，Adobe Campaign會核准其語法，其中架構在@xtkschema屬性中宣告。
* **extendedSchema（字串）**:接收當前模式擴展所基於的現成可用模式的名稱。 表單為「namespace:name」。
* **img(string)**:連結到架構的表徵圖（可在架構建立嚮導中定義）。
* **標籤（字串）**:方案標籤。
* **labelSingular(string)**:標籤（單數），以顯示在介面中。
* **lastModified(datetime)**:此屬性提供上次修改的日期和時間資訊。 它有「日期時間」表單。 顯示的值取自伺服器。 時間以UTC格式顯示。
* **庫（布林）**:將架構用作庫而非實體。 因此，由於&quot;@ref&quot;和&quot;@template&quot;屬性，其他方案可能會引用此方案。
* **mappingType（字串）**:

   * &quot;sql&quot;:資料庫映射
   * &quot;textFile&quot;:文本檔案映射
   * &quot;xmlFile&quot;:XML格式文本檔案映射
   * &quot;binaryFile&quot;:二進位檔案映射

* **modifiedBy-id(long)**:與變更結構的運算子的識別碼相符。
* **name(string)**:唯一方案名稱。
* **namespace(string)**:架構的名稱空間(預設值：nms、xtk、nl)。 為項目建立新模式時，建議您使用專用的名稱空間。
* **useRecycleBin（布林值）**:在應用程式中啟動垃圾筒功能。 刪除的記錄將放在垃圾筒中，然後再進行最終刪除。 此函式僅在「傳送」模式中可用。
* **view(boolean)**:如果它已激活(@view=&quot;true&quot;)，則模式將用作視圖。 資料庫結構更新嚮導將不考慮模式。 此選項主要用於引用外部表。
* **xtkschema（字串）**:定義模式語法的模式的名稱（預設情況下為xtk:srcSchema）。

### 範例 {#examples-11}

`<srcschema>` 「nms:delivery」的出廠模式元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```

## `<sysfilter>` 元素 {#sysfilter--element}

### 內容模型 {#content-model-15}

sysFilter:==condition

### 屬性 {#attributes-15}

無

### 父母 {#parents-15}

`<element>`

### 兒童 {#children-15}

`<condition>`

### 說明 {#description-15}

此元素可讓您定義篩選。

### 屬性說明 {#attribute-description-15}

此元素沒有屬性。

### 範例 {#examples-12}

定義具有@name屬性上條件的篩選：

```
<sysFilter>
      <condition expr="@name ='Doe'"/>
  <sysFilter>
```

## `<value>` 元素 {#value--element}

### 內容模型 {#content-model-16}

value:==help

### 屬性 {#attributes-16}

* @applicableIf（字串）
* @desc（字串）
* @enabledIf（字串）
* @img（字串）
* @label（字串）
* @name（字串）
* @value（字串）

### 父母 {#parents-16}

`<enumeration>`

### 兒童 {#children-16}

`<help>`

### 說明 {#description-16}

此元素可讓您定義枚舉中儲存的值。

### 屬性說明 {#attribute-description-16}

* **appliableIf（字串）**:此屬性可讓您使枚舉值成為可選值。 它接收XTK表達式。
* **desc（字串）**:枚舉值的說明。
* **enabledIf（字串）**:條件，以啟動枚舉值。
* **img(string)**:連結至&quot;namespace:image_name&quot;表單中列舉的影像。 映像必須導入到應用程式伺服器。
* **標籤（字串）**:枚舉值的標籤。
* **name(string)**:枚舉值的內部名稱。
* **值（字串）**:枚舉值的值。 值的類型是根據枚舉的類型定義的。 如果枚舉為字串類型，則它只能包含字串類型值。

### 範例 {#examples-13}

```
<enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>
```
