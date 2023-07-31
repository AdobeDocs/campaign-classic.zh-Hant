---
product: campaign
title: 技術檔案 — Adobe Campaign系統升級
description: Adobe Campaign系統升級
feature: Technote, Upgrade
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 9%

---

# Adobe Campaign 2023環境升級 {#ac-system-upgrade}

Campaign基礎架構仰賴協力廠商系統，且必須定期以最新版本和修正更新。 這些更新是強制性的，可確保服務的連續性，並確保Campaign環境的安全不會受到安全風險的影響。 此外，需要升級Campaign，以確保與協力廠商系統變更相容。

作為 **託管或受管理的Cloud Services客戶**，Adobe會在需要這些升級時通知您。 您將需要根據建議升級環境以確保合規性。

作為 **內部部署或混合客戶**，Adobe強烈建議您根據相同行事曆升級系統和Campaign版本。

基於安全考量，您必須 [安裝最新的Campaign版本編號](#ac-upgrade)，然後升級您的 [作業系統](#os-upgrade) 和/或您的 [關係資料庫管理系統(RDBMS)](#pg-upgrade).

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。另請參閱 [建置升級常見問答集](../../platform/using/faq-build-upgrade.md).
>

## Campaign版本編號升級 {#ac-upgrade}

**您有受到影響嗎？**

如果您受 [作業系統升級](#os-upgrade) 和/或 [資料庫系統升級](#pg-upgrade) 詳細資訊如下，您必須將您的Campaign環境升級至 [最新的7.3.2版本](../../rn/using/latest-release.md#release-7-3-2)，這些系統相容。

**如何更新？**

* 作為託管或受管理的Cloud Services客戶，Adobe將會聯絡您並升級您的Campaign版本。
* 作為混合型客戶，Adobe會通知您中間來源環境的已排程組建升級日期。 您也必須將行銷環境升級至相同版本。
* 身為內部部署客戶，您需要將Campaign環境升級至最新的7.3.2版本編號。


## 作業系統升級 {#os-upgrade}

**您有受到影響嗎？**

如果您在Debian作業系統上執行Campaign，若要受益於最新的Debian安全性更新，您需要將Campaign基礎架構移至 **Debian 11**. 請注意，Debian 9的安全性支援將持續提供至2023年6月30日。

**如何更新？**

* 作為託管或受管理的Cloud Services客戶，Adobe將會聯絡您並升級您的環境。
* 作為混合型客戶，Adobe會通知您中間來源環境的已排程升級日期。 如果您的行銷環境也在Debian上執行，也必須將其升級至Debian 11。
* 作為內部部署客戶，您需要將環境升級至Debian 11。

## 資料庫系統升級 {#pg-upgrade}

**您有受到影響嗎？**

如果您的Campaign資料庫系統是PostgreSQL，若要受益於最新的PostgreSQL創新和安全性更新，您需要升級至 **PostgreSQL 14**. 請注意，PostgreSQL 11將於2023年11月9日結束生命週期。

**如何更新？**

* 作為託管或受管理的Cloud Services客戶，Adobe將會聯絡您，並將您的資料庫系統從PostgreSQL 11升級至PostgreSQL 14。
* 身為混合型客戶，如果您的行銷資料庫系統是PostgreSQL，您必須將其升級至PostgreSQL 14。
* 作為內部部署客戶，您需要將資料庫系統升級至PostgreSQL 14。


## 有用的連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載最新的Campaign Classic建置](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者可以使用新的使用者端主控台](../../installation/using/client-console-availability-for-windows.md)
