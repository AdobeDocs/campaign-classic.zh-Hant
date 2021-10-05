---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '2012'
ht-degree: 0%

---

# 元素 {#element--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-4}

元素：==(屬性 | compute-string | dbindex |預設 |元素 |幫助 |加入 |鍵 | sysFilter | translatedDefault)

## 屬性 {#attributes-4}

_operation（字串）、advanced(boolean)、aggregate(string)、appliableIf(string)、autopk(boolean)、tellesTo(string)、convDate(string)、dataPolicy(string)、dataSource(string)、dbEnum(string)、defOnDuplicate(boolean)、desc(string)、displayAsField(boolean)、doesNotSupportDiff(boolen)、edit(string)、empty(string)、emptyKeyKeyEn(enum)、enum(en(enum)、en(emStringString)、enum(en(en(enum)、enum)SchemaTarget（字串）, expr（字串）, externalJoin(boolean), feature(string), featureDate(boolean), filterPath(string), folderLink(string), folderModel(string), fullLoad(boolean), hierarchPath(string), inout（字串）, integrity（字串）, label（字串）, labelSing(sing), length(length(sting), leng), leng), localablabereng(lacabeng), ler(lacalalable(locable), localled(localable), lonedNameng(locable), NARNEND索引鍵（布林值）、有序（布林值）、OVERFLOWTABLE（布林值）、PKSeQUENCE（字串）、PKGStatus（字串）、REF（字串）、必需（布林值）、REVAdvanced（布林值）、REVDESC（字串）、REVExtERNALJOIN（字串）、REVIntEGRITY（字串）、REVLaBEL（字串）、REVLink（字串）、REVTarget（字串）、REVViSIBLEIf（字串）、SQL（字串）、SQL(字串（字串）、SQL表)、SISIBLE(字串、SLEVISE（字串、SIBLE表）、STRE（STRING表）、STRING表、STRING表、STRING表、STRING表、SQLEX)SpaceIndex(STRING), TARGET(MNTOKEN)，範本(string), temporaryTable(boolean), translatedDefault(string), translatedExpr(string), type(MNTOKEN), unbound(boolean), user(boolean), userEnum(string), visibleIf(string), xml(boolean), xmlChildren(boolean)

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

Adobe Campaign中有四種類型的`<element>`元素：

* 根`<element>` :定義與架構匹配的SQL表的名稱。
* 結構`<element>` :定義`<element>`組   或   `<attribute>`    元素。
* 連結`<element>` :定義連結。 這些元素必須包含&quot;@type=link&quot;屬性。
* XML `<element>` :定義文字類型「mData」欄位。 此元素必須包含&quot;@type=xml&quot;屬性。

## 屬性說明 {#attribute-description-4}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴充現成可用的結構時。

   可存取的值包括：

   * &quot;none&quot;:單獨調解。 這表示Adobe Campaign將復原元素，而不會更新元素，或在不存在的情況下產生錯誤。
   * &quot;insertOrUpdate&quot;:更新為插入。 這表示Adobe Campaign將更新元素，或在元素不存在時加以建立。
   * &quot;insert&quot;:插入。 這表示Adobe Campaign將插入元素，而不會檢查元素是否存在。
   * &quot;update&quot;:更新。 這表示Adobe Campaign將更新元素，或在元素不存在時產生錯誤。
   * &quot;delete&quot;:刪除。 這表示Adobe Campaign將復原和刪除元素。

* **進階（布林值）**:啟用此選項時(@advanced=&quot;true&quot;)，它可讓您隱藏可用欄位清單上的屬性，這些欄位可用於配置表單中的清單。
* **匯總（字串）**:可讓您透過其他架構復 `<element>`  制的定義。此屬性會以「namespace:name」的形式接收架構聲明。
* **applicableIf（字串）**:條件。此屬性會接收XTK運算式。
* **autopk（布林值）**:如果啟用此選項(autopk=&quot;true&quot;)，則會自動定義唯一金鑰。此選項只能用於架構的主要元素。 警告：Adobe Campaign僅保證產生的金鑰是唯一的。 無法保證索引鍵值是連續和遞增的。
* **dataPolicy(string)**:允許對SQL欄位中允許的值指定批准約束。此屬性的值為：

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
* **預設值（字串）**:可讓您定義元素行為（呼叫函式、預設值）。此屬性會接收XTK運算式。
* **dsc（字串）**:可讓您插入元素的說明。此說明會顯示在介面的狀態列中。
* **displayAsField（布林值）**:如果激活了此屬性，則「連結」 `<element>`  類型將顯示為架構樹視圖（「結構」頁簽）中的欄位。這樣，可將連結顯示為本機欄位，並在查詢期間變更其行為。 在查詢的SELECT中找到元素時，將使用連結目標的值。 在查詢的WHERE中找到元素時，將會使用連結的基礎索引鍵。
* **編輯（字串）**:此屬性指定將以連結到架構的形式使用的輸入類型。
* **列舉（字串）**:接收連結到欄位的枚舉的名稱。枚舉可以插入到相同的架構或遠程架構中。
* **expr（字串）**:此屬性定義一個計算欄位，該欄位的定義不儲存在表中。它會接收Xpath或XTK（字串）運算式。
* **externalJoin（布林值）**:「連結」類型元素中的外部連接。
* **功能（字串）**:定義特徵欄位：這些欄位用於擴充現有表格中的資料，但會將資料儲存在附件表格中。接受的值為：

   * &quot;shared&quot;:內容儲存在每個資料類型的共用表中
   * &quot;dedicated&quot;:內容儲存在專用表中

   SQL特性表是根據特性類型自動建立的：

   * 專用：`Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 共用：`Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

   特徵欄位有兩種類型：在特徵上授權單個值的簡單欄位和多個選擇欄位，其中特徵被連結到可包含多個值的集合元素。

   在架構中定義特性時，此架構必須具有基於單一欄位的主鍵（未授權複合鍵）。

* **featureDate（布林值）**:連結到「@feature」特性欄位的屬性。如果其值為「true」，則可讓您找出值的上次更新時間。
* **filterPath(string)**:此屬性會接收Xpath，並可讓您在欄位上定義篩選器。
* **folderLink(string)**:此屬性會接收連結的名稱，可讓您復原包含實體的檔案。
* **folderModel(string)**:定義啟用實體儲存的資料夾類型。只有在出現「@folderLink」時，才會定義此屬性。
* **folderProcess(string)**:定義儲存實體模型實例的連結。只有在出現「@folderLink」時，才會定義此屬性。
* **fullLoad（布林值）**:在表單的欄位選擇期間，此屬性會強制顯示表格中的所有記錄。
* **img(string)**:接收連結到元素的影像的路徑。此屬性的值為「namespace:image name」類型。 例如：img=&quot;cus:myImage.jpg&quot;。 實際上，必須將映像導入應用程式伺服器。
* **完整性（字串）**:源表的出現對目標表的引用完整性。

   可存取的值包括：

   * &quot;define&quot;:如果透過連結參考Adobe Campaign，則不會刪除該實體
   * &quot;normal&quot;:刪除源出現時將初始化目標出現時的連結的密鑰（預設模式），此類型的完整性將初始化所有外鍵
   * &quot;own&quot;:刪除源事件會觸發刪除目標事件
   * &quot;owncopy&quot;:類似於「擁有」（若是刪除）或重複發生次數（若是重複）
   * &quot;中性&quot;:不執行任何動作

* **標籤（字串）**:元素標籤。
* **labelSingular（字串）**:介面某些部分中所使用元素的標籤（單數形式）。
* **length(string)**:max。為「字串」類型SQL欄位的值授權的字元數。
* **可本地化（布林值）**:如果已啟動，此屬性會告訴收集工具，以復原「@label」屬性的值，以供翻譯（內部使用）。
* **name(MNTOKEN)**:與表名稱匹配的元素的內部名稱。「@name」屬性的值必須是短的，最好是英文，並符合連結到XML的命名約束。

   當架構寫入資料庫時，前置詞會由Adobe Campaign自動新增至欄位名稱。

   * &quot;i&quot;:前置詞用於「整數」類型。
   * &quot;d&quot;:首碼表示&#39;double&#39;類型。
   * &quot;s&quot;:字元字串類型的前置詞。
   * &quot;ts&quot;:「date」類型的前置詞。

   要以自主方式定義表的名稱，必須在主架構元素的定義中使用「@sqltable」屬性。

* **noDbIndex（布林值）**:可讓您指定元素不會建立索引。
* **ordered（布林值）**:如果屬性已啟用(ordered=&quot;true&quot;),Adobe Campaign會將元素聲明序列保留在XML收集元素中。
* **pkSequence(string)**:接收用於計算自動增量密鑰的序列的名稱。只有在架構的根元素上定義了自動增量鍵時，才可使用此屬性。
* **pkgStatus(string)**:在套件匯出期間，值會作為此屬性值的函式來考量：

   * &quot;always&quot;:元素將始終存在
   * &quot;never&quot;:元素永遠不會存在
   * &quot;default（或無）&quot;:元素會匯出，除非它是預設元素，或它不是內部欄位，且與其他例項不相容

* **參考（字串）**:此屬性會定義由數個結構共用的>element>元素的參考（定義計分）。定義不會複製到目前的架構中。
* **必要（布林值）**:如果已啟用此屬性(@required=&quot;true&quot;)，介面中會反白顯示該欄位。欄位的標籤在表單中為紅色。
* **revAdvanced（布林值）**:啟動後，此屬性會指定相對的連結為「進階」連結。
* **revCardinality（字串）**:此屬性定義兩個表之間連結的基數。它用於「link」類型`<element>`。

   可能的值包括：

   * &quot;single&quot; :簡單的1-1類型連結
   * &quot;unbound&quot;:1-N類型集合連結

   依預設，如果建立連結期間未指定屬性，基數將為1-N。

* **revDesc（字串）**:此屬性接收連結到相反連結的說明。
* **revExternalJoin（布林值）**:激活後，此屬性可讓您強制外部連接到相反的連結上。
* **revIntegrity（字串）**:此屬性定義目標架構上的完整性。已授權與「@integrity」屬性相同的值。 依預設，Adobe Campaign會為此屬性提供「一般」值。
* **revLabel（字串）**:標籤。
* **revLink（字串）**:相對連結的名稱。如果值為&quot;_NONE_&quot;，則目標架構中不會建立相反的連結。
* **revTarget（字串）**:相對連結的目標。
* **sql（布林值）**:如果激活了此屬性(@sql=&quot;true&quot;)，則會強制儲存SQL元素，即使元素具有xml=&quot;true&quot;屬性亦然。
* **sqlname(string)**:表建立期間的欄位名稱。如果未指定&quot;@sqlname&quot;，預設會使用&quot;@name&quot;屬性的值。 將架構寫入表時，會根據欄位類型自動添加前置詞。
* **sqltable(string)**:對於架構的主要元素，此屬性將預設生成的SQL表的名稱重載。如果未指定「@sqltable」，則預設名稱的結構將如下所示：namespace（大寫字母），後跟SrcSchema的值「@name」。
* **tableSpace(string)**:此屬性允許您指定儲存表的表空間的新資料(在根上有 `<element>`效)。
* **tableSpaceIndex(string)**:此屬性用於為表指定新的索引儲存表空間(在根上有 `<element>`效)。
* **target(MNTOKEN)**:在表之間建立連結時接收目標架構的名稱。此屬性僅對「連結」類型元素作用中。
* **範本（字串）**:此屬性定義對由多個結 `<element>` 構共用的元素的引用。定義會自動複製到目前的架構中。
* **translatedDefault(string)**:如果找到「@default」屬性，則「@translatedDefault」可讓您重新定義運算式，以符合@default中定義的運算式，並由翻譯工具收集（內部使用）。
* **translatedExpr(string)**:如果找到「@expr」屬性，則「@translatedExpr」屬性可讓您重新定義與「@expr」中定義的屬性相符的運算式，該運算式將由翻譯工具收集（內部使用）。
* **類型(MNTOKEN)**:定義儲存在元素中的資料類型。

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

* **未綁定（布林值）**:如果已啟動屬性(unbound=&quot;true&quot;)，則會將連結聲明為1-N基數的集合元素。
* **userEnum(string)**:接收「開啟」枚舉的內部名稱。使用者可在介面中定義分項清單值。
* **xml（布林值）**:如果激活了此選項，則元素中定義的所有值都將儲存在TEXT類型「mData」欄位的XML中。這表示這些欄位將不會進行篩選或排序。
* **xmlChildren(boolean)**:強制儲存每個子代(  `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
