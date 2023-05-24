---
product: campaign
title: 結構描述元素和屬性 — 方法元素
description: 方法元素
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 1%

---

# 方法元素 {#method--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-10}

方法：==(說明 |引數)

## 屬性 {#attributes-10}

* @_operation （字串）
* @access （字串）
* @const （布林值）
* @hidden （布林值）
* @label （字串）
* @library （字串）
* @name (MNTOKEN)
* @pkonly （布林值）
* @static （布林值）

## 父項 {#parents-10}

`<methods>`  ,  `<interface />`

## 子系 {#children-10}

* `<help>`
* `<parameters>`

## 說明 {#description-10}

此元素可讓您定義SOAP方法。

## 使用與使用內容 {#use-and-context-of-use-7}

SOAP方法可啟用應用程式處理作業。

宣告新方法（非原生方法）需要「@library」：用於程式庫的名稱空間和名稱與宣告所在的結構描述名稱空間和名稱無關。

## 屬性說明 {#attribute-description-10}

* **存取（字串）**：此屬性會定義使用方法的存取控制。 如果缺少此屬性，則必須進行識別。 可用值為： &#39;anonymous&#39;、&#39;admin&#39;和&#39;sql&#39;。
* **常數（布林值）**：如果已啟動，此屬性表示宣告的方法將變更實體
* **標籤（字串）**：方法的標籤。
* **資料庫（字串）**：此方法不是應用程式的原生方法。 此屬性會採用找到方法定義的方法程式庫的值(nms：mylibrary.js)。
* **名稱(MNTOKEN)**：唯一方法名稱。
* **靜態（布林值）**：如果此屬性已啟用，則會將方法視為自主方法，呼叫方法時必須指定所有引數給方法。

## 範例 {#examples-7}

「訂閱」現成方法的定義：

```
 
<method name="Subscribe" static="true">
      <help>Creation of update of a recipient's subscription to an information service</help>
      <parameters>
        <param desc="Name of the information service(s) (separated with commas)"
               name="serviceName" type="string"/>
        <param desc="Recipient to subscribe and possibly create" name="recipient"
               type="DOMElement"/>
        <param desc="Create the recipient if they don't exist" name="create" type="boolean"/>
      </parameters>     
    </method>
```
