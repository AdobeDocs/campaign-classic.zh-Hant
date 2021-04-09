---
solution: Campaign Classic
product: campaign
title: 獨立部署
description: 獨立部署
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 3%

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
* Apache,
* PostgreSQL,
* Qmail。

隨著卷的增長，此體系結構的變體將資料庫伺服器移動到另一台電腦，以獲得更好的效能。

>[!NOTE]
>
>如果現有資料庫伺服器有足夠的資源，也可以使用它。

## 功能{#features}

### 優勢{#advantages}

* 完全獨立且配置成本低（如果使用下列開放原始碼軟體，則不需要計費授權）。
* 簡化安裝和網路組態。

### 缺點{#disadvantages}

* 發生事故時的重要電腦。
* 廣播訊息時的頻寬有限（根據我們的經驗，每小時大約有數萬封郵件）。
* 廣播時應用程式可能會變慢。
* 應用程式伺服器必須從外部（例如位於DMZ中）可用，因為它托管重定向伺服器。

## 安裝和配置步驟{#installation-and-configuration-steps}

### 必要條件 {#prerequisites}

* JDK、
* Web伺服器(IIS、Apache)、
* 訪問資料庫伺服器，
* 可通過POP3訪問的彈回郵箱，
* 建立兩個DNS別名：

   * 第一個是公開曝光，以追蹤並指向其公開IP上的電腦；
   * 第二個別名暴露給內部用戶，用於控制台訪問和指向同一台電腦。

* 防火牆配置為開啟SMTP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521 forOracle,5432 for PostgreSQL等) 埠。 有關詳細資訊，請參閱[網路配置](../../installation/using/network-configuration.md)。

在以下示例中，實例的參數為：

* 實例的名稱：**demo**
* DNS掩碼：**console.campaign.net***（僅用於客戶端控制台連接和報告）
* 資料庫：**campaign:demo@dbsrv**

### 安裝和配置（單台電腦）{#installing-and-configuring--single-machine-}

應用以下步驟：

