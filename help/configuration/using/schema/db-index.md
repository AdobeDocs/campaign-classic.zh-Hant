---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---

# dbindex元素 {#dbindex--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-3}

dbindex:==keyfield

## 屬性 {#attributes-3}

* @_operation（字串）
* @applicableIf（字串）
* @label（字串）
* @name(MNTOKEN)
* @unique（布林值）

## 父母 {#parents-3}

`<element>`

## 兒童 {#children-3}

`<keyfield>`

## 說明 {#description-3}

此元素可讓您定義連結至表格的索引。

## 使用與使用內容 {#use-and-context-of-use-3}

可以定義多個索引。 一個索引可以引用表的一個或多個欄位。 索引聲明通常遵循主架構元素的定義。

順序 `<keyfield>` 在 `<dbindex>` 非常重要。 第一個 `<keyfield>` 必須是查詢主要依據的索引標準。

通過串連表的名稱和索引的名稱來計算資料庫中索引的名稱。 例如：表名「Sample」、命名空間「Cus」、索引名「MyIndex」 — >索引建立查詢期間索引欄位的名稱：&quot;CusSample_myIndex&quot;。

## 屬性說明 {#attribute-description-3}

* **_operation（字串）**:定義資料庫中的寫入類型。

   此屬性主要用於擴充現成可用的結構時。

   可存取的值包括：

   * &quot;none&quot;:單獨調解。 這表示Adobe Campaign將復原元素，而不會更新元素，或在不存在的情況下產生錯誤。
   * &quot;insertOrUpdate&quot;:更新為插入。 這表示Adobe Campaign將更新元素，或在元素不存在時加以建立。
   * &quot;insert&quot;:插入。 這表示Adobe Campaign將插入元素，而不會檢查元素是否存在。
   * &quot;update&quot;:更新。 這表示Adobe Campaign將更新元素，或在元素不存在時產生錯誤。
   * &quot;delete&quot;:刪除。 這表示Adobe Campaign將復原和刪除元素。

* **applicatedIf（字串）**:考量索引的條件 — 接收XTK運算式。
* **標籤（字串）**:索引標籤。
* **name(MNTOKEN)**:唯一索引名稱。
* **唯一（布林值）**:如果激活了此選項(@unique=&quot;true&quot;)，則屬性保證索引在其整個欄位中的唯一性。

## 範例 {#examples-3}

在&quot;id&quot;欄位上建立索引。 (「@unique」屬性 `<dbindex>` 在資料庫（查詢）中建立索引時，元素會觸發添加&quot;UNIQUE&quot; SQL關鍵字。

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

在&quot;@mail&quot;和&quot;@phoneNumber&quot;欄位上建立複合索引：

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
