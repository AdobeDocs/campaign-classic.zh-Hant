---
product: campaign
title: 方案結構
description: 方案結構
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 3405efb8-a37c-4622-a271-63d7a4148751
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '1520'
ht-degree: 2%

---

# 方案結構{#schema-structure}

![](../../assets/v7-only.svg)

的基本結構 `<srcschema>` 如下所示：

```
<srcSchema>
    <enumeration>
        ...          //definition of enumerations
    </enumeration>
   
    <element>         //definition of the root <element>    (mandatory)

        <compute-string/>  //definition of a compute-string
        <dbindex>
            ...        //definition of indexes
        </dbindex>
        <key>
            ...        //definition of keys
        </key>
        <sysFilter>
            ...           //definition of filters
        </sysFilter>
        <attribute>
            ...             //definition of fields
        </attribute>
    
            <element>           //definition of sub-<element> 
                  <attribute>           //(collection, links or XML)
                  ...                         //and additional fields
                  </attribute>
                ...
            </element>
      
    </element> 

        <methods>                 //definition of SOAP methods
            <method>
                ...
            </method>
            ...
    </methods>  
          
</srcSchema>
```

資料架構的XML文檔必須包含 **`<srcschema>`** 根元素 **名稱** 和 **命名空間** 用於填充架構名稱及其命名空間的屬性。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

讓我們使用以下XML內容來說明資料架構的結構：

```
<recipient email="John.doe@aol.com" created="2009/03/12" gender="1"> 
  <location city="London"/>
</recipient>
```

使用其相應的資料模式：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email"/>
    <attribute name="created"/>
    <attribute name="gender"/>
    <element name="location">
      <attribute name="city"/>
   </element>
  </element>
</srcSchema>
```

## 說明 {#description}

架構的入口點是其主要元素。 易於識別，因為它與架構具有相同的名稱，並且它應是根元素的子級。 內容的說明以此元素開頭。

在本例中，主要元素由以下行表示：

```
<element name="recipient">
```

元素 **`<attribute>`** 和 **`<element>`** 在主要元素後面，可以定義XML結構中資料項的位置和名稱。

在我們的示例架構中，以下是：

```
<attribute name="email"/>
<attribute name="created"/>
<attribute name="gender"/>
<element name="location">
  <attribute name="city"/>
</element>
```

必須遵守下列規則：

* 每個 **`<element>`** 和 **`<attribute>`** 必須通過名稱標識 **名稱** 屬性。

   >[!IMPORTANT]
   >
   >元素名稱應簡潔明瞭，最好用英文表示，並且僅包括符合XML命名規則的授權字元。

* 僅 **`<element>`** 元素 **`<attribute>`** 元素 **`<element>`** XML結構中的元素。
* 安 **`<attribute>`** 元素在 **`<element>`**。
* 使用 **`<elements>`** 建議在多行資料字串中。

## 資料類型 {#data-types}

資料類型通過 **類型** 屬性 **`<attribute>`** 和 **`<element>`** 元素。

詳細清單可在 [`<attribute>` 元素](../../configuration/using/schema/attribute.md) 和 [`<element>` 元素](../../configuration/using/schema/element.md))。

如果未填充此屬性， **字串** 是預設資料類型，除非元素包含子元素。 如果確實如此，則僅用於分層結構元素(**`<location>`** 元素)。

架構支援以下資料類型：

* **字串**:字串。 示例：名字，鎮子等等。

   可以通過 **長度** attribute（可選，預設值&quot;255&quot;）。

* **布爾**:布爾欄位。 可能值的示例：true/false、0/1、yes/no等。
* **位元組**。 **短**。 **長**:整數（1位元組、2位元組、4位元組）。 示例：年齡、帳號、點數等。
* **雙**:雙精度浮點數。 示例：價格，價格等等。
* **日期**。 **日期**:日期和日期+時間。 示例：出生日期、購買日期等。
* **日期**:日期+時間，不包含時區資料。
* **時隙**:持續時間。 示例：資歷。
* **備忘錄**:長文本欄位（多行）。 示例：說明、注釋等。
* **UU**:用於支援GUID的&quot;uniqueidentifier&quot;欄位(僅在MicrosoftSQL Server中支援)。

   >[!NOTE]
   >
   >包含 **UU** 在MicrosoftSQL Server以外的引擎中，必須添加並使用其預設值完成&quot;newuuid()&quot;函式。

下面是我們輸入的類型的示例架構：

```
<srcSchema name="recipient" namespace="cus">
  <element name="recipient">
    <attribute name="email" type="string" length="80"/>
    <attribute name="created" type="datetime"/>
    <attribute name="gender" type="byte"/>
    <element name="location">
      <attribute name="city" type="string" length="50"/>
   </element>
  </element>
