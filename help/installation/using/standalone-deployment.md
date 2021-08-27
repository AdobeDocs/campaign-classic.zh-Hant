---
product: campaign
title: 獨立部署
description: 獨立部署
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 194366ab-fd9f-4431-9163-ae16c1f96db2
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 3%

---

# 獨立部署{#standalone-deployment}

![](../../assets/v7-only.svg)

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

### 先決條件 {#prerequisites}

* JDK、
* Web伺服器(IIS、Apache),
* 訪問資料庫伺服器，
* 可通過POP3訪問的退回郵箱，
* 建立兩個DNS別名：

   * 第一個向公眾公開，用於跟蹤並指向其公共IP上的電腦；
   * 向內部用戶公開的第二個別名，用於訪問控制台並指向同一台電腦。

* 防火牆配置為開啟SMTP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521(Oracle)、5432(PostgreSQL)等 埠。 有關詳細資訊，請參閱[網路配置](../../installation/using/network-configuration.md)。

在下列範例中，例項的參數為：

* 執行個體的名稱：**demo**
* DNS掩碼：**console.campaign.net***（僅用於用戶端主控台連線和報表）
* 資料庫：**campaign:demo@dbsrv**

### 安裝和配置（單台電腦） {#installing-and-configuring--single-machine-}

應用以下步驟：

1. 請依照Adobe Campaign伺服器的安裝程式操作：Linux上的&#x200B;**nlserver**&#x200B;軟體包或Windows上的&#x200B;**setup.exe**。

   如需詳細資訊，請參閱[在Linux](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)(Linux)中安裝Campaign的必要條件和[在Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)(Windows)中安裝Campaign的必要條件。

