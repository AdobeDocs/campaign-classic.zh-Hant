---
product: campaign
title: 配置對GoogleBigQuery的訪問
description: 瞭解如何配置FDA中對GoogleBigQuery的訪問
audience: platform
content-type: reference
topic-tags: connectors
exl-id: ebaad59f-0607-4090-92d0-e457fbf9a348
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 2%

---

# 配置對GoogleBigQuery的訪問 {#configure-fda-google-big-query}

![](../../assets/v7-only.svg)

使用Adobe Campaign Classic **聯合資料存取** (FDA)選項，用於處理儲存在外部資料庫中的資訊。 按照以下步驟配置訪問 [!DNL Google BigQuery]。

1. 配置 [!DNL Google BigQuery] 上 [窗口](#google-windows) 或 [Linux](#google-linux)
1. 配置 [!DNL Google BigQuery] [外部帳戶](#google-external) 在Adobe Campaign Classic
1. 設定 [!DNL Google BigQuery] 連接器批量載入 [窗口](#bulk-load-windows) 或 [Linux](#bulk-load-linux)

>[!NOTE]
>
> [!DNL Google BigQuery] 連接器可用於托管、混合和內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## GoogleBigQuery在Windows上 {#google-windows}

### 在Windows上設定的驅動程式 {#driver-window}

1. 下載 [Windows的ODBC驅動程式](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers)。

1. 在Windows中配置ODBC驅動程式。 如需詳細資訊，請參閱[此頁面](https://storage.googleapis.com/simba-bq-release/jdbc/Simba%20JDBC%20Driver%20for%20Google%20BigQuery%20Install%20and%20Configuration%20Guide.pdf)。

1. 對於 [!DNL Google BigQuery] 連接器工作時，Adobe Campaign Classic需要以下參數來連接：

   * **[!UICONTROL Project]**:建立或使用現有項目。

      有關詳細資訊，請參閱 [頁](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Service account]**:建立服務帳戶。

      有關詳細資訊，請參閱 [頁](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Key File Path]**:這樣 **[!UICONTROL Service account]** 需要 **[!UICONTROL Key File]** 為 [!DNL Google BigQuery] 通過ODBC連接。

      有關詳細資訊，請參閱 [頁](https://cloud.google.com/iam/docs/creating-managing-service-account-keys)。

   * **[!UICONTROL Dataset]**: **[!UICONTROL Dataset]** 對於ODBC連接是可選的。 因為每個查詢都需要提供表所在的資料集，因此指定 **[!UICONTROL Dataset]** 對於 [!DNL Google BigQuery] FDA連接器在Adobe Campaign Classic。

      有關詳細資訊，請參閱 [頁](https://cloud.google.com/bigquery/docs/datasets)。

1. 在Adobe Campaign Classic，您可以配置 [!DNL Google BigQuery] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#google-external)。

### 在Windows上設定批量載入 {#bulk-load-window}

>[!NOTE]
>
>您需要安裝Python才能使Google雲SDK工作。
>
>我們建議使用Python3，請參閱 [頁](https://www.python.org/downloads/)。

批量載入實用程式允許更快的傳輸，這是通過Google雲SDK實現的。

1. 從此下載Windows 64位(x86_64)存檔檔案 [頁](https://cloud.google.com/sdk/docs/downloads-versioned-archives) 並提取到相應的目錄中。

1. 運行 `google-cloud-sdk\install.sh` 的下界。 您需要接受路徑變數的設定。

1. 安裝後，檢查路徑變數 `...\google-cloud-sdk\bin` 的子菜單。 否則，手動添加。

1. 在  `..\google-cloud-sdk\bin\bq.cmd` 檔案，添加 `CLOUDSDK_PYTHON` 本地變數，它將重定向到Python安裝的位置。

   例如：

   ![](assets/google-big-query_1.png)

1. 重新啟動Adobe Campaign Classic以便將更改考慮在內。

## GoogleLinux上的BigQuery {#google-linux}

### 在Linux上設定的驅動程式 {#driver-linux}

在設定驅動程式之前，請注意指令碼和命令必須由root用戶運行。 還建議在運行指令碼時使用GoogleDNS 8.8.8.8。

配置 [!DNL Google BigQuery] 在Linux上，按照以下步驟操作：

1. 在安裝ODBC之前，請檢查Linux分發上是否安裝了以下軟體包：

   * 對於Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y grep sed tar wget perl curl
      ```

   * 對於Debian:

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

   * 對於Debian:

      ```
      # install unixODBC driver manager
      apt-get install -y odbcinst1debian2 libodbc1 odbcinst unixodbc
      ```

1. 訪問指令碼所在的目錄並運行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_odbc-setup.sh
   ```

### 在Linux上設定批量載入 {#bulk-load-linux}

>[!NOTE]
>
>您需要安裝Python才能使Google雲SDK工作。
>
>我們建議使用Python3，請參閱 [頁](https://www.python.org/downloads/)。

批量載入實用程式允許更快的傳輸，這是通過Google雲SDK實現的。

1. 在安裝ODBC之前，請檢查Linux分發上是否安裝了以下軟體包：

   * 對於Red Hat/CentOS:

      ```
      yum update
      yum upgrade
      yum install -y python3
      ```

   * 對於Debian:

      ```
      apt-get update
      apt-get upgrade
      apt-get install -y python3
      ```

1. 訪問指令碼所在的目錄並運行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./bigquery_sdk-setup.sh
   ```

## Google大查詢外部帳戶 {#google-external}

您需要建立 [!DNL Google BigQuery] 外部帳戶，將Adobe Campaign Classic實例連接到 [!DNL Google BigQuery] 外部資料庫。

1. 寄自Adobe Campaign Classic **[!UICONTROL Explorer]**&#x200B;按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為您的外部帳戶 **[!UICONTROL Type]**。

1. 配置 [!DNL Google BigQuery] 外部帳戶，必須指定：

   * **[!UICONTROL Type]**: [!DNL Google BigQuery]

   * **[!UICONTROL Service account]**:您的電子郵件 **[!UICONTROL Service account]**。 有關此項的詳細資訊，請參閱 [Google雲文檔](https://cloud.google.com/iam/docs/creating-managing-service-accounts)。

   * **[!UICONTROL Project]**:您的名稱 **[!UICONTROL Project]**。 有關此項的詳細資訊，請參閱 [Google雲文檔](https://cloud.google.com/resource-manager/docs/creating-managing-projects)。

   * **[!UICONTROL Key file Path]**:
      * **[!UICONTROL Upload key file to the server]**:選擇 **[!UICONTROL Click here to upload]** 如果你選擇通過Adobe Campaign Classic上傳密鑰。

      * **[!UICONTROL Enter manually the key file path]**:如果您選擇使用預先存在的密鑰，請在此欄位中複製/貼上您的絕對路徑。
   * **[!UICONTROL Dataset]**:您的名稱 **[!UICONTROL Dataset]**。 有關此項的詳細資訊，請參閱 [Google雲文檔](https://cloud.google.com/bigquery/docs/datasets-intro)。

   ![](assets/google-big-query.png)

連接器支援以下選項：

| Option | 說明 |
|:-:|:-:|
| 代理類型 | 用於通過ODBC和SDK連接器連接到BigQuery的代理類型。 </br>當前支援HTTP（預設）、http_no_tunnel、socks4和socks5。 |
| 代理主機 | 可以訪問代理的主機名或IP地址。 |
| 代理埠 | 代理正在運行的埠號，例如8080 |
| 代理UID | 用於已驗證代理的用戶名 |
| 代理密碼 | ProxyUid密碼 |
| bqpath | 請注意，這僅適用於批量載入工具（雲SDK）。 </br> 為避免使用PATH變數，或者如果google-cloud-sdk目錄必須移動到其他位置，可以使用此選項指定伺服器上雲sdk bin目錄的確切路徑。 |
