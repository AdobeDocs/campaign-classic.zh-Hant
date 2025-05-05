---
product: campaign
title: 技術檔案 — Adobe Campaign設定更新
description: Adobe Campaign設定更新
feature: Technote, Upgrade
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 8de62db2499449fc9966b6464862748e2514a774
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 8%

---

# 2021年Adobe Campaign設定更新 {#acc-config-updates}



基礎架構和設定應定期更新為最新的組建和產品修正。 為確保服務的連續性和安全性，這些修正是必要的。 此外，還需要升級以符合第三方變更。

作為&#x200B;**託管或Managed Services客戶**，Adobe會定期通知您組建版本升級。 您將需要根據建議進行升級以確保法規遵循。

作為&#x200B;**內部部署或混合客戶**，您應該根據最新發行的組建，定期升級實作。

基於安全考量，您現在必須升級至下列其中一個版本。 除了標準升級步驟外，還必須執行一些手動工作，以確保您的環境安全並準備好因應Adobe或協力廠商系統即將進行的變更。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>

## 安全性更新 {#acc-security-updates}

最新Campaign版本隨附安全性修正，可針對伺服器端請求偽造(SSRF)問題加強保護。 在[本頁](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)中深入瞭解。

**您有受到影響嗎？**

如果您的環境在低於下列的組建上，則會受到影響：

* Gold Standard 11. [了解更多](../../rn/using/gold-standard.md)
* Campaign 21.1.1版。 [了解更多](../../rn/using/latest-release.md)
* Campaign 20.2.5版。
* Campaign 20.1.4版。
* Campaign 19.2.4版。
* Campaign 19.1.8版。

