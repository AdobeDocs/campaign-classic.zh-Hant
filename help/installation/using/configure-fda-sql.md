---
product: campaign
title: 配置對MicrosoftSQL Server的訪問
description: 瞭解如何配置對MicrosoftSQL Server的訪問
source-git-commit: 26ae7ff1f0837a9a50057d97b00422a288b9dc7a
workflow-type: tm+mt
source-wordcount: '493'
ht-degree: 1%

---

# 配置對MicrosoftSQL Server的訪問 {#configure-fda-sql}

![](../../assets/v7-only.svg)

使用市場活動 **聯合資料存取** (FDA)選項，用於處理儲存在外部MicrosoftSQL Server資料庫中的資訊。 按照以下步驟配置訪問 [!DNL Microsoft SQL Server]。

1. 配置 [!DNL Microsoft SQL Server] 上 [CentOS](#sql-centos)。
1. 配置 [!DNL Microsoft SQL Server] 上 [Linux](#sql-linux)。
1. 配置 [!DNL Microsoft SQL Server] 上 [窗口](#sql-windows)。
1. 配置 [!DNL Microsoft SQL Server] [外部帳戶](#sql-external) 在活動中

## MicrosoftCentOS上的SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] 在CentOS 7和6上提供。

配置 [!DNL Microsoft SQL Server] 在CentOS上，執行以下步驟：

1. 使用以下命令下載並安裝SQL ODBC驅動程式：

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 在Adobe Campaign，您可以配置 [!DNL Microsoft SQL Server] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#sql-external)。

## MicrosoftLinux上的SQL Server {#sql-linux}

>[!NOTE]
>
> 如果運行的是舊版本的Adobe Campaign(7.2.1之前)，則需要安裝 `unix ODBC drivers`。

1. 從下載MS ODBC驅動程式 [此頁](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/)。

1. 以root用戶身份運行以下命令：

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 在Adobe Campaign，您可以配置 [!DNL Microsoft SQL Server] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#sql-external)。

## MicrosoftWindows上的SQL Server {#sql-windows}

配置 [!DNL Microsoft SQL Server] 在Windows上：

1. 在Windows中，按一下 **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**。

1. 從 **[!UICONTROL ODBC Data Sources (64-bit)]** 按一下 **[!UICONTROL Add...]**。

1. 檢查SQL Server Native Client v11是否在 **[!UICONTROL Create New Data Source]** 的子菜單。

1. 如果未列出SQL Server Native Client，則可以在 [此頁](https://www.microsoft.com/en-my/download/details.aspx?id=36434)。

1. 在Adobe Campaign，您可以配置 [!DNL Microsoft SQL Server] 外部帳戶。 有關如何配置外部帳戶的詳細資訊，請參閱 [此部分](#sql-external)。

## MicrosoftSQL Server外部帳戶 {#sql-external}

您需要建立 [!DNL Microsoft SQL Server] 將市場活動實例連接到您的外部帳戶 [!DNL Microsoft SQL Server] 外部資料庫。

1. 從市場活動 **[!UICONTROL Explorer]**&#x200B;按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選擇 **[!UICONTROL External database]** 作為您的外部帳戶 **[!UICONTROL Type]**。

1. 下 **[!UICONTROL Configuration]**&#x200B;選中 [!DNL Microsoft SQL Server] 從 **[!UICONTROL Type]** 下拉。

   ![](assets/sql.png)

1. 配置 **[!UICONTROL Microsoft SQL Server]** 外部帳戶身份驗證：

   * **[!UICONTROL Server]**:URL [!DNL Microsoft SQL Server] 伺服器。

   * **[!UICONTROL Account]**:用戶的名稱。

   * **[!UICONTROL Password]**:用戶帳戶密碼。

   * **[!UICONTROL Database]**:資料庫的名稱（可選）。

   * **[!UICONTROL Timezone]**:時區設定 [!DNL Microsoft SQL Server]。 [了解更多](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 按一下 **[!UICONTROL Parameters]** 按鈕 **[!UICONTROL Deploy functions]** 按鈕。

   >[!NOTE]
   >
   >要使所有函式都可用，您需要在遠程資料庫中建立Adobe CampaignSQL函式。 有關詳細資訊，請參閱 [頁](../../configuration/using/adding-additional-sql-functions.md)。

1. 按一下 **[!UICONTROL Save]** 完成配置。

連接器支援以下選項：

| Option | 說明 |
|---|---|
| 驗證 | 連接器支援的驗證類型。 當前支援的值：ActiveDirectoryMSI。 <br> 有關詳細資訊，請參閱示例8 [Microsoft文檔](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings)。 |
| 加密 | 指定連接是否在網路上使用TLS加密。 可能的值為 **是/強制（18.0及更高版本）**。 **無/可選（18.0及更高版本）**, **嚴格（18.0及更高版本）**。 預設值設定為 **是** 18.0及更高版本 **不** 在以前的版本中。 <br>有關此內容的詳細資訊，請參閱 [Microsoft文檔](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt)。 |
| TrustServerCertificate | 使用自簽名伺服器證書啟用加密(與 **加密**。 <br>接受的值： **是** 或 **不** （預設值，表示將驗證伺服器證書）。 |

