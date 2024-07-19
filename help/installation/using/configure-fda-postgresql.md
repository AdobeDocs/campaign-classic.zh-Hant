---
product: campaign
title: 設定PostgreSQL的存取權
description: 瞭解如何設定PostgreSQL的存取權
feature: Installation, Instance Settings
exl-id: 2c678f45-2555-4647-9885-bd002db7df37
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 2%

---

# 設定PostgreSQL的存取權 {#configure-fda-postgresql}



使用Campaign **同盟資料存取** (FDA)選項，處理儲存在外部PostgreSQL資料庫中的資訊。

## PostgreSQL設定 {#postgresql-configuration}

您必須先安裝Libpq。 Libpq可讓使用者端程式將查詢傳送至PostgreSQL後端伺服器，並接收這些查詢的結果。

請依照下列步驟設定[!DNL PostgreSQL]的存取權：

* 針對CentOS，執行以下命令`sudo apt-get -y install libpq-dev`。

* 針對Linux，執行以下命令`yum install postgresql-devel`。

* 對於Windows，Libpq是透過Adobe Campaign安裝中所包含的`libpq.dll`實作。

然後，您可以在Adobe Campaign中設定[!DNL PostgreSQL]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#postgresql-external)。

## PostgreSQL外部帳戶 {#postgresql-external}

>[!NOTE]
>
> PostgreSQL適用於CentOS 7和6。

您必須建立[!DNL PostgreSQL]外部帳戶，才能將Campaign執行個體連線至[!DNL PostgreSQL]外部資料庫。

1. 從行銷活動&#x200B;**[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 在&#x200B;**[!UICONTROL Configuration]**&#x200B;下，從&#x200B;**[!UICONTROL Type]**&#x200B;下拉式清單中選取[!DNL PostgreSQL, Greenplum]。

   ![](assets/postgresql_1.png)

1. 設定&#x200B;**[!UICONTROL PostgreSQL]**&#x200B;外部帳戶驗證：

   * **[!UICONTROL Server]**： [!DNL PostgreSQL]伺服器的網址。

   * **[!UICONTROL Account]**：使用者的名稱。

   * **[!UICONTROL Password]**：使用者帳戶密碼。

   * **[!UICONTROL Database]**：資料庫的名稱（選擇性）。

   * **[!UICONTROL Working schema]**：工作結構描述的名稱。 [了解更多](https://www.postgresql.org/docs/current/ddl-schemas.html)

   * **[!UICONTROL Timezone]**：時區設定在[!DNL PostgreSQL]。 [了解更多](https://www.postgresql.org/docs/7.2/timezones.html)

1. 按一下「**[!UICONTROL Parameters]**」標籤，然後按「**[!UICONTROL Deploy functions]**」按鈕以建立函式。

   >[!NOTE]
   >
   >若要讓所有函式都可使用，您需要在遠端資料庫中建立Adobe Campaign SQL函式。 如需詳細資訊，請參閱此[頁面](../../configuration/using/adding-additional-sql-functions.md)。

1. 完成設定時，請按一下&#x200B;**[!UICONTROL Save]**。

聯結器支援下列選項：

| 選項 | 說明 |
|:-:|:-:|
| PGSQL_CONNECT_逾時 | 連線等待時間上限（以秒為單位）。 <br>如需詳細資訊，請參閱[PostgreSQL檔案](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-CONNECT-CONNECT-TIMEOUT)。 |
| PGSQL_KEEPALIVES_IDLE | TCP應該傳送保持連線訊息至伺服器之後未使用的秒數。 <br>如需詳細資訊，請參閱[PostgreSQL檔案](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-IDLE)。 |
| PGSQL_KEEPALIVES_INTVL | 伺服器未確認的TCP keepalive訊息應該重新傳輸的秒數。  <br>如需詳細資訊，請參閱[PostgreSQL檔案](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-INTERVAL)。 |
| PGSQL_KEEPALIVES_CNT | 在使用者端與伺服器的連線被視為失效之前，可以遺失的TCP keepalive數目。 <br>如需詳細資訊，請參閱[PostgreSQL檔案](https://www.postgresql.org/docs/12/libpq-connect.html#LIBPQ-KEEPALIVES-COUNT)。 |