</srcSchema>
```

### 映射Adobe Campaign/DBMS資料的類型 {#mapping-the-types-of-adobe-campaign-dbms-data}

下表列出了Adobe Campaign為不同資料庫管理系統生成的資料類型的映射。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>Adobe Campaign</strong><br /> </td> 
   <td> <strong>PosgreSQL</strong><br /> </td> 
   <td> <strong>Oracle</strong><br /> </td> 
   <td> <strong>MS SQL</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 字串<br /> </td> 
   <td> VARCHAR(255)<br /> </td> 
   <td> VARCHAR2（如果為unicode，則為NVARCHAR2）<br /> </td> 
   <td> VARCHAR（如果unicode，則為NVARCHAR）<br /> </td> 
  </tr> 
  <tr> 
   <td> 布林<br /> </td> 
   <td> 斯馬林特<br /> </td> 
   <td> 數字(3)<br /> </td> 
   <td> 蒂尼因特<br /> </td> 
  </tr> 
  <tr> 
   <td> 位元組<br /> </td> 
   <td> 斯馬林特<br /> </td> 
   <td> 數字(3)<br /> </td> 
   <td> 蒂尼因特<br /> </td> 
  </tr> 
  <tr> 
   <td> 短<br /> </td> 
   <td> 斯馬林特<br /> </td> 
   <td> 數字(5)<br /> </td> 
   <td> 斯馬林特<br /> </td> 
  </tr> 
  <tr> 
   <td> 兩次<br /> </td> 
   <td> 雙精度<br /> </td> 
   <td> 浮動<br /> </td> 
   <td> 浮動<br /> </td> 
  </tr> 
  <tr> 
   <td> 長<br /> </td> 
   <td> 整數<br /> </td> 
   <td> 數字(10)<br /> </td> 
   <td> INT<br /> </td> 
  </tr> 
  <tr> 
   <td> Int64<br /> </td> 
   <td> 比金特<br /> </td> 
   <td> 數字(20)<br /> </td> 
   <td> 比金特<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期<br /> </td> 
   <td> 日期時間<br /> </td> 
  </tr> 
  <tr> 
   <td> 時間<br /> </td> 
   <td> 時間<br /> </td> 
   <td> 浮動<br /> </td> 
   <td> 浮動<br /> </td> 
  </tr> 
  <tr> 
   <td> 日期時間<br /> </td> 
   <td> 時間戳<br /> </td> 
   <td> 日期<br /> </td> 
   <td> MS SQL &lt; 2008:日期時間<br /> MS SQL &gt;= 2012:日期時間偏移<br /> </td> 
  </tr> 
  <tr> 
   <td> 達蒂梅諾茨<br /> </td> 
   <td> 時間戳<br /> </td> 
   <td> 日期<br /> </td> 
   <td> MS SQL &lt; 2008:日期時間<br /> MS SQL &gt;= 2012:DATETIME2<br /> </td> 
  </tr> 
  <tr> 
   <td> 時間盤<br /> </td> 
   <td> 雙精度<br /> </td> 
   <td> 浮動<br /> </td> 
   <td> 浮動<br /> </td> 
  </tr> 
  <tr> 
   <td> 備忘<br /> </td> 
   <td> 文本<br /> </td> 
   <td> CLOB（如果為Unicode，則為NCLOB）<br /> </td> 
   <td> TEXT（如果為Unicode，則為NTEXT）<br /> </td> 
  </tr> 
  <tr> 
   <td> blob<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> BLOB<br /> </td> 
   <td> 影像<br /> </td> 
  </tr> 
 </tbody> 
</table>

## 屬性 {#properties}

的 **`<elements>`** 和 **`<attributes>`** 資料模式的元素可以用各種屬性進行豐富。 您可以填充標籤以描述當前元素。

### 標籤和說明 {#labels-and-descriptions}

* 的 **標籤** 屬性，用於輸入簡要說明。

   >[!NOTE]
   >
   >標籤與實例的當前語言關聯。

   **範例**:

   ```
   <attribute name="email" type="string" length="80" label="Email"/>
   ```

   從Adobe Campaign客戶端控制台輸入表單中可以看到標籤：

   ![](assets/d_ncs_integration_schema_label.png)

* 的 **des** 屬性，用於輸入詳細說明。

   從Adobe Campaign客戶端控制台主窗口的狀態欄中的輸入表單中可以看到描述。

   >[!NOTE]
   >
   >說明與實例的當前語言相關聯。

   **範例**:

   ```
   <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
   ```

### 預設值 {#default-values}

的 **預設** 屬性用於定義在內容建立時返回預設值的表達式。

該值必須是符合XPath語言的表達式。 有關此內容的詳細資訊，請參閱 [使用XPath引用](../../configuration/using/schema-structure.md#referencing-with-xpath)。

**範例**:

* 當前日期： **default=&quot;GetDate()&quot;**
* 計數器： **default=&quot;&#39;FRM&#39;+CounterValue(&#39;myCounter&#39;)&quot;**

   在本示例中，預設值是使用字串的串聯並調用 **計數器值** 函式。 每次插入時，返回的數字遞增1。

   >[!NOTE]
   >
   >在Adobe Campaign客戶端控制台中， **[!UICONTROL Administration>Counters]** 節點用於管理計數器。

要將預設值連結到欄位，可以使用 `<default>  or  <sqldefault>   field.  </sqldefault> </default>`

`<default>` :允許您在建立圖元時用預設值預填充欄位。 該值將不是預設SQL值。

`<sqldefault>` :允許您在建立欄位時增加值。 此值顯示為SQL結果。 在模式更新期間，只有新記錄受此值影響。

### 分項清單 {#enumerations}

#### 自由枚舉 {#free-enumeration}

的 **用戶枚舉** 屬性用於定義一個可用枚舉，以記住和顯示通過此欄位輸入的值。 語法如下：

**userEnum=&quot;枚舉名稱&quot;**

可以自由選擇指定給枚舉的名稱，並與其他欄位共用。

這些值顯示在輸入表單的下拉清單中：

![](assets/d_ncs_integration_schema_user_enum.png)

>[!NOTE]
>
>在Adobe Campaign客戶端控制台中， **[!UICONTROL Administration > Enumerations]** 節點用於管理枚舉。

#### 設定枚舉 {#set-enumeration}

的 **枚舉** 屬性用於定義在事先已知可能值清單時使用的固定枚舉。

的 **枚舉** attribute是指在主元素外的架構中填充的枚舉類的定義。

枚舉允許用戶從下拉清單中選擇值，而不是在常規輸入欄位中輸入值：

![](assets/d_ncs_integration_schema_enum.png)

資料架構中枚舉聲明的示例：

```
<enumeration name="gender" basetype="byte" default="0">    
  <value name="unknown" label="Not specified" value="0"/>    
  <value name="male" label="male" value="1"/>   
  <value name="female" label="female" value="2"/>   
