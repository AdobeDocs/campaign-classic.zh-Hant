---
product: campaign
title: 配置對Synapse的訪問
description: 了解如何在FDA中配置Synapse的存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '703'
ht-degree: 1%

---

# 配置訪問Azure synapse {#configure-access-to-azure-synapse}

![](../../assets/v7-only.svg)

使用Campaign [同盟資料存取](../../installation/using/about-fda.md)(FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟來設定Microsoft Analytics的存取權限。Azure synapse分析

1. 在[CentOS](#azure-centos)、[Windows](#azure-windows)或[Debian](#azure-debian)上配置Azure synapse
1. 在Campaign中設定Azure synapse[外部帳戶](#azure-external)

## azure synapseCentOS {#azure-centos}

>[!CAUTION]
>
>* 安裝ODBC驅動程式時需要根權限。
>* Microsoft提供的Red Hat Enterprise ODBC驅動程式也可與CentOS一起使用以連接到SQL Server。
>* 13.0版可與Red Hat 6和7搭配使用。


若要在CentOS上設定Azure synapse，請遵循下列步驟：

1. 首先，安裝ODBC驅動程式。 您可以在此[page](https://www.microsoft.com/en-us/download/details.aspx?id=50420)中找到。

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

1. 安裝驅動程式後，您可以測試和驗證ODBC驅動程式，並根據需要查詢資料庫。 執行下列命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在Campaign中，您可以接著設定[!DNL Azure Synapse]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#azure-external)。

1. 由於Azure synapse分析通過TCP 1433埠進行通信，因此您需要在防火牆上開啟此埠。 使用下列命令：

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >若要允許來自Azure synapseAnalytics端的通訊，您可能需要將公用IP新增至允許清單。 要執行此操作，請參閱[Azure檔案](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

1. 如果是iptables，請運行以下命令：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## azure synapseWindows {#azure-windows}

>[!NOTE]
>
>這是ODBC驅動程式13版獨有的，但Adobe Campaign Classic也可以使用SQL Server本機客戶端驅動程式11.0和10.0。

要在Windows上配置Azure synapse:

1. 首先，安裝Microsoft ODBC驅動程式。 您可以在[此頁](https://www.microsoft.com/en-us/download/details.aspx?id=50420)中找到它。

1. 選擇要安裝的檔案：

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. 安裝ODBC驅動程式後，您就可以根據需要進行測試。 如需關於此項目的詳細資訊，請參閱此[頁面](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)。

1. 在Campaign Classic中，您接著可以設定[!DNL Azure Synapse]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#azure-external)。

1. 由於Azure synapse分析通過TCP 1433埠進行通信，因此您需要在Windows Defender防火牆上開啟此埠。 有關詳細資訊，請參閱[Windows文檔](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule)。

## azure synapseDebian {#azure-debian}

**必要條件:**

* 安裝ODBC驅動程式時需要根權限。
* 安裝msodbcsql包時需要curl。 如果尚未安裝，請運行以下命令：

   ```
   sudo apt-get install curl
   ```

若要在Debian上設定Azure synapse:

1. 首先，安裝SQL Server的Microsoft ODBC驅動程式。 使用以下命令安裝SQL Server的ODBC驅動程式13.1:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. 如果在調用&#x200B;**sudo apt-get update**&#x200B;時出現以下錯誤&#x200B;**&quot;找不到方法驅動程式/usr/lib/apt/methods/https&quot;**，則應運行該命令：

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 您現在需要使用以下命令來安裝mssql-tools。 需要Mssq工具才能使用批量復製程式（或BCP）實用程式和運行查詢。

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

1. 安裝驅動程式後，您可以測試和驗證ODBC驅動程式，並根據需要查詢資料庫。 執行下列命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在Campaign Classic中，您現在可以設定[!DNL Azure Synapse]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#azure-external)。

1. 要在Debian上配置iptables以確保與Azure synapse分析的連接，請使用以下命令為主機名啟用出站TCP 1433埠：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >若要允許來自Azure synapseAnalytics端的通訊，您可能需要將公用IP新增至允許清單。 要執行此操作，請參閱[Azure檔案](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。


## azure synapse外部帳戶 {#azure-external}

[!DNL Azure Synapse]外部帳戶可讓您將Campaign執行個體連結至Azure synapse外部資料庫。

要建立[!DNL Azure Synapse]外部帳戶，請執行以下步驟：

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，按一下&#x200B;**[!UICONTROL Administration]**「>」 **[!UICONTROL Platform]**「>」 **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

   ![](assets/azure_1.png)

1. 配置[!DNL Azure Synapse]外部帳戶，必須指定：

   * **[!UICONTROL Type]**:azure synapse分析

   * **[!UICONTROL Server]**:azure synapse伺服器的URL

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱
