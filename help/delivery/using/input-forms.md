---
product: campaign
title: 輸入表單
description: 瞭解如何在市場活動中使用輸入表單
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 2%

---

# 輸入表單{#input-forms}

![](../../assets/common.svg)

以下是關於在Adobe Campaign使用輸入表的一些一般原則。

Forms詳見 [此部分](../../configuration/using/identifying-a-form.md)。

## 表單結構 {#form-structure}

輸入表單的XML文檔必須包含 **`<form>`** 根元素 **名稱** 和 **命名空間** 屬性，分別填充表單名稱及其命名空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

預設情況下，表單與具有相同名稱和命名空間的資料架構相關聯。 要將表單與其他名稱關聯，請在 **實體模式** 屬性 **`<form>`** 的子菜單。

為了說明輸入表單的結構，我們基於示例模式「cus:book」來描述一個介面：

![](assets/d_ncs_content_form1.png)

這是相應的輸入表單：

```xml
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

編輯元素的說明以 **`<form>`** 根元素。

在 **`<input>`** 元素 **xpath** 屬性包含其架構中欄位的路徑。

**有關XPath語法的提醒：**

XPath語言在Adobe Campaign用於引用屬於資料模式的元素或屬性。

XPath是一種語法，用於在XML文檔的樹中查找節點。

元素由其名稱指定，屬性由前面帶有字元「@」的名稱指定。

範例:

* **@date**:選擇名稱為「日期」的屬性
* **第@title章**:在 `<chapter>` 元素
* **../@date**:從當前元素的父元素中選擇日期

編輯控制項會自動適應相應的資料類型並使用在架構中定義的標籤。

預設情況下，每個欄位都顯示在一行上，並佔用所有可用空間，具體取決於資料類型。

>[!CAUTION]
>
>輸入表單必須引用 **type=&quot;contentForm&quot;** 屬性 **`<form>`** 元素，以自動添加要輸入內容所需的框架。

## 格式 {#formatting}

控制件相對於彼此的佈置看起來像在HTML表中使用的佈置，其可能將控制件分成若干列、交錯元件或指定可用空間的佔用。 但是，請記住，格式只允許分配比例；不能為對象指定固定維。

如需詳細資訊，請參閱[本章節](../../configuration/using/form-structure.md#formatting)。

## 清單類型控制項 {#list-type-controls}

要編輯集合元素，必須使用清單類型控制項。

### 列清單 {#column-list}

此控制項顯示一個可編輯的列清單，其工具欄包含「添加」和「刪除」按鈕。

![](assets/d_ncs_content_form4.png)

```xml
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

必須用 **type=&quot;list&quot;** 屬性，並且清單的路徑必須引用集合元素。

列由子代聲明 **`<input>`** 清單中的元素。

>[!NOTE]
>
>在 **訂購=&quot;true&quot;** 為資料架構中的集合元素完成屬性。

預設情況下，工具欄按鈕垂直對齊。 也可以水準對齊：

![](assets/d_ncs_content_form5.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

的 **工具欄標題** 屬性強制工具欄的水準對齊並填充清單上方的標題。

>[!NOTE]
>
>對於不顯示在控制項左側的集合元素標籤，請添加 **nolabel=&quot;true&quot;** 屬性。

#### 放大清單 {#zoom-in-a-list}

清單資料的插入和編輯可以以單獨的編輯形式執行。

在下列情況下，會使用清單中的編輯表單：

* 為方便資訊輸入，
* 存在多線控制，
* 清單中的列僅包含主欄位，並且表單顯示集合元素的所有欄位。

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

通過 **`<form>`** 的子菜單。 其結構與輸入形式的結構相同。

A **[!UICONTROL Detail]** 按鈕 **zoom=&quot;true&quot;** 屬性在清單定義中輸入。 這允許您開啟選定行上的編輯表單。

>[!NOTE]
>
>添加 **zoomOnAdd=&quot;true&quot;** 屬性強制在插入清單的元素時調用編輯表單。

### 頁籤清單 {#tab-list}

此清單以制表符的形式顯示對集合元素的編輯。

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

必須用 **type=&quot;notebooklist&quot;** 屬性，並且清單的路徑必須引用集合元素。

頁籤的標題包含通過 **xpath標籤** 屬性。

編輯控制項必須在 **`<container>`** 清單控制項的子元素。

使用工具欄按鈕添加或刪除清單元素。

>[!NOTE]
>
>在 **訂購=&quot;true&quot;** 屬性將填充到資料架構中的集合元素。

## 容器 {#containers}

容器允許您對一組控制項進行分組。 它們通過 **`<container>`** 的子菜單。 它們已用於格式化多列中的控制項和頁籤清單的控制項。

有關容器以及如何在輸入表單中使用它們的詳細資訊，請參閱 [此部分](../../configuration/using/form-structure.md#containers)。

## 編輯表單 {#editing-forms}

編輯區域允許您輸入輸入表單的XML內容：

![](assets/d_ncs_content_form12.png)

的 **[!UICONTROL Preview]** 頁籤中，您可以查看輸入表單：

![](assets/d_ncs_content_form13.png)

閱讀有關 [編輯表單](../../configuration/using/editing-forms.md) 和 [形式結構](../../configuration/using/form-structure.md)。
