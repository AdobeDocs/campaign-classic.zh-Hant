---
solution: Campaign Classic
product: campaign
title: JavaScript 中的 SOAP 方法
description: JavaScript 中的 SOAP 方法
audience: configuration
content-type: reference
topic-tags: api
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '136'
ht-degree: 9%

---


# JavaScript 中的 SOAP 方法{#soap-methods-in-javascript}

這是在Adobe Campaign伺服器上執行的JavaScript。

## 靜態方法{#static-methods}

靜態SOAP方法是通過調用表示模式的對象上的方法來訪問的。 結構描述是&#39;namespace&#39;對象的屬性。 這些名稱空間是全局變數，因此，例如xtk或nms變數表示相應的名稱空間

下面的示例調用xtk:workflow模式的靜態PostEvent方法：

```
xtk.workflow.PostEvent("WKF1", "signal", "", $recipient-id='123', false) 
```

## 非靜態方法{#non-static-methods}

若要使用非靜態SOAP方法，必須先使用對應結構描述上的&quot;get&quot;或&quot;create&quot;方法來擷取實體。

下面的示例調用&quot;xtk:queryDef&quot;架構的ExecuteQuery方法：

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

* 使用&quot;get&quot;操作查詢收件者表：

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

* 在收件者表上查詢「選擇」操作：

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

