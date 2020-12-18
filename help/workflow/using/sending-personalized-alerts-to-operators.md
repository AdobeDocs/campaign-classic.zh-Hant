---
solution: Campaign Classic
product: campaign
title: 傳送個人化警報給營運商
description: 瞭解如何傳送個人化警報給營運商
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---


# 傳送個人化警報給營運商{#sending-personalized-alerts-to-operators}

在此範例中，我們想傳送警報給運算子，該運算子將包含開啟電子報但未點按其所含連結的設定檔名稱。

描述檔的名字和姓氏欄位會連結至&#x200B;**[!UICONTROL Recipients]**&#x200B;定位維度，而&#x200B;**[!UICONTROL Alert]**&#x200B;活動則會連結至&#x200B;**[!UICONTROL Operator]**&#x200B;定位維度。 因此，兩個定位維度之間沒有可用的欄位可執行協調並擷取名字和姓氏欄位，並在「警報」活動中顯示欄位。

此程式是建立工作流程，如下所示：

1. 使用&#x200B;**[!UICONTROL Query]**&#x200B;活動來定位資料。
1. 將&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動新增至工作流程，將查詢中的填入項目儲存至例項變數。
1. 使用&#x200B;**[!UICONTROL Test]**&#x200B;活動檢查人口計數。
1. 根據&#x200B;**[!UICONTROL Test]**&#x200B;活動結果，使用&#x200B;**[!UICONTROL Alert]**&#x200B;活動向操作員發送警報。

![](assets/uc_operator_1.png)

## 將人口儲存至例項變數{#saving-the-population-to-the-instance-variable}

將下面的代碼添加到&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動中。

```
var query = xtk.queryDef.create(  
    <queryDef schema="temp:query" operation="select">  
      <select>  
       <node expr="[target/recipient.@firstName]"/>  
       <node expr="[target/recipient.@lastName]"/>  
      </select>  
     </queryDef>  
  );  
  var items = query.ExecuteQuery();
```

請確定Javascript程式碼與您的工作流程資訊相符：

* **[!UICONTROL queryDef schema]**&#x200B;標籤應與查詢活動中使用的定位維的名稱相對應。
* **[!UICONTROL node expr]**&#x200B;標籤應與要檢索的欄位的名稱相對應。

![](assets/uc_operator_3.png)

要檢索這些資訊，請執行以下步驟：

1. 按一下右鍵&#x200B;**[!UICONTROL Query]**&#x200B;活動的出站轉移，然後選擇&#x200B;**[!UICONTROL Display the target]**。

   ![](assets/uc_operator_4.png)

1. 按一下右鍵清單，然後選擇&#x200B;**[!UICONTROL Configure list]**。

   ![](assets/uc_operator_5.png)

1. 查詢定位維和欄位名稱顯示在清單中。

   ![](assets/uc_operator_6.png)

## 測試人口計數{#testing-the-population-count}

將下列程式碼新增至&#x200B;**[!UICONTROL Test]**&#x200B;活動，以檢查目標人口是否至少包含1個描述檔。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 設定警報{#setting-up-the-alert}

現在，人口已新增至包含所需欄位的例項變數中，您可以將這些資訊新增至&#x200B;**[!UICONTROL Alert]**&#x200B;活動。

若要這麼做，請新增至以下程式碼的&#x200B;**[!UICONTROL Source]**&#x200B;標籤：

```
<ul>
<%
var items = new XML(instance.vars.items)
for each (var item in items){
%>
<li><%= item.target.@firstName %> <%= item.target.@lastName %></li>
<%
} %></ul>
```

>[!NOTE]
>
>**[!UICONTROL <%= item.target.recipient.@fieldName %>]**&#x200B;命令可讓您新增其中一個已透過&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動儲存至例項變數的欄位。\
>只要欄位已插入JavaScript程式碼，您就可以視需要新增欄位。

![](assets/uc_operator_8.png)

