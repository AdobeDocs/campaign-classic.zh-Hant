---
product: campaign
title: 監督工作流程
description: 瞭解如何監督市場活動工作流
feature: Workflows
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '646'
ht-degree: 0%

---

# 用例：監控工作流{#supervising-workflows}

![](../../assets/v7-only.svg)

此使用案例詳細說明了如何建立工作流，該工作流允許您監視「已暫停」、「已停止」或「有錯誤」的一組工作流的狀態。

其目的是：

* 使用工作流監視一組業務工作流。
* 通過「傳遞」活動向主管發送消息。

要監視一組工作流的狀態，您需要執行以下步驟：

1. 建立監視工作流。
1. 編寫JavaScript以確定工作流是暫停、停止還是出錯。
1. 建立 **[!UICONTROL Test]** 的子菜單。
1. 準備交貨模板。

>[!NOTE]
>
>除工作流外，市場活動 **工作流熱圖** 允許您詳細分析當前正在運行的工作流。 有關詳細資訊，請參閱 [專用段](heatmap.md)。
>
>有關如何 **監視工作流的執行**，請參閱 [此部分](monitoring-workflow-execution.md)。

## 步驟1:建立監視工作流 {#step-1--creating-the-monitoring-workflow}

我們要監視的工作流資料夾 **&quot;自定義工作流&quot;** 儲存在 **管理>生產>技術工作流** 的下界。 此資料夾包含一組業務工作流。

的 **監視工作流** 儲存在「技術工作流」資料夾的根目錄中。 使用的標籤 **&quot;監視&quot;**。

以下架構顯示活動的順序：

![](assets/uc_monitoring_workflow_overview.png)

此工作流由以下組成：

* a **&quot;開始&quot;** 的子菜單。
* a **&quot;JavaScript代碼&quot;** 用於分析業務工作流資料夾的活動。
* a **&quot;Test&quot;** 活動，將交貨發送給主管或重新啟動工作流。
* a **&quot;交付&quot;** 負責消息佈局的活動。
* a **&quot;等待&quot;** 控制工作流小版本之間提前期的活動。

## 步驟2:編寫JavaScript {#step-2--writing-the-javascript}

JavaScript代碼的第一部分與 **查詢(queryDef)** 它允許您識別具有「pause」(@state == 13)、「error」(@failed == 1)或「stopped」(@state == 20)狀態的工作流。

的 **內部名稱** 在以下條件下提供了要監視的工作流資料夾：

```
<condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
```

```
var strError = "";
var strPaused = "";
var strStop = "";

var queryWkfError = xtk.queryDef.create(
  <queryDef schema="xtk:workflow" operation="select">
    <select>
      <node expr="@internalName"/>
      <node expr="@state"/>
      <node expr="@label"/>
      <node expr="@failed"/>
      <node expr="@state"/>   
    </select>
    <where id="12837805386">
      <condition boolOperator="AND" expr="[folder/@name] = 'Folder20'" internalId="1"/>
        <condition boolOperator="AND" internalId="2">
          <condition boolOperator="OR" expr="@state = 20" internalId="3"/>
          <condition expr="@state = 13" internalId="4"/>
        </condition>  
    </where>
  </queryDef>
);
var ndWkfError = queryWkfError.ExecuteQuery(); 
```

JavaScript代碼的第二部分允許您 **顯示每個工作流的消息** 基於查詢期間恢復的狀態。

>[!NOTE]
>
>建立的字串必須載入到工作流的事件變數中。

```
for each ( var wkf in ndWkfError.workflow ) 
{
  if ( wkf.@state == 13 )  // Status 13 = paused
  {
    if ( wkf.@failed == 1 )
      strError += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
    else
      strPaused += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
  }
  
  if ( wkf.@state == 20 )  // Status 20 = stop
    strStop += "<li>Workflow '" + wkf.@internalName + "' with the label '" + wkf.@label + "'</li>";
}

vars.strWorkflowError = strError;
vars.strWorkflowPaused = strPaused;
vars.strWorkflowStop = strStop;
```

## 第3步：建立「Test」活動 {#step-3--creating-the--test--activity}

「Test」活動允許您根據「等待」活動確定是否需要發送交貨或監視工作流是否需要運行另一個週期。

將交貨發送給主管 **如果三個事件變數「vars.strWorkflowError」、「vars.strWorkflowPaused」或「vars.strWorkflowStop」中至少有一個不是void。**

![](assets/uc_monitoring_workflow_test.png)

可以將「等待」活動配置為定期重新啟動監視工作流。 對於這個用例， **等待時間設定為1小時**。

![](assets/uc_monitoring_workflow_attente.png)

## 第4步：準備交貨 {#step-4--preparing-the-delivery}

「交付」活動基於 **交貨模板** 儲存在 **資源>模板>交付模板** 的下界。

此模板必須包括：

* **主管的電子郵件地址**。
* **HTML內容** 的子菜單。

   ![](assets/uc_monitoring_workflow_variables_diffusion.png)

   聲明的三個變數(WF_Stop、WF_Paused、WF_Error)與三個工作流事件變數匹配。

   這些變數必須在 **變數** 的子菜單。

   恢復 **工作流事件變數的內容**，您需要聲明特定於傳遞的變數，這些變數將使用JavaScript代碼返回的值進行初始化。

   傳遞模板具有以下內容：

   ![](assets/uc_monitoring_workflow_model_diffusion.png)

建立和批准模板後，您需要配置 **交貨** 活動：

* 將「交貨」活動連結到先前建立的交貨模板。
* 將工作流的事件變數連結到特定於交付模板的事件變數。

按兩下 **交貨** 活動，然後選擇以下選項：

* 交貨：選擇 **新建，從模板建立**，然後選擇以前建立的交貨模板。
* 對於 **收件人和內容** 欄位，選擇 **在交貨中指定**。
* 要執行的操作：選擇 **準備並啟動**。
* 取消選中 **處理錯誤** 的雙曲餘切值。

   ![](assets/uc_monitoring_workflow_optionmodel.png)

* 轉到 **指令碼** 頁籤 **交貨** 活動，添加三 **字串** 通過個性化欄位菜單鍵入變數。

   ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

   ![](assets/uc_monitoring_workflow_linkvariables.png)

   聲明的三個變數為：

   ```
   delivery.variables._var[0].stringValue = vars.strWorkflowError;
   delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
   delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
   ```

啟動此監視工作流後，它會向收件人發送以下摘要：

![](assets/uc_monitoring_workflow_mailfinal.png)
