---
product: campaign
title: JavaScript 中的 SOAP 方法
feature: Configuration, Instance Settings
description: JavaScript 中的 SOAP 方法
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於Campaign Classic v7"
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '143'
ht-degree: 9%

---

# JavaScript 中的 SOAP 方法{#soap-methods-in-javascript}

這是在Adobe Campaign伺服器上執行的JavaScript。

## 靜態方法 {#static-methods}

靜態SOAP方法可透過在代表綱要的物件上叫用方法來存取。 結構描述是「namespace」物件的屬性。 這些名稱空間是全域變數，因此，例如，xtk或nms變數代表對應的名稱空間

以下範例會叫用xtk：workflow綱要的靜態PostEvent方法：

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## 非靜態方法 {#non-static-methods}

若要使用非靜態SOAP方法，必須先在對應結構描述上使用「get」或「create」方法擷取實體。

下列範例會叫用「xtk：queryDef」結構描述的ExecuteQuery方法：

```
var query = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
    </select>
  </queryDef>
)

var res = query.ExecuteQuery()

for each (var w in res.workflow) 
  logInfo(w.@internalName)
```

## 範例 {#examples}

* 使用「取得」作業查詢收件者表格：

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="get">    
      <select>      
        <node expr="@firstName"/>      
        <node expr="@lastName"/>      
        <node expr="@email"/>    
      </select>    
      <where>      
        <condition expr="@email = 'peter.martinez@adobe.com'"/>    
      </where>  
    </queryDef>)
  
  var recipient = query.ExecuteQuery()
  
  logInfo(recipient.@firstName)
  logInfo(recipient.@lastName)
  ```

* 使用「選取」作業查詢收件者表格：

  ```
  var query = xtk.queryDef.create(  
    <queryDef schema="nms:recipient" operation="select">    
      <select>      
        <node expr="@email"/>      
        <node expr="@lastName"/>      
        <node expr="@firstName"/>    
      </select>    
      <where>      
        <condition expr="@age > 25"/>    
      </where>    
    </queryDef>)
  
  var res = query.ExecuteQuery()
  
  for each (var recipient in res.recipient) 
  {  
    logInfo(recipient.@email)  
    logInfo(recipient.@firstName)  
    logInfo(recipient.@lastName)
  }
  ```

* 將資料寫入收件者表格：

  ```
  xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
  ```
