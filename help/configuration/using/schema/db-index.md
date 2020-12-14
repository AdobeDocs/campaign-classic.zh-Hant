---
solution: Campaign Classic
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
translation-type: tm+mt
source-git-commit: 922257b157f8d76d6e703b0510ff689d1aa4d067
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 2%

---


# dbindex元素{#dbindex--element}

## 內容模型{#content-model-3}

dbindex:==keyfield

## 屬性{#attributes-3}

* @_operation（字串）
* @applicableIf（字串）
* @label（字串）
* @name(MNTOKEN)
* @unique（布林值）

## 父代{#parents-3}

`<element>`

## 子項{#children-3}

`<keyfield>`

## 說明 {#description-3}

此元素可讓您定義連結至表格的索引。

## 使用與使用內容{#use-and-context-of-use-3}

可以定義多個索引。 一個索引可以引用表的一個或多個欄位。 索引聲明通常遵循主模式元素的定義。

`<dbindex>`中定義的`<keyfield>`元素的順序非常重要。 第一個`<keyfield>`必須是查詢主要基於的索引標準。

資料庫中索引的名稱是通過串連表的名稱和索引的名稱來計算的。 例如：建立索引查詢期間索引欄位的表名「Sample」、名稱空間「Cus」、索引名「MyIndex」->名稱：&quot;CusSample_myIndex&quot;。

## 屬性說明{#attribute-description-3}

* **_operation(string)**:定義資料庫中的寫入類型。

   此屬性主要用於擴展現成可用的架構。

   可存取的值包括：

   * 「無」:和解。 這表示Adobe Campaign將會復原元素，而不會更新元素，或在元素不存在時產生錯誤。
   * &quot;insertOrUpdate&quot;:使用插入進行更新。 這表示Adobe Campaign會更新元素，或在元素不存在時建立元素。
   * 「插入」:插入。 這表示Adobe Campaign將插入元素，而不檢查元素是否存在。
   * 「更新」:更新。 這表示Adobe Campaign會更新元素，或在元素不存在時產生錯誤。
   * 「刪除」:刪除。 這表示Adobe Campaign將會復原和刪除元素。

* **appliableIf（字串）**:條件——接收XTK運算式。
* **標籤（字串）**:索引標籤。
* **名稱(MNTOKEN)**:唯一索引名。
* **唯一（布林）**:如果激活此選項(@unique=&quot;true&quot;)，則屬性保證索引在其欄位中的唯一性。

## 範例 {#examples-3}

在「id」欄位上建立索引。 (`<dbindex>`元素上的&quot;@unique&quot;屬性在資料庫（查詢）中建立索引時觸發添加&quot;UNIQUE&quot; SQL關鍵字。)

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
