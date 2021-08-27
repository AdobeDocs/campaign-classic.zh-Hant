---
product: campaign
title: 技術檔案
description: 技術檔案
hide: true
hidefromtoc: true
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: 53ac193211a1d98c45e97bf01ab0ad843b8f8f02
workflow-type: tm+mt
source-wordcount: '1131'
ht-degree: 11%

---

# Adobe Campaign設定更新 — 2021年3月 {#acc-config-updates}

![](../../assets/v7-only.svg)

基礎架構和設定應定期更新，包含最新的組建和產品修正。 這些修正是確保服務和安全性持續性的必要措施。 此外，還需要升級以符合協力廠商的變更。

以&#x200B;**托管或Managed Services客戶**&#x200B;的形式，Adobe會定期通知您組建升級。 您必鬚根據建議進行升級，以確保符合規範。

身為&#x200B;**內部部署或混合客戶**，您應定期升級實作，以符合最新發行的組建。

基於安全考量，您現在必須升級至下列其中一個版本。 除了標準升級步驟，還必須執行一些手動任務，以確保您的環境安全，並且準備好迎接Adobe或第三方系統即將進行的更改。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 安全性更新 {#acc-security-updates}

最新的Campaign版本隨附安全性修正，加強針對伺服器端請求偽造(SSRF)問題的保護。 在[本頁](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)中深入瞭解。

**您有受到影響嗎？**

如果您的環境的組建比下列的低，您會受到影響：

* 金標11。 [深入瞭解](../../rn/using/gold-standard.md)
* Campaign 21.1.1版。 [深入瞭解](../../rn/using/latest-release.md)
* Campaign 20.2.4版。 [深入瞭解](../../rn/using/release--20-2.md)
* Campaign 20.1.4版。 [深入瞭解](../../rn/using/release--20-1.md)
* Campaign 19.2.4版。 [深入瞭解](../../rn/using/release--19-2.md)
* Campaign 19.1.8版。 [深入瞭解](../../rn/using/release--19-1.md)

在本小節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。

**如何更新？**

您需要升級至上述其中一個較新的組建。

* 身為混合客戶，Adobe會通知您中間來源執行個體的已排程升級日期。 Adobe強烈建議您也升級行銷執行個體。

   新組建版本向後相容於Campaign Classic17.9版本，但Adobe強烈建議對所有執行個體進行升級，以解決安全性弱點

* 身為內部部署客戶，系統會要求您將行銷和中間來源執行個體升級至最新組建。

>[!CAUTION]
>
>如果您無法在建議的時間範圍內升級，請&#x200B;**聯絡Adobe客戶服務團隊，對您的執行個體**&#x200B;套用短期手動安全性修正。

## Campaign Classic客戶端控制台更新  {#acc-cc-updates}

應安裝下方的&#x200B;**現在可用的**&#x200B;主控台版本，以解析最近識別的回歸。 此回歸會阻止使用用戶端主控台的某些元件，例如傳送中的日期選擇器和影像管理。 **主控** 台升級是必要的。

* 最新Gold Standard 11組建版本9032@10c2709。 [深入瞭解](../../rn/using/gold-standard.md)
* Campaign 20.1.4版。 [深入瞭解](../../rn/using/release--20-1.md)
* Campaign 19.2.4版。 [深入瞭解](../../rn/using/release--19-2.md)
* Campaign 19.1.8版。 [深入瞭解](../../rn/using/release--19-1.md)

## AdobeIdentity Management系統(IMS)更新

Adobe身分識別服務(IMS)將於2021年6月30日起停止支援舊版Internet Explorer。 ****[深入瞭解](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

需要升級Campaign用戶端主控台，以確保與AdobeIMS相容。

**您有受到影響嗎？**

如果您透過Adobe ID](../../integrations/using/about-adobe-id.md)連線至Campaign [，透過AdobeIdentity Management服務(IMS)，必須升級至下列其中一個新版本：

* 金標11。 [深入瞭解](../../rn/using/gold-standard.md)
* Campaign 21.1.1版。 [深入瞭解](../../rn/using/latest-release.md)
* Campaign 20.2.5版。 [深入瞭解](../../rn/using/release--20-2.md)
* Campaign 20.1.4版。 [深入瞭解](../../rn/using/release--20-1.md)
* Campaign 19.2.4版。 [深入瞭解](../../rn/using/release--19-2.md)
* Campaign 19.1.8版。 [深入瞭解](../../rn/using/release--19-1.md)

這些版本隨附新的連線通訊協定：在&#x200B;**2021年6月30日**&#x200B;之後，Campaign伺服器和用戶端主控台必須升級才能連線至Campaign。

在本小節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。

**如何更新？**

身為托管客戶，Adobe會與您合作，盡快將您的執行個體升級至較新版本。

身為內部部署/混合部署客戶，您需要升級至任一個較新版本，以便從新的用戶端主控台獲益，並確保在2021年6月30日之前順暢轉換&#x200B;****。

升級所有執行個體後，用戶端主控台也需升級至此版本。

* 了解如何存取[Adobe軟體發佈](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)。

* [了解如何安裝Campaign用戶端主控台](../../installation/using/installing-the-client-console.md)。

## 與Experience Cloud觸發器整合 {#acc-triggers-updates}

舊版oAuth驗證服務已終止。 已將觸發整合驗證（原本以oAUTH驗證設定為基礎，用於存取管道）移至Adobe I/O。**2021年8月18日**&#x200B;已淘汰具有Campaign [的舊版oAuth驗證模式](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。 托管環境可從延伸功能中獲益，直到2021年11月30日&#x200B;**。**&#x200B;身為內部部署或混合客戶，請聯絡Adobe客戶服務，將支援延長至2021年11月30日。 您必須提供[OAuth應用程式](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)的AppID以Adobe。

**您有受到影響嗎？**

如果您的執行個體在&#x200B;**舊版Campaign 19.1.8、20.2.4、Gold Standard 11**&#x200B;上執行，則您使用舊版的Triggers整合透過oAuth驗證：**您需要升級至更新版本，並移至Adobe I/O**。

必須升級至下列其中一個新版本：

* 金標11。 [深入瞭解](../../rn/using/gold-standard.md)
* Campaign 21.1.1版。 [深入瞭解](../../rn/using/latest-release.md)
* Campaign 20.2.5版。 [深入瞭解](../../rn/using/release--20-2.md)
* Campaign 19.1.8版。 [深入瞭解](../../rn/using/release--19-1.md)

在本小節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。

**如何更新？**

將實例升級到更新版本後，所有客戶都需要按照[過程移至新的驗證模式](../../integrations/using/configuring-adobe-io.md)。 這需要您產生新的Adobe I/O代號，並在實施中使用。  

此外，針對混合環境，客戶需確保管道是在中間來源執行個體上設定。 [深入瞭解](../../integrations/using/configuring-pipeline.md)。

[了解如何移轉至Adobe I/O](../../integrations/using/configuring-adobe-io.md)。

## APN更新 {#acc-apns-updates}

### 基於HTTP/2的APN提供程式API

自2021年3月31日&#x200B;**起，Apple推播通知服務(APN)不再支援舊版二進位通訊協定。**[顯示全文](https://developer.apple.com/news/?id=c88acm2b)。

**您的受影響嗎？**

如果您的執行個體在&#x200B;**舊版Campaign 21.1、**&#x200B;上執行，而您使用舊版Apple二進位通訊協定傳送推播通知，則需要更新為HTTP/2型APN提供者API。

在本小節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。

**如何更新？**

身為托管客戶，如果您已升級至新組建，Adobe已將您的執行個體更新至HTTP/2型API。

身為內部部署/混合部署客戶，您需要更新您的設定。 [了解如何移轉至HTTP/2](https://helpx.adobe.com/tw/campaign/kb/migrate-to-apns-http2.html)

### APN根證書更新

2021年3月29日，Apple推播通知服務(APN)基礎架構更新影響了Adobe Campaign Classic iOS通道。 作業系統組態變更為&#x200B;**強制**，以避免iOS推播通道中斷。

了解更多有關APN更改[的資訊，請參閱本頁](https://developer.apple.com/news/?id=7gx0a2lp)。

**您有受到影響嗎？**

如果您使用Campaign在iOS裝置上傳送推播通知，則會受到影響。

**如何更新？**

身為托管客戶，不需要採取任何動作：Adobe已將新的根憑證整合至您的環境。

身為內部部署/混合客戶，您必須更新設定，以確保在2021年3月29日前&#x200B;**順暢轉換**。

[了解如何合併新憑證](ios-certificate-update.md)。

## 實用連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [建置升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓使用者能使用新的用戶端主控台](../../installation/using/client-console-availability-for-windows.md)
