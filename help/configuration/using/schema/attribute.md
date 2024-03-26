---
product: campaign
title: 元素和屬性 — 屬性元素
description: 元素和屬性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: e4d34f56-b065-4dce-8974-11dc2767873a
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '1558'
ht-degree: 0%

---

# attribute element {#attribute--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model}

attribute：==help

## 屬性 {#attributes}

_operation （字串）、advanced （布林值）、applicatedIf （字串）、autoIncrement （布林值）、fallsTo （字串）、dataPolicy （字串）、dbEnum （字串）、defOnDuplicate （布林值）、default （字串）、desc （字串）、edit （字串）、enum （字串）、expr （字串）、featureDate （布林值）、img （字串）、inout （字串）、label （字串）、length （字串）、localizable （布林值）、name (MNTOKEN)、notNull （布林值）、pkgstatus （字串） ref)、ref（字串）、required（布林值）、sql（布林值）、sqlDefault（字串）、sqlname（字串）、sqltable（字串）、target(MNTOKEN)、template（字串）、translatedDefault（字串）、translatedExpr（字串）、type(MNTOKEN)、user（布林值）、userEnum（字串）、visibleIf（字串）、xml（布林值）

## 父項 {#parents}

`<element>`

## 子系 {#children}

`<help>`

## 說明 {#description}

`<attribute>` 元素可讓您定義資料庫中的欄位。

## 使用與使用內容 {#use-and-context-of-use}

`<attribute>` 元素必須在 `<element>` 元素。

順序 `<attribute>` 元素是在 `<srcschema>` 不會影響資料庫中的欄位建立順序。 建立序列將按字母順序排列。

## 屬性說明 {#attribute-description}

* **操作（字串）(_O)**：定義資料庫中的寫入型別。

  此屬性主要用於擴充現成可用的結構描述。

  可存取的值包括：

   * &quot;none&quot;：僅調解。 這表示Adobe Campaign將會復原元素，而不會更新元素，如果元素不存在則會產生錯誤。
   * &quot;insertOrUpdate&quot;：以插入更新。 這表示Adobe Campaign將更新元素，或如果元素不存在則建立元素。
   * &quot;insert&quot;： insertion. 這表示Adobe Campaign會插入元素，而不檢查元素是否存在。
   * &quot;update&quot;：更新。 這表示Adobe Campaign將更新元素，如果元素不存在則會產生錯誤。
   * &quot;delete&quot;：刪除。 這表示Adobe Campaign將復原和刪除元素。

* **進階（布林值）**：啟動此選項時(@advanced=&quot;true&quot;)，您可以在可用於設定表單清單的可用欄位清單上隱藏屬性。
* **appliedIf （字串）**：此屬性可讓您將欄位設為選用欄位。 此 `<attribute>` 遵循限制時，更新資料庫時將考慮元素。 &quot;applicableIf&quot;會收到XTK運算式。
* **autoIncrement （布林值）**：如果已啟用此選項，欄位會成為計數器。 這可讓您增加值（多為ID）。 （外部使用）
* **fallsTo （字串）**：採用共用欄位的表格的名稱和名稱空間，並填入宣告屬性的結構描述。 (僅用於 `<schema>`)。
* **dataPolicy （字串）**：可讓您針對SQL或XML欄位中允許的值指定核准限制。 此屬性的值為：

   * &quot;none&quot;：沒有值
   * &quot;smartCase&quot;：第一字母大寫
   * &quot;lowerCase&quot;：全部小寫
   * &quot;upperCase&quot;：全部大寫
   * &quot;email&quot;：電子郵件地址
   * &quot;phone&quot;：電話號碼
   * &quot;identifier&quot;：識別碼名稱
   * &quot;resIdentifier&quot;：檔案名稱

