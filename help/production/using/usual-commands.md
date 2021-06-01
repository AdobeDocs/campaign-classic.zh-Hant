---
product: campaign
title: 常用指令
description: 常用指令
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 3%

---

# 常用指令{#usual-commands}

本節列出Adobe Campaign中的常用命令。

命令&#x200B;**nlserver**&#x200B;是整個Adobe Campaign應用程式的輸入命令。

此命令的語法如下：**nlserver **`<command>`****`<arguments>`****

參數&#x200B;**`<command>`**&#x200B;對應於模組。

>[!NOTE]
>
>* 在任何情況下，您都可以新增&#x200B;**-noconsole**&#x200B;引數，以刪除模組啟動後顯示的註解。
>* 反之，您可以新增引數&#x200B;**-verbose**&#x200B;以顯示更多資訊。

>



## 監視命令{#monitoring-commands-}

>[!NOTE]
>
>要列出所有模組，需要使用&#x200B;**nlserver pdump**&#x200B;命令。

您可以新增參數&#x200B;**-who**&#x200B;以列出正在進行的連線（資料庫和應用程式）。

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

另一個有用的命令是&#x200B;**nlserver監視器**。 它列出監視XML檔案(在Adobe Campaign客戶端中獲取，或通過&#x200B;**monitor.jsp**&#x200B;網頁獲取)。

您可以新增參數&#x200B;**-missing**&#x200B;以列出缺少的模組（模組錯誤、模組關閉等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令{#module-launch-commands}

啟動模組的語法仍會有下列格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 與配置檔案中輸入的實例名稱相對應，或與單實例模 **** 組的預設值相對應。

## 關閉服務{#shut-down-services}

若要停止Adobe Campaign服務，請使用下列其中一個命令：

* 如果您有根或管理員存取權：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（Linux適用）:**systemctl停止nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 否則，在Adobe Campaign帳戶中：

   ```
   nlserver shutdown 
   ```

## 重新啟動服務{#restart-services}

同樣地，若要重新啟動Adobe Campaign，您可以使用下列其中一個命令：

* 如果您有根或管理員存取權：

   * 在Linux中：/etc/init.d

      >[!NOTE]
      >
      >從20.1開始，建議改用下列命令（Linux適用）:**systemctl啟動nlserver**

   * 在Windows中：net start nlserver6

* 否則，在Adobe Campaign帳戶中：**nlserver watchdog -svc -noconsole**

## 配置命令{#the-config-command}

**config**&#x200B;命令允許您管理伺服器配置，包括重新配置資料庫連接。

使用&#x200B;**-setdblogin**&#x200B;參數&#x200B;**nlserver**&#x200B;執行檔的&#x200B;**config**&#x200B;命令。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

要更改&#x200B;**internal**&#x200B;密碼，請執行以下操作：**nlserver config -internalpassword**

>[!IMPORTANT]
>
>若要使用&#x200B;**Internal**&#x200B;標識符登錄，您必須預先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 通常，您可以使用&#x200B;**config**&#x200B;命令，而不是手動修改配置檔案
>* 要獲取參數清單，請使用&#x200B;**-?** 參數： **nlserver配置 — ?**
>* 若是Oracle資料庫，則不得指定帳戶。 語法如下：

>
>  
nlserver config -setdblogin:Oracle:test6@dbserver

