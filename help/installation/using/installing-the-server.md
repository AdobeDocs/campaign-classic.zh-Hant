---
product: campaign
title: 安裝伺服器
description: 安裝伺服器
feature: Installation, Instance Settings
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '412'
ht-degree: 3%

---

# 安裝伺服器{#installing-the-server}



## 執行安裝程式 {#executing-the-installation-program}

若是Windows 32位元平台，請安裝Adobe Campaign 32位元。 若是Windows 64位元平台，請安裝Adobe Campaign 64位元。

Adobe Campaign伺服器的安裝步驟如下：

1. 執行檔案 **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. 選取安裝型別。

   ![](assets/s_ncs_install_installer_01a.png)

   有數種安裝型別可供使用：

   * **[!UICONTROL Installation of an application server]** ：安裝Adobe Campaign應用程式伺服器和使用者端主控台。
   * **[!UICONTROL Minimal installation (Network)]** ：從網路安裝使用者端電腦。 如有必要，電腦上只會安裝有限數量的DLL，而所有其他元件將會從網路磁碟機使用。
   * **[!UICONTROL Installation of a client]** ：安裝Adobe Campaign使用者端所需的元件。
   * **[!UICONTROL Custom installation]** ：使用者選擇要安裝的元素。

   選取 **應用程式伺服器的安裝**，並完成不同的步驟，如下所示：

   ![](assets/s_ncs_install_installer_02.png)

1. 選取安裝目錄：

   ![](assets/s_ncs_install_installer_03.png)

1. 按一下 **[!UICONTROL Finish]** 若要開始安裝，請執行下列動作：

   ![](assets/s_ncs_install_installer_04.png)

   進度列會顯示安裝的深度：

   ![](assets/s_ncs_install_installer_05.png)

   安裝完成後，系統會顯示訊息，讓您知道：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >伺服器安裝完成後，必須重新啟動伺服器以避免可能的網路問題。

   安裝完成後，請啟動Adobe Campaign以建立設定檔。 請參閱 [伺服器的首次啟動](#first-start-up-of-the-server).

## 摘要安裝測試 {#summary-installation-testing}

您可以使用下列指令來測試初始安裝：

```
nlserver pdump
```

如果Adobe Campaign未啟動，回應為：

```
No task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝測試完成後，請透過以下方式開啟命令提示字元： **[!UICONTROL Start > Programs > Adobe Campaign]** 選單並輸入下列指令：

```
nlserver web
```

安裝目錄中的檔案可用來設定Adobe Campaign伺服器模組。

會顯示下列資訊：

```
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

按下 **Ctrl+C** 若要停止程式，請輸入下列命令：

```
nlserver start web
```

會顯示下列資訊：

```
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

若要停止，請輸入：

```
nlserver stop web
```

會顯示下列資訊：

```
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部識別碼的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器會定義名為的技術登入 **內部** 擁有所有執行個體的所有權利。 安裝之後，登入沒有密碼。 必須定義一個。

若要了解詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

## 啟動Adobe Campaign服務 {#starting-adobe-campaign-services}

若要啟動Adobe Campaign服務，您可以使用服務管理員，或在命令列輸入以下內容（搭配適當的許可權）：

```
net start nlserver6
```

如果您稍後需要停止Adobe Campaign程式，請使用命令：

```
net stop nlserver6
```

## 安裝LibreOffice {#installing-libreoffice}

下載LibreOffice並遵循一般安裝步驟。

新增下列環境變數：

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
