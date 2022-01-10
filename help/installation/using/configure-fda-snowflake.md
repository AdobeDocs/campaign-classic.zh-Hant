---
product: campaign
title: 配置訪問Snowflake
description: 了解如何在FDA中設定Snowflake存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 6cecc81135afd067712e51ec9c1ad3239170702e
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 8%

---

# 配置訪問Snowflake {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

使用Campaign **同盟資料存取** (FDA)處理儲存於外部資料庫的資訊的選項。 請依照下列步驟，設定 [!DNL Snowflake].

1. 設定 [!DNL Snowflake] on [Linux](#snowflake-linux).
1. 設定 [!DNL Snowflake] [外部帳戶](#snowflake-external) 在Campaign

>[!NOTE]
>
>[!DNL Snowflake] 連接器適用於托管部署和內部部署。 如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeLinux {#snowflake-linux}

配置 [!DNL Snowflake] 在Linux上，請遵循下列步驟：

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

1. 在執行指令碼之前，您可以透過 `--help` 選項：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts/
   ./snowflake_odbc-setup.sh --help
   ```

1. 訪問指令碼所在的目錄，並以超級用戶身份運行以下指令碼：

   ```
   cd /usr/local/neolane/nl6/bin/fda-setup-scripts
   ./snowflake_odbc-setup.sh
   ```

1. 安裝ODBC驅動程式後，需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 然後，您可以在Campaign中設定 [!DNL Snowflake] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#snowflake-external).

## Snowflake外部帳戶 {#snowflake-external}

您需要建立 [!DNL Snowflake] 外部帳戶，將您的Campaign執行個體連線至您的 [!DNL Snowflake] 外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為外部帳戶 **[!UICONTROL Type]**.

1. 在 **[!UICONTROL Configuration]**，選取 [!DNL Snowflake] 從 **[!UICONTROL Type]** 下拉式清單。

   ![](assets/snowflake_5.png)

1. 新增 **[!UICONTROL Server]** URL和 **[!UICONTROL Database]**.

1. 設定 **[!UICONTROL Snowflake]** 外部帳戶驗證：

   * 對於帳戶/密碼驗證，必須指定：

      * **[!UICONTROL Account]**:使用者名稱

      * **[!UICONTROL Password]**:用戶帳戶密碼。

      ![](assets/snowflake.png)

   * 對於密鑰配對驗證，請按一下 **[!UICONTROL Keypair Auth]** 標籤來使用 **[!UICONTROL Private key]** 驗證並複製貼上 **[!UICONTROL Private key]**.

      ![](assets/snowflake_4.png)


1. 按一下 **[!UICONTROL Parameters]** ，然後 **[!UICONTROL Deploy functions]** 按鈕以建立函式。

   >[!NOTE]
   >
   >要使所有函式都可用，您需要在遠程資料庫中建立Adobe Campaign SQL函式。 如需詳細資訊，請參閱 [頁面](../../configuration/using/adding-additional-sql-functions.md).

   ![](assets/snowflake_2.png)

1. 按一下 **[!UICONTROL Save]** 完成設定時。

連接器支援下列選項：

| Option | 說明 |
|---|---|
| 工作架構 | 用於工作表的資料庫架構 |
| 倉儲 | 要使用的預設倉庫的名稱。 它會覆寫使用者的預設值。 |
| 時區名稱 | 預設為空，這表示使用Campaign Classic應用程式伺服器的系統時區。 選項可用來強制TIMEZONE會話參數。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | WEEK_START會話參數。 預設為0。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | USE_CACHED_RESULTS會話參數。 預設為TRUE。 此選項可用於禁用Snowflake快取結果。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
