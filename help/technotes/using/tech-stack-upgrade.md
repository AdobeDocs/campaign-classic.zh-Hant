---
product: campaign
title: 技術 — Adobe Campaign系統升級
description: Adobe Campaign系統升級
hide: true
hidefromtoc: true
exl-id: 78949d94-60b3-44f1-8e5a-d61b5b723e87
source-git-commit: b8bbdb4a0d595ec2bc884e041d1e56b81da8aa3d
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 8%

---

# Adobe Campaign 2023環境升級 {#ac-system-upgrade}

Campaign基礎架構依賴協力廠商系統，必須定期更新最新版本和修正。 這些更新是強制性的，以確保服務的連續性，並保護Campaign環境免受安全風險的影響。 此外，還需要Campaign升級，以確保與協力廠商系統變更相容。

As a **托管或托管Cloud Services客戶**,Adobe會在需要時通知您這些升級。 您需要根據建議升級您的環境，以確保符合規範。

作為 **內部部署或混合客戶**,Adobe強烈建議您根據相同的日曆升級系統和Campaign版本。

出於安全原因，您必須 [安裝最新的Campaign版本編號](#ac-upgrade)，然後升級您的 [作業系統](#os-upgrade) 和/或 [關係資料庫管理系統(RDBMS)](#pg-upgrade).

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。另請參閱 [建置升級常見問題集](../../platform/using/faq-build-upgrade.md).

## Campaign版本編號升級 {#ac-upgrade}

**您有受到影響嗎？**

如果您受 [作業系統升級](#os-upgrade) 和/或 [資料庫系統升級](#pg-upgrade) 以下詳細說明，您必須將您的Campaign環境升級至 [最新7.3.2版](../../rn/using/latest-release.md#release-7-3-2)，與這些系統相容。

**如何更新？**

* 身為托管或托管Cloud Services客戶，Adobe會與您聯絡並升級您的Campaign版本。
* 身為混合客戶，Adobe會通知您中間來源環境的已排程組建升級日期。 您也必須將行銷環境升級至相同版本。
* 身為內部部署客戶，系統請您將Campaign環境升級至最新的7.3.2版本編號。


## 作業系統升級 {#os-upgrade}

**您有受到影響嗎？**

如果您在Debian作業系統上執行Campaign，為了從最新的Debian安全性更新中受益，您需要將Campaign基礎架構移至 **Debian 11**. 請注意，Debian 9已於2022年6月30日終止服務，不再提供安全性修正。

**如何更新？**

* 身為托管或托管Cloud Services客戶，Adobe會與您連絡並升級您的環境。
* 身為混合客戶，Adobe會通知您中間來源環境的升級計畫日期。 如果您的行銷環境也在Debian上執行，您也必須將其升級至Debian 11。
* 身為內部部署客戶，系統請您將環境升級至Debian 11。

## 資料庫系統升級 {#pg-upgrade}

**您有受到影響嗎？**

如果您的Campaign資料庫系統是PostgreSQL，為了從最新的PostgreSQL創新和安全更新中受益，您需要升級到 **PostgreSQL 14**. 請注意，PostreSQL 11將於2022年11月30日終止服務。

**如何更新？**

* 作為托管Cloud Services或托管Adobe客戶，客戶將與您聯繫，並將資料庫系統從PostgreSQL 11升級到PostgreSQL 14。
* 作為混合客戶，如果您的行銷資料庫系統是PostgreSQL，則必須將其升級到PostgreSQL 14。
* 作為內部部署客戶，請您將資料庫系統升級為PostgreSQL 14。


## 實用連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載最新的Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者能使用新的用戶端主控台](../../installation/using/client-console-availability-for-windows.md)
