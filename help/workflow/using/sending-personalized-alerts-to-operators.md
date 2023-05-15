---
product: campaign
title: 傳送個人化警示給營運商
description: 了解如何傳送個人化警報給營運商
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 21c97eb3-60cd-4d19-bc0f-5ba9ec17e70a
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 2%

---

# 傳送個人化警示給營運商{#sending-personalized-alerts-to-operators}



在此範例中，我們想傳送警報給運算子，運算子將包含開啟電子報但未點按其所包含連結之設定檔的名稱。

設定檔的名字和姓氏欄位會連結至 **[!UICONTROL Recipients]** 目標維度，而 **[!UICONTROL Alert]** 活動已連結至 **[!UICONTROL Operator]** 目標維度。 因此，兩個目標維度之間沒有可用的欄位，無法執行調解和擷取名字和姓氏欄位，以及在「警報」活動中顯示。

程式是建立工作流程，如下所示：

1. 使用 **[!UICONTROL Query]** 目標資料的活動。
1. 新增 **[!UICONTROL JavaScript code]** 活動以從查詢儲存母體至例項變數。
1. 使用 **[!UICONTROL Test]** 活動以檢查母體計數。
1. 使用 **[!UICONTROL Alert]** 傳送警報給運算子的活動，視 **[!UICONTROL Test]** 活動結果。

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

請確定Javascript程式碼與您的工作流程資訊對應：

* 此 **[!UICONTROL queryDef schema]** 標籤應與查詢活動中使用的目標維度名稱相對應。
* 此 **[!UICONTROL node expr]** 標籤應對應至您要擷取之欄位的名稱。

![](assets/uc_operator_3.png)

若要擷取這些資訊，請遵循下列步驟：

1. 以滑鼠右鍵按一下 **[!UICONTROL Query]** 活動，然後選取 **[!UICONTROL Display the target]**.

   ![](assets/uc_operator_4.png)

1. 以滑鼠右鍵按一下清單，然後選取 **[!UICONTROL Configure list]**.

   ![](assets/uc_operator_5.png)

1. 查詢目標維度和欄位名稱會顯示在清單中。

   ![](assets/uc_operator_6.png)

## 測試人口計數 {#testing-the-population-count}

將下列程式碼新增至 **[!UICONTROL Test]** 活動，以檢查目標母體是否至少包含1個設定檔。

```
var.recCount>0
```

![](assets/uc_operator_7.png)

## 設定警報 {#setting-up-the-alert}

現在，母體已新增至包含所需欄位的執行個體變數中，您可以將這些資訊新增至 **[!UICONTROL Alert]** 活動。

若要這麼做，請將新增至 **[!UICONTROL Source]** 標籤下列程式碼：

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
>此 **[!UICONTROL <%= item.target.recipient.@fieldName %>]** 命令可讓您透過 **[!UICONTROL JavaScript code]** 活動。\
>只要欄位已插入JavaScript程式碼中，您就可以視需要新增欄位。

![](assets/uc_operator_8.png)
