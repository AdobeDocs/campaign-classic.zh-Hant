---
product: campaign
title: 常用指令
description: 常用指令
feature: Monitoring
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 4%

---

# 常用指令{#usual-commands}



本節列出Adobe Campaign中的常用命令。

指令 **nlserver** 是整個Adobe Campaign應用程式的輸入命令。

這個命令的語法如下： **nlserver **`<command>`****`<arguments>`****

引數 **`<command>`** 對應至模組。

>[!NOTE]
>
>* 無論如何，您可以新增 **-noconsole** 引數，用來刪除啟動模組後顯示的註解。
>* 相反地，您可以新增引數 **-verbose** 以顯示更多資訊。
>

## 監視命令 {#monitoring-commands-}

>[!NOTE]
>
>若要列出所有模組，您需要使用 **nlserver pdump** 命令。

您可以新增引數 **-who** 列出進行中的連線（資料庫和應用程式）。

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

另一個有用的指令是 **nlserver監視**. 其中列出監視XML檔案(在Adobe Campaign使用者端中取得，或透過 **monitor.jsp** 網頁)。

您可以新增引數 **-missing** 列出缺少的模組（模組、模組關閉等錯誤）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令 {#module-launch-commands}

啟動模組的語法仍會採用下列格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 對應於在組態檔案中輸入的例項名稱，或 **預設** 用於單執行個體模組。

## 關閉服務 {#shut-down-services}

若要停止Adobe Campaign服務，請使用下列命令之一：

* 如果您擁有根或管理員存取權：

   * 在Linux中：

     ```
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >從20.1版開始，建議您改用下列命令（適用於Linux）： **systemctl停止nlserver**

   * 在Windows中：

     ```
     net stop nlserver6
     ```

* 如果沒有，則在Adobe Campaign帳戶中：

  ```
  nlserver shutdown 
  ```

## 重新啟動服務 {#restart-services}

同樣地，若要重新啟動Adobe Campaign，您可以使用以下命令之一：

* 如果您擁有根或管理員存取權：

   * 在Linux中： /etc/init.d/nlserver6 start

     >[!NOTE]
     >
     >從20.1版開始，建議您改用下列命令（適用於Linux）： **systemctl啟動nlserver**

   * 在Windows中：網路啟動nlserver6

* 否則，在Adobe Campaign帳戶中： **nlserver watchdog -svc -noconsole**

## 設定命令 {#the-config-command}

此 **設定** command可讓您管理伺服器組態，包括重新設定資料庫連線。

使用 **設定** 命令 **nlserver** 包含下列專案的可執行檔案： **-setdblogin** 引數。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

若要變更 **內部** 密碼： **nlserver設定 — internalpassword**

>[!IMPORTANT]
>
>若要使用 **內部** 識別碼，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 一般而言，您可以使用 **設定** 命令
>* 若要取得引數清單，請使用 **-？** 引數： **nlserver設定 — ？**
>* 若是Oracle資料庫，則不得指定帳戶。 語法如下：
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>
