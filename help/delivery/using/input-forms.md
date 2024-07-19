---
product: campaign
title: 輸入表單
description: 瞭解如何在Campaign中使用輸入表單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Data Management
role: User, Developer
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '841'
ht-degree: 2%

---

# 輸入表單{#input-forms}

以下是有關在Adobe Campaign中使用輸入表單的一些一般原則。

在[本節](../../configuration/using/identifying-a-form.md)中詳細說明Forms。

## 表單結構 {#form-structure}

輸入表單的XML檔案必須包含具有&#x200B;**名稱**&#x200B;和&#x200B;**名稱空間**&#x200B;屬性的&#x200B;**`<form>`**&#x200B;根專案，才能分別填入表單名稱及其名稱空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

依預設，表單會與具有相同名稱和名稱空間的資料結構描述相關聯。 若要將表單與不同的名稱建立關聯，請在&#x200B;**`<form>`**&#x200B;專案的&#x200B;**entity-schema**&#x200B;屬性中輸入結構描述金鑰。

為了說明輸入表單的結構，我們根據範例結構描述「cus：book」描述了一個介面：

![](assets/d_ncs_content_form1.png)

這是對應的輸入表單：

```xml
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

編輯元素的說明以&#x200B;**`<form>`**&#x200B;根元素開頭。

在&#x200B;**`<input>`**&#x200B;元素中輸入編輯控制項，該元素具有&#x200B;**xpath**&#x200B;屬性，包含其結構描述中的欄位路徑。

**有關XPath語法的提醒：**

XPath語言在Adobe Campaign中用於參照屬於資料結構的元素或屬性。

XPath是一種語法，可讓您在XML檔案的樹狀結構中尋找節點。

元素是以其名稱來指定，而屬性是以字元「@」開頭的名稱來指定。

範例：

* **@date**：選取名稱為「date」的屬性
* **chapter/@title**：選取`<chapter>`專案下的「title」屬性
* **../@date**：從目前專案的父專案選取日期

編輯控制項會自動適應對應的資料型別，並使用結構描述中定義的標籤。

依預設，每個欄位會顯示在一行上，並佔用所有可用的空間（視資料型別而定）。

>[!CAUTION]
>
>輸入表單必須參考&#x200B;**`<form>`**&#x200B;元素上的&#x200B;**type=&quot;contentForm&quot;**&#x200B;屬性，才能自動新增輸入內容所需的框架。

## 格式 {#formatting}

控制項相對於彼此的排列方式看起來類似於HTML表格中使用的排列方式，可能會將控制項分割為數個欄、交錯元素或指定可用空間的佔用。 但是請記住，格式僅授權比例分配；您不能為物件指定固定尺寸。

如需詳細資訊，請參閱[本章節](../../configuration/using/form-structure.md#formatting)。

## 清單型別控制項 {#list-type-controls}

若要編輯收集要素，您必須使用清單型態控制項。

### 欄清單 {#column-list}

此控制項會顯示可編輯的欄清單，其工具列包含新增和刪除按鈕。

![](assets/d_ncs_content_form4.png)

```xml
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

清單控制項必須填入&#x200B;**type=&quot;list&quot;**&#x200B;屬性，而且清單的路徑必須參考集合專案。

資料行是由清單的子&#x200B;**`<input>`**&#x200B;專案宣告。

>[!NOTE]
>
>當資料結構描述中集合元素的&#x200B;**ordered=&quot;true&quot;**&#x200B;屬性完成時，會自動新增向上和向下排序箭頭。

依預設，工具列按鈕會垂直對齊。 它們也可以水準對齊：

![](assets/d_ncs_content_form5.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

**toolbarCaption**&#x200B;屬性強制水準對齊工具列並填入清單上方的標題。

>[!NOTE]
>
>若要讓集合元素標籤不顯示在控制項的左側，請新增&#x200B;**nolabel=&quot;true&quot;**&#x200B;屬性。

#### 放大清單 {#zoom-in-a-list}

可在單獨的編輯表單中插入和編輯清單資料。

在下列情況下會使用清單中的編輯表單：

* 為了方便資訊輸入，
* 存在多行控制項，
* 清單中的欄位僅包含主要欄位，而表單會顯示收集要素的所有欄位。

![](assets/d_ncs_content_form7.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter" zoom="true" zoomOnAdd="true">
  <input xpath="@name"/>
  <input xpath="@number"/>

  <form colcount="2" label="Editing a chapter">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </form>
</input>
```

編輯表單的定義是透過清單專案下的&#x200B;**`<form>`**&#x200B;專案所指定。 其結構與輸入表單的結構相同。

在清單定義中輸入&#x200B;**zoom=&quot;true&quot;**&#x200B;屬性時，會自動新增&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕。 這可讓您在選取的行上開啟編輯表單。

>[!NOTE]
>
>新增&#x200B;**zoomOnAdd=&quot;true&quot;**&#x200B;屬性會強制在插入清單的元素時呼叫編輯表單。

### 索引標籤清單 {#tab-list}

此清單會以索引標籤的形式顯示集合元素的編輯。

![](assets/d_ncs_content_form6.png)

```xml
<container toolbarCaption="List of chapters" type="notebooklist" xpath="chapter" xpath-label="@name">
  <container colcount="2">
    <input xpath="@name"/>
    <input xpath="@number"/>
    <input colspan="2" xpath="page"/>
  </container>
</container>
```

清單控制項必須填入&#x200B;**type=&quot;notebooklist&quot;**&#x200B;屬性，而且清單的路徑必須參考集合專案。

索引標籤的標題包含透過&#x200B;**xpath-label**&#x200B;屬性輸入的資料值。

編輯控制項必須在清單控制項的子項&#x200B;**`<container>`**&#x200B;元素下宣告。

使用工具列按鈕來新增或刪除清單元素。

>[!NOTE]
>
>為資料結構描述中的集合元素填入&#x200B;**ordered=&quot;true&quot;**&#x200B;屬性時，會自動新增左右排序箭頭。

## 容器 {#containers}

容器可讓您將一組控制項分組。 它們透過&#x200B;**`<container>`**&#x200B;元素存在。 它們已用來格式化數個欄中的控制項，並用來控制索引標籤清單。

如需有關容器，以及如何在輸入表單中使用容器的詳細資訊，請參閱[本節](../../configuration/using/form-structure.md#containers)。

## 編輯表單 {#editing-forms}

編輯區域可讓您輸入輸入表單的XML內容：

![](assets/d_ncs_content_form12.png)

**[!UICONTROL Preview]**&#x200B;索引標籤可讓您檢視輸入表單：

![](assets/d_ncs_content_form13.png)

深入瞭解[編輯表單](../../configuration/using/editing-forms.md)和[表單結構](../../configuration/using/form-structure.md)。
