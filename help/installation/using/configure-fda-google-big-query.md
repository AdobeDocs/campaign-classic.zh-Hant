---
solution: Campaign Classic
product: campaign
title: 設定Google BigQuery的存取權
description: 了解如何在FDA中設定Google BigQuery的存取權
audience: platform
content-type: reference
topic-tags: connectors
source-git-commit: 911302475b5ece96d527575148ee611fdb839753
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 2%

---


# 設定Google BigQuery {#configure-fda-google-big-query}的存取權

使用Adobe Campaign Classic **同盟資料存取**(FDA)選項來處理儲存在外部資料庫中的資訊。 請依照以下步驟配置[!DNL Google BigQuery]的訪問。

1. 在[Windows](#google-windows)或[Linux](#google-linux)上配置[!DNL Google BigQuery]
1. 在Adobe Campaign Classic中設定[!DNL Google BigQuery] [外部帳戶](#google-external)
1. 在[Windows](#bulk-load-windows)或[Linux](#bulk-load-linux)上設定[!DNL Google BigQuery]連接器大量負載

>[!NOTE]
>
> [!DNL Google BigQuery] 連接器適用於混合部署和內部部署。有關詳細資訊，請參見[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## Windows上的Google BigQuery {#google-windows}

### 在Windows {#driver-window}上設定的驅動程式

1. 下載Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)的[ODBC驅動程式。

1. 在Windows中配置ODBC驅動程式。 有關詳細資訊，請參見[此頁面](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)。

1. 為了讓[!DNL Google BigQuery]連接器正常運作，Adobe Campaign Classic需要下列參數才能連線：

   * **[!UICONTROL Project]**:建立或使用現有專案。

      如需詳細資訊，請參閱此[page](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Service account]**:建立服務帳戶。

      如需詳細資訊，請參閱此[page](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Key File Path]**:需 **[!UICONTROL Service account]** 要通過 **[!UICONTROL Key File]** ODBC連 [!DNL Google BigQuery] 接的。

      如需詳細資訊，請參閱此[page](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)。

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** 對於ODBC連接是可選的。由於每個查詢都必須提供表格所在的資料集，因此在Adobe Campaign Classic中，指定&#x200B;**[!UICONTROL Dataset]**&#x200B;是[!DNL Google BigQuery] FDA Connector的必要項目。

      如需詳細資訊，請參閱此[page](https://cloud.google.com/bigquery/docs/datasets)。

1. 在Adobe Campaign Classic中，您接著可以設定[!DNL Google BigQuery]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#google-external)。

### 在Windows {#bulk-load-window}上設定的批量載入

>[!NOTE]
>
>您需要安裝Python才能使Google Cloud SDK正常運作。
>
>建議使用Python3，請參見此[page](https://www.python.org/downloads/)。

大量載入公用程式可讓傳輸更快，這是透過Google Cloud SDK達成。

1. 從此[page](https://cloud.google.com/sdk/docs/downloads-versioned-archives)下載Windows 64位(x86_64)歸檔檔案，並將其解壓縮到相應目錄。

1. 運行`google-cloud-sdk\install.sh`指令碼。 您必須接受路徑變數的設定。

1. 安裝後，請檢查路徑變數`...\google-cloud-sdk\bin`是否已設定。 否則請手動新增。

1. 在`..\google-cloud-sdk\bin\bq.cmd`檔案中，添加`CLOUDSDK_PYTHON`本地變數，該變數將重定向到Python安裝的位置。

   例如：

   ![](assets/google-big-query_1.png)

1. 重新啟動Adobe Campaign Classic，以便考慮變更。

## Linux上的Google BigQuery {#google-linux}

### 在Linux {#driver-linux}上設定的驅動程式

1. 安裝ODBC驅動程式之前，需要更新系統。 在Linux或CentOS上，執行下列命令：

   ```
   yum update
   # install unixODBC driver manager
   yum install unixODBC
   ```

1. 然後，需要使用以下命令安裝unixODBC驅動程式管理器：

   ```
   # switch to root user
   sudo su
   ```

   在Debian上：

   ```
   apt-get update
   apt-get upgrade
   # install unixODBC driver manager
   apt-get install unixODBC
   ```

1. 下載[Magnitude Simba Linux ODBC驅動程式(.tar.gz)](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)。 然後，將目標檔案傳輸到電腦上的臨時資料夾，或使用wget命令：

   ```
   # in this example driver version is 2.3.1.1001
   wget https://storage.googleapis.com/simba-bq-release/odbc/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux.tar.gz
   ```

1. 按如下方式提取主目標檔案，其中&#x200B;**TarballName**&#x200B;是包含驅動程式的目標包的名稱：

   ```
   tar --directory=/tmp -zxvf [TarballName]
   ```

1. 訪問您提取的資料夾並提取與驅動程式版本對應的內部目標檔案。 在以下示例BigQueryDriver中，將其安裝到另一個臨時資料夾中：

   ```
   mkdir /tmp/BigQueryDriver/
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   tar --directory=/tmp/BigQueryDriver/ -zxvf SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version].tar.gz
   ```

1. 訪問提取主目標檔案的臨時位置，並將`GoogleBigQueryODBC.did`和`setup/simba.googlebigqueryodbc.ini`檔案複製到上一步驟中建立的新資料夾中：

   ```
   cd /tmp/SimbaODBCDriverforGoogleBigQuery_[Version]-Linux/
   cp GoogleBigQueryODBC.did /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   cp setup/simba.googlebigqueryodbc.ini /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/lib/
   ```

1. 建立安裝目錄，如下所示：

   ```
   mkdir -p /opt/simba/googlebigqueryodbc/
   ```

1. 將目錄的內容複製到新的安裝目錄中：

   ```
   cp -r /tmp/BigQueryDriver/SimbaODBCDriverforGoogleBigQuery[Bitness]_[Version]/* /opt/simba/googlebigqueryodbc/
   ```

1. 在安裝目錄的`simba.googlebigqueryodbc.ini`中將`<INSTALLDIR>`替換為`/opt/simba/googlebigqueryodbc`:

   ```
   cd /opt/simba/googlebigqueryodbc/lib/
   sed -i 's/<INSTALLDIR>/\/opt\/simba\/googlebigqueryodbc/g' simba.googlebigqueryodbc.ini
   ```

1. 將`DriverManagerEncoding`變更為`simba.googlebigqueryodbc.ini`中的UTF-16和`SwapFilePath`。 如有需要，您也可以變更記錄設定。

   以下是更新的驅動程式範圍配置檔案的示例：

   ```
   # /opt/simba/googlebigqueryodbc/lib/simba.googlebigqueryodbc.ini
   [Driver]
   DriverManagerEncoding=UTF-16
   ErrorMessagesPath=opt/simba/googlebigqueryodbc/ErrorMessages
   LogLevel=6
   LogPath=/tmp
   SwapFilePath=/tmp
   ```

1. 如果使用系統驅動程式檔案或任何當前`odbcinst.ini`檔案，請配置`/etc/odbcinst.ini`以指向Google BigQuery驅動程式位置`/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb[Bitness].so`。

   例如：

   ```
   # /etc/odbcinst.ini
   # Make sure to use Simba ODBC Driver for Google BigQuery as a driver name.
   
   [ODBC Drivers]
   Simba ODBC Driver for Google BigQuery=Installed
   
   [Simba ODBC Driver for Google BigQuery]
   Description=Simba ODBC Driver for Google BigQuery(64-bit)
   Driver=/opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   ```

1. 查找unixODBC驅動程式管理器庫的位置，並將`unixODBC`和`googlebigqueryodbc`庫路徑添加到`LD_LIBRARY_PATH environment`變數中。

   ```
   find / -name 'lib*odbc*.so*' -print
   #output:
   /usr/lib/x86_64-linux-gnu/libodbccr.so.2
   /usr/lib/x86_64-linux-gnu/libodbcinst.so.2.0.0
   /usr/lib/x86_64-linux-gnu/libodbccr.so.1
   .
   .
   /opt/simba/googlebigqueryodbc/lib/libgooglebigqueryodbc_sb64.so
   
   #the command would look like this
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/simba/googlebigqueryodbc:/usr/lib
   ```

1. 在Adobe Campaign Classic中，您接著可以設定[!DNL Google BigQuery]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#google-external)。

### 在Linux {#bulk-load-linux}上設定的批量載入

>[!NOTE]
>
>您需要安裝Python才能使Google Cloud SDK正常運作。
>
>建議使用Python3，請參見此[page](https://www.python.org/downloads/)。

大量載入公用程式可讓傳輸更快，這是透過Google Cloud SDK達成。

1. 下載此[page](https://cloud.google.com/sdk/docs/downloads-versioned-archives)中的Linux 64位(x86_64)歸檔檔案，並在相應目錄中提取。

1. 運行`google-cloud-sdk\install.sh`指令碼。 您必須接受路徑變數的設定。

1. 安裝後，請檢查路徑變數`...\google-cloud-sdk\bin`是否已設定。 否則請手動新增。

1. 如果您不想使用`PATH`變數，或想要將`google-cloud-sdk`目錄移至其他位置，請在配置&#x200B;**[!UICONTROL External account]**&#x200B;時使用`bqpath`選項值，指定系統上bin目錄的確切路徑。

1. 重新啟動Adobe Campaign Classic，以便考慮變更。

## Google BigQuery外部帳戶{#google-external}

您需要建立[!DNL Google BigQuery]外部帳戶，將您的Adobe Campaign Classic執行個體連接至[!DNL Google BigQuery]外部資料庫。

1. 在Adobe Campaign Classic **[!UICONTROL Explorer]**&#x200B;中，按一下「**[!UICONTROL Administration]** 」>「 **[!UICONTROL Platform]** 」>「 **[!UICONTROL External accounts]**」。

1. 按一下 **[!UICONTROL New]**。

1. 選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 配置[!DNL Google BigQuery]外部帳戶，必須指定：

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**:您的電子郵件 **[!UICONTROL Service account]**。如需詳細資訊，請參閱[Google雲端檔案](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Project]**:您的名 **[!UICONTROL Project]**&#x200B;稱。如需詳細資訊，請參閱[Google雲端檔案](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**:如果 **[!UICONTROL Click here to upload]** 您選擇透過Adobe Campaign Classic上傳金鑰，請選取「 」。

      * **[!UICONTROL Enter manually the key file path]**:如果您選擇使用預先存在的索引鍵，請在此欄位中複製/貼上絕對路徑。
   * **[!UICONTROL Dataset]**:您的名 **[!UICONTROL Dataset]**&#x200B;稱。如需詳細資訊，請參閱[Google雲端檔案](https://cloud.google.com/bigquery/docs/datasets-intro)。
   ![](assets/google-big-query.png)
