---
product: campaign
title: 設定Microsoft SQL Server的存取權
description: 瞭解如何設定Microsoft SQL Server的存取權
feature: Installation, Federated Data Access
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: 65ab4577-3126-4579-8fcc-e93772ebd1e8
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 2%

---

# 設定Microsoft SQL Server的存取權 {#configure-fda-sql}



使用行銷活動 **同盟資料存取** (FDA)選項，用於處理儲存在外部Microsoft SQL Server資料庫中的資訊。 請依照下列步驟，設定存取權至 [!DNL Microsoft SQL Server].

1. 設定 [!DNL Microsoft SQL Server] 於 [CentOS](#sql-centos).
1. 設定 [!DNL Microsoft SQL Server] 於 [Linux](#sql-linux).
1. 設定 [!DNL Microsoft SQL Server] 於 [Windows](#sql-windows).
1. 設定 [!DNL Microsoft SQL Server] [外部帳戶](#sql-external) 在Campaign中

## CentOS上的Microsoft SQL Server {#sql-centos}

>[!NOTE]
>
> [!DNL Microsoft SQL Server] 適用於CentOS 7和6。

進行設定 [!DNL Microsoft SQL Server] 在CentOS上，請遵循下列步驟：

1. 使用下列命令下載並安裝SQL ODBC驅動程式：

   ```
   sudo su
   curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo
   exit
   sudo yum remove unixODBC-utf16 unixODBC-utf16-devel #to avoid conflicts
   sudo ACCEPT_EULA=Y yum install msodbcsql
   ```

1. 接著，您可以在Adobe Campaign中設定 [!DNL Microsoft SQL Server] 外部帳戶。 有關如何設定外部帳戶的詳細資訊，請參閱 [本節](#sql-external).

## Linux上的Microsoft SQL Server {#sql-linux}

>[!NOTE]
>
> 如果您執行的是舊版Adobe Campaign （7.2.1之前），您必須安裝 `unix ODBC drivers`.

1. 下載MS ODBC驅動程式，從 [此頁面](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/msodbcsql17/).

1. 以root使用者的身分執行以下命令：

   ```
   # install the mssql odbc that was downloaded
   dpkg -i msodbcsql17_17.7.1.1-1_amd64.deb
   # accept the license terms
   ```

1. 接著，您可以在Adobe Campaign中設定 [!DNL Microsoft SQL Server] 外部帳戶。 有關如何設定外部帳戶的詳細資訊，請參閱 [本節](#sql-external).

## Windows上的Microsoft SQL Server {#sql-windows}

進行設定 [!DNL Microsoft SQL Server] 在Windows上：

1. 在Windows中，按一下 **[!UICONTROL Control Panel]** &#39;>&#39; **[!UICONTROL System and Security]** &#39;>&#39; **[!UICONTROL Administrative Tools]**&#39;>&#39; **[!UICONTROL ODBC Data Sources (64-bit)]**.

1. 從 **[!UICONTROL ODBC Data Sources (64-bit)]** 新視窗，按一下 **[!UICONTROL Add...]**.

1. 檢查SQL Server Native Client v11是否列於 **[!UICONTROL Create New Data Source]** 視窗。

1. 如果未列出SQL Server Native Client，您可以將其下載到 [此頁面](https://www.microsoft.com/en-my/download/details.aspx?id=36434).

1. 接著，您可以在Adobe Campaign中設定 [!DNL Microsoft SQL Server] 外部帳戶。 有關如何設定外部帳戶的詳細資訊，請參閱 [本節](#sql-external).

## Microsoft SQL Server外部帳戶 {#sql-external}

您需要建立 [!DNL Microsoft SQL Server] 將您的Campaign執行個體連線到您的外部帳戶 [!DNL Microsoft SQL Server] 外部資料庫。

1. 從Campaign **[!UICONTROL Explorer]**，按一下 **[!UICONTROL Administration]** &#39;>&#39; **[!UICONTROL Platform]** &#39;>&#39; **[!UICONTROL External accounts]**.

1. 按一下&#x200B;**[!UICONTROL New]**。

1. 選取 **[!UICONTROL External database]** 作為外部帳戶的 **[!UICONTROL Type]**.

1. 在 **[!UICONTROL Configuration]**，選取 [!DNL Microsoft SQL Server] 從 **[!UICONTROL Type]** 下拉式清單。

   ![](assets/sql.png)

1. 設定 **[!UICONTROL Microsoft SQL Server]** 外部帳戶驗證：

   * **[!UICONTROL Server]**：的URL [!DNL Microsoft SQL Server] 伺服器。

   * **[!UICONTROL Account]**：使用者名稱。

   * **[!UICONTROL Password]**：使用者帳戶密碼。

   * **[!UICONTROL Database]**：資料庫名稱（選用）。

   * **[!UICONTROL Timezone]**：時區設定於 [!DNL Microsoft SQL Server]. [了解更多](https://docs.microsoft.com/en-us/sql/t-sql/functions/current-timezone-transact-sql?view=sql-server-ver15)

1. 按一下 **[!UICONTROL Parameters]** 按Tab鍵，然後 **[!UICONTROL Deploy functions]** 按鈕以建立函式。

   >[!NOTE]
   >
   >若要讓所有函式都可使用，您需要在遠端資料庫中建立Adobe Campaign SQL函式。 如需詳細資訊，請參閱此 [頁面](../../configuration/using/adding-additional-sql-functions.md).

1. 按一下 **[!UICONTROL Save]** 完成設定時。

聯結器支援下列選項：

| 選項 | 說明 |
|---|---|
| 驗證 | 聯結器支援的驗證型別。 目前支援的值： ActiveDirectoryMSI。 <br> 有關詳細資訊，請參閱範例8 [Microsoft檔案](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory?view=sql-server-ver15#example-connection-strings). |
| 加密 | 指定連線是否透過網路使用TLS加密。 可能的值包括 **是/強制（18.0和更新版本）**， **no/optional （18.0和更新版本）**、和 **strict （18.0和更新版本）**. 預設值設為 **是** 在18.0版及更新版本中和 **否** 在舊版中。 <br>有關詳細資訊，請參閱 [Microsoft檔案](https://docs.microsoft.com/en-us/sql/connect/odbc/dsn-connection-string-attribute?view=azure-sqldw-latest#encrypt). |
| TrustServerCertificate | 使用自我簽署伺服器憑證啟用加密（當搭配使用時） **加密**. <br>接受的值： **是** 或 **否** （預設值，表示將驗證伺服器憑證）。 |
