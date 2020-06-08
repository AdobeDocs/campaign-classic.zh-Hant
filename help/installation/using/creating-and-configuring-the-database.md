---
title: 建立和配置資料庫
seo-title: 建立和配置資料庫
description: 建立和配置資料庫
seo-description: null
page-status-flag: never-activated
uuid: e5143d55-61fa-416a-80db-c29a0caf9a3e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: initial-configuration
discoiquuid: 7dd8a6a5-7cca-4e92-8226-1b9e450dfaf9
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 653f630079277ffb75915206c445e9414cfcdd7c
workflow-type: tm+mt
source-wordcount: '1295'
ht-degree: 0%

---


# 建立和配置資料庫{#creating-and-configuring-the-database}

當您建立資料庫時，Adobe Campaign提供兩種不同的選項：

1. 建立或循環使用資料庫： 如果要建立新資料庫或重新使用現有資料庫，請選擇此選項。 請參閱 [案例1: 建立／回收資料庫](#case-1--creating-recycling-a-database)。
1. 使用現有資料庫： 如果管理員已建立空資料庫且您想使用它，請選擇此選項； 或擴展現有資料庫的結構。 請參閱 [案例2: 使用現有資料庫](#case-2--using-an-existing-database)。

下面將詳述配置步驟。

>[!CAUTION]
>
>資料庫、用戶和方案的名稱不能以數字開頭或包含特殊字元。
>
>只有內 **部識** 別碼才能執行這些操作。 For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

## 案例1: 建立／回收資料庫 {#case-1--creating-recycling-a-database}

建立資料庫或回收現有資料庫的步驟如下。 某些配置取決於使用的資料庫引擎：

涉及下列步驟：

* [步驟1 —— 選擇資料庫引擎](#step-1---selecting-the-database-engine),
* [步驟2 —— 連接到伺服器](#step-2---connecting-to-the-server),
* [步驟3 —— 資料庫的連接和特性](#step-3---connection-and-characteristics-of-the-database),
* [步驟4 —— 要安裝的軟體包](#step-4---packages-to-install),
* [步驟5 —— 建立步驟](#step-5---creation-steps),
* [步驟6 —— 建立資料庫](#step-6---creating-the-database)。

### 步驟1 —— 選擇資料庫引擎 {#step-1---selecting-the-database-engine}

從下拉式清單中選取資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

支援的資料庫在「相容性」一節 [中顯示](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)。

確定伺服器並選擇要執行的操作類型。 在這個例子中， **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

伺服器標識資訊可能會隨所選資料庫引擎而異。

* 對於 **Oracle** 引擎，請填入為應用程式伺服器定 **義的TNS名稱** 。
* 對於 **PostgreSQL** 或 **** DB2引擎，必須指定在應用程式伺服器上定義的DNS名稱（或IP地址）才能訪問資料庫伺服器。
* 對於 **Microsoft SQL Server** Engine，必須定義：

   1. 應用伺服器上定義的用於訪問資料庫伺服器的DNS名稱（或IP地址）: **DNS** 或 **DNS\`<instance>`**（例項模式）,
   1. 用於訪問Microsoft SQL Server的驗證方法： **[!UICONTROL SQL Server authentication]** 或 **[!UICONTROL Windows NT authentication]**&#x200B;者。

      ![](assets/s_ncs_install_db_mssql_creation01.png)

### 步驟2 —— 連接到伺服器 {#step-2---connecting-to-the-server}

在窗口 **[!UICONTROL Server access]** 中，定義資料庫伺服器訪問。

![](assets/s_ncs_install_db_oracle_creation02.png)

要執行此操作，請輸入具有訪問資料庫權限的 **Administration系統帳戶的名稱和密碼** ，即：

* **系統** （用於Oracle資料庫）
* **sa** 對於Microsoft SQL Server資料庫，
* **postgres** for a PostgreSQL database,
* **db2inst1** （用於DB2資料庫）。

### 步驟3 —— 資料庫的連接和特性 {#step-3---connection-and-characteristics-of-the-database}

以下步驟可讓您設定登入資料庫的設定。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定義下列設定：

* 指定要建立的資料庫的名稱。

   >[!NOTE]
   >
   >對於DB2資料庫，資料庫的名稱不能超過8個字元。

* 輸入連結到此資料庫的帳戶的密碼。
* 指示資料庫是否必須使用Unicode。

   此選 **[!UICONTROL Unicode database]** 項可讓您以Unicode儲存所有字元類型，不論語言為何。

   >[!NOTE]
   >
   >使用Oracle資料庫時，選 **[!UICONTROL Unicode storage]** 項可以使 **用NCLOB** 和 **** NVARCHAR類型欄位。
   > 
   >如果不選擇此選項，Oracle資料庫的字元集(charset)必須啟用所有語言的資料儲存（建議使用AL32UTF8）。

* 為資料庫選擇時區，並指定是否要使用UTC（如果可用）。

   有關詳細資訊，請參閱 [時區管理](../../installation/using/time-zone-management.md)。

### 步驟4 —— 要安裝的軟體包 {#step-4---packages-to-install}

選擇要安裝的軟體包。

請參閱您的授權合約以檢查您有權安裝的解決方案和選項，例如「互動」或「社交行銷」。

![](assets/s_ncs_install_modules.png)

### 步驟5 —— 建立步驟 {#step-5---creation-steps}

在該 **[!UICONTROL Creation steps]** 窗口中，可以顯示和編輯用於建立表的SQL指令碼。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、Microsoft SQL Server或PostgreSQL資料庫，管理員還可以定義建立資料庫對 **像時要使用的儲存參數** 。

   這些參數會接收到確切的表空間名稱(警告： 區分大小寫)。 它們分別儲存在節 **[!UICONTROL Administration > Platform > Options]** 點中的以下選項：

   * **WdbcOptions_TableSpaceUser**: 基於方案的用戶表
   * **WdbcOptions_TableSpaceIndex**: 基於方案的用戶表索引
   * **WdbcOptions_TableSpaceWork**: 無架構的工作表
   * **WdbcOptions_TableSpaceWorkIndex**: 沒有模式的工作表索引

* 對於Oracle資料庫，Adobe Campaign用戶必須具有對Oracle庫的訪問權，通常作為Oinstall組的 **成員** 。
* 此選 **[!UICONTROL Set or change the administrator password]** 項可讓您輸入連結至具有管理員權限之Adobe Campaign運算子的密碼。

   我們建議為安全目的定義Adobe Campaign帳戶管理員密碼。

### 步驟6 —— 建立資料庫 {#step-6---creating-the-database}

使用嚮導的最後一個階段可以建立資料庫。 Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

建立資料庫後，您可以重新連接以完成實例配置。

您現在必須啟動部署精靈，才能完成執行個體的設定。 請參閱部 [署精靈](../../installation/using/deploying-an-instance.md#deployment-wizard)。

連結至執行個體之資料庫的連線設定會儲存在Adobe Campaign安 **`/conf/config-<instance>.xml`** 裝目錄的檔案中。

在base61資料庫上連結至「促銷活動」帳戶並加密密碼的Microsoft SQL Server設定範例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例2: 使用現有資料庫 {#case-2--using-an-existing-database}

資料庫以及用戶必須由資料庫管理員建立，並且訪問權限必須正確配置。

例如，對於Oracle資料庫，最低要求的權限為： 授予連接、資源和無限表空間。

要使用現有資料庫，配置步驟如下：

* [步驟1 —— 選擇資料庫引擎](#step-1---choosing-the-database-engine),
* [步驟2 —— 資料庫連接設定](#step-2---database-connection-settings),
* [步驟3 —— 要安裝的軟體包](#step-3---packages-to-install),
* [步驟4 —— 建立步驟](#step-4---creation-steps),
* [步驟5 —— 建立資料庫](#step-5---creating-the-database)。

### 步驟1 —— 選擇資料庫引擎 {#step-1---choosing-the-database-engine}

從下拉式清單中選擇資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

確定伺服器並選擇要執行的操作類型。 在這個例子中， **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

伺服器標識資訊可能會隨所選資料庫引擎而異。

* 對於 **Oracle** 引擎，請填入為應用程式伺服器定 **義的TNS名稱** 。
* 對於 **PostgreSQL** 或 **** DB2引擎，必須指定在應用程式伺服器上定義的DNS名稱（或IP地址）才能訪問資料庫伺服器。
* 對於 **Microsoft SQL Server** Engine，必須定義：

   1. 應用程式伺服器上定義的DNS名稱（或IP地址），以訪問資料庫伺服器，
   1. 用於訪問Microsoft SQL Server的安全方法： **[!UICONTROL SQL Server authentication]** 或 **[!UICONTROL Windows NT authentication]**&#x200B;者。

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 步驟2 —— 資料庫連接設定 {#step-2---database-connection-settings}

在窗口 **[!UICONTROL Database]** 中，定義資料庫連接設定。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定義下列設定：

* 輸入要使用的資料庫的名稱，
* 輸入與此資料庫關聯的帳戶的名稱和密碼，

   >[!NOTE]
   >
   >請確定架構名稱和用戶名都匹配。 建議建立資料庫的方式是透過促銷活動主控台用戶端。
   >對於Oracle資料庫，無需輸入帳戶名稱。

* 指示資料庫是否應為Unicode。

### 步驟3 —— 要安裝的軟體包 {#step-3---packages-to-install}

選擇要安裝的軟體包。

請參閱您的授權合約以檢查您有權安裝的解決方案和選項，例如「互動」或「銷售機會」。

![](assets/s_ncs_install_modules.png)

### 步驟4 —— 建立步驟 {#step-4---creation-steps}

在該 **[!UICONTROL Creation steps]** 窗口中，可以顯示和編輯用於建立表的SQL指令碼。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、Microsoft SQL Server或PostgreSQL資料庫，管理員可以定義建立資料庫對 **像時要使用的存** 儲參數。
* 對於Oracle資料庫，Adobe Campaign用戶必須具有對Oracle庫的訪問權，通常作為Oinstall組的 **成員** 。
* 此選 **[!UICONTROL Set or change the administrator password]** 項可讓您輸入連結至具有管理員權限之Adobe Campaign運算子的密碼。

   我們建議為安全目的定義Adobe Campaign帳戶管理員密碼。

### 步驟5 —— 建立資料庫 {#step-5---creating-the-database}

使用嚮導的最後一個階段可以建立資料庫。 Click **[!UICONTROL Start]** to confirm.

![](assets/s_ncs_install_db_oracle_creation06.png)

資料庫建立完成後，您可以重新連接以完成實例配置。

您現在必須啟動部署精靈，才能完成執行個體的設定。 請參閱部 [署精靈](../../installation/using/deploying-an-instance.md#deployment-wizard)。

連結至執行個體之資料庫的連線設定會儲存在Adobe Campaign安 **`/conf/config-<instance>.xml`** 裝目錄的檔案中。

在base61資料庫上連結至「促銷活動」帳戶並加密密碼的Microsoft SQL Server設定範例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

