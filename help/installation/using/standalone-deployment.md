---
title: 獨立部署
seo-title: 獨立部署
description: 獨立部署
seo-description: null
page-status-flag: never-activated
uuid: 48ce793e-cb9f-4102-898f-758512cb9bf2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 9834638f-a8bb-4969-9f8d-99b8d9fdb1ca
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 6b631f8456ad1f61cec1630334d76752f6af9866

---


# 獨立部署{#standalone-deployment}

此配置包含同一台電腦上的所有元件：

* 應用程式(Web),
* 傳送程式(mta),
* 重新導向程式（追蹤）,
* 工作流程和排程工作(wfserver)、
* 彈回郵件程式(inMail)、
* 統計進程(stat)。

進程之間的整體通信根據以下方案進行：

![](assets/s_900_ncs_install_standaloneconfig.png)

在管理少於100,000個收件者的清單時，以及例如以下軟體層時，可執行此類型的設定：

* Linux、
* Apache、
* PostgreSQL、
* Qmail。

隨著卷的增長，此體系結構的變體將資料庫伺服器移動到另一台電腦，以獲得更好的效能。

>[!NOTE]
>
>如果現有資料庫伺服器有足夠的資源，也可以使用它。

## 功能 {#features}

### 優勢 {#advantages}

* 完全獨立且配置成本低（如果使用下列開放原始碼軟體，則不需要計費授權）。
* 簡化安裝和網路組態。

### 缺點 {#disadvantages}

* 發生事故時的重要電腦。
* 廣播訊息時的頻寬有限（根據我們的經驗，每小時大約有數萬封郵件）。
* 廣播時應用程式可能會變慢。
* 應用程式伺服器必須從外部（例如位於DMZ中）可用，因為它托管重定向伺服器。

## 安裝和配置步驟 {#installation-and-configuration-steps}

### 必要條件 {#prerequisites}

* JDK、
* Web伺服器(IIS、Apache)、
* 訪問資料庫伺服器，
* 可通過POP3訪問的彈回郵箱，
* 建立兩個DNS別名：

   * 第一個是公開曝光，以追蹤並指向其公開IP上的電腦；
   * 第二個別名暴露給內部用戶，用於控制台訪問和指向同一台電腦。

* 防火牆配置為開啟STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL（1521 for Oracle,5432 for PostgreSQL等）埠。 有關詳細資訊，請參閱 [網路配置](../../installation/using/network-configuration.md)。

在以下示例中，實例的參數為：

* 實例的名稱：示 **范**
* DNS掩碼： **console.campaign.net*** （僅用於客戶端控制台連接和報告）
* 資料庫：促銷 **活動：demo@dbsrv**

### 安裝和配置（單台電腦） {#installing-and-configuring--single-machine-}

應用以下步驟：

1. 請依照Adobe Campaign伺服器的安裝程式：Linux上 **的nlserver** 套件，或 **Windows上的setup.exe** 。

   如需詳細資訊，請參 [閱Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)中的促銷活動安裝先決條件和Windows [(Windows)中](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) 的促銷活動安裝先決條件。

