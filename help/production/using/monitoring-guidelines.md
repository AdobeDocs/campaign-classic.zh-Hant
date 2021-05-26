---
solution: Campaign Classic
product: campaign
title: 監視准則
description: 探索監控 Campaign 執行個體和程序的準則和最佳作法。
audience: production
content-type: reference
topic-tags: introduction
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: bce114f36d1ec4582fc79e750d48155ba0d7cd1f
workflow-type: tm+mt
source-wordcount: '768'
ht-degree: 20%

---

# 監視准則 {#monitoring-guidelines}

## 執行個體監控控制面板{#instance-monitoring-dashboard}

**[!UICONTROL Monitoring]**&#x200B;標籤可從Campaign Classic首頁存取，是協助您監控執行個體的主要入口點。

它提供例項發生情況的控制面板：其狀態（組建版本、已安裝的套件等）、系統指標、記錄、目前執行的工作流程、上次傳送的狀態等。

您可於[此處](../../production/using/monitoring-processes.md)取得詳細資訊。

![](assets/monitoring_tab.png)

## 監控Campaign Classic進程{#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">監視您的執行個體</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">監視工作流程</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">監視傳遞</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">監視資料庫</a></p></td></tr>
</table>

有其他方式可監控不同的促銷活動程式。 它們提供數種監視執行個體的方式，以確保您的系統運作正常，並最終疑難排解在設定工作流程、傳送傳遞等作業時可能發生的問題。

### 監視實例{#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自動監控工具**

有數種自動方法可供使用。 協助您監視執行個體。 例如，您可以設定含有偵測到異常的電子郵件報表、以XML格式擷取指標清單等。 [按一下這裡](../../production/using/monitoring-processes.md#automatic-monitoring)以獲得更多資訊。

**稽核軌跡**

稽核追蹤可讓您視覺化執行個體中與選項、工作流程和結構相關的變更完整歷史記錄。 [按一下這裡](../../production/using/audit-trail.md)以獲得更多資訊。

**控制面板**

「控制面板」可讓您管理執行個體的數個設定：管理URL權限、檢查您的執行個體詳細資訊，例如伺服器的組建版本等。 它也可讓您監視連線至執行個體之SFTP伺服器上的可用空間。 [按一下這裡](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html)以獲得更多資訊。

>[!NOTE]
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
>
>請注意，您的執行個體必須托管在AWS上，並升級為最新的[Gold Standard](../../rn/using/gs-overview.md)組建或[最新的GA組建(21.1)](../../rn/using/latest-release.md)。 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)詳述的步驟操作。

### 監控工作流程 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流程熱度圖**

工作流程熱度圖提供執行個體上執行之所有工作流程的視覺表示法。 它可讓您輕鬆監視執行個體的負載，並據此規劃工作流程。 [按一下這裡](../../workflow/using/heatmap.md)以獲得更多資訊。

**稽核軌跡**

稽核追蹤可讓您視覺化工作流程中所做的所有修改及其目前狀態。 [按一下這裡](../../production/using/audit-trail.md).

**工作流程疑難排解**

在工作流程執行遇到問題時，可執行特定動作。 [按一下](../../production/using/workflow-execution.md) 這裡以取得詳細資訊

**工作流程狀態監控**

除了熱度圖之外，您還可以建立工作流程，讓您監控一組工作流程的狀態，並傳送循環訊息給主管。 [按一下這裡](../../workflow/using/supervising-workflows.md)以獲得更多資訊。

**一般准則**

使用工作流程時遵循准則和最佳實務有助於改善效能。 如需詳細資訊，請參閱下列章節：
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)
* [監控工作流程執行](../../workflow/using/monitoring-workflow-execution.md)

### 監視傳遞{#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP報表**

SMTP報表會依網域顯示傳送統計資料和SMTP錯誤。 [了解更多](../../production/using/monitoring-processes.md)

**最佳實務**

[傳遞傳送和設計的最佳](../../delivery/using/delivery-best-practices.md) 實務可協助您改善其效能。

**傳送疑**
難排解當傳送發生問題時，可執行特定動作：
* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [影像顯示問題](../../production/using/image-display-issues.md)
* [傳遞效能問題](../../delivery/using/delivery-performances.md)
* [臨時檔案問題](../../production/using/temporary-files.md)  — 僅限 *內部部署的托管模型*

### 監視資料庫{#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**資料庫清除工作流程**

「資料庫清理」工作流允許您從資料庫中刪除過時的資料。 建議避免資料庫的指數增長。 [按一下這裡](../../production/using/database-cleanup-workflow.md)以獲得更多資訊。

**資料庫效能疑難解答**

遇到資料庫效能問題時，可執行特定動作。 [按一下這裡](../../production/using/database-performances.md)以獲得更多資訊。

**維護資料庫**

*僅內部部署和混合托管模型*

建議您定期執行資料庫維護，以避免磁碟空間過度消耗，進而影響資料庫存取。 [按一下這裡](../../production/using/recommendations.md)以獲得更多資訊。

**備份和恢復**

*僅內部部署和混合托管模型*

備份是避免在電腦上出現問題（無論是物理或系統相關）時丟失資料的關鍵。 [按一下這裡](../../production/using/backup.md)以獲得更多資訊。[本節](../../production/using/restoration.md)中描述了恢復過程。

## Campaign Classic技術原則{#campaign-classic-technical-principles}

Campaign Classic檔案中提供技術資源。 建議您先熟悉這些主題，再對執行個體執行任何技術操作。

**托管模型和功能**

* [Campaign Classic托管模型](../../installation/using/hosting-models.md)
* [托管模型功能](../../installation/using/capability-matrix.md)

**伺服器配置**

*僅限內部部署與混合托管模型*

* [伺服器配置](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml檔案配置](../../installation/using/the-server-configuration-file.md)
* [傳遞能力的伺服器配置](../../installation/using/email-deliverability.md)
* [用於建立實例和聲明資料庫的命令行](../../installation/using/command-lines.md)

**一般原則**

* [Campaign Classic架構](../../production/using/general-architecture.md)
* [Campaign Classic模組](../../production/using/operating-principle.md)
* [Campaign Classic選項](../../installation/using/configuring-campaign-options.md)
* [如何設定模組的自動啟動](../../production/using/administration.md)
* [行銷活動設定原則](../../production/using/configuration-principle.md)
* [疑難排解程式](../../production/using/performance-and-throughput-issues.md)
