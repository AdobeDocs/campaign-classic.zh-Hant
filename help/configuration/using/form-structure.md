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



表單的說明是結構化XML檔案，可觀察表單結構描述的語法 **xtk：form**.

輸入表單的XML檔案必須包含 `<form>` 根元素具有 **名稱** 和 **名稱空間** 屬性，以填入表單名稱和名稱空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

依預設，表單會與具有相同名稱和名稱空間的資料結構描述相關聯。 若要將表單與不同名稱相關聯，請設定 **entity-schema** 的屬性 `<form>` 元素對應到結構描述金鑰的名稱。 為了說明輸入表單的結構，讓我們使用&quot;cus：recipient&quot;範例結構描述來說明介面：

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

編輯控制項的說明會從 `<form>` 根元素。 編輯控制項輸入於 **`<input>`** 元素搭配 **xpath** 包含其結構描述中欄位路徑的屬性。

編輯控制項會自動適應對應的資料型別，並使用結構描述中定義的標籤。

>[!NOTE]
>
>您可以透過新增「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」、「 」等標籤，多載其資料結構描述中定義的標籤 **標籤** 屬性至 `<input>` 元素：\
>`<input label="Email address" xpath="@name" />`

依預設，每個欄位都會顯示在單一行上，並依據資料型別佔用所有可用空間。

## 格式 {#formatting}

控制項的版面配置看起來類似於HTML表格中使用的版面，可以將控制項分割成數欄、交錯元素或指定可用空間的佔用。 但是請記住，格式設定只能讓您將區域以比例分割；您不能為物件指定固定尺寸。

若要以兩欄顯示上述範例的控制項，請執行下列動作：

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

此 **`<container>`** 元素搭配 **colcount** attribute可讓您在兩個欄上強制顯示子控制項。

此 **colspan** 控制項上的屬性會透過在其值中輸入的欄數來擴充控制項：

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

填入 **type=&quot;frame&quot;** 屬性，容器會在子控制項周圍新增一個框架，且標籤包含在 **標籤** 屬性：

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

A **`<static>`** 元素可用於格式化輸入表單：

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

此 **`<static>`** 標籤和 **分隔符號** type可讓您新增分隔列，其標籤包含在 **標籤** 屬性。

說明文字已使用 `<static>` 標籤中附加說明型別。 文字內容輸入於 **標籤** 屬性。

## 容器 {#containers}

容器可讓您將一組控制項分組。 他們由 **`<container>`** 元素。 以上使用它們來格式化數欄的控制項。

此 **xpath** 上的屬性 `<container>` 可讓您簡化子控制項的參照。 然後，控制項的參照會相對於父項 `<container>` 元素。

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

### 容器型別 {#types-of-container}

容器可用來使用頁面中格式化的一組欄位來建構複雜的控制項。

#### 標籤容器 {#tab-container}

索引標籤容器可格式化頁面中可從索引標籤存取的資料。

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

主要容器由 **type=&quot;notebook&quot;** 屬性。 標籤會在子項容器中宣告，而標籤的標籤會從 **標籤** 屬性。

![](assets/d_ncs_integration_form_exemple7.png)

>[!NOTE]
>
>A **style=&quot;down|up**（依預設）**&quot;** 特徵會強制標籤標籤垂直定位在控制項下方或上方。 此功能是選取性的。
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

主要容器由 **type=&quot;iconbox&quot;** 屬性。 與圖示相關聯的頁面會在子容器中宣告。 圖示的標籤會從 **標籤** 屬性。

頁面的圖示會從 `img="<image>"` 屬性，其中 `<image>` 是與其金鑰相對應的影像名稱，由名稱和名稱空間組成（例如「xtk：properties.png」）。

影像可從以下網址取得： **[!UICONTROL Administration > Configuration > Images]** 節點。

#### 可見度容器 {#visibility-container}

您可以透過動態條件遮罩一組控制項。

此範例說明「性別」欄位值上的控制項可見性：

```xml
<container type="visibleGroup" visibleIf="@gender=1">
  …
</container>
<container type="visibleGroup" visibleIf="@gender=2">
  …
</container>
```

可見度容器由屬性定義 **type=&quot;visibleGroup&quot;**. 此 **visibleIf** 屬性包含可見性條件。

條件語法的範例：

* **visibleIf=&quot;@email=&#39;peter.martinezATneeolane.net&#39;&quot;**：測試字串型別資料的相等性。 比較值必須以引號括住。
* **visibleIf=&quot;@gender >= 1和@gender！= 2英吋**：數值的條件。
* **visibleIf=&quot;@boolean1=true or @boolean2=false&quot;**：在布林值欄位上測試。

#### 啟用容器 {#enabling-container}

