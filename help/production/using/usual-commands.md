---
product: campaign
title: 常用指令
description: 常用指令
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: production-procedures
exl-id: 472ccc04-e68e-4ccb-90e9-7d626a4e794f
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 4%

---

# 常用指令{#usual-commands}



本節列出了Adobe Campaign的常見命令。

命令 **nlserver** 是整個Adobe Campaign應用程式的輸入命令。

此命令具有以下語法： **nlserver **`<command>`****`<arguments>`****

參數 **`<command>`** 對應於模組。

>[!NOTE]
>
>* 無論如何，您都可以 **-noconsole** 用於刪除模組啟動後顯示的注釋的參數。
>* 相反，您可以添加參數 **— 詳細** 的子菜單。
>


## 監視命令 {#monitoring-commands-}

>[!NOTE]
>
>要列出所有模組，您需要使用 **nlserver pdump** 的子菜單。

可以添加參數 **— 誰** 列出正在進行的連接（資料庫和應用程式）。

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

另一個有用的命令是 **nlserver監視器**。 它列出監視XML檔案(在Adobe Campaign客戶端或通過 **monitor.jsp** 頁面)。

可以添加參數 **缺少** 列出缺失的模組（模組錯誤、模組關閉等）

```
nlserver monitor -missing
HH:MM:SS > Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
inMail@test
mta@test
wfserver@test
```

這對應於具有自動啟動但尚未啟動的模組。

## 模組啟動命令 {#module-launch-commands}

要啟動模組的語法仍具有以下格式：

```
nlserver start <module>@<INSTANCE>
```

```
nlserver stop <module>@<INSTANCE>
```

>[!NOTE]
>
>**`<instance>`** 對應於在配置檔案中輸入的實例的名稱，或 **預設** 單實例模組。

## 關閉服務 {#shut-down-services}

要停止Adobe Campaign服務，請使用以下命令之一：

* 如果您具有根或管理員訪問權限：

   * 在Linux中：

      ```
      /etc/init.d/nlserver6 stop
      ```

      >[!NOTE]
      >
      >從20.1開始，建議改用以下命令（對於Linux）: **systemctl停止nlserver**

   * 在Windows中：

      ```
      net stop nlserver6
      ```

* 否則，在Adobe Campaign賬戶：

   ```
   nlserver shutdown 
   ```

## 重新啟動服務 {#restart-services}

同樣，要重新啟動Adobe Campaign，可以使用以下命令之一：

* 如果您具有根或管理員訪問權限：

   * 在Linux中：/etc/init.d/nlserver6啟動

      >[!NOTE]
      >
      >從20.1開始，建議改用以下命令（對於Linux）: **systmctl啟動nlserver**

   * 在Windows中：nlserver6

* 否則，在Adobe Campaign帳戶中： **nlserver監視程式 — svc -noconsole**

## config命令 {#the-config-command}

的 **配置** 命令，用於管理伺服器配置，包括重新配置資料庫連接。

使用 **配置** 命令 **nlserver** 執行檔 **-setdblogin** 的下界。

```
nlserver config -setdblogin:<[dbms:]account[:database][/password]@server>
```

```
nlserver config -setdblogin:PostgreSQL:<accountName>:test6@dbserver
```

輸入密碼。

更改 **內部** 密碼： **nlserver config -internpassword**

>[!IMPORTANT]
>
>使用 **內部** 標識符，您需要事先定義密碼。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

>[!NOTE]
>
>* 通常，您可以使用 **配置** 命令
>* 要獲取參數清單，請使用 **-?** 參數： **nlserver配置 — ?**
>* 對於Oracle資料庫，不能指定帳戶。 語法如下所示：
>
>  nlserver配置 — setdblogin:Oracle:test6@dbserver
