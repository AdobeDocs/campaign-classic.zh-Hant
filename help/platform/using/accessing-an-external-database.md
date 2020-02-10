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
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 訪問外部資料庫{#accessing-an-external-database}

## 關於同盟資料存取 {#about-federated-data-access}

Adobe Campaign provides the **Federated Data Access** (FDA) option in order to process information stored in one or more external databases: you can access external data without changing the structure of Adobe Campaign data.

>[!CAUTION]
>
>Federated Data Access **** (FDA)模組是可選的。 請檢查您的Adobe Campaign授權合約。
>  
>此外，只有在現場安裝或混合安裝時，才能通過FDA訪問外部資料庫。

### 操作原則 {#operating-principle}

FDA選項允許您從SQL源收集資料並自動檢測目標表的結構。

若要使用此功能，您必須：

1. 擁有與Adobe Campaign FDA模組相容的外部資料庫。 資料庫系統和相容版本清單在相容性清單中 [有詳細說明](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。 使用者也必須擁有 [Adobe Campaign](#remote-database-access-rights) 和外部資料庫的必要權限。
1. [在Adobe Campaign伺服器上](#specific-configurations-by-database-type) ，安裝與您的資料庫對應的驅動程式。
1. [建立並設定外部帳戶](#connecting-to-the-database) ，讓您建立Adobe Campaign與外部資料庫之間的連線。 有關可用外部帳戶的詳細資訊，請參閱本 [頁](../../platform/using/external-accounts.md)。
1. [在Adobe Campaign中建立外部資料庫的讀取架構](#creating-the-data-schema) 。 這允許您識別外部資料庫的資料結構。
1. 最終， [從先前建立的架構建立新的目標對應](#defining-data-mapping) ，如果傳送的收件者來自外部資料庫的話。 這具有某些限制，特別是在個人化交貨方面。

資料讀取結構建立後，您就可在Adobe Campaign工作流程中處理資料。 如需詳細資訊，請參閱[本小節](../../workflow/using/executing-a-workflow.md#architecture)。

### 最佳實務與建議 {#best-practices-and-recommendations}

FDA選項是用來在工作流程中以批次模式控制外部資料庫中的資料。 在另一種情況下使用FDA，例如進行單一作業時，必須謹慎（個人化、互動、即時傳送等）。

在開始利用外部資料庫之前，請執行效能測試以檢測任何可能的問題並使用此選項進行優化。

請盡量避免需要同時使用Adobe Campaign和外部資料庫的作業。 若要這麼做，您可以：

* 將Adobe Campaign資料庫匯出至外部資料庫，並僅從外部資料庫執行作業，然後再將結果重新匯入Adobe Campaign。
* 從外部Adobe Campaign資料庫收集資料，並在本機執行作業。

如果您想要使用外部資料庫的資料在傳送中進行個人化，請收集要在工作流程中使用的資料，以便在臨時表格中使用。 然後使用臨時表格中的資料來個人化您的傳送。

### 限制 {#limitations}

FDA選項受到您所使用外部資料庫系統的軟性限制。

基於效能原因，我們不建議使用此功能來執行單一作業（傳送個人化、互動模組、即時）。

## 按資料庫類型列出的特定配置 {#specific-configurations-by-database-type}

根據您想要能夠從Adobe Campaign存取的外部資料庫，您需要執行特定的組態。 這些配置實際上涉及在Adobe Campaign伺服器上安裝驅動程式並聲明屬於每個RDBMS的環境變數。

一般而言，您必須在Adobe Campaign伺服器的外部資料庫上安裝對應的用戶端層。

>[!NOTE]
>
>相容版本列在「促銷活動相 [容性矩陣」中](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#FederatedDataAccessFDA) 。

### 配置對Hadoop的訪問 {#configure-access-to-hadoop}

在FDA中連線至Hadoop外部資料庫需要Adobe Campaign伺服器上的下列組態。

#### 適用於Windows {#for-windows}

1. 安裝Windows版 [ODBC和Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886) 驅動程式。
1. 通過運行ODBC資料源管理工具建立DSN（資料源名稱）。 Hive的系統DSN示例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 建立Hadoop外部帳戶，如建立共用連 [接部分中詳細](#creating-a-shared-connection) 。

#### Linux版 {#for-linux}

1. 安裝unixodbc for Linux。

   ```
   apt-get install unixodbc
   ```

1. 從HortonWorks下載並安裝Apache Hive的ODBC驅動程式： [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/)。

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. 檢查ODBC檔案位置。

   ```
   root@campadpac71:/tmp# odbcinst -j
   unixODBC 2.3.1
   DRIVERS............: /etc/odbcinst.ini
   SYSTEM DATA SOURCES: /etc/odbc.ini
   FILE DATA SOURCES..: /etc/ODBCDataSources
   USER DATA SOURCES..: /root/.odbc.ini
   SQLULEN Size.......: 8
   SQLLEN Size........: 8
   SQLSETPOSIROW Size.: 8
   ```

1. 建立DSN（資料源名稱）並編輯odbc.ini檔案。 然後，為Hive連接建立DSN。

   以下是HDInsight設定名為「病毒式」連線的範例：

   ```
   [ODBC Data Sources]
   vorac 
   
   [vorac]
   Driver=/usr/lib/hive/lib/native/Linux-amd64-64/libhortonworkshiveodbc64.so
   HOST=vorac.azurehdinsight.net
   PORT=443
   Schema=sm_tst611
   HiveServerType=2
   AuthMech=6
   UID=admin
   PWD=<your password here>
   HTTPPath=
   UseNativeQuery=1
   ```

   >[!NOTE]
   >
   >此處 **的UseNativeQuery** 參數非常重要。 促銷活動會感知蜂窩，除非設定UseNativeQuery，否則無法正常運作。 通常，驅動程式或Hive SQL連接器將重寫查詢並篡改列順序。

   驗證設定取決於Hive/Hadoop配置。 例如，對於HD Insight，請使用AuthMech=6進行使用者／密碼驗證，如 [此說](http://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)。

1. 匯出變數。

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. 通過/usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini設定Hortonworks驅動程式。

   您必須使用UTF-16才能連線Campaign和unix-odbc(libodbcinst)。

   ```
   [Driver]
   
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=/usr/lib/hive/lib/native/hiveodbc/ErrorMessages/
   LogLevel=0
   LogPath=/tmp/hive
   SwapFilePath=/tmp
   
   ODBCInstLib=libodbcinst.so
   ```

1. 您現在可以使用isql測試連線。

   ```
   isql vorac
   isql vorac -v
   ```

1. 建立Hadoop外部帳戶，如建立共用連 [接部分中詳細](#creating-a-shared-connection) 。

### 配置對MySQL的訪問 {#configure-access-to-mysql}

有關如何配置MySQL資料庫的詳細資訊，請參閱本 [文](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html)。

### 配置對Netezza的訪問 {#configure-access-to-netezza}

在FDA中連線至Netezza外部資料庫需要Adobe Campaign伺服器下的其他設定：

1. 根據您使用的作業系統，安裝Netezza的ODBC驅動程式：

   * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux。 選擇與作業系統（linux或linux64）對應的資料夾，然後啟動unpack命令。 您可以保留在預設情況下建議的儲存庫中執行的安裝：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** for Windows。 解壓縮檔案並啟動與您的作業系統對應的可執行指令碼：nzodbcsetup.exe或nzodbcsetup64.exe。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行： **/etc/odbc.ini** （用於一般參數）和 **/etc/odbcinst.ini（用於聲明驅動程式）** 。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;與odbcinst.ini檔案的位置相對應。

   * **/etc/odbcinst.ini**

      ```
      [ODBC Drivers]
      NetezzaSQL = Installed
      
      [NetezzaSQL]
      Driver           = /usr/local/nz/lib/libnzsqlodbc3.so
      Setup            = /usr/local/nz/lib/libnzsqlodbc3.so
      APILevel         = 1
      ConnectFunctions = YYN
      Description      = Netezza ODBC driver
      DriverODBCVer    = 03.51
      DebugLogging     = false
      LogPath          = /tmp
      UnicodeTranslationOption = utf8
      CharacterTranslationOption = all
      PreFetch         = 256
      Socket           = 16384
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:/usr/local/nz/lib和/usr/local/nz/lib64。 &quot;/usr/local/nz&quot;與安裝驅動程式時預設提供的安裝儲存庫相對應。 您需要在此處指定已為安裝選擇的儲存庫。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NZ_ODBC_INI_PATH**:odbc.ini檔案的位置。 Netezza還需要此第二個變數來使用odbc.ini檔案。

1. 建立Netezza外部帳戶，如建立共用連 [接一節中所述](#creating-a-shared-connection) 。

>[!NOTE]
>
>不考慮對包含自動生成的主鍵的方案的操作。
>
>表將在模式中定義的第 **一個索引上使用** Organize on子句。 由於此子句限制為1到4個Netezza列，因此此索引不能包含4個以上的列。

### 配置對Oracle的訪問 {#configure-access-to-oracle}

在FDA中連線至Oracle外部資料庫需要Adobe Campaign伺服器下方的其他設定。

#### Linux版 {#for-linux-1}

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

#### 適用於Windows {#for-windows-1}

1. 安裝Oracle客戶端。
1. 在C:Oracle資料夾中，建立包含 **TNS定義的tnsnames.ora** 檔案。

   以C:Oracle為值添加TNS_ADMIN環境變數並重新啟動電腦。

### 配置對Sybase IQ的訪問 {#configure-access-to-sybase-iq}

在FDA中連接到Sybase IQ外部資料庫需要在Adobe Campaign伺服器上進行下列其他配置：

1. 確保unixodbc包位於伺服器上。
1. 安裝 **iq_odbc**。 安裝結束時可能會發生錯誤。 此錯誤可以忽略。
1. 安 **裝iq_client_common**。 安裝結束時可能會發生Java錯誤。 此錯誤可以忽略。
1. 配置ODBC驅動程式。 配置可在標準檔案中執行：/etc/odbc.ini，用於常規參數，/etc/odbcinst.ini，用於聲明驅動程式：

   * **/etc/odbc.ini** (以您自己的方式取 `<server_alias>` 代字元等值):

      ```
      [ODBC Data Sources]
      <server_alias>=libdbodbc.so
      
      [<server_alias>]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      Description=<description>
      Username=<username>
      Password=<password>
      ServerName=<server_name>
      CommLinks=tcpip(host=<host>)
      ```

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      SAP SybaseIQ=Installed
      
      [SAP SybaseIQ]
      Driver=/opt/sybase/IQ-16_0/lib64/libdbodbc16.so
      ```

1. 在LD_LIBRARY_PATH變數中添加新libodbc16.so庫的路徑。 若要這麼做：

   * 如果您使用customer.sh檔案來宣告您的路徑：為LD_LIBRARY_PATH變數添加路徑/opt/sybase/IQ-16_0/lib64。
   * 否則，請使用Unix命令。

1. 建立新的FDA外部帳戶，如「建立共用連 [線」一節所述](#creating-a-shared-connection) 。 對於Sybase IQ，伺服器名與步驟5中定義的ODBC連`<server_alias>`接()相對應。 它不一定是伺服器本身的名稱。

>[!NOTE]
>
>對於Windows，必須在Adobe Campaign伺服器上安裝Sybase IQ客戶端並建立ODBC連接。 請確定您在Windows中以服務的形式執行Adobe Campaign伺服器(nlserver)時建立系統資料來源。

### 配置對Teradata的訪問 {#configure-access-to-teradata}

在FDA中連線至Teradata外部資料庫需要Adobe Campaign伺服器上的某些額外設定。 有關如何配置Teradata資料庫的詳細資訊，請參閱本 [文](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html)。

1. 安裝Teradata [的ODBC驅動程式](http://downloads.teradata.com/download/connectivity/odbc-driver/linux)。

   它由三個軟體包組成，可以按以下順序安裝在Red Hat（或CentOS）/Suse上：

   * TeraGSS
   * tdicu1510（使用setup_wrapper.sh安裝）
   * tdobc1510（使用setup_wrapper.sh安裝）

1. 配置ODBC驅動程式。 配置可在標準檔案中執行： **/etc/odbc.ini** for general parameters and /etc/odbcinst.ini for sclariting drivers:

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      ```

      &quot;InstallDir&quot;與 **odbcinst.ini檔案的位置對應** 。

   * **/etc/odbcinst.ini**

      ```
      [ODBC DRIVERS]
      teradata=Installed
      
      [teradata]
      Driver=/opt/teradata/client/15.10/lib64/tdata.so
      APILevel=CORE
      ConnectFunctions=YYY
      DriverODBCVer=3.51
      SQLLevel=1
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:/opt/teradata/client/15.10/lib64和/opt/teradata/client/15.10/odbc_64/lib。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。
   * **NLSPATH**:opermsgs.cat檔案的位置(/opt/teradata/client/15.10/msg/opermsgs.cat)

### 配置對SAP HANA的訪問 {#configure-access-to-sap-hana}

在FDA中連線至SAP HANA外部資料庫需要Adobe Campaign伺服器上的某些額外設定：

1. 根據您使用的作業系統，安裝SAP HANA的ODBC驅動程式：

   * **hdb_client_linux.tgz** for Linux。 解壓縮後，啟動hdbinst命令並按照說明完成驅動程式安裝。
   * **hdb_client_windows.zip** for Windows。 解壓縮檔案並啟動可執行檔： **hdbinst.exe**。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行：/etc/odbc.ini代表一般參數，/etc/odbcinst.ini代表聲明驅動程式。

   * **/etc/odbc.ini**

      ```
      [ODBC]
      InstallDir=/etc/
      
      [HDB]
      Driver=HDBODBC
      servernode=localhost:39013 (this value depend of your server)
      User:SYSTEM
      ```

      &quot;InstallDir&quot;與 **odbcinst.ini檔案的位置對應** 。

   * **/etc/odbcinst.ini**

      ```
      [HDBODBC]
      Description = "SmartCloudPT HANA"
      Driver = /usr/sap/hdbclient/libodbcHDB.so
      ```

1. 指定Adobe Campaign伺服器的環境變數：

   * **LD_LIBRARY_PATH**:它應包含到SAP Hana客戶端(預設情況下為/usr/sap/hdbclient/ [libodbcHDB.so](http://libodbchdb.so/) )的連結。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。

1. 建立SAP Hana外部帳戶，如「建立共用連接」 [部分中所述](#creating-a-shared-connection) 。

## 遠程資料庫訪問權限 {#remote-database-access-rights}

首先，為了讓使用者可以透過FDA對外部資料庫執行作業，後者必須在Adobe Campaign中擁有特定的指名權。

1. 在Adobe Campaign **[!UICONTROL Administration > Access Management > Named Rights]** 檔案總管中選取節點。
1. 指定您選擇的標籤以建立新的權限。
1. 欄位 **[!UICONTROL Name]** 必須採用下列格式 **的使用者：base@server**，其中：

   * **user** 與外部資料庫中的用戶名相對應。
   * **base** 與外部資料庫的名稱相對應。
   * **伺服器** 與外部資料庫伺服器的名稱相對應。

      >[!NOTE]
      >
      >Oracle **中** :base部件是可選的。

1. 儲存指名的右側，然後從Adobe Campaign檔案總管的節 **[!UICONTROL Administration > Access Management > Operators]** 點將其連結至您選擇的使用者。

然後，若要處理外部資料庫中包含的資料，Adobe Campaign使用者必須在資料庫上至少擁有「寫入」權限，才能建立工作表。 Adobe Campaign會自動刪除這些項目。

一般而言，下列權利是必要的：

* **連接**:連接到遠程資料庫，
* **讀取資料**:只讀存取包含客戶資料的表格，
* **閱讀「中繼資料」**:存取伺服器資料目錄以取得表格結構，
* **載入**:在工作表中成批載入（處理系列和聯接時需要）,
* **CREATE/DROP** for **TABLE/INDEX/PROCEDURE/FUNCTION**,
* **EXPLAIN** （建議）:在遇到問題時監控效能，
* **WRITE Data** （視整合藍本而定）。

>[!NOTE]
>
>資料庫管理員需要使這些權限與每個資料庫引擎的特定權限相匹配。 有關詳細資訊，請參閱 [RDBMS特定權限](https://docs.campaign.adobe.com/doc/AC6.1/en/technicalResources/technicalResources.html)。

## 連接到資料庫 {#connecting-to-the-database}

要啟用到外部資料庫的連接，必須指定連接參數，即目標資料源和需要載入資料的表的名稱。

>[!CAUTION]
>
>Adobe Campaign使用者需要外部資料庫和Adobe Campaign應用程式伺服器的特定權限，才能處理來自外部資料庫的資料。 有關詳細資訊，請參閱「遠程數 [據庫訪問權限](#remote-database-access-rights) 」部分。
>
>為避免任何故障，存取遠端共用資料的營運商必須從個別空間工作。

### 建立共用連接 {#creating-a-shared-connection}

若要啟用共用外部資料庫的連線，只要此連線啟用，您就可透過Adobe Campaign存取資料庫。

1. 配置必須事先通過節點 **[!UICONTROL Administration > Platform > External accounts]** 定義。
1. 按一下按 **[!UICONTROL New]** 鈕並選取 **[!UICONTROL External database]** 類型。
1. 定義外 **[!UICONTROL Connection]** 部資料庫的參數。

   對於到 **ODBC** **[!UICONTROL Server]** type資料庫的連接，欄位必須包含ODBC資料源的名稱，而不包含伺服器名。 此外，可能需要某些附加配置，具體取決於使用的資料庫。 請參閱「按數 [據庫類型列出的特定配置](#specific-configurations-by-database-type) 」部分。

1. 在輸入參數後，按一下按 **[!UICONTROL Test the connection]** 鈕以核准參數。

   ![](assets/wf-external-account-create.png)

1. 如有必要，請取消選 **[!UICONTROL Enabled]** 中禁用對此資料庫的訪問而不刪除其配置的選項。
1. 若要允許Adobe Campaign存取此資料庫，您必須部署SQL函式。 按一下標 **[!UICONTROL Parameters]** 簽，然後按一 **[!UICONTROL Deploy functions]** 下按鈕。

   ![](assets/wf-external-account-functions.png)

可以在頁籤中為表和索引定義特定的工作表 **[!UICONTROL Parameters]** 空間。

### 使用Windows驗證建立連接 {#creating-a-connection-with-windows-authentication}

您也可以使用Windows驗證透過FDA連線。 操作步驟：

* 請確定Adobe Campaign服務是由不同於本機系統帳戶的Windows帳戶執行。
* 請確定Adobe Campaign運算子會針對Adobe Campaign應用程式伺服器和外部資料庫提供足夠的權限。
* 不需指定和，即可建立對應的 **[!UICONTROL Account]** 外部帳戶 **[!UICONTROL Password]**。 僅指定資料庫的名稱。

### 建立臨時連接 {#creating-a-temporary-connection}

您可以從工作流活動直接定義到外部資料庫的連接。 在這種情況下，它將位於本地外部資料庫上，保留以用於當前工作流：不會儲存在外部帳戶中。 此類型的守時連線可建立在工作流程的不同活動上，尤其 **[!UICONTROL Query]**&#x200B;是 **[!UICONTROL Data loading (RDBMS)]**、 **[!UICONTROL Enrichment]** 活動或活 **[!UICONTROL Split]** 動。

>[!CAUTION]
>
>不建議使用此類配置，但可定期用於收集資料。 不過，您應建立外部帳戶，如「建立共用連 [線」一節所示](#creating-a-shared-connection) 。

例如，在查詢活動中，建立到外部資料庫的定期連接的步驟如下：

1. 按一下 **[!UICONTROL Add data...]** 並選取 **[!UICONTROL External data]** 選項。
1. 選擇選 **[!UICONTROL Locally defining the data source]** 項。

   ![](assets/wf_add_data_local_external_data.png)

1. 在下拉清單中選擇目標資料庫引擎。 輸入伺服器的名稱並提供驗證參數。

   也指定外部資料庫的名稱。

   ![](assets/wf_add_data_local_external_data_param.png)

   Click the **[!UICONTROL Next]** button.

1. 選擇儲存資料的表。

   您可以直接在相應欄位中輸入表的名稱，或按一下編輯表徵圖訪問資料庫表的清單。

   ![](assets/wf_add_data_local_external_data_select_table.png)

1. 按一下 **[!UICONTROL Add]** 按鈕，可定義外部資料庫資料與Adobe Campaign資料庫中資料之間的一或數個協調欄位。 和 **[!UICONTROL Edit expression]** 的圖 **[!UICONTROL Remote field]** 標 **[!UICONTROL Local field]** 允許您訪問每個表的欄位清單。

   ![](assets/wf_add_data_local_external_data_join.png)

1. 如有必要，請指定篩選條件和資料排序模式。
1. 選擇要在外部資料庫中收集的其他資料。 若要這麼做，請連按兩下您要新增的欄位，以在中顯示欄位 **[!UICONTROL Output columns]**。

   ![](assets/wf_add_data_local_external_data_select.png)

   按一下 **[!UICONTROL Finish]** 確認此配置。

### 安全連接 {#secure-connection}

在設定外部FDA帳戶時，您可以確保外部資料庫的存取安全。

若要這麼做，請在使用之端&#x200B;**口的伺服器位址和位址後新增「:ssl**」。 例如： **192.168.0.52:4501:ssl**。

然後，資料會透過安全SSL通訊協定傳送。

### 其他配置 {#additional-configurations}

如有必要，可以建立用於處理外部資料庫中資料的模式。 同樣地，Adobe Campaign也可讓您定義外部表格中資料的對應。 這些設定是一般的，不僅適用於工作流程。

>[!NOTE]
>
>如需在Adobe Campaign中建立結構以及定義新資料對應的詳細資訊，請參 [閱此頁](../../configuration/using/about-schema-edition.md)。

## 建立資料架構 {#creating-the-data-schema}

要在外部資料庫上建立方案，請按一下 **[!UICONTROL New]** 資料方案清單上方的按鈕，然後選擇 **[!UICONTROL Access external data]**。

![](assets/wf_new_schema_fda.png)

輸入方案的名稱和說明，然後選擇將啟用與資料庫連接的外部帳戶。 這允許訪問外部基礎中可用的表清單。 選擇包含要收集之資料的表格。

![](assets/wf_new_schema_select_table_fda.png)

Click **[!UICONTROL OK]** to confirm. Adobe Campaign會自動偵測選取表格的結構並產生邏輯架構。

>[!NOTE]
>
>Adobe Campaign不會產生連結。

按一 **[!UICONTROL Save]** 下以確認建立。

![](assets/wf_new_schema_generate_fda.png)

在映射表（標準或FDA映射）時，會自動建立索引。

## 定義資料映射 {#defining-data-mapping}

Adobe Campaign可讓您定義外部表格中資料的對應。

為此，在建立外部表的模式後，您需要建立新的傳送映射以將此表中的資料用作傳送目標。

若要這麼做，請套用下列步驟：

1. 建立新的傳送對應並選擇您剛建立的定位維度，例如。

   ![](assets/wf_new_mapping_create_fda.png)

1. 指出儲存傳送資訊的欄位（姓氏、名字、電子郵件、地址等）。

   ![](assets/wf_new_mapping_define_join.png)

1. 指定資訊儲存的參數，包括擴充功能架構的字尾，以方便辨識。

   ![](assets/wf_new_mapping_define_names.png)

   您可以選擇是將排除(排除&#x200B;**日誌**)、消息(**broadlog**)或單獨的表中儲存。

   您也可以選擇是否管理此傳送對應的追蹤(**trackinglog**)。

1. 然後，選擇要考慮的擴展。 擴充功能類型取決於您平台的參數和選項（檢視您的授權合約）。

   ![](assets/wf_new_mapping_define_extensions.png)

   按一下按 **[!UICONTROL Save]** 鈕以啟動傳送對應建立：所有連結的表都會基於所選參數自動建立。

## 其他選項 {#additional-options}

### HTTP中繼到遠程實例 {#http-relay-to-a-remote-instance}

您可以使用HTTP協定訪問遠程實例中配置的外部資料庫。

>[!NOTE]
>
>並非所有SQL資料類型都受此功能支援。 完全不支援Blob資料類型。 其他資料類型可能無法根據目標資料庫（例如Microsoft SQL server上的時間戳）工作。 如需詳細資訊，請聯絡Adobe支援。

如此可簡化兩個執行個體之間的資料傳輸與同步化。 它還使您能夠避免實例和遠程資料庫之間的任何隧道以及安裝客戶端層來訪問此資料庫。 目標實例可以是托管實例。

>[!CAUTION]
>
>此選項僅用於促進資料複製流(ETL)。
>
>例如，它可讓雲端裝載的執行個體直接存取「內部部署」裝載的資料庫中的資料。 但是，它不允許直接從雲端在「內部部署」代管資料庫上進行定位。

為此，您必須配置兩個實例的外部帳戶，以便本地實例可以使用HTTP協定與遠程實例通信：

* 本機例項：選擇新的連 **[!UICONTROL HTTP relay to a remote database]** 接類型。

   若是大量負載資料傳輸，也請指定緩衝區大小。 如果要減小傳輸資料的大小，請選擇壓縮選項。

   必 **[!UICONTROL Data source]** 須使用以下語法定義：&quot;nms:extAccount : `<internal_name_of_the_external_account>`&quot;

   ![](assets/fda_over_http_1.png)

   >[!NOTE]
   >
   >我們建議您使用HTTPS連線。

* 遠程實例：在FDA外部帳戶中，檢查透過HTTP中繼存取的資料庫目標 **[!UICONTROL 'HTTP relay to a remote database' account option]**。

   ![](assets/fda_over_http_2.png)

以下示例顯示了新的可能操作模式：

![](assets/schema_fda_over_http_2.png)

>[!CAUTION]
>
>遠程實例的預設資料庫也必須通過外部帳戶訪問。

此操作方法避免了每個實例的清理工作流刪除使用該實例作為中繼的資料庫的工作表。

因此，在上例中，遠程實例的清理工作流不會對紅色FDA資料庫執行任何操作，因為該資料庫由本地實例使用。

### 直接建立臨時結構 {#directly-creating-temporary-schemas}

如果您想要管理對FDA外部資料庫的數次存取，新選項可讓您在設定外部帳戶時直接建立使用中的架構。

>[!NOTE]
>
>此選項僅適用於PostgreSQL。

![](assets/fda_work_table.png)

### 使用外部資料最佳化電子郵件個人化 {#optimizing-email-personalization-with-external-data}

從build 8740開始，此選 **[!UICONTROL Prepare the personalization data with a workflow]** 項現在可在傳送屬 **[!UICONTROL Analysis]** 性的標籤中取用。

在傳送分析期間，此選項會自動建立並執行將所有連結至目標的資料儲存在暫存表格中的工作流程，包括FDA中連結之表格的資料。

勾選此選項，可大幅提升執行個人化的效能。

### 雲端訊息- FDA同步化 {#cloud-messaging---fda-synchronization}

當Cloud Messaging伺服器和Marketing伺服器長時間未同步時，Marketing伺服器上遺失的廣播量可能會相當大。 為了通過FDA優化廣播同步，已 **添加了NmsMidSourcing_LogsPeriodHour** 選項。 這允許指定最大時間段（以小時為單位），以限制每次執行同步工作流時恢復的廣播數。

此選項將添加到控制台中的節點 **[!UICONTROL Administration > Options]** 中。

>[!CAUTION]
>
>此選項僅 **能用** 於透過FDA同步大量廣播。

>[!NOTE]
>
>僅當存在上次恢復日期時(**** NmsMidSourcing_LastBroadLog_*選項)，才考慮該選項。

### 消息中心- XtkFolder表的讀取訪問 {#message-center---read-access-on-the-xtkfolder-table}

在構建8141和更高版本中，如果郵件中心使用FDA作為歸檔模式，則需要手動操作。

您必須將XtKFolder表格的讀取存取權授與與外部FDA帳戶連結的使用者。

例如，對於PostgreSQL資料庫，命令如下：

```
GRANT SELECT ON XtkFolder TO DBUSER;
```

此用戶必須具有對以下表的讀取訪問權限：

* NmsBroadLogRtEvent
* NmsBroadLogBatchEvent
* NmsTrackingLogRtEvent
* NmsTrackingLogBatchEvent
* NmsRtEvent
* NmsBatchEvent
* NmsBroadLogMsg
* NmsTrackingUrl
* NmsDelivery
* NmsWebTrackingLog

>[!NOTE]
此修改會刪除「關係xtkfolder的權限被拒絕」錯誤訊息。

如果在外部FDA帳戶中選擇的工作模式不是現成可用的Neolane帳戶，則無需對訪問權限進行此修改。

## 在工作流中使用來自外部資料庫的資料 {#using-data-from-an-external-database-in-a-workflow}

在數個Adobe Campaign工作流程活動中，您可以使用儲存在外部資料庫中的資料。

### 篩選外部資料 {#filtering-on-external-data}

查詢活動允許您添加外部資料，並在定義的篩選器配置中使用它。

For more on this, refer to the [Query](../../workflow/using/targeting-data.md#selecting-data) section.

### 建立子集 {#creating-sub-sets}

分割活動允許您建立子集。 您可以使用外部資料來定義要使用的篩選條件。

For more on this, refer to the [Split](../../workflow/using/split.md) section.

### 載入外部資料庫 {#loading-external-database}

可在資料載入(RDBMS)中使用外部資料。 此活動會顯示在「資料 [載入」區](../../workflow/using/data-loading--rdbms-.md) 。

### 新增資訊和連結 {#adding-information-and-links}

富集活動允許您將其他資料添加到工作流的工作表以及到外部表的連結。 因此，它可利用外部資料庫的資料。 此活動將顯示在「 [Enrichment](../../workflow/using/enrichment.md) 」（擴充）部分。
