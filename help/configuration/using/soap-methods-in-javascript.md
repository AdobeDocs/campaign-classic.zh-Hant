---
product: campaign
title: JavaScript 中的 SOAP 方法
description: JavaScript 中的 SOAP 方法
exl-id: 62020447-fe59-4363-994d-de4d8032bbd7
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---

# JavaScript 中的 SOAP 方法{#soap-methods-in-javascript}

![](../../assets/v7-only.svg)

這是在Adobe Campaign伺服器上執行的JavaScript。

## 靜態方法 {#static-methods}

通過調用表示架構的對象上的方法來訪問靜態SOAP方法。 架構是「namespace」對象的屬性。 這些命名空間是全局變數，因此，例如，xtk或nms變數表示相應的命名空間

以下示例調用xtk:workflow架構的靜態PostEvent方法：

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## 非靜態方法 {#non-static-methods}

要使用非靜態SOAP方法，必須首先使用相應架構上的&quot;get&quot;或&quot;create&quot;方法檢索實體。

以下示例調用&quot;xtk:queryDef&quot;架構的ExecuteQuery方法：

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

* 對具有「get」操作的收件人表進行查詢：

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

* 使用「select」操作查詢收件人表：

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

* 將資料寫入收件人表：

   ```
   xtk.session.Write(<recipient _operation="insert" lastName="Martinez" firstName="Peter" xtkschema="nms:recipient"/>);
   ```
