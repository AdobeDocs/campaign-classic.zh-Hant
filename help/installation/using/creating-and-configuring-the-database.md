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

當您建立資料庫時，Adobe Campaign提供兩種不同的選項：

1. 建立或回收資料庫：如果要建立新資料庫或重複使用現有資料庫，請選擇此選項。 請參閱 [案例1：建立/回收資料庫](#case-1--creating-recycling-a-database).
1. 使用現有資料庫：如果管理員已建立空白資料庫，而且您想要使用它，請選擇此選項；或擴充現有資料庫的結構。 請參閱 [案例2：使用現有資料庫](#case-2--using-an-existing-database).

設定步驟將於下文詳細說明。

>[!CAUTION]
>
>資料庫、使用者和結構描述的名稱不能以數字開頭或包含特殊字元。
>
>僅限 **內部** 識別碼可執行這些操作。 如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

## 案例1：建立/回收資料庫 {#case-1--creating-recycling-a-database}

建立資料庫或回收現有基礎的步驟如下所示。 有些設定視所使用的資料庫引擎而定：

涉及下列步驟：

* [步驟1 — 選取資料庫引擎](#step-1---selecting-the-database-engine)，
* [步驟2 — 連線到伺服器](#step-2---connecting-to-the-server)，
* [步驟3 — 資料庫的連線與特性](#step-3---connection-and-characteristics-of-the-database)，
* [步驟4 — 要安裝的套件](#step-4---packages-to-install)，
* [步驟5 — 建立步驟](#step-5---creation-steps)，
* [步驟6 — 建立資料庫](#step-6---creating-the-database).

### 步驟1 — 選取資料庫引擎 {#step-1---selecting-the-database-engine}

從下拉式清單中選取資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

Campaign中列出支援的資料庫 [相容性矩陣](../../rn/using/compatibility-matrix.md).

識別伺服器並選擇要執行的作業型別。 在這種情況下， **[!UICONTROL Create or recycle a database]**.

![](assets/s_ncs_install_db_oracle_creation01.png)

視選取的資料庫引擎而定，伺服器識別資訊可能會有所不同。

* 對於 **oracle** 引擎，填入 **TNS名稱** 已為應用程式伺服器定義。
* 對於 **PostgreSQL** 或 **DB2** 引擎，您必須指定在應用程式伺服器上定義的DNS名稱（或IP位址），才能存取資料庫伺服器。
* 對於 **Microsoft SQL Server** 引擎，您必須定義：應用程式伺服器上定義的DNS名稱（或IP位址），才能存取資料庫伺服器： **DNS** 或 **DNS`\<instance>`** （例項模式），

   >[!CAUTION]
   >
   > 從20.3版本開始，停止支援Windows NT驗證。 **[!UICONTROL SQL Server authentication]** 現在是Microsoft SQL Server唯一可用的驗證模式。 [深入了解](../../rn/using/deprecated-features.md)

   ![](assets/s_ncs_install_db_mssql_creation01.png)

### 步驟2 — 連線到伺服器 {#step-2---connecting-to-the-server}

在 **[!UICONTROL Server access]** 視窗，定義資料庫伺服器存取許可權。

![](assets/s_ncs_install_db_oracle_creation02.png)

要執行此操作，請輸入 **管理系統帳戶** 具有存取資料庫的許可權，例如：

* **系統** 對於Oracle資料庫，
* **sa** 若為Microsoft SQL Server資料庫，
* **postgres** 對於PostgreSQL資料庫，
* **db2inst1** DB2資料庫。

### 步驟3 — 資料庫的連線與特性 {#step-3---connection-and-characteristics-of-the-database}

下列步驟可讓您設定登入資料庫的設定。

![](assets/s_ncs_install_db_oracle_creation03.png)

您需要定義下列設定：

* 指定要建立的資料庫名稱。

   >[!NOTE]
   >
   >對於DB2資料庫，資料庫名稱不得超過8個字元。

* 輸入連結至此資料庫的帳戶密碼。
* 指示資料庫是否必須採用Unicode。

   此 **[!UICONTROL Unicode database]** 選項可讓您以Unicode儲存所有字元型別，無論語言為何。

   >[!NOTE]
   >
   >若使用Oracle資料庫， **[!UICONTROL Unicode storage]** 選項可讓您使用 **NCLOB** 和 **NVARCHAR** 輸入欄位。
   > 
   >如果不選取此選項，Oracle資料庫的字元集（字元集）必須啟用所有語言的資料儲存（建議使用AL32UTF8）。

* 選擇資料庫的時區，並指定是否要以UTC格式（如果可用）。

   有關詳細資訊，請參閱 [時區管理](../../installation/using/time-zone-management.md).

### 步驟4 — 要安裝的套件 {#step-4---packages-to-install}

選取您要安裝的套裝軟體。

請參閱您的授權合約，檢查您有權安裝的解決方案和選項，例如「互動」或「社交行銷」。

![](assets/s_ncs_install_modules.png)

### 步驟5 — 建立步驟 {#step-5---creation-steps}

此 **[!UICONTROL Creation steps]** 視窗可讓您顯示和編輯用來建立表格的SQL命令檔。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、Microsoft SQL Server或PostgreSQL資料庫，管理員也可以定義 **儲存引數** 建立資料庫物件時使用。

   這些引數會收到確切的表格空間名稱（警告：區分大小寫）。 它們分別儲存在 **[!UICONTROL Administration > Platform > Options]** 節點(請參閱 [本節](../../installation/using/configuring-campaign-options.md#database))：

   * **WdbcOptions_TableSpaceUser**：以結構描述為基礎的使用者表格
   * **WdbcOptions_TableSpaceIndex**：以結構描述為基礎的使用者表格索引
   * **WdbcOptions_TableSpaceWork**：沒有結構描述的工作表
   * **WdbcOptions_TableSpaceWorkIndex**：沒有結構描述的工作表索引

* 對於Oracle資料庫，Adobe Campaign使用者必須擁有Oracle資料庫的存取權，通常是 **oinstall** 群組。
* 此 **[!UICONTROL Set or change the administrator password]** 選項可讓您輸入連結至具有管理員許可權的Adobe Campaign運運算元的密碼。

   基於安全考量，建議您定義Adobe Campaign帳戶管理員密碼。

### 步驟6 — 建立資料庫 {#step-6---creating-the-database}

精靈的最後階段可讓您建立資料庫。 按一下 **[!UICONTROL Start]** 確認。

![](assets/s_ncs_install_db_oracle_creation06.png)

建立資料庫後，您可以重新連線以完成執行處理組態。

您現在必須啟動部署精靈，才能完成執行個體的設定。 請參閱 [部署精靈](../../installation/using/deploying-an-instance.md#deployment-wizard).

連結至執行個體的資料庫連線設定會儲存在檔案中 **`/conf/config-<instance>.xml`** 在Adobe Campaign安裝目錄中找到。

連結至&#39;campaign&#39;帳戶及其加密密碼的base61資料庫上的Microsoft SQL Server設定範例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```

## 案例2：使用現有資料庫 {#case-2--using-an-existing-database}

資料庫以及使用者都必須由資料庫管理員建立，且存取許可權設定正確。

例如，對於Oracle資料庫，最低必要許可權為：GRANTCONNECT、RESOURCE和UNLIMITED TABLESPACE。

若要使用現有資料庫，設定步驟如下：

* [步驟1 — 選擇資料庫引擎](#step-1---choosing-the-database-engine)，
* [步驟2 — 資料庫連線設定](#step-2---database-connection-settings)，
* [步驟3 — 要安裝的套件](#step-3---packages-to-install)，
* [步驟4 — 建立步驟](#step-4---creation-steps)，
* [步驟5 — 建立資料庫](#step-5---creating-the-database).

### 步驟1 — 選擇資料庫引擎 {#step-1---choosing-the-database-engine}

從下拉式清單中選擇資料庫引擎。

![](assets/s_ncs_install_db_select_engine.png)

識別伺服器並選擇您要執行的作業型別。 在這種情況下， **[!UICONTROL Use an existing database]**.

![](assets/s_ncs_install_db_oracle_exists_01.png)

視選取的資料庫引擎而定，伺服器識別資訊可能會有所不同。

* 對於 **oracle** 引擎，填入 **TNS名稱** 已為應用程式伺服器定義。
* 對於 **PostgreSQL** 或 **DB2** 引擎，您必須指定在應用程式伺服器上定義的DNS名稱（或IP位址），才能存取資料庫伺服器。
* 對於 **Microsoft SQL Server** 引擎，您必須定義：

   1. 應用程式伺服器上定義的DNS名稱（或IP位址），用來存取資料庫伺服器，
   1. 用來存取Microsoft SQL Server的安全性方法： **[!UICONTROL SQL Server authentication]** 或 **[!UICONTROL Windows NT authentication]**.

      ![](assets/s_ncs_install_db_mssql_exists_01.png)

### 步驟2 — 資料庫連線設定 {#step-2---database-connection-settings}

在 **[!UICONTROL Database]** 視窗，定義資料庫連線設定。

![](assets/s_ncs_install_db_oracle_exists_02.png)

您需要定義下列設定：

* 輸入要使用的資料庫名稱，
* 輸入與此資料庫關聯之帳戶的名稱和密碼，

   >[!NOTE]
   >
   >請確定結構描述名稱和使用者名稱相符。 建立資料庫的建議方式是透過Campaign主控台使用者端。
   >對於Oracle資料庫，您不需要輸入帳戶名稱。

* 指示資料庫是否應為Unicode。

### 步驟3 — 要安裝的套件 {#step-3---packages-to-install}

選取您要安裝的套裝軟體。

請參閱您的授權合約，檢視您有權安裝的解決方案和選項，例如「互動」或「銷售機會」。

![](assets/s_ncs_install_modules.png)

### 步驟4 — 建立步驟 {#step-4---creation-steps}

此 **[!UICONTROL Creation steps]** 視窗可讓您顯示和編輯用來建立表格的SQL命令檔。

![](assets/s_ncs_install_db_oracle_creation04.png)

* 對於Oracle、Microsoft SQL Server或PostgreSQL資料庫，管理員可以定義 **儲存引數** 建立資料庫物件時使用。
* 對於Oracle資料庫，Adobe Campaign使用者必須擁有Oracle資料庫的存取權，通常是 **oinstall** 群組。
* 此 **[!UICONTROL Set or change the administrator password]** 選項可讓您輸入連結至具有管理員許可權的Adobe Campaign運運算元的密碼。

   基於安全考量，建議您定義Adobe Campaign帳戶管理員密碼。

### 步驟5 — 建立資料庫 {#step-5---creating-the-database}

精靈的最後階段可讓您建立資料庫。 按一下 **[!UICONTROL Start]** 確認。

![](assets/s_ncs_install_db_oracle_creation06.png)

資料庫建立完成後，您可以重新連線以完成執行處理組態。

您現在必須啟動部署精靈，才能完成執行個體的設定。 請參閱 [部署精靈](../../installation/using/deploying-an-instance.md#deployment-wizard).

連結至執行個體的資料庫連線設定會儲存在檔案中 **`/conf/config-<instance>.xml`** 在Adobe Campaign安裝目錄中找到。

連結至&#39;campaign&#39;帳戶及其加密密碼的base61資料庫上的Microsoft SQL Server設定範例：

```
<dbcnx encrypted="1" login="campaign:myBase" password="myPassword" provider="DB" server="dbServer"/>
```
