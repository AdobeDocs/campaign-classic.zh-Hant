---
product: campaign
title: 設定存取權至 [!DNL Vertica Analytics]
description: 瞭解如何在FDA中設定 [!DNL Vertica Analytics] 的存取權
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 1%

---

# 設定[!DNL Vertica Analytics]的存取權 {#configure-fda-vertica}



使用Campaign **同盟資料存取** (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟設定[!DNL Vertica Analytics]的存取權。

1. 在[CentOS](#vertica-centos)、[Windows](#vertica-windows)或[Debian](#vertica-debian)上設定[!DNL Vertica Analytics]
1. 在Campaign中設定[!DNL Vertica Analytics] [外部帳戶](#vertica-external)

![](assets/snowflake_3.png)

## CentOS上的[!DNL Vertica Analytics] {#vertica-centos}

若要在CentOS上設定[!DNL Vertica Analytics]，請遵循下列步驟：

1. 下載[!DNL Vertica Analytics]的ODBC驅動程式。 [按一下這裡](https://www.vertica.com/download/vertica/client-drivers/)下載最新的Linux RPM。

1. 然後，您需要使用以下命令安裝unixODBC：

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 如果您先前已安裝[!DNL Vertica Analytics]伺服器，則會已經安裝ODBC驅動程式。 在此情況下，請依照下列步驟更新磁碟機：

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [VerVertica Analyticstica]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. 然後，您可以在Adobe Campaign中設定[!DNL Vertica Analytics]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#vertica-external)。

## Windows上的[!DNL Vertica Analytics] {#vertica-windows}

1. 下載適用於Windows](https://www.vertica.com/download/vertica/client-drivers/)的[ODBC驅動程式。 若要安裝適用於Windows的驅動程式，您必須啟用.NET Framework 3.5，否則安裝助理會嘗試自動啟用並下載驅動程式。

1. 在Windows中設定ODBC驅動程式。 如需詳細資訊，請參閱[此頁面](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. 然後，您可以在Adobe Campaign中設定[!DNL Vertica Analytics]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#vertical-external)。

## 在Debian上的[!DNL Vertica Analytics] {#vertica-debian}

1. 下載[!DNL Vertica Analytics]的ODBC驅動程式。 [按一下這裡](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html)開始下載。

1. 然後，您需要使用以下命令安裝unixODBC：

   ```
   apt-get install unixODBC
   ```

1. 如果您先前已安裝[!DNL Vertica Analytics]伺服器，則會已經安裝ODBC驅動程式。 在此情況下，請依照下列步驟更新磁碟機：

   ```
   #Switch to root
   sudo su
   
   #Move or copy the downloaded file and change to /root
   mv vertica_9.3..xx_odbc_x86_64_linux.tar.gz /
   cd /
   
   #Uncompress the file you downloaded
   tar vzxf vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Remove the tar.gz since it is not needed anymore
   rm vertica_9.3..xx_odbc_x86_64_linux.tar.gz
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica Analytics and save
   [Vertica Analytics]
   Description = Vertica Analytics ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica Analytics"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica Analytics
   Database = VMart
   Servername = # The name of the server where Vertica Analytics is installed. Use localhost if Vertica Analytics is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. 然後，您可以在Adobe Campaign中設定[!DNL Vertica Analytics]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#vertica-external)。

## [!DNL Vertica Analytics]外部帳戶 {#vertica-external}

您必須建立[!DNL Vertica Analytics]外部帳戶，才能將Campaign執行個體連線至[!DNL Vertica Analytics]外部資料庫。

1. 從行銷活動&#x200B;**[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 設定&#x200B;**[!UICONTROL Vertica Analytics]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**： [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**： [!DNL Vertica Analytics]伺服器的URL

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼

   * **[!UICONTROL Database]**：資料庫的名稱

   ![](assets/vertica.png)

聯結器支援下列選項：

| 選項 | 說明 |
|---|---|
| 時區名稱 | 預設為空白，這表示會使用Campaign Classic應用程式伺服器的系統時區。 選項可用來強制TIMEZONE工作階段引數。 |