</enumeration>
```

枚舉通過 **`<enumeration>`** 的子菜單。

枚舉屬性如下：

* **基本類型**:與值關聯的資料類型，
* **標籤**:枚舉的描述，
* **名稱**:枚舉的名稱，
* **預設**:枚舉的預設值。

枚舉值在 **`<value>`** 元素，具有以下屬性：

* **名稱**:內部儲存的值的名稱，
* **標籤**:表徵圖。

#### dbenum枚舉 {#dbenum-enumeration}

* 的 **貝努姆** 屬性用於定義屬性與 **枚舉** 屬性。

   然而， **名稱** 屬性不在內部儲存值，它儲存一個代碼，該代碼允許您擴展相關表而不修改其架構。

   值通過 **[!UICONTROL Administration>Enumerations]** 的下界。

   例如，此枚舉用於指定市場活動的性質。

   ![](assets/d_ncs_configuration_schema_dbenum.png)

### 範例 {#example}

下面是我們的示例架構，其中填充了以下屬性：

```
<srcSchema name="recipient" namespace="cus">
  <enumeration name="gender" basetype="byte">    
    <value name="unknown" label="Not specified" value="0"/>    
    <value name="male" label="male" value="1"/>   
    <value name="female" label="female" value="2"/>   
  </enumeration>

  <element name="recipient">
    <attribute name="email" type="string" length="80" label="Email" desc="Email of recipient"/>
    <attribute name="created" type="datetime" label="Date of creation" default="GetDate()"/>
    <attribute name="gender" type="byte" label="gender" enum="gender"/>
    <element name="location" label="Location">
      <attribute name="city" type="string" length="50" label="City" userEnum="city"/>
   </element>
  </element>
