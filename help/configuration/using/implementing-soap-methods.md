---
title: 實施SOAP方法
seo-title: 實施SOAP方法
description: 實施SOAP方法
seo-description: null
page-status-flag: never-activated
uuid: c9366f4e-460d-4087-88f7-9cc6d0de597a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: api
discoiquuid: 76984d9d-7759-4e0f-a275-09cca27589fa
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7ff12260d875b85256c8678fa8d100fd355398e

---


# 實施SOAP方法{#implementing-soap-methods}

## 簡介 {#introduction}

可在JavaScript中建立SOAP方法。 該功能簡單地啟用了應用程式進程，避免了在表單中開發JSP及其調用。

這些SOAP方法的行為方式與應用程式中原生定義的方法相同。 支援相同的屬性：靜態、僅密鑰和const。

## 定義方法庫 {#defining-a-method-library}

建立方法庫涉及兩個階段：

* SOAP方法聲明，
* JavaScript中的定義（或實作）。

### 聲明 {#declaration}

首先，在架構中聲明方法(有關如何建立和編輯架構的詳細資訊，請參 [閱本節](../../configuration/using/about-schema-edition.md))。

其聲明與原生方法的聲明類似，但您需要添加&#39;library&#39;屬性，指定定義所在的方法庫的名稱。

此名稱與「JavaScript代碼」類型實體的名稱（與名稱空間）一致。

例如：

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
>用於庫的名稱空間和名稱獨立於找到聲明的名稱空間和架構名稱。

### 定義 {#definition}

SOAP方法以JavaScript函式的形式實施，這些函式被分組在表示庫的指令碼中。

>[!NOTE]
>
>方法庫可以對各種模式的函式進行分組，反之亦然，一個模式的函式可以在單獨的庫中定義。

指令碼可包含在初始程式庫載入期間要執行的程式碼。

**1. 名稱**

函式的名稱必須符合下列格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

例如：

下列JavaScript函式是上述方法的實作。 它應使用「cus:test」名稱在「JavaScript程式碼」類型實體中定義。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2. 簽名**

函式的簽名必須包含聲明中每個&#39;in&#39;或&#39;inout&#39;參數的引數。

特定案例：

* **非靜態方法**:函式必須首先包含一個附加引數，與以&#39;xml&#39;(E4X)類型對象形式傳遞的XML實體一致。
* **&quot;key only&quot;類型方法**:函式必須首先包含一個附加引數，與以字串形式傳遞的鍵一致。

**3. 傳回的值**

函式必須傳回每個&#39;out&#39;或&#39;inout&#39;類型參數的值。 具體案例：如果聲明方法時沒有任何&#39;static&#39;、&#39;key only&#39;或&#39;const&#39;屬性，則第一個返回的值必須與修改的實體一致。 可以返回新對象或返回第一個修改的參數。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

若要傳回數個值，這些值必須顯示在表格中。

例如：

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```

