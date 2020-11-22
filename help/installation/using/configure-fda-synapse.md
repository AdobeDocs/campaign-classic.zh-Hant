---
solution: Campaign Classic
product: campaign
title: 配置對突觸的訪問
description: 瞭解如何在FDA中配置對Synapse的訪問
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---


# 配置對Azure突觸的訪問 {#configure-access-to-azure-synapse}

使用Campaign [Federated Data Access](../../installation/using/about-fda.md) (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟來設定對Microsoft Azure Synapse Analytics的存取。

1. 在 [CentOS](#azure-centos)、 [Windows](#azure-windows) 或 [Debian上設定Azure突觸](#azure-debian)
1. 在Campaign中設定Azure [突觸外部帳戶](#azure-external) 。

## CentOS上的Azure突觸 {#azure-centos}

>[!CAUTION]
>
>* 安裝ODBC驅動程式時需要根權限。
>* Microsoft提供的Red Hat Enterprise ODBC驅動程式也可與CentOS一起使用以連接到SQL Server。
>* 13.0版將適用於Red Hat 6和7。


要在CentOS上配置Azure Synapse，請執行以下步驟：

1. 首先，安裝ODBC驅動程式。 您可在本頁找到 [它](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

   >[!NOTE]
   >
   >這是ODBC驅動程式第13版的獨有內容。

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/6/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   # Uninstall if already installed Unix ODBC driver
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   
   sudo ACCEPT_EULA=Y yum install msodbcsql
   
   sudo ACCEPT_EULA=Y yum install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   
   # the Microsoft driver expects unixODBC to be here /usr/lib64/libodbc.so.1, so add soft links to the '.so.2' files
   cd /usr/lib64
   sudo ln -s libodbccr.so.2   libodbccr.so.1
   sudo ln -s libodbcinst.so.2 libodbcinst.so.1
   sudo ln -s libodbc.so.2     libodbc.so.1
   
   # Set the path for unixODBC
   export ODBCINI=/usr/local/etc/odbc.ini
   export ODBCSYSINI=/usr/local/etc
   source ~/.bashrc
   
   #Add a DSN information to /etc/odbc.ini
   sudo vi /etc/odbc.ini
   
   #Add the following:
   [Azure Synapse Analytics]
   Driver      = ODBC Driver 13 for SQL Server
   Description = Azure Synapse Analytics DSN
   Trace       = No
   Server      = [insert your server here]
   ```

1. 如果需要，可以通過運行以下命令來安裝unixODBC開發標頭：

   ```
   sudo yum install unixODBC-devel
   ```

1. 安裝驅動程式後，您可以測試並驗證ODBC驅動程式，並根據需要查詢資料庫。 運行以下命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在促銷活動中，您可以接著設定您的 [!DNL Azure Synapse] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參 [閱本節](#azure-external)。

1. 由於Azure Synapse Analytics通過TCP 1433埠進行通信，因此您需要在防火牆上開啟此埠。 使用下列命令：

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >若要允許來自Azure Synapse Analytics的通訊，您可能需要將公用IP新增至allowlist。 若要這麼做，請參閱 [Azure檔案](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

1. 如果是iptables，請運行以下命令：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## Windows上的Azure突觸 {#azure-windows}

>[!NOTE]
>
>這是ODBC驅動程式第13版的獨有內容，但Adobe Campaign Classic也可以使用SQL Server Native Client驅動程式11.0和10.0。

要在Windows上配置Azure突觸：

1. 首先，安裝Microsoft ODBC驅動程式。 您可在本頁中找 [到它](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

1. 選擇要安裝的以下檔案：

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. 在安裝ODBC驅動程式後，您可以根據需要對其進行測試。 如需關於此項目的詳細資訊，請參閱此[頁面](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)。

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Azure Synapse] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參 [閱本節](#azure-external)。

1. 由於Azure Synapse Analytics通過TCP 1433埠進行通信，因此您需要在Windows Defender Firewall上開啟此埠。 For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

## Debian上的Azure突觸 {#azure-debian}

**必要條件:**

* 安裝ODBC驅動程式時需要根權限。
* 需要Curl才能安裝msodbcsql軟體包。 如果尚未安裝，請運行以下命令：

   ```
   sudo apt-get install curl
   ```

要在Debian上配置Azure突觸：

1. 首先，安裝SQL Server的Microsoft ODBC驅動程式。 使用以下命令來安裝SQL Server的ODBC驅動程式13.1:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. 如果您在呼叫 **sudo apt-get update時遇到以下錯誤：** 「The method driver /usr/lib/apt/methods/https could not be found」（方法驅動程式/usr/lib/apt/methods/https找不到） ****，則應運行該命令：

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 您現在需要使用下列命令安裝mssql-tools。 需要Mssq-tools才能使用批量復製程式（或BCP）實用程式並運行查詢。

   ```
   sudo ACCEPT_EULA=Y apt-get install mssql-tools
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bash_profile
   echo 'export PATH="$PATH:/opt/mssql-tools/bin"' >> ~/.bashrc
   source ~/.bashrc
   ```

1. 如果需要，可以通過運行以下命令來安裝unixODBC開發標頭：

   ```
   sudo yum install unixODBC-devel
   ```

1. 安裝驅動程式後，您可以測試並驗證ODBC驅動程式，並根據需要查詢資料庫。 運行以下命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在Campaign Classic中，您現在可以設定您的 [!DNL Azure Synapse] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參 [閱本節](#azure-external)。

1. 若要在Debian上配置iptables以確保與Azure Synapse Analytics的連接，請使用下列命令為您的主機名啟用出站TCP 1433埠：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >若要允許來自Azure Synapse Analytics的通訊，您可能需要將公用IP新增至allowlist。 若要這麼做，請參閱 [Azure檔案](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。


## Azure Synapse外部帳戶 {#azure-external}

外部 [!DNL Azure Synapse] 帳戶可讓您將Campaign例項連接至Azure Synapse外部資料庫。

若要建立您的 [!DNL Azure Synapse] 外部帳戶，請遵循下列步驟：

1. 在促銷 **[!UICONTROL Explorer]**&#x200B;活動中，按 **[!UICONTROL Administration]** 一下「>」 **[!UICONTROL Platform]** 「>」 **[!UICONTROL External accounts]**。

1. 按一下 **[!UICONTROL New]**。

1. 選 **[!UICONTROL External database]** 擇作為外部帳戶 **[!UICONTROL Type]**。

   ![](assets/azure_1.png)

1. 設定外 [!DNL Azure Synapse] 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:Azure突觸分析

   * **[!UICONTROL Server]**:Azure Synapse伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