1. 在安裝Adobe Campaign伺服器後，請使用命令 **nlserver web -tomcat** （Web模組可讓您在連接埠8080上的獨立Web伺服器模式監聽中啟動Tomcat）來啟動應用程式伺服器(web)，並確保Tomcat正確啟動：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次執行Web模組時，會在安裝資料夾下的 **conf目錄中建立** config-default.xml ******** 和serverConf.xml檔案。 serverConf.xml中可用的所 **有參數** ，都列在本節 [中](../../installation/using/the-server-configuration-file.md)。

   按 **Ctrl+C** 以停止伺服器。

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:服 [務器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 針對Windows:服 [務器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)。

1. 使用 **命令** :

   ```
   nlserver config -internalpassword
   ```

   For more on this, refer to [Internal identifier](../../installation/using/campaign-server-configuration.md#internal-identifier).

1. 使用DNS **遮色片建立** 示範例項 **，以進行追蹤(在本例中為** tracking.campaign.net **)並存取用戶端主控台(在本例中為** console.campaign.net)。 有兩種方法可以做到：

   * 透過主控台建立執行個體：

      ![](assets/install_create_new_connexion.png)

      有關詳細資訊，請參閱 [建立實例和登錄](../../installation/using/creating-an-instance-and-logging-on.md)。

      或

   * 使用命令行建立實例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有關詳細資訊，請參閱 [建立實例](../../installation/using/command-lines.md#creating-an-instance)。

1. 編輯 **-demo.xml** 檔案(在 **config-default.xml**&#x200B;旁的步驟中建立)，並確保 **mta** (傳送， **wfserver,In Mail Mail********** (彈回數和BounceStat)工作流程（啟用統計資訊）的config config和xml進程。 然後配置統計伺服器的地址：

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

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. 編輯 **** serverConf.xml檔案並指定傳送網域，然後指定MTA模組用來回答MX類型DNS查詢的DNS伺服器IP（或主機）位址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **參數** ，僅用於Windows。

   如需詳細資訊，請參閱促銷活 [動伺服器設定](../../installation/using/campaign-server-configuration.md)。

1. 將用戶端設定程式(**setup-client-7.XX**、 **SETUP-client-6.XX** 、 ************ EXEfor v.1)複製至Jayyyyyy的新增/Datakit/Eng/jjsp資料夾。

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:適用於 [Linux的客戶端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 針對Windows:適用於 [Windows的客戶端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

1. 請遵循下列章節所述的Web伺服器整合程式(IIS、Apache):

   * 針對Linux:與Linux [的Web伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 針對Windows:與Windows [版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 啟動網站並使用URL測試重新導向：https://tracking.campaign.net/r/test。

   瀏覽器必須顯示以下訊息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:啟 [動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 針對Windows:啟 [動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器(**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux)，再執行命令 **nlserver pdump** ，以檢查是否存在所有已啟用的模組。

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（適用於Linux）:系 **統mctl啟動nlserver**

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

   此命令也可讓您知道電腦上安裝的Adobe Campaign伺服器版本和組建版本號碼。

1. 使用URL **測試nlserver web** module:https://console.campaign.net/nl/jsp/logon.jsp

   此URL可讓您存取用戶端設定程式的下載頁面。

   在到達 **訪問控制頁** 時輸入內部登錄和關聯密碼。

   ![](assets/s_ncs_install_access_client.png)

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:適用於 [Linux的客戶端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 針對Windows:適用於 [Windows的客戶端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

1. 啟動Adobe Campaign用戶端主控台（從上一個下載頁面或直接在伺服器上啟動以進行Windows安裝），將伺服器連線URL設為https://console.campaign.net，並使用內部登 **入** 。

   請參閱 [建立例項並登入和](../../installation/using/creating-an-instance-and-logging-on.md)[內部識別碼](../../installation/using/campaign-server-configuration.md#internal-identifier)。

   首次登錄時，資料庫建立嚮導將顯示：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   按照嚮導中的步驟建立與連接實例關聯的資料庫。

   有關詳細資訊，請參 [閱建立和配置資料庫](../../installation/using/creating-and-configuring-the-database.md)。

   建立資料庫後，請註銷。

1. 使用管理員登入( **admin** login without a password)重新登入用戶端主控台，並啟動部署精靈( **[!UICONTROL Tools > Advanced]** 功能表)以完成執行個體的設定。

   有關詳細資訊，請參閱 [部署實例](../../installation/using/deploying-an-instance.md)。

   要設定的主要參數如下：

   * 電子郵件傳送：寄件者和回覆位址，以及彈回郵件的錯誤信箱。
   * 追蹤：填入用於重新導向的外部URL和內部URL，按一下追蹤伺服器上的 **Registration** ，然後在追蹤伺服器的 **** demo例項上驗證它。

      For more on this, refer to [Tracking configuration](../../installation/using/deploying-an-instance.md#tracking-configuration).

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由於Adobe Campaign伺服器既是應用程式伺服器又是重新導向伺服器，用來收集追蹤記錄和傳輸URL的內部URL是與Tomcat(https://localhost:8080)的直接內部連線。

   * 彈回數管理：輸入要處理彈回郵件的參數(請勿將「未處理 **彈回郵件** 」區段納入考量)。
   * 存取來源：提供兩個報表URL:Web表單和鏡像頁面。

      ![](assets/d_ncs_install_web_url.png)

