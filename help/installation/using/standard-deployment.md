---
solution: Campaign Classic
product: campaign
title: 標準部署
description: 標準部署
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 4df126fa-4a6e-46a7-af6e-1e2e97f0072e
translation-type: tm+mt
source-git-commit: b0a1e0596e985998f1a1d02236f9359d0482624f
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 3%

---

# 標準部署{#standard-deployment}

對於此配置，需要三台電腦：

* LAN內部的應用程式伺服器，供一般使用者使用（準備促銷活動、報告等）,
* 在DMZ中，在負載平衡器後面有兩個前沿伺服器。

DMZ中的兩台伺服器可處理跟蹤、鏡像頁和交付，並且冗餘，以實現高可用性。

LAN中的應用程式伺服器為最終用戶提供服務，並執行所有經常性進程（工作流引擎）。 因此，當前端伺服器上達到峰值負載時，應用程式使用者不會受到影響。

資料庫伺服器可以裝載在與這三台電腦不同的電腦上。 否則，只要Adobe Campaign（Linux或Windows）支援作業系統，應用程式伺服器和資料庫伺服器就必須在LAN中共用同一台電腦。

伺服器和進程之間的通用通信根據以下方案進行：

![](assets/s_001_ncs_install_standardconfig.png)

這種配置可以處理大量接收者（500,000到1,000,000），因為資料庫伺服器（以及可用頻寬）是主要的限制因素。

## 功能{#features}

### 優勢{#advantages}

* 故障切換功能：在另一台電腦出現硬體問題時能夠將進程切換到一台電腦。
* 由於MTA和重新導向功能可部署在負載平衡器後的兩部電腦上，因此整體效能更佳。 有了兩個活動的MTA和足夠的頻寬，在每小時100,000封郵件的區域內實現廣播速率是可能的。

## 安裝和配置步驟{#installation-and-configuration-steps}

### 必要條件 {#prerequisites}

* JDK在這三部電腦上，
* Web伺服器(IIS、Apache)。
* 訪問所有三台電腦上的資料庫伺服器，
* 可通過POP3訪問的彈回郵箱，
* 建立兩個DNS別名：

   * 首先暴露在公眾面前，用於跟蹤並指向虛擬IP地址(VIP)上的負載平衡器，然後分配給兩個前端伺服器，
   * 第二個則暴露給內部使用者，供他們透過主控台存取，並指向相同的應用程式伺服器。

