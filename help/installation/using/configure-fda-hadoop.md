---
product: campaign
title: 設定Hadoop的存取權
description: 瞭解如何在FDA中設定Hadoop存取權
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: e3a97e55-dd8b-41e1-b48c-816d973f62a8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 1%

---

# 設定Hadoop的存取權 {#configure-access-to-hadoop}



使用Campaign **同盟資料存取** (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟設定對Hadoop的存取權。

1. 設定[Hadoop資料庫](#configuring-hadoop)
1. 在Campaign中設定Hadoop[外部帳戶](#hadoop-external)

## 設定Hadoop 3.0 {#configuring-hadoop}

在Adobe Campaign伺服器上連線至FDA中的Hadoop外部資料庫需要下列設定。 請注意，此設定適用於Windows和Linux。

1. 根據您的作業系統版本，下載ODBC驅動程式以進行Hadoop。 驅動程式可在[此頁面](https://www.cloudera.com/downloads.html)上找到。

1. 然後，您需要安裝ODBC驅動程式，並為您的Hive連線建立DSN。 您可以在[此頁面](https://docs.cloudera.com/documentation/other/connectors/hive-odbc/2-6-5/Cloudera-ODBC-Driver-for-Apache-Hive-Install-Guide.pdf)中找到指示

1. 下載和安裝ODBC驅動程式之後，您需要重新啟動Campaign Classic。 要執行此操作，請執行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 然後，您可以在Campaign Classic中設定[!DNL Hadoop]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#hadoop-external)。

## hadoop外部帳戶 {#hadoop-external}

[!DNL Hadoop]外部帳戶可讓您將Campaign執行個體連線至Hadoop外部資料庫。

1. 在Campaign Classic中，設定您的[!DNL Hadoop]外部帳戶。 從&#x200B;**[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** / **[!UICONTROL Platform]** / **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 設定&#x200B;**[!UICONTROL Hadoop]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**： ODBC (Sybase ASE，Sybase IQ)

   * **[!UICONTROL Server]**： DNS的名稱

   * **[!UICONTROL Account]**：使用者名稱

   * **[!UICONTROL Password]**：使用者帳戶密碼

   * **[!UICONTROL Database]**：未在DSN中指定資料庫的名稱。 若在DSN中指定，可保留空白

   * **[!UICONTROL Time zone]**：伺服器時區

   ![](assets/hadoop3.png)

聯結器支援下列ODBC選項：

| 名稱 | 值 |
|---|---|
| ODBCMgr | iODBC |
| 倉儲 | 1/2/4 |

聯結器也支援下列Hive選項：

| 名稱 | 值 | 說明 |
|---|---|---|
| bulkKey | Azure Blob或DataLake存取金鑰 | 對於wasb://或wasbs://大量載入器(亦即，如果大量載入工具以wasb://或wasbs://開頭)。 <br>它是大量載入之Blob或DataLake貯體的存取金鑰。 |
| hdfsPort | 連線埠號碼<br>預設為8020 | 對於HDFS大量載入(亦即，如果大量載入工具以webhdfs://或webhdfss://開頭)。 |
| bucketnumber | 20 | 建立叢集表格時的值區數。 |
| 檔案格式 | PARQUET | 工作表的預設檔案格式。 |


## 設定Hadoop 2.1 {#configure-access-hadoop-2}

如果您需要連線到Hadoop2.1，請遵循下列針對[Windows](#for-windows)或[Linux](#for-linux)的步驟。

### WindowsHadoop2.1 {#for-windows}

1. 安裝適用於Windows的ODBC和[Azure HD Insight](https://www.microsoft.com/en-us/download/details.aspx?id=40886)驅動程式。
1. 執行[ODBC資料來源管理員]工具來建立DSN (資料Source名稱)。 提供用於Hive的系統DSN範例供您修改。

   ```
   Description: vorac (or any name you like)
   Host: vorac.azurehdinsight.net
   Port: 443
   Database: sm_tst611 (or your database name)
   Mechanism: Azure HDInsight Service
   User/Password: admin/<your password here>
   ```

1. 建立Hadoop外部帳戶，如[此區段](#hadoop-external)中所詳述。

### 適用於Linux的Hadoop2.1 {#for-linux}

1. 安裝適用於Linux的unixodbc。

   ```
   apt-get install unixodbc
   ```

1. 從HortonWorks下載並安裝適用於Apache Hive的ODBC驅動程式： [https://www.cloudera.com/downloads.html](https://www.cloudera.com/downloads.html)。

   ```
   dpkg -i hive-odbc-native_2.1.10.1014-2_amd64.deb
   ```

1. 檢查ODBC檔案的位置。

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

1. 建立DSN (資料Source名稱)並編輯odbc.ini檔案。 然後，為您的Hive連線建立DSN。

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
   >此處的&#x200B;**UseNativeQuery**&#x200B;引數非常重要。 Campaign具有Hive感知功能，除非設定UseNativeQuery，否則將無法正常運作。 通常，驅動程式或Hive SQL聯結器會重寫查詢並篡改欄順序。

   驗證設定取決於Hive/Hadoop設定。 例如，對於HD Insight，請使用AuthMech=6進行使用者/密碼驗證，如[此處](https://www.simba.com/products/Spark/doc/ODBC_InstallGuide/unix/content/odbc/hi/configuring/authenticating/azuresvc.htm)所述。

1. 匯出變數。

   ```
   export ODBCINI=/etc/myodbc.ini
   export ODBCSYSINI=/etc/myodbcinst.ini
   ```

1. 透過/usr/lib/hive/lib/native/Linux-amd64-64/hortonworks.hiveodbc.ini設定Hortonworks驅動程式。

   您必須使用UTF-16才能與Campaign和unix-odbc (libodbcinst)連線。

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

1. 建立Hadoop外部帳戶，如[此區段](#hadoop-external)中所詳述。