* **dbEnum （字串）**：接收「已關閉」分項清單的內部名稱。 列舉值必須在 `<srcschema>`.
* **defOnDuplicate （布林值）**：如果此屬性已啟用，在複製記錄時，預設值(在@default中定義)會自動重新套用至記錄。
* **預設（字串）**：可讓您定義預設欄位的值（呼叫函式、預設值）。 此屬性會接收XTK運算式。
* **desc （字串）**：可讓您插入屬性的說明。 此說明會顯示在介面的狀態列中。
* **編輯（字串）**：此屬性會指定連結至結構描述的表單中將使用的輸入型別。
* **列舉（字串）**：接收連結至欄位的列舉名稱。 列舉可以插入相同結構描述或遠端結構描述中。
* **expr （字串）**：定義欄位預先計算運算式。 此屬性會接收Xpath或XTK運算式。
* **功能（字串）**：定義特性欄位：這些欄位用於擴充現有表格中的資料，但可儲存於附件表格中。 接受的值包括：

   * &quot;shared&quot;：內容會根據資料型別儲存在共用表格中
   * &quot;dedicated&quot;：內容會儲存在專用表格中

  SQL特性表格是根據特性型別自動建置：

   * 專用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 已共用： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  有兩種特性欄位：簡單oà¹單一值授權於特性的欄位，以及oà¹多選欄位，特性連結至可能包含數個值的收集要素。

  在結構描述中定義特性時，此結構描述必須具有根據單一欄位的主要金鑰（複合金鑰未獲授權）。

* **featureDate （布林值）**：連結至「@feature」特性欄位的屬性。 若其值為「true」，則可讓您檢視上次更新值的時間。
* **img （字串）**：可讓您定義連結至欄位之影像的路徑（名稱空間+影像名稱）（範例： img=&quot;cus：mypicture.jpg&quot;）。 實際上，必須將影像匯入應用程式伺服器。
* **標籤（字串）**：連結至欄位的標籤，通常會送給介面中的使用者。 它可讓您避免命名限制。
* **length （字串）**：最大值 「字串」型別SQL欄位值的字元數。 如果未指定「@length」屬性，Adobe Campaign會自動建立255個字元的欄位。
* **可本地化（布林值）**：如果已啟動，此屬性會告訴收集工具復原「@label」屬性的值以供翻譯（內部使用）。
* **名稱(MNTOKEN)**：與表格中欄位名稱相符的屬性名稱。 「@name」屬性的值必須很短，最好是英文，並符合XML命名限制。

  當結構描述寫入資料庫時，Adobe Campaign會自動將字首新增到欄位名稱中：

   * &quot;i&quot;： &#39;integer&#39;型別的前置詞。
   * &quot;d&quot;： &#39;double&#39;型別的前置詞。
   * 「s」：字元字串型別的前置詞。
   * &quot;ts&quot;： &#39;date&#39;型別的前置詞。

  若要完整定義表格中的欄位名稱，請在定義屬性時使用「@sqlname」選項。

* **notNull （布林值）**：可讓您重新定義Adobe Campaign有關管理資料庫中NULL記錄的行為。 依預設，數值欄位不是Null，字串和日期型別欄位可以是Null。
* **pkgStatus （字串）**：在套件匯出期間，會根據「@pkgStatus」的值考慮值：

   * &quot;always&quot;：永遠存在
   * &quot;never&quot;：永遠不存在
   * &quot;default (or nothing)&quot;：會匯出值，除非這是預設值或不是與其他執行個體不相容的內部欄位。