此容器可讓您啟用或停用動態條件的一組資料。 停用控制項會使其無法編輯。 下列範例說明如何從「性別」欄位的值啟用控制項：

```xml
<container type="enabledGroup" enabledIf="@gender=1">
  …
</container>
<container type="enabledGroup" enabledIf="@gender=2">
  …
</container>
```

啟用容器是由 **type=&quot;enabledGroup&quot;** 屬性。 此 **enabledIf** 屬性包含啟用條件。

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

可透過編輯欄位存取目標選擇。 預先輸入可協助輸入，以便從輸入的前幾個字元中輕鬆找到目標元素。 然後會根據 **計算字串** 定義於目標結構描述中。 如果結構描述在控制項中驗證後不存在，則會顯示即時目標建立的確認訊息。 確認會在目標表格中建立新記錄，並將其與連結建立關聯。

下拉式清單可用來從已建立的記錄清單中選取目標元素。

此 **[!UICONTROL Modify the link]** （資料夾）圖示會啟動包含目標元素清單和篩選區域的選擇表單：

![](assets/d_ncs_integration_form_exemple10.png)

此 **[!UICONTROL Edit link]** （放大鏡）圖示會啟動連結元素的編輯表單。 根據預設，使用的形式是在目標結構描述的索引鍵上推匯出來的。 此 **表單** 屬性可讓您強制使用編輯表單的名稱（例如「cus：company2」）。

您可以透過新增以下專案來限制目標元素的選擇 **`<sysfilter>`** 元素輸入表單中的連結定義：

```xml
<input xpath="company">
  <sysFilter>
    <condition expr="[location/@city] =  'Newton"/>
  </sysFilter>
</input>
```

您也可以將清單排序為 **`<orderby>`** 元素：

```xml
<input xpath="company">
  <orderBy>
    <node expr="[location/@zipCode]"/>
  </orderBy>
</input>
```

### 控制項屬性 {#control-properties}

* **noAutoComplete**：停用預先輸入（值為「true」）
* **createmode**：如果連結不存在，則會立即建立。 可能的值包括：

   * **無**：停用建立。 如果連結不存在，則會顯示錯誤訊息
   * **內嵌**：在編輯欄位中建立包含內容的連結
   * **版本**：在連結上顯示編輯表單。 驗證表單時，資料會儲存（預設模式）

* **noZoom**：連結上沒有編輯表單（值為「true」）
* **表單**：多載目標元素的編輯表單

## 連結清單 {#list-of-links}

在資料結構描述中作為集合元素(unbound=&quot;true&quot;)輸入的連結必須透過清單才能檢視與其相關聯的所有元素。

原則包含顯示已最佳化資料載入的連結元素清單（透過資料批次下載，僅在清單可見時執行）。

結構描述中的集合連結範例：

```xml
<element label="Events" name="rcpEvent" target="cus:event" type="link" unbound="true">
…
</element>
```

清單的輸入形式：

![](assets/d_ncs_integration_form_exemple11.png)

```xml
 <input xpath="rcpEvent" type="linklist">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

清單控制項由 **type=&quot;linklist&quot;** 屬性。 清單路徑必須參照集合連結。

欄是透過 **`<input>`** 清單元素。 此 **xpath** attribute是指目標結構描述中欄位的路徑。

帶有標籤的工具列（在架構中的連結上定義）會自動放置在清單上方。

清單可透過以下方式篩選 **[!UICONTROL Filters]** 按鈕並設定為新增和排序欄。

此 **[!UICONTROL Add]** 和 **[!UICONTROL Delete]** 按鈕可讓您新增和刪除連結上的集合元素。 依預設，新增元素會啟動目標結構描述的編輯表單。

此 **[!UICONTROL Detail]** 按鈕會在以下情況下自動新增： **zoom=&quot;true&quot;** 屬性完成於 **`<input>`** 清單的標籤：可讓您啟動所選行的編輯表單。

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

### 關係表格 {#relationship-table}

關係表格可讓您連結兩個具有N-N基數的表格。 關係表格僅包含兩個表格的連結。

因此，將元素新增至清單應可讓您從關係表格中的兩個連結之一完成清單。

結構描述中的關係表範例：

```xml
<srcSchema name="subscription" namespace="cus">
  <element name="recipient" type="link" target="cus:recipient" label="Recipient"/>
  <element name="service" type="link" target="cus:service" label="Subscription service"/>
</srcSchema>
```

例如，我們以&quot;cus：recipient&quot;結構描述的輸入表單開始。 清單必須顯示與服務訂閱的關聯，而且必須允許您透過選取現有服務來新增訂閱。

![](assets/d_ncs_integration_form_exemple12.png)

```xml
<input type="linklist" xpath="subscription" xpathChoiceTarget="service" xpathEditTarget="service" zoom="true">
  <input xpath="recipient"/>
  <input xpath="service"/>
