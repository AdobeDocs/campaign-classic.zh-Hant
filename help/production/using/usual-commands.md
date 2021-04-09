---
solution: Campaign Classic
product: campaign
title: 常用命令
description: 常用命令
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 3%

---

# 常用命令{#usual-commands}

本節列出了Adobe Campaign的常用命令。

命令&#x200B;**nlserver**&#x200B;是整個Adobe Campaign應用程式的輸入命令。

此命令具有以下語法：**nlserver **`<command>`****`<arguments>`****

參數&#x200B;**`<command>`**&#x200B;與模組相對應。

>[!NOTE]
>
>* 無論如何，您都可以添加&#x200B;**-noconsole**&#x200B;參數，以刪除在啟動模組後顯示的注釋。
>* 相反地，您可以新增引數&#x200B;**-verbose**&#x200B;以顯示詳細資訊。

>



## 監視命令{#monitoring-commands-}

>[!NOTE]
>
>要列出所有模組，需要使用&#x200B;**nlserver pdump**&#x200B;命令。

可以添加參數&#x200B;**-who**&#x200B;以列出正在進行的連接（資料庫和應用程式）。

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

另一個有用的命令是&#x200B;**nlserver monitor**。 它列出監控XML檔案(在Adobe Campaign客戶端或通過&#x200B;**monitor.jsp**&#x200B;網頁獲得)。

可以添加參數&#x200B;**-missing**&#x200B;以列出缺少的模組（模組中出錯，模組關閉等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令{#module-launch-commands}

啟動模組的語法仍具有下列格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 對應於在配置檔案中輸入的實例的名稱，或單實例模 **** 塊的預設名稱。

## 關閉服務{#shut-down-services}

要停止Adobe Campaign服務，請使用以下命令之一：

* 如果您具有root或管理員訪問權限：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（適用於Linux）:**systemctl stop nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 否則，在Adobe Campaign帳戶中：

   ```
   nlserver shutdown 
   ```

## 重新啟動服務{#restart-services}

同樣，要重新啟動Adobe Campaign，您可以使用以下命令之一：

* 如果您具有root或管理員訪問權限：

   * 在Linux中：/etc/init.d/nlserver6 start

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（適用於Linux）:**systemmctl start nlserver**

   * 在Windows中：net start nlserver6

* 否則，在Adobe Campaign帳戶中：**nlserver watchdog -svc -noconsole**

## config命令{#the-config-command}

使用&#x200B;**config**&#x200B;命令可以管理伺服器配置，包括資料庫連接的重新配置。

使用&#x200B;**nlserver**&#x200B;執行檔的&#x200B;**config**&#x200B;命令和&#x200B;**-setdblogin**&#x200B;參數。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

要更改&#x200B;**internal**&#x200B;密碼：**nlserver config -internalpassword**

>[!IMPORTANT]
>
>若要使用&#x200B;**Internal**&#x200B;識別碼登入，您必須事先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 一般而言，您不需手動修改配置檔案，而可使用&#x200B;**config**&#x200B;命令
>* 若要取得參數清單，請使用&#x200B;**-?** 參數： **nlserver config -?**
>* 對於Oracle資料庫，不能指定帳戶。 語法如下：

>
>  
nlserver config -setdblogin:Oracle:test6@dbserver