* **ref （字串）**：此屬性會定義 `<attribute>` 由數個結構描述共用的元素（定義分解）。 定義不會複製到目前的結構描述中。
* **必要（布林值）**：如果此屬性已啟用(@required=&quot;true&quot;)，介面中會醒目提示欄位。 欄位的標籤在表單中將為紅色。
* **sql （布林值）**：如果此屬性已啟用(@sql=&quot;true&quot;)，則會強制儲存SQL屬性，即使包含屬性的元素具有xml=&quot;true&quot;屬性亦然。
* **sqlDefault （字串）**：此屬性可讓您定義在啟動@notNull屬性時用於更新資料庫的預設值。 如果在屬性建立後新增此屬性，即使對於新記錄，結構描述行為也不會變更。 若要變更結構描述並更新新記錄的值，您需要刪除並再次建立屬性。
* **sqlname （字串）**：建立表格時欄位的。 如果未指定@sqlname，預設會使用「@name」屬性的值。 在資料庫中寫入結構描述時，會根據欄位型別自動新增字首。
* **範本（字串）**：此屬性會定義 `<attribute>` 由數個結構描述共用的元素。 定義會自動複製到目前的結構描述中。
* **translatedDefault （字串）**：如果找到「@default」屬性，「@translatedDefault」可讓您重新定義運算式，以符合@default中定義的運算式，由翻譯工具（內部使用）收集。
* **translatedExpr （字串）**：如果存在「@expr」屬性，「@translatedExpr」屬性可讓您重新定義運算式，以符合@expr中定義的運算式，由翻譯工具（內部使用）收集。
* **型別(MNTOKEN)**：欄位型別。

  欄位型別是一般型別。 根據所安裝的資料庫型別，Adobe Campaign會將定義的型別變更為結構更新期間所安裝資料庫的特定值。

  可用型別清單：

   * 任何
   * 紙匣
   * blob
   * 布林值
   * 位元組
   * CDATA
   * 日期時間
   * datetimetz
   * datetimenotz
   * 日期
   * 雙精度浮點數
   * 列舉
   * 浮點數
   * html
   * int64
   * 連結
   * 長
   * 備忘錄
   * MNTOKEN
   * 百分比
   * 主要金鑰
   * 短
   * 字串
   * 時間
   * 時間範圍
   * uuid

  如果「@type」屬性留空，Adobe Campaign預設會將長度為100的字元字串（字串）連結至欄位。

  如果欄位為STRING型別，且欄位名稱未以「@sqlname」屬性的存在來指定，則資料庫中欄位名稱的前面會自動加上「s」。 此作業模式與INTEGER (i)、DOUBLE (d)和DATES (ts)型別欄位類似。

* **userEnum （字串）**：接收「開啟」分項清單的內部名稱。 分項清單的值可由使用者在介面中定義。
* **visibleIf （字串）**：以XTK運算式的形式定義條件，以顯示或隱藏屬性。

  >[!IMPORTANT]
  >
  >屬性已隱藏，但仍可存取其資料。

* **xml （布林值）**：如果已啟用此選項，則欄位的值不會有連結的SQL欄位。 Adobe Campaign會建立文字型別「mData」欄位以儲存記錄。 這表示這些欄位沒有篩選或排序功能。

### 範例 {#examples}

值儲存在資料庫中的列舉值範例：

```
    <enumeration name="myEnum">
       <value name="One" value="1"/>
       <value name="Two" value="2"/>
    </enumeration>

    <element label="Sample" name="Sample">
       <attribute dbEnum="myEnum" length="100" name="Number" required="true" type="string"/>
    </element>     
```

具有「@datapolicy」的XML欄位宣告：

```
<attribute dataPolicy="phone" desc="Mobile number" label="Mobile"
     length="32" name="mobilePhone" sqlname="sMobilePhone" type="string"/>
```

具有「@applicableIf」的範例：只有在國家/地區數量大於20時，才會建立「contains」屬性。

```
<attribute length="100" name="Continent" type="string" applicableIf="@country > 20"/>
```

「共用」型別的「@feature」範例：

```
<attribute name="field1" label="Field 1" type="long" feature="shared"/>
<attribute name="field1" label="Field 1" type="long" feature="shared" sqlname="126" sqltable="Ft_Content_Long"/>
```

「dedicated」型別的「@feature」範例：

```
<attribute name="field1" label="Field 1" type="long" feature="dedicated"/>
<attribute name="field1" label="Field 1" type="long" feature="dedicated" sqlname="sField1" sqltable="Ft_recipient_field1"/>
```
