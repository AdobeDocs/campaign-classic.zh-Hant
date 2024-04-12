---
product: campaign
title: 獨立部署
description: 獨立部署
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 3%

---

# 獨立部署{#standalone-deployment}



此設定包含相同電腦上的所有元件：

* 應用程式流程（網頁）、
* 傳遞過程(mta)，
* 重新導向程式（追蹤），
* 工作流程程式與排程工作(wfserver)，
* 退回郵件程式(inMail)，
* 統計處理(stat)。

程式之間的整體通訊是根據以下結構描述執行的：

![](assets/s_900_ncs_install_standaloneconfig.png)

此類設定可在管理少於100,000位收件者的清單時執行，並包含下列軟體層：

* Linux、
* Apache，
* PostgreSQL、
* Qmail。

隨著磁碟區成長，此架構的變體會將資料庫伺服器移至另一部電腦，以獲得更優異的效能。

>[!NOTE]
>
>如果現有資料庫伺服器有足夠的資源，也可以使用。

## 功能 {#features}

### 優點 {#advantages}

* 完全獨立且低設定成本（若使用下列開放原始碼軟體，則不需要付費授權）。
* 簡化安裝及網路設定。

### 缺點 {#disadvantages}

* 發生事件的重要電腦。
* 廣播郵件時頻寬有限（根據我們的經驗，大約每小時有數萬封郵件）。
* 廣播時應用程式速度可能變慢。
* 應用程式伺服器必須可從外部使用（例如位於DMZ時），因為它裝載了重新導向伺服器。

## 安裝和設定步驟 {#installation-and-configuration-steps}

### 先決條件 {#prerequisites}

* JDK、
* 網頁伺服器(IIS、Apache)、
* 存取資料庫伺服器，
* 可透過POP3存取的彈回信箱，
* 建立兩個DNS別名：

   * 首次公開給大眾使用公開IP追蹤及指向電腦；
   * 向內部使用者公開的第二個別名，用於主控台存取並指向相同的電腦。

* 防火牆已設定為開啟SMTP (25)、DNS (53)、HTTP (80)、HTTPS (443)、SQL (1521用於Oracle、5432用於PostgreSQL等) 連線埠。 如需詳細資訊，請參閱 [網路設定](../../installation/using/network-configuration.md).

在下列範例中，例項的引數為：

* 執行個體的名稱： **示範**
* DNS遮罩： **console.campaign.net&#42;** （僅適用於使用者端主控台連線和報表）
* 資料庫： **campaign：demo@dbsrv**

### 安裝和設定（單一電腦） {#installing-and-configuring--single-machine-}

應用以下步驟：

1. 請依照Adobe Campaign伺服器的安裝程式進行： **nlserver** package on Linux或 **setup.exe** 在Windows上。

   有關詳細資訊，請參閱 [在Linux安裝Campaign的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)和 [在Windows安裝Campaign的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)。

1. 安裝Adobe Campaign伺服器後，請使用命令啟動應用程式伺服器（網頁） **nlserver web -tomcat** （Web模組可讓您以獨立Web伺服器模式在連線埠8080上接聽，啟動Tomcat），並確保Tomcat正確啟動：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >第一次執行Web模組時，會建立 **config-default.xml** 和 **serverConf.xml** 中的檔案 **conf** 目錄（在安裝資料夾下）。 所有引數都可在 **serverConf.xml** 列於此 [區段](../../installation/using/the-server-configuration-file.md).

   按下 **Ctrl+C** 停止伺服器。

   如需詳細資訊，請參閱下列章節：

   * 針對Linux： [伺服器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server)，
   * 對於Windows： [伺服器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server).

