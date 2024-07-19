---
product: campaign
title: 設定Google BigQuery的存取權
description: 瞭解如何在FDA中設定Google BigQuery的存取權
feature: Installation, Federated Data Access
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '960'
ht-degree: 2%

---

# 設定Google BigQuery的存取權 {#configure-fda-google-big-query}



使用Adobe Campaign Classic **同盟資料存取** (FDA)選項來處理儲存在外部資料庫中的資訊。 請依照下列步驟設定[!DNL Google BigQuery]的存取權。

1. 在[Windows](#google-windows)或[Linux](#google-linux)上設定[!DNL Google BigQuery]
1. 在Adobe Campaign Classic中設定[!DNL Google BigQuery] [外部帳戶](#google-external)
1. 在[Windows](#bulk-load-windows)或[Linux](#bulk-load-linux)上設定[!DNL Google BigQuery]聯結器大量載入

>[!NOTE]
>
> [!DNL Google BigQuery]聯結器可用於託管、混合及內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## Windows上的Google BigQuery {#google-windows}

### 在Windows上設定的驅動程式 {#driver-window}

1. 下載適用於Windows](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)的[ODBC驅動程式。

1. 在Windows中設定ODBC驅動程式。 如需詳細資訊，請參閱[此頁面](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)。

1. 為了讓[!DNL Google BigQuery]聯結器運作，Adobe Campaign Classic需要下列引數才能連線：

   * **[!UICONTROL Project]**：建立或使用現有的專案。

     如需詳細資訊，請參閱此[頁面](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Service account]**：建立服務帳戶。

     如需詳細資訊，請參閱此[頁面](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Key File Path]**： **[!UICONTROL Service account]**&#x200B;需要&#x200B;**[!UICONTROL Key File]**&#x200B;才能透過ODBC進行[!DNL Google BigQuery]連線。

     如需詳細資訊，請參閱此[頁面](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)。

   * **[!UICONTROL Dataset]**： **[!UICONTROL Dataset]**&#x200B;是ODBC連線的選用專案。 由於每個查詢都需要提供資料表所在的資料集，因此在Adobe Campaign Classic中必須指定[!DNL Google BigQuery] FDA聯結器的&#x200B;**[!UICONTROL Dataset]**。

     如需詳細資訊，請參閱此[頁面](https://cloud.google.com/bigquery/docs/datasets)。

1. 然後，您可以在Adobe Campaign Classic中設定[!DNL Google BigQuery]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#google-external)。

### 在Windows上設定大量載入 {#bulk-load-window}

>[!NOTE]
>
>您必須安裝Python，Google Cloud SDK才能運作。
>
>我們建議使用Python3，請參閱此[頁面](https://www.python.org/downloads/)。

大量載入公用程式可讓您透過Google Cloud SDK更快地進行傳輸。

1. 從此[頁面](https://cloud.google.com/sdk/docs/downloads-versioned-archives)下載Windows 64位元(x86_64)封存，並將它解壓縮到對應的目錄中。

1. 執行`google-cloud-sdk\install.sh`指令碼。 您需要接受路徑變數的設定。

1. 安裝之後，檢查路徑變數`...\google-cloud-sdk\bin`是否已設定。 如果沒有，請手動新增。

1. 在`..\google-cloud-sdk\bin\bq.cmd`檔案中新增`CLOUDSDK_PYTHON`本機變數，這會重新導向至Python安裝的位置。

   例如：

   ![](assets/google-big-query_1.png)

1. 重新啟動Adobe Campaign Classic以納入變更。

## Linux上的Google BigQuery {#google-linux}

### 在Linux上設定的驅動程式 {#driver-linux}

設定驅動程式之前，請注意，指令碼和命令必須由root使用者執行。 此外也建議在執行指令碼時使用Google DNS 8.8.8.8。

若要在Linux上設定[!DNL Google BigQuery]，請遵循下列步驟：

1. 在ODBC安裝之前，請檢查您的Linux發行版本上是否已安裝下列套裝軟體：

   * 若為Red Hat/CentOS：

     ```
     yum update
     yum upgrade
     yum install -y grep sed tar wget perl curl
     ```

   * 對於Debian：

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y grep sed tar wget perl curl
     ```

1. 安裝前更新系統：

   * 若為Red Hat/CentOS：

     ```
     # install unixODBC driver manager
     yum install -y unixODBC
     ```

   * 對於Debian：

     ```
     # install unixODBC driver manager
     apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
     ```

1. 在執行指令碼之前，您可以指定 — help引數來取得更多資訊：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. 存取指令碼所在的目錄，並以root使用者的身分執行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### 在Linux上設定大量負載 {#bulk-load-linux}

>[!NOTE]
>
>您必須安裝Python，Google Cloud SDK才能運作。
>
>我們建議使用Python3，請參閱此[頁面](https://www.python.org/downloads/)。

大量載入公用程式可讓您透過Google Cloud SDK更快地進行傳輸。

1. 在ODBC安裝之前，請檢查您的Linux發行版本上是否已安裝下列套裝軟體：

   * 若為Red Hat/CentOS：

     ```
     yum update
     yum upgrade
     yum install -y python3
     ```

   * 對於Debian：

     ```
     apt-get update
     apt-get upgrade
     apt-get install -y python3
     ```

1. 存取指令碼所在的目錄，然後執行下列指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Google BigQuery外部帳戶 {#google-external}

您必須建立[!DNL Google BigQuery]外部帳戶，才能將Adobe Campaign Classic執行個體連線至[!DNL Google BigQuery]外部資料庫。

1. 從Adobe Campaign Classic **[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 設定[!DNL Google BigQuery]外部帳戶，您必須指定：

   * **[!UICONTROL Type]**： [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**：您&#x200B;**[!UICONTROL Service account]**&#x200B;的電子郵件。 如需詳細資訊，請參閱[Google Cloud檔案](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Project]**：您的&#x200B;**[!UICONTROL Project]**&#x200B;名稱。 如需詳細資訊，請參閱[Google Cloud檔案](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Key file Path]**：
      * **[!UICONTROL Upload key file to the server]**：如果您選擇透過Adobe Campaign Classic上傳金鑰，請選取&#x200B;**[!UICONTROL Click here to upload]**。

      * **[!UICONTROL Enter manually the key file path]**：如果您選擇使用預先存在的金鑰，請在此欄位中複製/貼上您的絕對路徑。

   * **[!UICONTROL Dataset]**：您的&#x200B;**[!UICONTROL Dataset]**&#x200B;名稱。 如需詳細資訊，請參閱[Google Cloud檔案](https://cloud.google.com/bigquery/docs/datasets-intro)。

   ![](assets/google-big-query.png)

聯結器支援下列選項：

| 選項 | 說明 |
|:-:|:-:|
| ProxyType | 用來透過ODBC和SDK聯結器連線至BigQuery的Proxy型別。 目前支援</br>HTTP （預設）、http_no_tunnel、socks4和socks5。 |
| ProxyHost | 可連線到Proxy的主機名稱或IP位址。 |
| ProxyPort | 執行Proxy的連線埠號碼，例如8080 |
| ProxyUid | 用於已驗證Proxy的使用者名稱 |
| proxypwd | ProxyUid密碼 |
| bqpath | 請注意，這僅適用於大量載入工具(Cloud SDK)。 </br>若要避免使用PATH變數或必須將google-cloud-sdk目錄移至其他位置，您可以使用此選項指定伺服器上cloud sdk bin目錄的精確路徑。 |
| GCloudConfigName | 請注意，這適用於7.3.4版開始並僅適用於大量載入工具(Cloud SDK)。</br> Google Cloud SDK使用設定將資料載入BigQuery表格。 名為`accfda`的組態儲存用來載入資料的引數。 不過，此選項可讓使用者為組態指定不同的名稱。 |
| GCloudDefaultConfigName | 請注意，這適用於7.3.4版開始並僅適用於大量載入工具(Cloud SDK)。</br>必須先將作用中的標籤傳輸至新的設定，才能刪除作用中的Google Cloud SDK設定。 此暫時設定是重新建立載入資料的主要設定所必需的。 暫存組態的預設名稱為`default`，如有需要，可以變更此名稱。 |
| GCloudRecreateConfig | 請注意，這適用於7.3.4版開始並僅適用於大量載入工具(Cloud SDK)。</br>設為`false`時，大量載入機制不會嘗試重新建立、刪除或修改Google Cloud SDK設定。 相反地，它會使用電腦上現有的設定繼續進行資料載入。 當其他作業取決於Google Cloud SDK設定時，此功能很有價值。 </br>如果使用者在沒有適當組態的情況下啟用此引擎選項，大量載入機制將會發出警告訊息： `No active configuration found. Please either create it manually or remove the GCloudRecreateConfig option`。 為避免進一步的錯誤，它會恢復為使用預設的ODBC陣列插入大量載入機制。 |

