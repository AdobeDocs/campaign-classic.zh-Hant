---
product: campaign
title: 監視指南
description: 探索監控 Campaign 執行個體和程序的準則和最佳作法
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 18%

---

# 監視指南 {#monitoring-guidelines}



## 執行個體監視儀表板 {#instance-monitoring-dashboard}

可從Campaign Classic首頁存取的&#x200B;**[!UICONTROL Monitoring]**&#x200B;標籤是協助您監視執行個體的主要進入點。

它提供執行個體上所發生情況的儀表板：其狀態（組建版本、已安裝套件等）、系統指標、記錄、目前正在執行的工作流程、上次傳送傳遞的狀態等。

您可於[此處](../../production/using/monitoring-processes.md)取得詳細資訊。

![](assets/monitoring_tab.png)

## 監控Campaign Classic流程 {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">監視您的執行個體</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">監視工作流程</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">監視傳遞</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">監視資料庫</a></p></td></tr>
</table>

監控不同Campaign流程的其他方法可供使用。 它們提供數種監視執行個體的方式，以確保您的系統健康且最終疑難排解設定工作流程、傳送傳遞等時可能發生的問題。

### 監視您的執行個體 {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自動監視工具**

有數種自動方法可供使用。 協助您監控執行個體。 例如，您可以設定包含偵測到異常的電子郵件報表、擷取XML格式的指標清單等。 [按一下這裡](../../production/using/monitoring-processes.md#automatic-monitoring)以獲得更多資訊。

**稽核軌跡**

稽核軌跡可讓您以視覺效果呈現執行個體中與選項、工作流程和結構描述相關的完整變更歷史記錄。 [按一下這裡](../../production/using/audit-trail.md)以獲得更多資訊。

**控制面板**

「控制面板」可以讓您管理執行個體的多項設定：管理URL許可權、檢查執行個體的詳細資訊（例如伺服器的組建版本）等。 它也可讓您監視連線到執行個體的SFTP伺服器上的可用空間。 [按一下這裡](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)以獲得更多資訊。

>[!NOTE]
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
>
>請注意，您的執行個體必須託管在AWS上，並以[最新GA版本編號](../../rn/using/rn-overview.md)升級。 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)詳述的步驟操作。

### 監視工作流程 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流程熱度圖**

工作流程熱度圖提供執行個體上執行之所有工作流程的視覺化表示。 它可讓您輕鬆監控執行個體的負載，並據此規劃工作流程。 [按一下這裡](../../workflow/using/heatmap.md)以獲得更多資訊。

**稽核軌跡**

稽核軌跡可讓您以視覺效果呈現工作流程中所做的所有修改及其目前狀態。 [按一下這裡](../../production/using/audit-trail.md)。

**工作流程疑難排解**

遇到工作流程執行問題時，可執行特定動作。 [按一下這裡](../../production/using/workflow-execution.md)以取得詳細資訊

**工作流程狀態監視**

除了熱度圖之外，您還可以建立工作流程，讓您監視一組工作流程的狀態，並傳送週期性訊息給主管。 [按一下這裡](../../workflow/using/supervising-workflows.md)以獲得更多資訊。

**一般准則**

使用工作流程時，遵循准則和最佳實務有助於改善效能。 如需詳細資訊，請參閱下列章節：
* [使用工作流程時的最佳實務](../../workflow/using/workflow-best-practices.md)
* [監控工作流程執行](../../workflow/using/monitoring-workflow-execution.md)

### 監視傳遞 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP報告**

SMTP報告會依網域顯示傳遞統計資料和SMTP錯誤。 [了解更多](../../production/using/monitoring-processes.md)

**最佳實務**

[傳遞傳送和設計的最佳實務](../../delivery/using/delivery-best-practices.md)可協助您改善其效能。

**傳遞疑難排解**
遇到傳送問題時，可執行特定動作：
* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [影像顯示問題](../../production/using/image-display-issues.md)
* [傳遞效能問題](../../delivery/using/delivery-performances.md)
* [暫存檔案問題](../../production/using/temporary-files.md) - *僅限內部部署託管模型*

### 監視資料庫 {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**資料庫清除工作流程**

資料庫清理工作流程可讓您從資料庫中刪除過時的資料。 建議避免資料庫呈指數增長。 [按一下這裡](../../production/using/database-cleanup-workflow.md)以獲得更多資訊。

**資料庫效能疑難排解**

遇到資料庫效能問題時，可以執行特定動作。 [按一下這裡](../../production/using/database-performances.md)以獲得更多資訊。

**維護資料庫**

*僅限內部部署和混合託管模型*

建議您定期執行資料庫維護，以避免過度消耗磁碟空間，進而影響資料庫存取。 [按一下這裡](../../production/using/recommendations.md)以獲得更多資訊。

**備份與還原**

*僅限內部部署和混合託管模型*

若要避免在電腦上發生問題（無論是實體或系統相關問題）時遺失資料，備份是必要的。 [按一下這裡](../../production/using/backup.md)以取得詳細資訊。 [本節](../../production/using/restoration.md)中說明還原程式。

## Campaign Classic技術原則 {#campaign-classic-technical-principles}

Campaign Classic檔案中提供技術資源。 在執行個體上執行任何技術作業之前，建議您先熟悉這些主題。

**託管模型與功能**

* [Campaign Classic託管模型](../../installation/using/hosting-models.md)
* [託管模型功能](../../installation/using/capability-matrix.md)

**伺服器組態**

*僅限內部部署和混合託管模型*

* [伺服器設定](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml檔案組態](../../installation/using/the-server-configuration-file.md)
* [傳遞能力的伺服器設定](../../installation/using/email-deliverability.md)
* [用來建立執行個體和宣告資料庫的命令列](../../installation/using/command-lines.md)

**一般原則**

* [Campaign Classic架構](../../production/using/general-architecture.md)
* [Campaign Classic模組](../../production/using/operating-principle.md)
* [Campaign Classic選項](../../installation/using/configuring-campaign-options.md)
* [如何設定模組的自動啟動](../../production/using/administration.md)
* [Campaign設定原則](../../production/using/configuration-principle.md)
* [疑難排解程式](../../production/using/performance-and-throughput-issues.md)
