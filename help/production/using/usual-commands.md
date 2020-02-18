---
title: 常用命令
seo-title: 常用命令
description: 常用命令
seo-description: null
page-status-flag: never-activated
uuid: f06df8c0-d4ec-4d6b-84d5-f46d852388a3
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: production-procedures
discoiquuid: 90718075-87a7-4e9a-935b-571010908e79
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: de04b5d3ceb883a571ee665f630be931a68a5a3e

---


# 常用命令{#usual-commands}

本節列出Adobe Campaign中的常用命令。

命令 **nlserver** 是整個Adobe Campaign應用程式的輸入命令。

此命令具有以下語法： **nlserver **`<command>`****`<arguments>`****

參數 **`<command>`** 與模組對應。

>[!NOTE]
>
>* 無論如何，您都可以新增 **-noconsole引數** ，以刪除在模組啟動後顯示的注釋。
>* 相反地，您可以新增引數 **-verbose** ，以顯示更多資訊。
>



## 監控命令 {#monitoring-commands-}

>[!NOTE]
>
>要列出所有模組，需要使用 **nlserver pdump** 命令。

您可以添加參數 **-who** ，以列出正在進行的連接（資料庫和應用程式）。

```
nlserver pdump -who
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
web@default (9984) - 50.1 Mo
watchdog (2273) - 6.6 Mo
syslogd@default (9931) - 7.0 Mo
trackinglogd@default (9985) - 45.6 Mo
mta@test (9986) - 9.6 Mo
wfserver@test (9987) - 8.8 Mo

Connections ------------------------------------------------------
Last Access IP Instance Login 
DD/MM/YYYY HH:MM:SS 127.0.0.1 default formation_fr|tracking
DD/MM/YYYY HH:MM:SS 127.0.0.1 default internal|monitoring

Connection pool --------------------------------------------------
Datasource Server Provider Login 
default xxxxx myserver myprovider test400
```

另一個有用的命令是 **nlserver monitor**。 它列出監控XML檔案(在Adobe Campaign用戶端或透過 **monitor.jsp** 網頁取得)。

可以添加參數 **-missing** ，以列出缺少的模組（模組中出錯，模組關閉等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令 {#module-launch-commands}

啟動模組的語法仍具有下列格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 對應於在配置檔案中輸入的實例名稱，或單實例模 **塊的** 「預設」名稱。

## 關閉服務 {#shut-down-services}

若要停止Adobe Campaign服務，請使用下列其中一個命令：

* 如果您具有root或管理員訪問權限：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（適用於Linux）: **systemctl stop nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 否則，在Adobe Campaign帳戶中：

   ```
   nlserver shutdown 
   ```

## 重新啟動服務 {#restart-services}

同樣地，若要重新啟動Adobe Campaign，您可以使用下列其中一個命令：

* 如果您具有root或管理員訪問權限：

   * 在Linux中：/etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（適用於Linux）:系 **統mctl啟動nlserver**

   * 在Windows中：net start nlserver6

* 否則，在Adobe Campaign帳戶中： **nlserver watchdog -svc -noconsole**

## config命令 {#the-config-command}

config **命令** ，可讓您管理伺服器配置，包括重新配置資料庫連接。

使用帶 **有** -setdblogin參數的nlserver **執行檔****** 的config命令。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

要更改內部 **密碼** : **nlserver config -internalpassword**

>[!CAUTION]
>
>若要使用內部識 **別碼登入** ，您必須事先定義密碼。 如需詳細資訊，請參閱[本小節](../../installation/using/campaign-server-configuration.md#internal-identifier)。

>[!NOTE]
>
>* 一般而言，您不需手動修改設定檔案，而可使用config命 **令** 。
>* 若要取得參數清單，請使 **用-?** 參數： **nlserver config -?**
>* 對於Oracle資料庫，不能指定帳戶。 語法如下：
>
>  
nlserver config -setdblogin:Oracle:test6@dbserver


