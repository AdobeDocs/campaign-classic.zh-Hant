---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 01f4e4ee841a797f4be61ffc01096b7f651ce963
workflow-type: tm+mt
source-wordcount: '1114'
ht-degree: 7%

---


# Adobe Campaign配置更新- 2021年3月{#acc-config-updates}

基礎架構和設定應定期更新，以取得最新的建置和產品修正。 這些修正是確保服務與安全性持續性的必要措施。 此外，需要升級才能與協力廠商的變更保持一致。

身為&#x200B;**代管或Managed Services客戶**,Adobe會定期通知您建置升級。 您必須依照建議進行升級，以確保符合規範。

身為&#x200B;**內部部署或Hybrid客戶**，您應定期升級實作，以符合最新發佈的組建版本。

出於安全考慮，您現在必須升級至下列其中一個版本。 除了標準升級步驟外，還必須執行一些手動任務，以確保您的環境安全，並準備好迎接Adobe或協力廠商系統即將進行的更改。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。


## 安全性更新

最新的促銷活動版本隨附安全性修正，加強針對伺服器端偽造要求(SSRF)問題的保護。 在本頁瞭解更多[的資訊。](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)

**您受影響嗎？**

如果您的環境的組建版本低於下列版本，您會受到影響：

* 金標11 [進一步了解](../rn/using/gold-standard.md)
* Campaign 21.1.1發行。 [進一步了解](../rn/using/latest-release.md)
* Campaign 20.3.3發行。 [進一步了解](../rn/using/release--20-3.md)
* Campaign 20.2.4發行。 [進一步了解](../rn/using/release--20-2.md)
* Campaign 20.1.4發行。 [進一步了解](../rn/using/release--20-1.md)
* Campaign 19.2.4發行。 [進一步了解](../rn/using/release--19-2.md)
* Campaign 19.1.8發行。 [進一步了解](../rn/using/release--19-1.md)

