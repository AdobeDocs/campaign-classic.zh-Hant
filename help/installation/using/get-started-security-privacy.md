---
solution: Campaign Classic
product: campaign
title: 開始使用安全性和隱私權
description: 進一步瞭解要檢查的安全性和隱私性關鍵元素。
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
translation-type: tm+mt
source-git-commit: 45a77d3fc143ab9c6f9f17ab6118f8816254f6fd
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 3%

---


# 開始使用安全性和隱私權{#get-started-security-privacy}

本節將向您介紹檢查安全性和隱私權的關鍵要素。

## 隱私權

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

隱私權配置和強化是安全性最佳化的關鍵要素。 以下是有關隱私權的一些最佳實務：

* Protect您的客戶PII，方法是使用HTTPS而非HTTP
* 使用PII檢視限制來保護隱私權並防止資料遭到誤用。
* 請確定加密的密碼受到限制。
* Protect可能包含個人資訊的頁面，例如鏡像頁面、Web應用程式等。

[顯示全文](../../installation/using/privacy.md)

## 存取管理

<img src="assets/do-not-localize/icon_access.svg" width="60px">

訪問管理是加強安全性的一個重要部分。 以下是一些主要的最佳實務：

* 建立足夠的安全性群組
* 檢查每個運算子是否擁有適當的存取權限
* 避免使用管理員運算子，並避免管理群組中的運算子過多

[顯示全文](../../installation/using/access-management.md)

## 指令碼和編碼准則

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

在Adobe Campaign進行開發時（工作流程、Javascript、JSSP等），請一律遵循下列准則：

* **指令碼**:嘗試避免SQL陳述式，使用參數化函式而不是字串串連，通過將要使用的SQL函式添加到允許清單來避免SQL插入。

* **保護資料模型**:使用命名權限來限制運算元動作，新增系統篩選(sysFilter)

* **在Web應用程式中新增擷取功能**:瞭解如何在您的公開登陸頁面和訂閱頁面中新增captcha。

[顯示全文](../../installation/using/scripting-coding-guidelines.md)

## 網路、資料庫和SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

部署內部部署類型的體系結構時，需要檢查的一個非常重要的問題是網路配置。

此外，您必須遵循資料庫引擎的安全性。

[顯示全文](../../installation/using/network-database.md)

## 伺服器組態

<img src="assets/do-not-localize/icon_server.svg" width="60px">

必須在所有伺服器上執行配置。 配置檔案的類型為&#x200B;**serverConf.xml**&#x200B;和&#x200B;**`config-<instance>.xml`**。 以下是需要驗證的關鍵要素：

* **安全區**:配置安全區，以便它們直接考慮代理客戶機的IP地址。

* **檔案上傳保護**:使用新的uploadAllowList屬性，限制可上傳至Adobe Campaign伺服器的檔案類型。這可用於伺服器配置檔案。

* **中繼**:通過為未使用的模組／應用程式禁用中繼規則來微調中繼配置。

* **輸出連** 接保 **護和命令限** 制（伺服器端）

* 您也可以新增額外的HTTP標題、啟用checkIPConsistent、enableTLS、sessionTimeOutSec等。 如需詳細資訊，請參閱[促銷活動伺服器設定檔案](../../installation/using/configuring-campaign-server.md)和[伺服器設定檔案說明](../../installation/using/the-server-configuration-file.md)。

[顯示全文](../../installation/using/server-configuration.md)

## Web-server配置

<img src="assets/do-not-localize/icon_web.svg" width="60px">

在配置Web伺服器(Apache/IIS)時，應遵循以下幾個最佳做法：

* 停用舊版SSL和密碼：
* 刪除TRACE方法：
* 移除橫幅：
* 限制查詢大小以防止上傳重要檔案：

[顯示全文](../../installation/using/web-server-configuration.md)
