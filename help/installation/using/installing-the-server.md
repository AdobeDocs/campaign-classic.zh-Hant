---
product: campaign
title: 安裝伺服器
description: 安裝伺服器
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 3%

---

# 安裝伺服器{#installing-the-server}



## 執行安裝程式 {#executing-the-installation-program}

若為Windows 32位元平台，請安裝Adobe Campaign 32位元。 若為Windows 64位元平台，請安裝Adobe Campaign 64位元。

Adobe Campaign伺服器的安裝步驟如下：

1. 執行檔案 **setup.exe**.

   ![](assets/s_ncs_install_installer_01.png)

1. 選擇安裝類型。

   ![](assets/s_ncs_install_installer_01a.png)

   有數種安裝類型可供使用：

   * **[!UICONTROL Installation of an application server]** :安裝Adobe Campaign應用程式伺服器和用戶端主控台。
   * **[!UICONTROL Minimal installation (Network)]** :從網路安裝客戶端電腦。 如有必要，電腦上只會安裝有限數量的DLL，而所有其他元件將從網路驅動器中使用。
   * **[!UICONTROL Installation of a client]** :安裝Adobe Campaign用戶端所需的元件。
   * **[!UICONTROL Custom installation]** :使用者會選擇要安裝的元素。

   選擇 **安裝應用程式伺服器**，並執行下列不同步驟：

   ![](assets/s_ncs_install_installer_02.png)

1. 選擇安裝目錄：

   ![](assets/s_ncs_install_installer_03.png)

1. 按一下 **[!UICONTROL Finish]** 要啟動安裝，請執行以下操作：

   ![](assets/s_ncs_install_installer_04.png)

   進度欄顯示安裝的距離：

   ![](assets/s_ncs_install_installer_05.png)

   安裝完成後，系統會顯示訊息，通知您：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >伺服器安裝完成後，需要重新啟動伺服器以避免可能的網路問題。

   安裝完成後，啟動Adobe Campaign以建立設定檔。 請參閱 [伺服器的首次啟動](#first-start-up-of-the-server).

## 摘要安裝測試 {#summary-installation-testing}

您可以使用以下命令測試初始安裝：

```
nlserver pdump
```

如果Adobe Campaign未啟動，回應為：

```
No task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝測試完成後，請透過 **[!UICONTROL Start > Programs > Adobe Campaign]** ，然後輸入以下命令：

```
nlserver web
```

![](assets/s_ncs_install_cmd_nlserverweb.png)

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

Press **Ctrl+C** 要停止進程，請輸入以下命令：

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

## 內部標識符的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器會定義技術登入，稱為 **內部** 在所有情況下均具有所有權利。 安裝後登錄名沒有密碼。 必須定義一個。

在[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)了解更多資訊。

## 啟動Adobe Campaign服務 {#starting-adobe-campaign-services}

若要啟動Adobe Campaign服務，您可以使用服務管理員，或在命令列輸入下列內容（具有適當權限）:

```
net start nlserver6
```

如果您稍後需要停止Adobe Campaign程式，請使用命令：

```
net stop nlserver6
```

## 安裝LibreOffice {#installing-libreoffice}

下載LibreOffice並按照常規安裝步驟操作。

新增下列環境變數：

```
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
