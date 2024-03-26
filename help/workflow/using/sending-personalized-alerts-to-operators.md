---
product: campaign
title: 傳送個人化警示給營運商
description: 瞭解如何傳送個人化警示給營運商
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 4%

---

# 傳送個人化警示給營運商{#sending-personalized-alerts-to-operators}



在此範例中，我們想傳送警報給運運算元，該警報會包含開啟電子報但未點按其中所含連結的設定檔名稱。

設定檔的名字和姓氏欄位會連結至 **[!UICONTROL Recipients]** 目標維度，而 **[!UICONTROL Alert]** 活動已連結至 **[!UICONTROL Operator]** 目標維度。 因此，兩個目標維度之間沒有可用的欄位來執行調解，並擷取名字和姓氏欄位，以及將它們顯示在警報活動中。

建立工作流程的過程如下：

1. 使用 **[!UICONTROL Query]** 活動以鎖定資料。
1. 新增 **[!UICONTROL JavaScript code]** 活動放入工作流程，以將查詢的母體儲存至執行個體變數。
1. 使用 **[!UICONTROL Test]** 活動以檢查母體計數。
1. 使用 **[!UICONTROL Alert]** 活動以傳送警報給運運算元，視 **[!UICONTROL Test]** 活動結果。

![](assets/uc_operator_1.png)

## 將母體儲存至執行個體變數 {#saving-the-population-to-the-instance-variable}

將下列程式碼新增至 **[!UICONTROL JavaScript code]** 活動。

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

* 此 **[!UICONTROL queryDef schema]** 標籤應該對應到查詢活動中所使用目標維度的名稱。
* 此 **[!UICONTROL node expr]** 標籤應該對應至您要擷取的欄位名稱。

![](assets/uc_operator_3.png)

若要擷取這些資訊，請遵循下列步驟：

1. 在中的出站轉變上按一下滑鼠右鍵 **[!UICONTROL Query]** 活動，然後選取 **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. 在清單上按一下滑鼠右鍵，然後選取 **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. 查詢目標維度和欄位名稱會顯示在清單中。

   ![](assets/uc_operator_6.png)

## 測試母體計數 {#testing-the-population-count}

將下列程式碼新增至 **[!UICONTROL Test]** 活動以檢查目標母體是否包含至少1個設定檔。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 設定警報 {#setting-up-the-alert}

現在，母體已新增至具有所需欄位的執行個體變數中，您可以將這些資訊新增至 **[!UICONTROL Alert]** 活動。

若要這麼做，請將新增至 **[!UICONTROL Source]** 將程式碼標籤在底下：

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
>此 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** command可讓您新增已透過以下專案儲存至執行個體變數的其中一個欄位： **[!UICONTROL JavaScript code]** 活動。\
>只要欄位已插入JavaScript程式碼中，您就可以視需要新增任意數目的欄位。

![](assets/uc_operator_8.png)
