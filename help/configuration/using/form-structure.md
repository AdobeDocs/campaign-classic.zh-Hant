---
product: campaign
title: 表單結構
description: 表單結構
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
exl-id: e61f2b63-06d3-4b8c-867f-1c729176d2da
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '2385'
ht-degree: 0%

---

# 表單結構{#form-structure}



表單的描述是一種結構化XML文檔，它會觀察表單架構的語法 **xtk:form**.

輸入表單的XML文檔必須包含 `<form>` 根元素與 **名稱** 和 **命名空間** 屬性來填入表單名稱和命名空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

依預設，表單會與具有相同名稱和命名空間的資料架構相關聯。 若要將表單與不同名稱建立關聯，請設定 **實體綱要** 屬性 `<form>` 元素到綱要索引鍵的名稱。 若要說明輸入表單的結構，請讓我們使用「cus:recipient」範例結構來說明介面：

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

以範例結構為基礎的輸入表單：

![](assets/d_ncs_integration_form_exemple1.png)

```xml
<form name="recipient" namespace="cus">
  <input xpath="@gender"/>
  <input xpath="@birthDate"/>
  <input xpath="@email"/>
</form>
```

編輯控制項的說明從 `<form>` 根元素。 在 **`<input>`** 元素搭配 **xpath** 屬性，包含其架構中欄位的路徑。

編輯控制項會自動適應對應的資料類型，並使用架構中定義的標籤。

>[!NOTE]
>
>您可以借由新增 **標籤** 屬性 `<input>` 元素：\
>`<input label="Email address" xpath="@name" />`

依預設，每個欄位會顯示在單一行上，並根據資料類型佔據所有可用空間。

## 格式 {#formatting}

控制項的佈局類似於在HTML表中使用的佈局，可將控制項分成多列、交錯元件或指定佔用可用空間。 但請記住，格式設定只能讓您將區域按比例劃分；不能為對象指定固定維。

要以兩列顯示上述示例的控制項：

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

此 **`<container>`** 元素搭配 **count** 屬性可讓您強制將子項控制項顯示到兩欄。

此 **colspan** 控制項上的屬性將控制項擴展為輸入值中輸入的列數：

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

填入 **type=&quot;frame&quot;** 屬性，則容器在子控制項周圍添加框架，標籤包含在 **標籤** 屬性：

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

A **`<static>`** 元素可用來格式化輸入表單：

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

此 **`<static>`** 標籤 **分隔符號** 類型可讓您新增分隔符號列，並加上 **標籤** 屬性。

已使用 `<static>` 標籤。 文字的內容會在 **標籤** 屬性。

## 容器 {#containers}

容器可讓您將一組控制項分組。 它們由 **`<container>`** 元素。 上方用來設定數欄之控制項的格式。

此 **xpath** 屬性 `<container>` 可讓您簡化子控制項的參考。 然後，控制項的引用相對於父項 `<container>` 元素。

不含「xpath」的容器範例：

```xml
<container colcount="2">
  <input xpath="location/@zipCode"/>
  <input xpath="location/@city"/>
</container>
```

在名為「location」的元素中新增「xpath」的範例：

```xml
<container colcount="2" xpath="location">
  <input xpath="@zipCode"/>
  <input xpath="@city"/>
</container>
```

### 容器類型 {#types-of-container}

容器可用來使用頁面格式的一組欄位來建構複雜的控制項。

#### 標籤容器 {#tab-container}

索引標籤容器會將資料格式化為可從索引標籤存取的頁面。

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

主容器由 **type=&quot;notebook&quot;** 屬性。 標籤會在子容器中宣告，標籤的標籤會從 **標籤** 屬性。

![](assets/d_ncs_integration_form_exemple7.png)

>[!NOTE]
>
>A **style=&quot;down&quot;|up**（預設）**&quot;** 功能會強制標籤在控制項下或上方垂直定位。 此功能是選取性的。
>`<container style="down" type="notebook">  … </container>`

#### 圖示清單 {#icon-list}

此容器會顯示一個垂直圖示列，可讓您選取要顯示的頁面。

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

主容器由 **type=&quot;iconbox&quot;** 屬性。 與表徵圖關聯的頁面在子容器中聲明。 圖示的標籤會從 **標籤** 屬性。

頁面的圖示會從 `img="<image>"` 屬性，其中 `<image>` 是與其索引鍵對應的影像名稱，由名稱和命名空間組成（例如&quot;xtk:properties.png&quot;）。

