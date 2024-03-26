---
product: campaign
title: 元素和屬性 — dbindex元素
description: dbindex元素
feature: Schema Extension
exl-id: d7d1e427-12e0-4f07-9e01-d184dbe2ebf1
source-git-commit: fd5e4bbc87a48f029a09b14ab1d927b9afe4ac52
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---

# dbindex元素 {#dbindex--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-3}

dbindex：==keyfield

## 屬性 {#attributes-3}

* @_operation （字串）
* @applicableIf （字串）
* @label （字串）
* @name (MNTOKEN)
* @unique （布林值）

## 父項 {#parents-3}

`<element>`

## 子系 {#children-3}

`<keyfield>`

## 說明 {#description-3}

此元素可讓您定義連結至表格的索引。

## 使用與使用內容 {#use-and-context-of-use-3}

可以定義多個索引。 一個索引可以參考資料表的一或多個欄位。 索引宣告通常遵循主要結構描述元素的定義。

的順序 `<keyfield>` 在中定義的元素 `<dbindex>` 非常重要。 第一個 `<keyfield>` 必須是查詢主要依據的索引標準。

資料庫中索引的名稱是透過串連資料表的名稱和索引的名稱來計算的。 例如：資料表名稱&quot;Sample&quot;、名稱空間&quot;Cus&quot;、索引名稱&quot;MyIndex&quot;->建立索引期間索引欄位的名稱查詢：&quot;CusSample_myIndex&quot;。

## 屬性說明 {#attribute-description-3}

* **操作（字串）(_O)**：定義資料庫中的寫入型別。

  此屬性主要用於擴充現成可用的結構描述。

  可存取的值包括：

   * &quot;none&quot;：僅調解。 這表示Adobe Campaign將會復原元素，而不會更新元素，如果元素不存在則會產生錯誤。
   * &quot;insertOrUpdate&quot;：以插入更新。 這表示Adobe Campaign將更新元素，或如果元素不存在則建立元素。
   * &quot;insert&quot;： insertion. 這表示Adobe Campaign會插入元素，而不檢查元素是否存在。
   * &quot;update&quot;：更新。 這表示Adobe Campaign將更新元素，如果元素不存在則會產生錯誤。
   * &quot;delete&quot;：刪除。 這表示Adobe Campaign將復原和刪除元素。

* **appliedIf （字串）**：考慮索引的條件 — 接收XTK運算式。
* **標籤（字串）**：索引標籤。
* **名稱(MNTOKEN)**：唯一索引名稱。
* **唯一（布林值）**：如果已啟用此選項(@unique=&quot;true&quot;)，屬性會保證其欄位中索引的唯一性。

## 範例 {#examples-3}

在「id」欄位上建立索引。 (上的「@unique」屬性 `<dbindex>` 在資料庫中建立索引時，元素會觸發新增「唯一」SQL關鍵字（查詢）。

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
