---
title: 企業部署
seo-title: 企業部署
description: 企業部署
seo-description: null
page-status-flag: never-activated
uuid: 2c2b5cef-86cb-4cb5-801a-ca6afeae90bb
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: installation
content-type: reference
topic-tags: deployment-types-
discoiquuid: 066d0ac1-033c-467b-aa6c-43a97ecd8632
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 5f3ceab5ee82587d9f1829792bdabf2209f793cd

---


# 企業部署{#enterprise-deployment}

這是最完整的配置。 它以標準配置為基礎，以提高安全性和可用性：

* 在HTTP或TCP負載平衡器後面提供專用的重新導向伺服器，以提升可擴充性和可用性，
* 兩台應用程式伺服器，用於提高吞吐量和故障轉移能力（容錯），它們在LAN中隔離。

伺服器和進程之間的通用通信根據以下方案進行：

![](assets/s_901_ncs_install_enterpriseconfig.png)

通過這種配置，在適當的頻寬和調整下，預期的吞吐量可以超過每小時100,000封郵件。

## 功能 {#features}

### 優勢 {#advantages}

* 最佳化安全性：只有需要暴露在外部的伺服器才安裝在DMZ的電腦上。
* 高可用性更容易確保：只有從外部看到的電腦才需要考慮高可用性。

### 缺點 {#disadvantages}

硬體和管理成本提高。

### 建議的設備 {#recommended-equipment}

* 應用程式伺服器：2 Ghz四核CPU,4 GB RAM，軟體RAID 1 80 GB SATA硬碟。
* 重定向伺服器：2 Ghz四核CPU,4 GB RAM，軟體RAID 1 80 GB SATA硬碟。

>[!NOTE]
>
>可以重複使用現有的負載平衡器來向重定向伺服器發送流量。

## 安裝和配置步驟 {#installation-and-configuration-steps}

### 必要條件 {#prerequisites}

* JDK在兩個應用程式伺服器上，
* Web伺服器(IIS、Apache)。
* 訪問兩個應用程式伺服器上的資料庫伺服器，
* 可通過POP3訪問的彈回郵箱，
* 在負載平衡器上建立兩個DNS別名：

   * 首次公開用於追蹤並指向虛擬IP位址(VIP)上的負載平衡器，然後散布至兩個正面伺服器，
   * 第二個則暴露給內部使用者，以便透過主控台存取，並指向虛擬IP位址(VIP)上的負載平衡器，然後該負載平衡器會散布至兩個應用程式伺服器。