</input>
```

此 **Xpathchoicetarget** 屬性可讓您從輸入的連結啟動選擇表單。 建立關係表格記錄會自動更新目前收件者和所選服務的連結。

>[!NOTE]
>
>此 **xpathEditTarget** 屬性可讓您強制編輯輸入連結上選取的行。

### 清單屬性 {#list-properties}

* **noToolbar**：隱藏工具列（值為「true」）
* **toolbarCaption**：多載工具列標籤
* **toolbarAlign**：修改工具列的垂直或水準幾何（可能的值： 「垂直」|「水準」）
* **img**：顯示與清單相關聯的影像
* **表單**：多載目標元素的編輯表單
* **縮放**：新增 **[!UICONTROL Zoom]** 按鈕以編輯目標元素
* **xpathEditTarget**：在輸入的連結上設定編輯
* **Xpathchoicetarget**：此外，會在輸入的連結上啟動選擇表單

## 記憶體清單控制項 {#memory-list-controls}

記憶體清單可讓您使用清單資料預先載入來編輯集合元素。 無法篩選或設定此清單。

這些清單用於XML對應的收集要素或低容量連結。

### 欄清單 {#column-list}

此控制項會顯示可編輯的欄清單，其工具列包含「新增」和「刪除」按鈕。

![](assets/d_ncs_integration_form_exemple13.png)

```xml
<input xpath="rcpEvent" type="list">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

清單控制項必須填入 **type=&quot;list&quot;** 屬性，而清單的路徑必須參照收集要素。

欄會在子項中宣告 **`<input>`** 清單的標籤。 欄的標籤和大小可以強制使用 **標籤** 和 **colSize** 屬性。

>[!NOTE]
>
>排序順序箭頭會在 **ordered=&quot;true&quot;** 屬性會新增至資料結構描述中的收集元素。

工具列按鈕可水準對齊：

![](assets/d_ncs_integration_form_exemple14.png)

```xml
<input nolabel="true" toolbarCaption="List of events" type="list" xpath="rcpEvent" zoom="true">
  <input xpath="@label"/>
  <input xpath="@date"/>
</input>
```

此 **toolbarCaption** attribute會強制工具列的水準對齊，並輸入清單上方的標題。

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

編輯表單已完成 `<form>` 清單定義下的元素。 其結構與輸入表單的結構相同。 此 **[!UICONTROL Detail]** 按鈕會在以下時自動新增： **zoom=&quot;true&quot;** 屬性完成於 **`<input>`** 清單的標籤。 此屬性可讓您啟動所選行的編輯表單。

>[!NOTE]
>
>新增 **zoomOnAdd=&quot;true&quot;** attribute會在插入清單元素時強制呼叫編輯表單。

### 清單屬性 {#list-properties-1}

* **noToolbar**：隱藏工具列（值為「true」）
* **toolbarCaption**：多載工具列標籤
* **toolbarAlign**：修改工具列的位置（可能的值： &quot;vertical&quot;|&quot;horizontal&quot;）
* **img**：顯示與清單相關聯的影像
* **表單**：多載目標元素的編輯表單
* **縮放**：新增 **[!UICONTROL Zoom]** 按鈕以編輯目標元素
* **zoomOnAdd**：啟動新增專案上的編輯表單
* **Xpathchoicetarget**：此外，會在輸入的連結上啟動選擇表單

## 不可編輯的欄位 {#non-editable-fields}

若要顯示欄位並防止編輯該欄位，請使用 **`<value>`** 標籤或完成 **readOnly=&quot;true&quot;** 上的屬性 **`<input>`** 標籤之間。

「性別」欄位範例：

![](assets/d_ncs_integration_form_exemple16.png)

```xml
<value value="@gender"/>
<input xpath="@gender" readOnly="true"/>
```

## 選項按鈕 {#radio-button}

選項按鈕可讓您從多個選項中進行選擇。 此 **`<input>`** 標籤可用來列出可能的選項，以及 **checkedValue** attribute會指定與選項相關的值。

「性別」欄位範例：

```xml
<input type="RadioButton" xpath="@gender" checkedValue="0" label="Choice 1"/>
<input type="RadioButton" xpath="@gender" checkedValue="1" label="Choice 2"/>
<input type="RadioButton" xpath="@gender" checkedValue="2" label="Choice 3"/>
```

![](assets/d_ncs_integration_form_exemple17.png)

## 核取方塊 {#checkbox}

核取方塊會反映布林值狀態（是否選取）。 依預設，此控制項由「布林值」(true/false)欄位使用。 預設值為0或1的變數可以與此按鈕相關聯。 此值可透過 **checkValue** 屬性。

```xml
<input xpath="@boolean1"/>
<input xpath="@field1" type="checkbox" checkedValue="Y"/>
```

