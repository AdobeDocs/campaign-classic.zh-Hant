---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 1818bd2aeb60689b2ce0e59cb0bd157f000de513
workflow-type: tm+mt
source-wordcount: '1552'
ht-degree: 0%

---


# `<attribute>` 元素  {#attribute--element}

## 內容模型{#content-model}

attribute:==help

## 屬性{#attributes}

_operation（字串）、進階（布林）、appliableIf（字串）、autoIncrement（布林）、stringTo（字串）、dataPolicy（字串）、dbEnum（字串）、defOnDuplicate（布林）、default（字串）、desc（字串）、enum（字串）、expr（字串）、fegr(string(str)、feature(string)、be(string)、feateraturation(sing)、feature(string)、featureDate)、featureDeDatureDatureDateDateDate)、img（字串）、inout（字串）、標籤（字串）、長度（字串）、可本地化（布林）、名稱(MNTOKEN)、notNull（布林）、pkgStatus（字串）、ref（字串）、必要（布林）、sql（布林）、sqlDefault（字串）、sqltable（字串）、target(met（字串）、範本（字串）、translatedDefault（字串）、translatedExpr（字串）、type(MNTOKEN)、user(boolean)、userEnum（字串）、visibleIf（字串）、xml(boolean)

## 父代{#parents}

`<element>`

## 子項{#children}

`<help>`

## 說明 {#description}

`<attribute>` 元素可讓您定義資料庫中的欄位。

## 使用與使用內容{#use-and-context-of-use}

`<attribute>` 元素必須在元素中 `<element>` 宣告。

`<attribute>`元素在`<srcschema>`中定義的序列不會影響資料庫中的欄位建立序列。 建立順序將按字母順序排列。

## 屬性說明{#attribute-description}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴展現成可用的架構。

   可存取的值包括：

   * 「無」:和解。 這表示Adobe Campaign將會復原元素，而不會更新元素，或在元素不存在時產生錯誤。
   * &quot;insertOrUpdate&quot;:使用插入進行更新。 這表示Adobe Campaign會更新元素，或在元素不存在時建立元素。
   * 「插入」:插入。 這表示Adobe Campaign將插入元素，而不檢查元素是否存在。
   * 「更新」:更新。 這表示Adobe Campaign會更新元素，或在元素不存在時產生錯誤。
   * 「刪除」:刪除。 這表示Adobe Campaign將會復原和刪除元素。

* **進階（布林值）**:啟用此選項(@advanced=&quot;true&quot;)時，它可讓您隱藏可用欄位清單中的屬性，這些欄位可用來設定表單中的清單。
* **appliableIf（字串）**:此屬性可讓您將欄位設為選用。當符合約束條件時，在更新資料庫時將考慮`<attribute>`元素。 &quot;appliableIf&quot;接收XTK運算式。
* **autoIncrement（布林值）**:如果此選項被激活，則欄位將變為計數器。這可讓您增加值（大部分是ID）。 （外部使用）
* **terlessTo(string)**:使用共用該欄位的表的名稱和名稱空間，並填充聲明該屬性的架構。（僅用於`<schema>`）。
* **dataPolicy（字串）**:可讓您指定在SQL或XML欄位中允許的值的核准限制。此屬性的值為：

   * 「無」:無值
   * &quot;smartCase&quot;:字母大寫
   * &quot;lowerCase&quot;:全部小寫
   * &quot;upperCase&quot;:全部大寫
   * 「電子郵件」:電子郵件位址
   * 「電話」:電話號碼
   * 「識別碼」:標識符名稱
   * &quot;resIdentifier&quot;:檔案名稱

* **dbEnum（字串）**:接收「已關閉」枚舉的內部名稱。枚舉值必須在`<srcschema>`中定義。
* **defOnDuplicate（布林值）**:如果激活了此屬性，則當記錄重複時，預設值（在@default中定義）會自動重新應用於記錄。
* **default(string)**:可讓您定義預設欄位的值（呼叫函式、預設值）。此屬性接收XTK表達式。
* **desc（字串）**:可讓您插入屬性的說明。此說明顯示在介面的狀態欄中。
* **edit(string)**:此屬性指定將以連結到方案的形式使用的輸入類型。
* **列舉（字串）**:接收連結到欄位的枚舉的名稱。枚舉可以插入到同一模式或遠程模式中。
* **expr（字串）**:定義欄位預計算表達式。此屬性接收Xpath或XTK表達式。
* **功能（字串）**:定義特徵欄位：這些欄位用於擴展現有表中的資料，但儲存在附件表中。接受的值為：

   * 「共用」:內容儲存在每個資料類型的共用表格中
   * 「專用」:內容儲存在專用表格中

   SQL特徵表是根據特徵類型自動構建的：

   * 專屬：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特徵欄位有兩種類型：簡單的à¹其中在特徵上授權單一值的欄位；另的¹多個選擇欄位，其中特徵連結至可包含數個值的收集元素。

   在模式中定義特徵時，此模式必須具有基於單個欄位的主鍵（組合鍵未授權）。

* **featureDate（布林值）**:屬性連結至「@feature」特徵欄位。如果其值為&quot;true&quot;，則可讓您瞭解值上次更新的時間。
* **img(string)**:可讓您定義連結至欄位的影像路徑（namespace +影像名稱）(範例：img=&quot;cus:mypicture.jpg&quot;)。實際上，映像必須導入到應用程式伺服器。
* **標籤（字串）**:連結至欄位的標籤，主要會寄送給介面中的使用者。它可讓您避免命名限制。
* **長度（字串）**:max.「字串」類型SQL欄位值的字元數。 如果未指定「@length」屬性，Adobe Campaign會自動建立255個字元的欄位。
* **可定位（布林值）**:如果已激活，此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:與表格中欄位名稱相符的屬性名稱。「@name」屬性的值必須是短的，最好是英文，並符合XML命名限制。

   當架構寫入資料庫時，Adobe Campaign會自動將字首新增至欄位名稱：

   * 「i」:前置詞。
   * &quot;d&quot;:首碼。
   * &quot;s&quot;:首碼。
   * &quot;ts&quot;:首碼。

   要完全定義表中欄位的名稱，請在定義屬性時使用&quot;@sqlname&quot;選項。

* **notNull（布林值）**:可讓您重新定義Adobe Campaign在資料庫中管理NULL記錄的行為。依預設，數值欄位不是null，字串和日期類型欄位可以是null。
* **pkgStatus（字串）**:在包導出過程中，根據&quot;@pkgStatus&quot;的值，會考慮以下值：

   * 「always」:allowest
   * 「永不」:永遠不存在
   * &quot;default（或nothing）&quot;:值會導出，除非它是預設值，或者它不是與其他實例不相容的內部欄位。

* **ref(string)**:此屬性定義對由多個方案( `<attribute>` 定義分解)共用的元素的引用。定義不會複製到目前的架構中。
* **必要（布林值）**:如果此屬性已啟用(@required=&quot;true&quot;)，則介面中會反白顯示此欄位。欄位的標籤在表單中會顯示為紅色。
* **sql（布林值）**:如果激活此屬性(@sql=&quot;true&quot;)，則會強制儲存SQL屬性，即使包含該屬性的元素具有xml=&quot;true&quot;屬性。
* **sqlDefault（字串）**:此屬性允許您定義在激活@notNull屬性時更新資料庫時考慮的預設值。如果在屬性建立後添加了此屬性，則即使對新記錄，架構行為也不會更改。 要更改方案並更新新記錄的值，需要刪除並再次建立屬性。
* **sqlname（字串）**:的子菜單。如果未指定@sqlname，則預設情況下會使用&quot;@name&quot;屬性的值。 在資料庫中寫入模式時，會根據欄位類型自動添加前置詞。
* **範本（字串）**:此屬性定義對由多個方案 `<attribute>` 共用的元素的引用。定義會自動複製到當前模式。
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

* **userEnum（字串）**:接收&quot;open&quot;枚舉的內部名稱。枚舉的值可由用戶在介面中定義。
* **visibleIf(string)**:定義XTK表達式形式的條件以顯示或隱藏屬性。

   >[!IMPORTANT]
   >
   >屬性已隱藏，但仍可存取其資料。

* **xml（布林值）**:如果激活此選項，則欄位的值沒有連結的SQL欄位。Adobe Campaign會建立文字類型「mData」欄位以儲存記錄。 這表示這些欄位沒有篩選或排序。

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
