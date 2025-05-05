---
product: campaign
title: 常用指令
description: 常用指令
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: b8a6a0db27826309456c285c08d4f1d85de70283
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 4%

---

# 常用指令{#usual-commands}



本節列出Adobe Campaign中的常用命令。

命令&#x200B;**nlserver**&#x200B;是整個Adobe Campaign應用程式的輸入命令。

這個命令的語法如下： **nlserver &#x200B;**`<command>`**&#x200B;**`<arguments>`**&#x200B;**

引數&#x200B;**`<command>`**&#x200B;對應至模組。

>[!NOTE]
>
>* 無論如何，您可以新增&#x200B;**-noconsole**&#x200B;引數，以刪除模組啟動後顯示的註解。
>* 反之，您可以新增引數&#x200B;**-verbose**&#x200B;以顯示更多資訊。
>

## 監視命令 {#monitoring-commands-}

>[!NOTE]
>
>若要列出所有模組，您必須使用&#x200B;**nlserver pdump**&#x200B;命令。

您可以新增引數&#x200B;**-who**，列出進行中的連線（資料庫和應用程式）。

```sql
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

另一個有用的命令是&#x200B;**nlserver monitor**。 它列出監視XML檔案(在Adobe Campaign使用者端或透過&#x200B;**monitor.jsp**&#x200B;網頁取得)。

您可以新增引數&#x200B;**-missing**，列出缺少的模組（模組、模組關閉等錯誤）

```sql
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令 {#module-launch-commands}

啟動模組的語法仍會採用下列格式：

```sql
nlserver start <module>@<INSTANCE>
```

```sql
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`**&#x200B;對應到組態檔中輸入的執行個體名稱，或是&#x200B;**預設** （針對單一執行個體模組）。

## 關閉服務 {#shut-down-services}

若要停止Adobe Campaign服務，請使用下列命令之一：

* 如果您擁有根或管理員存取權：

   * 在Linux中：

     ```sql
     /etc/init.d/nlserver6 stop
     ```

     >[!NOTE]
     >
     >從20.1開始，我們建議改用以下命令（適用於Linux）： **systemctl stop nlserver**

   * 在Windows中：

     ```sql
     net stop nlserver6
     ```

* 如果沒有，則在Adobe Campaign帳戶中：

  ```sql
  nlserver shutdown 
  ```

## 重新啟動服務 {#restart-services}

同樣地，若要重新啟動Adobe Campaign，您可以使用以下命令之一：

* 如果您擁有根或管理員存取權：

   * 在Linux中： `/etc/init.d/nlserver6 start`

     >[!NOTE]
     >
     >從20.1開始，我們建議改用以下命令（適用於Linux）： **systemctl start nlserver**

   * 在Windows中： `net start nlserver6`

* 否則，在Adobe Campaign帳戶中： **nlserver watchdog -svc -noconsole**

## 設定命令 {#the-config-command}

**config**&#x200B;命令可讓您管理伺服器組態，包括重新設定資料庫連線。

使用包含&#x200B;**-setdblogin**&#x200B;引數的&#x200B;**nlserver**&#x200B;可執行檔的&#x200B;**config**&#x200B;命令。

```sql
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```sql
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

若要變更&#x200B;**內部**&#x200B;密碼： **nlserver config -internalpassword**

>[!IMPORTANT]
>
>若要使用&#x200B;**內部**&#x200B;識別碼登入，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 一般而言，您可以使用&#x200B;**config**&#x200B;命令，而不必手動修改組態檔
>* 若要取得引數清單，請使用&#x200B;**-？**&#x200B;引數： **nlserver config -？**
>* 若是Oracle資料庫，則不得指定帳戶。 語法如下：
>
>  `nlserver config -setdblogin:Oracle:test6@dbserver`
>

以下是MSSQL的範例：

```sql
nlserver config -setdblogin:mssql:<login>/"<password>"@<server> -instance:<instance_name> 
```

* 在config-&lt;instance_name>.xml檔案的dataSource節點中可以找到login （例如account：user）和server。
* 密碼必須以引號「」括住。

