---
title: 舊式連接器
seo-title: 舊式連接器
description: 舊式連接器
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
source-git-commit: 70b143445b2e77128b9404e35d96b39694d55335
workflow-type: tm+mt
source-wordcount: '1233'
ht-degree: 0%

---


# 舊式連接器 {#legacy-connectors}

Adobe仍支援舊版FDA連接器。 不過，我們建議以本頁所列的更新替代項目來取代 [它們](../../platform/using/specific-configuration-database.md)。

## 配置對Hadoop 2.1的訪問 {#configure-access-to-hadoop}

### 適用於Windows {#for-windows}

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

1. 建立Hadoop外部帳戶，如本頁 [部分所述](../../platform/using/external-accounts.md#hadoop-external-account) 。

### Linux版 {#for-linux}

1. 安裝unixodbc for Linux。

   ```
   apt-get install unixodbc
   ```

1. 從HortonWorks下載並安裝Apache Hive的ODBC驅動程式： [https://www.hortonworks.com/downloads/](https://www.hortonworks.com/downloads/).

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

   驗證設定取決於Hive/Hadoop配置。 例如，對於HD Insight，請使用AuthMech=6進行使用者／密碼驗證，如 [此說](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)。

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

1. 建立Hadoop外部帳戶，如本頁 [部分所述](../../platform/using/external-accounts.md#hadoop-external-account) 。

## 配置對Netezza的訪問 {#configure-access-to-netezza}

在FDA中連線至Netezza外部資料庫需要Adobe Campaign伺服器下的其他設定：

1. 根據您使用的作業系統，安裝Netezza的ODBC驅動程式：

   * **nz-linuxclient-v7.2.0.0.tar.gz** for Linux。 選擇與作業系統（linux或linux64）對應的資料夾，然後啟動unpack命令。 您可以保留在預設建議的儲存庫中執行的安裝：&quot;/usr/local/nz&quot;。
   * **nz-winclient-v7.2.0.0.zip** for Windows。 解壓縮檔案並啟動與您的作業系統對應的可執行指令碼：nzodbcsetup.exe或nzodbcsetup64.exe。 按照嚮導說明完成驅動程式的安裝。

1. 配置ODBC驅動程式。 配置可在標準檔案中執行： **/etc/odbc.ini** ，用於一般參數， **/etc/odbcinst.ini** ，用於聲明驅動程式。

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

1. 在Campaign Classic中，您接著可以設定Netezza外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

1. 若要設定外 **[!UICONTROL Netezza]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:內泰扎

   * **[!UICONTROL Server]**:Netezza伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

>[!NOTE]
>
>不考慮對包含自動生成的主鍵的方案的操作。
>
>表將在模式中定義的第 **一個索引上使用** Organize on子句。 由於此子句限制為1到4個Netezza列，因此此索引不能包含4個以上的列。

## 配置對Sybase IQ的訪問 {#configure-access-to-sybase-iq}

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

1. 在Campaign Classic中，您可以配置Sybase IQ外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

1. 若要設定外 **[!UICONTROL Sybase IQ]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:ODBC(Sybase ASE、Sybase IQ)

   * **[!UICONTROL Server]**:與步驟5中定義的ODBC`<server_alias>`連接()相對應。 不一定是伺服器本身的名稱。

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

>[!NOTE]
>
>對於Windows，必須在Adobe Campaign伺服器上安裝Sybase IQ客戶端並建立ODBC連接。 請確定您在Windows中以服務的形式執行Adobe Campaign伺服器(nlserver)時建立系統資料來源。

## 配置對Teradata的訪問 {#configure-access-to-teradata}

在FDA中連線至Teradata外部資料庫需要Adobe Campaign伺服器上的某些額外設定。 有關如何配置Teradata資料庫的詳細資訊，請參閱本 [頁](../../platform/using/appendices-fda.md#teradata-configuration)。

1. 安裝Teradata [的ODBC驅動程式](https://downloads.teradata.com/download/connectivity/odbc-driver/linux)。

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

1. 在Campaign Classic中，您接著可以設定您的Teradata外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

1. 若要設定外 **[!UICONTROL Teradata]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:Teradata

   * **[!UICONTROL Server]**:Teradata伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

## 配置對SAP HANA的訪問 {#configure-access-to-sap-hana}

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

   * **LD_LIBRARY_PATH**:依預設，應包含SAP Hana用戶端(/usr/sap/hdbclient/libodbcHDB.so)的連結。
   * **ODBCINI**:odbc.ini檔案的位置(例如/etc/odbc.ini)。

1. 在Campaign Classic中，您可以設定SAP Hana外部帳戶。 From the **[!UICONTROL Explorer]**, click **[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**.

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL External database]** 擇為 **[!UICONTROL Type]**。

1. 若要設定外 **[!UICONTROL SAP Hana]** 部帳戶，您必須指定：

   * **[!UICONTROL Type]**:SAP Hana

   * **[!UICONTROL Server]**:SAP Hana伺服器的URL

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼
