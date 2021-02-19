---
solution: Campaign Classic
product: campaign
title: 中間來源部署
description: 中間來源部署
audience: installation
content-type: reference
topic-tags: deployment-types-
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---


# 中間來源部署{#mid-sourcing-deployment}

此配置是代管(ASP)配置和內部化之間的最佳中間解決方案。 對外執行元件是在Adobe Campaign所代管的「中部採購」伺服器上執行。

>[!NOTE]
>
>若要設定此類型的部署，您必須取得適當的選項。 請檢查您的授權合約。

伺服器和進程之間的通用通信根據以下方案進行：

![](assets/s_ncs_install_midsourcing.png)

* 執行和彈回管理模組在實例上被禁用。
* 應用程式已設定為在使用SOAP呼叫（透過HTTP或HTTPS）驅動的遠端「中端來源」伺服器上執行訊息。

## 功能{#features}

### 優勢{#advantages}

* 簡化的伺服器組態：客戶無需配置面向外的模組（mta和inMail）。
* 頻寬使用有限：由於執行是由中間採購伺服器執行的，因此只需足夠的頻寬即可將個性化資料發送到中間採購伺服器。
* 高可用性不再是內部問題：問題轉移到中間源伺服器（重定向、鏡像頁、執行伺服器等）。
* 資料庫不會離開公司：只有匯整訊息所需的資料才會傳送至中端來源伺服器（HTTPS可用於此）。
* 這種部署方式可以解決高容量體系結構（資料庫中的許多接收方），並具有很高的交付吞吐量。

### 缺點{#disadvantages}

* 由於從中端來源伺服器取得資訊所花的時間，因此在檢視訊息執行資訊和報告功能方面有輕微的延遲。
* 調查和Web表格仍保留在用戶端平台上。

### 建議的設備{#recommended-equipment}

* 應用程式伺服器：2 Ghz四核CPU,4 GB RAM，軟體RAID 1 80 GB SATA硬碟。
* 資料庫伺服器：3 GHz雙四核CPU、最低4 GB RAM、硬體RAID 10 15000RPM SAS硬碟機，數量取決於資料庫的大小和預期效能。

>[!NOTE]
>
>重新導向和中間採購是個別的元素，不過一般而言，追蹤伺服器會與中間採購伺服器共用。

## 安裝和配置步驟{#installation-and-configuration-steps-}

### 必要條件 {#prerequisites}

* 應用程式伺服器上的JDK。
* 訪問應用程式伺服器上的資料庫伺服器。
* 防火牆配置為開啟HTTP(80)或HTTPS(443)埠至中端源伺服器。

### 安裝和配置（中部採購部署）{#installing-and-configuring--mid-sourcing-deployment-}

請參閱[Mid-sourcing server](../../installation/using/mid-sourcing-server.md)。
