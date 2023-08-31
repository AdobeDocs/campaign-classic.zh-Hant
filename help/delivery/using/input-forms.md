---
product: campaign
title: 輸入表單
description: 瞭解如何在Campaign中使用輸入表單
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Data Management
role: User, Developer
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: d2f5f2a662c022e258fb3cc56c8502c4f4cb2849
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 2%

---

# 輸入表單{#input-forms}

以下是有關在Adobe Campaign中使用輸入表單的一些一般原則。

Forms的詳細資訊，請參閱 [本節](../../configuration/using/identifying-a-form.md).

## 表單結構 {#form-structure}

輸入表單的XML檔案必須包含 **`<form>`** 根元素具有 **名稱** 和 **名稱空間** 屬性以分別填入表單名稱及其名稱空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

依預設，表單會與具有相同名稱和名稱空間的資料結構描述相關聯。 若要將表單與不同名稱建立關聯，請在 **entity-schema** 的屬性 **`<form>`** 元素。

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

編輯元素的說明開頭為 **`<form>`** 根元素。

編輯控制項輸入於 **`<input>`** 元素與 **xpath** 包含其結構描述中欄位路徑的屬性。

**有關XPath語法的提醒：**

XPath語言在Adobe Campaign中用於參照屬於資料結構的元素或屬性。

XPath是一種語法，可讓您在XML檔案的樹狀結構中尋找節點。

元素是以其名稱來指定，而屬性是以字元「@」開頭的名稱來指定。

範例:

* **@date**：選取名為「date」的屬性
* **chapter/@title**：選取「 」底下的「title」屬性 `<chapter>` 元素
* **../@date**：從目前元素的父元素中選取日期

編輯控制項會自動適應對應的資料型別，並使用結構描述中定義的標籤。

依預設，每個欄位會顯示在一行上，並佔用所有可用的空間（視資料型別而定）。

>[!CAUTION]
>
>輸入表單必須參考 **type=&quot;contentForm&quot;** 上的屬性 **`<form>`** 元素來自動新增輸入內容所需的框架。

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

清單控制項必須填入 **type=&quot;list&quot;** 屬性，而清單的路徑必須參照收集要素。

欄由子項宣告 **`<input>`** 清單元素。

>[!NOTE]
>
>當出現下列情況時，會自動新增向上和向下排序箭頭： **ordered=&quot;true&quot;** 資料結構描述中集合元素的屬性已完成。

依預設，工具列按鈕會垂直對齊。 它們也可以水準對齊：

![](assets/d_ncs_content_form5.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

此 **toolbarCaption** 屬性會強制水準對齊工具列，並填入清單上方的標題。

>[!NOTE]
>
>若要讓集合元素標籤不顯示在控制項的左側，請新增 **nolabel=&quot;true&quot;** 屬性。

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

編輯表單的定義是透過 **`<form>`** 元素。 其結構與輸入表單的結構相同。

A **[!UICONTROL Detail]** 按鈕會在以下情況自動新增： **zoom=&quot;true&quot;** 在清單定義中輸入屬性。 這可讓您在選取的行上開啟編輯表單。

>[!NOTE]
>
>新增 **zoomOnAdd=&quot;true&quot;** 屬性會強制在插入清單的元素時呼叫編輯表單。

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

清單控制項必須填入 **type=&quot;notebooklist&quot;** 屬性，而清單的路徑必須參照收集要素。

索引標籤的標題包含透過輸入的資料值 **xpath-label** 屬性。

編輯控制項必須宣告於 **`<container>`** 元素是清單控制項的子項。

使用工具列按鈕來新增或刪除清單元素。

>[!NOTE]
>
>當出現下列情況時，會自動新增左右排序箭頭： **ordered=&quot;true&quot;** 屬性會針對資料結構描述中的收集元素填入。

## 容器 {#containers}

容器可讓您將一組控制項分組。 它們透過 **`<container>`** 元素。 它們已用來格式化數個欄中的控制項，並用來控制索引標籤清單。

有關容器及如何在輸入表單中使用的詳細資訊，請參閱 [本節](../../configuration/using/form-structure.md#containers).

## 編輯表單 {#editing-forms}

編輯區域可讓您輸入輸入表單的XML內容：

![](assets/d_ncs_content_form12.png)

此 **[!UICONTROL Preview]** 索引標籤可讓您檢視輸入表單：

![](assets/d_ncs_content_form13.png)

深入瞭解 [編輯表單](../../configuration/using/editing-forms.md) 和 [表單結構](../../configuration/using/form-structure.md).
