---
product: campaign
title: 安裝伺服器
description: 安裝伺服器
feature: Installation, Instance Settings
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: installation
content-type: reference
topic-tags: installing-campaign-in-windows-
exl-id: c0cb4efa-cae9-4312-88fb-738857a89595
source-git-commit: 7906e9fee164d731659bbb9f96394faca5961240
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 1%

---

# 安裝伺服器{#installing-the-server}

## 執行安裝程式 {#executing-the-installation-program}

Adobe Campaign伺服器的安裝步驟如下：

1. 執行檔案&#x200B;**setup.exe**。

   ![](assets/s_ncs_install_installer_01.png)

1. 選取安裝型別。

   ![](assets/s_ncs_install_installer_01a.png)

   有數種安裝型別可供使用：

   * **[!UICONTROL Installation of an application server]** ：安裝Adobe Campaign應用程式伺服器和使用者端主控台。
   * **[!UICONTROL Minimal installation (Network)]** ：從網路安裝使用者端電腦。 如有必要，電腦上只會安裝有限數量的DLL，而所有其他元件將會從網路磁碟機使用。
   * **[!UICONTROL Installation of a client]** ：安裝Adobe Campaign使用者端所需的元件。
   * **[!UICONTROL Custom installation]** ：使用者選擇要安裝的元素。

   選取&#x200B;**應用程式伺服器的安裝**，然後執行下列不同的步驟：

   ![](assets/s_ncs_install_installer_02.png)

1. 選取安裝目錄：

   ![](assets/s_ncs_install_installer_03.png)

1. 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;開始安裝：

   ![](assets/s_ncs_install_installer_04.png)

   進度列會顯示安裝的深度：

   ![](assets/s_ncs_install_installer_05.png)

   安裝完成後，系統會顯示訊息，讓您知道：

   ![](assets/s_ncs_install_installer_06.png)

   >[!NOTE]
   >
   >伺服器安裝完成後，必須重新啟動伺服器以避免可能的網路問題。

   安裝完成後，請啟動Adobe Campaign以建立設定檔。 請參閱[伺服器](#first-start-up-of-the-server)的首次啟動。

## 摘要安裝測試 {#summary-installation-testing}

您可以使用下列指令來測試初始安裝：

```sql
nlserver pdump
```

如果Adobe Campaign未啟動，回應為：

```sql
No task
```

## 伺服器的首次啟動 {#first-start-up-of-the-server}

安裝測試完成後，透過&#x200B;**[!UICONTROL Start > Programs > Adobe Campaign]**&#x200B;功能表開啟命令提示字元並輸入下列命令：

```sql
nlserver web
```

安裝目錄中的檔案可用來設定Adobe Campaign伺服器模組。

會顯示下列資訊：

```sql
15:30:12 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
15:30:12 >   Web server start (pid=664, tid=4188)...
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confserverConf.xml' server via '[INSTALL]bin..conffraserverConf.xml.sample
15:30:12 >   Creation of server configuration file '[INSTALL]bin..confconfig-default.xml' server via '[INSTALL]bin..confmodelsconfig-default.xml
15:30:12 >   Server started
15:30:12 >   Stop requested (pid=664)
15:30:12 >   Web server stop (pid=664, tid=4188)...
```

按&#x200B;**Ctrl+C**&#x200B;停止程式，然後輸入下列命令：

```sql
nlserver start web
```

會顯示下列資訊：

```sql
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Start of the 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair') task in a new process 
12:17:21 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:17:21 >   Web server start (pid=29188, tid=-1224824320)...
12:17:21 >   Generation of configuration changes '[INSTALL]bin..confserverConf.xml.diff' between '[INSTALL]bin..confserverConf.xml' and '[INSTALL]bin..conffraserverConf.xml.sample'
12:17:22 >   Tomcat started
12:17:22 >   Server started
```

若要停止，請輸入：

```sql
nlserver stop web
```

會顯示下列資訊：

```sql
12:18:31 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
12:18:31 >   Stop requested for 'web@default' ('nlserver web -tracefile:web@default -instance:default -detach -tomcat -autorepair', pid=29188, tid=-1224824320)...
12:18:31 >   Stop requested (pid=29188)
12:18:31 >   Web server stopped (pid=29188, tid=-1224824320)...
```

## 內部識別碼的密碼 {#password-for-the-internal-identifier}

Adobe Campaign伺服器定義名稱為&#x200B;**internal**&#x200B;的技術登入，其擁有所有執行個體的所有權利。 安裝之後，登入沒有密碼。 必須定義一個。

若要了解詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

## 啟動Adobe Campaign服務 {#starting-adobe-campaign-services}

若要啟動Adobe Campaign服務，您可以使用服務管理員，或在命令列輸入以下內容（搭配適當的許可權）：

```sql
net start nlserver6
```

如果您稍後需要停止Adobe Campaign程式，請使用命令：

```sql
net stop nlserver6
```

## 安裝LibreOffice {#installing-libreoffice}

下載LibreOffice並遵循一般安裝步驟。

新增下列環境變數：

```sql
OOO_BASIS_INSTALL_DIR="C:\Program Files (x86)\LibreOffice 6\"
```
