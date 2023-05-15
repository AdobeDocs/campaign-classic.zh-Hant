---
product: campaign
title: 獨立部署
description: 獨立部署
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 3%

---

# 獨立部署{#standalone-deployment}



此配置包括同一電腦上的所有元件：

* 應用程式(web),
* 傳遞程式(mta),
* 重定向過程（跟蹤）,
* 工作流進程和計畫任務(wfserver),
* 退回郵件程式(inMail),
* 統計過程(stat)。

進程之間的整體通信根據以下方案進行：

![](assets/s_900_ncs_install_standaloneconfig.png)

在管理少於100,000個收件者的清單時，可以運行此類配置，例如，使用以下軟體層：

* Linux,
* Apache,
* PostgreSQL,
* Qmail。

隨著卷的增長，此體系結構的一個變體會將資料庫伺服器移動到另一台電腦，以獲得更好的效能。

>[!NOTE]
>
>如果現有資料庫伺服器具有足夠的資源，也可以使用它。

## 功能 {#features}

### 優勢 {#advantages}

* 完全獨立且配置成本低（如果使用下面列出的開源軟體，則無需計費許可證）。
* 簡化安裝和網路配置。

### 缺點 {#disadvantages}

* 發生事故時的關鍵電腦。
* 廣播郵件時頻寬有限（根據我們的經驗，每小時大約有數萬封郵件）。
* 廣播時應用程式可能會變慢。
* 應用程式伺服器必須可從外部（例如位於DMZ中）使用，因為它承載重定向伺服器。

## 安裝和配置步驟 {#installation-and-configuration-steps}

### 必要條件 {#prerequisites}

* JDK、
* Web伺服器(IIS、Apache),
* 訪問資料庫伺服器，
* 可通過POP3訪問的退回郵箱，
* 建立兩個DNS別名：

   * 第一個向公眾公開，用於跟蹤並指向其公共IP上的電腦；
   * 向內部用戶公開的第二個別名，用於訪問控制台並指向同一台電腦。

* 防火牆配置為開啟SMTP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521(Oracle)、5432(PostgreSQL)等 埠。 有關詳細資訊，請參閱 [網路配置](../../installation/using/network-configuration.md).

在下列範例中，例項的參數為：

* 執行個體的名稱： **示範**
* DNS掩碼： **console.campaign.net&#42;** (僅用於客戶端控制台連接和報告。
* 資料庫： **campaign:demo@dbsrv**

### 安裝和配置（單台電腦） {#installing-and-configuring--single-machine-}

應用以下步驟：

1. 請依照Adobe Campaign伺服器的安裝程式操作： **nlserver** Linux或 **setup.exe** 在Windows上。

   有關詳細資訊，請參閱 [在Linux安裝Campaign的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)和 [在Windows安裝Campaign的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)。

