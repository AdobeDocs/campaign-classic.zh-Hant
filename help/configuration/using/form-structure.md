---
product: campaign
title: 表單結構
description: 表單結構
feature: Application Settings
role: Data Engineer, Developer
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: e61f2b63-06d3-4b8c-867f-1c729176d2da
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '2398'
ht-degree: 0%

---

# 表單結構{#form-structure}



表單的描述是結構化XML檔案，它遵循表單結構描述&#x200B;**xtk：form**&#x200B;的語法。

輸入表單的XML檔案必須包含具有&#x200B;**名稱**&#x200B;和&#x200B;**名稱空間**&#x200B;屬性的`<form>`根專案，才能填入表單名稱和名稱空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

依預設，表單會與具有相同名稱和名稱空間的資料結構描述相關聯。 若要將表單與不同名稱建立關聯，請將`<form>`專案的&#x200B;**entity-schema**&#x200B;屬性設定為結構描述金鑰的名稱。 為了說明輸入表單的結構，讓我們使用「cus：recipient」範例結構描述介面：

```xml
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="Male" value="1"/>   
    <value name="female" label="Female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email address of recipient"/>
    <attribute name="birthDate" type="datetime" label="Date"/>
    <attribute name="gender" type="byte" label="Gender" enum="gender"/>
  </element>
</srcSchema>
```

根據範例結構的輸入表單：

![](assets/d_ncs_integration_form_exemple1.png)

```xml
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

編輯控制項的說明從`<form>`根專案開始。 在&#x200B;**`<input>`**&#x200B;元素中輸入編輯控制項，該元素具有&#x200B;**xpath**&#x200B;屬性，包含其結構描述中的欄位路徑。

編輯控制項會自動適應對應的資料型別，並使用結構描述中定義的標籤。

>[!NOTE]
>
>您可以將&#x200B;**label**&#x200B;屬性新增至`<input>`元素，以多載在其資料結構描述中定義的標籤：\
>`<input label="Email address" xpath="@name" />`

依預設，每個欄位都會顯示在一行上，並依據資料型別佔用所有可用空間。

## 格式 {#formatting}

控制項的版面配置看起來類似於HTML表格中使用的版面，可能會將控制項分割成數個欄、交錯元素或指定可用空間的佔用。 不過，請記住，格式僅可讓您以比例將區域分割；您無法指定物件的固定維度。

若要以兩欄顯示上述範例的控制項：

![](assets/d_ncs_integration_form_exemple2.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email"/>
  </container>
</form>
```

具有&#x200B;**colcount**&#x200B;屬性的&#x200B;**`<container>`**&#x200B;元素可讓您強制在兩個資料行上顯示子控制項。

控制項上的&#x200B;**colspan**&#x200B;屬性會將控制項擴充到其值中所輸入的資料行數目：

