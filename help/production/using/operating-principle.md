---
product: campaign
title: 操作原則
description: 操作原則
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 2%

---

# 操作原則{#operating-principle}



從技術上講，Adobe Campaign平台基於幾個模組。

有許多Adobe Campaign模組。 有些操作是連續的，而有些則偶爾啟動以執行管理任務（例如配置資料庫連接）或運行經常性任務（例如合併跟蹤資訊）。

有三種類型的Adobe Campaign模組：

* 多實例模組：對所有實例運行單個進程。 這適用於以下模組： **網**。 **syslog**。 **跟蹤日誌** 和 **監視** (來自 **config-default.xml** )。
* 單實例模組：每個實例運行一個進程。 這適用於以下模組： **門**。 **wf伺服器**。 **郵件**。 **簡訊** 和 **統計** (來自 **配置`<instance>`.xml** )。
* 實用程式模組：這些模組偶爾運行，以執行偶爾或經常操作(**清理**。 **配置**、下載跟蹤日誌等)。

使用命令行工具執行模組管理 **nlserver** 安裝於 **賓** 的子目錄。

的常規語法 **nlserver** 工具如下所示：

**nlserver `<command>``<command arguments>`**

對於可用模組清單，請使用 **nlserver** 的子菜單。

下表詳細介紹了可用模組：

| 命令 | 說明 |
|---|---|
| 別名清除 | 標準化枚舉值 |
| 計費 | 將系統活動報告發送到billing@neolane.net |
| 清理 | 清除資料庫：從資料庫中刪除過時資料，並運行資料庫引擎優化程式使用的統計資訊的更新。 |
| 配置 | 修改伺服器配置 |
| 出口 | 導出到命令行：用於將在Adobe Campaign客戶端控制台中建立的導出模型發送到命令行 |
| 檔案轉換 | 轉換設定大小的檔案 |
| 導入 | 導入到命令行：用於將在Adobe Campaign客戶端控制台中建立的導入模型發送到命令行。 |
| 郵件 | 入站郵件分析器 |
| 安裝程式 | 客戶安裝檔案的可用性 |
| java | 執行JavaScript指令碼，訪問SOAP API。 |
| 工作 | 命令行處理 |
| 合併 | 窗體合併 |
| 中間採購 | 在中間採購模式下恢復交貨資訊 |
| 監控 | XML按實例顯示伺服器進程和計畫任務的狀態。 |
| mta | 主代理傳輸消息 |
| 包 | 導入或導出實體包檔案 |
| 轉儲 | 顯示伺服器進程狀態 |
| 準備 | 準備交貨操作 |
| 重新啟動 | 部分伺服器重新啟動 |
| 運行 | 工作流實例的執行 |
| 關閉 | 完全系統關閉 |
| 簡訊 | 簡訊通知處理 |
| sql | SQL指令碼執行 |
| 開始 | 其他啟動 |
| 統計 | 維護MTA連接統計 |
| 停止 | 部分系統關閉 |
| 提交資料 | 提交交貨操作 |
| syslog | 日誌和跟蹤寫入伺服器 |
| 追蹤 | 整合和檢索跟蹤日誌 |
| 跟蹤日誌 | 跟蹤日誌寫入和清除伺服器 |
| 監視 | 啟動和監視實例 |
| 網 | 應用程式伺服器（HTTP和SOAP） |
| wf伺服器 | 工作流伺服器 |

>[!IMPORTANT]
>
>最後一個模組：連結到應用伺服器的跟蹤和中繼模組，為了效能，通過本機機制通過動態庫整合到Apache或IIS Web伺服器中。 沒有可以啟動或管理此模組的Adobe Campaign命令。 因此，必須使用Web伺服器本身的命令。

使用以下命令顯示模組用法及其參數的語法： **nlserver `[module]` -?**

範例:

**nlserver配置 — ?**

```
Usage: nlserver [-verbose:<verbose mode>] [-?|h|H] [-version] [-noconsole]
 [-tracefile:<file>] [-tracefilter:<[type|!type],...>]
 [-instance:<instance>] [-low] [-high] [-queryplans] [-detach]
 [-internalpassword:<[password/newpassword]>] [-postupgrade]
 [-nogenschema] [-force] [-allinstances]
 [-addinstance:<instance/DNS masks[/language]>]
 [-setdblogin:<[dbms:]account[:database][/password]@server>]
 [-monoinstance]
 [-addtrackinginstance:<instance/masks DNS[/databaseId/[/language[/password]]]>]
 [-trackingpassword:<[password][/newpassword]>]
 [-setproxy:<protocol/server:port[/login]>] [-reload]
 [-applyxsl:<schema/file.xsl>] [-filter:<file>]
 [-setactivationkey:<activation key>]
 [-getactivationkey:<client identifier>]
-verbose : verbose mode
-? : display this help message
-version : display version number
-noconsole : no longer display logs and traces on the console
-tracefile : name of trace file to be generated (without extension)
-tracefilter : filter for the traces to be generated e.g.: wdbc,soap,!xtkquery.
-instance : instance to be used (default instance if this option is not present).
-low : start up with low priority
-high : start up with high priority (not recommended)
-queryplans : generate traces with the execution plans of SQL queries.
-detach : detaches the process from its parent (internal option)
-internalpassword : changes the password of the server internal account.
-postupgrade : updates the database following upgrade to a higher version. 
-nogenschema : does not recompute the schemas during database update
-force : updates the database even if this has already been done with the current build 
-allinstances : updates the database over all configured instances
-addinstance : adds a new instance.
-setdblogin : sets the parameters for connection to the database of an instance. The DBMS can be 'oracle', 'postgresql', 'mssql' or 'odbc' (default=postgresql)
-monoinstance : initializes for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
