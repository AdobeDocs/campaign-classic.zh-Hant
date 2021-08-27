---
product: campaign
title: 配置訪問Snowflake
description: 了解如何在FDA中設定Snowflake存取權
audience: platform
content-type: reference
topic-tags: connectors
exl-id: bdb5e422-ecfe-42eb-bd15-39fe5ec0ff1d
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 6%

---

# 配置訪問Snowflake {#configure-access-to-snowflake}

![](../../assets/v7-only.svg)

使用Campaign **同盟資料存取**(FDA)選項來處理儲存在外部資料庫中的資訊。 請依照以下步驟配置[!DNL Snowflake]的訪問。

1. 在[CentOS](#snowflake-centos)、[Windows](#snowflake-windows)或[Debian](#snowflake-debian)上配置[!DNL Snowflake]
1. 在Campaign中設定[!DNL Snowflake] [外部帳戶](#snowflake-external)


>[!NOTE]
>
>[!DNL Snowflake] 連接器適用於托管部署和內部部署。如需詳細資訊，請參閱[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## SnowflakeCentOS {#snowflake-centos}

要在CentOS上配置[!DNL Snowflake]，請執行以下步驟：

1. 下載[!DNL Snowflake]的ODBC驅動程式。 [按一](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 下這裡開始下載。
1. 然後，您需要使用以下命令在CentOs上安裝ODBC驅動程式：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 下載和安裝ODBC驅動程式後，需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 在Campaign中，您可以接著設定[!DNL Snowflake]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#snowflake-external)。

## SnowflakeWindows {#snowflake-windows}

1. 下載Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)的[ODBC驅動程式。 請注意，安裝驅動程式需要管理員級權限。 有關詳細資訊，請參閱[此頁面](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驅動程式。 有關詳細資訊，請參閱[此頁面](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 在Campaign中，您可以接著設定[!DNL Snowflake]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#snowflake-external)。

## SnowflakeDebian {#snowflake-debian}

1. 下載[!DNL Snowflake]的ODBC驅動程式。 [按一下](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 這裡開始下載。

1. 然後，您需要使用以下命令在Debian上安裝ODBC驅動程式：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 下載和安裝ODBC驅動程式後，需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在Campaign中，您可以接著設定[!DNL Snowflake]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[此部分](#snowflake-external)。

## Snowflake外部帳戶 {#snowflake-external}

您需要建立[!DNL Snowflake]外部帳戶，將您的Campaign執行個體連結至您的[!DNL Snowflake]外部資料庫。

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，按一下&#x200B;**[!UICONTROL Administration]**「>」 **[!UICONTROL Platform]**「>」 **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 配置&#x200B;**[!UICONTROL Snowflake]**&#x200B;外部帳戶，必須指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:伺服器的 [!DNL Snowflake] URL

   * **[!UICONTROL Account]**:使用者名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

   ![](assets/snowflake.png)

1. 按一下&#x200B;**[!UICONTROL Parameters]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Deploy functions]**&#x200B;按鈕以建立函式。

   ![](assets/snowflake_2.png)

連接器支援下列選項：

| 選項 | 說明 |
|---|---|
| 工作架構 | 用於工作表的資料庫架構 |
| 倉儲 | 要使用的預設倉庫的名稱。 它會覆寫使用者的預設值。 |
| 時區名稱 | 預設為空，這表示使用Campaign Classic應用程式伺服器的系統時區。 選項可用來強制TIMEZONE會話參數。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone). |
| WeekStart | WEEK_START會話參數。 預設為0。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start). |
| UseCachedResult | USE_CACHED_RESULTS會話參數。 預設為TRUE。 此選項可用於禁用Snowflake快取結果。 <br>[如需關於此項目的詳細資訊，請參閱此頁面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html). |
