---
product: campaign
title: 安裝伺服器
description: 安裝伺服器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 3%

---

# 安裝伺服器{#installing-the-server}



## 執行安裝程式 {#executing-the-installation-program}

對於Windows 32位平台，請安裝Adobe Campaign32位。 對於Windows 64位平台，請安裝Adobe Campaign64位。

Adobe Campaign伺服器的安裝步驟如下：

1. 執行檔案 **setup.exe**。

   ![](assets/s_ncs_install_installer_01.png)

1. 選擇安裝類型。

   ![](assets/s_ncs_install_installer_01a.png)

   有幾種安裝類型可用：

   * **[!UICONTROL Installation of an application server]** :安裝Adobe Campaign應用程式伺服器和客戶端控制台。
   * **[!UICONTROL Minimal installation (Network)]** :從網路安裝客戶機。 如有必要，電腦上將只安裝有限數量的DLL，並且所有其他元件都將從網路驅動器中使用。
   * **[!UICONTROL Installation of a client]** :安裝Adobe Campaign客戶端所需的元件。
   * **[!UICONTROL Custom installation]** :用戶選擇要安裝的元素。

   選擇 **安裝應用程式伺服器**，並按照如下所示執行不同步驟：

   ![](assets/s_ncs_install_installer_02.png)

1. 選擇安裝目錄：

   ![](assets/s_ncs_install_installer_03.png)

1. 按一下 **[!UICONTROL Finish]** 啟動安裝：

   ![](assets/s_ncs_install_installer_04.png)

   進度欄顯示安裝的距離：

   ![](assets/s_ncs_install_installer_05.png)

   安裝完成後，將顯示一條消息通知您：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >伺服器安裝完成後，需要重新啟動伺服器以避免可能的網路問題。

   安裝完成後，啟動Adobe Campaign以建立配置檔案。 請參閱 [伺服器的首次啟動](#first-start-up-of-the-server)。

## 摘要安裝測試 {#summary-installation-testing}

可以使用以下命令test初始安裝：

```
nlserver pdump
```

如果Adobe Campaign未啟動，則響應為：

```
No task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝test完成後，通過 **[!UICONTROL Start > Programs > Adobe Campaign]** 命令：

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

安裝目錄中的檔案用於配置Adobe Campaign伺服器模組。

顯示以下資訊：

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

按 **Ctrl+C** 要停止進程，請輸入以下命令：

```
nlserver start web
```

顯示以下資訊：

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

顯示以下資訊：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部標識符的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器定義名為 **內部** 對所有情況都擁有所有權。 安裝後登錄名沒有密碼。 必須定義一個。

在[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)了解更多資訊。

## 啟動Adobe Campaign服務 {#starting-adobe-campaign-services}

要啟動Adobe Campaign服務，可以使用服務管理器或在命令行中輸入以下內容（具有相應權限）:

```
net start nlserver6
```

如果以後需要停止Adobe Campaign進程，請使用命令：

```
net stop nlserver6
```

## 安裝LibreOffice {#installing-libreoffice}

下載LibreOffice並遵循常規安裝步驟。

添加以下環境變數：

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
