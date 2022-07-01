---
product: campaign
title: 配置對Vertica的訪問
description: 瞭解如何配置FDA中對Vertica的訪問
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 8b2a9c73-807a-4936-9fd6-9d26c805a31f
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 2%

---

# 配置對Vertica的訪問 {#configure-fda-vertica}

![](../../assets/v7-only.svg)

使用市場活動 **聯合資料存取** (FDA)選項，用於處理儲存在外部資料庫中的資訊。 按照以下步驟配置訪問 [!DNL Vertica]。

1. 配置 [!DNL Vertica] 上 [CentOS](#vertica-centos)。 [窗口](#vertica-windows) 或 [德比](#vertica-debian)
1. 配置 [!DNL Vertica] [外部帳戶](#vertica-external) 在活動中

>[!NOTE]
>
>[!DNL Vertica] 連接器可用於混合部署和內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## CentOS上的Vertica {#vertica-centos}

配置 [!DNL Vertica] 在CentOS上，執行以下步驟：

1. 下載ODBC驅動程式 [!DNL Vertica]。 [按一下這裡](https://www.vertica.com/download/vertica/client-drivers/) 下載最新的Linux RPM。

1. 然後，需要使用以下命令安裝unixODBC:

   ```
   yum search unixODBC
   yum install unixODBC.x86_64
   ```

1. 如果您以前安裝過 [!DNL Vertica] 伺服器，將已安裝ODBC驅動程式。 在這種情況下，請按如下方式更新驅動器：

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

1. 在Adobe Campaign，您可以配置 [!DNL Vertica] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#vertica-external)。

## Windows上的Vertica {#vertica-windows}

1. 下載 [Windows的ODBC驅動程式](https://www.vertica.com/download/vertica/client-drivers/)。 要安裝Windows驅動程式，您需要啟用.NET Framework 3.5，否則安裝嚮導將嘗試自動啟用並下載它。

1. 在Windows中配置ODBC驅動程式。 有關此內容的詳細資訊，請參閱 [此頁](https://www.vertica.com/docs/9.2.x/HTML/Content/Authoring/ConnectingToVertica/ClientODBC/SettingUpADSN.htm)

1. 在Adobe Campaign，您可以配置 [!DNL Vertica] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#vertical-external)。

## 德比語上的維蒂卡 {#vertica-debian}

1. 下載ODBC驅動程式 [!DNL Vertica]。 [按一下這裡](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 開始下載。

1. 然後，需要使用以下命令安裝unixODBC:

   ```
   apt-get install unixODBC
   ```

1. 如果您以前安裝過 [!DNL Vertica] 伺服器，將已安裝ODBC驅動程式。 在這種情況下，請按如下方式更新驅動器：

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

1. 在Adobe Campaign，您可以配置 [!DNL Vertica] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#vertica-external)。

## Vertica外部帳戶 {#vertica-external}

您需要建立 [!DNL Vertica] 將市場活動實例連接到您的外部帳戶 [!DNL Vertica] 外部資料庫。

1. 從市場活動 **[!UICONTROL Explorer]**&#x200B;按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為您的外部帳戶 **[!UICONTROL Type]**。

1. 配置 **[!UICONTROL Vertica]** 外部帳戶，必須指定：

   * **[!UICONTROL Type]**: [!DNL Vertica Analytics]

   * **[!UICONTROL Server]**:URL [!DNL Vertica] 伺服器

   * **[!UICONTROL Account]**:用戶名

   * **[!UICONTROL Password]**:用戶帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

   ![](assets/vertica.png)

連接器支援以下選項：

| Option | 說明 |
|---|---|
| 時區名稱 | 預設為空，這意味著使用Campaign Classic應用伺服器的系統時區。 該選項可用於強制TIMEZONE會話參數。 |

