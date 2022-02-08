---
product: campaign
title: 實施 SOAP 方法
description: 實施 SOAP 方法
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 3%

---

# 實現SOAP方法{#implementing-soap-methods}

![](../../assets/v7-only.svg)

## 簡介 {#introduction}

可以在JavaScript中建立SOAP方法。 該函式簡單地使應用程式進程能夠進行，避免了在表單中開發JSP及其調用。

這些SOAP方法的行為方式與應用程式中本機定義的方法相同。 支援相同的屬性：靜態、僅鍵和常數。

## 定義方法庫 {#defining-a-method-library}

建立方法庫涉及兩個階段：

* SOAP方法聲明，
* JavaScript中的定義（或實現）。

### 聲明 {#declaration}

從在架構中聲明方法開始(有關如何建立和編輯架構的詳細資訊，請參閱 [此部分](../../configuration/using/about-schema-edition.md))。

它們的聲明與本機方法的聲明類似，但是您需要添加「library」屬性，指定定義所在的方法庫的名稱。

此名稱與「JavaScript代碼」類型實體的名稱（命名空間）一致。

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
>用於庫的命名空間和名稱與找到聲明的命名空間和架構名稱無關。

### 定義 {#definition}

SOAP方法以JavaScript函式的形式實現，該JavaScript函式在表示庫的指令碼中分組。

>[!NOTE]
>
>一種方法庫可以對各種模式的函式進行分組，或者反之亦然，可以在單獨的庫中定義一個模式的函式。

指令碼可以包含在初始庫載入期間要執行的代碼。

**1. 名稱**

函式名稱必須符合以下格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

範例:

以下JavaScript函式是上述方法的實現。 它應使用「cus:test」名稱在「JavaScript代碼」類型實體中定義。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 簽名**

函式的簽名必須包括聲明的每個「in」或「inout」參數的參數。

具體案例：

* **非靜態方法**:該函式必須首先包含附加參數，與以「xml」(E4X)類型對象形式傳遞的XML實體一致。
* **&quot;僅鍵&quot;類型方法**:該函式必須首先包含附加參數，與以字串形式傳遞的鍵一致。

**3. 返回的值**

函式必須為每個「out」或「inout」類型參數返回值。 具體案例：如果聲明方法時沒有使用任何「static」、「key only」或「const」屬性，則第一個返回的值必須與修改的實體一致。 可以返回新對象或返回第一個修改的參數。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

當要返回多個值時，它們必須顯示在表中。

範例:

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
