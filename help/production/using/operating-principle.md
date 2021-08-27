---
product: campaign
title: 操作原則
description: 操作原則
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 1c032ef9-af11-4947-90c6-76cb9434ae85
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 1%

---

# 操作原則{#operating-principle}

![](../../assets/v7-only.svg)

技術上，Adobe Campaign平台以數個模組為基礎。

有許多Adobe Campaign模組。 有些會持續運行，而有些則偶爾啟動，以執行管理任務（例如配置資料庫連接）或運行經常性任務（例如整合跟蹤資訊）。

有三種類型的Adobe Campaign模組：

* 多實例模組：對所有實例運行單個進程。 這適用於下列模組：**web**、**syslogd**、**trackinglogd**&#x200B;和&#x200B;**watchdog**（**config-default.xml**&#x200B;檔案中的活動）。
* 單實例模組：每個實例運行一個進程。 這適用於下列模組：**mta**、**wfserver**、**inMail**、**sms**&#x200B;和&#x200B;**stat**（來自&#x200B;**config-`<instance>`.xml**&#x200B;檔案的活動）。
* 實用程式模組：這些模組偶爾會執行，以執行偶爾或經常的操作（**cleanup**、**config**、下載追蹤記錄等）。

使用安裝資料夾&#x200B;**bin**&#x200B;目錄中安裝的命令行工具&#x200B;**nlserver**&#x200B;來執行模組管理。

**nlserver**&#x200B;工具的一般語法如下：

**nlserver  `<command>``<command arguments>`**

有關可用模組的清單，請使用&#x200B;**nlserver**&#x200B;命令。

下表詳細說明了可用模組：

| 命令 | 說明 |
|---|---|
| aliasCleancing | 標準化枚舉值 |
| 帳單 | 將系統活動報告傳送至billing@neolane.net |
| cleanup | 清除資料庫：從資料庫中刪除過時的資料，並運行資料庫引擎優化程式所使用統計資訊的更新。 |
| 設定 | 修改伺服器配置 |
| copybase | 資料庫的副本 |
| 匯出 | 導出到命令行：可讓您將在Adobe Campaign用戶端主控台中建立的匯出模型傳送至命令列 |
| fileconvert | 轉換設定大小的檔案 |
| 匯入 | 導入到命令行：可讓您將在Adobe Campaign用戶端主控台中建立的匯入模型傳送至命令列。 |
| inMail | 傳入郵件分析器 |
| 安裝程式 | 客戶安裝檔案的可用性 |
| javascript | 執行JavaScript指令碼，並可存取SOAP API。 |
| 工作 | 命令列處理 |
| 合併 | 表單合併 |
| midSourcing | 在中間來源模式下恢復交貨資訊 |
| 監視 | XML按實例顯示伺服器進程和計畫任務的狀態。 |
| mta | 主代理傳輸消息 |
| 套件 | 導入或導出實體包檔案 |
| pdump | 顯示伺服器進程狀態 |
| prepareda | 準備傳遞動作 |
| 重新啟動 | 部分伺服器重新啟動 |
| runwf | 執行工作流程例項 |
| 關閉 | 完全關閉系統 |
| sms | SMS通知處理 |
| sql | SQL指令碼執行 |
| 開始 | 其他開始 |
| stat | 維護MTA連接統計資訊 |
| 停止 | 部分系統關閉 |
| submitda | 提交傳遞動作 |
| syslogd | 日誌和跟蹤寫入伺服器 |
| 追蹤 | 整合和擷取追蹤記錄 |
| trackinglogd | 跟蹤日誌寫入和清除伺服器 |
| 監視 | 啟動和監視實例 |
| web | 應用程式伺服器（HTTP和SOAP） |
| wfserver | 工作流程伺服器 |

>[!IMPORTANT]
>
>最後一個模組：連結到應用程式伺服器的跟蹤和中繼模組，為了效能，它通過本機機制通過動態庫整合到Apache或IIS web伺服器中。 沒有可讓您啟動或管理此模組的Adobe Campaign命令。 因此，必須使用Web伺服器本身的命令。

使用以下命令顯示模組用法及其參數的語法：**nlserver `[module]` -?**

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
-monoinstance : initialises for a single instance ().
-addtrackinginstance : adds a new tracking instance.
-trackingpassword : changes the tracking password of an instance
-setproxy : sets the parameters for connection to a proxy server. The protocol can be 'http', 'https' or 'all'.
-reload : asks the server to reload the configuration of the instances. 
-applyxsl : applies an XSL stylesheet to all entities of a schema. 
-filter : applies the XTK filter contained in the file during loading of the schema entities.
-setactivationkey : sets the activation key
```
