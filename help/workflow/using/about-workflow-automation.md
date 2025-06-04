---
product: campaign
title: 關於工作流程
description: 使用工作流程自動化程序、管理資料和客群、傳送訊息等
feature: Workflows, Data Management
exl-id: 024a7344-9376-4ff3-926a-003148229f9f
source-git-commit: b45cc49f15f51e3624c46713c95966f465b2e4da
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 9%

---

# 使用工作流程自動化 {#gs-workflows}

Adobe Campaign的工作流程可讓您的團隊簡化並自動化整個平台的端對端業務流程。 透過直覺式的圖形介面，您可以設計和管理工作流程來協調工作，例如資料細分、行銷活動執行、檔案處理，甚至使用者核准 — 全都集中在一處。

例如，您可以自動執行從遠端伺服器擷取檔案、擷取檔案內容，以及順暢地將資料載入Adobe Campaign伺服器的程式，減少手動工作量，並提升營運效率。 工作流程引擎可確保每個步驟都可靠地執行，並受到追蹤以利可視性和控制。

>[!BEGINTABS]

>[!TAB 工作流程檔案]

若要進一步瞭解工作流程管理，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=zh-Hant){target=_blank}。


[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/about-workflows.html?lang=zh-Hant){target=_blank}


>[!TAB 有用的連結]

在Campaign v8檔案中瞭解與工作流程管理相關的關鍵步驟：

* [工作流程活動](https://experienceleague.adobe.com/docs/campaign/automation/workflows/wf-activities/activities.html?lang=zh-Hant){target=_blank}：活動是任務範本。 工作流程包括目標定位、流量控制、動作和事件活動。

* [建立工作流程](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/build-a-workflow.html?lang=zh-Hant){target=_blank}：瞭解如何建立和執行目標定位、行銷活動和技術工作流程。

* [最佳實務](https://experienceleague.adobe.com/docs/campaign/automation/workflows/introduction/workflow-best-practices.html?lang=zh-Hant){target=_blank}：瞭解最佳化行銷活動工作流程效能、改善工作流程設計和定義正確設定的指導方針。

* [監視工作流程](https://experienceleague.adobe.com/docs/campaign/automation/workflows/monitoring-workflows/monitor-workflow-execution.html?lang=zh-Hant){target=_blank}：瞭解如何監視工作流程執行，以確保一切正常執行。

* [工作流程使用案例](https://experienceleague.adobe.com/docs/campaign/automation/workflows/use-cases/workflow-use-cases.html?lang=zh-Hant){target=_blank}：瞭解哪些內容可以使用工作流程，以及如何透過端對端使用案例實作工作流程。


>[!ENDTABS]





<!--

Adobe Campaign uses workflows to:

* Carry out targeting campaigns. [Learn more](building-a-workflow.md#implementation-steps-)
* Build campaigns: for each campaign, the **[!UICONTROL Workflow]** tab lets you build the target and create the deliveries. [Learn more](building-a-workflow.md#campaign-workflows)
* Perform technical processes: cleanup, collecting tracking information or provisional calculations. [Learn more](building-a-workflow.md#technical-workflows)

A workflow can mean both a process definition (the workflow model, which is a representation of what is supposed to happen) and an instance of this process (a workflow instance, which is a representation of what is actually happening).

The workflow template describes the various tasks to be performed and how they are linked together. The task templates are called activities and are represented by icons. They are linked together by transitions.

![](assets/example1.png)

Each workflow contains:

* **[!UICONTROL Activities]**

  An activity describes a task template. The various activities available are represented on the diagram by icons. Each type has common properties and specific properties. For example, while all activities have a name and label, only the **[!UICONTROL Approval]** activity has an assignment.

  In a workflow diagram, a given activity can produce multiple tasks, in particular when there is a loop or recurrent (periodic) actions.

  All workflow activities are listed in [this section](about-activities.md), including use cases and samples.

* **[!UICONTROL Transitions]**

  Transitions enable you to link activities and to define their sequence. A transition links a source activity to a destination activity. There are several sorts of transitions, which depend on the source activity. Some transitions have additional parameters such as a duration, a condition or a filter.

  A transition which is not linked to a destination activity is colored orange and the arrow head is shown as a diamond.

  >[!NOTE]
  >
  >A workflow containing unterminated transitions can still be executed: a warning message will be generated and the workflow will pause once it reaches the transition but it will not generate an error. It is thus possible to start a workflow without it being finished and to add to it as you go along.

  For more information about how to build a workflow, refer to [this section](building-a-workflow.md).

* **[!UICONTROL Worktables]**

  The worktable contains all the information carried by the transition. Each workflow uses several worktables. The data conveyed in these tables can be accelerated and used throughout the workflow's life cycle, as long as it is not purged. Indeed, unneeded tables are purged each time the workflow is passivated, and possibly during the execution of the largest workflows to avoid overloading the server.

  Learn more on workflow data and tables in [this section](how-to-use-workflow-data.md).

## Key principles and best practices{#principles-workflows}

Refer to these sections to find guidance and best practices to automate processes with workflows:

* Learn more about workflow activities in [this page](how-to-use-workflow-data.md).
* Learn how to build a workflow in [this section](building-a-workflow.md).
* Discover how to use workflows to import data in Campaign in [this section](../../platform/using/import-export-workflows.md).
* Workflow best practices are detailed in [this page](workflow-best-practices.md).
* Find guidance about workflow execution in [this section](starting-a-workflow.md).
* Learn how to monitor workflows in [this page](monitoring-workflow-execution.md).
* Learn how to grant access to users to use workflows in [this page](managing-rights.md).

-->