1. 按照Adobe Campaign伺服器的安裝過程操作：**nlserver**&#x200B;套件（在Linux上）或&#x200B;**setup.exe**（在Windows上）。

   有關詳細資訊，請參閱[Linux中促銷活動安裝的先決條件(Linux)和[Windows中促銷活動安裝的先決條件(Windows)。](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)

1. 安裝Adobe Campaign伺服器後，使用命令&#x200B;**nlserver web -tomcat**&#x200B;啟動應用程式伺服器(Web)（Web模組使您能夠在埠8080上的獨立Web伺服器模式偵聽中啟動Tomcat），並確保Tomcat正確啟動：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次執行Web模組時，它會在安裝資料夾下的&#x200B;**conf**&#x200B;目錄下建立&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;檔案。 **serverConf.xml**&#x200B;中的所有可用參數都列在[部分](../../installation/using/the-server-configuration-file.md)中。

   按&#x200B;**Ctrl+C**&#x200B;以停止伺服器。

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:[伺服器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 針對Windows:[伺服器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)。

1. 使用以下命令更改&#x200B;**internal**&#x200B;口令：

   ```
   nlserver config -internalpassword
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 使用DNS遮罩建立&#x200B;**demo**&#x200B;例項以進行追蹤（在本例中為&#x200B;**tracking.campaign.net**），並存取用戶端主控台（在本例中為&#x200B;**console.campaign.net**）。 有兩種方法可以做到：

   * 透過主控台建立執行個體：

      ![](assets/install_create_new_connexion.png)

      有關詳細資訊，請參閱[建立實例並登錄](../../installation/using/creating-an-instance-and-logging-on.md)。

      或

   * 使用命令行建立實例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有關詳細資訊，請參閱[建立實例](../../installation/using/command-lines.md#creating-an-instance)。

1. 編輯&#x200B;**config-demo.xml**&#x200B;檔案（在上一步驟中建立於&#x200B;**config-default.xml**&#x200B;旁），並確定&#x200B;**mta**（傳送）、**wfserver**（工作流程）、**inMail**（彈回數）和a10/>stat **（統計）進程被啟用。**&#x200B;然後配置統計伺服器的地址：

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

1. 編輯&#x200B;**serverConf.xml**&#x200B;檔案並指定傳送網域，然後指定MTA模組用來回答MX類型DNS查詢的DNS伺服器IP（或主機）位址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers**&#x200B;參數僅用於Windows。

   如需詳細資訊，請參閱[促銷活動伺服器組態](../../installation/using/configuring-campaign-server.md)。

1. 將用戶端主控台設定程式（v7或&#x200B;**setup-client-6.XX**,v6.1的&#x200B;**setup-client-7.XX**, **/datakit/>,**/datakit/）複製至&#x200B;**/nl/eng/jsp**&#x200B;資料夾。 ****[進一步瞭解](../../installation/using/client-console-availability-for-windows.md)。

1. 請遵循下列章節所述的Web伺服器整合程式(IIS、Apache):

   * 針對Linux:[與Linux的Web伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 針對Windows:[與Windows版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 啟動網站並使用URL測試重新導向：https://tracking.campaign.net/r/test。

   瀏覽器必須顯示以下訊息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:[啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 針對Windows:[啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器(在Windows中&#x200B;**net start nlserver6**，在Linux中&#x200B;**/etc/init.d/nlserver6 start**)，並再次運行命令&#x200B;**nlserver pdump**&#x200B;以檢查是否存在所有已啟用的模組。

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（適用於Linux）:**systemmctl start nlserver**

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

   此命令還可讓您瞭解安裝在電腦上的Adobe Campaign伺服器的版本和內部版本號。

1. 使用URL測試&#x200B;**nlserver web**&#x200B;模組：https://console.campaign.net/nl/jsp/logon.jsp

   此URL可讓您存取用戶端設定程式的下載頁面。

   當您到達訪問控制頁時，輸入&#x200B;**internal**&#x200B;登錄和相關密碼。 [進一步瞭解](../../installation/using/client-console-availability-for-windows.md)。

   ![](assets/s_ncs_install_access_client.png)

1. 啟動Adobe Campaign客戶端控制台（從上一個下載頁面啟動或直接在伺服器上啟動Windows安裝），將伺服器連接URL設定為https://console.campaign.net，並使用&#x200B;**internal**&#x200B;登錄進行連接。

   請參閱[本頁](../../installation/using/creating-an-instance-and-logging-on.md)和[本節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

   首次登錄時，資料庫建立嚮導將顯示：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   按照嚮導中的步驟建立與連接實例關聯的資料庫。

   有關詳細資訊，請參閱[建立和配置資料庫](../../installation/using/creating-and-configuring-the-database.md)。

   建立資料庫後，請註銷。

1. 使用&#x200B;**admin**&#x200B;登入功能，不使用密碼重新登入用戶端主控台，並啟動部署精靈（**[!UICONTROL Tools > Advanced]**&#x200B;功能表）以完成執行個體的設定。

   有關詳細資訊，請參閱[部署實例](../../installation/using/deploying-an-instance.md)。

   要設定的主要參數如下：

   * 電子郵件傳送：寄件者和回覆位址，以及彈回郵件的錯誤信箱。
   * 追蹤：填入用於重新導向的外部URL和內部URL，按一下追蹤伺服器&#x200B;**上的「註冊」，然後在追蹤伺服器的** demo **例項上驗證它。**

      有關詳細資訊，請參閱[跟蹤配置](../../installation/using/deploying-an-instance.md#tracking-configuration)。

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由於Adobe Campaign伺服器同時用作應用程式伺服器和重定向伺服器，用於收集跟蹤日誌和傳輸URL的內部URL是與Tomcat(https://localhost:8080)的直接內部連接。

   * 彈回數管理：輸入要處理彈回郵件的參數（請勿將&#x200B;**未處理彈回郵件**&#x200B;區段納入考量）。
   * 存取來源：提供兩個報表URL:Web表單和鏡像頁面。

      ![](assets/d_ncs_install_web_url.png)
