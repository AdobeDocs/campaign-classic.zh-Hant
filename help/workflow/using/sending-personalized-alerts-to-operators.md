---
product: campaign
title: 傳送個人化警示給營運商
description: 瞭解如何傳送個人化警示給營運商
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 2%

---

# 傳送個人化警示給營運商{#sending-personalized-alerts-to-operators}



在此範例中，我們想傳送警報給運運算元，該警報會包含開啟電子報但未點按其中所含連結的設定檔名稱。

設定檔的名字和姓氏欄位已連結至&#x200B;**[!UICONTROL Recipients]**&#x200B;目標維度，而&#x200B;**[!UICONTROL Alert]**&#x200B;活動已連結至&#x200B;**[!UICONTROL Operator]**&#x200B;目標維度。 因此，兩個目標維度之間沒有可用的欄位來執行調解，並擷取名字和姓氏欄位，以及將它們顯示在警報活動中。

建立工作流程的過程如下：

1. 使用&#x200B;**[!UICONTROL Query]**&#x200B;活動來鎖定資料。
1. 將&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動新增至工作流程，以將查詢的母體儲存至執行個體變數。
1. 使用&#x200B;**[!UICONTROL Test]**&#x200B;活動檢查母體計數。
1. 根據&#x200B;**[!UICONTROL Test]**&#x200B;活動結果，使用&#x200B;**[!UICONTROL Alert]**&#x200B;活動傳送警示給運運算元。

![](assets/uc_operator_1.png)

## 將母體儲存至執行個體變數 {#saving-the-population-to-the-instance-variable}

將下列程式碼新增至&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動。

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

請確定Javascript程式碼對應於您的工作流程資訊：

* **[!UICONTROL queryDef schema]**&#x200B;標籤應該對應到查詢活動中使用的目標維度名稱。
* **[!UICONTROL node expr]**&#x200B;標籤應該對應至您要擷取的欄位名稱。

![](assets/uc_operator_3.png)

若要擷取這些資訊，請遵循下列步驟：

1. 以滑鼠右鍵按一下&#x200B;**[!UICONTROL Query]**&#x200B;活動的出站轉變，然後選取&#x200B;**[!UICONTROL Display the target]**。

   ![](assets/uc_operator_4.png)

1. 在清單上按一下滑鼠右鍵，然後選取&#x200B;**[!UICONTROL Configure list]**。

   ![](assets/uc_operator_5.png)

1. 查詢目標維度和欄位名稱會顯示在清單中。

   ![](assets/uc_operator_6.png)

## 測試母體計數 {#testing-the-population-count}

將下列程式碼新增至&#x200B;**[!UICONTROL Test]**&#x200B;活動，以檢查目標母體是否包含至少1個設定檔。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 設定警報 {#setting-up-the-alert}

現在，母體已新增到具有所需欄位的執行個體變數中，您可以將這些資訊新增到&#x200B;**[!UICONTROL Alert]**&#x200B;活動中。

若要這麼做，請在&#x200B;**[!UICONTROL Source]**&#x200B;索引標籤中新增下列程式碼：

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
>**[!UICONTROL <%= item.target.recipient.@fieldName %>]**&#x200B;命令可讓您新增已透過&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動儲存至執行個體變數的其中一個欄位。\
>只要欄位已插入JavaScript程式碼中，您就可以新增所需數量的欄位。

![](assets/uc_operator_8.png)
