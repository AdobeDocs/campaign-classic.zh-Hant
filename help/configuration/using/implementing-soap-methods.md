---
product: campaign
title: 實施 SOAP 方法
description: 實施 SOAP 方法
audience: configuration
content-type: reference
topic-tags: api
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 4%

---

# 實施 SOAP 方法{#implementing-soap-methods}

![](../../assets/v7-only.svg)

## 簡介 {#introduction}

可以在JavaScript中建立SOAP方法。 該函式僅支援應用程式，它可以避免開發JSP及其在表單中的調用。

這些SOAP方法的行為與應用程式中原生定義的方法相同。 支援相同的屬性：靜態、僅鍵和const。

## 定義方法庫 {#defining-a-method-library}

建立方法庫涉及兩個階段：

* SOAP方法聲明，
* JavaScript中的定義（或實作）。

### 聲明 {#declaration}

首先，在結構中聲明方法(有關如何建立和編輯結構的詳細資訊，請參閱 [本節](../../configuration/using/about-schema-edition.md))。

其聲明與原生方法的聲明類似，只是您需要新增&#39;library&#39;屬性，指定定義所在之方法程式庫的名稱。

此名稱與「JavaScript程式碼」類型實體的名稱（與命名空間）一致。

範例:

testLog(msg)方法在nms:recipient擴展中聲明

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>命名空間和用於程式庫的名稱與找到聲明的命名空間和架構名稱無關。

### 定義 {#definition}

SOAP方法是以JavaScript函式的形式實施，這些函式被分組到代表程式庫的指令碼中。

>[!NOTE]
>
>方法程式庫可以對各種架構的函式進行分組，反之亦然，則可在個別程式庫中定義一個架構的函式。

指令碼可包含要在初始程式庫載入期間執行的程式碼。

**1. 名稱**

函式的名稱必須符合下列格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

範例:

下列JavaScript函式為上述方法的實施。 應使用「cus:test」名稱，在「JavaScript程式碼」類型實體中定義。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 簽名**

函式的簽名必須包含聲明中每個「in」或「inout」參數的參數。

特定案例：

* **非靜態方法**:函式必須先包含其他引數，與以&#39;xml&#39;(E4X)類型物件形式傳遞的XML實體一致。
* **&quot;僅限鍵&quot;類型方法**:函式必須先包含其他引數，並與以字元字串形式傳遞的索引鍵一致。

**3. 傳回的值**

函式必須傳回每個「out」或「inout」類型參數的值。 具體案例：如果在聲明方法時未使用「static」、「key only」或「const」屬性，則第一個返回值必須與修改的實體一致。 可以返回新對象或返回第一個修改的參數。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

若要傳回數個值，必須在表格中顯示。

範例:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
