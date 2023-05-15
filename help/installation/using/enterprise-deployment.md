---
product: campaign
title: 企業部署
description: 企業部署
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 38c14010-203a-47ab-b23d-6f431dab9a88
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1221'
ht-degree: 3%

---

# 企業部署{#enterprise-deployment}



這是最完整的設定。 它以標準配置為基礎，提供更高的安全性和可用性：

* 在HTTP或TCP負載平衡器後面的專用重定向伺服器，以實現可擴充性和可用性，
* 兩個應用程式伺服器，用於改進吞吐量和故障轉移能力（容錯），它們在LAN中隔離。

伺服器和進程之間的一般通信根據以下模式執行：

![](assets/s_901_ncs_install_enterpriseconfig.png)

使用這種類型的配置，預期的吞吐量可以超過每小時100,000封郵件，並有適當的頻寬和調整。

## 功能 {#features}

### 優勢 {#advantages}

* 優化的安全性：DMZ中的電腦上只安裝需要向外部公開的伺服器。
* 高可用性更易於確保：只有從外部可見的電腦才需要管理，同時考慮到高可用性。

### 缺點 {#disadvantages}

硬體和管理成本更高。

### 推薦設備 {#recommended-equipment}

* 應用程式伺服器：2 Ghz四核CPU,4 GB RAM，軟體RAID 1 80 GB SATA硬碟。
* 重定向伺服器：2 Ghz四核CPU,4 GB RAM，軟體RAID 1 80 GB SATA硬碟。

>[!NOTE]
>
>可以對到重定向伺服器的流量重複使用現有負載平衡器。

## 安裝和配置步驟 {#installation-and-configuration-steps}

### 必要條件 {#prerequisites}

* 兩個應用程式伺服器上的JDK,
* 兩個前端上的Web伺服器(IIS、Apache),
* 訪問兩個應用程式伺服器上的資料庫伺服器，
* 可通過POP3訪問的退回郵箱，
* 在負載平衡器上建立兩個DNS別名：

   * 首先公開，用於追蹤並指向虛擬IP位址(VIP)上的負載平衡器，然後分配給兩個前端伺服器，
   * 第二個向內部用戶公開，以便通過控制台訪問，並指向虛擬IP地址(VIP)上的負載平衡器，然後該負載平衡器分發給兩個應用伺服器。

* 防火牆配置為開啟STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521(Oracle)、5432(PostgreSQL)等 埠。 如需詳細資訊，請參閱區段 [資料庫存取](../../installation/using/network-configuration.md#database-access).

>[!CAUTION]
>
>如果應用程式伺服器指向單個資料庫實例，在一個實例上導入標準包之後，包中包含的架構不會載入到另一個實例上。
>  
>如果應用程式伺服器指向單個資料庫實例，則更改一個實例上的架構後，該架構不會載入到另一個實例上。
>
>要恢復這些問題，您需要在發生錯誤的第二個實例上重新啟動「web@default」進程。

### 安裝和配置應用程式伺服器1 {#installing-and-configuring-the-application-server-1}

在下列範例中，例項的參數為：

* 執行個體的名稱：示範
* DNS掩碼：tracking.campaign.net&#42;, console.campaign.net&#42; （應用程式伺服器處理客戶端控制台連接和報告以及鏡像頁面和取消訂閱頁面的URL）
* 語言：英文
* 資料庫：campaign:demo@dbsrv

安裝第一個伺服器的步驟如下：

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

   * Linux: [伺服器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 對於Windows: [伺服器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

1. 變更 **內部** 使用命令輸入密碼：

   ```
   nlserver config -internalpassword
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 建立 **示範** 具有用於追蹤之DNS遮罩的例項(在此例中， **tracking.campaign.net**)和用戶端主控台的存取權(在此例中， **console.campaign.net**)。 執行此作業有兩種方式：

   * 透過主控台建立執行個體：

      ![](assets/install_create_new_connexion.png)

      有關詳細資訊，請參閱 [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).

      或

   * 使用命令行建立實例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有關詳細資訊，請參閱 [建立例項](../../installation/using/command-lines.md#creating-an-instance).

1. 編輯 **config-demo.xml** 檔案(通過上一個命令建立，位於 **config-default.xml** 檔案)，檢查 **mta** （傳遞）, **wfserver** （工作流程）, **inMail** （反彈郵件）和 **stat** （統計資料）程式，然後設定 **應用程式** 統計伺服器：

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

1. 測試 **nlserver web** 模組（使用URL）: [https://console.campaign.net/nl/jsp/logon.jsp](https://tracking.campaign.net/r/test).

   此URL可讓您存取用戶端設定程式的下載頁面。 [了解更多](../../installation/using/client-console-availability-for-windows.md)。

   輸入 **內部** 進入存取控制頁面時，登入和相關密碼。

   ![](assets/s_ncs_install_access_client.png)

### 安裝和配置應用程式伺服器2 {#installing-and-configuring-the-application-server-2}

應用以下步驟：

1. 安裝Adobe Campaign伺服器。
1. 將您建立的實例的檔案複製到應用程式伺服器1。

   我們會保留與應用程式伺服器1相同的執行個體名稱。

1. 變更 **內部** 與應用程式伺服器1相同。
1. 將資料庫連結到實例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 編輯 **config-demo.xml** 檔案(通過上一個命令建立，位於 **config-default.xml** 檔案)，檢查 **mta** （傳遞）, **wfserver** （工作流程）, **inMail** （反彈郵件）和 **stat** （統計資料）程式，然後設定 **應用程式** 統計伺服器：

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

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 編輯 **serverConf.xml** 檔案，並填入MTA模組的DNS設定：

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >此 **nameServers** 參數僅用於Windows。

   有關詳細資訊，請參閱 [Campaign伺服器設定](../../installation/using/configuring-campaign-server.md).

1. 啟動Adobe Campaign伺服器。

   如需詳細資訊，請參閱下列章節：

   * Linux: [伺服器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)
   * 對於Windows: [伺服器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)

### 安裝和配置前端伺服器 {#installing-and-configuring-the-frontal-servers}

安裝和配置過程在兩台電腦上都相同。

步驟如下：

1. 安裝Adobe Campaign伺服器，
1. 遵守以下章節所述的Web伺服器整合程式(IIS、Apache):

   * Linux: [與Linux網頁伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md),
   * 對於Windows: [與Windows版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md).

1. 複製 **config-demo.xml** 和 **serverConf.xml** 安裝期間建立的檔案。 在 **config-demo.xml** 檔案，激活 **trackinglogd** 處理和停用 **mta**, **inmail**, **wfserver** 和 **stat** 程式。
1. 編輯 **serverConf.xml** 檔案，並在重新導向的參數中填入備援追蹤伺服器：

   ```
   <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
   <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
   ```

1. 啟動網站並從URL測試重新導向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)

   瀏覽器應顯示下列訊息（視負載平衡器重新導向的URL而定）:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * Linux: [啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration),
   * 對於Windows: [啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration).

1. 啟動Adobe Campaign伺服器。