![](assets/d_ncs_integration_form_exemple20.png)

## 分項清單 {#enumeration}

<!-- to be completed -->

## 導覽階層編輯 {#navigation-hierarchy-edit}

此控制項會在一組要編輯的欄位上建立樹狀結構。

要編輯的控制項會分組在 **`<container>`** 輸入於 **`<input>`** 樹狀結構控制項的標籤：

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

運算式欄位會從運算式動態更新欄位； **`<input>`** 標籤用於 **xpath** 屬性，輸入要更新的欄位路徑和 **expo** 包含更新運算式的屬性。

```xml
<!-- Example: updating the boolean1 field from the value contained in the field with path /tmp/@flag -->
<input expr="Iif([/tmp/@flag]=='On', true, false)" type="expr" xpath="@boolean1"/>
<input expr="[/ignored/@action] == 'FCP'" type="expr" xpath="@launchFCP"/>
```

## 表單的內容 {#context-of-forms}

執行輸入表單會初始化包含正在編輯之實體資料的XML檔案。 此檔案代表表單的內容，並可當做工作區使用。

### 更新內容 {#updating-the-context}

若要修改表單的前後關聯，請使用 `<set expr="<value>" xpath="<field>"/>` 標籤，其中 `<field>` 是目的地欄位，且 `<value>` 是更新運算式或值。

使用範例 `<set>` 標籤：

* **`<set expr="'Test'" xpath="/tmp/@test" />`**：將&#39;Test&#39;值放置在暫時位置/tmp/@test1
* **`<set expr="'Test'" xpath="@lastName" />`**：以「Test」值更新「lastName」屬性上的實體
* **`<set expr="true" xpath="@boolean1" />`**：將「boolean1」欄位的值設為「true」
* **`<set expr="@lastName" xpath="/tmp/@test" />`**：以「lastName」屬性的內容更新

透過初始化和關閉表單時，可以更新表單的內容 **`<enter>`** 和 **`<leave>`** 標籤之間。

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
>此 `<enter>` 和 `<leave>` 標籤可用於 `<container>` （「notebook」和「iconbox」型別）。

### 運算式語言 {#expression-language-}

巨集語言可用於表單定義中，以執行條件測試。

此 **`<if expr="<expression>" />`** 如果運算式已驗證，標籤會執行標籤底下指定的指示：

```xml
<if expr="([/tmp/@test] == 'Test' or @lastName != 'Doe') and @boolean2 == true">
  <set xpath="@boolean1" expr="true"/>
</if>
```

此 **`<check expr="<condition>" />`** 標籤與 **`<error>`** 標籤會阻止表單驗證，如果不滿足條件，則會顯示錯誤訊息：

```xml
<leave>
  <check expr="/tmp/@test != ''">
    <error>You must populate the 'Test' field!</error> 
  </check>
</leave>
```

<!-- changer exemple par un exemple plus parlant. cf. vidéo validation 02:27. noter aussi l'attribut required dans l'exemple de la vidéo. -->

## 精靈 {#wizards}

精靈會以頁面的形式引導您完成一組資料輸入步驟。 驗證表單時，輸入的資料會儲存。

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

是否存在 **type=&quot;wizard&quot;** 上的屬性 `<form>` element可讓您定義表單建構中的精靈模式。 頁面完成自 `<container>` 元素，為的子項 `<form>` 元素。 此 `<container>` 頁面的元素會填入title和desc的標題屬性，以在頁面標題下顯示說明。 此 **[!UICONTROL Previous]** 和 **[!UICONTROL Next]** 會自動新增按鈕，以允許在不同頁面之間瀏覽。

此 **[!UICONTROL Finish]** 按鈕會儲存輸入的資料並關閉表單。

### SOAP方法 {#soap-methods}

SOAP方法執行可從填入的啟動 **`<leave>`** 標籤的後面。

此 **`<soapcall>`** 標籤包含方法的呼叫，並具有下列輸入引數：

```xml
<soapCall name="<name>" service="<schema>">
  <param  type="<type>" exprIn="<xpath>"/>  
  …
</soapCall>
```

服務的名稱及其實作結構描述是透過 **名稱** 和 **服務** 屬性 **`<soapcall>`** 標籤之間。

有關輸入引數的說明，請參見 **`<param>`** 下的元素 **`<soapcall>`** 標籤之間。

引數型別必須透過 **type** 屬性。 可能的型別如下：

* **字串**：字元字串
* **布林值**：布林值
* **位元組**：8位元整數
* **短**：16位元整數
* **long**：32位元整數
* **短**：16位元整數
* **兩次**：雙精確度浮點數
* **DOMElement**：元素型別節點

此 **exprIn** attribute包含要以引數形式傳遞的資料位置。

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
