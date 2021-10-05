---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '1553'
ht-degree: 0%

---

# 屬性元素 {#attribute--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model}

屬性：==幫助

## 屬性 {#attributes}

_operation（字串）、advanced(boolean)、appliableIf(string)、autoIncrement(boolean)、tellesTo(string)、dataPolicy(string)、dbEnum(string)、defOnDuplicate(boolean)、default(string)、desc(string)、edit(string)、enum(string)、expr(string)、featureDate(boolean)、inut(string)、legng(string)、lableng(locable)、lalated(be)、NOL(ben)、NEN(NOT)STRING)、REF（字串）、必要（布林值）、SQL（布林值）、SQLDefault（字串）、SQLNAME（字串）、SQLTABLE（字串）、TARGET(MNTOKEN)、範本（字串）、translatedDefault（字串）、translatedExpr（字串）、類型(MNTOKEN)、用戶（布林值）、userEnum（字串）、visibleIf（字串）、xml（布林值）

## 父母 {#parents}

`<element>`

## 兒童 {#children}

`<help>`

## 說明 {#description}

`<attribute>` 元素可讓您定義資料庫中的欄位。

## 使用與使用內容 {#use-and-context-of-use}

`<attribute>` 元素中必須宣告 `<element>` 元素。

在`<srcschema>`中定義`<attribute>`元素的序列不會影響資料庫中的欄位建立序列。 建立順序將按字母順序排列。

## 屬性說明 {#attribute-description}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴充現成可用的結構時。

   可存取的值包括：

   * &quot;none&quot;:單獨調解。 這表示Adobe Campaign將復原元素，而不會更新元素，或在不存在的情況下產生錯誤。
   * &quot;insertOrUpdate&quot;:更新為插入。 這表示Adobe Campaign將更新元素，或在元素不存在時加以建立。
   * &quot;insert&quot;:插入。 這表示Adobe Campaign將插入元素，而不會檢查元素是否存在。
   * &quot;update&quot;:更新。 這表示Adobe Campaign將更新元素，或在元素不存在時產生錯誤。
   * &quot;delete&quot;:刪除。 這表示Adobe Campaign將復原和刪除元素。

* **進階（布林值）**:啟用此選項時(@advanced=&quot;true&quot;)，它可讓您隱藏可用欄位清單上的屬性，這些欄位可用於配置表單中的清單。
* **applicableIf（字串）**:此屬性可讓您將欄位設為選填欄位。當符合約束時更新資料庫時，將考慮`<attribute>`元素。 &quot;appliableIf&quot;接收XTK運算式。
* **autoIncrement（布林值）**:如果啟用此選項，欄位就會變成計數器。這可讓您增加值（大部分是ID）。 （外部使用）
* **tellesTo（字串）**:取用共用欄位之表格的名稱和命名空間，並填入宣告屬性的架構。（僅用於`<schema>`）。
* **dataPolicy(string)**:允許對SQL或XML欄位中允許的值指定批准約束。此屬性的值為：

   * &quot;none&quot;:無值
   * &quot;smartCase&quot;:首字母大寫
   * &quot;lowerCase&quot;:全部小寫
   * &quot;upperCase&quot;:全部大寫
   * &quot;email&quot;:電子郵件地址
   * &quot;phone&quot;:電話號碼
   * &quot;identifier&quot;:識別碼名稱
   * &quot;resIdentifier&quot;:檔案名

* **dbEnum(string)**:接收「已關閉」枚舉的內部名稱。必須在`<srcschema>`中定義枚舉值。
* **defOnDuplicate（布林值）**:如果激活了此屬性，則當記錄重複時，預設值(在@default中定義)將自動重新應用於記錄。
* **預設值（字串）**:可讓您定義預設欄位的值（呼叫函式、預設值）。此屬性會接收XTK運算式。
* **dsc（字串）**:可讓您插入屬性的說明。此說明會顯示在介面的狀態列中。
* **編輯（字串）**:此屬性指定將以連結到架構的形式使用的輸入類型。
* **列舉（字串）**:接收連結到欄位的枚舉的名稱。枚舉可以插入到相同的架構或遠程架構中。
* **expr（字串）**:定義欄位預計算表達式。此屬性會接收Xpath或XTK運算式。
* **功能（字串）**:定義特徵欄位：這些欄位用於擴充現有表格中的資料，但會將資料儲存在附件表格中。接受的值為：

   * &quot;shared&quot;:內容儲存在每個資料類型的共用表中
   * &quot;dedicated&quot;:內容儲存在專用表中

   SQL特性表是根據特性類型自動建立的：

   * 專用：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特徵欄位有兩種類型：簡單的oà¹欄位，其中單個值被授權於特徵上；或者，oà¹多個選擇欄位，其中特徵被連結至可包含多個值的集合元素。

   在架構中定義特性時，此架構必須具有基於單一欄位的主鍵（未授權複合鍵）。

