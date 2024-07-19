---
product: campaign
title: 結構元素和屬性 — 元素元素
description: 元素元素
feature: Schema Extension
exl-id: 60f15ae5-b2bd-48f9-aa45-8f795a3071aa
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 0%

---

# 元素元素 {#element--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-4}

元素：==(屬性 | 計算字串 | dbindex | 預設 | 元素 | 說明 | 加入 | key | sysFilter | translatedDefault)

## 屬性 {#attributes-4}

_operation （字串）、advanced （布林值）、aggregate （字串）、applicateIf （字串）、autopk （布林值）、fallsTo （字串）、convDate （字串）、dataPolicy （字串）、dataSource （字串）、dbEnum （字串）、defOnDuplicate （布林值）、default （字串）、desc （字串）、displayAsField （布林值）、doesNotSupportDiff （布林值）、edit （字串）、empage （字串）、enum （字串）、enum （字串）、enumImage （字串） target （字串）、expr （字串）、externalJoin （布林值）、feature （字串）、featureDate （布林值）、filterPath （字串）、folderLink （字串）、folderModel （字串）、folderProcess （字串）、fullLoad （布林值）、hierarchical （布林值）、hierarchicalPath （字串）、img （字串）、inout （字串）、完整性（字串）、label （字串）、labelSingular （字串）、length （字串）、localizable （布林值）、name (布林值（布林值）、name (MNTOKEN)、NODbIndex （布林值）、NOKeY （布林值） 、OVERFLOWTABLE （布林值）、PKSeQUENCE （字串）、PKGStATUS （字串）、REF （字串）、REVAdVANCED （布林值）、REVCarDINALITY （字串）、REVDeSC （字串）、REVExTERNALJoIN （布林值）、REVIntEGRITY （字串）、REVLABEL （字串）、REVVisIBLEIf （字串）、SQL （布林值）、SQLNAME （字串）、SQLTABLE （字串）、TABLESpACE （字串）、TABLESpACEIndex （字串）、TARGET (MNING （字串）、TARGET (目標(MNNN TOKEN)、TEMPLATE（字串）、TEMPLATETABLE（布林值）、TRANSLATEDDefAULT（字串）、TRANSLATEDExPR（字串）、TYPE(MNTOKEN)、unbound（布林值）、user（布林值）、userEnum（字串）、visibleIf（字串）、xml（布林值）、xmlChildren（布林值）

## 父項 {#parents-4}

`<srcschema>`

`<element>`

## 子系 {#children-4}

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

Adobe Campaign中有四種型別的`<element>`元素：

* 根`<element>` ：定義符合結構描述的SQL資料表名稱。
* 結構`<element>` ：定義`<element>`的群組   或   `<attribute>`    元素。
* 連結`<element>` ：定義連結。 此元素必須包含「@type=link」屬性。
* XML `<element>` ：定義文字型別「mData」欄位。 此元素必須包含「@type=xml」屬性。

## 屬性說明 {#attribute-description-4}

* **_operation （字串）**：定義在資料庫中寫入的型別。

  此屬性主要用於擴充現成可用的結構描述。

  可存取的值包括：

   * &quot;none&quot;：僅調解。 這表示Adobe Campaign將會復原元素，而不會更新元素，如果元素不存在則會產生錯誤。
   * &quot;insertOrUpdate&quot;：以插入更新。 這表示Adobe Campaign將更新元素，或如果元素不存在則建立元素。
   * &quot;insert&quot;： insertion. 這表示Adobe Campaign會插入元素，而不檢查元素是否存在。
   * &quot;update&quot;：更新。 這表示Adobe Campaign將更新元素，如果元素不存在則會產生錯誤。
   * &quot;delete&quot;：刪除。 這表示Adobe Campaign將復原和刪除元素。

* **進階（布林值）**：啟動此選項時(@advanced=&quot;true&quot;)，它可讓您隱藏可用欄位清單上的屬性，以設定表單中的清單。
* **彙總（字串）**：可讓您透過其他結構描述複製`<element>`的定義。 此屬性會收到「namespace：name」形式的結構描述宣告。
* **applicableIf （字串）**：套用索引的條件。 此屬性會接收XTK運算式。
* **autopk （布林值）**：如果已啟動此選項(autopk=&quot;true&quot;)，將自動定義唯一金鑰。 此選項只能用於結構描述的主要元素。 警告，Adobe Campaign僅保證產生的索引鍵是唯一的。 不保證索引鍵值為連續和累加。
* **dataPolicy （字串）**：可讓您針對SQL欄位中允許的值指定核准限制。 此屬性的值為：

   * &quot;none&quot;：沒有值
   * &quot;smartCase&quot;：第一字母大寫
   * &quot;lowerCase&quot;：全部小寫
   * &quot;upperCase&quot;：全部大寫
   * &quot;email&quot;：電子郵件地址
   * &quot;phone&quot;：電話號碼
   * &quot;identifier&quot;：識別碼名稱
   * &quot;resIdentifier&quot;：檔案名稱

* **dbEnum （字串）**：接收「已關閉」列舉的內部名稱。 列舉值必須在`<srcschema>`中定義。
* **defOnDuplicate （布林值）**：如果此屬性已啟用，則在複製記錄時，預設值(在@default中定義)會自動重新套用至記錄。
* **預設（字串）**：可讓您定義元素行為（呼叫函式，預設值）。 此屬性會接收XTK運算式。
* **desc （字串）**：可讓您插入專案的說明。 此說明會顯示在介面的狀態列中。
* **displayAsField （布林值）**：如果啟動此屬性，「連結」型別`<element>`將顯示為結構描述樹狀檢視中的欄位（「結構」標籤）。 如此一來，就可將連結顯示為本機欄位，並可在查詢期間變更其行為。 在查詢的SELECT中找到元素時，將會使用連結目標的值。 在查詢的WHERE中找到元素時，將會使用連結的基礎索引鍵。
* **編輯（字串）**：此屬性會指定連結至結構描述的表單中將使用的輸入型別。
* **列舉（字串）**：接收連結至欄位的列舉名稱。 列舉可以插入相同結構描述或遠端結構描述中。
* **expr （字串）**：此屬性定義了沒有定義儲存在資料表中的計算欄位。 它會接收Xpath或XTK （字串）運算式。
* **externalJoin （布林值）**： &quot;link&quot;型別專案中的外部聯結。
* **功能（字串）**：定義特性欄位：這些欄位是用來擴充現有表格中的資料，但儲存於附件表格中。 接受的值包括：

   * &quot;shared&quot;：內容會根據資料型別儲存在共用表格中
   * &quot;dedicated&quot;：內容會儲存在專用表格中

  SQL特性表格是根據特性型別自動建置：

   * 專用： `Ft_[name_of_the_schema_containing_the_characteristic]_[name_of_the_characteristic]`
   * 已共用： `Ft_[type_of_key_of_the_schema_containing_the_characteristic]_[type_of_the_characteristic]`

  特性欄位有兩種型別：簡單欄位（單一值授權於特性）以及多選欄位（特性連結至可能包含數個值的收集要素）。

  在結構描述中定義特性時，此結構描述必須具有根據單一欄位的主要金鑰（複合金鑰未獲授權）。

* **featureDate （布林值）**：連結至「@feature」特性欄位的屬性。 若其值為「true」，則可讓您檢視上次更新值的時間。
* **filterPath （字串）**：此屬性會接收Xpath，並讓您在欄位上定義篩選器。
* **folderLink （字串）**：此屬性會接收連結的名稱，讓您復原包含實體的檔案。
* **folderModel （字串）**：定義啟用實體儲存的資料夾型別。 此屬性僅在出現「@folderLink」時定義。
* **folderProcess （字串）**：定義儲存實體模型執行個體的連結。 此屬性僅在出現「@folderLink」時定義。
* **fullLoad （布林值）**：在表單中選取欄位時，此屬性會強制顯示表格中的所有記錄。
* **img （字串）**：接收連結至專案的影像路徑。 此屬性的值為「namespace：image name」型別。 例如： img=&quot;cus：myImage.jpg&quot;。 實際上，必須將影像匯入應用程式伺服器。
* **完整性（字串）**：來源資料表指向目標資料表的出現參照完整性。

  可存取的值包括：

   * &quot;define&quot;：如果透過連結參照，Adobe Campaign不會刪除實體
   * &quot;normal&quot;：刪除來源出現位置會初始化目標出現位置上連結的索引鍵（預設模式），此型別的完整性會初始化所有外來索引鍵
   * &quot;own&quot;：刪除來源事件會觸發目標事件的刪除
   * &quot;owncopy&quot;：類似於&quot;own&quot; （若刪除）或重複發生次數（若重複）
   * &quot;neutral&quot;：不執行任何動作

* **標籤（字串）**：元素標籤。
* **labelSingular （字串）**：在介面的某些部分使用的元素標籤（單一形式）。
* **長度（字串）**：上限。 為「字串」型別SQL欄位的值授權的字元數。
* **localizable （布林值）**：如果啟用，此屬性會告訴收集工具復原「@label」屬性的值以供翻譯（內部使用）。
* **name (MNTOKEN)**：符合資料表名稱的元素內部名稱。 「@name」屬性的值必須很短，最好是英文，並符合連結至XML的命名限制。

  當結構描述寫入資料庫時，Adobe Campaign會自動將字首新增到欄位名稱中。

   * &quot;i&quot;： &#39;integer&#39;型別的前置詞。
   * &quot;d&quot;： &#39;double&#39;型別的前置詞。
   * 「s」：字元字串型別的前置詞。
   * &quot;ts&quot;： &#39;date&#39;型別的前置詞。

  若要以自主方式定義表格名稱，您必須在主要結構描述元素的定義中使用「@sqltable」屬性。

* **noDbIndex （布林值）**：可讓您指定不會為專案編制索引。
* **ordered （布林值）**：如果屬性已啟用(ordered=&quot;true&quot;)，Adobe Campaign會保留XML集合專案中的專案宣告順序。
* **pkSequence （字串）**：接收要用於計算自動增量金鑰的序列名稱。 只有在架構的根元素上定義了自動增量索引鍵時，才能使用此屬性。
* **pkgStatus （字串）**：在套件匯出期間，將會考量值作為這個屬性值的函式：

   * &quot;always&quot;：元素將永遠存在
   * &quot;never&quot;：元素絕不會出現
   * &quot;default (or nothing)&quot;：除非元素是預設元素，或不是內部欄位且與其他執行個體不相容，否則會匯出元素

* **ref （字串）**：此屬性會定義由數個結構描述共用之>element>元素的參考（定義分解）。 定義不會複製到目前的結構描述中。
* **必要（布林值）**：如果此屬性已啟用(@required=&quot;true&quot;)，介面中會反白顯示欄位。 欄位的標籤在表單中將為紅色。
* **revAdvanced （布林值）**：啟動時，此屬性會指定相反的連結是「進階」連結。
* **revCardinality （字串）**：此屬性定義兩個資料表之間連結的基數。 它用於「連結」型別`<element>`。

  可能的值包括：

   * &quot;single&quot; ：簡單的1-1型別連結
   * &quot;unbound&quot;： 1-N型別集合連結

  根據預設，如果在建立連結期間未指定屬性，基數將為1-N。

* **revDesc （字串）**：這個屬性會收到連結到相反連結的描述。
* **revExternalJoin （布林值）**：啟動時，此屬性可讓您在相反連結上強制外部聯結。
* **revIntegrity （字串）**：此屬性定義目標結構描述上的完整性。 會授權與「@integrity」屬性相同的值。 依預設，Adobe Campaign會為此屬性提供「正常」值。
* **revLabel （字串）**：相反連結的標籤。
* **revLink （字串）**：相反連結的名稱。 如果值為「_NONE_」，則不會在目的地結構描述中建立相反的連結。
* **revTarget （字串）**：相反連結的目標。
* **sql （布林值）**：如果此屬性已啟用(@sql=&quot;true&quot;)，即使元素具有xml=&quot;true&quot;屬性，也會強制儲存SQL元素。
* **sqlname （字串）**：資料表建立期間欄位的名稱。 如果未指定「@sqlname」，預設會使用「@name」屬性的值。 將結構描述寫入表格時，會根據欄位型別自動新增字首。
* **sqltable （字串）**：對於結構描述的主要專案，此屬性會多載預設產生的SQL資料表名稱。 如果未指定「@sqltable」，預設名稱的結構會如下所示：名稱空間（第一個字母大寫），後面接著SrcSchema的值「@name」。
* **tableSpace （字串）**：此屬性可讓您為資料表指定新的資料儲存表格空間（在根`<element>`上有效）。
* **tableSpaceIndex （字串）**：此屬性可讓您為資料表指定新的索引儲存空間表格空間（在根`<element>`上有效）。
* **目標(MNTOKEN)**：在資料表之間建立連結時，會收到目標結構描述的名稱。 此屬性僅對「連結」型別元素有效。
* **範本（字串）**：此屬性會定義數個結構描述共用之`<element>`元素的參考。 定義會自動複製到目前的結構描述中。
* **translatedDefault （字串）**：如果找到「@default」屬性，「@translatedDefault」可讓您重新定義運算式，以符合@default中定義的運算式，以由翻譯工具收集（內部使用）。
* **translatedExpr （字串）**：如果找到「@expr」屬性，則「@translatedExpr」屬性可讓您重新定義符合「@expr」中定義的運算式，並且此運算式將由翻譯工具（內部使用）收集。
* **type (MNTOKEN)**：定義儲存在元素中的資料型別。

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

* **未繫結（布林值）**：如果啟動屬性(unbound=&quot;true&quot;)，連結會宣告為1-N基數的集合元素。
* **userEnum （字串）**：接收「開啟」列舉的內部名稱。 列舉值可由使用者在介面中定義。
* **xml （布林值）**：如果已啟用此選項，則元素中定義的所有值都會儲存在TEXT型別「mData」欄位的XML中。 這表示這些欄位將不會進行篩選或排序。
* **xmlChildren （布林值）**：強制儲存每個子系( `<element>  or  <attribute>   ) of the   <element>    element in an XML document.   </element>  </attribute> </element>`
