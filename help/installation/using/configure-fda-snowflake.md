---
solution: Campaign Classic
product: campaign
title: 配置對雪花的訪問
description: 瞭解如何設定FDA的雪花存取權
audience: platform
content-type: reference
topic-tags: connectors
translation-type: tm+mt
source-git-commit: 535339b5a9b39625100d630b0b831df143dbeb01
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 6%

---


# 配置對雪花的訪問{#configure-access-to-snowflake}

使用Campaign **Federated Data Access**(FDA)選項來處理儲存在外部資料庫中的資訊。 請遵循下列步驟來設定對[!DNL Snowflake]的存取。

1. 在[CentOS](#snowflake-centos)、[Windows](#snowflake-windows)或[Debian](#snowflake-debian)上配置[!DNL Snowflake]
1. 在促銷活動中設定[!DNL Snowflake] [外部帳戶](#snowflake-external)


>[!NOTE]
>
>[!DNL Snowflake] connector適用於代管和內部部署。有關詳細資訊，請參見[此頁面](../../installation/using/capability-matrix.md)。

![](assets/snowflake_3.png)

## CentOS上的雪花{#snowflake-centos}

要在CentOS上配置[!DNL Snowflake]，請執行以下步驟：

1. 下載[!DNL Snowflake]的ODBC驅動程式。 [按一](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/snowflake-odbc-2.20.2.x86_64.rpm) 下此處開始下載。
1. 然後，您需要使用以下命令在CentOs上安裝ODBC驅動程式：

   ```
   rpm -Uvh unixodbc
   rpm -Uvh snowflake-odbc-2.20.2.x86_64.rpm
   ```

1. 在下載並安裝ODBC驅動程式後，您需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   /etc/init.d/nlserver6 stop
   /etc/init.d/nlserver6 start
   ```

1. 在促銷活動中，您可以接著設定您的[!DNL Snowflake]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[本節](#snowflake-external)。

## Windows上的雪花{#snowflake-windows}

1. 下載用於Windows](https://docs.snowflake.net/manuals/user-guide/odbc-download.html)的[ODBC驅動程式。 請注意，您需要管理員級權限才能安裝驅動程式。 如需詳細資訊，請參閱[本頁](https://docs.snowflake.net/manuals/user-guide/admin-user-management.html)

1. 配置ODBC驅動程式。 如需詳細資訊，請參閱[本頁](https://docs.snowflake.net/manuals/user-guide/odbc-windows.html#step-2-configure-the-odbc-driver)

1. 在促銷活動中，您可以接著設定您的[!DNL Snowflake]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[本節](#snowflake-external)。

## 德比亞河畔雪花{#snowflake-debian}

1. 下載[!DNL Snowflake]的ODBC驅動程式。 [按一下](https://sfc-repo.snowflakecomputing.com/odbc/linux/latest/index.html) 此處開始下載。

1. 然後，您需要使用以下命令在Debian上安裝ODBC驅動程式：

   ```
   apt-get install unixodbc
   apt-get install snowflake-odbc-x.xx.x.x86_64.deb
   ```

1. 在下載並安裝ODBC驅動程式後，您需要重新啟動Campaign Classic。 要執行此操作，請運行以下命令：

   ```
   systemctl stop nlserver.service
   systemctl start nlserver.service
   ```

1. 在促銷活動中，您可以接著設定您的[!DNL Snowflake]外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱[本節](#snowflake-external)。

## 雪花外部帳戶{#snowflake-external}

您需要建立[!DNL Snowflake]外部帳戶，將您的Campaign例項連接至您的[!DNL Snowflake]外部資料庫。

1. 在促銷活動&#x200B;**[!UICONTROL Explorer]**&#x200B;中，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;> &#39;> &#39; **[!UICONTROL External accounts]**。

1. 按一下 **[!UICONTROL New]**。

1. 選擇&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 設定&#x200B;**[!UICONTROL Snowflake]**&#x200B;外部帳戶，您必須指定：

   * **[!UICONTROL Type]**: [!DNL Snowflake]

   * **[!UICONTROL Server]**:伺服器的URL [!DNL Snowflake] 。

   * **[!UICONTROL Account]**:用戶名稱

   * **[!UICONTROL Password]**:使用者帳戶密碼

   * **[!UICONTROL Database]**:資料庫的名稱

   ![](assets/snowflake.png)

1. 按一下&#x200B;**[!UICONTROL Parameters]**&#x200B;頁籤，然後按一下&#x200B;**[!UICONTROL Deploy functions]**&#x200B;按鈕以建立函式。

   ![](assets/snowflake_2.png)

連接器支援以下選項：

| 選項 | 說明 |
|---|---|
| 工作架構 | 用於工作表的資料庫模式 |
| 倉庫 | 要使用的預設倉庫名稱。 它會覆寫使用者的預設值。 |
| 時區名稱 | 預設為空，這表示使用Campaign Classic應用程式伺服器的系統時區。 此選項可用於強制TIMEZONE會話參數。 <br>有關詳細資訊，請參見[此頁面](https://docs.snowflake.net/manuals/sql-reference/parameters.html#timezone)。 |
| WeekStart | WEEK_START會話參數。 依預設設為0。 <br>有關詳細資訊，請參見[此頁面](https://docs.snowflake.com/en/sql-reference/parameters.html#week-start)。 |
| UseCachedResult | USE_CACHED_RESULTS會話參數。 預設設定為TRUE。 此選項可用於禁用雪花快取結果。 <br>有關詳細資訊，請參見[此頁面](https://docs.snowflake.net/manuals/user-guide/querying-persisted-results.html)。 |