* **featureDate（布林值）**:連結到「@feature」特性欄位的屬性。如果其值為「true」，則可讓您找出值的上次更新時間。
* **img(string)**:可讓您定義連結至欄位之影像的路徑（命名空間+影像名稱）(範例：img=&quot;cus:mypicture.jpg&quot;)。實際上，必須將映像導入應用程式伺服器。
* **標籤（字串）**:連結至欄位的標籤，通常會傳送給介面中的使用者。它可讓您避免命名限制。
* **length(string)**:max。「字串」類型SQL欄位的值的字元數。 如果未指定「@length」屬性，Adobe Campaign會自動建立255個字元的欄位。
* **可本地化（布林值）**:如果已啟動，此屬性會告訴收集工具，以復原「@label」屬性的值，以供翻譯（內部使用）。
* **name(MNTOKEN)**:與表中欄位名稱匹配的屬性名稱。「@name」屬性的值必須是短的，最好是英文，並符合XML命名限制。

   當架構寫入資料庫時，前置詞會由Adobe Campaign自動新增至欄位名稱：

   * &quot;i&quot;:前置詞用於「整數」類型。
   * &quot;d&quot;:首碼表示&#39;double&#39;類型。
   * &quot;s&quot;:字元字串類型的前置詞。
   * &quot;ts&quot;:「date」類型的前置詞。

   要完全定義表中欄位的名稱，在定義屬性時使用「@sqlname」選項。

* **notNull（布林值）**:可讓您重新定義Adobe Campaign在資料庫中管理NULL記錄的行為。預設情況下，數值欄位不為null，字串和日期類型欄位可為null。
* **pkgStatus(string)**:在套件匯出期間，會根據「@pkgStatus」的值考量值：

   * &quot;always&quot;:總是存在
   * &quot;never&quot;:永不存在
   * &quot;default（或無）&quot;:除非值是預設值，或它不是與其他實例不相容的內部欄位，否則會導出該值。

* **參考（字串）**:此屬性會定義對由多個結 `<attribute>` 構共用的元素的參考（定義計分）。定義不會複製到目前的架構中。
* **必要（布林值）**:如果已啟用此屬性(@required=&quot;true&quot;)，介面中會反白顯示該欄位。欄位的標籤在表單中為紅色。
* **sql（布林值）**:如果激活了此屬性(@sql=&quot;true&quot;)，則會強制儲存SQL屬性，即使包含該屬性的元素具有xml=&quot;true&quot;屬性時也是如此。
* **sqlDefault（字串）**:如果激活了屬性，此屬性允許您定義更新資料庫時考慮的預設@notNull值。如果此屬性是在建立屬性後添加的，則即使是新記錄，架構行為也不會更改。 若要變更結構並更新新記錄的值，您需要刪除並再次建立屬性。
* **sqlname(string)**:表建立期間的欄位。如果@sqlname未指定，預設會使用「@name」屬性的值。 當將架構寫入資料庫時，會根據欄位類型自動添加前置詞。
* **範本（字串）**:此屬性定義對由多個結 `<attribute>` 構共用的元素的引用。定義會自動複製到目前的架構中。
* **translatedDefault(string)**:如果找到「@default」屬性，則「@translatedDefault」可讓您重新定義運算式，以符合@default中定義的運算式，並由翻譯工具收集（內部使用）。
* **translatedExpr(string)**:如果存在「@expr」屬性，則「@translatedExpr」屬性可讓您重新定義表達式，以匹配@expr中定義的表達式，由翻譯工具收集（內部使用）。
* **類型(MNTOKEN)**:欄位類型。

   欄位類型為通用。 根據安裝的資料庫類型，Adobe Campaign會將定義的類型更改為結構更新期間所安裝資料庫的特定值。

   可用類型清單：

   * 任何
   * bin
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datemetz
   * datetimenotz
   * 日期
   * 兩次
   * 列舉
   * 浮點
   * html
   * int64
   * 連結
   * long
   * 備忘錄
   * MNTOKEN
   * 百分比
   * primarykey
   * short
   * 字串
   * 時間
   * 時間盤
   * uuid

   如果「@type」屬性留空，Adobe Campaign依預設會將長度為100的字元字串(STRING)連結至欄位。

   如果欄位為STRING類型，且欄位名稱未由&quot;@sqlname&quot;屬性的存在指定，則資料庫中欄位的名稱會自動前面加上&quot;s&quot;。 此操作模式與INTEGER(i)、DOUBLE(d)和DATES(ts)類型欄位類似。

* **userEnum(string)**:接收「開啟」枚舉的內部名稱。枚舉的值可由用戶在介面中定義。
* **visibleIf（字串）**:會以XTK運算式的形式定義條件，以顯示或隱藏屬性。

   >[!IMPORTANT]
   >
   >屬性隱藏，但仍可存取其資料。

* **xml（布林值）**:如果激活了此選項，則欄位的值沒有連結的SQL欄位。Adobe Campaign會為記錄儲存建立「mData」文字類型欄位。 這表示這些欄位沒有篩選或排序。

### 範例 {#examples}

其值儲存在資料庫中的枚舉值的示例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

使用&quot;@datapolicy&quot;聲明XML欄位：

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

以「@applicableIf」為例：「包含」屬性僅會在國家/地區數量大於20時建立。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

「@feature」為「共用」類型的範例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

「@feature」為「dedicated」類型的範例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
