---
title: 操作原則
seo-title: 操作原則
description: 操作原則
seo-description: null
page-status-flag: never-activated
uuid: a15929ca-5b1f-499a-a883-43fd0a318c98
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 5e9c17ad-14d2-4173-9fc9-0e48a21426c8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 2a11a73b0679c0a65dc10f71869bf2a6c6efc008

---


# 操作原則{#operating-principle}

從技術上講，Adobe Campaign平台是以數個模組為基礎。

Adobe Campaign有許多模組。 有些會持續運作，而有些則偶爾啟動以執行管理任務（例如配置資料庫連接）或執行經常性任務（例如合併跟蹤資訊）。

Adobe Campaign模組有三種類型：

* 多實例模組：所有例項都會執行單一程式。 這適用於以下模組： **web** syslogd **、** trackinglogd **和** Activities( **from the watchdog-****** config default.xmlFile)。
* 單實例模組：每個實例運行一個進程。 這適用於以下模組： **mfta**, wfserver **,** Mail **inSmsServer**, **inStat********`<instance>`** （活動來自Config-xml.xml檔案）。
* 實用程式模組：這些模組偶爾會執行，以執行偶爾或經常執行的&#x200B;**作業**(清除 **、設定**、下載追蹤記錄等)。

使用安裝資料夾的bin目錄中安 **裝的命令行工具nlserver** , **** 執行模組管理。

nlserver工具的一般 **語法** 如下：

**nlserver`<command>``<command arguments>`**

有關可用模組的清單，請使用 **nlserver** 命令。

下表詳細介紹了可用模組：

| 命令 | 說明 |
|---|---|
| aliasClacining | 標準化枚舉值 |
| 計費 | 將系統活動報告發送到billing@neolane.net |
| 清除 | 清理資料庫：從資料庫中刪除過時的資料，並運行資料庫引擎優化程式所使用統計資訊的更新。 |
| config | 修改伺服器配置 |
| copybase | 資料庫的副本 |
| 匯出 | 導出到命令行：可讓您傳送在Adobe Campaign用戶端主控台中建立的匯出模型至命令列 |
| fileconvert | 轉換設定大小的檔案 |
| 導入 | 導入到命令行：可讓您傳送在Adobe Campaign用戶端主控台中建立的匯入模型至命令列。 |
| inMail | 入站郵件分析器 |
| 安裝安裝 | 客戶安裝檔案的可用性 |
| javascript | 執行JavaScript指令碼，並可存取SOAP API。 |
| 工作 | 命令列處理 |
| 合併 | 表單合併 |
| midSourcing | 在中部採購模式下恢復交貨資訊 |
| 監視器 | XML依例項顯示伺服器程式和排程工作的狀態。 |
| mta | 主代理傳輸消息 |
| package | 導入或導出實體包檔案 |
| pdump | 顯示伺服器進程狀態 |
| prepareda | 準備傳送動作 |
| 重新啟動 | 部分伺服器重啟 |
| runwf | 工作流實例的執行 |
| 關閉 | 完全系統關閉 |
| sms | SMS通知處理 |
| sql | SQL指令碼執行 |
| start | 其他開始 |
| stat | 維護MTA連接統計資訊 |
| 停止 | 部分系統關閉 |
| 提交數 | 提交傳送動作 |
| syslogd | 日誌和跟蹤寫入伺服器 |
| 追蹤 | 合併和檢索跟蹤日誌 |
| trackinglogd | 跟蹤日誌寫入和清除伺服器 |
| 監視 | 啟動和監視實例 |
| web | 應用程式伺服器（HTTP和SOAP） |
| wfserver | 工作流程伺服器 |

>[!CAUTION]
>
>最後一個模組：與應用伺服器連結的跟蹤和中繼模組，為了效能考慮，它通過本地機制通過動態庫整合到Apache或IIS web伺服器中。 沒有Adobe Campaign命令可讓您啟動或管理此模組。 因此，您必須使用Web伺服器本身的命令。

使用以下命令顯示模組用法及其參數的語法： **nlserver`[module]`-?**

例如：

**nlserver config -?**

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

