---
product: campaign
title: 豐富化內容
description: 豐富化內容
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Data Management
role: User, Developer, Data Engineer
exl-id: a4472a7c-a16b-4d10-a8ca-f74ca5f62de4
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 0%

---

# 豐富化內容{#enriching-content}

彙總可讓您利用外部資料豐富內容。 此資料來自一般查詢或連結表格。

## 一般查詢 {#generic-queries}

查詢是透過&#x200B;**[!UICONTROL Aggregator]**&#x200B;索引標籤中的出版物範本設定的。

擷取的資料會透過其主要元素擴充XML輸出檔案。

從收件者綱要(**nms：recipient**)上的查詢傳回的範例：

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

**`<collection-recipient>`**&#x200B;元素代表由查詢產生的檔案的輸入元素。 擷取的資料會傳回至此元素下；在我們的範例中，為收件者清單。

### 新增查詢 {#adding-a-query}

使用精靈編輯查詢引數。

1. 在第一個頁面中，指定標籤和包含要擷取之資料的結構描述。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >編輯欄位&#x200B;**Path**&#x200B;用於重新命名查詢輸出專案。

1. 下一頁可讓您選取要擷取的資料。

   ![](assets/d_ncs_content_query2.png)

1. 下一頁會定義篩選條件。

   ![](assets/d_ncs_content_query3.png)

1. 最後一頁會啟動查詢傳回資料的預覽。

   ![](assets/d_ncs_content_query4.png)

## 連結表格 {#linked-tables}

連結可讓您擷取連結到內容的外部資料。

連結資料有兩種型別：

* 內容連結：這是原生內容管理模式。 連結的內容會自動整合到XML輸出檔案中。
* 外部表格的連結可讓您存取資料庫中的所有其他表格，但會限制使用彙總器擷取所選連結的資料。

### 連結至內容結構描述 {#link-to-a-content-schema}

在資料結構中宣告內容連結的方式如下：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

連結的定義已填入&#x200B;**字串**&#x200B;型別&#x200B;**`<element>`**&#x200B;中，**expandSchemaTarget**&#x200B;屬性參考了目標結構描述（範例中為「cus：chapter」）。 參考的結構描述必須是內容結構描述。

目標元素的內容豐富了連結元素，也就是範例結構描述中的&#x200B;**`<chapter>`**&#x200B;元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>連結的&#x200B;**計算字串**&#x200B;是從&#x200B;**computeString**&#x200B;屬性呈現的。

在輸入表單中，連結的編輯控制項宣告如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

**[!UICONTROL Magnifier]**&#x200B;圖示可讓您開啟連結專案的編輯表單。

#### 連結集合 {#link-collection}

若要填入連結集合，請將&#x200B;**unbound=&quot;true&quot;**&#x200B;屬性新增至資料結構描述中連結元素的定義：

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

目標要素的內容豐富了每個收集要素：

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

在輸入表單中，清單控制項宣告如下：

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

顯示預設欄，以檢視目標元素的&#x200B;**計算字串**。

### 外部表格的連結 {#links-to-external-tables}

在資料綱要中宣告外部表格的連結如下：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

在&#x200B;**連結** — 型別&#x200B;**`<element>`**&#x200B;上填入連結的定義，且&#x200B;**target**&#x200B;屬性參考目標結構描述（範例中為「nms：recipient」）。

依照慣例，必須從資料結構描述的主要元素宣告連結。

**計算字串**&#x200B;和目標專案的索引鍵豐富了主要專案上的&#x200B;**`<name>-id`**&#x200B;和&#x200B;**`<name>-cs`**&#x200B;屬性。

在我們的範例中，連結填入到「cus：book」綱要中，連結資料的內容包含在「mainContact-id」和「mainContact-cs」屬性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

連結編輯控制項宣告如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以透過輸入表單中的連結定義新增&#x200B;**`<sysfilter>`**&#x200B;元素來限制目標元素的選擇：

```
<input xpath="mainContact">
  <!-- Filter the selection of the link on the Adobe domain -->
  <sysFilter>
    <condition expr="@domain =  'adobe.com '"/>
  </sysFilter>
</input>
```

>[!NOTE]
>
>此限制也適用於內容連結。

#### 連結集合 {#link-collection-1}

集合的定義與集合元素上清單的定義相同：

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

在輸入表單中，清單控制項宣告如下：

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>此清單可編輯，並讓您從上方顯示的「連結」型別控制項中選取連結。

目標要素的內容豐富了輸出檔案中的每個收集要素：

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### 連結彙總 {#link-aggregation}

每個參考連結的內容僅限於內部索引鍵和目標專案的&#x200B;**計算字串**。

JavaScript指令碼是用來透過SOAP查詢擴充連結的內容。

**範例**：將收件者名稱新增至「mainContact」連結和「contact」集合連結：

```
// Update <mainContact> link
var mainContactId = content.@['mainContact-id']
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+mainContactId}/>
      </where>
    </queryDef>)

var recipient = query.ExecuteQuery()
content.mainContact.@lastName = recipient.@lastName

// Update <contact> link collection
for each(var contact in content.contact)
{
  var contactId = contact.@['recipient-id']
  var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="get">
      <select>
        <node expr="@lastName"/>
      </select>
      <where>
        <condition expr={"@id="+contactId}/>
      </where>
    </queryDef>
  )
  
  var recipient = query.ExecuteQuery()
  contact.@lastName = recipient.@lastName
}
```

指令碼執行後取得的結果：

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

JavaScript程式碼的內容是透過&#x200B;**[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]**&#x200B;資料夾新增，且必須填入每個轉換的出版物範本。

![](assets/d_ncs_content_link5.png)