瞭解如何在本節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本[。

**如何更新？**

您必須升級至上述任一較新的版本。

* 身為混合型客戶，Adobe會通知您中部採購實例的升級計畫日期。 Adobe強烈建議您也升級行銷實例。

   新版本向後相容Campaign Classic17.9版本，但Adobe強烈建議對所有實例進行升級以解決安全漏洞

* 身為內部部署客戶，您必須將行銷和中部採購實例升級至最新版本。

>[!CAUTION]
>
>如果您無法在建議的時間範圍內升級，請&#x200B;**聯絡Adobe客戶服務團隊，以針對您的例項套用短期手動安全性修正。**


## Campaign Classic客戶端控制台更新

**現已提供**&#x200B;控制台版本，應安裝以解決最近識別的回歸。 此回歸無法使用用戶端主控台的某些元件，例如傳送中的日期選擇器和影像管理。 **控制台** 升級是必備的。

* 最新的Gold Standard 11組建版本9032@10c2709。 [進一步了解](../rn/using/gold-standard.md)
* Campaign 20.1.4發行。 [進一步了解](../rn/using/release--20-1.md)
* Campaign 19.2.4發行。 [進一步了解](../rn/using/release--19-2.md)
* Campaign 19.1.8發行。 [進一步了解](../rn/using/release--19-1.md)

## AdobeIdentity Management系統(IMS)更新

Adobe身分服務(IMS)將從2021年6月30日&#x200B;**停止支援舊版Internet Explorer。**[進一步瞭解](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

必須升級促銷活動用戶端主控台，以確保與AdobeIMS相容。

**您受影響嗎？**

如果您透過Adobe ID](../integrations/using/about-adobe-id.md)連線至促銷活動，透過AdobeIdentity Management服務(IMS)，必須升級至下列其中一個新版本：[

* 金標11 [進一步了解](../rn/using/gold-standard.md)
* Campaign 21.1.1發行。 [進一步了解](../rn/using/latest-release.md)
* Campaign 20.3.3發行。 [進一步了解](../rn/using/release--20-3.md)
* Campaign 20.2.4發行。 [進一步了解](../rn/using/release--20-2.md)
* Campaign 20.1.4發行。 [進一步了解](../rn/using/release--20-1.md)
* Campaign 19.2.4發行。 [進一步了解](../rn/using/release--19-2.md)
* Campaign 19.1.8發行。 [進一步了解](../rn/using/release--19-1.md)

這些版本隨附新的連線通訊協定：升級對於促銷活動伺服器和用戶端主控台而言都是強制性的，才能在&#x200B;**2021年6月30日**&#x200B;後連線至促銷活動。

瞭解如何在本節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本[。

**如何更新？**

身為代管客戶，Adobe不久將與您合作，將您的例項升級至較新版本。

身為內部部署／混合型客戶，您需要升級至其中一個較新版本，以便從新的客戶端主控台獲益，並確保在2021年6月30日之前順暢地轉換&#x200B;**。**

在升級所有實例後，Client Console也需要升級到此版本。

* 瞭解如何訪問[Adobe軟體分發](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)。

* [瞭解如何安裝Campaign Client Console](../installation/using/installing-the-client-console.md)。

## 與Experience Cloud觸發器整合

舊版驗證服務已到期。 觸發器整合驗證原本是以oAUTH驗證設定為基礎，以存取管線，現在已移至Adobe I/O。它將於2021年11月30日&#x200B;**退休。**[進一步瞭解](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/APIEOL.md?mv=email)。

**您受影響嗎？**

如果您的例項是在&#x200B;**舊版Campaign 19.1.8、20.2.4、Gold Standard 11**&#x200B;上執行，則您使用舊版Triggers整合透過Auth驗證：**您需要升級至較新版本並移至Adobe I/O**。

必須升級至下列其中一個新版本：

* 金標11 [進一步了解](../rn/using/gold-standard.md)
* Campaign 21.1.1發行。 [進一步了解](../rn/using/latest-release.md)
* Campaign 20.3.3發行。 [進一步了解](../rn/using/release--20-3.md)
* Campaign 20.2.4發行。 [進一步了解](../rn/using/release--20-2.md)
* Campaign 19.1.8發行。 [進一步了解](../rn/using/release--19-1.md)

瞭解如何在本節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本[。

**如何更新？**

當實例升級到較新版本後，所有客戶都需要按照[過程移至新的驗證模式](../integrations/using/configuring-adobe-io.md)。 這需要您產生新的Adobe I/OToken，並在實作中使用它。  

此外，對於混合環境，客戶需要確保在中端採購實例上配置了管道。 [進一步瞭解](../integrations/using/configuring-pipeline.md)。

[瞭解如何移轉至Adobe I/O](../integrations/using/configuring-adobe-io.md)。

## APN更新

### 基於HTTP/2的APNs提供者API

自2021年3月31日起，Apple推播通知服務(APN)將不再支援舊版二進位通訊協定。 ****[顯示全文](https://developer.apple.com/news/?id=c88acm2b)。

**您的影響力？**

如果您的例項是在Campaign 21.1以前的&#x200B;**版本上執行，而且您使用舊版Apple二進位通訊協定傳送推播通知，則需要更新為以HTTP/2為基礎的APNs提供者API。**

瞭解如何在本節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本[。

**如何更新？**

身為代管客戶，如果您已升級至新建版本，Adobe已將您的例項更新至HTTP/2架構的API。

身為內部部署／代管客戶，您需要更新您的設定。 [瞭解如何移轉至HTTP/2](https://helpx.adobe.com/tw/campaign/kb/migrate-to-apns-http2.html)

### APN根證書更新

在2021年3月29日，Apple推播通知服務(APNs)基礎架構更新將影響Adobe Campaign ClassiciOS頻道。 作業系統組態變更為&#x200B;**mandatory**&#x200B;以避免iOS推播頻道中斷。

在本頁](https://developer.apple.com/news/?id=7gx0a2lp)中進一步瞭解APN更改[。

**您受影響嗎？**

如果您使用促銷活動在iOS裝置上傳送推播通知，您會受到影響。

**如何更新？**

身為代管客戶，您不需採取任何動作：Adobe已將新的根證書整合到您的環境中。

身為內部部署／混合型客戶，您需要更新您的設定，以確保在2021年3月29日前順暢地進行&#x200B;**轉換。**

[瞭解如何整合新憑證](ios-certificate-update.md)。

## 有用的連結

* [升級您的環境](../production/using/build-upgrade.md)
* [建立升級常見問答集](../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic組建版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [讓新的用戶端主控台可供使用](../installation/using/client-console-availability-for-windows.md)
