---
product: campaign
title: 中間來源部署
description: 中間來源部署
feature: Installation, Architecture, Deployment
audience: installation
content-type: reference
topic-tags: deployment-types-
exl-id: 8a4d7ef1-de5b-4aee-a527-1b74d987ba61
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 2%

---

# 中間來源部署{#mid-sourcing-deployment}



此設定是託管(ASP)設定與內部化之間的最佳中繼解決方案。 在Adobe Campaign託管的「中間來源」伺服器上執行向外執行元件。

>[!NOTE]
>
>若要設定此型別的部署，您必須取得適當的選項。 請檢查您的授權合約。

伺服器與處理序之間的一般通訊會根據以下結構描述執行：

![](assets/s_ncs_install_midsourcing.png)

* 執行個體上已停用執行和退回管理模組。
* 應用程式設定為在使用SOAP呼叫（透過HTTP或HTTPS）驅動的遠端「中間來源」伺服器上執行訊息。

## 功能 {#features}

### 優點 {#advantages}

* 簡化伺服器設定：客戶不需要設定對外模組（mta和inMail）。
* 頻寬使用限制：由於執行是由中間來源伺服器執行，因此只需要足夠的頻寬即可將個人化資料傳送至中間來源伺服器。
* 高可用性不再是內部問題：問題已轉移至中間來源伺服器（重新導向、映象頁面、執行伺服器等）。
* 資料庫不會離開公司：只有組合訊息所需的資料才會傳送到中間來源伺服器（HTTPS可用於此作業）。
* 這種型別的部署可以作為高容量架構（資料庫中有許多收件者）的解決方案，並具備可觀的傳遞輸送量。

### 缺點 {#disadvantages}

* 由於從中間來源伺服器取回資訊所需的時間，檢視訊息執行資訊和報告功能方面稍有延遲。
* 調查與網路表單仍保留在使用者端平台上。

### 建議的裝置 {#recommended-equipment}

* 應用程式伺服器：2 Ghz四核心CPU、4 GB RAM、軟體RAID 1 80 GB SATA硬碟。
* 資料庫伺服器：3 GHz雙四核心CPU、至少4 GB RAM、硬體RAID 10 15000RPM SAS硬碟，數量依資料庫的大小和預期效能而定。

>[!NOTE]
>
>重新導向和中間來源是獨立的元素，不過追蹤伺服器通常會和中間來源伺服器共用。

## 安裝和設定步驟 {#installation-and-configuration-steps-}

### 先決條件 {#prerequisites}

* 應用程式伺服器上的JDK。
* 存取應用程式伺服器上的資料庫伺服器。
* 防火牆已設定為開啟HTTP (80)或HTTPS (443)連線埠至中間來源伺服器。

### 安裝和設定（中間來源部署） {#installing-and-configuring--mid-sourcing-deployment-}

請參閱 [中間來源伺服器](../../installation/using/mid-sourcing-server.md).
