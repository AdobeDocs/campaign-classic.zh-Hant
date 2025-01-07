---
product: campaign
title: 元素和屬性 — srcschema元素
description: 元素和屬性
feature: Schema Extension
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: bc4329b4-d272-4d32-bdaa-290cb9912af4
source-git-commit: 254c89490fefa5d405bcecd2f1781df46450a873
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 1%

---

# srcschema元素 {#srcschema--element}


## 內容模型 {#content-model-14}

srcSchema：==(屬性 | createdBy | 資料 | 元素 | 分項清單 | 說明 | 介面 | 方法 | modifiedby)

## 屬性 {#attributes-14}

created (datetime)、createdBy-id (long)、desc (string)、entitySchema (string)、extendedSchema (string)、img (string)、implements (string)、label (string)、labelSingular (string)、lastModified (datetime)、library (boolean)、mappingType (string)、modifiedBy-id (long)、name (string)、namespace (string)、useRecycleBin （布林）、view (view (boolean)、xtkschema (string)

## 父項 {#parents-14}

無

## 子系 {#children-14}

* `<attribute>`
* `<createdby>`
* `<data>`
* `<element>`
* `<enumeration>`
* `<help>`
* `<interface>`
* `<methods>`
* `<modifiedby>`

## 說明 {#description-14}

`<srcschema>`是結構描述的根元素。 這是結構描述定義的輸入點。

## 使用與使用內容 {#use-and-context-of-use-9}

結構描述簡報可在[關於結構描述參考](../../../configuration/using/about-schema-reference.md)和[結構描述結構](../../../configuration/using/schema-structure.md)中使用。

## 屬性說明 {#attribute-description-14}

* **已建立（日期時間）**：此屬性提供有關建立結構描述的日期與時間的資訊。 它有「日期時間」表單。 顯示的值取自伺服器。 時間會以UTC格式顯示。
* **createdBy-id (long)**：是建立結構描述之運運算元的識別碼。
* **desc （字串）**：結構描述描述
* **entitySchema （字串）**：以語法和核准為基礎的基本結構描述(Adobe Campaign預設為：xtk：srcSchema)。 儲存目前的結構描述時，Adobe Campaign會核准其在@xtkschema屬性中宣告之結構描述的文法。
* **extendedSchema （字串）**：接收目前結構描述擴充功能所根據的現成結構描述名稱。 形式為「namespace：name」。
* **img （字串）**：連結至結構描述的圖示（可能在結構描述建立助理中定義）。
* **標籤（字串）**：結構描述標籤。
* **labelSingular （字串）**：在介面中顯示的標籤(singular)。
* **lastModified (datetime)**：此屬性提供上次修改日期與時間的資訊。 它有「日期時間」表單。 顯示的值取自伺服器。 時間會以UTC格式顯示。
* **資料庫（布林值）**：使用結構描述做為資料庫，而不是實體。 因此，由於「@ref」和「@template」屬性，此結構描述可能會被其他結構描述參考。
* **mappingType （字串）**：

   * &quot;sql&quot;：資料庫對應
   * &quot;textFile&quot;：文字檔對應
   * 「xmlFile」： XML格式文字檔案對應
   * &quot;binaryFile&quot;：二進位檔案對應

* **modifiedBy-id (long)**：符合變更結構描述之運運算元的識別碼。
* **名稱（字串）**：唯一的結構描述名稱。
* **名稱空間（字串）**：結構描述的名稱空間（預設： nms， xtk， nl）。 為專案建立新結構描述時，我們建議您使用專用的名稱空間。
* **useRecycleBin （布林值）**：啟用應用程式中的垃圾桶功能。 刪除的記錄將會在最終刪除之前被放置在垃圾桶中。 此函式僅適用於「傳送」模式。
* **檢視（布林值）**：如果啟用(@view=&quot;true&quot;)，則會將結構描述當做檢視。 資料庫結構更新輔助程式不會將結構描述列入考量。 此選項主要用於參照外部表格。
* **xtkschema （字串）**：定義結構描述文法的結構描述名稱（預設為xtk：srcSchema）。

## 範例 {#examples-11}

「nms：delivery」現成結構描述的`<srcschema>`元素

```
<srcSchema desc="Defines all the settings of a delivery (or delivery template)."  
           entitySchema="xtk:srcSchema" img="nms:campaign.png" implements="xtk:persist" 
           label="Diffusions" labelSingular="Diffusion" md5="DCD2164CD0276B1DCA6E1C9E2A75EC04"
           name="delivery" namespace="nms" useRecycleBin="true" xtkschema="xtk:srcSchema">
```
