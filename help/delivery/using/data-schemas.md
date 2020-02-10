---
title: 資料結構
seo-title: 資料結構
description: 資料結構
seo-description: null
page-status-flag: never-activated
uuid: 3327a38c-e44d-4581-a67b-bb60c1604a5f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: content-management
discoiquuid: aeaa9475-3715-40a4-8864-29d126883272
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7dbc876fae0bde78e3088ee1ab986cd09e9bcc38

---


# 資料結構{#data-schemas}

以下是有關在Adobe Campaign中使用資料結構描述的一些一般原則。

如需在Adobe Campaign中建立和設定資料結構描述的詳細資訊，請參 [閱此節](../../configuration/using/about-schema-edition.md)。

## 架構結構 {#schema-structure}

資料結構的XML檔案必須包含 **`<srcschema>`** 根元素，其中 **包含** namespace **** 屬性，以填入結構名稱及其命名空間。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

方案的入口點是其主要元素。 很容易識別，因為它與結構相同，而且應是根元素的子項。 內容的說明以此元素開始。

在內容管理架構中，主要元素由以下行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

在主 **要元素中輸入的範本屬性** ，可讓您將具有一般屬性的架構擴充至所有內容定義，例如名稱、建立日期、作者、相關字串等。

這些屬性在 **ncm:content架構中說明** 。

>[!NOTE]
>
>xmlChildren屬性的存 **** 在表示通過主元素輸入的資料結構儲存在內容實例的XML文檔中。

>[!CAUTION]
>
>在建立新模式或在模式擴展期間，需要為整個模式保留相同的主鍵序列值(@pkSequence)。

## 資料類型 {#data-types}

以下是內容管理架構的範例，其中填入了下列類型：

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

可使用各種屬性來豐富資 **`<element>`** 料 **`<attribute>`** 架構的元素。

內容管理中使用的主要屬性如下：

* **標籤**:簡短描述，
* **desc**:詳細描述，
* **預設**:運算式在內容建立時傳回預設值，
* **userEnum**:免費枚舉以儲存和顯示通過此欄位輸入的值，
* **列舉**:修正當事先已知可能值的清單時所使用的列舉。

以下是我們的範例架構，其中填入了屬性：

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

## 系列元素 {#collection-elements}

系列是具有相同名稱和相同階層層級的元素清單。

在我們的範例中， **`<chapter>`** 和元 **`<page>`** 素是系列元素。 因此 **，必須將未綁定** 的屬性添加到以下元素的定義中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在ordered=&quot; **** true&quot;屬性可讓您對插入的系列元素進行排序。

## 元素參照 {#element-referencing}

在內容結構描述中，元素參考使用較多。 它可讓您將元素的定義分解， **`<element>`** 以便在具有相同結構的其他元素上引用它。

要 **引用的元素** 上的ref屬性必須使用引用元素的路徑(XPath)完成。

**範例**:添加與示 **例模式的元素具有****`<chapter>`** 相同結構的附錄部分。

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

章節結構會移至主要元素外部名稱為&quot;section&quot;的元素。 本章和章節引用「章節」元素。

## 計算字串 {#compute-string}

計 **算字串** 是XPath運算式，用來建構代表內容例項的字串。

以下是我們的示例模式及其 **計算字串**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 編輯結構 {#editing-schemas}

編輯欄位可讓您輸入來源架構的XML內容：

![](assets/d_ncs_integration_schema_edition.png)

保存源模式時，將自動啟動擴展模式生成。

>[!NOTE]
>
>「名 **稱** 」編輯控制項可讓您輸入架構的索引鍵，包括名稱和命名空間。 架構 **根元素的名** 稱和名稱空間屬性 **** ，將在架構的XML編輯欄位中自動更新。
