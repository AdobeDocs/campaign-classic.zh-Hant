---
product: campaign
title: 輸入表單
description: 輸入表單
audience: delivery
content-type: reference
topic-tags: content-management
exl-id: 8ec52c96-44a2-4544-93b6-9ba251510682
source-git-commit: cf4e316e9c9bce467e2bd2bd04097f55b3dbb9c7
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 2%

---

# 輸入表單{#input-forms}

![](../../assets/common.svg)

以下是關於在Adobe Campaign使用輸入表格的一些一般原則。

Forms在 [本節](../../configuration/using/identifying-a-form.md).

## 表單結構 {#form-structure}

輸入表單的XML文檔必須包含 **`<form>`** 根元素與 **名稱** 和 **命名空間** 屬性，分別填入表單名稱及其命名空間。

```xml
<form name="form_name" namespace="name_space">
…
</form>
```

依預設，表單會與具有相同名稱和命名空間的資料架構相關聯。 要將表單與其他名稱關聯，請在 **實體綱要** 屬性 **`<form>`** 元素。

為了說明輸入表單的結構，我們以範例結構「cus:book」為基礎描述介面：

![](assets/d_ncs_content_form1.png)

此為對應的輸入表單：

```xml
<form name="book" namespace="cus" type="contentForm">
  <input xpath="@name"/>
  <input xpath="@date"/>
  <input xpath="@language"/>
</form>
```

編輯元素的說明以 **`<form>`** 根元素。

在 **`<input>`** 元素搭配 **xpath** 屬性，包含其架構中欄位的路徑。

**有關XPath語法的提醒：**

Adobe Campaign中使用XPath語言來參考屬於資料架構的元素或屬性。

XPath是一種語法，用於在XML文檔的樹中查找節點。

元素由其名稱指定，屬性由名稱指定，名稱前面加上字元「@」。

範例:

* **@date**:選擇名稱為「date」的屬性
* **章節/@title**:選取 `<chapter>` 元素
* **../@date**:從當前元素的父元素中選擇日期

編輯控制項會自動適應對應的資料類型，並使用架構中定義的標籤。

依預設，每個欄位會顯示在一行，並根據資料類型佔據所有可用空間。

>[!CAUTION]
>
>輸入表單必須參考 **type=&quot;contentForm&quot;** 屬性 **`<form>`** 元素來自動新增要輸入內容所需的框架。

## 格式 {#formatting}

控制項相對彼此的佈置類似於在HTML表中使用的佈置，其可能將控制項分成若干列、交錯元件或指定佔用可用空間。 但是，請記住，格式只允許分配比例；不能為對象指定固定維。

如需詳細資訊，請參閱[本章節](../../configuration/using/form-structure.md#formatting)。

## 清單類型控制項 {#list-type-controls}

若要編輯集合元素，您必須使用清單類型控制項。

### 欄清單 {#column-list}

此控制項顯示可編輯的列清單，其工具欄包含「添加」和「刪除」按鈕。

![](assets/d_ncs_content_form4.png)

```xml
<input xpath="chapter" type="list">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

清單控制項必須填入 **type=&quot;list&quot;** 屬性，且清單的路徑必須參考集合元素。

列由子項聲明 **`<input>`** 清單的元素。

>[!NOTE]
>
>當 **ordered=&quot;true&quot;** 資料結構中集合元素的屬性已完成。

依預設，工具列按鈕會垂直對齊。 也可水準對齊：

![](assets/d_ncs_content_form5.png)

```xml
<input nolabel="true" toolbarCaption="List of chapters" type="list" xpath="chapter">
  <input xpath="@name"/>
  <input xpath="@number"/>
</input>
```

此 **工具欄標題** 屬性會強制工具列的水準對齊方式，並填入清單上方的標題。

>[!NOTE]
>
>若要讓集合元素標籤不顯示在控制項左側，請新增 **nolabel=&quot;true&quot;** 屬性。

#### 放大清單 {#zoom-in-a-list}

清單資料的插入和編輯可以以單獨的編輯形式執行。

在清單中編輯表單的用途如下：

* 為方便資訊輸入，
* 有多線控制，
* 清單中的欄僅包含主要欄位，表單會顯示集合元素的所有欄位。

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

編輯表單的定義是透過 **`<form>`** 元素。 其結構與輸入形式的結構相同。

A **[!UICONTROL Detail]** 按鈕時自動新增 **zoom=&quot;true&quot;** 屬性。 這可讓您開啟所選行上的編輯表單。

>[!NOTE]
>
>新增 **zoomOnAdd=&quot;true&quot;** 屬性會在插入清單的元素時強制呼叫編輯表單。

### 索引標籤清單 {#tab-list}

此清單以頁簽形式顯示集合元素的編輯。

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

清單控制項必須填入 **type=&quot;notebooklist&quot;** 屬性，且清單的路徑必須參考集合元素。

索引標籤的標題包含透過 **xpath-label** 屬性。

編輯控制項必須在 **`<container>`** 是清單控制項子項的元素。

使用工具欄按鈕添加或刪除清單元素。

>[!NOTE]
>
>當 **ordered=&quot;true&quot;** 屬性會填入資料結構中集合元素的。

## 容器 {#containers}

容器可讓您將一組控制項分組。 它們透過 **`<container>`** 元素。 它們已用於格式化數列中的控制項以及用於控制標籤清單。

有關容器以及如何在輸入表單中使用容器的詳細資訊，請參閱 [本節](../../configuration/using/form-structure.md#containers).

## 編輯表單 {#editing-forms}

編輯區域可讓您輸入輸入表單的XML內容：

![](assets/d_ncs_content_form12.png)

此 **[!UICONTROL Preview]** 索引標籤可讓您檢視輸入表單：

![](assets/d_ncs_content_form13.png)

深入了解 [編輯表單](../../configuration/using/editing-forms.md) 和 [表單結構](../../configuration/using/form-structure.md).