1. 安裝Adobe Campaign伺服器後，使用命令啟動應用程式伺服器(web) **nlserver web -tomcat** （Web模組使您能夠在埠8080上以獨立Web伺服器模式偵聽方式啟動Tomcat），並確保Tomcat正確啟動：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次執行Web模組時，會建立 **config-default.xml** 和 **serverConf.xml** 檔案 **conf** 目錄。 中所有可用的參數 **serverConf.xml** 列於此 [節](../../installation/using/the-server-configuration-file.md).

   Press **Ctrl+C** 來停止伺服器。

   如需詳細資訊，請參閱下列章節：

   * Linux: [伺服器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 對於Windows: [伺服器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. 變更 **內部** 使用命令輸入密碼：

   ```
   nlserver config -internalpassword
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 建立 **示範** 具有用於追蹤之DNS遮罩的例項(在此例中， **tracking.campaign.net**)和用戶端主控台的存取權(在此例中， **console.campaign.net**)。 執行此作業有兩種方式：

   * 透過主控台建立執行個體：

      ![](assets/install_create_new_connexion.png)

      有關詳細資訊，請參閱 [建立例項並登入](../../installation/using/creating-an-instance-and-logging-on.md).

      或

   * 使用命令行建立實例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有關詳細資訊，請參閱 [建立例項](../../installation/using/command-lines.md#creating-an-instance).

1. 編輯 **config-demo.xml** 檔案(在 **config-default.xml**)，並確保 **mta** （傳遞）, **wfserver** （工作流程）, **inMail** （退回郵件）和 **stat** （統計資料）程式已啟用。 然後配置統計伺服器的地址：

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="localhost"/>
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 編輯 **serverConf.xml** 檔案並指定傳送網域，然後指定MTA模組用來回答MX類型DNS查詢的DNS伺服器的IP（或主機）位址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >此 **nameServers** 參數僅用於Windows。

   有關詳細資訊，請參閱 [Campaign伺服器設定](../../installation/using/configuring-campaign-server.md).

1. 複製客戶端控制台安裝程式(**setup-client-7.XX**, **YYYY.exe** 適用於v7或 **setup-client-6.XX**, **YYYY.exe** (v6.1)轉換為 **/datakit/nl/eng/jsp** 檔案夾。 [了解更多](../../installation/using/client-console-availability-for-windows.md)。

1. 按照以下各節所述的Web伺服器整合過程(IIS、Apache)操作：

   * Linux: [與Linux網頁伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 對於Windows: [與Windows版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 啟動網站並使用URL測試重新導向：https://tracking.campaign.net/r/test。

   瀏覽器必須顯示下列訊息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * Linux: [啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 對於Windows: [啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器(**net start nlserver6** 在Windows中， **/etc/init.d** 在Linux中)，然後執行命令 **nlserver pdump** 再次檢查是否有所有已啟用的模組。

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（Linux適用）: **systemctl啟動nlserver**

   ```
   12:09:54 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   syslogd@default (7611) - 9.2 MB
   stat@demo (5988) - 1.5 MB
   inMail@demo (7830) - 11.9 MB
   watchdog (27369) - 3.1 MB
   mta@demo (7831) - 15.6 MB
   wfserver@demo (7832) - 11.5 MB
   web@default (28671) - 40.5 MB
   ```

   此命令也可讓您知道電腦上安裝之Adobe Campaign伺服器的版本和組建編號。

1. 測試 **nlserver web** 模組（使用URL）:https://console.campaign.net/nl/jsp/logon.jsp

   此URL可讓您存取用戶端設定程式的下載頁面。

   輸入 **內部** 進入存取控制頁面時，登入和相關密碼。 [了解更多](../../installation/using/client-console-availability-for-windows.md)。

   ![](assets/s_ncs_install_access_client.png)

1. 啟動Adobe Campaign用戶端主控台（從上一個下載頁面啟動，或直接在伺服器上啟動以進行Windows安裝），將伺服器連線URL設為https://console.campaign.net ，然後使用 **內部** 登入。

   請參閱 [本頁](../../installation/using/creating-an-instance-and-logging-on.md) 和 [本節](../../installation/using/configuring-campaign-server.md#internal-identifier).

   第一次登錄時，資料庫建立嚮導將出現：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   請依照精靈中的步驟操作，並建立與連線執行個體相關聯的資料庫。

   有關詳細資訊，請參閱 [建立和配置資料庫](../../installation/using/creating-and-configuring-the-database.md).

   建立資料庫後，請註銷。

1. 使用 **管理員** 不使用密碼登錄並啟動部署嚮導( **[!UICONTROL Tools > Advanced]** 功能表)，完成執行個體的設定。

   有關詳細資訊，請參閱 [部署執行個體](../../installation/using/deploying-an-instance.md).

   要設定的主要參數如下：

   * 電子郵件傳送：退回郵件的寄件者和回覆地址及錯誤信箱。
   * 追蹤：填入用於重新導向的外部URL和內部URL，按一下 **在追蹤伺服器上註冊** 然後在 **示範** 追蹤伺服器的例項。

      有關詳細資訊，請參閱 [追蹤設定](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由於Adobe Campaign伺服器同時作為應用程式伺服器和重新導向伺服器，因此用於收集追蹤記錄和傳輸URL的內部URL是與Tomcat(https://localhost:8080)的直接內部連線。

   * 退信管理：輸入處理退信的參數(請勿使用 **未處理的退回郵件** 區段)。
   * 訪問方：提供兩個URL供報表、Web表單和鏡像頁面使用。

      ![](assets/d_ncs_install_web_url.png)
