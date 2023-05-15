---
product: campaign
title: 配置對Microsoft SQL Server的訪問
description: 了解如何配置對Microsoft SQL Server的訪問
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# 配置對Microsoft SQL Server的訪問 {#configure-fda-sql}



使用Campaign **同盟資料存取** (FDA)選項，處理儲存在外部Microsoft SQL Server資料庫中的資訊。 請依照下列步驟，設定 [!DNL Microsoft SQL Server].

1. 設定 [!DNL Microsoft SQL Server] on [CentOS](#sql-centos).
1. 設定 [!DNL Microsoft SQL Server] on [Linux](#sql-linux).
1. 設定 [!DNL Microsoft SQL Server] on [Windows](#sql-windows).
1. 設定 [!DNL Microsoft SQL Server] [外部帳戶](#sql-external) 在Campaign

## Microsoft CentOS上的SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] 適用於CentOS 7和6。

配置 [!DNL Microsoft SQL Server] 在CentOS上，請遵循下列步驟：

1. 使用以下命令下載並安裝SQL ODBC驅動程式：

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 在Adobe Campaign中，您可以設定 [!DNL Microsoft SQL Server] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#sql-external).

## Microsoft Linux上的SQL Server {#sql-linux}

>[!NOTE]
>
> 如果您執行的是舊版Adobe Campaign（在7.2.1之前），則需要安裝 `unix ODBC drivers`.

1. 從下載MS ODBC驅動程式 [本頁](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. 以root用戶身份運行以下命令：

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 在Adobe Campaign中，您可以設定 [!DNL Microsoft SQL Server] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#sql-external).

## Microsoft Windows上的SQL Server {#sql-windows}

配置 [!DNL Microsoft SQL Server] 在Windows上：

1. 在Windows中，按一下 **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. 從 **[!UICONTROL ODBC Data Sources (64-bit)]** 按一下 **[!UICONTROL Add...]**.

1. 檢查SQL Server本機客戶端v11是否列於 **[!UICONTROL Create New Data Source]** 窗口。

1. 如果未列出SQL Server本機客戶端，可以在 [本頁](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. 在Adobe Campaign中，您可以設定 [!DNL Microsoft SQL Server] 外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱 [本節](#sql-external).

## Microsoft SQL Server外部帳戶 {#sql-external}

您需要建立 [!DNL Microsoft SQL Server] 外部帳戶，將您的Campaign執行個體連線至您的 [!DNL Microsoft SQL Server] 外部資料庫。

1. 從促銷活動 **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為外部帳戶 **[!UICONTROL Type]**.

1. 在 **[!UICONTROL Configuration]**，選取 [!DNL Microsoft SQL Server] 從 **[!UICONTROL Type]** 下拉式清單。

   ![](assets/sql.png)

1. 設定 **[!UICONTROL Microsoft SQL Server]** 外部帳戶驗證：

   * **[!UICONTROL Server]**:的URL [!DNL Microsoft SQL Server] 伺服器。

   * **[!UICONTROL Account]**:使用者名稱。

   * **[!UICONTROL Password]**:用戶帳戶密碼。

   * **[!UICONTROL Database]**:資料庫名稱（可選）。

   * **[!UICONTROL Timezone]**:時區設定於 [!DNL Microsoft SQL Server]. [了解更多](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 按一下 **[!UICONTROL Parameters]** ，然後 **[!UICONTROL Deploy functions]** 按鈕以建立函式。

   >[!NOTE]
   >
   >要使所有函式都可用，您需要在遠程資料庫中建立Adobe Campaign SQL函式。 如需詳細資訊，請參閱 [頁面](../../configuration/using/adding-additional-sql-functions.md).

1. 按一下 **[!UICONTROL Save]** 完成設定時。

連接器支援下列選項：

| Option | 說明 |
|---|---|
| 驗證 | 連接器支援的驗證類型。 目前支援的值：ActiveDirectoryMSI。 <br> 如需詳細資訊，請參閱的範例8 [Microsoft檔案](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| 加密 | 指定連接是否通過網路使用TLS加密。 可能的值包括 **是/強制（18.0和更新版本）**, **否/可選（18.0和更新版本）**，和 **嚴格（18.0及更新版本）**. 預設值設為 **是** 18.0版及更新版本中 **no** 在舊版中。 <br>有關詳細資訊，請參閱 [Microsoft檔案](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | 使用自簽名的伺服器證書啟用加密(當與 **加密**. <br>接受的值： **是** 或 **no** （預設值，表示將驗證伺服器憑證）。 |
