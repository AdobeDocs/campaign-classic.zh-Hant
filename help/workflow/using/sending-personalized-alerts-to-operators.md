---
product: campaign
title: 傳送個人化警示給營運商
description: 瞭解如何向操作員發送個性化警報
feature: Workflows
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# 傳送個人化警示給營運商{#sending-personalized-alerts-to-operators}

![](../../assets/common.svg)

在此示例中，我們要向操作員發送警報，該操作員將包含開啟新聞簡報但未按一下該新聞稿所包含連結的配置檔案的名稱。

配置檔案的名字和姓氏欄位連結到 **[!UICONTROL Recipients]** 目標維，而 **[!UICONTROL Alert]** 活動已連結到 **[!UICONTROL Operator]** 目標維。 因此，兩個目標維之間沒有可用的欄位來執行協調並檢索名字和姓氏欄位，並在「警報」活動中顯示它們。

該流程將按如下方式構建工作流：

1. 使用 **[!UICONTROL Query]** 活動到目標資料。
1. 添加 **[!UICONTROL JavaScript code]** 將填充從查詢保存到實例變數。
1. 使用 **[!UICONTROL Test]** 活動，以檢查人口數。
1. 使用 **[!UICONTROL Alert]** 活動，根據 **[!UICONTROL Test]** 活動結果。

![](assets/uc_operator_1.png)

## 將填充保存到實例變數 {#saving-the-population-to-the-instance-variable}

將以下代碼添加到 **[!UICONTROL JavaScript code]** 的子菜單。

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

確保Javascript代碼與工作流資訊對應：

* 的 **[!UICONTROL queryDef schema]** 標籤應與查詢活動中使用的目標維的名稱相對應。
* 的 **[!UICONTROL node expr]** 標籤應與要檢索的欄位的名稱相對應。

![](assets/uc_operator_3.png)

要檢索這些資訊，請執行以下步驟：

1. 按一下右鍵 **[!UICONTROL Query]** 活動，然後選擇 **[!UICONTROL Display the target]**。

   ![](assets/uc_operator_4.png)

1. 按一下右鍵清單，然後選擇 **[!UICONTROL Configure list]**。

   ![](assets/uc_operator_5.png)

1. 以維和欄位名稱為目標的查詢顯示在清單中。

   ![](assets/uc_operator_6.png)

## 測試人口數 {#testing-the-population-count}

將以下代碼添加到 **[!UICONTROL Test]** 活動，檢查目標人口是否至少包含1個配置檔案。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 設定警報 {#setting-up-the-alert}

既然已將填充添加到具有所需欄位的實例變數中，則可以將這些資訊添加到 **[!UICONTROL Alert]** 的子菜單。

為此，請將 **[!UICONTROL Source]** 頁籤：

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
>的 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** 命令允許您通過 **[!UICONTROL JavaScript code]** 的子菜單。\
>只要欄位已插入到JavaScript代碼中，就可以根據需要添加任意多個欄位。

![](assets/uc_operator_8.png)
