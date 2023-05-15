---
product: campaign
title: 在Campaign中使用資料結構
description: 了解如何在Campaign中使用資料綱要
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Data Model
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 1%

---

# 在Campaign中使用資料結構{#data-schemas}



以下是關於在Adobe Campaign中使用資料結構的一些一般原則。

如需在Adobe Campaign中建立和設定資料結構的詳細資訊，請參閱 [本節](../../configuration/using/about-schema-edition.md).

## 方案結構 {#schema-structure}

資料架構的XML文檔必須包含 **`<srcschema>`** 根元素與 **名稱** 和 **命名空間** 屬性來填入結構名稱及其命名空間。

```
<srcSchema name="schema_name" namespace="namespace">
...
</srcSchema>
```

架構的進入點是其主要元素。 很容易識別，因為其名稱與結構相同，且應為根元素的子項。 內容的說明以此元素開頭。

在內容管理架構中，主要元素由下列行表示：

```
<element name="book" template="ncm:content" xmlChildren="true">
```

此 **範本** 在主要元素中輸入的屬性可讓您將具有一般屬性的結構擴充至所有內容定義，例如名稱、建立日期、作者、關聯字串等。

這些屬性在 **ncm:content** 綱要。

>[!NOTE]
>
>存在 **xmlChildren** 屬性指示通過主元素輸入的資料結構儲存在內容實例的XML文檔中。

>[!CAUTION]
>
>在建立新架構或架構擴充期間，您需要為整個架構保留相同的主鍵序列值(@pkSequence)。

## 資料類型 {#data-types}

以下是內容管理架構的範例，其中填入的類型如下：

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

可使用各種屬性來豐富 **`<element>`** 和 **`<attribute>`** 資料結構的元素。

內容管理中使用的主要屬性如下：

* **標籤**:簡短描述，
* **desc**:長描述，
* **預設**:運算式在內容建立時傳回預設值，
* **userEnum**:可儲存並顯示透過此欄位輸入的值的免費分項清單，
* **列舉**:修正事前已知可能值清單時所使用的分項清單。

以下是已填入屬性的範例結構：

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

在我們的範例中， **`<chapter>`** 和 **`<page>`** 元素是集合元素。 此 **未綁定** 因此，必須將屬性新增至這些元素的定義中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>存在 **ordered=&quot;true&quot;** 屬性可讓您排序插入的集合元素。

## 元素參考 {#element-referencing}

元素參考在內容結構中很常使用。 它可讓您將 **`<element>`** 元素，以便在具有相同結構的其他元素上參照它。

此 **ref** 必須使用引用元素的路徑(XPath)完成要引用的元素上的屬性。

**範例**:新增 **附錄** 與 **`<chapter>`** 範例結構的元素。

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

章節結構會移至主要元素外部名稱為「section」的元素。 章節和章節參考「section」元素。

## 計算字串 {#compute-string}

A **計算字串** 是XPath運算式，用於建構代表內容例項的字串。

以下是我們的範例架構及其 **計算字串**:

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

儲存來源架構時，會自動啟動延伸架構產生。

>[!NOTE]
>
>此 **名稱** 編輯控制項可讓您輸入架構的索引鍵，由名稱和命名空間組成。 此 **名稱** 和 **命名空間** 架構根元素的屬性會自動在架構的XML編輯欄位中更新。
