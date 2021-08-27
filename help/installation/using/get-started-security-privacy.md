---
product: campaign
title: 開始使用安全性和隱私權
description: 進一步了解有關安全性和隱私權需要檢查的關鍵元素。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 8%

---

# 開始使用安全性和隱私權 {#get-started-security-privacy}

![](../../assets/v7-only.svg)

本節將介紹有關安全性和隱私權需要檢查的關鍵元素。 某些設定只能由內部部署客戶執行。

## 隱私權

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

隱私權配置和強化是安全性最佳化的關鍵元素。 以下是關於隱私權的一些最佳實務：

* Protect使用HTTPS而非HTTP，讓客戶PII
* 使用PII檢視限制來保護隱私權並防止資料誤用。
* 請確定加密密碼受限。
* Protect可能包含個人資訊的頁面，例如鏡像頁面、網頁應用程式等。

[顯示全文](../../installation/using/privacy.md)

## 存取管理

<img src="assets/do-not-localize/icon_access.svg" width="60px">

訪問管理是加強安全性的重要環節。 以下是一些主要最佳實務：

* 建立足夠的安全組
* 檢查每個運算子是否擁有適當的存取權限
* 請避免使用管理員運算子，並避免管理員群組中有太多運算子

[顯示全文](../../installation/using/access-management.md)

## 指令碼和程式碼指南

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

在Adobe Campaign中開發時（工作流程、Javascript、JSSP等），請一律遵循下列准則：

* **指令碼**:嘗試避免SQL陳述式，使用參數化函式而不是字串串連接，通過將要使用的SQL函式添加到允許清單來避免SQL插入。

* **保護資料模型**:使用命名權限來限制運算子操作，添加系統篩選器(sysFilter)

* **在Web應用程式中新增captcha**:了解如何在您的公開登錄頁面和訂閱頁面中新增captcha。

[顯示全文](../../installation/using/scripting-coding-guidelines.md)

## 網路、資料庫和 SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

部署內部部署類型的架構時，需檢查的一項非常重要的事項是網路配置。

您也必須遵循資料庫引擎的安全性。

[顯示全文](../../installation/using/network-database.md)

## 伺服器配置

<img src="assets/do-not-localize/icon_server.svg" width="60px">

必須在所有伺服器上執行配置。 配置檔案的類型為&#x200B;**serverConf.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**。 以下是需要驗證的關鍵元素：

* **安全區域**:配置安全區域，以便它們直接考慮代理客戶端的IP地址。

* **檔案上傳保護**:限制可使用新uploadAllowList屬性上傳至Adobe Campaign伺服器的檔案類型。這可用於伺服器設定檔案。

* **中繼**:通過為未使用的模組/應用程式停用中繼規則來微調中繼配置。

* **傳出連** 線保護 **與命令限制** （伺服器端）

* 您也可以新增額外的HTTP標題、啟用checkIPConstent、enableTLS、sessionTimeOutSec等。 如需詳細資訊，請參閱[Campaign伺服器設定檔案](../../installation/using/configuring-campaign-server.md)和[伺服器設定檔案說明](../../installation/using/the-server-configuration-file.md) 。

[顯示全文](../../installation/using/server-configuration.md)

## Web伺服器配置

<img src="assets/do-not-localize/icon_web.svg" width="60px">

設定Web伺服器(Apache/IIS)時，應遵循數個最佳實務：

* 停用舊版SSL和加密
* 移除TRACE方法
* 移除橫幅
* 限制查詢大小以防止上傳重要檔案

[顯示全文](../../installation/using/web-server-configuration.md)
