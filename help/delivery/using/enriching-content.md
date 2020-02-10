---
title: 豐富內容
seo-title: 豐富內容
description: 豐富內容
seo-description: null
page-status-flag: never-activated
uuid: 6f1bce9f-88ed-4ad3-987f-79f6c68264d2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: 4404c21e-0a89-4762-af20-384ad7071916
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 豐富內容{#enriching-content}

匯整器可讓您使用外部資料豐富內容。 此資料來自一般查詢或連結的表格。

## 一般查詢 {#generic-queries}

查詢是通過頁籤中的發佈模板 **[!UICONTROL Aggregator]** 配置的。

擷取的資料將透過其主要元素豐富XML輸出檔案。

從收件方案上的查詢返回的示例(**nms:recipient**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

元 **`<collection-recipient>`** 素表示由查詢產生的文檔的輸入元素。 檢索到的資料在此元素下返回；在我們的範例中，是收件者清單。

### 添加查詢 {#adding-a-query}

查詢參數是使用嚮導編輯的。

1. 在第一頁中，指定標籤和包含要檢索的資料的架構。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >編輯欄位 **Path** 用於更名查詢輸出元素。

1. 下一頁可讓您選取要擷取的資料。

   ![](assets/d_ncs_content_query2.png)

1. 下一頁定義篩選條件。

   ![](assets/d_ncs_content_query3.png)

1. 最後一頁會啟動查詢傳回資料的預覽。

   ![](assets/d_ncs_content_query4.png)

## 連結的表格 {#linked-tables}

連結可讓您擷取連結至內容的外部資料。

連結資料有兩種類型：

* 內容連結：這是原生內容管理模式。 連結的內容會自動整合在XML輸出檔案中。
* 到外部表的連結允許訪問資料庫中的所有其它表，並限制使用聚合器檢索所選連結的資料。

### 內容架構的連結 {#link-to-a-content-schema}

在資料模式中聲明內容連結如下：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

連結的定義會填入 **字串**- **`<element>`**&#x200B;類型，而 **expandSchemaTarget** 屬性會參照目標結構（我們範例中的「cus:chapter」）。 引用的架構必須是內容架構。

目標元素的內容豐富了連結元素，即我們示例模式 **`<chapter>`** 中的元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>連 **結的Compute字串** ，是從computeString屬性 **呈現** 。

在輸入表單中，連結的編輯控制聲明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

此圖 **[!UICONTROL Magnifier]** 示可讓您開啟連結元素的編輯表單。

#### 連結系列 {#link-collection}

若要填入連結的集合，請將 **unboind=&quot;true&quot;** 屬性新增至資料結構中連結元素的定義：

```
<element expandSchemaTarget="cus:chapter" label="List of chapters" name="chapter"  ordered="true" unbound="true"/>
```

目標元素的內容豐富了每個收集元素：

```
<chapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</chapter>
```

在輸入表單中，清單控制項聲明如下：

```
<input editable="false" nolabel="true" toolbarCaption="List of chapters" type="articleList" xpath="chapter" zoom="true"/>
```

![](assets/d_ncs_content_link2.png)

將顯示一個預設列，以查看目標元 **素的** 「計算」字串。

### 外部表的連結 {#links-to-external-tables}

在資料模式中聲明到外部表的連結如下：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

鏈路的定義填充在鏈 **路類型****`<element>`**&#x200B;上， **target** 屬性引用目標模式（在本例中為nms:recipient）。

依慣例，必須從資料架構的主要元素宣告連結。

計 **算字串** 和目標元素的索引鍵會豐富主元素 **`<name>-id`** 上的 **`<name>-cs`** 屬性和屬性。

在我們的範例中，連結會填入「cus:book」架構中，連結資料的內容會包含在「mainContact-id」和「mainContact-cs」屬性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

連結編輯控制項宣告如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以透過輸入表單中的連結定義來新增 **`<sysfilter>`** 元素，以限制目標元素的選擇：

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

#### 連結系列 {#link-collection-1}

系列的定義與系列元素上清單的定義相同：

```
<element label="List of contacts" name="contact" unbound="true">
  <element label="Recipient" name="recipient" target="nms:recipient" type="link"/>
</element>
```

在輸入表單中，清單控制項聲明如下：

```
<input nolabel="true" toolbarCaption="List of contacts" type="list" xpath="contact">
  <input xpath="recipient"/>
</input>
```

![](assets/d_ncs_content_link4.png)

>[!NOTE]
>
>清單是可編輯的，可讓您從上方顯示的「連結」類型控制項中選取連結。

目標元素的內容豐富了輸出文檔中的每個收集元素：

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### 鏈路聚合 {#link-aggregation}

參考的每個連結的內容僅限於目標元素的內 **部索引鍵** 和計算字串。

JavaScript指令碼可用來透過SOAP查詢豐富連結的內容。

**範例**:將收件者名稱新增至「mainContact」連結和「contact」系列連結：

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

指令碼執行後獲得的結果：

```
<mainContact lastName="Doe"/>

<contact id="11504978621" lastName="Doe" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>  
<contact id="11504982510" lastName="Martinez" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/> 
```

JavaScript程式碼的內容會透過資料夾新增， **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** 而且必須在每次轉換的出版物範本中填入。

![](assets/d_ncs_content_link5.png)