</srcSchema>
```

## 集合 {#collections}

集合是具有相同名稱和相同分層級別的元素的清單。

的 **解除** 值為&quot;true&quot;的屬性允許您填充收集元素。

**示例**:定義 **`<group>`** 架構中的集合元素。

```
<element name="group" unbound="true" label="List of groups">
  <attribute name="label" type="string" label="Label"/>
</element>
```

通過投影XML內容：

```
<group label="Group1"/>
<group label="Group2"/>
```

## 使用XPath引用 {#referencing-with-xpath}

XPath語言在Adobe Campaign用於引用屬於資料模式的元素或屬性。

XPath是一種語法，用於在XML文檔的樹中查找節點。

元素由其名稱指定，屬性由前面帶有字元「@」的名稱指定。

**範例**:

* **@email**:選擇電子郵件，
* **位置/@city**:在 **`<location>`** 元素
* **../@email**:從當前元素的父元素中選擇電子郵件地址
* **組`[1]/@label`**:選擇「label」屬性，該屬性是第一個 **`<group>`** 集合元素
* **組`[@label='test1']`**:選擇「label」屬性，該屬性是 **`<group>`** 元素和包含值「test1」

>[!NOTE]
>
>當路徑與子元素交叉時，將添加附加約束。 在這種情況下，以下表達式必須放在括弧之間：
>
>* **位置/@city** 無效；請使用 **`[location/@city]`**
>* **`[@email]`** 和 **@email** 等於
>


還可以定義複雜表達式，如以下算術運算：

* **@gender+1**:為 **性別** 屬性，
* **@email + &#39;(&#39;+@created+&#39;&#39;**:通過在圓括弧之間為建立日期添加的電子郵件地址的值（對於字串類型，將常數置於引號中）來構建字串。

為了豐富這種語言的潛力，在表達式中增加了高級函式。

您可以通過Adobe Campaign客戶端控制台中的任何表達式編輯器訪問可用函式清單：

![](assets/d_ncs_integration_schema_function.png)

**範例**:

* **GetDate()**:返回當前日期
* **年(@created)**:返回「已建立」屬性中包含的日期的年份。
* **GetEmailDomain(@email)**:返回電子郵件地址的域。

## 通過計算字串生成字串 {#building-a-string-via-the-compute-string}

A **計算字串** 是XPath表達式，用於構建一個字串，該字串表示與架構關聯的表中的記錄。 **計算字串** 主要用在圖形介面中，以顯示選定記錄的標籤。

的 **計算字串** 通過 **`<compute-string>`** 元素。 安 **EXPR** 屬性包含用於計算顯示的XPath表達式。

**示例**:收件人表的計算字串。

```
<srcSchema name="recipient" namespace="nms">  
  <element name="recipient">
    <compute-string expr="@lastName + ' ' + @firstName +' (' + @email + ')' "/>
    ...
  </element>
</srcSchema>
```

收件人的計算字串的結果： **無名氏(john.doe@aol.com)**

>[!NOTE]
>
>如果架構不包含計算字串，則預設情況下會使用架構主鍵的值填充計算字串。
