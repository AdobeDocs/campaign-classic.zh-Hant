---
product: campaign
title: 在市場活動中使用資料架構
description: 瞭解如何在市場活動中使用資料架構
feature: Data Model
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 1%

---

# 在市場活動中使用資料架構{#data-schemas}

![](../../assets/common.svg)

以下是關於在Adobe Campaign使用資料模式的一些一般原則。

有關在Adobe Campaign建立和配置資料架構的詳細資訊，請參閱 [此部分](../../configuration/using/about-schema-edition.md)。

## 方案結構 {#schema-structure}

資料架構的XML文檔必須包含 **`<srcschema>`** 根元素 **名稱** 和 **命名空間** 用於填充架構名稱及其命名空間的屬性。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

架構的入口點是其主要元素。 易於識別，因為它與架構具有相同的名稱，並且它應是根元素的子級。 內容的說明以此元素開頭。

在內容管理架構中，主元素由以下行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

的 **模板** 在主元素中輸入的屬性允許您將具有泛型屬性的架構擴展到所有內容定義，如名稱、建立日期、作者、關聯字串等。

這些屬性在 **ncm：內容** 架構。

>[!NOTE]
>
>存在 **xml子項** attribute指示通過主元素輸入的資料結構儲存在內容實例的XML文檔中。

>[!CAUTION]
>
>建立新架構或在架構擴展期間，需要為整個架構保留相同的主鍵序列值(@pkSequence)。

## 資料類型 {#data-types}

下面是一個內容管理架構的示例，其中填充了以下類型：

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

可使用各種屬性來豐富 **`<element>`** 和 **`<attribute>`** 資料架構的元素。

內容管理中使用的主要屬性如下：

* **標籤**:簡短描述，
* **des**:長描述，
* **預設**:表達式在內容建立時返回預設值，
* **用戶枚舉**:用於儲存和顯示通過此欄位輸入的值的免費枚舉，
* **枚舉**:在事先已知可能值清單時使用的固定枚舉。

下面是我們的示例架構，其中填充了以下屬性：

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

集合是具有相同名稱和相同分層級別的元素的清單。

在我們的例子中， **`<chapter>`** 和 **`<page>`** 元素是集合元素。 的 **解除** 因此，必須將屬性添加到這些元素的定義中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在 **訂購=&quot;true&quot;** 屬性允許您對插入的收集元素進行排序。

## 元素引用 {#element-referencing}

元素引用在內容架構中使用得很多。 它使您能夠分解 **`<element>`** 以便可以參照具有相同結構的其它元素。

的 **參照** 必須使用引用元素的路徑(XPath)完成要引用的元素上的屬性。

**示例**:添加 **附錄** 結構與 **`<chapter>`** 示例架構的元素。

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

章結構將移到主元素外帶名稱為&quot;section&quot;的元素。 本章和章節提及&quot;節&quot;元素。

## 計算字串 {#compute-string}

A **計算字串** 是用於構造表示內容實例的字串的XPath表達式。

下面是我們的示例架構及其 **計算字串**:

```
<srcSchema name="book" namespace="cus">
  <element name="book" label="Book" desc="Example book" template="ncm:content" xmlChildren="true">
    <compute-string expr="@name"/>
    ...
  </element>
</srcSchema>
```

## 編輯方案 {#editing-schemas}

編輯欄位用於輸入源架構的XML內容：

![](assets/d_ncs_integration_schema_edition.png)

保存源架構後，將自動啟動擴展架構生成。

>[!NOTE]
>
>的 **名稱** 編輯控制項用於輸入架構的鍵，包括名稱和命名空間。 的 **名稱** 和 **命名空間** 在架構的XML編輯欄位中自動更新架構根元素的屬性。