1. 變更 **內部** 使用命令的密碼：

   ```
   nlserver config -internalpassword
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 建立 **示範** 具有DNS遮罩以追蹤的例項(在此案例中， **tracking.campaign.net**)和使用者端主控台的存取權(在此案例中， **console.campaign.net**)。 有兩種方法可以達成此目的：

   * 透過主控台建立執行個體：

     ![](assets/install_create_new_connexion.png)

     有關詳細資訊，請參閱 [建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md).

     或

   * 使用命令列建立例證：

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
     ```

     有關詳細資訊，請參閱 [建立執行個體](../../installation/using/command-lines.md#creating-an-instance).

1. 編輯 **config-demo.xml** 檔案(在前一個步驟中建立且位於 **config-default.xml**)並確定 **mta** （傳遞）， **wfserver** （工作流程）， **inMail** （退回郵件）和 **stat** （統計）處理作業已啟用。 然後設定統計資料伺服器的位址：

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

1. 編輯 **serverConf.xml** 檔案並指定傳遞網域，然後指定MTA模組用於回應MX型別DNS查詢之DNS伺服器的IP （或主機）位址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >此 **nameServer** 引數僅用於Windows。

   有關詳細資訊，請參閱 [Campaign伺服器設定](../../installation/using/configuring-campaign-server.md).

1. 複製使用者端主控台安裝程式 **setup-client-7.XXX.exe** 至 **/datakit/nl/eng/jsp** 資料夾。 [了解更多](../../installation/using/client-console-availability-for-windows.md)。

1. 請依照下列各節中說明的Web伺服器整合程式(IIS、Apache)操作：

   * 針對Linux： [與Linux網頁伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 對於Windows： [與Windows版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 使用URL啟動網站並測試重新導向： https://tracking.campaign.net/r/test。

   瀏覽器必須顯示下列訊息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * 針對Linux： [啟動Web伺服器並測試設定](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 對於Windows： [啟動Web伺服器並測試設定](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器(**網路啟動nlserver6** 在Windows， **/etc/init.d/nlserver6開始** （在Linux中）並執行指令 **nlserver pdump** 再次檢查所有已啟用的模組是否存在。

   >[!NOTE]
   >
   >從20.1版開始，建議您改用下列命令（適用於Linux）： **systemctl啟動nlserver**

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

   此命令也可讓您知道電腦上安裝的Adobe Campaign伺服器的版本和版本編號。

1. 測試 **nlserver web** 使用URL的模組： https://console.campaign.net/nl/jsp/logon.jsp

   此URL可讓您存取使用者端安裝程式的下載頁面。

   輸入 **內部** 存取控制頁面時的登入及相關密碼。 [了解更多](../../installation/using/client-console-availability-for-windows.md)。

   ![](assets/s_ncs_install_access_client.png)

1. 啟動Adobe Campaign使用者端主控台（從先前的下載頁面，或直接在伺服器上針對Windows安裝啟動），將伺服器連線URL設定為https://console.campaign.net ，並使用連線 **內部** 登入。

   請參閱 [此頁面](../../installation/using/creating-an-instance-and-logging-on.md) 和 [本節](../../installation/using/configuring-campaign-server.md#internal-identifier).

   第一次登入時，會顯示資料庫建立精靈：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   請依照精靈中的步驟，建立與連線執行處理關聯的資料庫。

   有關詳細資訊，請參閱 [建立和設定資料庫](../../installation/using/creating-and-configuring-the-database.md).

   建立資料庫之後，請登出。

1. 使用重新登入使用者端主控台 **管理員** 不使用密碼登入並啟動部署精靈( **[!UICONTROL Tools > Advanced]** 功能表)，以完成執行個體的設定。

   有關詳細資訊，請參閱 [部署執行個體](../../installation/using/deploying-an-instance.md).

   要設定的主要引數如下：

   * 電子郵件傳遞：寄件者和回覆地址，以及退回郵件的錯誤信箱。
   * 追蹤：填入用於重新導向的外部URL和內部URL，按一下 **在追蹤伺服器上註冊** 然後在驗證 **示範** 追蹤伺服器的例項。

     有關詳細資訊，請參閱 [追蹤設定](../../installation/using/deploying-an-instance.md#tracking-configuration).

     ![](assets/s_ncs_install_deployment_wiz_09.png)

     由於Adobe Campaign伺服器同時作為應用程式伺服器和重新導向伺服器使用，因此用於收集追蹤記錄和傳輸URL的內部URL是與Tomcat的直接內部連線(https://localhost:8080)。

   * 退回管理：輸入引數以處理退回郵件(請勿採用 **未處理的退回郵件** 區段放入考量)。
   * 存取來源：提供報表、網路表單及映象頁面的兩個URL。

     ![](assets/d_ncs_install_web_url.png)