這些影像可從 **[!UICONTROL Administration > Configuration > Images]** 節點。

#### 可見性容器 {#visibility-container}

您可以透過動態條件來遮罩一組控制項。

此示例說明對「性別」欄位值的控制的可見性：

```xml
<container type="visibleGroup" visibleIf="@gender=1">
  …
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  …
</container>
```

可見性容器由屬性定義 **type=&quot;visibleGroup&quot;**. 此 **visibleIf** 屬性包含可見性條件。

條件語法的範例：

* **visibleIf=&quot;@email=&#39;peter.martinezATneeolane.net&#39;&quot;**:測試字串類型資料上的相等。 比較值必須以引號括住。
* **visibleIf=&quot;@gender >= 1和@gender!= 2」**:條件。
* **visibleIf=&quot;@boolean1=true或@boolean2=false&quot;**:測試布林欄位。

#### 啟用容器 {#enabling-container}

此容器可讓您啟用或停用動態條件中的資料集。 禁用控制項會阻止其編輯。 以下範例說明如何從「性別」欄位的值啟用控制：

```xml
<container type="enabledGroup" enabledIf="@gender=1">
  …
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  …
</container>
```

啟用容器由 **type=&quot;enabledGroup&quot;** 屬性。 此 **enabledIf** 屬性包含啟用條件。

## 編輯連結 {#editing-a-link}

請記住，資料結構中已宣告連結，如下所示：

```xml
<element label="Company" name="company" target="cus:company" type="link"/>
```

輸入表單中連結的編輯控制項如下：

![](assets/d_ncs_integration_form_exemple9.png)

```xml
<input xpath="company"/>
```

可透過編輯欄位存取目標選取項目。 輸入由預先輸入輔助，以便從輸入的前幾個字元中輕鬆找到目標元素。 搜尋接著會根據 **計算字串** 定義。 如果控制項中驗證後架構不存在，則會顯示即時建立目標的確認訊息。 確認會在目標表格中建立新記錄，並將其與連結關聯。

下拉式清單可用於從已建立的記錄清單中選取目標元素。

此 **[!UICONTROL Modify the link]** （資料夾）圖示會啟動選取表單，其中包含目標元素清單和篩選區域：

![](assets/d_ncs_integration_form_exemple10.png)

此 **[!UICONTROL Edit link]** （放大鏡）圖示會啟動連結元素的編輯表單。 預設會針對目標架構的索引鍵推導使用的形式。 此 **表單** 屬性可讓您強制編輯表單的名稱(例如&quot;cus:company2&quot;)。

您可以新增 **`<sysfilter>`** 元素（輸入表單中的連結定義）:

```xml
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

您也可以使用 **`<orderby>`** 元素：

```xml
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### 控制屬性 {#control-properties}

* **noAutoComplete**:停用預先類型（值為「true」）
* **createMode**:如果連結不存在，則會即時建立連結。 可能的值包括：

   * **無**:禁用建立。 如果連結不存在，則會顯示錯誤訊息
   * **內嵌**:在編輯欄位中建立與內容的連結
   * **版本**:顯示連結上的編輯表單。 驗證表單時，會儲存資料（預設模式）

* **noZoom**:連結上沒有編輯表單（且值為「true」）
* **表單**:覆寫目標元素的編輯表單

## 連結清單 {#list-of-links}

在資料結構中以收集元素形式輸入的連結(unbound=&quot;true&quot;)必須瀏覽清單，才能檢視與其相關聯的所有元素。

該原則包括顯示具有最佳化資料載入的連結元素清單（由資料批次下載，只有在清單可見時才執行）。

結構中的集合連結範例：

```xml
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
…
</element>
```

其輸入形式的清單：

![](assets/d_ncs_integration_form_exemple11.png)

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

清單控制項由 **type=&quot;linklist&quot;** 屬性。 清單路徑必須參考集合連結。

欄會透過 **`<input>`** 清單的元素。 此 **xpath** 屬性是指目標架構中欄位的路徑。

具有標籤的工具列（在架構的連結上定義）會自動放在清單上方。

清單可透過 **[!UICONTROL Filters]** 按鈕，並設定為新增及排序欄。

此 **[!UICONTROL Add]** 和 **[!UICONTROL Delete]** 按鈕可讓您新增和刪除連結上的集合元素。 依預設，新增元素會啟動目標架構的編輯表單。

此 **[!UICONTROL Detail]** 按鈕時自動新增 **zoom=&quot;true&quot;** 屬性已在上完成 **`<input>`** 標籤：它可讓您啟動所選行的編輯表單。

