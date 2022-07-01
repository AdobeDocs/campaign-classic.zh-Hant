---
product: campaign
title: 配置對PostgreSQL的訪問
description: 瞭解如何配置對PostgreSQL的訪問
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 1%

---

# 配置對PostgreSQL的訪問 {#configure-fda-postgresql}

![](../../assets/v7-only.svg)

使用市場活動 **聯合資料存取** (FDA)選項，用於處理儲存在外部PostgreSQL資料庫中的資訊。

## PostgreSQL配置 {#postgresql-configuration}

您首先需要安裝Libpq。 Libpq允許客戶端程式將查詢發送到PostgreSQL後端伺服器並接收這些查詢的結果。

按照以下步驟配置訪問 [!DNL PostgreSQL]:

* 對於CentOS，執行以下命令 `sudo apt-get -y install libpq-dev`。

* 對於Linux，執行以下命令 `yum install postgresql-devel`。

* 對於Windows,Libpq通過 `libpq.dll` 包含在Adobe Campaign安裝中。

在Adobe Campaign，您可以配置 [!DNL PostgreSQL] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#postgresql-external)。

## PostgreSQL外部帳戶 {#postgresql-external}

>[!NOTE]
>
> PostgreSQL在CentOS 7和6上提供。

您需要建立 [!DNL PostgreSQL] 將市場活動實例連接到您的外部帳戶 [!DNL PostgreSQL] 外部資料庫。

1. 從市場活動 **[!UICONTROL Explorer]**&#x200B;按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為您的外部帳戶 **[!UICONTROL Type]**。

1. 下 **[!UICONTROL Configuration]**&#x200B;選中 [!DNL PostgreSQL, Greenplum] 從 **[!UICONTROL Type]** 下拉。

   ![](assets/postgresql_1.png)

1. 配置 **[!UICONTROL PostgreSQL]** 外部帳戶身份驗證：

   * **[!UICONTROL Server]**:URL [!DNL PostgreSQL] 伺服器。

   * **[!UICONTROL Account]**:用戶的名稱。

   * **[!UICONTROL Password]**:用戶帳戶密碼。

   * **[!UICONTROL Database]**:資料庫的名稱（可選）。

   * **[!UICONTROL Working schema]**:工作架構的名稱。 [了解更多](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**:時區設定 [!DNL PostgreSQL]。 [了解更多](https://www.postgresql.org/docs/7.2/timezones.html)

1. 按一下 **[!UICONTROL Parameters]** 按鈕 **[!UICONTROL Deploy functions]** 按鈕。

   >[!NOTE]
   >
   >要使所有函式都可用，您需要在遠程資料庫中建立Adobe CampaignSQL函式。 有關詳細資訊，請參閱 [頁](../../configuration/using/adding-additional-sql-functions.md)。

1. 按一下 **[!UICONTROL Save]** 完成配置。

連接器支援以下選項：

| Option | 說明 |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | 最長等待連接時間（秒）。 <br>有關此內容的詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT)。 |
| PGSQL_KEEPALIVES_IDLE | TCP應向伺服器發送keepalive消息的不活動秒數。 <br>有關此內容的詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE)。 |
| PGSQL_KEEPALIVES_INTVL | 伺服器未確認的TCP keepalive消息應重新傳輸的秒數。  <br>有關此內容的詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL)。 |
| PGSQL_KEEPALIVES_CNT | 在客戶端與伺服器的連接被認為已死之前可能丟失的TCP持久連接數。 <br>有關此內容的詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT)。 |
