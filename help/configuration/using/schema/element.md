---
product: campaign
title: 架構元素和屬性 — 元素元素
description: 元素元素
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '2014'
ht-degree: 0%

---

# 元素元素 {#element--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-4}

元素：==(屬性 |計算字串 | dbindex |預設 |元素 |幫助 |加入 |鍵 | sysFilter |已轉換預設值)

## 屬性 {#attributes-4}

_operation(string)、advanced(boolean)、aggregate(string)、autopk(boolean)、leartsTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dbEnum(string)、defOnDuplicate(boolean)、defauault(string)、desc(sc(sc(st(string)、desc(string)、desc(sinc(sing)、dipdisplayDic(sc(sin)、displayAsAs)、displayAsAsAsAs欄位(boolean)、doesNotSupportDiff(boolean)、edit(string)、emptyKeyValue(string)、enum(string)、enumImage(string)、expandSchemaTarget(string)、expr(string)、externalJoin(boolean)、featureDate(bolean)、filterPath(string)、folean)、folderModel(string)、folderProcess(string)、fullLoad(boolean)、hiercialPath(string)、img(string)、inout(string)、完整性(string)、標籤(string)、labelSingular(string)、length(boolean)、noDbIndex(booolean)鍵（布爾型）、有序（布爾型）、overflowtable(boolean)、pkSequence(string)、pkgStatus(string)、ref(string)、required(boolean)、revAdvanced(boolean)、revCardinality(string)、revExternalJoin(boel)、revIntegrity(string)、revLabel(strity(stringlink(string)、revTarget(string)、revVisibleIf(string)、sql(boolean)、sqlname(string)、sqltable(string)、tableSpace(string)、tableSpaceIndex(string)、target(MNTOKEN)、template(string)、temporaryTable(boolean)、translatedDefault(string)、transledExpr(strationed(string)、transledExpr(string)、typeMNTOKEN)、未綁定（布爾）、user（布爾）、userEnum（字串）、visibleIf（字串）、xml（布爾）、xmlChildren（布爾）

## 父母 {#parents-4}

`<srcschema>`

`<element>`

## 兒童 {#children-4}

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

有四種類型 `<element>`  Adobe Campaign元素：

* 根 `<element>`  :定義與架構匹配的SQL表的名稱。
* 結構 `<element>`  :定義  `<element>`   或   `<attribute>`    元素。
* 連結 `<element>`  :定義連結。 此元素必須包括「@type=link」屬性。
* XML `<element>`  :定義文本類型「mData」欄位。 此元素必須包含「@type=xml」屬性。

## 屬性說明 {#attribute-description-4}

* **操作（字串）**:定義在資料庫中寫入的類型。

   此屬性主要用於擴展開箱模式。

   可訪問的值為：

   * &quot;無&quot;:單獨和解。 這意味著，Adobe Campaign將恢復元素，而不更新該元素，如果該元素不存在，則不生成錯誤。
   * &quot;insertOrUpdate&quot;:用插入更新。 這意味著Adobe Campaign將更新元素或在元素不存在時建立它。
   * &quot;插入&quot;:插入。 這意味著Adobe Campaign將插入元素，而不檢查它是否存在。
   * &quot;更新&quot;:更新。 這意味著Adobe Campaign將更新元素，或在元素不存在時生成錯誤。
   * &quot;刪除&quot;:刪除。 這意味著Adobe Campaign將恢復和刪除元素。

* **高級（布爾值）**:激活此選項(@advanced=&quot;true&quot;)時，它允許您隱藏可用欄位清單中的屬性，這些欄位可用於在表單中配置清單。
* **聚合（字串）**:允許您複製 `<element>`  通過另一個架構。 此屬性接收「namespace:name」形式的架構聲明。
* **appliatedIf（字串）**:用於應用索引的條件。 此屬性接收XTK表達式。
* **autopk（布爾值）**:如果激活此選項(autopk=&quot;true&quot;)，則將自動定義唯一鍵。 此選項只能用於架構的主元素。 警告，Adobe Campaign只保證生成的密鑰是唯一的。 不能保證關鍵值是連續的和增量的。
* **dataPolicy（字串）**:允許您對SQL欄位中允許的值指定批准約束。 此屬性的值為：

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
* **預設（字串）**:用於定義元素行為（調用函式，預設值）。 此屬性接收XTK表達式。
* **desc（字串）**:用於插入元素的說明。 此說明顯示在介面的狀態欄中。
* **displayAsField（布爾型）**:如果此屬性被激活，則為&quot;link&quot;類型 `<element>`  將在架構的樹視圖中顯示為欄位（「結構」頁籤）。 這樣，就可以將連結顯示為本地欄位，並在查詢期間更改其行為。 在查詢的SELECT中找到元素時，將使用連結目標的值。 在查詢的WHERE中找到元素時，將使用連結的基礎鍵。
* **編輯（字串）**:此屬性指定將以連結到架構的形式使用的輸入類型。
* **枚舉（字串）**:接收連結到該欄位的枚舉的名稱。 枚舉可以插入到同一架構或遠程架構中。
* **expr（字串）**:此屬性定義一個計算欄位，該欄位的定義不儲存在表中。 它接收Xpath或XTK（字串）表達式。
* **externalJoin（布爾型）**:「link」類型元素中的外部聯接。
* **特徵（字串）**:定義特徵欄位：這些欄位用於擴展現有表中的資料，但儲存在附件表中。 接受的值為：

   * &quot;共用&quot;:內容按資料類型儲存在共用表中
   * &quot;專用&quot;:內容儲存在專用表中

   SQL特徵表是根據特徵類型自動生成的：

   * 專用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   有兩種類型的特徵欄位：對特徵授權單個值的簡單欄位和多個選擇欄位，其中特徵被連結到可包含多個值的集合元素。

   在模式中定義特徵時，此模式必須具有基於單個欄位的主鍵（未授權複合鍵）。

* **featureDate（布爾型）**:連結到「@feature」特徵欄位的屬性。 如果其值為&quot;true&quot;，則允許您查找上次更新值的時間。
* **filterPath（字串）**:此屬性接收Xpath，並允許您在欄位上定義篩選器。
* **folderLink（字串）**:此屬性接收連結的名稱，用於恢復包含實體的檔案。
* **folderModel（字串）**:定義啟用實體儲存的資料夾類型。 僅當存在「@folderLink」時才定義此屬性。
* **folderProcess（字串）**:定義實體模型實例儲存的連結。 僅當存在「@folderLink」時才定義此屬性。
* **fullLoad（布爾型）**:此屬性強制在表單的欄位選擇期間顯示表中的所有記錄。
* **img（字串）**:接收連結到元素的影像的路徑。 此屬性的值為「namespace:image name」類型。 例如：img=&quot;cus:myImage.jpg&quot;。 物理上，必須將映像導入到應用程式伺服器。
* **完整性（字串）**:源表對目標表的出現的參照完整性。

   可訪問的值為：

   * &quot;define&quot;:Adobe Campaign不刪除通過連結引用的實體
   * &quot;正常&quot;:刪除源實例將初始化目標實例上連結的鍵（預設模式），此類完整性將初始化所有外鍵
   * &quot;own&quot;:刪除源事件會觸發刪除目標事件
   * &quot;owncopy&quot;:類似於&quot;own&quot;（刪除時）或重複（重複時）
   * &quot;中性&quot;:什麼也不做

* **標籤（字串）**:元素標籤。
* **labelSingular（字串）**:在介面的某些部分中使用的元素的標籤（奇異形式）。
* **長度（字串）**:最大。 為「字串」類型SQL欄位的值授權的字元數。
* **可本地化（布爾型）**:如果激活了該屬性，則此屬性將告訴收集工具恢復「@label」屬性的值以進行轉換（內部使用）。
* **名稱(MNTOKEN)**:與表名稱匹配的元素的內部名稱。 「@name」屬性的值必須短，最好是英文，並符合連結到XML的命名約束。

   當模式寫入資料庫時，前置詞由Adobe Campaign自動添加到欄位名。

   * 「i」：「integer」類型的前置詞。
   * &quot;d&quot;:「double」類型的前置詞。
   * &quot;s&quot;:字串類型的前置詞。
   * &quot;ts&quot;:「date」類型的前置詞。

   要以自主方式定義表的名稱，需要在主架構元素的定義中使用「@sqltable」屬性。

* **noDbIndex（布爾）**:用於指定將不為元素編製索引。
* **有序（布爾值）**:如果屬性被激活(ordered=&quot;true&quot;)，則Adobe Campaign將元素聲明序列保留在XML集合元素中。
* **pkSequence（字串）**:接收用於計算自動增量鍵的序列的名稱。 僅當在架構的根元素上定義了自動增量鍵時，才能使用此屬性。
* **pkgStatus（字串）**:在包導出過程中，值將作為此屬性值的函式被考慮：

   * &quot;always&quot;:元素將始終存在
   * &quot;從不&quot;:元素永遠不會出現
   * &quot;default（或nothing）&quot;:除非元素是預設元素，或者它不是內部欄位，並且與其他實例不相容，否則將導出該元素

* **ref（字串）**:此屬性定義對由多個架構共用的>element>元素的引用（定義分解）。 定義未複製到當前架構中。
* **必需（布爾型）**:如果激活了此屬性(@required=&quot;true&quot;)，則該欄位將在介面中突出顯示。 該欄位的標籤將以紅色顯示。
* **revAdvanced（布爾）**:激活後，此屬性指定相反的連結是「高級」連結。
* **revCardinality（字串）**:此屬性定義兩個表之間連結的基數。 它用於「連結」類型 `<element>`。

   可能的值為：

   * &quot;單一&quot;:簡單1-1類型連結
   * &quot;未綁定&quot;:1-N類型集合連結

   預設情況下，如果在建立連結時未指定屬性，則基數將為1-N。

* **revDesc（字串）**:此屬性接收連結到相反連結的說明。
* **revExternalJoin（布爾型）**:激活後，此屬性允許您強制外部連接到相反的連結上。
* **revIntegrity（字串）**:此屬性定義目標架構上的完整性。 與「@integrity」屬性相同的值被授權。 預設情況下，Adobe Campaign會為此屬性提供「normal」值。
* **revLabel（字串）**:的子菜單。
* **revLink（字串）**:相對連結的名稱。 如果值為&quot;_無_&quot;，在目標架構中將不建立相反的連結。
* **revTarget（字串）**:相反鏈路的目標。
* **sql（布爾型）**:如果此屬性被激活(@sql=&quot;true&quot;)，則會強制儲存SQL元素，即使該元素具有xml=&quot;true&quot;屬性。
* **sqlname（字串）**:建立表期間欄位的名稱。 如果未指定「@sqlname」，則預設使用「@name」屬性的值。 將模式寫入表時，會根據欄位類型自動添加前置詞。
* **sqltable（字串）**:對於架構的主要元素，此屬性將重載預設生成的SQL表的名稱。 如果未指定「@sqltable」，則預設名稱將按如下方式結構：命名空間（首字母大寫），後跟SrcSchema &quot;@name&quot;的值。
* **tableSpace（字串）**:此屬性用於為表指定新的資料儲存表空間（在根上有效） `<element>`)。
* **tableSpaceIndex（字串）**:此屬性用於為表指定新的索引儲存表空間（在根上有效） `<element>`)。
* **目標(MNTOKEN)**:在表之間建立連結時接收目標架構的名稱。 此屬性僅對「link」類型元素處於活動狀態。
* **模板（字串）**:此屬性定義對 `<element>` 由多個架構共用的元素。 定義將自動複製到當前架構中。
* **translatedDefault（字串）**:如果找到「@default」屬性，則「@translatedDefault」將允許您重新定義表達式以與在@default中定義的表達式相匹配，由轉換工具收集（內部使用）。
* **translatedExpr（字串）**:如果找到&quot;@expr&quot;屬性，則&quot;@translatedExpr&quot;屬性允許您重新定義與&quot;@expr&quot;中定義的表達式相匹配的表達式，該表達式將由轉換工具收集（內部使用）。
* **類型(MNTOKEN)**:定義儲存在元素中的資料類型。

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

* **未綁定（布爾型）**:如果已激活屬性(unbond=&quot;true&quot;)，則將連結聲明為1-N基數的集合元素。
* **userEnum（字串）**:接收「open」枚舉的內部名稱。 枚舉值可由用戶在介面中定義。
* **xml（布爾值）**:如果激活此選項，則元素中定義的所有值都以XML形式儲存在TEXT類型「mData」欄位中。 這意味著這些欄位將不進行篩選或排序。
* **xmlChildren（布爾型）**:強制儲存每個孩子( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
