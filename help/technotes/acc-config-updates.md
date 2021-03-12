---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 74610fa197dd9ef27342e08dd0ba3403c1a9acc0
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 4%

---


# Adobe Campaign配置更新- 2021年3月{#acc-config-updates}

您必須使用最新的組建版本和產品修正來更新您的基礎架構和設定。 這些修正是確保服務連續性和安全性的必備修正。

促銷活動使用者必須升級至下列其中一個最新版本：

* 金標11 [進一步了解](../rn/using/gold-standard.md)
* Campaign 21.1.1發行。 [進一步了解](../rn/using/latest-release.md)
* Campaign 20.3.3發行。 [進一步了解](../rn/using/release--20-3.md)
* Campaign 20.2.4發行。 [進一步了解](../rn/using/release--20-2.md)
* Campaign 20.1.4發行。 [進一步了解](../rn/using/release--20-1.md)
* Campaign 19.2.4發行。 [進一步了解](../rn/using/release--19-2.md)
* Campaign 19.1.8發行。 [進一步了解](../rn/using/release--19-1.md)

這些建置可確保特定促銷活動服務的連續性：Experience Cloud觸發器整合、APNs身份驗證和影響AdobeIdentity Management服務(IMS)身份驗證機制的新連接協定。

身為代管客戶，Adobe會定期通知您需要的建置升級。 您必須依照建議進行升級，以確保符合規範。

身為內部部署／混合型客戶，您必須升級至上述版本之一。 此外，還必須執行一些手動任務，以確保您的環境安全，並準備好迎接Adobe或第三方系統即將進行的更改。

>[!NOTE]
>
>如需這些變更的任何問題，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 安全性更新

最新的促銷活動版本隨附安全性修正，可加強針對伺服器端偽造要求(SSRF)問題的保護。 在本頁瞭解更多[的資訊。](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)

**您受影響嗎？**

如果您的環境建置低於Campaign 21.1，您會受到影響。

**如何更新？**

您必須升級至上述任一較新的版本。

* 身為混合型客戶，Adobe會將中端採購執行個體升級至新版本，並強烈建議您也升級其行銷執行個體。

   新建版本至少與Campaign Classic17.9版本相容，但為避免任何安全性差距，Adobe強烈建議將所有執行個體升級為新建版本。 

* 身為內部部署客戶，您被要求將行銷和中部採購實例升級至較新的版本。

>[!CAUTION]
>
>如果您目前無法升級，**必須聯絡Adobe客戶服務團隊，以手動套用例項的安全性修正。**


## 促銷活動用戶端主控台更新

最新的Gold Standard 11組建版本修正了回歸，使主控台無法使用某些元件，例如日期選擇器和影像管理在傳送中。 控制台升級是必備的。

[進一步瞭解](../rn/using/gold-standard.md)。

## 透過IMS連線至促銷活動

Adobe身分服務(IMS)將從2021年6月30日起停止支援舊版Internet Explorer。 [進一步瞭解](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。已更新促銷活動主控台，以確保與IMS相容。

**您受影響嗎？**

如果您透過Adobe ID](../integrations/using/about-adobe-id.md)透過Adobe身分服務(IMS)連線至促銷活動[，則必須升級至上述其中一個新版本。 這些版本隨附新的連線通訊協定：升級對於促銷活動伺服器和用戶端主控台而言都是強制性的，因此在&#x200B;**2021年6月30日**&#x200B;之後，才能連線至促銷活動。

**如何更新？**

身為代管客戶，您不需採取任何動作：Adobe已將實例升級到較新版本。

身為內部部署／混合型客戶，您需要升級至其中一個較新版本，以便從新的客戶端主控台獲益，並確保在2021年6月30日之前順暢地轉換&#x200B;**。**

在升級所有實例後，客戶端控制台也需要升級到此版本。

* 瞭解如何訪問[Adobe軟體分發](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)。

* [瞭解如何安裝Campaign Client主控台](../installation/using/installing-the-client-console.md)。

## 與Experience Cloud觸發器整合

舊版驗證服務已到期。 觸發器整合驗證原本是以oAUTH驗證設定為基礎，以存取管線，現在已移至Adobe I/O。它將於2021年4月30日&#x200B;**退休。**[進一步瞭解](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411)。

**您受影響嗎？**

如果您使用舊版的觸發器整合（透過oAuth驗證）,**您必須移至Adobe I/O**。

**如何更新？**

當實例升級到較新版本後，所有客戶都需要按照[過程移至新的驗證模式](../integrations/using/configuring-adobe-io.md)。 這需要產生新的Adobe I/OToken，並在實作中使用它。  

此外，對於混合環境，客戶需要確保在中端採購實例上配置了管道。 [進一步瞭解](../integrations/using/configuring-pipeline.md)。

[瞭解如何移轉至Adobe I/O](../integrations/using/configuring-adobe-io.md)。

## 基於HTTP/2的APNs提供者API

自2021年3月31日起，Apple推播通知服務(APN)將不再支援舊版二進位通訊協定。 [顯示全文](https://developer.apple.com/news/?id=c88acm2b)。

**您的影響力？**

如果您的例項是在舊版Campaign 21.1上執行，並使用舊版Apple二進位通訊協定傳送推播通知，您必須更新為以HTTP/2為基礎的APNs提供者API。

**如何更新？**

身為代管客戶，您不需採取任何動作：Adobe已將您的例項更新為以HTTP/2為基礎的API。

身為內部部署／代管客戶，您需要更新您的設定。 [瞭解如何移轉至HTTP/2](https://helpx.adobe.com/tw/campaign/kb/migrate-to-apns-http2.html)

## APN根證書更新

在2021年3月29日，Apple推播通知服務(APNs)基礎架構更新將影響Adobe Campaign ClassiciOS頻道。 作業系統組態變更為&#x200B;**mandatory**&#x200B;以避免iOS推播頻道中斷。

在本頁](https://developer.apple.com/news/?id=7gx0a2lp)中進一步瞭解APN更改[。

**您受影響嗎？**

如果您使用促銷活動在iOS裝置上傳送推播通知，您會受到影響。

**如何更新？**

身為代管客戶，您不需採取任何動作：Adobe已將新的根證書整合到您的環境中。

身為內部部署／混合型客戶，您需要更新您的設定，以確保在2021年3月29日前順暢地進行&#x200B;**轉換。**

[瞭解如何整合新憑證](ios-certificate-update.md)。
