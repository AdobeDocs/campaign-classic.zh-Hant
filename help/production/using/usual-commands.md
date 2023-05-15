---
product: campaign
title: 常用指令
description: 常用指令
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 4%

---

# 常用指令{#usual-commands}



本節列出Adobe Campaign中的常用命令。

命令 **nlserver** 是整個Adobe Campaign應用程式的input命令。

此命令的語法如下： **nlserver **`<command>`****`<arguments>`****

參數 **`<command>`** 對應至模組。

>[!NOTE]
>
>* 在任何情況下，您都可以新增 **-noconsole** 用於刪除模組啟動後顯示的注釋的參數。
>* 反之，您可以新增引數 **-verbose** 以顯示更多資訊。
>


## 監視命令 {#monitoring-commands-}

>[!NOTE]
>
>若要列出所有模組，您必須使用 **nlserver pdump** 命令。

您可以新增參數 **-who** 列出正在進行的連接（資料庫和應用程式）。

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

另一個有用的命令是 **nlserver監視器**. 它會列出監控XML檔案(在Adobe Campaign用戶端中取得，或透過 **monitor.jsp** 網頁)。

您可以新增參數 **-missing** 列出缺少的模組（模組、模組關閉等錯誤）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令 {#module-launch-commands}

啟動模組的語法仍會有下列格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 與設定檔案中輸入之執行個體的名稱相對應，或 **預設** 用於單實例模組。

## 關閉服務 {#shut-down-services}

若要停止Adobe Campaign服務，請使用下列其中一個命令：

* 如果您有根或管理員存取權：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（Linux適用）: **systemctl停止nlserver**

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

* 如果您有根或管理員存取權：

   * 在Linux中：/etc/init.d

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（Linux適用）: **systemctl啟動nlserver**

   * 在Windows中：net start nlserver6

* 否則，在Adobe Campaign帳戶中： **nlserver watchgd -svc -noconsole**

## config命令 {#the-config-command}

此 **設定** 命令允許您管理伺服器配置，包括重新配置資料庫連接。

使用 **設定** 命令 **nlserver** 可執行檔案 **-setdblogin** 參數。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

若要變更 **內部** 密碼： **nlserver config -internalpassword**

>[!IMPORTANT]
>
>若要使用 **內部** 識別碼，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 一般而言，您可以使用，而不是手動修改組態檔 **設定** 命令
>* 若要取得參數清單，請使用 **-?** 參數： **nlserver配置 — ?**
>* 若是Oracle資料庫，則不得指定帳戶。 語法如下：
>
>  nlserver配置 — setdblogin:Oracle:test6@dbserver
