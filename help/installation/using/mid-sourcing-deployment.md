---
product: campaign
title: 中間來源部署
description: 中間來源部署
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 1%

---

# 中間來源部署{#mid-sourcing-deployment}

![](../../assets/v7-only.svg)

此配置是托管(ASP)配置和內部化之間的最佳中間解決方案。 對外執行元件會在Adobe Campaign托管的「中間來源」伺服器上執行。

>[!NOTE]
>
>若要設定此類型的部署，您必須取得適當的選項。 請檢查您的許可證合同。

伺服器和進程之間的一般通信根據以下模式執行：

![](assets/s_ncs_install_midsourcing.png)

* 執行和退信管理模組在執行個體上是停用的。
* 應用程式可配置為在使用SOAP呼叫（通過HTTP或HTTPS）驅動的遠程「中源」伺服器上執行消息。

## 功能 {#features}

### 優勢 {#advantages}

* 簡化的伺服器配置：客戶不需要配置向外的模組（mta和inMail）。
* 頻寬使用有限：由於執行是由中間來源伺服器執行，因此只需要足夠的頻寬，即可將個人化資料傳送至中間來源伺服器。
* 高可用性不再是內部問題：問題已轉移到中間來源伺服器（重定向、鏡像頁、執行伺服器等）。
* 資料庫不會離開公司：只有組合訊息所需的資料才會傳送至中間來源伺服器（HTTPS可用於此）。
* 此類部署可以是高容量體系結構（資料庫中的許多收件人）的解決方案，具有顯著的傳送吞吐量。

### 缺點 {#disadvantages}

* 檢視訊息執行資訊和報告功能因從中間來源伺服器取得資訊所需的時間而略有延遲。
* 調查和網路表單仍保留在用戶端平台上。

### 推薦設備 {#recommended-equipment}

* 應用程式伺服器：2 Ghz四核CPU,4 GB RAM，軟體RAID 1 80 GB SATA硬碟。
* 資料庫伺服器：3 GHz雙四核CPU，最少4 GB RAM，硬體RAID 10 15000RPM SAS硬碟，數量取決於資料庫的大小和預期效能。

>[!NOTE]
>
>重新導向與中間來源是個別元素，但一般而言，追蹤伺服器將與中間來源伺服器共用。

## 安裝和配置步驟 {#installation-and-configuration-steps-}

### 先決條件 {#prerequisites}

* 應用程式伺服器上的JDK。
* 訪問應用程式伺服器上的資料庫伺服器。
* 防火牆配置為向中間來源伺服器開啟HTTP(80)或HTTPS(443)埠。

### 安裝和設定（中間來源部署） {#installing-and-configuring--mid-sourcing-deployment-}

請參閱[中間來源伺服器](../../installation/using/mid-sourcing-server.md)。
