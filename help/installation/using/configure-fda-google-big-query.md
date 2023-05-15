---
product: campaign
title: 設定Google BigQuery的存取權
description: 了解如何在FDA中設定Google BigQuery的存取權
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 2%

---

# 設定Google BigQuery的存取權 {#configure-fda-google-big-query}



使用Adobe Campaign Classic **同盟資料存取** (FDA)處理儲存於外部資料庫的資訊的選項。 請依照下列步驟，設定 [!DNL Google BigQuery].

1. 設定 [!DNL Google BigQuery] on [Windows](#google-windows) 或 [Linux](#google-linux)
1. 設定 [!DNL Google BigQuery] [外部帳戶](#google-external) 在Adobe Campaign Classic
1. 設定 [!DNL Google BigQuery] 連接器大量載入 [Windows](#bulk-load-windows) 或 [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] 連接器適用於托管、混合式和內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## Google BigQuery on Windows {#google-windows}

### 在Windows上設定的驅動程式 {#driver-window}

1. 下載 [Windows的ODBC驅動程式](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

1. 在Windows中配置ODBC驅動程式。 如需詳細資訊，請參閱[此頁面](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)。

1. 若 [!DNL Google BigQuery] 連接器運作時，Adobe Campaign Classic需要下列參數才能連線：

   * **[!UICONTROL Project]**:建立或使用現有專案。

      如需詳細資訊，請參閱 [頁面](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Service account]**:建立服務帳戶。

      如需詳細資訊，請參閱 [頁面](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Key File Path]**:the **[!UICONTROL Service account]** 要求a **[!UICONTROL Key File]** a [!DNL Google BigQuery] 通過ODBC連接。

      如需詳細資訊，請參閱 [頁面](https://cloud.google.com/iam/docs/creating-managing-service-account-keys).

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** 對於ODBC連接是可選的。 因為每個查詢都必須提供表格所在的資料集，並指定 **[!UICONTROL Dataset]** 強制 [!DNL Google BigQuery] Adobe Campaign Classic的FDA連接器。

      如需詳細資訊，請參閱 [頁面](https://cloud.google.com/bigquery/docs/datasets).

1. 在Adobe Campaign Classic中，您可以設定 [!DNL Google BigQuery] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#google-external).

### 在Windows上設定大量載入 {#bulk-load-window}

>[!NOTE]
>
>您需要安裝Python才能使Google Cloud SDK正常運作。
>
>我們建議使用Python3，請參閱 [頁面](https://www.python.org/downloads/).

大量載入公用程式可讓傳輸更快，這是透過Google Cloud SDK所達成。

1. 從此下載Windows 64位(x86_64)歸檔檔案 [頁面](https://cloud.google.com/sdk/docs/downloads-versioned-archives) 並提取到相應目錄中。

1. 執行 `google-cloud-sdk\install.sh` 指令碼。 您必須接受路徑變數的設定。

1. 安裝後，檢查路徑變數 `...\google-cloud-sdk\bin` 已設定。 否則請手動新增。

1. 在  `..\google-cloud-sdk\bin\bq.cmd` 檔案，新增 `CLOUDSDK_PYTHON` 本地變數，此變數將重定向到Python安裝的位置。

   例如：

   ![](assets/google-big-query_1.png)

1. 重新啟動Adobe Campaign Classic，以便考慮變更。

## Google BigQuery on Linux {#google-linux}

### 在Linux上設定的驅動程式 {#driver-linux}

在設定驅動程式之前，請注意指令碼和命令必須由根用戶運行。 執行指令碼時，也建議使用Google DNS 8.8.8.8。

配置 [!DNL Google BigQuery] 在Linux上，請遵循下列步驟：

1. 在ODBC安裝之前，請檢查Linux分發上是否安裝了以下軟體包：

   * 對於Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y grep sed tar wget perl curl
      ```

1. 安裝前更新系統：

   * 對於Red Hat/CentOS:

      ```
      # install unixODBC driver manager
      yum install -y unixODBC
      ```

   * Debian:

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. 在運行指令碼之前，可以通過指定 — help參數來獲取更多資訊：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh --help
   ```

1. 訪問指令碼所在的目錄，並以超級用戶身份運行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### 在Linux上設定的大量載入 {#bulk-load-linux}

>[!NOTE]
>
>您需要安裝Python才能使Google Cloud SDK正常運作。
>
>我們建議使用Python3，請參閱 [頁面](https://www.python.org/downloads/).

大量載入公用程式可讓傳輸更快，這是透過Google Cloud SDK所達成。

1. 在ODBC安裝之前，請檢查Linux分發上是否安裝了以下軟體包：

   * 對於Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. 訪問指令碼所在的目錄，並運行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Google BigQuery外部帳戶 {#google-external}

您需要建立 [!DNL Google BigQuery] 將Adobe Campaign Classic執行個體連結至 [!DNL Google BigQuery] 外部資料庫。

1. 從Adobe Campaign Classic **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為外部帳戶 **[!UICONTROL Type]**.

1. 設定 [!DNL Google BigQuery] 外部帳戶，您必須指定：

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**:您的 **[!UICONTROL Service account]**. 如需詳細資訊，請參閱 [Google Cloud檔案](https://cloud.google.com/iam/docs/creating-managing-service-accounts).

   * **[!UICONTROL Project]**:您的 **[!UICONTROL Project]**. 如需詳細資訊，請參閱 [Google Cloud檔案](https://cloud.google.com/resource-manager/docs/creating-managing-projects).

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**:選取 **[!UICONTROL Click here to upload]** 如果您選擇透過Adobe Campaign Classic上傳金鑰。

      * **[!UICONTROL Enter manually the key file path]**:如果您選擇使用預先存在的索引鍵，請在此欄位中複製/貼上絕對路徑。
   * **[!UICONTROL Dataset]**:您的 **[!UICONTROL Dataset]**. 如需詳細資訊，請參閱 [Google Cloud檔案](https://cloud.google.com/bigquery/docs/datasets-intro).

   ![](assets/google-big-query.png)

連接器支援下列選項：

| Option | 說明 |
|:-:|:-:|
| ProxyType | 用來透過ODBC和SDK連接器連線至BigQuery的代理類型。 </br>目前支援HTTP（預設值）、http_no_tunnel、socks4和socks5。 |
| ProxyHost | 可到達代理的主機名或IP地址。 |
| 代理埠 | 代理運行的埠號，例如8080 |
| ProxyUid | 用於已驗證代理的用戶名 |
| ProxyPwd | ProxyUid密碼 |
| bqpath | 請注意，這僅適用於大量載入工具(Cloud SDK)。 </br> 為避免使用PATH變數，或如果google-cloud-sdk目錄必須移至其他位置，您可以透過此選項指定伺服器上雲端sdk bin目錄的確切路徑。 |
