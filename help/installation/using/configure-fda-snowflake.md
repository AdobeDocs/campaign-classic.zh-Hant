---
product: campaign
title: 配置對Snowflake的訪問
description: 瞭解如何配置FDA中對Snowflake的訪問
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 6%

---

# 配置對Snowflake的訪問 {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

使用市場活動 **聯合資料存取** (FDA)選項，用於處理儲存在外部資料庫中的資訊。 按照以下步驟配置訪問 [!DNL Snowflake]。

1. 配置 [!DNL Snowflake] 上 [Linux](#snowflake-linux)。
1. 配置 [!DNL Snowflake] [外部帳戶](#snowflake-external) 在活動中

>[!NOTE]
>
>[!DNL Snowflake] 連接器可用於托管部署和內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeLinux {#snowflake-linux}

配置 [!DNL Snowflake] 在Linux上，按照以下步驟操作：

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

1. 在運行指令碼之前，您可以使用 `--help` 選項：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. 訪問指令碼所在的目錄，並以root用戶身份運行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. 安裝ODBC驅動程式後，需要重新啟動Campaign Classic。 為此，請運行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在「市場活動」中，您可以配置 [!DNL Snowflake] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#snowflake-external)。

## Snowflake外部帳戶 {#snowflake-external}

您需要建立 [!DNL Snowflake] 將市場活動實例連接到您的外部帳戶 [!DNL Snowflake] 外部資料庫。

1. 從市場活動 **[!UICONTROL Explorer]**&#x200B;按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為您的外部帳戶 **[!UICONTROL Type]**。

1. 下 **[!UICONTROL Configuration]**&#x200B;選中 [!DNL Snowflake] 從 **[!UICONTROL Type]** 下拉。

   ![](assets/snowflake_5.png)

1. 添加 **[!UICONTROL Server]** URL和 **[!UICONTROL Database]**。

1. 配置 **[!UICONTROL Snowflake]** 外部帳戶身份驗證：

   * 對於帳戶/密碼驗證，必須指定：

      * **[!UICONTROL Account]**:用戶名

      * **[!UICONTROL Password]**:用戶帳戶密碼。

      ![](assets/snowflake.png)

   * 對於密鑰對驗證，請按一下 **[!UICONTROL Keypair Auth]** 頁籤 **[!UICONTROL Private key]** 驗證並複製貼上 **[!UICONTROL Private key]**。

      ![](assets/snowflake_4.png)


1. 按一下 **[!UICONTROL Parameters]** 按鈕 **[!UICONTROL Deploy functions]** 按鈕。

   >[!NOTE]
   >
   >要使所有函式都可用，您需要在遠程資料庫中建立Adobe CampaignSQL函式。 有關詳細資訊，請參閱 [頁](../../configuration/using/adding-additional-sql-functions.md)。

   ![](assets/snowflake_2.png)

1. 按一下 **[!UICONTROL Save]** 完成配置。

連接器支援以下選項：

| Option | 說明 |
|---|---|
| 工作架構 | 用於工作表的資料庫架構 |
| 倉庫 | 要使用的預設倉庫的名稱。 它將覆蓋用戶的預設值。 |
| 時區名稱 | 預設為空，這意味著使用Campaign Classic應用伺服器的系統時區。 該選項可用於強制TIMEZONE會話參數。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| 周開始 | WEEK_START會話參數。 預設設定為0。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | USE_CACHED_RESULTS會話參數。 預設設定為TRUE。 此選項可用於禁用Snowflake快取結果。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
| 批量線程 | 用於Snowflake批量載入器的線程數，越多的線程意味著對於較大的批量載入而言效能越好。 預設設定為1。 可根據電腦線程計數來調整數量。 |
| chunkSize | 確定批量載入器區塊的檔案大小。 預設設定為128MB。 當與bulkThreads一起使用時，可以修改以獲得更優的效能。 更多併發活動線程意味著更好的效能。 <br>有關此內容的詳細資訊，請參閱 [Snowflake文檔](https://docs.snowflake.net/manuals/sql-reference/sql/put.html)。 |
| 階段名稱 | 預設定的內部階段的名稱。 它將用於批量載入，而不是建立新的臨時階段。 |