* 防火牆配置為開啟STMP(25)、DNS(53)、HTTP(80)、HTTPS(443)、SQL(1521 forOracle、5432 for PostgreSQL等) 埠。 有關詳細資訊，請參閱[Database access](../../installation/using/network-configuration.md#database-access)一節。

### 安裝應用程式伺服器{#installing-the-application-server}

按照步驟從Adobe Campaign應用程式伺服器安裝獨立實例以建立資料庫（步驟12）。 請參閱[安裝和配置（單機）](../../installation/using/standalone-deployment.md#installing-and-configuring--single-machine-)。

由於電腦不是追蹤伺服器，因此請勿考慮與Web伺服器的整合。

在以下示例中，實例的參數為：

* 實例的名稱：**demo**
* DNS掩碼：**console.campaign.net***（僅用於客戶端控制台連接和報告）
* 語言：英文
* 資料庫：**campaign:demo@dbsrv**

### 安裝兩台前端伺服器{#installing-the-two-frontal-servers}

安裝和配置過程在兩台電腦上都相同。

步驟如下：

1. 安裝Adobe Campaign伺服器。

   有關詳細資訊，請參閱[Linux中促銷活動安裝的先決條件(Linux)和[Windows中促銷活動安裝的先決條件(Windows)。](../../installation/using/prerequisites-of-campaign-installation-in-linux.md)](../../installation/using/prerequisites-of-campaign-installation-in-windows.md)

1. 請遵循下列章節所述的Web伺服器整合程式(IIS、Apache):

   * 針對Linux:[與Linux的Web伺服器整合](../../installation/using/integration-into-a-web-server-for-linux.md)
   * 針對Windows:[與Windows版Web伺服器整合](../../installation/using/integration-into-a-web-server-for-windows.md)

1. 建立&#x200B;**demo**&#x200B;實例。 有兩種方法可以做到：

   * 透過主控台建立執行個體：

      ![](assets/install_create_new_connexion.png)

      有關詳細資訊，請參閱[建立實例並登錄](../../installation/using/creating-an-instance-and-logging-on.md)。

      或

   * 使用命令行建立實例：

      ```
      nlserver config -addinstance:demo/tracking.campaign.net*
      ```

      有關詳細資訊，請參閱[建立實例](../../installation/using/command-lines.md#creating-an-instance)。
   實例的名稱與應用程式伺服器的名稱相同。

   使用&#x200B;**nlserver web**&#x200B;模組（鏡像頁、取消訂閱）連線至伺服器時，將會從負載平衡器的URL(tracking.campaign.net)進行。

1. 將&#x200B;**internal**&#x200B;變更為與應用程式伺服器相同。

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#internal-identifier)。

1. 將資料庫連結到實例：

   ```
   nlserver config -setdblogin:PostgreSQL:campaign:demo@dbsrv -instance:demo
   ```

1. 在&#x200B;**config-default.xml**&#x200B;和&#x200B;**config-demo.xml**&#x200B;檔案中，啟用&#x200B;**web**、**trackinglogd**&#x200B;和&#x200B;**mta**&#x200B;模組。

   如需詳細資訊，請參閱[本章節](../../installation/using/configuring-campaign-server.md#enabling-processes)。

1. 編輯&#x200B;**serverConf.xml**&#x200B;檔案並填入：

   * MTA模組的DNS配置：

      ```
      <dnsConfig localDomain="campaign.com" nameServers="192.0.0.1, 192.0.0.2"/>
      ```

      >[!NOTE]
      >
      >**nameServers**&#x200B;參數僅用於Windows。

      如需詳細資訊，請參閱[傳送設定](configuring-campaign-server.md#delivery-settings)。

   * 重新導向參數中的冗餘追蹤伺服器：

      ```
      <spareServer enabledIf="$(hostname)!='front_srv1'" id="1" url="https://front_srv1:8080"/>
      <spareServer enabledIf="$(hostname)!='front_srv2'" id="2" url="https://front_srv2:8080"/>
      ```

      有關詳細資訊，請參閱[冗餘跟蹤](../../installation/using/configuring-campaign-server.md#redundant-tracking)。

1. 啟動網站並測試從URL的重新導向：[https://tracking.campaign.net/r/test](https://tracking.campaign.net/r/test)。

   瀏覽器應顯示下列訊息（視負載平衡器所重新導向的URL而定）:

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv1"/>
   ```

   或

   ```
   <redir status="OK" date="AAAA/MM/JJ HH:MM:SS" build="XXXX" host="tracking.campaign.net" localHost="front_srv2"/>
   ```

   如需詳細資訊，請參閱下列章節：

   * 針對Linux:[啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-linux.md#launching-the-web-server-and-testing-the-configuration)
   * 針對Windows:[啟動Web伺服器並測試配置](../../installation/using/integration-into-a-web-server-for-windows.md#launching-the-web-server-and-testing-the-configuration)

1. 啟動Adobe Campaign伺服器。
1. 在Adobe Campaign控制台中，使用&#x200B;**admin**&#x200B;登入功能連線，毋需輸入密碼，然後啟動部署精靈。

   有關詳細資訊，請參閱[部署實例](../../installation/using/deploying-an-instance.md)。

   除了追蹤模組的設定外，組態與獨立執行個體相同。

1. 填入用於重新導向的外部URL（負載平衡器的URL）和兩個正面伺服器的內部URL。

   有關詳細資訊，請參閱[跟蹤配置](../../installation/using/deploying-an-instance.md#tracking-configuration)。

   ![](assets/d_ncs_install_tracking2.png)

   >[!NOTE]
   >
   >我們使用先前建立的兩個追蹤伺服器的現有例項，並使用&#x200B;**internal**&#x200B;登入。