載入清單時，可套用篩選和排序：

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

關係表允許您將兩個表連結為N-N基數。 關係表僅包含指向兩個表的連結。

因此，將元素新增至清單，應可讓您從關係表格中的兩個連結之一完成清單。

架構中的關係表示例：

```xml
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

例如，我們從「cus:recipient」架構的輸入形式開始。 清單必須顯示與服務訂閱的關聯，並且必須允許您通過選擇現有服務來添加訂閱。

![](assets/d_ncs_integration_form_exemple12.png)

```xml
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

此 **xpathChoiceTarget** 屬性可讓您從輸入的連結啟動選取表單。 建立關係表記錄將自動更新指向當前收件人和所選服務的連結。

>[!NOTE]
>
>此 **xpathEditTarget** 屬性可讓您在輸入的連結上強制編輯選取的行。

### 清單屬性 {#list-properties}

* **noToolbar**:隱藏工具列（含「true」值）
* **工具欄標題**:重新載入工具列標籤
* **工具欄對齊**:修改工具列的垂直或水準幾何(可能的值：&quot;vertical&quot;|&quot;horizontal&quot;)
* **img**:顯示與清單關聯的影像
* **表單**:覆寫目標元素的編輯表單
* **縮放**:新增 **[!UICONTROL Zoom]** 按鈕來編輯目標元素
* **xpathEditTarget**:在輸入的連結上設定編輯
* **xpathChoiceTarget**:此外，在輸入的連結上啟動選擇表單

## 記憶體清單控制項 {#memory-list-controls}

記憶體清單可讓您使用清單資料預先載入來編輯收集元素。 無法篩選或設定此清單。

這些清單用於XML映射的集合元素或低卷連結。

### 欄清單 {#column-list}

此控制項顯示可編輯的列清單，其工具欄包含「添加」和「刪除」按鈕。

![](assets/d_ncs_integration_form_exemple13.png)

```xml
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

清單控制項必須填入 **type=&quot;list&quot;** 屬性，且清單的路徑必須參考集合元素。

列在子項中聲明 **`<input>`** 清單的標籤。 欄標籤和大小可以使用 **標籤** 和 **colSize** 屬性。

>[!NOTE]
>
>排序順序箭頭會在 **ordered=&quot;true&quot;** 屬性會新增至資料結構中的集合元素。

工具欄按鈕可以水準對齊：

![](assets/d_ncs_integration_form_exemple14.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

此 **工具欄標題** 屬性會強制工具列的水準對齊方式，並在清單上方輸入標題。

#### 放大清單 {#zoom-in-a-list}

在單獨的編輯表單中可以輸入資料的插入和編輯。

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

編輯表單已從 `<form>` 元素。 其結構與輸入形式相同。 此 **[!UICONTROL Detail]** 按鈕時自動新增 **zoom=&quot;true&quot;** 屬性已在上完成 **`<input>`** 標籤。 此屬性可讓您啟動所選行的編輯表單。

>[!NOTE]
>
>新增 **zoomOnAdd=&quot;true&quot;** 屬性會在插入清單元素時強制呼叫編輯表單。

### 清單屬性 {#list-properties-1}

* **noToolbar**:隱藏工具列（含「true」值）
* **工具欄標題**:重新載入工具列標籤
* **工具欄對齊**:修改工具列的位置(可能的值：&quot;vertical&quot;|&quot;horizontal&quot;)
* **img**:顯示與清單關聯的影像
* **表單**:覆寫目標元素的編輯表單
* **縮放**:新增 **[!UICONTROL Zoom]** 按鈕來編輯目標元素
* **zoomOnAdd**:在新增項目上啟動編輯表單
* **xpathChoiceTarget**:此外，在輸入的連結上啟動選擇表單

## 不可編輯的欄位 {#non-editable-fields}

若要顯示欄位並防止其編輯，請使用 **`<value>`** 標籤或完成 **readOnly=&quot;true&quot;** 屬性 **`<input>`** 標籤。

「性別」欄位範例：

![](assets/d_ncs_integration_form_exemple16.png)

```xml
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## 選項按鈕 {#radio-button}

選項按鈕可讓您從數個選項中選擇。 此 **`<input>`** 標籤可用來列出可能的選項，以及 **checkedValue** 屬性指定與選項關聯的值。

「性別」欄位範例：

