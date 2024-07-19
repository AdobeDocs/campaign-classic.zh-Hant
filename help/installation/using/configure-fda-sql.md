---
product: campaign
title: 設定Microsoft SQL Server的存取權
description: 瞭解如何設定Microsoft SQL Server的存取權
feature: Installation, Federated Data Access
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 1%

---

# 設定Microsoft SQL Server的存取權 {#configure-fda-sql}



使用Campaign **同盟資料存取** (FDA)選項，處理儲存在外部Microsoft SQL Server資料庫中的資訊。 請依照下列步驟設定[!DNL Microsoft SQL Server]的存取權。

1. 在[CentOS](#sql-centos)上設定[!DNL Microsoft SQL Server]。
1. 在[Linux](#sql-linux)上設定[!DNL Microsoft SQL Server]。
1. 在[Windows](#sql-windows)上設定[!DNL Microsoft SQL Server]。
1. 在Campaign中設定[!DNL Microsoft SQL Server] [外部帳戶](#sql-external)

## CentOS上的Microsoft SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server]可在CentOS 7和6上使用。

若要在CentOS上設定[!DNL Microsoft SQL Server]，請遵循下列步驟：

1. 使用下列命令下載並安裝SQL ODBC驅動程式：

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 然後，您可以在Adobe Campaign中設定[!DNL Microsoft SQL Server]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#sql-external)。

## Linux上的Microsoft SQL Server {#sql-linux}

>[!NOTE]
>
> 如果您執行較舊版本的Adobe Campaign （7.2.1之前），您必須安裝`unix ODBC drivers`。

1. 從[此頁面](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/)下載MS ODBC驅動程式。

1. 以root使用者的身分執行以下命令：

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 然後，您可以在Adobe Campaign中設定[!DNL Microsoft SQL Server]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#sql-external)。

## Windows上的Microsoft SQL Server {#sql-windows}

若要在Windows上設定[!DNL Microsoft SQL Server]：

1. 在Windows中，按一下&#x200B;**[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**。

1. 從&#x200B;**[!UICONTROL ODBC Data Sources (64-bit)]**&#x200B;新視窗，按一下&#x200B;**[!UICONTROL Add...]**。

1. 檢查SQL Server Native Client v11是否列在&#x200B;**[!UICONTROL Create New Data Source]**&#x200B;視窗中。

1. 如果未列出SQL Server Native Client，您可以在[此頁面](https://www.microsoft.com/en-my/download/details.aspx?id=36434)中下載。

1. 然後，您可以在Adobe Campaign中設定[!DNL Microsoft SQL Server]外部帳戶。 如需如何設定外部帳戶的詳細資訊，請參閱[本節](#sql-external)。

## Microsoft SQL Server外部帳戶 {#sql-external}

您必須建立[!DNL Microsoft SQL Server]外部帳戶，才能將Campaign執行個體連線至[!DNL Microsoft SQL Server]外部資料庫。

1. 從行銷活動&#x200B;**[!UICONTROL Explorer]**，按一下&#x200B;**[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**。

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取&#x200B;**[!UICONTROL External database]**&#x200B;作為外部帳戶的&#x200B;**[!UICONTROL Type]**。

1. 在&#x200B;**[!UICONTROL Configuration]**&#x200B;下，從&#x200B;**[!UICONTROL Type]**&#x200B;下拉式清單中選取[!DNL Microsoft SQL Server]。

   ![](assets/sql.png)

1. 設定&#x200B;**[!UICONTROL Microsoft SQL Server]**&#x200B;外部帳戶驗證：

   * **[!UICONTROL Server]**： [!DNL Microsoft SQL Server]伺服器的網址。

   * **[!UICONTROL Account]**：使用者的名稱。

   * **[!UICONTROL Password]**：使用者帳戶密碼。

   * **[!UICONTROL Database]**：資料庫的名稱（選擇性）。

   * **[!UICONTROL Timezone]**：時區設定在[!DNL Microsoft SQL Server]。 [了解更多](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 按一下「**[!UICONTROL Parameters]**」標籤，然後按「**[!UICONTROL Deploy functions]**」按鈕以建立函式。

   >[!NOTE]
   >
   >若要讓所有函式都可使用，您需要在遠端資料庫中建立Adobe Campaign SQL函式。 如需詳細資訊，請參閱此[頁面](../../configuration/using/adding-additional-sql-functions.md)。

1. 完成設定時，請按一下&#x200B;**[!UICONTROL Save]**。

聯結器支援下列選項：

| 選項 | 說明 |
|---|---|
| 驗證 | 聯結器支援的驗證型別。 目前支援的值： ActiveDirectoryMSI。 <br>如需詳細資訊，請參閱[Microsoft檔案](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings)的範例8。 |
| 加密 | 指定連線是否透過網路使用TLS加密。 可能的值是&#x200B;**是/強制（18.0和更新版本）**、**否/選用（18.0和更新版本）**&#x200B;和&#x200B;**嚴格（18.0和更新版本）**。 在18.0版及更新版本中，預設值設為&#x200B;**是**，而在舊版中則設為&#x200B;**否**。 <br>如需詳細資訊，請參閱[Microsoft檔案](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt)。 |
| TrustServerCertificate | 與&#x200B;**Encrypt**&#x200B;搭配使用時，啟用使用自我簽署伺服器憑證的加密。 <br>接受的值： **是**&#x200B;或&#x200B;**否** （預設值，表示將驗證伺服器憑證）。 |
