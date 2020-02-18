---
title: 安裝伺服器
seo-title: 安裝伺服器
description: 安裝伺服器
seo-description: null
page-status-flag: never-activated
uuid: 02534211-c267-490d-b9c1-78f56f1284e1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
discoiquuid: d1510fd9-995b-46c6-8d57-e1fe3999235e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c25e2a4f2280cdcc61e0522f8235149410b5dacf

---


# 安裝伺服器{#installing-the-server}

## 執行安裝程式 {#executing-the-installation-program}

若是Windows 32位元平台，請安裝Adobe Campaign 32位元。 若是Windows 64位元平台，請安裝Adobe Campaign 64位元。

Adobe Campaign伺服器的安裝步驟如下：

1. 執行文 **件setup.exe**。

   ![](assets/s_ncs_install_installer_01.png)

1. 選擇安裝類型。

   ![](assets/s_ncs_install_installer_01a.png)

   有幾種安裝類型可用：

   * **[!UICONTROL Installation of an application server]** :安裝Adobe Campaign應用程式伺服器和用戶端主控台。
   * **[!UICONTROL Minimal installation (Network)]** :從網路安裝客戶機。 如果需要，電腦上將只安裝有限數量的DLL，並且所有其它元件將從網路驅動器使用。
   * **[!UICONTROL Installation of a client]** :安裝Adobe Campaign用戶端所需的元件。
   * **[!UICONTROL Custom installation]** :使用者選擇要安裝的元素。
   選 **擇安裝應用程式伺服器**，然後執行下列不同步驟：

   ![](assets/s_ncs_install_installer_02.png)

1. 選擇安裝目錄：

   ![](assets/s_ncs_install_installer_03.png)

1. 按一下 **[!UICONTROL Finish]** 以啟動安裝：

   ![](assets/s_ncs_install_installer_04.png)

   進度列顯示安裝的距離：

   ![](assets/s_ncs_install_installer_05.png)

   安裝完成後，會出現一則訊息，告知您：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >在伺服器安裝完成後，需要重新啟動伺服器以避免可能的網路問題。

   安裝完成後，啟動Adobe Campaign以建立設定檔案。 請參 [閱伺服器的首次啟動](#first-start-up-of-the-server)。

## 安裝測試摘要 {#summary-installation-testing}

您可以使用下列命令測試初始安裝：

```
nlserver pdump
```

如果Adobe Campaign未啟動，回應是：

```
No task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝測試完成後，通過菜單開啟命令提 **[!UICONTROL Start > Programs > Adobe Campaign]** 示符並輸入以下命令：

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

安裝目錄中的檔案可用來設定Adobe Campaign伺服器模組。

將顯示以下資訊：

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

按 **Ctrl+C** 停止進程，然後輸入以下命令：

```
nlserver start web
```

將顯示以下資訊：

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

要停止，請輸入：

```
nlserver stop web
```

將顯示以下資訊：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部識別碼的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器會定義名為內部的技術登 **入** ，此登入具有所有例項的所有權限。 在安裝後，登入就沒有密碼。 必須定義一個。

請參閱「內 [部識別碼](../../installation/using/campaign-server-configuration.md#internal-identifier)」一節。

## 啟動Adobe Campaign服務 {#starting-adobe-campaign-services}

若要啟動Adobe Campaign服務，您可以使用服務管理員，或在命令列中輸入下列項目（具有適當的權限）:

```
net start nlserver6
```

如果您日後需要停止Adobe Campaign程式，請使用以下命令：

```
net stop nlserver6
```

## 安裝LibreOffice {#installing-libreoffice}

例如，從https://www.libreoffice.org/download/libreoffice-fresh/下載LibreOffice [](https://www.libreoffice.org/download/libreoffice-fresh/) ，並遵循一般安裝步驟。

添加以下環境變數：

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```