1. 安裝Adobe Campaign伺服器後，使用命令&#x200B;**nlserver web -tomcat**&#x200B;啟動應用程式伺服器(web)（Web模組允許您在埠8080上的獨立Web伺服器模式偵聽中啟動Tomcat），並確保Tomcat正確啟動：

   ```
   12:08:18 >   Application server for Adobe Campaign Classic (7.X YY.R build XXX@SHA1) of DD/MM/YYYY
   12:08:18 >   Starting Web server module (pid=28505, tid=-1225184768)...
   12:08:18 >   Tomcat started
   12:08:18 >   Server started
   ```

   >[!NOTE]
   >
   >首次執行Web模組時，它會在安裝資料夾下的&#x200B;**conf**&#x200B;目錄中建立&#x200B;**config-default.xml**&#x200B;和&#x200B;**serverConf.xml**&#x200B;檔案。 **serverConf.xml**&#x200B;中所有可用的參數都列在此[節](../../installation/using/the-server-configuration-file.md)中。

   按&#x200B;**Ctrl+C**&#x200B;以停止伺服器。

   如需詳細資訊，請參閱下列章節：

   * Linux:[伺服器的首次啟動](../../installation/using/installing-packages-with-linux.md#first-start-up-of-the-server),
   * 對於Windows:[伺服器的首次啟動](../../installation/using/installing-the-server.md#first-start-up-of-the-server)。

1. 使用命令更改&#x200B;**internal**&#x200B;密碼：

   ```
   nlserver config -internalpassword
   ```

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 使用DNS遮罩建立&#x200B;**demo**&#x200B;例項，以便追蹤（在此例中為&#x200B;**tracking.campaign.net**）和存取用戶端主控台（在此例中為&#x200B;**console.campaign.net**）。 執行此作業有兩種方式：

   * 透過主控台建立執行個體：

      ![](assets/install_create_new_connexion.png)

      有關詳細資訊，請參閱[建立實例並登錄](../../installation/using/creating-an-instance-and-logging-on.md)。

      或

   * 使用命令行建立實例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*,console.campaign.net*
      ```

      有關詳細資訊，請參閱[建立實例](../../installation/using/command-lines.md#creating-an-instance)。

1. 編輯&#x200B;**config-demo.xml**&#x200B;檔案（在上一步建立，位於&#x200B;**config-default.xml**&#x200B;旁邊），並確保&#x200B;**mta**（傳送）、**wfserver**（工作流）、**inMail**（退信郵件）和&#x200B;**a11/>（統計資訊）進程已啟用。**&#x200B;然後配置統計伺服器的地址：

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

1. 編輯&#x200B;**serverConf.xml**&#x200B;檔案並指定傳送網域，然後指定MTA模組用來回答MX類型DNS查詢的DNS伺服器的IP（或主機）地址。

   ```
   <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
   ```

   >[!NOTE]
   >
   >**nameServers**&#x200B;參數僅用於Windows。

   如需詳細資訊，請參閱[Campaign伺服器設定](../../installation/using/configuring-campaign-server.md)。

1. 將客戶端控制台安裝程式（**setup-client-7.XX**、v7的&#x200B;**YYYY.exe**&#x200B;或&#x200B;**setup-client-6.XX**、v6.1的&#x200B;**YYYY.exe**）複製到&#x200B;**/datakit/nl/eng/jsp/**&#x200B;資料夾。 [深入瞭解](../../installation/using/client-console-availability-for-windows.md)。

1. 按照以下各節所述的Web伺服器整合過程(IIS、Apache)操作：

   * Linux:[整合至Linux的Web伺服器](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 對於Windows:[整合至Windows適用的Web伺服器](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 啟動網站並使用URL測試重新導向：https://tracking.campaign.net/r/test。

   瀏覽器必須顯示下列訊息：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="localhost"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * Linux:[啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 對於Windows:[啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器(**net start nlserver6**，在Windows中，**/etc/init.d/nlserver6 start**)，再次運行命令&#x200B;**nlserver pdump**&#x200B;以檢查是否存在所有已啟用的模組。

   >[!NOTE]
   >
   >從20.1開始，建議改用下列命令（Linux適用）:**systemctl啟動nlserver**

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

1. 使用URL測試&#x200B;**nlserver web**&#x200B;模組：https://console.campaign.net/nl/jsp/logon.jsp

   此URL可讓您存取用戶端設定程式的下載頁面。

   進入訪問控制頁時，輸入&#x200B;**內部**&#x200B;登錄和相關密碼。 [深入瞭解](../../installation/using/client-console-availability-for-windows.md)。

   ![](assets/s_ncs_install_access_client.png)

1. 啟動Adobe Campaign用戶端主控台（從上一個下載頁面啟動，或直接在伺服器上啟動以進行Windows安裝），將伺服器連線URL設為https://console.campaign.net ，並使用&#x200B;**內部**&#x200B;登入進行連線。

   請參閱[此頁面](../../installation/using/creating-an-instance-and-logging-on.md)和[此區段](../../installation/using/configuring-campaign-server.md#internal-identifier)。

   第一次登錄時，資料庫建立嚮導將出現：

   ![](assets/s_ncs_install_db_oracle_creation01.png)

   請依照精靈中的步驟操作，並建立與連線執行個體相關聯的資料庫。

   有關詳細資訊，請參閱[建立和配置資料庫](../../installation/using/creating-and-configuring-the-database.md)。

   建立資料庫後，請註銷。

1. 不使用密碼使用&#x200B;**admin**&#x200B;登入重新登入用戶端主控台，然後啟動部署精靈（**[!UICONTROL Tools > Advanced]**&#x200B;功能表）以完成執行個體的設定。

   有關詳細資訊，請參閱[部署執行個體](../../installation/using/deploying-an-instance.md)。

   要設定的主要參數如下：

   * 電子郵件傳送：退回郵件的寄件者和回覆地址及錯誤信箱。
   * 追蹤：填入用於重新導向的外部URL和內部URL，按一下追蹤伺服器&#x200B;**上的**&#x200B;註冊，然後在追蹤伺服器的&#x200B;**demo**&#x200B;例項上驗證。

      如需詳細資訊，請參閱[追蹤設定](../../installation/using/deploying-an-instance.md#tracking-configuration)。

      ![](assets/s_ncs_install_deployment_wiz_09.png)

      由於Adobe Campaign伺服器同時作為應用程式伺服器和重新導向伺服器，因此用於收集追蹤記錄和傳輸URL的內部URL是與Tomcat(https://localhost:8080)的直接內部連線。

   * 退信管理：輸入用於處理退信的參數（不要考慮&#x200B;**未處理退信郵件**&#x200B;部分）。
   * 訪問方：提供兩個URL供報表、Web表單和鏡像頁面使用。

      ![](assets/d_ncs_install_web_url.png)
