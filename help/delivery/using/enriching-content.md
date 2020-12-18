---
solution: Campaign Classic
product: campaign
title: 豐富化內容
description: 豐富化內容
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---


# 豐富化內容{#enriching-content}

匯整器可讓您使用外部資料豐富內容。 此資料來自一般查詢或連結的表格。

## 一般查詢{#generic-queries}

查詢是通過&#x200B;**[!UICONTROL Aggregator]**&#x200B;頁籤中的發佈模板配置的。

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

**`<collection-recipient>`**&#x200B;元素代表由查詢產生的文檔的輸入元素。 檢索到的資料在此元素下返回；在我們的範例中，是收件者清單。

### 添加查詢{#adding-a-query}

查詢參數是使用嚮導編輯的。

1. 在第一頁中，指定標籤和包含要檢索的資料的架構。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >編輯欄位&#x200B;**Path**&#x200B;用於更名查詢輸出元素。

1. 下一頁可讓您選取要擷取的資料。

   ![](assets/d_ncs_content_query2.png)

1. 下一頁定義篩選條件。

   ![](assets/d_ncs_content_query3.png)

1. 最後一頁會啟動查詢傳回資料的預覽。

   ![](assets/d_ncs_content_query4.png)

## 連結表{#linked-tables}

連結可讓您擷取連結至內容的外部資料。

連結資料有兩種類型：

* 內容連結：這是原生內容管理模式。 連結的內容會自動整合在XML輸出檔案中。
* 到外部表的連結允許訪問資料庫中的所有其它表，並限制使用聚合器檢索所選連結的資料。

### 連結至內容架構{#link-to-a-content-schema}

在資料模式中聲明內容連結如下：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

連結的定義會填入至&#x200B;**字串**-type **`<element>`**，而&#x200B;**expandSchemaTarget**&#x200B;屬性會參照目標結構（在我們的範例中為cus:chapter）。 引用的架構必須是內容架構。

目標元素的內容豐富了連結元素，即我們示例模式中的&#x200B;**`<chapter>`**&#x200B;元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>連結的&#x200B;**計算字串**&#x200B;是從&#x200B;**computeString**&#x200B;屬性中顯示的。

在輸入表單中，連結的編輯控制聲明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

**[!UICONTROL Magnifier]**&#x200B;圖示可讓您開啟連結的元素的編輯表單。

#### 連結系列{#link-collection}

若要填入連結集合，請將&#x200B;**unboind=&quot;true&quot;**&#x200B;屬性新增至資料結構中連結元素的定義：

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

為了查看目標元素的&#x200B;**計算字串**，將顯示預設列。

### 外部表{#links-to-external-tables}的連結

在資料模式中聲明到外部表的連結如下：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

鏈路的定義填充在&#x200B;**link**-type **`<element>`**&#x200B;上，並且&#x200B;**target**&#x200B;屬性引用目標模式（在我們的示例中為「nms:recipient」）。

依慣例，必須從資料架構的主要元素宣告連結。

**計算字串**&#x200B;和目標元素的鍵豐富了主元素上的&#x200B;**`<name>-id`**&#x200B;和&#x200B;**`<name>-cs`**&#x200B;屬性。

在我們的範例中，連結會填入「cus:book」架構中，連結資料的內容會包含在「mainContact-id」和「mainContact-cs」屬性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

連結編輯控制項宣告如下：

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

#### 連結系列{#link-collection-1}

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

#### 鏈路聚合{#link-aggregation}

參考的每個連結的內容限制為目標元素的內部鍵和&#x200B;**計算字串**。

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

JavaScript程式碼的內容會透過&#x200B;**[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]**&#x200B;資料夾新增，而且必須在每個轉換的出版物範本中填入。

![](assets/d_ncs_content_link5.png)

