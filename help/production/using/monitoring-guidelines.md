---
product: campaign
title: 監視指南
description: 探索監控 Campaign 執行個體和程序的準則和最佳作法。
feature: Monitoring
exl-id: ca0c33c5-7350-462a-bc65-4cab51e529d9
source-git-commit: c54102b2ec32fbea89ce41dd3c9fedb98e612996
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# 監視指南 {#monitoring-guidelines}

![](../../assets/v7-only.svg)

## 實例監視儀表板 {#instance-monitoring-dashboard}

的 **[!UICONTROL Monitoring]** 頁籤，可從Campaign Classic首頁訪問，它是幫助您監視實例的主要入口點。

它提供了實例上發生的情況的儀表板：其狀態（生成版本、已安裝的包等）、系統指示符、日誌、當前正在運行的工作流、上次發送的遞送的狀態等。

您可於[此處](../../production/using/monitoring-processes.md)取得詳細資訊。

![](assets/monitoring_tab.png)

## 監視Campaign Classic進程 {#monitoring-campaign-classic-processes}

<table>
<tr><td><img src="assets/do-not-localize/icon_system.svg" width="60px"><p><a href="#monitoring-instance">監視實例</a></p></td>
<td><img src="assets/do-not-localize/icon_workflows.svg" width="60px"><p><a href="#monitoring-workflows">監視工作流程</a></p></td>
<td><img src="assets/do-not-localize/icon_send.svg" width="60px"><p><a href="#monitoring-deliveries">監視傳遞</a></p></td>
<td><img src="assets/do-not-localize/icon_database.svg" width="60px"><p><a href="#monitoring-database">監視資料庫</a></p></td></tr>
</table>

還提供了監控不同市場活動流程的其他方法。 它們提供了多種監視實例的方法，以確保您的系統正常，並最終解決在設定工作流、發送遞送等時可能出現的問題。

### 監視實例 {#monitoring-instance}

<img src="assets/do-not-localize/icon_system.svg" width="60px">

**自動監控工具**

有幾種自動方法可供使用。 來幫助您監視實例。 例如，您可以設定具有檢測到的異常的電子郵件報告，檢索XML格式的指示符清單等。 [按一下這裡](../../production/using/monitoring-processes.md#automatic-monitoring)以獲得更多資訊。

**稽核軌跡**

「審核跟蹤」允許您直觀顯示與實例中的選項、工作流和架構相關的更改的完整歷史記錄。 [按一下這裡](../../production/using/audit-trail.md)以獲得更多資訊。

**控制面板**

通過「控制面板」，您可以管理實例的幾個設定：管理URL權限，檢查您的實例詳細資訊，如伺服器的生成版本等。 它還允許您監視連接到實例的SFTP伺服器上的可用空間。 [按一下這裡](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=zh-Hant)以獲得更多資訊。

>[!NOTE]
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
>
>請注意，您的實例必須托管在AWS上，並使用 [最新的GA版本](../../rn/using/rn-overview.md)。 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)詳述的步驟操作。

### 監控工作流程 {#monitoring-workflows}

<img src="assets/do-not-localize/icon_workflows.svg" width="60px">

**工作流程熱度圖**

「工作流熱度圖」提供了在實例上運行的所有工作流的可視化表示。 它使您能夠輕鬆監視實例上的負載並相應地規劃工作流。 [按一下這裡](../../workflow/using/heatmap.md)以獲得更多資訊。

**稽核軌跡**

「審核跟蹤」(Audit trail)允許您可視化工作流中所做的所有修改及其當前狀態。 [按一下這裡](../../production/using/audit-trail.md).

**工作流疑難解答**

當遇到工作流執行問題時，可以執行特定操作。 [按一下這裡](../../production/using/workflow-execution.md) 的

**工作流狀態監視**

除熱度圖外，您還可以建立一個工作流，該工作流允許您監視一組工作流的狀態，並向主管發送定期消息。 [按一下這裡](../../workflow/using/supervising-workflows.md)以獲得更多資訊。

**一般准則**

在使用工作流時遵循指導原則和最佳做法有助於改進效能。 有關詳細資訊，請參閱以下各節：
* [使用工作流時的最佳做法](../../workflow/using/workflow-best-practices.md)
* [監控工作流程執行](../../workflow/using/monitoring-workflow-execution.md)

### 監視傳遞 {#monitoring-deliveries}

<img src="assets/do-not-localize/icon_send.svg" width="60px">

**SMTP報告**

SMTP報告按域顯示傳遞統計資訊和SMTP錯誤。 [了解更多](../../production/using/monitoring-processes.md)

**最佳實務**

[交付發送和設計的最佳做法](../../delivery/using/delivery-best-practices.md) 能幫助你改善他們的表現。

**交付故障排除**
遇到交貨問題時，可執行特定操作：
* [可交付性問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)
* [影像顯示問題](../../production/using/image-display-issues.md)
* [交付效能問題](../../delivery/using/delivery-performances.md)
* [臨時檔案問題](../../production/using/temporary-files.md) - *僅限內部托管模型*

### 監視資料庫 {#monitoring-database}

<img src="assets/do-not-localize/icon_database.svg" width="60px">

**資料庫清除工作流程**

通過「資料庫清理」工作流，您可以從資料庫中刪除過時資料。 建議避免資料庫的指數級增長。 [按一下這裡](../../production/using/database-cleanup-workflow.md)以獲得更多資訊。

**資料庫效能疑難解答**

遇到資料庫效能問題時可執行特定操作。 [按一下這裡](../../production/using/database-performances.md)以獲得更多資訊。

**維護資料庫**

*僅限本地和混合托管模式*

我們建議您定期執行資料庫維護，以避免磁碟空間的過度消耗，從而影響資料庫訪問。 [按一下這裡](../../production/using/recommendations.md)以獲得更多資訊。

**備份和恢復**

*僅限本地和混合托管模式*

備份是避免在電腦上出現問題（無論是與物理或系統相關）時丟失資料的關鍵。 [按一下這裡](../../production/using/backup.md)以獲得更多資訊。恢復過程如中所述 [此部分](../../production/using/restoration.md)。

## Campaign Classic技術原則 {#campaign-classic-technical-principles}

技術資源可在Campaign Classic文檔中找到。 我們建議您在對實例執行任何技術操作之前先熟悉這些主題。

**托管模型和功能**

* [Campaign Classic托管模型](../../installation/using/hosting-models.md)
* [托管模型功能](../../installation/using/capability-matrix.md)

**伺服器配置**

*僅內置和混合托管模型*

* [伺服器配置](../../installation/using/configuring-campaign-server.md)
* [Serverconf.xml檔案配置](../../installation/using/the-server-configuration-file.md)
* [用於可傳送性的伺服器配置](../../installation/using/email-deliverability.md)
* [建立實例並聲明資料庫的命令行](../../installation/using/command-lines.md)

**一般原則**

* [Campaign Classic架構](../../production/using/general-architecture.md)
* [Campaign Classic模組](../../production/using/operating-principle.md)
* [Campaign Classic選項](../../installation/using/configuring-campaign-options.md)
* [如何設定模組自動啟動](../../production/using/administration.md)
* [戰役配置原則](../../production/using/configuration-principle.md)
* [故障排除過程](../../production/using/performance-and-throughput-issues.md)
