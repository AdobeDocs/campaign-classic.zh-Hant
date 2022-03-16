---
product: campaign
title: 架構元素和屬性 — 方法元素
description: 方法元素
exl-id: 0fb74318-fe09-473c-8e33-1f3afd66b4cc
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---

# 方法元素 {#method--element}

![](../../../assets/v7-only.svg)

## 內容模型 {#content-model-10}

方法：==（幫助） |參數)

## 屬性 {#attributes-10}

* @_operation（字串）
* @access（字串）
* @const（布爾值）
* @hidden（布爾值）
* @label（字串）
* @library（字串）
* @name(MNTOKEN)
* @pkonly（布爾值）
* @static（布爾值）

## 父母 {#parents-10}

`<methods>`  ,  `<interface />`

## 兒童 {#children-10}

* `<help>`
* `<parameters>`

## 說明 {#description-10}

此元素用於定義SOAP方法。

## 使用和使用上下文 {#use-and-context-of-use-7}

SOAP方法啟用應用程式進程。

聲明新方法（非本機）時，「@library」是必需的：用於庫的命名空間和名稱獨立於聲明所在架構的命名空間和名稱。

## 屬性說明 {#attribute-description-10}

* **訪問（字串）**:此屬性定義使用該方法的訪問控制。 如果缺少此屬性，則必須進行標識。 可用值包括：「anonymous」、「admin」和「sql」。
* **const（布爾值）**:如果激活，則此屬性表示聲明的方法將更改實體
* **標籤（字串）**:的子菜單。
* **庫（字串）**:此方法不是應用程式固有的。 此屬性取值找到方法定義的方法庫(nms:mylibrary.js)。
* **名稱(MNTOKEN)**:唯一方法名稱。
* **靜態（布爾值）**:如果激活了此屬性，則該方法被視為自主方法，則調用該屬性時必須為該方法指定所有參數。

## 範例 {#examples-7}

「訂閱」框外方法的定義：

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
