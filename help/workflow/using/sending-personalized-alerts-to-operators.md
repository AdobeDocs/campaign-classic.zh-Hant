---
title: 傳送個人化警報給營運商
seo-title: 傳送個人化警報給營運商
description: 傳送個人化警報給營運商
seo-description: null
page-status-flag: never-activated
uuid: 10dd46b9-df28-4043-91f9-c9316a7c69d3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: use-cases
discoiquuid: 4d72db10-29bd-4b3c-adb3-bead02890271
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 傳送個人化警報給營運商{#sending-personalized-alerts-to-operators}

在此範例中，我們想傳送警報給運算子，該運算子將包含開啟電子報但未點按其所含連結的設定檔名稱。

描述檔的名字和姓氏欄位會連結至定 **[!UICONTROL Recipients]** 位維度，而活 **[!UICONTROL Alert]** 動則會連結至定 **[!UICONTROL Operator]** 位維度。 因此，兩個定位維度之間沒有可用的欄位可執行協調並擷取名字和姓氏欄位，並在「警報」活動中顯示欄位。

此程式是建立工作流程，如下所示：

1. 使用活 **[!UICONTROL Query]** 動來定位資料。
1. 將活動 **[!UICONTROL JavaScript code]** 新增至工作流程，以將查詢中的填入項目儲存至例項變數。
1. 使用活 **[!UICONTROL Test]** 動檢查人口計數。
1. 根據 **[!UICONTROL Alert]** 活動結果，使用活動向操作員發送 **[!UICONTROL Test]** 警報。

![](assets/uc_operator_1.png)

## 將人口儲存至例項變數 {#saving-the-population-to-the-instance-variable}

將下列程式碼新增至活 **[!UICONTROL JavaScript code]** 動。

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

* 標 **[!UICONTROL queryDef schema]** 記應與查詢活動中使用的定位維的名稱相對應。
* 標 **[!UICONTROL node expr]** 記應與您要擷取之欄位的名稱對應。

![](assets/uc_operator_3.png)

要檢索這些資訊，請執行以下步驟：

1. 按一下右鍵活動中的出站轉 **[!UICONTROL Query]** 換，然後選擇 **[!UICONTROL Display the target]**。

   ![](assets/uc_operator_4.png)

1. 按一下右鍵清單，然後選擇 **[!UICONTROL Configure list]**。

   ![](assets/uc_operator_5.png)

1. 查詢定位維和欄位名稱顯示在清單中。

   ![](assets/uc_operator_6.png)

## 測試人口計數 {#testing-the-population-count}

將下列程式碼新增至活 **[!UICONTROL Test]** 動，以檢查目標人口是否至少包含1個描述檔。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 設定警報 {#setting-up-the-alert}

現在，人口已新增至包含所需欄位的例項變數中，您可以將這些資訊新增至活 **[!UICONTROL Alert]** 動。

若要這麼做，請將下列程式 **[!UICONTROL Source]** 碼新增至標籤：

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
>此命 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** 令可讓您新增其中一個已透過活動儲存至例項變數的欄 **[!UICONTROL JavaScript code]** 位。\
>只要欄位已插入JavaScript程式碼，您就可以視需要新增欄位。

![](assets/uc_operator_8.png)

