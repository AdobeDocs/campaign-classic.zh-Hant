---
product: campaign
title: 配置對Synapse的訪問
description: 瞭解如何配置對FDA中Synapse的訪問
audience: platform
content-type: reference
topic-tags: connectors
exl-id: 59d0277a-7588-4504-94e3-50f87b60da8a
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 1%

---

# 配置對Azure synapse的訪問 {#configure-access-to-azure-synapse}

![](../../assets/v7-only.svg)

使用市場活動 [聯合資料存取](../../installation/using/about-fda.md) (FDA)選項，用於處理儲存在外部資料庫中的資訊。 按照以下步驟配置訪問 **MicrosoftAzure synapse分析**。

1. 配置Azure synapse [CentOS](#azure-centos)。 [窗口](#azure-windows) 或 [德比](#azure-debian)
1. 配置Azure synapse [外部帳戶](#azure-external) 在活動中

## azure synapseCentOS {#azure-centos}

>[!CAUTION]
>
>* 您需要根權限才能安裝ODBC驅動程式。
>* Microsoft提供的Red Hat Enterprise ODBC驅動程式也可與CentOS一起使用以連接到SQL Server。
>* 版本13.0將與Red Hat 6和7配合使用。


要在CentOS上配置Azure synapse，請執行以下步驟：

1. 首先，安裝ODBC驅動程式。 你可以在這裡找到 [頁](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

   >[!NOTE]
   >
   >這不適用於ODBC驅動程式的版本13。

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

1. 安裝驅動程式後，您可以test和驗證ODBC驅動程式，並根據需要查詢資料庫。 運行以下命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在「市場活動」中，您可以配置 [!DNL Azure Synapse] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#azure-external)。

1. 由於Azure synapse分析通過TCP 1433埠進行通信，因此您需要在防火牆上開啟此埠。 使用以下命令：

   ```
   firewall-cmd --permanent --add-rich-rule='rule family="ipv4" source address="[server_ip_here]/32" port port="1433" protocol="tcp" accept'
   # you can ping your hostname and the ping command will translate the hostname to IP address which you can use here
   ```

   >[!NOTE]
   >
   >要允許來自Azure synapse分析的通信，可能需要將公共IP添加到允許清單。 為此，請參閱 [Azure文檔](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

1. 如果是iptables，請運行以下命令：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

## azure synapseWindows {#azure-windows}

>[!NOTE]
>
>這不適用於ODBC驅動程式版本13，但Adobe Campaign Classic還可以使用SQL Server Native Client驅動程式11.0和10.0。

要在Windows上配置Azure synapse:

1. 首先，安裝MicrosoftODBC驅動程式。 你可以在 [此頁](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

1. 選擇要安裝的以下檔案：

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. 安裝ODBC驅動程式後，如果需要，可以test它。 如需關於此項目的詳細資訊，請參閱此[頁面](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)。

1. 在Campaign Classic中，您可以配置 [!DNL Azure Synapse] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#azure-external)。

1. 由於Azure synapse分析通過TCP 1433埠進行通信，因此您需要在Windows Defender防火牆上開啟此埠。 有關此內容的詳細資訊，請參閱 [Windows文檔](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule)。

## azure synapse德比 {#azure-debian}

**必要條件:**

* 您需要根權限才能安裝ODBC驅動程式。
* 安裝msodbcsql包需要Curl。 如果未安裝，請運行以下命令：

   ```
   sudo apt-get install curl
   ```

要在Debian上配置Azure synapse:

1. 首先，為SQL Server安裝MicrosoftODBC驅動程式。 使用以下命令為SQL Server安裝ODBC驅動程式13.1:

   ```
   sudo su
   curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
   curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list
   exit
   sudo apt-get update
   sudo ACCEPT_EULA=Y apt-get install msodbcsql
   ```

1. 如果遇到以下錯誤 **&quot;找不到方法驅動程式/usr/lib/apt/methods/https&quot;** 呼叫 **sudo apt get更新**，您應運行以下命令：

   ```
   sudo apt-get install apt-transport-https ca-certificates
   ```

1. 現在，您需要使用以下命令安裝mssql-tools。 使用批量復製程式（或BCP）實用程式和運行查詢需要Mssq-tools。

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

1. 安裝驅動程式後，您可以test和驗證ODBC驅動程式，並根據需要查詢資料庫。 運行以下命令：

   ```
   /opt/mssql-tools/bin/sqlcmd -S yourServer -U yourUserName -P yourPassword -q "your query" # for example -q "select 1"
   ```

1. 在Campaign Classic中，您現在可以配置 [!DNL Azure Synapse] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#azure-external)。

1. 要在Debian上配置iptables以確保與Azure synapse分析的連接，請使用以下命令為主機名啟用出站TCP 1433埠：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >要允許來自Azure synapse分析的通信，可能需要將公共IP添加到允許清單。 為此，請參閱 [Azure文檔](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

## azure synapse外部帳戶 {#azure-external}

的 [!DNL Azure Synapse] 外部帳戶允許您將市場活動實例連接到Azure synapse外部資料庫。

建立 [!DNL Azure Synapse] 外部帳戶遵循以下步驟：

1. 從市場活動 **[!UICONTROL Explorer]**&#x200B;按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為您的外部帳戶 **[!UICONTROL Type]**。

   ![](assets/azure_1.png)

1. 下 **[!UICONTROL Configuration]**&#x200B;選中 **[!UICONTROL Azure Synapse Analytics]** 從 **[!UICONTROL Type]** 下拉。

   ![](assets/azure_2.png)

1. 配置 [!DNL Azure Synapse] 外部帳戶：

   * 對於標準驗證，必須指定：

      * **[!UICONTROL Server]**:azure synapse伺服器的URL

      * **[!UICONTROL Account]**:用戶名

      * **[!UICONTROL Password]**:用戶帳戶密碼

      * **[!UICONTROL Database]**:資料庫的名稱

      ![](assets/azure_3.png)

   * 對於系統分配的托管身份驗證，必須指定：

      * **[!UICONTROL Server]**:azure synapse伺服器的URL

      * **[!UICONTROL Database]**:資料庫的名稱

      * **[!UICONTROL Options]**:添加以下語法 `Authentication=ActiveDirectoryMsi`

      ![](assets/azure_4.png)



1. 按一下&#x200B;**[!UICONTROL Save]**。

連接器支援以下選項：

| Option | 說明 |
|---|---|
| 驗證 | 連接器支援的驗證類型。 當前支援的值：ActiveDirectoryMSI。 </br>有關詳細資訊，請參閱 [SQL文檔](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings) （連接字串示例n°8）。 |