在本節[&#128279;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。

**如何更新？**

您需要升級至上述其中一個較新的組建。

* 身為混合型客戶，Adobe會通知您中間來源執行個體的已排程升級日期。 Adobe強烈建議您也升級行銷執行個體。

  新組建版本可回溯相容於Campaign Classic 17.9版本，但Adobe強烈建議升級所有執行個體，以解決安全漏洞

* 身為內部部署客戶，您需要將行銷和中間來源執行個體升級至最新組建版本。

>[!CAUTION]
>
>如果您無法在建議的時間範圍內升級，請連絡Adobe客戶服務團隊，為您的執行個體套用短期手動安全性修正&#x200B;**。**
>

## Campaign Classic使用者端主控台更新  {#acc-cc-updates}

應安裝下列&#x200B;**現在可用**&#x200B;個主控台版本，以解決最近識別的回歸。 此回歸會防止在傳遞中使用使用者端主控台的某些元件，例如日期選擇器和影像管理。 **主控台必須升級**。

* 最新Gold Standard 11版本編號9032@10c2709。 [了解更多](../../rn/using/gold-standard.md)
* Campaign 20.1.4版。
* Campaign 19.2.4版。
* Campaign 19.1.8版。

## AdobeIdentity Management系統(IMS)更新

Adobe身分服務(IMS)將從2021年6月30日&#x200B;**起停止支援舊版Internet Explorer**。 [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

需要升級Campaign使用者端主控台，以確保與Adobe IMS相容。

**您有受到影響嗎？**

如果您要透過Adobe ID[&#128279;](../../integrations/using/about-adobe-id.md)並透過AdobeIdentity Management Service (IMS)連線至Campaign ，則必須升級至下列新版本之一：

* Gold Standard 11. [了解更多](../../rn/using/gold-standard.md)
* Campaign 21.1.1版。 [了解更多](../../rn/using/latest-release.md)
* Campaign 20.2.5版。
* Campaign 20.1.4版。
* Campaign 19.2.4版。
* Campaign 19.1.8版。

這些發行版本隨附新的連線通訊協定：Campaign伺服器和使用者端主控台都必須升級，才能在&#x200B;**2021年6月30日**&#x200B;後連線至Campaign。

在本節[&#128279;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。

**如何更新？**

作為託管客戶，Adobe將協助您儘快將執行個體升級至較新版本。

作為內部部署/混合部署客戶，您需要升級至較新版本之一，以受益於新的使用者端主控台，並確保在2021年6月30日之前&#x200B;**無縫轉換**。

升級所有執行個體後，使用者端主控台也需要升級為此版本。

* 瞭解如何存取[Adobe軟體發佈](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)。

* [瞭解如何安裝Campaign使用者端主控台](../../installation/using/installing-the-client-console.md)。

## 與Experience Cloud觸發程式整合 {#acc-triggers-updates}

舊版oAuth驗證服務已到期。 已將Triggers整合驗證（最初根據oAUTH驗證設定來存取管道）移至Adobe I/O。促銷活動[的舊版oAuth驗證模式已於&#x200B;**2021年9月日**&#x200B;淘汰](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 託管環境繼續使用延伸功能，直到 **2022 年 2 月 23 日**。若為內部部署或混合客戶，請聯絡Adobe客戶服務，將支援延長至2022年2月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md#step-optional)。

**您有受到影響嗎？**

如果您的執行個體是在Campaign 19.1.8、20.2.4、Gold Standard 11 **之前的**&#x200B;版本上執行，那麼您是透過oAuth驗證使用舊版的Triggers整合： **您必須升級至較新版本，並移至Adobe I/O**。

必須升級至下列新版本之一：

* Gold Standard 11. [了解更多](../../rn/using/gold-standard.md)
* Campaign 21.1.1版。 [了解更多](../../rn/using/latest-release.md)
* Campaign 20.2.5版。
* Campaign 19.1.8版。

在本節[&#128279;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。

**如何更新？**

執行個體升級至較新版本後，所有客戶都必須遵循[程式移至新的驗證模式](../../integrations/using/about-triggers.md#implement)。 這需要您產生新的Adobe I/O代號，並在實施中使用它。  

此外，對於混合環境，客戶需要確保在中間來源執行個體上設定管道。 [了解更多](../../integrations/using/configuring-pipeline.md)。

[瞭解如何移轉至Adobe I/O](../../integrations/using/about-triggers.md#implement)。

## APNs更新 {#acc-apns-updates}

### 以HTTP/2為基礎的APNs提供者API

自2021年3月31日&#x200B;**起**，Apple推播通知服務(APN)不再支援舊版二進位通訊協定。 [閱讀全文](https://developer.apple.com/news/?id=c88acm2b)。

**您有受到影響嗎？**

如果您的執行個體是在比Campaign 21.1，**舊的**&#x200B;版本上執行，而您傳送推播通知使用的是舊版Apple二進位通訊協定，則需要更新為以HTTP/2為基礎的APN提供者API。

在本節[&#128279;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。

**如何更新？**

作為託管客戶，如果您已升級至新的組建版本，Adobe已將您的執行個體更新至HTTP/2型API。

身為內部部署/混合部署客戶，您需要更新設定。

### APNs根憑證更新

2021年3月29日，Apple推播通知服務(APN)基礎架構更新影響Adobe Campaign Classic iOS頻道。 作業系統設定變更為&#x200B;**必要**，以避免iOS推播頻道中斷。

在此頁面[&#128279;](https://developer.apple.com/news/?id=7gx0a2lp)中進一步瞭解APN變更。

**您有受到影響嗎？**

如果您使用Campaign在iOS裝置上傳送推播通知，則會受到影響。

**如何更新？**

作為託管客戶，無需採取任何動作：Adobe已將新的根憑證整合至您的環境。

作為內部部署/混合部署客戶，您需要更新設定，以確保在2021年3月29日之前&#x200B;**無縫轉換**。

[瞭解如何合併新憑證](ios-certificate-update.md)。

## 有用的連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者可以使用新的使用者端主控台](../../installation/using/client-console-availability-for-windows.md)