![](assets/d_ncs_integration_form_exemple3.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form> 
```

藉由填入&#x200B;**type=&quot;frame&quot;**&#x200B;屬性，容器會在&#x200B;**label**&#x200B;屬性中包含標籤的子控制項周圍新增框架：

![](assets/d_ncs_integration_form_exemple4.png)

```xml
<form name="recipient" namespace="cus">
  <container colcount="2" type="frame" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
</form>
```

可以使用&#x200B;**`<static>`**&#x200B;元素來格式化輸入表單：

![](assets/d_ncs_integration_form_exemple5.png)

```xml
<form name="recipient" namespace="cus">
  <static type="separator" colspan="2" label="General"/>
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email" colspan="2"/>
  <static type="help" label="General information about recipient with date of birth, gender, and email address." colspan="2"/>
</form>
```

具有&#x200B;**分隔符號**&#x200B;型別的&#x200B;**`<static>`**&#x200B;標籤可讓您新增分隔符號列，其標籤包含在&#x200B;**label**&#x200B;屬性中。

已使用帶有說明型別的`<static>`標籤新增說明文字。 已在&#x200B;**標籤**&#x200B;屬性中輸入文字的內容。

## 容器 {#containers}

容器可讓您將一組控制項分組。 它們由&#x200B;**`<container>`**&#x200B;元素表示。 上面用來格式化數欄的控制項。

`<container>`上的&#x200B;**xpath**&#x200B;屬性可讓您簡化子控制項的參考。 然後，控制項的參照會相對於父`<container>`元素。

不含「xpath」的容器範例：

```xml
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

將「xpath」新增至名為「location」的元素的範例：

```xml
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### 容器型別 {#types-of-container}

容器是用來建構複雜的控制項，使用一組格式化在頁面中的欄位。

#### 索引標籤容器 {#tab-container}

索引標籤容器會格式化可從索引標籤存取之頁面中的資料。

![](assets/d_ncs_integration_form_exemple6.png)

```xml
<container type="notebook">
  <container colcount="2" label="General">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location">
    …
  </container>
</container>
```

主要容器由&#x200B;**type=&quot;notebook&quot;**&#x200B;屬性定義。 標籤會在子容器中宣告，且標籤的標籤會從&#x200B;**label**&#x200B;屬性填入。

![](assets/d_ncs_integration_form_exemple7.png)

>[!NOTE]
>
>**style=&quot;down|up**（依預設）**&quot;**&#x200B;功能會強制將索引標籤垂直定位在控制項下方或上方。 此功能為選用。
>`<container style="down" type="notebook">  … </container>`

#### 圖示清單 {#icon-list}

此容器會顯示垂直圖示列，讓您選取要顯示的頁面。

![](assets/d_ncs_integration_form_exemple8.png)

```xml
<container type="iconbox">
  <container colcount="2" label="General" img="xtk:properties.png">
    <input xpath="@gender"/>
    <input xpath="@birthDate"/>
    <input xpath="@email" colspan="2"/>
  </container>
  <container colcount="2" label="Location" img="nms:msgfolder.png">
    …
  </container>
</container>
```

主要容器由&#x200B;**type=&quot;iconbox&quot;**&#x200B;屬性定義。 與圖示關聯的頁面會在子容器中宣告。 圖示的標籤是從&#x200B;**label**&#x200B;屬性填入。

頁面圖示是從`img="<image>"`屬性填入，其中`<image>`是對應至其索引鍵（由名稱和名稱空間組成，如&quot;xtk：properties.png&quot;）的影像名稱。

可從&#x200B;**[!UICONTROL Administration > Configuration > Images]**&#x200B;節點取得影像。

#### 可見度容器 {#visibility-container}

您可以透過動態條件遮罩一組控制項。

此範例說明「性別」欄位值之控制項的可見度：

```xml
<container type="visibleGroup" visibleIf="@gender=1">
  …
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  …
</container>
```

可見度容器是由屬性&#x200B;**type=&quot;visibleGroup&quot;**&#x200B;所定義。 **visibleIf**&#x200B;屬性包含可見性條件。

條件語法的範例：

* **visibleIf=&quot;@email=&#39;peter.martinezATneeolane.net&#39;&quot;**：測試字串型別資料的相等性。 比較值必須以引號括住。
* **visibleIf=&quot;@gender >= 1和@gender！= 2&quot;**：數值的條件。
* **visibleIf=&quot;@boolean1=true or @boolean2=false&quot;**：測試布林值欄位。

#### 正在啟用容器 {#enabling-container}

此容器可讓您啟用或停用動態條件中的一組資料。 停用控制項可防止編輯控制項。 下列範例說明如何從「性別」欄位的值啟用控制項：

```xml
<container type="enabledGroup" enabledIf="@gender=1">
  …
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  …
</container>
```

啟用容器是由&#x200B;**type=&quot;enabledGroup&quot;**&#x200B;屬性所定義。 **enabledIf**&#x200B;屬性包含啟用條件。

## 編輯連結 {#editing-a-link}

請記住，在資料結構中宣告的連結如下：

```xml
<element label="Company" name="company" target="cus:company" type="link"/>
```

連結在其輸入表單中的編輯控制項如下：

![](assets/d_ncs_integration_form_exemple9.png)

```xml
<input xpath="company"/>
```

可透過編輯欄位存取目標選擇。 預先輸入可協助輸入，以便從輸入的前幾個字元輕鬆找到目標元素。 然後搜尋會以目標結構描述中定義的&#x200B;**計算字串**&#x200B;為基礎。 如果結構描述在控制項中驗證後不存在，則會顯示即時目標建立的確認訊息。 確認會在目標表格中建立新記錄，並將其與連結建立關聯。

下拉式清單可用來從已建立的記錄清單中選取目標元素。

**[!UICONTROL Modify the link]** （資料夾）圖示會啟動包含目標元素清單和篩選區域的選擇表單：

![](assets/d_ncs_integration_form_exemple10.png)

**[!UICONTROL Edit link]** （放大鏡）圖示會啟動連結專案的編輯表單。 根據預設，使用的形式是在目標架構的索引鍵上推斷。 **表單**&#x200B;屬性可讓您強制使用編輯表單的名稱（例如&quot;cus：company2&quot;）。

您可以從輸入表單的連結定義中新增&#x200B;**`<sysfilter>`**&#x200B;元素，以限制目標元素的選擇：

```xml
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

您也可以使用&#x200B;**`<orderby>`**&#x200B;元素來排序清單：

```xml
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### 控制項屬性 {#control-properties}

* **noAutoComplete**：停用預先輸入（值為「true」）
* **createMode**：如果連結不存在，就會立即建立連結。 可能的值包括：

   * **none**：停用建立。 如果連結不存在，則會顯示錯誤訊息
   * **inline**：在編輯欄位中建立與內容的連結
   * **edition**：在連結上顯示編輯表單。 驗證表單時，資料會儲存（預設模式）

* **noZoom**：連結上沒有編輯表單（值為「true」）
* **表單**：多載目標專案的編輯表單

## 連結清單 {#list-of-links}

在資料結構描述中作為集合元素(unbound=&quot;true&quot;)輸入的連結必須透過清單，才能檢視與其相關聯的所有元素。

原則包含顯示已最佳化資料載入的連結元素清單（透過資料批次下載，僅在清單可見時執行）。

綱要中的集合連結範例：

```xml
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
…
</element>
```

清單的輸入形式如下：

![](assets/d_ncs_integration_form_exemple11.png)

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

清單控制項由&#x200B;**type=&quot;linklist&quot;**&#x200B;屬性定義。 清單路徑必須參照集合連結。

資料行是透過清單的&#x200B;**`<input>`**&#x200B;專案宣告。 **xpath**&#x200B;屬性參考目標結構描述中欄位的路徑。

具有標籤的工具列（在架構中的連結上定義）會自動放置在清單上方。

清單可透過&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕篩選，並設定為新增及排序欄。

**[!UICONTROL Add]**&#x200B;和&#x200B;**[!UICONTROL Delete]**&#x200B;按鈕可讓您新增和刪除連結上的集合元素。 依預設，新增元素會啟動目標架構的編輯表單。

在清單的&#x200B;**`<input>`**&#x200B;標籤上完成&#x200B;**zoom=&quot;true&quot;**&#x200B;屬性時，**[!UICONTROL Detail]**&#x200B;按鈕會自動新增：它可讓您啟動所選行的編輯表單。

載入清單時可套用篩選和排序：

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
  <orderBy>
    <node expr="@date" sortDesc="true"/>
  </orderBy>
</input>
```

### 關係表 {#relationship-table}

關係表格可讓您連結具有N-N基數的兩個表格。 關係表格僅包含兩個表格的連結。

因此，將元素新增至清單應可讓您從關係表格中的兩個連結之一完成清單。

結構描述中的關係表範例：

```xml
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

例如，我們以&quot;cus：recipient&quot;綱要的輸入表單開始。 清單必須顯示與服務訂閱的關聯，而且必須允許您透過選取現有服務來新增訂閱。

![](assets/d_ncs_integration_form_exemple12.png)

```xml
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

**xpathChoiceTarget**&#x200B;屬性可讓您從輸入的連結啟動選擇表單。 建立關係表記錄會自動更新目前收件者和所選服務的連結。

>[!NOTE]
>
>**xpathEditTarget**&#x200B;屬性可讓您強制編輯所輸入連結上選取的行。

### 清單屬性 {#list-properties}

* **noToolbar**：隱藏工具列（值為「true」）
* **toolbarCaption**：多載工具列標籤
* **toolbarAlign**：修改工具列的垂直或水準幾何（可能的值：「垂直」|「水準」）
* **img**：顯示與清單關聯的影像
* **表單**：多載目標專案的編輯表單
* **縮放**：新增&#x200B;**[!UICONTROL Zoom]**&#x200B;按鈕以編輯目標專案
* **xpathEditTarget**：在輸入的連結上設定編輯
* **xpathChoiceTarget**：若要新增此專案，請在輸入的連結上啟動選取表單

## 記憶體清單控制項 {#memory-list-controls}

記憶體清單可讓您使用清單資料預先載入來編輯集合元素。 無法篩選或設定此清單。

這些清單用於XML對應的收集要素或低容量連結。

### 欄清單 {#column-list}

此控制項會顯示可編輯的欄清單，其工具列包含新增和刪除按鈕。

![](assets/d_ncs_integration_form_exemple13.png)

```xml
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

清單控制項必須填入&#x200B;**type=&quot;list&quot;**&#x200B;屬性，而且清單的路徑必須參考集合專案。

資料行是在清單的子&#x200B;**`<input>`**&#x200B;標籤中宣告。 可以使用&#x200B;**label**&#x200B;和&#x200B;**colSize**&#x200B;屬性強制資料行標籤和大小。

>[!NOTE]
>
>將&#x200B;**ordered=&quot;true&quot;**&#x200B;屬性新增至資料結構描述中的集合元素時，會自動新增排序箭頭。

工具列按鈕可水準對齊：

![](assets/d_ncs_integration_form_exemple14.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

**toolbarCaption**&#x200B;屬性強制水準對齊工具列並輸入清單上方的標題。

#### 放大清單 {#zoom-in-a-list}

在清單中插入和編輯資料時，可在單獨的編輯表單中輸入。

![](assets/d_ncs_integration_form_exemple15.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true" zoomOnAdd="true">
  <input xpath="@label"/>
  <input xpath="@date"/>

  <form colcount="2" label="Event">
    <input xpath="@label"/>
    <input xpath="@date"/>
  </form>
</input>
```

從清單定義下的`<form>`元素完成編輯表單。 其結構與輸入表單的結構相同。 在清單的&#x200B;**`<input>`**&#x200B;標籤上完成&#x200B;**zoom=&quot;true&quot;**&#x200B;屬性時，會自動新增&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕。 此屬性可讓您啟動所選行的編輯表單。

>[!NOTE]
>
>新增&#x200B;**zoomOnAdd=&quot;true&quot;**&#x200B;屬性會強制在插入清單元素時呼叫編輯表單。

### 清單屬性 {#list-properties-1}

* **noToolbar**：隱藏工具列（值為「true」）
* **toolbarCaption**：多載工具列標籤
* **toolbarAlign**：修改工具列的位置（可能的值：「垂直」|「水準」）
* **img**：顯示與清單關聯的影像
* **表單**：多載目標專案的編輯表單
* **縮放**：新增&#x200B;**[!UICONTROL Zoom]**&#x200B;按鈕以編輯目標專案
* **zoomOnAdd**：啟動新增的編輯表單
* **xpathChoiceTarget**：若要新增此專案，請在輸入的連結上啟動選取表單

## 不可編輯的欄位 {#non-editable-fields}

若要顯示欄位並防止編輯它，請使用&#x200B;**`<value>`**&#x200B;標籤或完成&#x200B;**`<input>`**&#x200B;標籤上的&#x200B;**readOnly=&quot;true&quot;**&#x200B;屬性。

「性別」欄位範例：

![](assets/d_ncs_integration_form_exemple16.png)

```xml
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## 選項按鈕 {#radio-button}

選項按鈕可讓您從數個選項中進行選擇。 **`<input>`**&#x200B;標籤是用來列出可能的選項，而&#x200B;**checkedValue**&#x200B;屬性會指定與選項相關的值。

「性別」欄位範例：

```xml
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## 核取方塊 {#checkbox}

核取方塊會反映布林值狀態（是否選取）。 依預設，此控制項由「布林值」(true/false)欄位使用。 預設值為0或1的變數可以與此按鈕相關聯。 此值可透過&#x200B;**checkValue**&#x200B;屬性多載。

```xml
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## 分項清單 {#enumeration}

<!-- to be completed -->

## 導覽階層編輯 {#navigation-hierarchy-edit}

此控制項會在一組要編輯的欄位上建立樹狀結構。

要編輯的控制項會分組在樹狀結構控制項的&#x200B;**`<input>`**&#x200B;標籤下輸入的&#x200B;**`<container>`**&#x200B;中：

```xml
<input nolabel="true" type="treeEdit">
  <container label="Text fields">
    <input xpath="@text1"/>
    <input xpath="@text2"/>
  </container>
  <container label="Boolean fields">
    <input xpath="@boolean1"/>
    <input xpath="@boolean2"/>
  </container>
</input>
```

![](assets/d_ncs_integration_form_exemple18.png)

## 運算式欄位 {#expression-field}

運算式欄位會從運算式動態更新欄位；**`<input>`**&#x200B;標籤與&#x200B;**xpath**&#x200B;屬性搭配使用，以輸入要更新的欄位路徑以及包含更新運算式的&#x200B;**expo**&#x200B;屬性。

```xml
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## 表單的內容 {#context-of-forms}

執行輸入表單會初始化包含正在編輯之實體資料的XML檔案。 此檔案代表表單的內容，可當作工作區使用。

### 更新內容 {#updating-the-context}

若要修改表單的內容，請使用`<set expr="<value>" xpath="<field>"/>`標籤，其中`<field>`是目的地欄位，`<value>`是更新運算式或值。

`<set>`標籤的使用範例：

* **`<set expr="'Test'" xpath="/tmp/@test" />`**：將&#39;Test&#39;值放置在暫存位置/tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**：以&#39;Test&#39;值更新&#39;lastName&#39;屬性上的實體
* **`<set expr="true" xpath="@boolean1" />`**：將「boolean1」欄位的值設為「true」
* **`<set expr="@lastName" xpath="/tmp/@test" />`**：「lastName」屬性的內容更新

透過&#x200B;**`<enter>`**&#x200B;和&#x200B;**`<leave>`**&#x200B;標籤初始化和關閉表單時，可以更新表單的內容。

```xml
<form name="recipient" namespace="cus">
  <enter>
    <set…
  </enter>
  …
  <leave>
    <set…
  </leave>
</form>
```

>[!NOTE]
>
>`<enter>`和`<leave>`標籤可用於頁面（「notebook」和「iconbox」型別）的`<container>`。

### 運算式語言 {#expression-language-}

巨集語言可用於表單定義中，以執行條件測試。

如果運算式已驗證，**`<if expr="<expression>" />`**&#x200B;標籤會執行標籤下指定的指示：

```xml
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

與&#x200B;**`<error>`**&#x200B;標籤合併的&#x200B;**`<check expr="<condition>" />`**&#x200B;標籤會阻止表單驗證，且如果未滿足條件，會顯示錯誤訊息：

```xml
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

<!-- changer exemple par un exemple plus parlant. cf. vidéo validation 02:27. noter aussi l'attribut required dans l'exemple de la vidéo. -->

## 精靈 {#wizards}

助理會以頁面的形式引導您完成一組資料輸入步驟。 當您驗證表單時，輸入的資料會儲存。

助理具有下列結構：

```xml
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Assistant example" entity-schema="nms:recipient">
  <container title="Title of page 1" desc="Long description of page 1">
    <input xpath="@lastName"/>
    <input xpath="comment"/>
  </container>
  <container title="Title of page 2" desc="Long description of page 2">
    …
  </container>
  …
</form>
```

![](assets/d_ncs_integration_form_exemple19.png)

`<form>`元素上存在&#x200B;**type=&quot;wizard&quot;**&#x200B;屬性，可讓您定義表單建構中的助理模式。 這些頁面是從`<container>`個元素完成的，這些元素是`<form>`元素的子項。 頁面的`<container>`元素已填入標題的標題屬性和desc，以在頁面標題下顯示說明。 **[!UICONTROL Previous]**&#x200B;和&#x200B;**[!UICONTROL Next]**&#x200B;按鈕會自動新增，以允許在不同頁面之間瀏覽。

「**[!UICONTROL Finish]**」按鈕會儲存輸入的資料並關閉表單。

### SOAP方法 {#soap-methods}

SOAP方法執行可從頁面結尾的填入&#x200B;**`<leave>`**&#x200B;標籤啟動。

**`<soapcall>`**&#x200B;標籤包含方法的呼叫，並具有下列輸入引數：

```xml
<soapCall name="<name>" service="<schema>">
  <param  type="<type>" exprIn="<xpath>"/>  
  …
</soapCall>
```

服務的名稱及其實作結構描述是透過&#x200B;**`<soapcall>`**&#x200B;標籤的&#x200B;**名稱**&#x200B;和&#x200B;**服務**&#x200B;屬性輸入的。

輸入引數在&#x200B;**`<soapcall>`**&#x200B;標籤下的&#x200B;**`<param>`**&#x200B;專案上描述。

必須透過&#x200B;**type**&#x200B;屬性指定引數型別。 可能的型別如下：

* **字串**：字元字串
* **布林值**：布林值
* **位元組**： 8位元整數
* **short**： 16位元整數
* **long**： 32位元整數
* **short**： 16位元整數
* **double**：雙精確度浮點數
* **DOMElement**：元素型別節點

**exprIn**&#x200B;屬性包含要作為引數傳遞的資料的位置。

**範例**：

```xml
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param  type="DOMElement"    exprIn="/tmp/entityList"/>         
    <param  type="DOMElement"    exprIn="/tmp/choiceList"/>         
    <param  type="boolean"       exprIn="true"/>       
  </soapCall>
</leave>
```
