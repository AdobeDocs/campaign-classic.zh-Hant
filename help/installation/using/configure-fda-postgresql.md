---
product: campaign
title: 配置對PostgreSQL的訪問
description: 了解如何配置對PostgreSQL的訪問
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 1%

---

# 配置對PostgreSQL的訪問 {#configure-fda-postgresql}



使用Campaign **同盟資料存取** (FDA)選項，以處理儲存在外部PostgreSQL資料庫中的資訊。

## PostgreSQL配置 {#postgresql-configuration}

您首先需要安裝Libpq。 Libpq允許客戶端程式將查詢發送到PostgreSQL後端伺服器並接收這些查詢的結果。

請依照下列步驟，設定 [!DNL PostgreSQL]:

* 對於CentOS，執行以下命令 `sudo apt-get -y install libpq-dev`.

* 對於Linux，執行以下命令 `yum install postgresql-devel`.

* 針對Windows，透過 `libpq.dll` 包含在Adobe Campaign安裝中。

在Adobe Campaign中，您可以設定 [!DNL PostgreSQL] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#postgresql-external).

## PostgreSQL外部帳戶 {#postgresql-external}

>[!NOTE]
>
> PostgreSQL可用於CentOS 7和6。

您需要建立 [!DNL PostgreSQL] 外部帳戶，將您的Campaign執行個體連線至您的 [!DNL PostgreSQL] 外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為外部帳戶 **[!UICONTROL Type]**.

1. 在 **[!UICONTROL Configuration]**，選取 [!DNL PostgreSQL, Greenplum] 從 **[!UICONTROL Type]** 下拉式清單。

   ![](assets/postgresql_1.png)

1. 設定 **[!UICONTROL PostgreSQL]** 外部帳戶驗證：

   * **[!UICONTROL Server]**:的URL [!DNL PostgreSQL] 伺服器。

   * **[!UICONTROL Account]**:使用者名稱。

   * **[!UICONTROL Password]**:用戶帳戶密碼。

   * **[!UICONTROL Database]**:資料庫名稱（可選）。

   * **[!UICONTROL Working schema]**:工作架構的名稱。 [了解更多](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**:時區設定於 [!DNL PostgreSQL]. [了解更多](https://www.postgresql.org/docs/7.2/timezones.html)

1. 按一下 **[!UICONTROL Parameters]** ，然後 **[!UICONTROL Deploy functions]** 按鈕以建立函式。

   >[!NOTE]
   >
   >要使所有函式都可用，您需要在遠程資料庫中建立Adobe Campaign SQL函式。 如需詳細資訊，請參閱 [頁面](../../configuration/using/adding-additional-sql-functions.md).

1. 按一下 **[!UICONTROL Save]** 完成設定時。

連接器支援下列選項：

| Option | 說明 |
|:-:|:-:|
| PGSQL_CONNECT_TIMEOUT | 等待連接的最大值（秒）。 <br>有關詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT). |
| PGSQL_KEEPALIVES_IDLE | 未活動的秒數，TCP應在此秒後向伺服器發送keepalive消息。 <br>有關詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE). |
| PGSQL_KEEPALIVES_INTVL | 伺服器未確認的TCP keepalive消息應重新傳輸的秒數。  <br>有關詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL). |
| PGSQL_KEEPALIVES_CNT | 在客戶端與伺服器的連接被視為無效之前可能丟失的TCP保留數。 <br>有關詳細資訊，請參閱 [PostgreSQL文檔](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT). |
