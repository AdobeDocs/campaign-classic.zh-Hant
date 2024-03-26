---
product: campaign
title: 監督工作流程
description: 瞭解如何監督行銷活動工作流程
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: ca6d4bf4-7b3a-4d36-9fc3-0b83531d0132
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 1%

---

# 使用案例：監督您的工作流程{#supervising-workflows}



此使用案例詳細說明如何建立工作流程，以讓您監視一組「已暫停」、「已停止」或「發生錯誤」的工作流程的狀態。

其目的是：

* 使用工作流程來監視業務工作流程群組。
* 透過「傳遞」活動傳送訊息給主管。

若要監視一組工作流程的狀態，您必須遵循下列步驟：

1. 建立監控工作流程。
1. 撰寫JavaScript以判斷工作流程是否已暫停、停止或發生錯誤。
1. 建立 **[!UICONTROL Test]** 活動。
1. 準備傳遞範本。

>[!NOTE]
>
>除了工作流程、行銷活動之外， **工作流程熱度圖** 可讓您詳細分析目前執行的工作流程。 有關詳細資訊，請參閱 [專用區段](heatmap.md).
>
>如需如何操作的詳細資訊 **監視工作流程的執行**，請參閱 [本節](monitoring-workflow-execution.md).

## 步驟1：建立監控工作流程 {#step-1--creating-the-monitoring-workflow}

我們要監視的工作流程資料夾是 **&quot;CustomWorkflows&quot;** 儲存在 **管理>生產>技術工作流程** 節點。 此資料夾包含一組業務工作流程。

此 **監視工作流程** 儲存在Technical Workflows資料夾的根目錄中。 使用的標籤為 **&quot;監視&quot;**.

下列結構描述顯示活動的順序：

![](assets/uc_monitoring_workflow_overview.png)

此工作流程由以下部分組成：

* a **&quot;Start&quot;** 活動。
* a **&quot;JavaScript程式碼&quot;** 負責分析業務工作流程資料夾的活動。
* a **&quot;測試&quot;** 活動，將傳遞傳送給主管或重新啟動工作流程。
* a **&quot;傳送&quot;** 負責訊息佈局的活動。
* a **&quot;Wait&quot;** 控制工作流程反複專案之間前置時間的活動。

## 步驟2：編寫JavaScript {#step-2--writing-the-javascript}

JavaScript程式碼的第一部分與 **查詢(queryDef)** 可讓您識別具有「暫停」(@state == 13)、「錯誤」(@failed == 1)或「已停止」(@state == 20)狀態的工作流程。

此 **內部名稱** 要監視的工作流程資料夾的下列情況：

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

JavaScript程式碼的第二個部分可讓您 **顯示每個工作流程的訊息** 根據查詢期間復原的狀態而定。

>[!NOTE]
>
>建立的字串必須載入工作流程的事件變數中。

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

## 步驟3：建立「測試」活動 {#step-3--creating-the--test--activity}

「測試」活動可讓您根據「等待」活動，決定是否需要傳送傳遞或監控工作流程是否需要執行另一個週期。

傳遞已傳送給主管 **如果三個事件變數「vars.strWorkflowError」、「vars.strWorkflowPaused」或「vars.strWorkflowStop」中至少有一個不是void。**

![](assets/uc_monitoring_workflow_test.png)

「等待」活動可設定為定期重新啟動監視工作流程。 對於此使用案例， **等待時間設為一小時**.

![](assets/uc_monitoring_workflow_attente.png)

## 步驟4：準備傳送 {#step-4--preparing-the-delivery}

「傳送」活動是根據 **傳遞範本** 儲存在 **資源>範本>傳遞範本** 節點。

此範本必須包括：

* **主管的電子郵件地址**.
* **HTML內容** 用於插入個人化文字。

  ![](assets/uc_monitoring_workflow_variables_diffusion.png)

  宣告的三個變數(WF_Stop、WF_Paused、WF_Error)符合三個工作流程事件變數。

  這些變數必須在以下位置宣告： **變數** 傳遞範本屬性的索引標籤。

  要復原 **工作流程事件變數的內容**，您需要宣告傳送專用的變數，這些變數將使用JavaScript程式碼傳回的值進行初始化。

  傳遞範本的內容如下：

  ![](assets/uc_monitoring_workflow_model_diffusion.png)

建立並核准範本後，您需要設定 **傳遞** 活動至：

* 將「傳遞」活動連結至先前建立的傳遞範本。
* 將工作流程的事件變數連結至傳送範本的特定事件變數。

按兩下 **傳遞** 活動，並選取下列選項：

* 傳送：選取 **新增，根據範本建立**，並選取先前建立的傳送範本。
* 對於 **收件者和內容** 欄位，選取 **已在傳遞中指定**.
* 要執行的動作：選取 **準備並開始**.
* 取消核取 **處理錯誤** 選項。

  ![](assets/uc_monitoring_workflow_optionmodel.png)

* 前往 **指令碼** 的標籤 **傳遞** 活動，新增三個 **字元字串** 透過個人化欄位功能表輸入變數。

  ![](assets/uc_monitoring_workflow_selectlinkvariables.png)

  ![](assets/uc_monitoring_workflow_linkvariables.png)

  宣告的三個變數為：

  ```
  delivery.variables._var[0].stringValue = vars.strWorkflowError;
  delivery.variables._var[1].stringValue = vars.strWorkflowPaused;
  delivery.variables._var[2].stringValue = vars.strWorkflowStop; 
  ```

啟動此監視工作流程後，它會傳送以下摘要給收件者：

![](assets/uc_monitoring_workflow_mailfinal.png)
