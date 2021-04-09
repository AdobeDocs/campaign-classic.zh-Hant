---
solution: Campaign Classic
product: campaign
title: 建立和設定資料庫
description: 建立和設定資料庫
audience: installation
content-type: reference
topic-tags: initial-configuration
exl-id: f40bab8c-5064-40d9-beed-101a9f22c094
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 1%

---

# 建立和設定資料庫{#creating-and-configuring-the-database}

建立資料庫時，Adobe Campaign提供了兩個不同的選項：

1. 建立或循環使用資料庫：如果要建立新資料庫或重新使用現有資料庫，請選擇此選項。 請參閱[案例1:建立／循環使用資料庫](#case-1--creating-recycling-a-database)。
1. 使用現有資料庫：如果管理員已建立空資料庫且您想使用它，請選擇此選項；或擴展現有資料庫的結構。 請參閱[案例2:使用現有資料庫](#case-2--using-an-existing-database)。

下面將詳述配置步驟。

>[!CAUTION]
>
>資料庫、用戶和方案的名稱不能以數字開頭或包含特殊字元。
>
>只有&#x200B;**internal**&#x200B;標識符可以執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

## 案例1:建立／回收資料庫{#case-1--creating-recycling-a-database}

建立資料庫或回收現有資料庫的步驟如下。 某些配置取決於使用的資料庫引擎：

涉及下列步驟：

* [步驟1 —— 選擇資料庫引擎](#step-1---selecting-the-database-engine),
* [步驟2 —— 連接到伺服器](#step-2---connecting-to-the-server),
* [步驟3 —— 資料庫的連接和特性](#step-3---connection-and-characteristics-of-the-database),
* [步驟4 —— 要安裝的軟體包](#step-4---packages-to-install),
* [步驟5 —— 建立步驟](#step-5---creation-steps),
* [步驟6 —— 建立資料庫](#step-6---creating-the-database)。

### 步驟1 —— 選擇資料庫引擎{#step-1---selecting-the-database-engine}

從下拉式清單中選取資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

支援的資料庫列於Campaign [ Compatibility matrix](../../rn/using/compatibility-matrix.md)中。

確定伺服器並選擇要執行的操作類型。 在本例中，**[!UICONTROL Create or recycle a database]**。

![](assets/s_ncs_install_db_oracle_creation01.png)

伺服器標識資訊可能會隨所選資料庫引擎而異。

* 對於&#x200B;**Oracle**&#x200B;引擎，請填入為應用程式伺服器定義的&#x200B;**TNS名稱**。
* 對於&#x200B;**PostgreSQL**&#x200B;或&#x200B;**DB2**&#x200B;引擎，必須指定應用程式伺服器上定義的DNS名稱（或IP地址）才能訪問資料庫伺服器。
* 對於&#x200B;**Microsoft SQL Server**&#x200B;引擎，必須定義：應用伺服器上定義的用於訪問資料庫伺服器的DNS名稱（或IP地址）:**DNS**&#x200B;或&#x200B;**DNS`\<instance>`**（例項模式）,

   >[!CAUTION]
   >
   > 從20.3開始，Windows NT驗證將終止服務。 **[!UICONTROL SQL Server authentication]** 現在是Microsoft SQL Server唯一可用的驗證模式。[顯示全文](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### 步驟2 —— 連接到伺服器{#step-2---connecting-to-the-server}

在&#x200B;**[!UICONTROL Server access]**&#x200B;窗口中，定義資料庫伺服器訪問。

![](assets/s_ncs_install_db_oracle_creation02.png)

要執行此操作，請輸入&#x200B;**管理系統帳戶**&#x200B;的名稱和密碼，該帳戶具有訪問資料庫的權限，即：

* **oracle** 資料庫的系統，
* **對** 於Microsoft SQL Server資料庫，
* **PostgreSQL** 資料庫的Postgress,
* **db2inst1** （用於DB2資料庫）。

### 步驟3 —— 資料庫{#step-3---connection-and-characteristics-of-the-database}的連接和特性

以下步驟可讓您設定登入資料庫的設定。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定義下列設定：

* 指定要建立的資料庫的名稱。

   >[!NOTE]
   >
   >對於DB2資料庫，資料庫的名稱不能超過8個字元。

* 輸入連結到此資料庫的帳戶的密碼。
* 指示資料庫是否必須使用Unicode。

   **[!UICONTROL Unicode database]**&#x200B;選項可讓您以Unicode儲存所有字元類型，不論語言為何。

   >[!NOTE]
   >
   >使用Oracle資料庫時， **[!UICONTROL Unicode storage]**&#x200B;選項可以使用&#x200B;**NCLOB**&#x200B;和&#x200B;**NVARCHAR**&#x200B;類型欄位。
   > 
   >如果您未選取此選項，Oracle資料庫的字元集（字元集）必須啟用所有語言的資料儲存（建議使用AL32UTF8）。

* 為資料庫選擇時區，並指定是否要使用UTC（如果可用）。

   有關詳細資訊，請參閱[時區管理](../../installation/using/time-zone-management.md)。

### 步驟4 —— 要安裝的軟體包{#step-4---packages-to-install}

選擇要安裝的軟體包。

請參閱您的授權合約以檢查您有權安裝的解決方案和選項，例如「互動」或「社交行銷」。

![](assets/s_ncs_install_modules.png)

### 步驟5 —— 建立步驟{#step-5---creation-steps}

通過&#x200B;**[!UICONTROL Creation steps]**&#x200B;窗口，可以顯示和編輯用於建立表的SQL指令碼。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、Microsoft SQL Server或PostgreSQL資料庫，管理員還可以定義建立資料庫對象時使用的&#x200B;**儲存參數**。

   這些參數會接收到確切的表空間名稱(警告：區分大小寫)。 它們分別儲存在&#x200B;**[!UICONTROL Administration > Platform > Options]**&#x200B;節點中的以下選項中（請參閱[本節](../../installation/using/configuring-campaign-options.md#database)）:

   * **WdbcOptions_TableSpaceUser**:基於方案的用戶表
   * **WdbcOptions_TableSpaceIndex**:基於方案的用戶表索引
   * **WdbcOptions_TableSpaceWork**:無架構的工作表
   * **WdbcOptions_TableSpaceWorkIndex**:沒有模式的工作表索引

* 對於Oracle資料庫，Adobe Campaign用戶必須具有Oracle庫的訪問權，通常作為&#x200B;**oinstall**&#x200B;組的成員。
* **[!UICONTROL Set or change the administrator password]**&#x200B;選項可讓您輸入連結至具有管理員權限之Adobe Campaign運算子的密碼。

   我們建議為安全目的定義Adobe Campaign帳戶管理員密碼。

### 步驟6 —— 建立資料庫{#step-6---creating-the-database}

使用嚮導的最後一個階段可以建立資料庫。 按一下&#x200B;**[!UICONTROL Start]**&#x200B;進行確認。

![](assets/s_ncs_install_db_oracle_creation06.png)

建立資料庫後，您可以重新連接以完成實例配置。

您現在必須啟動部署精靈，才能完成執行個體的設定。 請參閱[部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard)。

連結到實例的資料庫的連接設定儲存在位於Adobe Campaign安裝目錄的&#x200B;**`/conf/config-<instance>.xml`**&#x200B;檔案中。

在base61資料庫上連結至「促銷活動」帳戶並加密密碼的Microsoft SQL Server設定範例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例2:使用現有資料庫{#case-2--using-an-existing-database}

資料庫以及用戶必須由資料庫管理員建立，並且訪問權限必須正確配置。

例如，對於Oracle資料庫，最低要求的權限為：授予CONNECT、資源和無限表空間。

要使用現有資料庫，配置步驟如下：

* [步驟1 —— 選擇資料庫引擎](#step-1---choosing-the-database-engine),
* [步驟2 —— 資料庫連接設定](#step-2---database-connection-settings),
* [步驟3 —— 要安裝的軟體包](#step-3---packages-to-install),
* [步驟4 —— 建立步驟](#step-4---creation-steps),
* [步驟5 —— 建立資料庫](#step-5---creating-the-database)。

### 步驟1 —— 選擇資料庫引擎{#step-1---choosing-the-database-engine}

從下拉式清單中選擇資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

確定伺服器並選擇要執行的操作類型。 在本例中，**[!UICONTROL Use an existing database]**。

![](assets/s_ncs_install_db_oracle_exists_01.png)

伺服器標識資訊可能會隨所選資料庫引擎而異。

* 對於&#x200B;**Oracle**&#x200B;引擎，請填入為應用程式伺服器定義的&#x200B;**TNS名稱**。
* 對於&#x200B;**PostgreSQL**&#x200B;或&#x200B;**DB2**&#x200B;引擎，必須指定應用程式伺服器上定義的DNS名稱（或IP地址）才能訪問資料庫伺服器。
* 對於&#x200B;**Microsoft SQL Server**&#x200B;引擎，必須定義：

   1. 應用程式伺服器上定義的用於訪問資料庫伺服器的DNS名稱（或IP地址）,
   1. 用於訪問Microsoft SQL Server的安全方法：**[!UICONTROL SQL Server authentication]**&#x200B;或&#x200B;**[!UICONTROL Windows NT authentication]**。

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 步驟2 —— 資料庫連接設定{#step-2---database-connection-settings}

在&#x200B;**[!UICONTROL Database]**&#x200B;窗口中，定義資料庫連接設定。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定義下列設定：

* 輸入要使用的資料庫的名稱，
* 輸入與此資料庫關聯的帳戶的名稱和密碼，

   >[!NOTE]
   >
   >請確定架構名稱和使用者名稱都相符。 建議建立資料庫的方式是透過促銷活動主控台用戶端。
   >對於Oracle資料庫，無需輸入帳戶名稱。

* 指示資料庫是否應為Unicode。

### 步驟3 —— 安裝{#step-3---packages-to-install}的軟體包

選擇要安裝的軟體包。

請參閱您的授權合約以檢查您有權安裝的解決方案和選項，例如「互動」或「銷售機會」。

![](assets/s_ncs_install_modules.png)

### 步驟4 —— 建立步驟{#step-4---creation-steps}

通過&#x200B;**[!UICONTROL Creation steps]**&#x200B;窗口，可以顯示和編輯用於建立表的SQL指令碼。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、Microsoft SQL Server或PostgreSQL資料庫，管理員可以定義建立資料庫對象時使用的&#x200B;**儲存參數**。
* 對於Oracle資料庫，Adobe Campaign用戶必須具有Oracle庫的訪問權，通常作為&#x200B;**oinstall**&#x200B;組的成員。
* **[!UICONTROL Set or change the administrator password]**&#x200B;選項可讓您輸入連結至具有管理員權限之Adobe Campaign運算子的密碼。

   我們建議為安全目的定義Adobe Campaign帳戶管理員密碼。

### 步驟5 —— 建立資料庫{#step-5---creating-the-database}

使用嚮導的最後一個階段可以建立資料庫。 按一下&#x200B;**[!UICONTROL Start]**&#x200B;進行確認。

![](assets/s_ncs_install_db_oracle_creation06.png)

資料庫建立完成後，您可以重新連接以完成實例配置。

您現在必須啟動部署精靈，才能完成執行個體的設定。 請參閱[部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard)。

連結到實例的資料庫的連接設定儲存在位於Adobe Campaign安裝目錄的&#x200B;**`/conf/config-<instance>.xml`**&#x200B;檔案中。

在base61資料庫上連結至「促銷活動」帳戶並加密密碼的Microsoft SQL Server設定範例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
