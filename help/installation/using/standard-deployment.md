---
product: campaign
title: 標準部署
description: 標準部署
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
source-git-commit: 0fba6a2ad4ffa864e2f726f241aa9d7cd39072a6
workflow-type: tm+mt
source-wordcount: '836'
ht-degree: 3%

---

# 標準部署{#standard-deployment}



對於此設定，需要三部電腦：

* LAN內部的應用程式伺服器，適用於一般使用者（準備行銷活動、報告等）；
* DMZ中的兩個前端伺服器位於負載平衡器後面。

DMZ中的兩部伺服器可處理追蹤、映象頁面及傳送，並具備備援功能，提供高可用性。

LAN中的應用程式伺服器為一般使用者提供服務，並執行所有循環程式（工作流程引擎）。 因此，當前端伺服器達到尖峰負載時，應用程式使用者不受影響。

資料庫伺服器可以在這三部電腦以外的其他電腦上託管。 否則，只要Adobe Campaign （Linux或Windows）支援作業系統，應用程式伺服器和資料庫伺服器就會在LAN內共用相同的電腦。

伺服器與處理序之間的一般通訊會根據以下結構描述執行：

![](assets/s_001_ncs_install_standardconfig.png)

由於資料庫伺服器（以及可用的頻寬）是主要限制因素，因此這種設定型別可以處理大量收件者（500,000到1,000,000）。

## 功能 {#features}

### 優點 {#advantages}

* 容錯移轉功能：可在另一部電腦發生硬體問題時，將處理作業切換至另一部電腦。
* 整體效能更佳，因為MTA和重新導向功能可部署在負載平衡器後的兩部電腦上。 有了兩個作用中的MTA和足夠的頻寬，每小時就可能達到100,000封郵件的廣播速率。

## 安裝和設定步驟 {#installation-and-configuration-steps}

### 先決條件 {#prerequisites}

* 所有三部電腦均使用JDK，
* 位於兩個前端的網頁伺服器(IIS、Apache)，
* 存取所有三部電腦上的資料庫伺服器，
* 可透過POP3存取的彈回信箱，
* 建立兩個DNS別名：

   * 第一個公開給大眾用於追蹤和指向虛擬IP位址(VIP)上的負載平衡器，然後分發給兩個前端伺服器，
   * 第二個透過主控台向內部使用者公開，以存取並指向相同的應用程式伺服器。

* 防火牆已設定為開啟STMP (25)、DNS (53)、HTTP (80)、HTTPS (443)、SQL (1521 (Oracle)、5432 (PostgreSQL)等) 連線埠。 如需進一步資訊，請參閱區段[資料庫存取](../../installation/using/network-configuration.md#database-access)。

### 安裝應用程式伺服器 {#installing-the-application-server}

請依照步驟從Adobe Campaign應用程式伺服器安裝獨立執行個體以建立資料庫（步驟12）。 請參閱[安裝和設定（單一電腦）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

由於電腦不是追蹤伺服器，請勿將與Web伺服器的整合列入考量。

在下列範例中，例項的引數為：

* 執行個體的名稱： **示範**
* DNS遮罩： **console.campaign.net&#42;** （僅適用於使用者端主控台連線和報表）
* 語言：英文
* 資料庫： **行銷活動：demo@dbsrv**

### 安裝兩個前端伺服器 {#installing-the-two-frontal-servers}

兩部電腦上的安裝及設定程式相同。

步驟如下：

1. 安裝Adobe Campaign伺服器。

   如需詳細資訊，請參閱[在Linux安裝Campaign的必要條件](../../installation/using/prerequisites-of-campaign-installation-in-linux.md) (Linux)以及[在Windows](../../installation/using/prerequisites-of-campaign-installation-in-windows.md) (Windows)安裝Campaign的必要條件。

1. 請依照下列各節中說明的Web伺服器整合程式(IIS、Apache)操作：

   * 針對Linux： [與Linux網頁伺服器的整合](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 針對Windows： [整合至Windows的Web伺服器](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 建立&#x200B;**示範**&#x200B;執行個體。 有兩種方法可以達成此目的：

   * 透過主控台建立執行個體：

     ![](assets/install_create_new_connexion.png)

     如需詳細資訊，請參閱[建立執行個體並登入](../../installation/using/creating-an-instance-and-logging-on.md)。

     或

   * 使用命令列建立例證：

     ```
     nlserver config -addinstance:demo/tracking.campaign.net*
     ```

     如需詳細資訊，請參閱[建立執行個體](../../installation/using/command-lines.md#creating-an-instance)。

   執行個體的名稱與應用程式伺服器的名稱相同。

   將會從負載平衡器(tracking.campaign.net)的URL連線到具有&#x200B;**nlserver web**&#x200B;模組（映象頁面、取消訂閱）的伺服器。

1. 將&#x200B;**internal**&#x200B;變更為與應用程式伺服器相同。

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 將資料庫連結至執行處理：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 在&#x200B;**config-default.xml**&#x200B;和&#x200B;**config-demo.xml**&#x200B;檔案中，啟用&#x200B;**web**、**trackinglogd**&#x200B;和&#x200B;**mta**&#x200B;模組。

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 編輯&#x200B;**serverConf.xml**&#x200B;檔案並填入：

   * MTA模組的DNS設定：

     ```
     <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
     ```

     >[!NOTE]
     >
     >**nameServers**&#x200B;引數僅用於Windows。

     如需詳細資訊，請參閱[傳遞設定](configure-delivery-settings.md)。

   * 重新導向引數中的多餘追蹤伺服器：

     ```
     <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
     <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
     ```

     如需詳細資訊，請參閱[備援追蹤](configuring-campaign-server.md#redundant-tracking)。

1. 啟動網站並從URL測試重新導向： [https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)。

   瀏覽器應顯示以下訊息（視負載平衡器重新導向的URL而定）：

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * 針對Linux： [正在啟動網頁伺服器並測試組態](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 針對Windows： [正在啟動Web伺服器並測試組態](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器。
1. 在Adobe Campaign Console中，使用無密碼的&#x200B;**管理員**&#x200B;登入進行連線，然後啟動部署精靈。

   如需詳細資訊，請參閱[部署執行個體](../../installation/using/deploying-an-instance.md)。

   除了追蹤模組的設定外，設定與獨立執行個體完全相同。

1. 填入用於重新導向的外部URL （負載平衡器的外部URL）和兩個前端伺服器的內部URL。

   如需詳細資訊，請參閱[追蹤組態](../../installation/using/deploying-an-instance.md#tracking-configuration)。

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >我們使用先前建立的兩個追蹤伺服器的現有執行個體，並使用&#x200B;**內部**&#x200B;登入。