* 防火牆配置為開啟STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL（1521 for Oracle,5432 for PostgreSQL等）埠。 有關詳細資訊，請參閱「資料庫 [訪問」一節](../../installation/using/network-configuration.md#database-access)。

>[!CAUTION]
>
>如果應用程式伺服器指向單個資料庫實例，則在將標準包導入一個實例後，該包中包含的模式不會載入到另一個實例。
>  
>如果應用程式伺服器指向單個資料庫實例，則在更改一個實例上的模式後，該模式不會載入到另一個實例上。
>
>要恢復這些問題，您需要在第二個發生錯誤的實例上重新啟動「web@default」進程。

### 安裝和配置應用程式伺服器1 {#installing-and-configuring-the-application-server-1}

在以下示例中，實例的參數為：

* 實例的名稱：展示
* DNS掩碼：tracking.campaign.net*, console.campaign.net*（應用程式伺服器會處理用戶端主控台連線和報表的URL，以及鏡像頁面和取消訂閱頁面）
* 語言：英文
* 資料庫：促銷活動：demo@dbsrv

安裝第一台伺服器的步驟如下：

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

   * 針對Linux:服 [務器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 針對Windows:服 [務器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

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

1. 編輯 **config-demo.xml** 檔案(透過 **config-default.xml檔案建立，並位於檔案旁邊)，檢查mta** （傳送） **(WoffServer** ,InMailMailServer（回彈）和ChraidStat(先前啟用的App Stat)統計資料，然後設定The **************** configAppStat統計資料的先前：

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
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
   >nameServer **s** 參數僅用於Windows。

   如需詳細資訊，請參閱促銷活 [動伺服器設定](../../installation/using/campaign-server-configuration.md)。

1. 將用戶端設定程式(**setup-client-7.XX**、 **SETUP-client-6.XX** 、 ************ EXEfor v.1)複製至Jayyyyyy的新增/Datakit/Eng/jjsp資料夾。

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:適用於 [Linux的客戶端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 針對Windows:Windows [的客戶端控制台可用性](../../installation/using/client-console-availability-for-windows.md)。

1. 啟動Adobe Campaign伺服器(**net start nlserver6** in Windows, **/etc/init.d/nlserver6 start** in Linux)，再執行命令 **nlserver pdump** ，以檢查是否存在所有已啟用的模組。

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

1. 使用URL **測試nlserver web** module: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test)。

   此URL可讓您存取用戶端設定程式的下載頁面。

   在到達 **訪問控制頁** 時輸入內部登錄和關聯密碼。

   ![](assets/s_ncs_install_access_client.png)

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:適用於 [Linux的客戶端控制台可用性](../../installation/using/client-console-availability-for-linux.md)
   * 針對Windows:適用於 [Windows的客戶端控制台可用性](../../installation/using/client-console-availability-for-windows.md)

### 安裝和配置應用程式伺服器2 {#installing-and-configuring-the-application-server-2}

應用以下步驟：

1. 安裝Adobe Campaign伺服器。
1. 將您建立之執行個體的檔案複製到應用程式伺服器1。

   我們會保留與應用程式伺服器1相同的例項名稱。

1. 將內 **部變更** 為與應用程式伺服器1相同。
1. 將資料庫連結到實例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 編輯 **config-demo.xml** 檔案(透過 **config-default.xml檔案建立，並位於檔案旁邊)，檢查mta** （傳送） **(WoffServer** ,InMailMailServer（回彈）和ChraidStat(先前啟用的App Stat)統計資料，然後設定The **************** configAppStat統計資料的先前：

   ```
   <?xml version='1.0'?>
   <serverconf>  
     <shared>    
       <!-- add lang="eng" to dataStore to force English for the instance -->    
       <dataStore hosts="tracking.campaign.net*,console.campaign.net*">      
         <mapping logical="*" physical="default"/>    
       </dataStore>  </shared>  
       <mta autoStart="true" statServerAddress="app">
       <wfserver autoStart="true"/>  
       <inMail autoStart="true"/>  
       <sms autoStart="false"/>  
       <listProtect autoStart="false"/>
   </serverconf>
   ```

   For more on this, refer to [Enabling processes](../../installation/using/campaign-server-configuration.md#enabling-processes).

1. 編輯 **serverConf.xml檔案** ，並填充MTA模組的DNS配置：

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >nameServers **參數** ，僅用於Windows。

   如需詳細資訊，請參閱促銷活 [動伺服器設定](../../installation/using/campaign-server-configuration.md)。

1. 啟動Adobe Campaign伺服器。

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:服 [務器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 針對Windows:服 [務器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 安裝和配置前端伺服器 {#installing-and-configuring-the-frontal-servers}

安裝和配置過程在兩台電腦上都相同。

步驟如下：

1. 安裝Adobe Campaign伺服器、
1. 符合下列章節所述的Web伺服器整合程式(IIS、Apache):

   * 針對Linux:與 [Linux的Web伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md),
   * 針對Windows:與 [Windows版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md)。

1. 複製 **安裝期間建立的config-demo.xml****和serverConf.xml** 檔案。 在 **config-demo.xml檔案中，啟用** config-demo.xml **進程並停用trackinglogd** 進程，並停用 **ta**、inmail、wserver ************ fserver和Stat進程。
1. 編輯 **serverConf.xml檔案** ，並在重新導向的參數中填入冗餘追蹤伺服器：

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 啟動網站並測試從URL的重新導向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   瀏覽器應顯示下列訊息（視負載平衡器所重新導向的URL而定）:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:啟 [動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * 針對Windows:啟 [動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)。

1. 啟動Adobe Campaign伺服器。

