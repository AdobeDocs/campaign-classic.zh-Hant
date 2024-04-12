---
product: campaign
title: 安全性與隱私權檢查清單
description: 進一步瞭解關於安全性和隱私權需要檢查的關鍵元素
feature: Installation, Privacy, Access Management, Privacy Tools
audience: installation
content-type: reference
topic-tags: prerequisites-and-recommendations-
exl-id: ec40498e-e673-4792-8dcf-8bb7e852b532
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 7%

---

# 安全性與隱私權檢查清單{#get-started-security-privacy}



本節將向您介紹有關安全性和隱私權需要檢查的核心元素。 部分設定只能由內部部署客戶執行。

## 隱私權

<img src="assets/do-not-localize/icon_privacy.svg" width="60px">

隱私權設定和強化是安全性最佳化的關鍵元素。 以下是隱私權方面的一些最佳實務：

* 使用HTTPS而非HTTPProtect您的客戶PII
* 使用PII檢視限制來保護隱私權並防止資料被濫用。
* 請確定加密的密碼受到限制。
* Protect中可能包含個人資訊的頁面，例如映象頁面、網頁應用程式等。

[閱讀全文](../../installation/using/privacy.md)

## 存取管理

<img src="assets/do-not-localize/icon_access.svg" width="60px">

存取管理是強化安全性的重要一環。 以下是一些主要最佳實務：

* 建立足夠的安全性群組
* 檢查每個操作員是否具有適當的存取許可權
* 避免使用管理員運運算元，並避免在管理員群組中擁有太多運運算元

[閱讀全文](../../installation/using/access-management.md)

## 指令碼和程式碼指南

<img src="assets/do-not-localize/icon_scripting.svg" width="60px">

在Adobe Campaign中進行開發時（工作流程、JavaScript、JSSP等），請一律遵循下列准則：

* **指令碼**：請嘗試避免SQL陳述式，使用引數化函式而非字串串串連，將要使用的SQL函式新增至允許清單以避免SQL插入。

* **保護資料模型**：使用已命名的許可權來限制運運算元動作、新增系統篩選器(sysFilter)

* **在Web應用程式中新增字幕**：瞭解如何在您的公開登陸頁面和訂閱頁面中新增驗證碼。

[閱讀全文](../../installation/using/scripting-coding-guidelines.md)

## 網路、資料庫和 SSL/TLS

<img src="assets/do-not-localize/icon_network.svg" width="60px">

在部署內部部署型別的架構時，有一件非常重要的事要檢查，那就是網路組態。

您也必須遵循資料庫引擎安全性。

[閱讀全文](../../installation/using/network-database.md)

>[!CAUTION]
>
>自2021年7月14日起，任何不支援TLS 1.2通訊協定的使用者端系統將會失去所有Adobe產品和服務的存取權。 在此日期之前，請確定所有使用者和使用者端系統都符合TLS 1.2規範。 [了解更多](https://helpx.adobe.com/x-productkb/multi/eol-tls-support.html)

## 伺服器設定

<img src="assets/do-not-localize/icon_server.svg" width="60px">

必須在所有伺服器上執行設定。 組態檔案的型別為 **serverConf.xml** 和 **`config-<instance>.xml`**. 以下是需要驗證的關鍵元素：

* **安全性區域**：設定安全性區域，使其直接考慮Proxy使用者端的IP位址。

* **檔案上傳保護**：限制可使用新的uploadAllowList屬性上傳至Adobe Campaign伺服器的檔案型別。 這可用於伺服器設定檔。

* **轉送**：停用未使用模組/應用程式的轉送規則，以微調轉送設定。

* **傳出連線的保護** 和 **命令限制** （伺服器端）

* 您也可以新增額外的HTTP標頭、啟用checkIPConsistent、enableTLS、sessionTimeOutSec等。 請參閱 [Campaign伺服器設定檔案](../../installation/using/configuring-campaign-server.md) 和 [伺服器設定檔描述](../../installation/using/the-server-configuration-file.md) 以取得詳細資訊。

[閱讀全文](../../installation/using/server-configuration.md)

## Web伺服器設定

<img src="assets/do-not-localize/icon_web.svg" width="60px">

設定網頁伺服器(Apache/IIS)時，應遵循數個最佳實務：

* 停用舊的SSL版本和加密
* 移除TRACE方法
* 移除橫幅
* 限制查詢大小以防止重要檔案上傳

[閱讀全文](../../installation/using/web-server-configuration.md)
