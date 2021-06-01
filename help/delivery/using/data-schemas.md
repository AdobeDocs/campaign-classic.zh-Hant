---
product: campaign
title: 資料方案
description: 資料方案
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 3e28bfee-0321-40f4-9ef6-1bdb5b25041b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 2%

---

# 資料方案{#data-schemas}

以下是關於在Adobe Campaign中使用資料結構的一些一般原則。

如需在Adobe Campaign中建立和設定資料結構的詳細資訊，請參閱[此區段](../../configuration/using/about-schema-edition.md)。

## 方案結構 {#schema-structure}

資料架構的XML文檔必須包含&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;屬性的&#x200B;**`<srcschema>`**&#x200B;根元素，以填充架構名稱及其命名空間。

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

在主要元素中輸入的&#x200B;**template**&#x200B;屬性可讓您將具有一般屬性的架構擴展到所有內容定義，如名稱、建立日期、作者、關聯字串等。

這些屬性在&#x200B;**ncm:content**&#x200B;架構中描述。

>[!NOTE]
>
>**xmlChildren**&#x200B;屬性的存在表示通過主元素輸入的資料結構儲存在內容實例的XML文檔中。

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

可以使用各種屬性來豐富資料架構的&#x200B;**`<element>`**&#x200B;和&#x200B;**`<attribute>`**&#x200B;元素。

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

## 集合元素{#collection-elements}

集合是具有相同名稱和相同階層層級的元素清單。

在我們的範例中，**`<chapter>`**&#x200B;和&#x200B;**`<page>`**&#x200B;元素是集合元素。 因此，必須將&#x200B;**unbound**&#x200B;屬性新增至這些元素的定義中：

```
<element name="chapter" label="Chapter" unbound="true" ordered="true">
```

```
<element name="page" type="string" label="Page" desc="Content of page" unbound="true">
```

>[!NOTE]
>
>**ordered=&quot;true&quot;**&#x200B;屬性的存在可讓您排序插入的集合元素。

## 引用{#element-referencing}的元素

元素參考在內容結構中很常使用。 它使您可以對&#x200B;**`<element>`**&#x200B;元素的定義進行分解，以便在具有相同結構的其他元素上引用它。

要引用的元素上的&#x200B;**ref**&#x200B;屬性必須使用引用元素的路徑(XPath)完成。

**範例**:新增與 **** 範例結構的元素 **`<chapter>`** 結構相同的Appendixsection。

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

**計算字串**&#x200B;是XPath表達式，用於構造表示內容實例的字串。

以下是其&#x200B;**計算字串**&#x200B;的範例架構：

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
>**Name**&#x200B;編輯控制項允許您輸入架構的密鑰，包括名稱和命名空間。 架構根元素的&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;屬性會在架構的XML編輯欄位中自動更新。
