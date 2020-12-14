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
source-wordcount: '205'
ht-degree: 3%

---


# 方法元素{#method--element}

## 內容模型{#content-model-10}

方法：==(help |參數)

## 屬性{#attributes-10}

* @_operation（字串）
* @access（字串）
* @const（布林值）
* @hidden（布林值）
* @label（字串）
* @library（字串）
* @name(MNTOKEN)
* @pkonly（布林值）
* @static（布林值）

## 父代{#parents-10}

`<methods>`  ,  `<interface />`

## 子項{#children-10}

* `<help>`
* `<parameters>`

## 說明 {#description-10}

此元素可讓您定義SOAP方法。

## 使用與使用內容{#use-and-context-of-use-7}

SOAP方法可啟用應用程式程式。

宣告新方法（非原生）時，必須使用「@library」:namespace和用於庫的名稱獨立於聲明所在的架構的名稱空間和名稱。

## 屬性說明{#attribute-description-10}

* **存取（字串）**:此屬性定義使用方法的訪問控制。如果此屬性遺失，則必須進行識別。 可用值包括：&#39;anonymous&#39;、&#39;admin&#39;和&#39;sql&#39;。
* **const（布林值）**:如果激活了該屬性，則此屬性表示聲明的方法將改變實體
* **標籤（字串）**:標籤。
* **程式庫（字串）**:此方法不是應用程式的原生方法。此屬性使用找到方法定義的方法庫(nms:mylibrary.js)的值。
* **名稱(MNTOKEN)**:唯一方法名稱。
* **靜態（布林值）**:如果激活了此屬性，則方法被視為自治，在調用該屬性時，必須將所有參數指定給該方法。

## 範例 {#examples-7}

「訂閱」現成可用方法的定義：

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
