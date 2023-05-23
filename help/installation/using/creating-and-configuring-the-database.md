---
product: campaign
title: 建立和設定資料庫
description: 建立和設定資料庫
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 2%

---

# 建立和設定資料庫{#creating-and-configuring-the-database}

建立資料庫時，Adobe Campaign提供了兩個不同的選項：

1. 建立或循環使用資料庫：如果要建立新資料庫或重新使用現有資料庫，請選擇此選項。 請參閱 [案例1:建立/循環使用資料庫](#case-1--creating-recycling-a-database)。
1. 使用現有資料庫：如果管理員已建立空資料庫，並且您想使用它，則選擇此選項；或擴展現有資料庫的結構。 請參閱 [案例二：使用現有資料庫](#case-2--using-an-existing-database)。

下文詳細介紹了配置步驟。

>[!CAUTION]
>
>資料庫、用戶和架構的名稱不能以數字開頭或包含特殊字元。
>
>僅 **內部** 標識符可以執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

## 案例1:建立/循環使用資料庫 {#case-1--creating-recycling-a-database}

下面介紹了建立資料庫或回收現有庫的步驟。 某些配置取決於使用的資料庫引擎：

涉及以下步驟：

* [步驟1 — 選擇資料庫引擎](#step-1---selecting-the-database-engine)。
* [步驟2 — 連接到伺服器](#step-2---connecting-to-the-server)。
* [步驟3 — 資料庫的連接和特性](#step-3---connection-and-characteristics-of-the-database)。
* [步驟4 — 要安裝的軟體包](#step-4---packages-to-install)。
* [步驟5 — 建立步驟](#step-5---creation-steps)。
* [步驟6 — 建立資料庫](#step-6---creating-the-database)。

### 步驟1 — 選擇資料庫引擎 {#step-1---selecting-the-database-engine}

從下拉清單中選擇資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

市場活動中列出了支援的資料庫 [相容性矩陣](../../rn/using/compatibility-matrix.md)。

確定伺服器並選擇要執行的操作類型。 在這個例子中， **[!UICONTROL Create or recycle a database]**。

![](assets/s_ncs_install_db_oracle_creation01.png)

根據所選資料庫引擎，伺服器標識資訊可能不同。

* 對於 **Oracle** 引擎，填充 **TNS名稱** 為應用程式伺服器定義。
* 對於 **PostgreSQL** 或 **資料庫2** 引擎中，必須指定應用程式伺服器上定義的DNS名稱（或IP地址）才能訪問資料庫伺服器。
* 對於 **MicrosoftSQL Server** 引擎，必須定義：在應用程式伺服器上定義以訪問資料庫伺服器的DNS名稱（或IP地址）: **DNS** 或 **DNS`\<instance>`** （實例模式）,

   >[!CAUTION]
   >
   > 從20.3開始，Windows NT身份驗證將取消。 **[!UICONTROL SQL Server authentication]** 現在是MicrosoftSQL Server唯一可用的身份驗證模式。 [深入了解](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### 步驟2 — 連接到伺服器 {#step-2---connecting-to-the-server}

在 **[!UICONTROL Server access]** 窗口，定義資料庫伺服器訪問。

![](assets/s_ncs_install_db_oracle_creation02.png)

為此，請輸入 **管理系統帳戶** 具有訪問資料庫權限，即：

* **系統** oracle資料庫，
* **沙** MicrosoftSQL Server資料庫，
* **郵戳** PostgreSQL資料庫，
* **db2inst1** 的子目錄。

### 步驟3 — 資料庫的連接和特性 {#step-3---connection-and-characteristics-of-the-database}

通過以下步驟，可以配置登錄資料庫的設定。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定義以下設定：

* 指定要建立的資料庫的名稱。

   >[!NOTE]
   >
   >對於DB2資料庫，資料庫名稱不能超過8個字元。

* 輸入連結到此資料庫的帳戶的密碼。
* 指示資料庫是否必須為Unicode。

   的 **[!UICONTROL Unicode database]** 選項，可以將所有字元類型以Unicode儲存，而不考慮語言。

   >[!NOTE]
   >
   >使用Oracle資料庫， **[!UICONTROL Unicode storage]** 選項 **恩克洛布** 和 **NVARCHAR** 的下界。
   > 
   >如果未選擇此選項，Oracle資料庫的字元集（字元集）必須啟用所有語言的資料儲存（建議使用AL32UTF8）。

* 為資料庫選擇時區，並指定是否希望它以UTC（如果可用）顯示。

   有關此內容的詳細資訊，請參閱 [時區管理](../../installation/using/time-zone-management.md)。

### 步驟4 — 要安裝的軟體包 {#step-4---packages-to-install}

選擇要安裝的包。

請參閱您的許可協定，以檢查您有權安裝的解決方案和選項，如「交互」或「社交營銷」。

![](assets/s_ncs_install_modules.png)

### 步驟5 — 建立步驟 {#step-5---creation-steps}

的 **[!UICONTROL Creation steps]** 窗口，您可以顯示和編輯用於建立表的SQL指令碼。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、MicrosoftSQL Server或PostgreSQL資料庫，管理員還可以定義 **儲存參數** 在建立資料庫對象時使用。

   這些參數將接收準確的表空間名(警告：區分大小寫)。 它們分別儲存在 **[!UICONTROL Administration > Platform > Options]** 節點(請參見 [此部分](../../installation/using/configuring-campaign-options.md#database)):

   * **WdbcOptions_TableSpaceUser**:基於模式的用戶表
   * **WdbcOptions_TableSpaceIndex**:基於模式的用戶表索引
   * **WdbcOptions_TableSpaceWork**:無架構的工作表
   * **WdbcOptions_TableSpaceWorkIndex**:沒有架構的工作表索引

* 對於Oracle資料庫，Adobe Campaign用戶必須具有訪問Oracle庫的權限，通常是 **安裝** 組。
* 的 **[!UICONTROL Set or change the administrator password]** 選項，您可以輸入具有管理員權限的連結到Adobe Campaign操作員的密碼。

   為安全起見，我們建議定義Adobe Campaign帳戶管理員密碼。

### 步驟6 — 建立資料庫 {#step-6---creating-the-database}

在嚮導的最後一個階段，您可以建立資料庫。 按一下 **[!UICONTROL Start]** 確認。

![](assets/s_ncs_install_db_oracle_creation06.png)

建立資料庫後，可以重新連接以完成實例配置。

現在必須啟動部署嚮導才能完成實例的配置。 請參閱 [部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard)。

連結到實例的資料庫的連接設定儲存在檔案中 **`/conf/config-<instance>.xml`** 在Adobe Campaign安裝目錄中。

在base61資料庫上的MicrosoftSQL Server配置示例，該資料庫連結到具有加密密碼的「campaign」帳戶：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例二：使用現有資料庫 {#case-2--using-an-existing-database}

資料庫以及用戶必須由資料庫管理員建立，並且訪問權限的配置正確。

例如，對於Oracle資料庫，所需的最低權限是：GRANTCONNECT、RESOURCE和UNLIMITED TABLESPACE。

要使用現有資料庫，配置步驟如下：

* [步驟1 — 選擇資料庫引擎](#step-1---choosing-the-database-engine)。
* [步驟2 — 資料庫連接設定](#step-2---database-connection-settings)。
* [步驟3 — 要安裝的軟體包](#step-3---packages-to-install)。
* [步驟4 — 建立步驟](#step-4---creation-steps)。
* [步驟5 — 建立資料庫](#step-5---creating-the-database)。

### 步驟1 — 選擇資料庫引擎 {#step-1---choosing-the-database-engine}

從下拉清單中選擇資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

確定伺服器並選擇要執行的操作類型。 在這個例子中， **[!UICONTROL Use an existing database]**。

![](assets/s_ncs_install_db_oracle_exists_01.png)

根據所選資料庫引擎，伺服器標識資訊可能不同。

* 對於 **Oracle** 引擎，填充 **TNS名稱** 為應用程式伺服器定義。
* 對於 **PostgreSQL** 或 **資料庫2** 引擎中，必須指定應用程式伺服器上定義的DNS名稱（或IP地址）才能訪問資料庫伺服器。
* 對於 **MicrosoftSQL Server** 引擎，必須定義：

   1. 在應用程式伺服器上定義以訪問資料庫伺服器的DNS名稱（或IP地址）,
   1. 用於訪問MicrosoftSQL Server的安全方法： **[!UICONTROL SQL Server authentication]** 或 **[!UICONTROL Windows NT authentication]**。

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 步驟2 — 資料庫連接設定 {#step-2---database-connection-settings}

在 **[!UICONTROL Database]** 窗口，定義資料庫連接設定。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定義以下設定：

* 輸入要使用的資料庫名稱，
* 輸入與此資料庫關聯的帳戶的名稱和密碼，

   >[!NOTE]
   >
   >確保架構名和用戶名都匹配。 建議通過市場活動控制台客戶端建立資料庫。
   >對於Oracle資料庫，無需輸入帳戶名。

* 指示資料庫是否應為Unicode。

### 步驟3 — 要安裝的軟體包 {#step-3---packages-to-install}

選擇要安裝的包。

請參閱您的許可協定以檢查您有權安裝的解決方案和選項，如「交互」或「銷售線索」。

![](assets/s_ncs_install_modules.png)

### 步驟4 — 建立步驟 {#step-4---creation-steps}

的 **[!UICONTROL Creation steps]** 窗口，您可以顯示和編輯用於建立表的SQL指令碼。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、MicrosoftSQL Server或PostgreSQL資料庫，管理員可以定義 **儲存參數** 在建立資料庫對象時使用。
* 對於Oracle資料庫，Adobe Campaign用戶必須具有訪問Oracle庫的權限，通常是 **安裝** 組。
* 的 **[!UICONTROL Set or change the administrator password]** 選項，您可以輸入具有管理員權限的連結到Adobe Campaign操作員的密碼。

   為安全起見，我們建議定義Adobe Campaign帳戶管理員密碼。

### 步驟5 — 建立資料庫 {#step-5---creating-the-database}

在嚮導的最後一個階段，您可以建立資料庫。 按一下 **[!UICONTROL Start]** 確認。

![](assets/s_ncs_install_db_oracle_creation06.png)

資料庫建立完成後，您可以重新連接以完成實例配置。

現在必須啟動部署嚮導才能完成實例的配置。 請參閱 [部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard)。

連結到實例的資料庫的連接設定儲存在檔案中 **`/conf/config-<instance>.xml`** 在Adobe Campaign安裝目錄中。

在base61資料庫上的MicrosoftSQL Server配置示例，該資料庫連結到具有加密密碼的「campaign」帳戶：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
