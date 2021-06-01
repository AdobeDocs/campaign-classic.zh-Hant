---
product: campaign
title: 豐富化內容
description: 豐富化內容
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: a4472a7c-a16b-4d10-a8ca-f74ca5f62de4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# 豐富化內容{#enriching-content}

整合器可讓您以外部資料豐富內容。 此資料來自一般查詢或連結的表格。

## 一般查詢{#generic-queries}

查詢是透過&#x200B;**[!UICONTROL Aggregator]**&#x200B;索引標籤中的發佈範本來設定。

檢索到的資料將通過其主要元素豐富XML輸出文檔。

從收件者方案(**nms:recipient**)上的查詢傳回的範例：

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

**`<collection-recipient>`**&#x200B;元素表示查詢後生成的文檔的輸入元素。 擷取的資料會在此元素下傳回；在我們的範例中，是收件者清單。

### 添加查詢{#adding-a-query}

查詢參數是使用精靈編輯。

1. 在第一頁，指定標籤和包含要擷取資料的架構。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >編輯欄位&#x200B;**Path**&#x200B;用於更名查詢輸出元素。

1. 下一頁可讓您選取要擷取的資料。

   ![](assets/d_ncs_content_query2.png)

1. 下一頁會定義篩選條件。

   ![](assets/d_ncs_content_query3.png)

1. 最後一頁會啟動查詢傳回資料的預覽。

   ![](assets/d_ncs_content_query4.png)

## 連結的表{#linked-tables}

連結可讓您擷取連結至內容的外部資料。

連結資料有兩種類型：

* 內容連結：這是本機內容管理模式。 連結的內容會自動整合到XML輸出文檔中。
* 指向外部表的連結允許訪問資料庫中的所有其他表，約束是檢索具有聚合器的所選連結的資料。

### 內容架構{#link-to-a-content-schema}的連結

資料結構中會依下列方式宣告內容連結：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

連結的定義會填入&#x200B;**string**-type **`<element>`**&#x200B;上，而&#x200B;**expandSchemaTarget**&#x200B;屬性會參考目標結構（本例中為「cus:chapter」）。 引用的架構必須是內容架構。

目標元素的內容豐富了連結元素，亦即範例架構中的&#x200B;**`<chapter>`**&#x200B;元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>連結的&#x200B;**計算字串**&#x200B;從&#x200B;**computeString**&#x200B;屬性顯示。

在輸入表單中，連結的編輯控制項聲明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

**[!UICONTROL Magnifier]**&#x200B;圖示可讓您開啟連結元素的編輯表單。

#### 連結集合{#link-collection}

若要填入連結集合，請將&#x200B;**unbound=&quot;true&quot;**&#x200B;屬性新增至資料結構中連結元素的定義：

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

顯示預設列，以便查看目標元素的&#x200B;**計算字串**。

### 外部表{#links-to-external-tables}的連結

在資料架構中，外部表的連結將聲明如下：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

連結的定義會填入&#x200B;**link**-type **`<element>`**&#x200B;上，而&#x200B;**target**&#x200B;屬性會參考目標架構（在本範例中為「nms:recipient」）。

根據慣例，必須從資料架構的主要元素宣告連結。

**計算字串**&#x200B;和目標元素的鍵值豐富了主元素上的&#x200B;**`<name>-id`**&#x200B;和&#x200B;**`<name>-cs`**&#x200B;屬性。

在我們的範例中，連結會填入「cus:book」結構中，連結資料的內容會包含在「mainContact-id」和「mainContact-cs」屬性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

連結編輯控制項的宣告如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以透過輸入表單中的連結定義新增&#x200B;**`<sysfilter>`**&#x200B;元素，以限制目標元素的選擇：

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

#### 連結集合{#link-collection-1}

集合的定義與集合元素清單的定義相同：

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
>清單是可編輯的，可讓您從上方呈現的「連結」類型控制項中選取連結。

目標元素的內容豐富了輸出檔案中的每個收集元素：

```
<contact id="11504978621" recipient-cs="Doe John (john.doe@adobe.com)" recipient-id="3012"/>
<contact id="11504982510" recipient-cs="Martinez Peter (peter.martinez@adobe.com)" recipient-id="3013"/>
```

#### 連結聚合{#link-aggregation}

所參考的每個連結的內容僅限於目標元素的內部索引鍵和&#x200B;**計算字串**。

JavaScript指令碼可用來透過SOAP查詢擴充連結的內容。

**範例**:將收件者名稱新增至「mainContact」連結和「contact」集合連結：

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

JavaScript程式碼的內容會透過&#x200B;**[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]**&#x200B;資料夾新增，且必須填入至每次轉換的發佈範本中。

![](assets/d_ncs_content_link5.png)
