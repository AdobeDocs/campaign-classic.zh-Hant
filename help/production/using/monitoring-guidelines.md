---
solution: Campaign Classic
product: campaign
title: 監視准則
description: 探索監控 Campaign 執行個體和程序的準則和最佳作法。
audience: production
content-type: reference
topic-tags: introduction
translation-type: tm+mt
source-git-commit: 9aa0ecd423bfbf1082e9ce5bdb36aaf1611dea54
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 8%

---


# 監視准則 {#monitoring-guidelines}

## 實例監控控制面板{#instance-monitoring-dashboard}

**[!UICONTROL Monitoring]**&#x200B;標籤可從Campaign Classic首頁存取，是協助您監控執行個體的主要入口點。

它提供執行個體發生情況的控制面板：其狀態（組建版本、已安裝的封裝等）、系統指標、記錄檔、目前執行的工作流程、上次傳送的傳送狀態等。

您可於[此處](../../production/using/monitoring-processes.md)取得詳細資訊。

![](assets/monitoring_tab.png)

## 監控Campaign Classic進程{#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">監控您的實例</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#moniroting-workflows">監控工作流程</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">監控傳送</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">監視資料庫</a></p></td></tr>
</table>

您還可使用其他方式監控不同的促銷活動程式。 它們提供數種監控例項的方式，以確保您的系統正常運作，並最終疑難排解在設定工作流程、傳送傳送等時可能發生的問題。

### 監控實例{#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自動監控工具**

有幾種自動方法可供使用。 來協助您監控您的實例。 例如，您可以設定偵測到異常的電子郵件報表、擷取XML格式的指標清單等。 [按一](../../production/using/monitoring-processes.md#automatic-monitoring) 下這裡以取得詳細資訊。

**稽核軌跡**

稽核記錄可讓您直觀地顯示實例中與選項、工作流程和結構描述相關的變更的完整記錄。 [按一](../../production/using/audit-trail.md) 下這裡以取得詳細資訊。

**控制面板**

「控制面板」可讓您管理數個例項的設定：管理URL權限、檢查您的例項詳細資訊，例如伺服器的建置版本等。 它還允許您監視連接到實例的SFTP伺服器上的可用空間。 [按一](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/control-panel-home.html) 下這裡以取得詳細資訊。

>[!NOTE]
>
>請注意，「控制面板」僅供管理員使用者存取，可供所有使用Adobe Managed Services的客戶使用。

### 監控工作流程 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流程熱度圖**

Workflow HeatMap以視覺化方式呈現執行個體上執行的所有工作流程。 它可讓您輕鬆監控執行個體的負載，並據此規劃工作流程。 [按一](../../workflow/using/heatmap.md) 下這裡以取得詳細資訊。

**稽核軌跡**

「稽核記錄」可讓您視覺化工作流程中所做的所有修改及其目前狀態。 [按一下這裡](../../production/using/audit-trail.md).

**工作流程疑難排解**

當遇到工作流執行問題時，可執行特定動作。 [按一](../../production/using/workflow-execution.md) 下這裡以取得詳細資訊

**工作流程狀態監控**

除了熱圖外，您還可以建立工作流程，讓您監控一組工作流程的狀態，並傳送循環訊息給主管。 [按一](../../workflow/using/supervising-workflows.md) 下這裡以取得詳細資訊。

**一般准則**

使用工作流程時，請遵循准則和最佳實務，有助於改善效能。 如需詳細資訊，請參閱下列章節：
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)
* [監控工作流程執行](../../workflow/using/monitoring-workflow-execution.md)

### 監視傳遞{#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP報告**

SMTP報告按域顯示傳送統計資訊和SMTP錯誤。 [進一步了解](../../production/using/monitoring-processes.md)

**最佳實務**

[傳送和設計的最佳實務](../../delivery/using/delivery-best-practices.md) 可協助您改善其效能。

**傳送疑**
難排解當傳送發生問題時，可執行特定動作：
* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [影像顯示問題](../../production/using/image-display-issues.md)
* [傳送效能問題](../../delivery/using/delivery-performances.md)
* [臨時檔案問題](../../production/using/temporary-files.md) -僅 *限內部部署代管模型*

### 監視資料庫{#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**資料庫清除工作流程**

「資料庫清理」工作流允許您從資料庫中刪除過時的資料。 建議避免資料庫的指數級增長。 [按一](../../production/using/database-cleanup-workflow.md) 下這裡以取得詳細資訊。

**資料庫效能故障排除**

在遇到資料庫效能問題時，可以執行特定操作。 [按一](../../production/using/database-performances.md) 下這裡以取得詳細資訊。

**資料庫維護**

*僅限內部部署和混合式代管模型*

建議您定期執行資料庫維護，以避免磁碟空間過度消耗，從而影響資料庫訪問。 [按一](../../production/using/recommendations.md) 下這裡以取得詳細資訊。

**備份和還原**

*僅限內部部署和混合式代管模型*

備份是避免在電腦發生問題（無論是物理問題還是與系統相關）時丟失資料的關鍵。 [按一](../../production/using/backup.md) 下這裡以取得詳細資訊。還原過程在[本節](../../production/using/restoration.md)中介紹。

## Campaign Classic技術原則{#campaign-classic-technical-principles}

技術資源可在Campaign Classic檔案中取得。 建議您在對實例執行任何技術操作之前先熟悉這些主題。

**代管模型與功能**

* [Campaign Classic代管模型](../../installation/using/hosting-models.md)
* [代管模型功能](../../installation/using/capability-matrix.md)

**伺服器組態**

*僅限內部部署與混合式代管模型*

* [強制性伺服器組態](../../installation/using/campaign-server-configuration.md)
* [Serverconf.xml檔案配置](../../installation/using/the-server-configuration-file.md)
* [可傳遞的伺服器組態](../../installation/using/email-deliverability.md)
* [用於建立實例和聲明資料庫的命令行](../../installation/using/command-lines.md)

**一般原則**

* [Campaign Classic架構](../../production/using/general-architecture.md)
* [Campaign Classic模組](../../production/using/operating-principle.md)
* [Campaign Classic選項](../../installation/using/configuring-campaign-options.md)
* [如何設定模組的自動啟動](../../production/using/administration.md)
* [促銷活動設定原則](../../production/using/configuration-principle.md)
* [疑難排解程式](../../production/using/performance-and-throughput-issues.md)
