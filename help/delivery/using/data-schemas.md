---
product: campaign
title: 在Campaign中使用資料結構
description: 瞭解如何在Campaign中使用資料結構描述
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Data Model
role: User, Developer, Data Engineer
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 1%

---

# 在Campaign中使用資料結構{#data-schemas}

以下是有關在Adobe Campaign中使用資料結構描述的一些一般原則。

如需在Adobe Campaign中建立和設定資料結構的詳細資訊，請參閱 [本節](../../configuration/using/about-schema-edition.md).

## 方案結構 {#schema-structure}

資料結構描述的XML檔案必須包含 **`<srcschema>`** 根元素具有 **名稱** 和 **名稱空間** 屬性來填入結構描述名稱及其名稱空間。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

結構描述的進入點是其主要元素。 它很容易識別，因為其名稱與結構描述相同，且應是根元素的子項。 內容的說明以此元素開頭。

在內容管理結構中，主要元素由下列行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

此 **範本** 在主要元素中輸入的屬性可讓您將具有一般屬性的結構描述擴充至所有內容定義，例如名稱、建立日期、作者、關聯的字串等。

這些屬性的說明請參閱 **ncm：content** 綱要。

>[!NOTE]
>
>是否存在 **xmlChildren** attribute表示透過主要元素輸入的資料結構會儲存在內容例項的XML檔案中。

>[!CAUTION]
>
>建立新結構描述或在結構描述擴充期間，您需要為整個結構描述保留相同的主要索引鍵序列值(@pkSequence)。

## 資料類型 {#data-types}

以下是填入型別的內容管理結構描述範例：

```
<srcSchema name="book" namespace="cus">
  <element name="book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string"/>
    <attribute name="date" type="date"/>
    <attribute name="language" type="string"/>
    <element name="chapter">
      <attribute name="name" type="string"/>
      <element name="page" type="string>
        <attribute name="number" type="short"/>
      </element>
    </element>
  </element>
</element>
```

## 屬性 {#properties}

可使用各種屬性來擴充 **`<element>`** 和 **`<attribute>`** 個資料結構元素。

內容管理使用的主要屬性如下：

* **標籤**：簡短說明，
* **desc**：詳細說明，
* **預設**：建立內容時傳回預設值的運算式，
* **userEnum**：可自由分項清單，以儲存和顯示透過此欄位輸入的值；
* **列舉**：修正預先知道可能值清單時所使用的分項清單。

以下是填入屬性的結構描述範例：

```
<srcSchema name="book" namespace="cus">
  <enumeration name="language" basetype="string" default="eng">    
    <value name="fra" label="French"/>    
    <value name="eng" label="English"/>   
  </enumeration>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter">
      <attribute name="name" type="string" label="Name" desc="Name of chapter"/>
      <element name="page" type="string" label="Page" desc="Page content">
        <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
      </element>
    </element>
  </element>
</srcSchema>
```

## 集合元素 {#collection-elements}

集合是具有相同名稱和相同階層層級的元素清單。

在我們的範例中， **`<chapter>`** 和 **`<page>`** 元素是收集元素。 此 **未繫結** 因此，必須將屬性新增到這些元素的定義中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>是否存在 **ordered=&quot;true&quot;** attribute可讓您排序插入的集合元素。

## 元素參考 {#element-referencing}

在內容結構描述中，通常會使用元素參考。 它可讓您將 **`<element>`** 元素，以便在具有相同結構的其他元素上參照它。

此 **ref** 要參考之元素上的屬性必須以參考元素的路徑(XPath)完成。

**範例**：新增 **附錄** 與具有相同結構的區段 **`<chapter>`** 我們範例結構描述中的元素。

```
<srcSchema name="book" namespace="cus">
  <element name="section">
    <attribute name="name" type="string" label="Name" desc="Name"/>
    <element name="page" type="string" label="Page" desc="Content of page">
      <attribute name="number" type="short" label="Number" default="CounterValue('numPage')"/>
    </element>

  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <attribute name="title" type="string" label="Title" default="'New book'"/>
    <attribute name="date" type="date" default="GetDate()"/>
    <attribute name="language" type="string" label="Language" enum="language"/>
    <element name="chapter" label="Chapter" ref="section"/>
    <element name="appendix" label="Appendix" ref="section"/>
  </element>
</srcSchema>
```

章節結構會移至主要元素以外名為「section」的元素。 章節和區段會參照「section」元素。

## 計算字串 {#compute-string}

A **計算字串** 是用於建構代表內容執行個體的字串的XPath運算式。

以下是我們的範例結構描述及其 **計算字串**：

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 編輯方案 {#editing-schemas}

編輯欄位可讓您輸入來源架構的XML內容：

![](assets/d_ncs_integration_schema_edition.png)

儲存來源結構描述時，會自動啟動擴充結構描述產生作業。

>[!NOTE]
>
>此 **名稱** 編輯控制項可讓您輸入綱要的索引鍵，包括名稱和名稱空間。 此 **名稱** 和 **名稱空間** 結構描述根元素的屬性會在結構描述的XML編輯欄位中自動更新。
