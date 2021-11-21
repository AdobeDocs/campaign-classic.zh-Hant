---
product: campaign
title: 設定Vertica的存取權
description: 了解如何在FDA中設定Vertica的存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 0cfe8439007b56014eba497c511904c4f11b39ce
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---

# 設定Vertica的存取權 {#configure-fda-vertica}

![](../../assets/v7-only.svg)

使用Campaign **同盟資料存取** (FDA)處理儲存於外部資料庫的資訊的選項。 請依照下列步驟，設定 [!DNL Vertica].

1. 設定 [!DNL Vertica] on [CentOS](#vertica-centos), [Windows](#vertica-windows) 或 [Debian](#vertica-debian)
1. 設定 [!DNL Vertica] [外部帳戶](#vertica-external) 在Campaign


>[!NOTE]
>
>[!DNL Vertica] 連接器適用於混合部署和內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## CentOS上的Vertica {#vertica-centos}

配置 [!DNL Vertica] 在CentOS上，請遵循下列步驟：

1. 下載ODBC驅動程式 [!DNL Vertica]. [按一下這裡](https://www.vertica.com/download/vertica/client-drivers/) 下載最新的Linux RPM。

1. 然後，需要使用以下命令安裝unixODBC:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 如果您先前已安裝 [!DNL Vertica] 伺服器，將已安裝ODBC驅動程式。 在這種情況下，請按如下方式更新驅動器：

   ```
   #Switch to root
   sudo su
   
   #Install the package (add --force to update it)
   rpm -Uvh vertica-client-x.x.x-x.x86_64.rpm [--force]
   
   #Open odbcinst.ini
   vi /etc/odbcinst.ini
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   
   #Cleanup
   #Remove the ODBC package
   rm vertica-client-x.x.x-x.x86_64.rpm
   ```

1. 在Adobe Campaign中，您可以設定 [!DNL Vertica] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#vertica-external).

## Windows上的Vertica {#vertica-windows}

1. 下載 [Windows的ODBC驅動程式](https://www.vertica.com/download/vertica/client-drivers/). 要安裝Windows驅動程式，您需要啟用.NET Framework 3.5，否則安裝嚮導將嘗試自動啟用並下載它。

1. 在Windows中配置ODBC驅動程式。 有關詳細資訊，請參閱 [本頁](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. 在Adobe Campaign中，您可以設定 [!DNL Vertica] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#vertical-external).

## Vertica on Debian {#vertica-debian}

1. 下載ODBC驅動程式 [!DNL Vertica]. [按一下這裡](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 開始下載。

1. 然後，需要使用以下命令安裝unixODBC:

   ```
   apt-get install unixODBC
   ```

1. 如果您先前已安裝 [!DNL Vertica] 伺服器，將已安裝ODBC驅動程式。 在這種情況下，請按如下方式更新驅動器：

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
   
   #Add a section for Vertica and save
   [Vertica]
   Description = Vertica ODBC Driver
   Driver = /opt/vertica/lib64/libverticaodbc.so
   
   #Open odbc.ini
   vi /etc/odbc.ini
   
   #Add your DSN in ODBC Data Sources section, for example:
   [ODBC Data Sources]
   VMart = "VMart database on Vertica"
   
   #Add a DSN definition section below, for example:
   [VMart]
   Description = Vmart Database
   Driver = Vertica
   Database = VMart
   Servername = # The name of the server where Vertica is installed. Use localhost if Vertica is installed on the same machine.
   UID = dbadmin
   PWD = <password>
   Port = 5433
   ```

1. 在Adobe Campaign中，您可以設定 [!DNL Vertica] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#vertica-external).

## Vertica外部帳戶 {#vertica-external}

您需要建立 [!DNL Vertica] 外部帳戶，將您的Campaign執行個體連線至您的 [!DNL Vertica] 外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為外部帳戶 **[!UICONTROL Type]**.

1. 設定 **[!UICONTROL Vertica]** 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**:的URL [!DNL Vertica] 伺服器

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱
   ![](assets/vertica.png)
