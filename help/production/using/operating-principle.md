---
product: campaign
title: 操作原則
description: 操作原則
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 14ba450ebff9bba6a36c0df07d715b7279604222
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 2%

---

# 操作原則{#operating-principle}



技術上，Adobe Campaign平台是以數個模組為基礎。

Adobe Campaign模組有許多。 有些會持續運作，而有些則偶爾會啟動，以執行管理工作（例如設定資料庫連線）或執行週期性工作（例如合併追蹤資訊）。

Adobe Campaign模組分為三種型別：

* 多執行個體模組：針對所有執行個體執行單一程式。 這適用於下列模組： **網頁**， **syslogd**， **trackinglogd** 和 **看門狗** (活動來自 **config-default.xml** 檔案)。
* 單一執行個體模組：每個執行個體會執行一個處理序。 這適用於下列模組： **mta**， **wfserver**， **inMail**， **簡訊** 和 **stat** (活動來自 **config-`<instance>`.xml** 檔案)。
* 公用程式模組：這些模組會偶爾執行，以執行偶爾或重複的作業(**cleanup**， **設定**、下載追蹤記錄檔等)。

使用命令列工具執行模組管理 **nlserver** 安裝在中 **紙匣** 安裝資料夾的目錄。

的一般語法 **nlserver** 工具如下：

**nlserver `<command>``<command arguments>`**

如需可用模組的清單，請使用 **nlserver** 命令。

下表詳細說明可用的模組：

| 命令 | 說明 |
|---|---|
| aliasCleaning | 標準化分項清單 |
| 帳單 | 傳送系統活動報告至billing@neolane.net |
| cleanup | 清除資料庫：從資料庫刪除過時的資料，並更新資料庫引擎最佳化處理程式使用的統計資料。 |
| 設定 | 修改伺服器組態 |
| 匯出 | 匯出至命令列：可讓您將在Adobe Campaign使用者端主控台中建立的匯出模型傳送至命令列 |
| fileconvert | 轉換設定大小的檔案 |
| 匯入 | 匯入至命令列：可讓您將在Adobe Campaign使用者端主控台中建立的匯入模型傳送至命令列。 |
| inMail | 傳入郵件分析器 |
| installset | 客戶安裝檔案的可用性 |
| javascript | 使用對SOAP API的存取權執行JavaScript指令碼。 |
| 工作 | 命令列處理 |
| 合併 | 表單合併 |
| midSourcing | 在中間來源模式下復原傳遞資訊 |
| 監視 | XML依執行處理顯示伺服器處理作業和排程工作的狀態。 |
| mta | 主要代理程式傳輸訊息 |
| 封裝 | 匯入或匯出實體封裝檔案 |
| pdump | 顯示伺服器處理作業狀態 |
| prepareda | 準備傳遞動作 |
| 重新啟動 | 部分伺服器重新啟動 |
| runwf | 工作流程執行個體的執行 |
| 關機 | 系統完全關機 |
| 簡訊 | SMS通知處理 |
| sql | SQL指令碼執行 |
| 開始 | 其他開始 |
| stat | 維護MTA連線統計資料 |
| 停止 | 部分系統關機 |
| submitda | 提交傳遞動作 |
| syslogd | 記錄及追蹤寫入伺服器 |
| 追蹤 | 合併和擷取追蹤記錄 |
| trackinglogd | 追蹤記錄檔寫入和清除伺服器 |
| 看門狗 | 啟動和監視執行個體 |
| 網頁 | 應用程式伺服器（HTTP和SOAP） |
| wfserver | 工作流程伺服器 |

>[!IMPORTANT]
>
>最後有一個模組：連結至應用程式伺服器的追蹤和轉送模組，為了效能，會透過原生機制透過動態程式庫整合至Apache或IIS網頁伺服器。 Adobe Campaign命令無法讓您啟動或管理此模組。 因此，您必須使用Web伺服器本身的命令。

模組使用方式及其引數的語法會使用下列命令顯示： **nlserver `[module]` -？**

例如：

**nlserver設定 — ？**

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
