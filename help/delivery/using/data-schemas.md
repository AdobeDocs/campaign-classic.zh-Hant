---
solution: Campaign Classic
product: campaign
title: 資料綱要
description: 資料綱要
audience: delivery
content-type: reference
topic-tags: content-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---


# 資料綱要{#data-schemas}

以下是有關在Adobe Campaign中使用資料結構描述的一些一般原則。

如需在Adobe Campaign中建立和設定資料結構的詳細資訊，請參閱[本節](../../configuration/using/about-schema-edition.md)。

## 綱要結構 {#schema-structure}

資料架構的XML文檔必須包含&#x200B;**`<srcschema>`**&#x200B;根元素，其中&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;屬性必須填入架構名稱及其命名空間。

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

在主要元素中輸入的&#x200B;**template**&#x200B;屬性可讓您將具有一般屬性的架構擴充至所有內容定義，例如名稱、建立日期、作者、相關字串等。

這些屬性在&#x200B;**ncm:content**&#x200B;架構中有說明。

>[!NOTE]
>
>存在&#x200B;**xmlChildren**&#x200B;屬性表示通過主元素輸入的資料結構儲存在內容實例的XML文檔中。

>[!CAUTION]
>
>建立新模式或在模式擴展期間，需要為整個模式保留相同的主鍵序列值(@pkSequence)。

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

各種屬性可用於豐富資料架構的&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;元素。

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

## 系列元素{#collection-elements}

系列是具有相同名稱和相同階層層級的元素清單。

在我們的範例中，**`<chapter>`**&#x200B;和&#x200B;**`<page>`**&#x200B;元素是系列元素。 因此，**unbound**&#x200B;屬性必須添加到以下元素的定義中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在&#x200B;**ordered=&quot;true&quot;**&#x200B;屬性可讓您排序插入的系列元素。

## 引用{#element-referencing}的元素

在內容結構描述中，元素參考使用較多。 它可讓您對&#x200B;**`<element>`**&#x200B;元素的定義進行分解，以便對具有相同結構的其他元素進行引用。

要引用的元素上的&#x200B;**ref**&#x200B;屬性必須以引用元素的路徑(XPath)完成。

**範例**:添加與示 **** 例模式的元素具有相 **`<chapter>`** 同結構的Appendixsection。

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

## 計算字串{#compute-string}

**計算字串**&#x200B;是用於構造表示內容實例的字串的XPath表達式。

以下是我們的示例模式及其&#x200B;**Compute string**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 編輯綱要 {#editing-schemas}

編輯欄位可讓您輸入來源架構的XML內容：

![](assets/d_ncs_integration_schema_edition.png)

保存源模式時，將自動啟動擴展模式生成。

>[!NOTE]
>
>**Name**&#x200B;編輯控制項可讓您輸入架構的索引鍵，包括名稱和命名空間。 架構根元素的&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;屬性會在架構的XML編輯欄位中自動更新。
