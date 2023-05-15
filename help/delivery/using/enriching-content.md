---
product: campaign
title: 豐富化內容
description: 豐富化內容
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Data Management
exl-id: a4472a7c-a16b-4d10-a8ca-f74ca5f62de4
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '661'
ht-degree: 0%

---

# 豐富化內容{#enriching-content}



整合器可讓您以外部資料豐富內容。 此資料來自一般查詢或連結的表格。

## 一般查詢 {#generic-queries}

查詢是透過 **[!UICONTROL Aggregator]** 標籤。

檢索到的資料將通過其主要元素豐富XML輸出文檔。

從收件者結構上的查詢傳回的範例(**nms:recipient**):

```
<book name="Content Management">
  ...
  <collection-recipient>
    <recipient lastName="Doe" firstName="John" email="john.doe@aolf.com">
    ...
  </collection-recipient>
</book>
```

此 **`<collection-recipient>`** 元素表示由查詢生成的文檔的輸入元素。 擷取的資料會在此元素下傳回；在我們的範例中，是收件者清單。

### 新增查詢 {#adding-a-query}

查詢參數是使用精靈編輯。

1. 在第一頁，指定標籤和包含要擷取資料的架構。

   ![](assets/d_ncs_content_query1.png)

   >[!NOTE]
   >
   >編輯欄位 **路徑** 用於更名查詢輸出元素。

1. 下一頁可讓您選取要擷取的資料。

   ![](assets/d_ncs_content_query2.png)

1. 下一頁會定義篩選條件。

   ![](assets/d_ncs_content_query3.png)

1. 最後一頁會啟動查詢傳回資料的預覽。

   ![](assets/d_ncs_content_query4.png)

## 連結的表 {#linked-tables}

連結可讓您擷取連結至內容的外部資料。

連結資料有兩種類型：

* 內容連結：這是本機內容管理模式。 連結的內容會自動整合到XML輸出文檔中。
* 指向外部表的連結允許訪問資料庫中的所有其他表，約束是檢索具有聚合器的所選連結的資料。

### 連結至內容結構 {#link-to-a-content-schema}

資料結構中會依下列方式宣告內容連結：

```
<element expandSchemaTarget="cus:chapter" label="Main chapter" name="mainChapter" type="string"/>
```

連結的定義會填入 **字串**-type **`<element>`**，和 **expandSchemaTarget** 屬性會參考目標結構（在範例中為「cus:chapter」）。 引用的架構必須是內容架構。

目標元素的內容豐富了連結元素，即 **`<chapter>`** 範例綱要中的元素：

```
<mainChapter computeString="Introduction" id="7011" title="Introduction" xtkschema="cus:chapter">    
  <page>Introduction to input <STRONG>forms</STRONG>.</page>
</mainChapter>
```

>[!NOTE]
>
>此 **計算字串** 的 **computeString** 屬性。

在輸入表單中，連結的編輯控制項聲明如下：

```
<input type="articleEdit" xpath="mainChapter"/>
```

![](assets/d_ncs_content_link.png)

此 **[!UICONTROL Magnifier]** 表徵圖可讓您開啟連結元素的編輯表單。

#### 連結集合 {#link-collection}

若要填入連結集合，請新增 **unbound=&quot;true&quot;** 屬性，以定義資料結構中的連結元素：

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

系統會顯示預設欄，以檢視 **計算字串** 目標元素中。

### 外部表的連結 {#links-to-external-tables}

在資料架構中，外部表的連結將聲明如下：

```
<element label="Main contact" name="mainContact" target="nms:recipient" type="link"/>
```

連結的定義會填入 **連結**-type **`<element>`**，和 **目標** 屬性會參考目標架構（本範例中為「nms:recipient」）。

根據慣例，必須從資料架構的主要元素宣告連結。

此 **計算字串** 而目標元素的鍵則會豐富 **`<name>-id`** 和 **`<name>-cs`** 屬性。

在我們的範例中，連結會填入「cus:book」結構中，連結資料的內容會包含在「mainContact-id」和「mainContact-cs」屬性中：

```
<book computeString="Content management" date="2006/06/08" id="6106" language="en" mainContact-cs="John Doe (john.doe@adobe.com)" mainContact-id="3012" name="Content management" xtkschema="cus:book">
```

連結編輯控制項的宣告如下：

```
<input xpath="mainContact"/>
```

![](assets/d_ncs_content_link3.png)

您可以新增 **`<sysfilter>`** 元素（透過輸入表單中的連結定義）:

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

#### 連結匯總 {#link-aggregation}

所參考的每個連結的內容僅限於內部索引鍵和 **計算字串** 的URL區段。

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

JavaScript程式碼的內容會透過 **[!UICONTROL Administration > Configuration > Content management > JavaScript Codes]** 資料夾和，必須填入到每次轉換的發佈範本中。

![](assets/d_ncs_content_link5.png)