```xml
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## 核取方塊 {#checkbox}

核取方塊會反映布林值狀態（選取與否）。 依預設，此控制項由「布林值」(true/false)欄位使用。 採用預設值0或1的變數可與此按鈕相關聯。 此值可以透過 **checkValue** 屬性。

```xml
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## 分項清單 {#enumeration}

<!-- to be completed -->

## 導覽階層編輯 {#navigation-hierarchy-edit}

此控制項會在要編輯的一組欄位上建立樹狀結構。

要編輯的控制項會分組在 **`<container>`** 在 **`<input>`** 樹控制項的標籤：

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

運算式欄位會從運算式動態更新欄位；the **`<input>`** 標籤搭配 **xpath** 屬性，輸入要更新的欄位的路徑，以及 **博覽** 包含更新表達式的屬性。

```xml
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## 表單內容 {#context-of-forms}

輸入表單的執行初始化包含被編輯實體的資料的XML文檔。 本檔案代表表單的內容，可作為工作區使用。

### 更新內容 {#updating-the-context}

要修改表單的上下文，請使用 `<set expr="<value>" xpath="<field>"/>` 標籤，其中 `<field>` 是目的地欄位，和 `<value>` 是更新運算式或值。

的使用範例 `<set>` 標籤：

* **`<set expr="'Test'" xpath="/tmp/@test" />`**:將「測試」值置於臨時位置/tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**:使用「測試」值更新「lastName」屬性上的實體
* **`<set expr="true" xpath="@boolean1" />`**:將「boolean1」欄位的值設為「true」
* **`<set expr="@lastName" xpath="/tmp/@test" />`**:使用「lastName」屬性的內容更新

透過 **`<enter>`** 和 **`<leave>`** 標籤。

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
>此 `<enter>` 和 `<leave>` 標籤可用於 `<container>` （「筆記型電腦」和「iconbox」類型）。

### 運算式語言 {#expression-language-}

可在表單定義中使用宏語言，以執行條件式測試。

此 **`<if expr="<expression>" />`** 如果運算式已驗證，則tag會執行標籤下指定的指示：

```xml
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

此 **`<check expr="<condition>" />`** 標籤與 **`<error>`** 標籤會防止驗證表單，並在不符合條件時顯示錯誤訊息：

```xml
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

<!-- changer exemple par un exemple plus parlant. cf. vidéo validation 02:27. noter aussi l'attribut required dans l'exemple de la vidéo. -->

## 嚮導 {#wizards}

精靈會引導您以頁面形式完成資料輸入步驟集。 驗證表單時，輸入的資料會儲存。

精靈的結構如下：

```xml
<form type="wizard" name="example" namespace="cus" img="nms:rcpgroup32.png" label="Wizard example" entity-schema="nms:recipient">
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

存在 **type=&quot;wizard&quot;** 屬性 `<form>` 元素可讓您在表單的建構中定義精靈模式。 頁面從 `<container>` 元素，即 `<form>` 元素。 此 `<container>` 頁面的元素會填入標題的標題屬性，而desc會在頁面標題下顯示說明。 此 **[!UICONTROL Previous]** 和 **[!UICONTROL Next]** 按鈕會自動新增，以允許在頁面之間瀏覽。

此 **[!UICONTROL Finish]** 按鈕將保存輸入的資料並關閉表單。

### SOAP方法 {#soap-methods}

可從填入的 **`<leave>`** 標籤。

此 **`<soapcall>`** 標籤包含對方法的呼叫，並包含下列輸入參數：

```xml
<soapCall name="<name>" service="<schema>">
  <param  type="<type>" exprIn="<xpath>"/>  
  …
</soapCall>
```

服務的名稱及其實作結構會透過 **名稱** 和 **服務** 屬性 **`<soapcall>`** 標籤。

有關輸入參數的說明，請參閱 **`<param>`** 下方的元素 **`<soapcall>`** 標籤。

必須透過 **type** 屬性。 可能的類型如下：

* **字串**:字串
* **布林值**:布林值
* **位元組**:8位整數
* **short**:16位整數
* **long**:32位整數
* **short**:16位整數
* **兩次**:雙精度浮點數
* **DOMElement**:元素類型節點

此 **exprIn** 屬性包含要作為參數傳遞的資料的位置。

**範例**:

```xml
<leave>
  <soapCall name="RegisterGroup" service="nms:recipient">         
    <param  type="DOMElement"    exprIn="/tmp/entityList"/>         
    <param  type="DOMElement"    exprIn="/tmp/choiceList"/>         
    <param  type="boolean"       exprIn="true"/>       
  </soapCall>
</leave>
```
