---
title: 訪問外部資料庫
seo-title: 訪問外部資料庫
description: 訪問外部資料庫
seo-description: null
page-status-flag: never-activated
uuid: b84359b9-c584-431d-80d5-71146d9b6854
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: connectors
discoiquuid: dd3d14cc-5153-428d-a98a-32b46f0fe811
translation-type: tm+mt
source-git-commit: 3acf2359c74a3dc4b18c8976fee14dcbaf3fa510
workflow-type: tm+mt
source-wordcount: '1826'
ht-degree: 2%

---


# 配置FDA連接器 {#specific-configurations-by-database-type}

根據您想要能夠從Adobe Campaign存取的外部資料庫，您需要執行特定的組態。 這些配置實際上涉及在Adobe Campaign伺服器上安裝驅動程式並聲明屬於每個RDBMS的環境變數。

有關舊式連接器（如Teradata、Hadoop 2.1或Netezza）的詳細資訊，請參閱本 [頁](../../platform/using/legacy-connectors.md)。

一般而言，您必須在Adobe Campaign伺服器的外部資料庫上安裝對應的用戶端層。

>[!NOTE]
>
>相容版本會列在「促銷活動相 [容性矩陣」中](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA)。

## 配置對Azure突觸的訪問 {#configure-access-to-azure-synapse}

### Azure突觸外部帳戶 {#azure-external}

外部 [!DNL Azure] 帳戶可讓您將Campaign例項連接至Azure Synapse外部資料庫。
要建立外部 [!DNL Azure Synapse] 帳戶外部帳戶，請：

1. 在Campaign Classic中，設定您的 [!DNL Azure Synapse] 外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]**。

1. 選 **[!UICONTROL External database]** 擇作為外部帳戶 **[!UICONTROL Type]**。

1. 設定外 [!DNL Azure Synapse] 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:Azure突觸分析

   * **[!UICONTROL Server]**:Azure Synapse伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

   ![](assets/azure_1.png)

### CentOS上的Azure突觸 {#azure-centos}

**必要條件:**

* 安裝ODBC驅動程式時需要根權限。
* Microsoft提供的Red Hat Enterprise ODBC驅動程式也可與CentOS一起使用以連接到SQL Server。
* 13.0版將適用於Red Hat 6和7。

在CentOS上配置Azure突觸：

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

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Azure Synapse] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#azure-external)。

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

### Windows上的Azure突觸 {#azure-windows}

>[!NOTE]
>
>這是ODBC驅動程式第13版的獨有內容，但Adobe Campaign Classic也可以使用SQL Server Native Client驅動程式11.0和10.0。

要在Windows上配置Azure突觸：

