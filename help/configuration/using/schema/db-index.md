---
product: campaign
title: 元素和屬性 — dbindex元素
description: dbindex元素
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# dbindex元素 {#dbindex--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-3}

dbindex:=鍵欄位

## 屬性 {#attributes-3}

* @_operation（字串）
* @applicableIf（字串）
* @label（字串）
* @name(MNTOKEN)
* @unique（布爾值）

## 父母 {#parents-3}

`<element>`

## 兒童 {#children-3}

`<keyfield>`

## 說明 {#description-3}

使用此元素可以定義連結到表的索引。

## 使用和使用上下文 {#use-and-context-of-use-3}

可以定義多個索引。 一個索引可以引用表的一個或多個欄位。 索引聲明通常遵循主架構元素的定義。

訂單 `<keyfield>` 在 `<dbindex>` 很重要。 第一個 `<keyfield>` 必須是查詢主要基於的索引標準。

資料庫中索引的名稱是通過將表名稱與索引名稱連接來計算的。 例如：索引建立查詢期間索引欄位的表名「Sample」、命名空間「Cus」、索引名「MyIndex」 — >名稱：&quot;CusSample_myIndex&quot;。

## 屬性說明 {#attribute-description-3}

* **操作（字串）**:定義在資料庫中寫入的類型。

   此屬性主要用於擴展開箱模式。

   可訪問的值為：

   * &quot;無&quot;:單獨和解。 這意味著，Adobe Campaign將恢復元素，而不更新該元素，如果該元素不存在，則不生成錯誤。
   * &quot;insertOrUpdate&quot;:用插入更新。 這意味著Adobe Campaign將更新元素或在元素不存在時建立它。
   * &quot;插入&quot;:插入。 這意味著Adobe Campaign將插入元素，而不檢查它是否存在。
   * &quot;更新&quot;:更新。 這意味著Adobe Campaign將更新元素，或在元素不存在時生成錯誤。
   * &quot;刪除&quot;:刪除。 這意味著Adobe Campaign將恢復和刪除元素。

* **appliatedIf（字串）**:用於考慮索引的條件 — 接收XTK表達式。
* **標籤（字串）**:索引標籤。
* **名稱(MNTOKEN)**:唯一索引名。
* **唯一（布爾值）**:如果激活此選項(@unique=&quot;true&quot;)，則屬性將確保索引在其整個欄位中的唯一性。

## 範例 {#examples-3}

在「id」欄位上建立索引。 (「@unique」屬性 `<dbindex>` 元素觸發器在資料庫（查詢）中建立索引時添加「UNIQUE」 SQL關鍵字。

```
<element label="Sample" name="Sample">
  <dbindex name="myIndex" label="My index on the ID field" unique="true" applicableIf="HasPackage('nms:social')">
      <keyfield xpath="@id"/>
  </dbindex>
    <attribute name="id" type="long"/>
</element>          
```

```
ALTER TABLE CusSample ADD iSampleId INTEGER;
UPDATE CusSample SET iSampleId = 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET Default 0;
ALTER TABLE CusSample ALTER COLUMN iSampleId SET NOT NULL; 
CREATE UNIQUE INDEX CusSample_myIndex ON CusSample(iSampleId);
```

在「@mail」和「@phoneNumber」欄位上建立複合索引：

```
<element label="NewSchemaUser" name="NewSchemaUser">
  <dbindex name="myIndex" label="My composite index">
         <keyfield xpath="@email"/>
         <keyfield xpath="@phone"/>
  </dbindex>
  
  <attribute name="email" type="string"/>
  <attribute name="phone" type="string"/>
</element>      
```

```
CREATE INDEX DocNewSchemaUser_myIndex ON DocNewSchemaUser(sEmail, sPhone);
```
