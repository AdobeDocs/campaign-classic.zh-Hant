---
product: campaign
title: 元素和屬性 — 屬性元素
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 0%

---

# 屬性元素 {#attribute--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model}

屬性：==幫助

## 屬性 {#attributes}

_operation(string)、advanced(boolean)、appliableIf(string)、autoIncrement(boolean)、latesTo(string)、dataPolicy(string)、dbEnum(string)、defOnDuplicate(boolean)、desc(string)、enum(string)、expr(string)、featr(string)、fefefature(string)、feature(stion(string)、feature(string)、feature(string)、img(string)、inout(string)、label(string)、length(string)、可本地化(boolean)、name(boolean)、notNull(boolean)、pkgStatus(string)、ref(string)、required(boolean)、sqlDefault(string)、sqlname(string)、target(mtoken)、template, translatedDefault(string), translatedExpr(string), type(MNTOKEN), user(boolean), userEnum(string), visibleIf(string), xml(boolean)

## 父母 {#parents}

`<element>`

## 兒童 {#children}

`<help>`

## 說明 {#description}

`<attribute>` 元素允許在資料庫中定義欄位。

## 使用和使用上下文 {#use-and-context-of-use}

`<attribute>` 元素必須在 `<element>` 的子菜單。

序列 `<attribute>` 元素在 `<srcschema>` 不會影響資料庫中的欄位建立順序。 建立順序將按字母順序排列。

## 屬性說明 {#attribute-description}

* **操作（字串）**:定義在資料庫中寫入的類型。

   此屬性主要用於擴展開箱模式。

   可訪問的值為：

   * &quot;無&quot;:單獨和解。 這意味著，Adobe Campaign將恢復元素，而不更新該元素，如果該元素不存在，則不生成錯誤。
   * &quot;insertOrUpdate&quot;:用插入更新。 這意味著Adobe Campaign將更新元素或在元素不存在時建立它。
   * &quot;插入&quot;:插入。 這意味著Adobe Campaign將插入元素，而不檢查它是否存在。
   * &quot;更新&quot;:更新。 這意味著Adobe Campaign將更新元素，或在元素不存在時生成錯誤。
   * &quot;刪除&quot;:刪除。 這意味著Adobe Campaign將恢復和刪除元素。

* **高級（布爾值）**:激活此選項(@advanced=&quot;true&quot;)時，它允許您隱藏可用欄位清單中的屬性，這些欄位可用於在表單中配置清單。
* **appliatedIf（字串）**:此屬性允許您使欄位成為可選欄位。 的 `<attribute>` 當滿足約束時，在更新資料庫時將考慮元素。 &quot;appliableIf&quot;接收XTK表達式。
* **autoIncrement（布爾值）**:如果激活此選項，該欄位將變為計數器。 這樣，您就可以增加值（大多為ID）。 （外部使用）
* **屬於（字串）**:獲取共用該欄位的表的名稱和命名空間，並填充聲明該屬性的架構。 (僅在 `<schema>`)。
* **dataPolicy（字串）**:允許您對SQL或XML欄位中允許的值指定批准約束。 此屬性的值為：

   * &quot;無&quot;:無值
   * &quot;smartCase&quot;:首字母大寫
   * &quot;lowerCase&quot;:全部小寫
   * &quot;upperCase&quot;:全部大寫
   * 「電子郵件」：電子郵件地址
   * &quot;電話&quot;:電話號碼
   * &quot;標識符&quot;:標識符名稱
   * &quot;resIdentifier&quot;:檔案名

* **dbEnum（字串）**:接收「已關閉」枚舉的內部名稱。 必須在 `<srcschema>`。
* **defOnDuplicate（布爾型）**:如果激活此屬性，則當記錄重複時，預設值(在@default中定義)將自動重新應用於記錄。
* **預設（字串）**:用於定義預設欄位的值（調用函式，預設值）。 此屬性接收XTK表達式。
* **desc（字串）**:用於插入屬性的說明。 此說明顯示在介面的狀態欄中。
* **編輯（字串）**:此屬性指定將以連結到架構的形式使用的輸入類型。
* **枚舉（字串）**:接收連結到該欄位的枚舉的名稱。 枚舉可以插入到同一架構或遠程架構中。
* **expr（字串）**:定義欄位預計算表達式。 此屬性接收Xpath或XTK表達式。
* **特徵（字串）**:定義特徵欄位：這些欄位用於擴展現有表中的資料，但儲存在附件表中。 接受的值為：

   * &quot;共用&quot;:內容按資料類型儲存在共用表中
   * &quot;專用&quot;:內容儲存在專用表中

   SQL特徵表是根據特徵類型自動生成的：

   * 專用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   有兩種類型的特徵欄位：簡單oà¹欄位，其中單個值在特徵上被授權，而oà¹多個選擇欄位，其中特徵被連結到可能包含多個值的收集元素。

   在模式中定義特徵時，此模式必須具有基於單個欄位的主鍵（未授權複合鍵）。

* **featureDate（布爾型）**:連結到「@feature」特徵欄位的屬性。 如果其值為&quot;true&quot;，則允許您查找上次更新值的時間。
* **img（字串）**:用於為連結到欄位的影像定義路徑（命名空間+影像名稱）(示例：img=&quot;cus:mypicture.jpg&quot;)。 物理上，必須將映像導入到應用程式伺服器。
* **標籤（字串）**:連結到該欄位的標籤，主要發往介面中的用戶。 它可以避免命名限制。
* **長度（字串）**:最大。 「字串」類型SQL欄位的值的字元數。 如果未指定「@length」屬性，則Adobe Campaign會自動為255個字元建立一個欄位。
* **可本地化（布爾型）**:如果激活了該屬性，則此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:與表中欄位名稱匹配的屬性的名稱。 「@name」屬性的值必須短，最好是英文，並符合XML命名約束。

   當模式寫入資料庫時，前置詞會由Adobe Campaign自動添加到欄位名：

   * 「i」：「integer」類型的前置詞。
   * &quot;d&quot;:「double」類型的前置詞。
   * &quot;s&quot;:字串類型的前置詞。
   * &quot;ts&quot;:「date」類型的前置詞。

   要完全定義表中欄位的名稱，請在定義屬性時使用「@sqlname」選項。

* **notNull（布爾值）**:用於重新定義Adobe Campaign在資料庫中管理NULL記錄的行為。 預設情況下，數字欄位不為空，字串和日期類型欄位可以為空。
* **pkgStatus（字串）**:在包導出過程中，根據「@pkgStatus」的值將值考慮在內：

   * &quot;always&quot;:總是出現
   * &quot;從不&quot;:永遠
   * &quot;default（或nothing）&quot;:除非該值是預設值，或者它不是與其他實例不相容的內部欄位，否則將導出該值。

* **ref（字串）**:此屬性定義對 `<attribute>` 由多個架構共用的元素（定義分解）。 定義未複製到當前架構中。
* **必需（布爾型）**:如果激活了此屬性(@required=&quot;true&quot;)，則該欄位將在介面中突出顯示。 該欄位的標籤將以紅色顯示。
* **sql（布爾型）**:如果此屬性被激活(@sql=&quot;true&quot;)，則會強制儲存SQL屬性，即使包含該屬性的元素具有xml=&quot;true&quot;屬性。
* **sqlDefault（字串）**:如果激活了@notNull屬性，則此屬性允許您定義更新資料庫時考慮的預設值。 如果在屬性建立後添加此屬性，則即使是新記錄，架構行為也不會更改。 要更改方案並更新新記錄的值，需要刪除並再次建立屬性。
* **sqlname（字串）**:的子菜單。 如果未指@sqlname，則預設使用「@name」屬性的值。 當模式寫入資料庫時，會根據欄位類型自動添加前置詞。
* **模板（字串）**:此屬性定義對 `<attribute>` 由多個架構共用的元素。 定義將自動複製到當前架構中。
* **translatedDefault（字串）**:如果找到「@default」屬性，則「@translatedDefault」將允許您重新定義表達式以與在@default中定義的表達式相匹配，由轉換工具收集（內部使用）。
* **translatedExpr（字串）**:如果存在「@expr」屬性，則「@translatedExpr」屬性允許您重新定義表達式以匹配在@expr中定義的表達式，由轉換工具收集（內部使用）。
* **類型(MNTOKEN)**:的子菜單。

   欄位類型為泛型。 根據安裝的資料庫類型，Adobe Campaign將定義的類型更改為特定於在結構更新期間安裝的資料庫的值。

   可用類型清單：

   * 任意
   * 賓
   * blob
   * 布爾
   * 位元組
   * CDATA
   * 日期
   * 日期表
   * 日期
   * 日期
   * 雙
   * 枚舉
   * 浮
   * html
   * int64
   * 連結
   * 長
   * 備忘錄
   * MNTOKEN
   * 百分比
   * 主鍵
   * 短
   * 字串
   * 時間
   * 時隙
   * uuid

   如果「@type」屬性為空，則預設情況下，Adobe Campaign會將長度為100的字串(STRING)連結到欄位。

   如果欄位為STRING類型，且欄位名稱未由「@sqlname」屬性的存在指定，則資料庫中欄位的名稱將自動以「s」開頭。 此操作模式與INTEGER(i)、DOUBLE(d)和DATES(ts)類型欄位類似。

* **userEnum（字串）**:接收「open」枚舉的內部名稱。 枚舉的值可由介面中的用戶定義。
* **visibleIf（字串）**:定義XTK表達式形式的條件以顯示或隱藏屬性。

   >[!IMPORTANT]
   >
   >該屬性已隱藏，但仍然可以訪問其資料。

* **xml（布爾值）**:如果激活此選項，則欄位的值沒有連結的SQL欄位。 Adobe Campaign為記錄儲存建立文本類型「mData」欄位。 這表示這些欄位沒有篩選或排序。

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

使用「@datapolicy」聲明XML欄位：

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

帶&quot;@applicableIf&quot;的示例：僅當國家數量大於20時，才會建立「contains」屬性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

「@feature」為「shared」類型的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

「@feature」為「dedicated」類型的示例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
