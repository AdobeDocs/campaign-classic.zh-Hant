---
product: campaign
title: 實施 SOAP 方法
description: 實施 SOAP 方法
feature: Configuration
role: Data Engineer, Developer
exl-id: 441a0e5c-fa7f-46c8-a65a-5cca4c846d43
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 3%

---

# 實作SOAP方法{#implementing-soap-methods}



## 簡介 {#introduction}

您可以在JavaScript中建立SOAP方法。 此函式只會啟用應用程式流程，可以避免在表單中開發JSP及其呼叫。

這些SOAP方法的行為方式與應用程式中原生定義的行為方式相同。 支援相同的屬性：靜態、僅金鑰和常數。

## 定義方法程式庫 {#defining-a-method-library}

建立方法程式庫涉及兩個階段：

* SOAP方法宣告，
* JavaScript中的定義（或實施）。

### 宣告 {#declaration}

首先，請在結構描述中宣告方法（如需如何建立和編輯結構描述的詳細資訊，請參閱[本節](../../configuration/using/about-schema-edition.md)）。

它們的宣告與原生方法的宣告類似，但是您必須新增「library」屬性，指定定義所在的方法程式庫名稱。

此名稱與「JavaScript程式碼」型別實體的名稱（連同名稱空間）一致。

例如：

testLog(msg)方法在nms：recipient擴充功能中宣告

```
<method name="testLog" static="true" library="cus:test">
     <parameters>
       <param name="message" type="string" inout="in"/>
     </parameters>
   </method>
```

>[!NOTE]
>
>用於程式庫的名稱空間和名稱與發現宣告的名稱空間和結構描述名稱無關。

### 定義 {#definition}

SOAP方法會以JavaScript函式的形式實作，這些函式已分組在代表程式庫的指令碼中。

>[!NOTE]
>
>方法程式庫可以為各種結構描述將函式分組，反之亦然，一個結構描述的函式可以在單獨的程式庫中定義。

指令碼可包含要在初始程式庫載入期間執行的程式碼。

**1. 名稱**

函式的名稱必須符合下列格式：

```
 <schema-namespace>_<schema-name>_<method-name>
```

例如：

下列JavaScript函式為上述方法的實作。 應使用「cus：test」名稱，在「JavaScript程式碼」型別實體中定義。

```
function nms_recipient_testLog(message)
 {
   logInfo("*** " + message)
 }
```

**2。 簽章**

函式的簽章必須為宣告的每個&#39;in&#39;或&#39;inout&#39;引數包含一個引數。

特定案例：

* **非靜態方法**：函式必須先包含額外的引數，與以&#39;xml&#39; (E4X)型別物件形式傳遞的XML實體一致。
* **「僅限索引鍵」型別方法**：函式必須先包含額外的引數，與以字元字串形式傳遞的索引鍵一致。

**3。 傳回的值**

函式必須傳回每個&#39;out&#39;或&#39;inout&#39;型別引數的值。 特定案例：如果宣告方法時不含任何「static」、「key only」或「const」屬性，則第一個傳回值必須與修改的實體一致。 可以傳回新物件或傳回第一個修改過的引數。

例如：

```
function nms_recipient_setLastName(self, name)
 {
   self.@lastName = name
   return self
 }
```

要傳回數個值時，必須將其顯示在表格中。

例如：

```
function nms_recipient_getKey(self)
 {
   return [self.@firstName, self.@lastName]
 }
```
