---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---


# 元素元素{#element--element}

## 內容模型{#content-model-4}

element:==(attribute) |計算字串 | dbindex |預設 |元素 |說明 |加入 |密鑰 | sysFilter | translatedDefault)

## 屬性{#attributes-4}

_operation(string)、advanced(boolean)、aggregate(string)、appabliedIf(string)、autopk(boolean)、tessTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dbEnum(string)、defOnDuplicate(booliple)、deate(string)、deac(s、de)、desc(stric(sting)、desc(string)、desc(string(string(string)、desc(string)、desc(string)、duce)、desc(string(sing)、desc(string)、displayAs)、displayAs)、displayAsAsDisplayAsfield(boolean)、doesNotSupportDiff(boolean)、edit(string)、emptyKeyValue(string)、enum(string)、enumImage(string)、expandSchemaTarget(string)、expr(string)、externalJoin(boolean)、featureDate(bate)、filterPath(s)、fulen)、filterPath(stringPh(string)、fonealPh(stingPath(string)、fone)、foryPh(string)、foreringPh(stringPh(string)、feringVen)、foleringPh(singLen)、folenFolenFolerLingLingLink(singL)、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hierarchicalPath(string)、img(string)、inout(string)、integrity(string)、labelSingular(string)、length(boolean)、name(boolean)、no索引鍵（布林）、有序（布林）、overflowtable（布林）、pkSequence(string)、pkgStatus(string)、ref(string)、revAdvanced（布林）、revCardinality(string)、revDesc(string)、revExternalJoin(boolean)、revIntegrity(string)、revLabel(string)、revLabel(string)、revStringlink(string)、revTarget(string)、revVisibleIf(string)、sql(boolean)、sqlname(string)、sqltable(string)、tableSpace(string)、tableSpaceIndex(string)、target(MNTOKEN)、temporaryTable(boolean)、translatedDefault(string)、translatedExpr(str(str(string)、type)、typestringExpr(string)、typeMNTOKEN)、未系結（布林）、user（布林）、userEnum（字串）、visibleIf（字串）、xml（布林）、xmlChildren（布林）

## 父代{#parents-4}

`<srcschema>`

`<element>`

## 子項{#children-4}

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

## 說明 {#description-4}

Adobe Campaign中有四種`<element>`元素：

* 根`<element>` :定義與方案匹配的SQL表的名稱。
* 結構`<element>` :定義`<element>`的群組   或   `<attribute>`    元素。
* 連結`<element>` :定義連結。 這些元素必須包含&quot;@type=link&quot;屬性。
* XML `<element>` :定義「mData」文字類型欄位。 此元素必須包含&quot;@type=xml&quot;屬性。

## 屬性說明{#attribute-description-4}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴展現成可用的架構。

   可存取的值包括：

   * 「無」:和解。 這表示Adobe Campaign將會復原元素，而不會更新元素，或在元素不存在時產生錯誤。
   * &quot;insertOrUpdate&quot;:使用插入進行更新。 這表示Adobe Campaign會更新元素，或在元素不存在時建立元素。
   * 「插入」:插入。 這表示Adobe Campaign將插入元素，而不檢查元素是否存在。
   * 「更新」:更新。 這表示Adobe Campaign會更新元素，或在元素不存在時產生錯誤。
   * 「刪除」:刪除。 這表示Adobe Campaign將會復原和刪除元素。

* **進階（布林值）**:啟用此選項(@advanced=&quot;true&quot;)時，它可讓您隱藏可用欄位清單中的屬性，這些欄位可用來設定表單中的清單。
* **aggregate(string)**:可讓您透過其他架構復 `<element>`  制定義。此屬性接收「namespace:name」形式的架構聲明。
* **appliableIf（字串）**:條件。此屬性接收XTK表達式。
* **autopk（布林值）**:如果此選項已啟用(autopk=&quot;true&quot;)，則會自動定義唯一金鑰。此選項只能用於架構的主要元素。 警告，Adobe Campaign只保證產生的金鑰是唯一的。 不保證密鑰值是連續的和增量的。
* **dataPolicy（字串）**:可以為SQL欄位中允許的值指定批准約束。此屬性的值為：

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
* **default(string)**:可讓您定義元素行為（對函式的呼叫，預設值）。此屬性接收XTK表達式。
* **desc（字串）**:可讓您插入元素的說明。此說明顯示在介面的狀態欄中。
* **displayAsField（布林值）**:如果激活了此屬性，則「連結」類 `<element>`  型將在結構樹視圖（「結構」頁籤）中顯示為欄位。這樣，就可以將連結顯示為本機欄位，並在查詢期間變更其行為。 在查詢的SELECT中找到元素時，將使用連結目標的值。 在查詢的WHERE中找到元素時，將使用連結的基礎鍵。
* **edit(string)**:此屬性指定將以連結到方案的形式使用的輸入類型。
* **列舉（字串）**:接收連結到欄位的枚舉的名稱。枚舉可以插入到同一模式或遠程模式中。
* **expr（字串）**:此屬性定義一個計算欄位，該欄位的定義不儲存在表中。它接收Xpath或XTK（字串）運算式。
* **externalJoin（布林值）**:「連結」類型元素中的外部連結。
* **功能（字串）**:定義特徵欄位：這些欄位用於擴展現有表中的資料，但儲存在附件表中。接受的值為：

   * 「共用」:內容儲存在每個資料類型的共用表格中
   * 「專用」:內容儲存在專用表格中

   SQL特徵表是根據特徵類型自動構建的：

   * 專屬：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特徵欄位有兩種類型：其中在特徵上授權單一值的簡單欄位，以及在多個選擇欄位中，特徵連結至可包含數個值的收集元素。

   在模式中定義特徵時，此模式必須具有基於單個欄位的主鍵（組合鍵未授權）。

* **featureDate（布林值）**:屬性連結至「@feature」特徵欄位。如果其值為&quot;true&quot;，則可讓您瞭解值上次更新的時間。
* **filterPath（字串）**:此屬性會接收Xpath，並讓您在欄位上定義篩選。
* **folderLink（字串）**:此屬性接收連結的名稱，該名稱允許您恢復包含實體的檔案。
* **folderModel(string)**:定義啟用實體儲存的資料夾類型。僅當存在&quot;@folderLink&quot;時才定義此屬性。
* **folderProcess（字串）**:定義實體模型實例儲存所在的連結。僅當存在&quot;@folderLink&quot;時才定義此屬性。
* **fullLoad（布林值）**:此屬性強制在表單的欄位選擇期間顯示表中的所有記錄。
* **img(string)**:接收連結至元素的影像路徑。此屬性的值為&quot;namespace:image name&quot;類型。 例如：img=&quot;cus:myImage.jpg&quot;。 實際上，映像必須導入到應用程式伺服器。
* **完整性（字串）**:源表對目標表的出現的參照完整性。

   可存取的值包括：

   * 「定義」:如果透過連結參考實體，Adobe Campaign不會將其刪除
   * 「正常」:刪除源實例將初始化目標實例上連結的鍵（預設模式），此類型的完整性將初始化所有外鍵
   * 「擁有」:刪除源實例會觸發刪除目標實例
   * 「下載」:類似「擁有」（若是刪除）或重複發生次數（若是重複）
   * 「中性」:不做任何事

* **標籤（字串）**:元素標籤。
* **labelSingular(string)**:介面的某些部分中使用的元素的標籤（奇異形式）。
* **長度（字串）**:max.為「字串」類型SQL欄位的值授權的字元數。
* **可定位（布林值）**:如果已激活，此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:與表名稱匹配的元素的內部名稱。「@name」屬性的值必須是短的，最好是英文，並符合連結至XML的命名限制。

   當架構寫入資料庫時，Adobe Campaign會自動將字首新增至欄位名稱。

   * 「i」:前置詞。
   * &quot;d&quot;:首碼。
   * &quot;s&quot;:首碼。
   * &quot;ts&quot;:首碼。

   要以自治方式定義表的名稱，需要在主模式元素的定義中使用&quot;@sqltable&quot;屬性。

* **noDbIndex（布林值）**:可讓您指定元素不會建立索引。
* **有序（布林值）**:如果屬性已啟用(ordered=&quot;true&quot;),Adobe Campaign會將元素宣告順序保留在XML收集元素中。
* **pkSequence（字串）**:接收用於計算自動增量密鑰的序列的名稱。僅當在方案的根元素上定義了自動增量鍵時，才可以使用此屬性。
* **pkgStatus（字串）**:在包導出過程中，值將作為此屬性值的函式被考慮：

   * 「always」:元素將永遠存在
   * 「永不」:元素永遠不會出現
   * &quot;default（或nothing）&quot;:元素會匯出，除非它是預設元素，或者它不是內部欄位，而且與其他例項不相容

* **ref(string)**:此屬性定義對由多個結構（定義分解）共用的>element>元素的引用。定義不會複製到目前的架構中。
* **必要（布林值）**:如果此屬性已啟用(@required=&quot;true&quot;)，則介面中會反白顯示此欄位。欄位的標籤在表單中會顯示為紅色。
* **revAdvanced（布林值）**:啟用時，此屬性指定相反的連結為「進階」連結。
* **revCardinality（字串）**:此屬性定義兩個表之間連結的基數。它用於&quot;link&quot;類型`<element>`。

   可能的值包括：

   * 「單一」:簡單1-1類型連結
   * 「未系結」:1-N類型系列連結

   依預設，如果在建立連結時未指定屬性，基數會是1-N。

* **revDesc（字串）**:此屬性接收連結到相反連結的說明。
* **revExternalJoin（布林值）**:啟動後，此屬性可讓您在相反的連結上強制外部連接。
* **revIntegrity(string)**:此屬性定義目標方案上的完整性。授權的值與「@integrity」屬性相同。 依預設，Adobe Campaign會為此屬性提供「一般」值。
* **revLabel（字串）**:標籤。
* **revLink（字串）**:相反連結的名稱。如果值為&quot;_NONE_&quot;，則目標模式中將不建立相反的連結。
* **revTarget（字串）**:目標。
* **sql（布林值）**:如果此屬性被激活(@sql=&quot;true&quot;)，則會強制儲存SQL元素，即使該元素具有xml=&quot;true&quot;屬性。
* **sqlname（字串）**:表建立期間的欄位名稱。如果未指定&quot;@sqlname&quot;，則預設情況下會使用&quot;@name&quot;屬性的值。 將模式寫入表時，會根據欄位類型自動添加前置詞。
* **sqltable（字串）**:對於方案的主要元素，此屬性會過載預設生成的SQL表的名稱。如果未指定&quot;@sqltable&quot;，則預設名稱將按如下結構化：namespace（字母大寫），後面跟著SrcSchema &quot;@name&quot;的值。
* **tableSpace（字串）**:此屬性用於為表指定儲存表空間的新資料(在根上有 `<element>`效)。
* **tableSpaceIndex(string)**:此屬性用於為表指定新的索引儲存表空間(在根上有 `<element>`效)。
* **target(MNTOKEN)**:在表之間建立連結時接收目標方案的名稱。此屬性僅對&quot;link&quot;類型元素處於活動狀態。
* **範本（字串）**:此屬性定義對由多個方案 `<element>` 共用的元素的引用。定義會自動複製到當前模式。
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
* **userEnum（字串）**:接收&quot;open&quot;枚舉的內部名稱。枚舉值可由用戶在介面中定義。
* **xml（布林值）**:如果啟用此選項，元素中定義的所有值都會以XML格式儲存在TEXT類型&quot;mData&quot;欄位中。這表示這些欄位將不會進行篩選或排序。
* **xmlChildren（布林值）**:強制儲存每個子系(  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