1. 首先，安裝Microsoft ODBC驅動程式。 您可在本頁找到 [它](https://www.microsoft.com/en-us/download/details.aspx?id=50420)。

1. 選擇要安裝的以下檔案：

   ```
   your_language\your_architecture\msodbcsql.msi (i.e: English\X64\msodbcsql.msi)
   ```

1. 在安裝ODBC驅動程式後，您可以根據需要對其進行測試。 如需關於此項目的詳細資訊，請參閱此[頁面](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/system-requirements-installation-and-driver-files?view=sql-server-ver15#installing-microsoft-odbc-driver-for-sql-server)。

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Azure Synapse] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#azure-external)。

1. 由於Azure Synapse Analytics通過TCP 1433埠進行通信，因此您需要在Windows Defender Firewall上開啟此埠。 For more on this, refer to [Windows documentation](https://docs.microsoft.com/en-us/windows/security/threat-protection/windows-firewall/create-an-outbound-program-or-service-rule).

### Debian上的Azure突觸 {#azure-debian}

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

1. 在Campaign Classic中，您現在可以設定您的 [!DNL Azure Synapse] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#azure-external)。

1. 若要在Debian上配置iptables以確保與Azure Synapse Analytics的連接，請使用下列命令為您的主機名啟用出站TCP 1433埠：

   ```
   iptables -A OUTPUT -p tcp -d [server_hostname_here] --dport 1433 -j ACCEPT
   ```

   >[!NOTE]
   >
   >若要允許來自Azure Synapse Analytics的通訊，您可能需要將公用IP新增至allowlist。 若要這麼做，請參閱 [Azure檔案](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-firewall-configure#use-the-azure-portal-to-manage-server-level-ip-firewall-rules)。

## 配置對雪花的訪問 {#configure-access-to-snowflake}

>[!NOTE]
>
>[!DNL Snowflake] connector適用於代管和內部部署。 有關詳細資訊，請參見[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

### 雪花外部帳戶 {#snowflake-external}

外部 [!DNL Snowflake] 帳戶可讓您將促銷活動實例連接至Snowflake外部資料庫。

1. 在Campaign Classic中，設定您的 [!DNL Snowflake] 外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]**。

1. 選 **[!UICONTROL External database]** 擇作為外部帳戶 **[!UICONTROL Type]**。

1. 設定外 **[!UICONTROL Snowflake]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:伺服器的URL [!DNL Snowflake]

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

   ![](assets/snowflake.png)

1. 按一下標 **[!UICONTROL Parameters]** 簽，然後按一 **[!UICONTROL Deploy functions]** 下按鈕以建立函式。

   ![](assets/snowflake_2.png)

連接器支援以下選項：

| 選項 | 說明 |
|---|---|
| 工作架構 | 用於工作表的資料庫模式 |
| 倉庫 | 要使用的預設倉庫名稱。 它會覆寫使用者的預設值。 |
| 時區名稱 | 預設為空，這表示使用Campaign Classic應用程式伺服器的系統時區。 此選項可用於強制TIMEZONE會話參數。 <br>有關詳細資訊，請參見[此頁面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | WEEK_START會話參數。 依預設設為0。 <br>有關詳細資訊，請參見[此頁面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | USE_CACHED_RESULTS會話參數。 預設設定為TRUE。 此選項可用於禁用雪花快取結果。 <br>有關詳細資訊，請參見[此頁面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |

### CentOS上的雪花 {#snowflake-centos}

1. 下載的ODBC驅動程式 [!DNL Snowflake]。 [按一下這裡](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) ，開始下載。
1. 然後，您需要使用以下命令在CentOs上安裝ODBC驅動程式：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 在下載並安裝ODBC驅動程式後，您需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Snowflake] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#snowflake-external)。

### 德比安雪花 {#snowflake-debian}

1. 下載的ODBC驅動程式 [!DNL Snowflake]。 [按一下這裡](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) ，開始下載。

1. 然後，您需要使用以下命令在Debian上安裝ODBC驅動程式：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 在下載並安裝ODBC驅動程式後，您需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Snowflake] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#snowflake-external)。

### 窗戶上的雪花 {#snowflake-windows}

1. 下載Windows [版ODBC驅動程式](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)。 請注意，您需要管理員級權限才能安裝驅動程式。 For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驅動程式。 For more on this, refer to [this page](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Snowflake] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#snowflake-external)。

## 配置對Hadoop 3.0的訪問 {#configure-access-to-hadoop-3}

### Hadoop外部帳戶 {#hadoop-external}

外部 [!DNL Hadoop] 帳戶可讓您將Campaign實例連接到Hadoop外部資料庫。

1. 在Campaign Classic中，設定您的 [!DNL Hadoop] 外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]**。

1. 選 **[!UICONTROL External database]** 擇作為外部帳戶 **[!UICONTROL Type]**。

1. 設定外 **[!UICONTROL Hadoop]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**:DNS的名稱

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:DSN中未指定的資料庫名稱。 如果在DSN中指定，則可保留為空

   * **[!UICONTROL Time zone]**:伺服器時區

   ![](assets/hadoop3.png)

連接器支援以下ODBC選項：

| 名稱 | 值 |
|---|---|
| ODBCMgr | iODBC |
| 倉庫 | 1/2/4 |

連接器還支援以下Hive選項：

| 名稱 | 值 | 說明 |
|---|---|---|
| bulkKey | Azure blob或DataLake存取金鑰 | 對於wasb://或wasbs://大量載入器(即，如果批量載入工具以wasb://或wasbs://開頭)。 <br>它是blob或DataLake儲存貯體的存取金鑰，以進行大量載入。 |
| hdfsPort | 埠 <br>號預設設定為8020 | 對於HDFS批量載入(即，如果批量載入工具以webhdfs://或webhdfss://開頭)。 |
| burketsNumber | 20 | 建立聚簇表時的桶數。 |
| fileFormat | 鑲木 | 工作表的預設檔案格式。 |

### 配置Hadoop 3.0 {#configuring-hadoop}

在FDA中連線至Hadoop外部資料庫需要Adobe Campaign伺服器上的下列組態。 請注意，此配置適用於Windows和Linux。

1. 根據您的OS版本下載Hadoop的ODBC驅動程式。 此頁上可找到驅 [動程式](https://www.cloudera.com/downloads.html)。

1. 然後，您需要安裝ODBC驅動程式並為Hive連接建立DSN。 本頁提供說 [明](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)

1. 在下載並安裝ODBC驅動程式後，您需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Hadoop] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#hadoop-external)。

## 配置對Oracle的訪問 {#configure-access-to-oracle}

### Oracle外部帳戶 {#oracle-external}

外部 [!DNL Oracle] 帳戶可讓您將Campaign實例連接到Hadoop外部資料庫。

1. 在Campaign Classic中，設定您的 [!DNL oracle] 外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一下 **[!UICONTROL New]**。

1. 選 **[!UICONTROL External database]** 擇作為外部帳戶 **[!UICONTROL Type]**。

1. 設定外 **[!UICONTROL Oracle]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:Oracle

   * **[!UICONTROL Server]**:DNS的名稱

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Time zone]**:伺服器時區

   ![](assets/oracle_config.png)

### Linux上的Oracle {#for-linux-1}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的其他設定。

1. 安裝與Oracle版本對應的Oracle完整客戶端。
1. 將您的TNS定義新增至安裝。 要執行此操作，請在/etc/oracle儲存庫 **的tnsnames.ora** 檔案中指定它們。 如果此儲存庫不存在，請建立它。

   然後建立新的TNS_ADMIN環境變數：導出TNS_ADMIN=/etc/oracle並重新啟動電腦。

1. 將Oracle整合到您的Adobe Campaign伺服器(nlserver)。 若要這麼做，請檢查 **customer.sh** 檔案是否位於Adobe Campaign伺服器樹狀結構的「nl6」資料夾中，且其中包含Oracle程式庫的連結。

   例如，對於11.2版的客戶：

   ```
   export ORACLE_HOME=/usr/lib/oracle/11.2
   export TNS_ADMIN=/etc/oracle
   export LD_LIBRARY_PATH=$ORACLE_HOME/client64/lib:$LD_LIBRARY_PATH
   ```

   >[!NOTE]
   >
   >這些值（尤其是ORACLE_HOME）取決於您的安裝儲存庫。 請務必先檢查樹結構，然後再參照這些值。

1. 安裝Oracle所需的庫：

   * **libclntsh.so**

      ```
      cd /usr/lib/oracle/<version>/client<architecture>/lib
      ln -s libclntsh.so.<version> libclntsh.so
      ```

   * **libaio1**

      ```
      aptitude install libaio1
      or
      yum install libaio1
      ```

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Oracle] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#oracle-external)。

### Windows版Oracle {#for-windows-1}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的其他設定。

1. 安裝Oracle客戶端。

1. 在C:Oracle資料夾中，建立包含 **TNS定義的tnsnames.ora** 檔案。

1. 以C:Oracle為值添加TNS_ADMIN環境變數並重新啟動電腦。

1. 在Campaign Classic中，您接著可以設定您的 [!DNL Oracle] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱此 [節](../../platform/using/specific-configuration-database.md#oracle-external)。