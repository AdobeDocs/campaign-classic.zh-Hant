---
product: campaign
title: 元素和屬性
description: 元素和屬性
audience: configuration
content-type: reference
topic-tags: schema-reference
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 34404fbe935e68f3cc11d937839209443ad4ca60
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 3%

---

# 方法元素 {#method--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-10}

方法：==(幫助 |參數)

## 屬性 {#attributes-10}

* @_operation（字串）
* @access（字串）
* @const（布林值）
* @hidden（布林值）
* @label（字串）
* @library（字串）
* @name(MNTOKEN)
* @pkonly（布林值）
* @static（布林值）

## 父母 {#parents-10}

`<methods>`  ,  `<interface />`

## 兒童 {#children-10}

* `<help>`
* `<parameters>`

## 說明 {#description-10}

此元素可讓您定義SOAP方法。

## 使用與使用內容 {#use-and-context-of-use-7}

SOAP方法啟用應用程式進程。

聲明新方法（非本機）時，必須使用「@library」：命名空間和用於程式庫的名稱與聲明所在架構的命名空間和名稱無關。

## 屬性說明 {#attribute-description-10}

* **存取（字串）**:此屬性定義使用方法的訪問控制。如果此屬性遺失，則必須進行識別。 可用值包括：&#39;anonymous&#39;、&#39;admin&#39;和&#39;sql&#39;。
* **const（布林值）**:如果激活，此屬性表示聲明的方法將更改實體
* **標籤（字串）**:方法的標籤。
* **程式庫（字串）**:此方法不是應用程式的原生方法。此屬性會取用找到方法定義的方法程式庫(nms:mylibrary.js)的值。
* **name(MNTOKEN)**:唯一方法名稱。
* **靜態（布林值）**:如果激活了此屬性，則該方法被視為自主，則調用該屬性時必須將所有參數指定給該方法。

## 範例 {#examples-7}

「訂閱」的現成可用方法定義：

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
