---
product: campaign
title: 技術 — Adobe Campaign配置更新
description: Adobe Campaign配置更新
exl-id: 7db02123-2e2a-40d9-8385-728ff69985e4
source-git-commit: f4513834cf721f6d962c7c02c6c64b2171059352
workflow-type: tm+mt
source-wordcount: '1125'
ht-degree: 12%

---

# Adobe Campaign配置更新2021 {#acc-config-updates}

![](../../assets/v7-only.svg)

基礎架構和設定應定期更新為最新的版本和產品修復。 這些修復是確保服務和安全性的連續性所必需的。 此外，需要升級才能與第三方更改保持一致。

作為 **托管或Managed Services客戶**,Adobe將定期通知您生成升級。 您將需要根據建議進行升級以確保符合要求。

作為 **內部或混合型客戶**，您應根據最新發佈的版本定期升級實施。

出於安全原因，您現在必須升級到下面列出的版本之一。 除了標準升級步驟外，還必須執行一些手動任務，以確保您的環境安全，並準備好從Adobe或第三方系統進行即將進行的更改。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 安全更新 {#acc-security-updates}

最新的活動版本附帶了一個安全修復程式，它加強了針對伺服器端請求偽造(SSRF)問題的保護。 在[本頁](https://helpx.adobe.com/tw/security/products/campaign/apsb21-04.html)中深入瞭解。

**您有受到影響嗎？**

如果環境的構建比下面列出的環境低，則會影響您：

* 金標11。 [了解更多](../../rn/using/gold-standard.md)
* 市場活21.1.1發佈。 [了解更多](../../rn/using/latest-release.md)
* 市場活20.2.5發佈。 [了解更多](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* 市場活20.1.4發佈。 [了解更多](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* 市場活19.2.4發佈。 [了解更多](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* 市場活19.1.8發佈。 [了解更多](../../rn/using/release--2019.md#release-19-1-8-build-9039)

瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

**如何更新？**

您需要升級到上面列出的更新版本之一。

* 作為混合型客戶，Adobe將通知您中間採購實例的計畫升級日期。 Adobe強烈建議您也升級營銷實例。

   新版本向後相容Campaign Classic17.9版，但Adobe強烈建議對所有實例進行升級以解決安全漏洞

* 作為內部客戶，您需要將市場營銷和中間採購實例升級為最新版本。

>[!CAUTION]
>
>如果無法在建議的時間內升級， **您應聯繫Adobe客戶服務團隊，以在您的實例上應用短期手動安全修復**。

## Campaign Classic客戶端控制台更新  {#acc-cc-updates}

的 **現在可用** 應安裝以下控制台版本以解決最近確定的回歸。 此回歸阻止在交貨中使用客戶端控制台的某些元件，如日期選取器和映像管理。 **控制台升級** 的子菜單。

* 最新的金標標準11內部版本9032@10c2709。 [了解更多](../../rn/using/gold-standard.md)
* 市場活20.1.4發佈。 [了解更多](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* 市場活19.2.4發佈。 [了解更多](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* 市場活19.1.8發佈。 [了解更多](../../rn/using/release--2019.md#release-19-1-8-build-9039)

## AdobeIdentity Management系統(IMS)更新

Adobe身份服務(IMS)將停止支援舊Internet Explorer版本 **2021年6月30日**。 [了解更多資訊](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

需要升級Campaign Client Console以確保與Adobe IMS的相容性。

**您有受到影響嗎？**

如果要連接到市場活動 [通過Adobe ID](../../integrations/using/about-adobe-id.md)，通過AdobeIdentity Management服務(IMS)，升級到下面列出的一個新版本是強制性的：

* 金標11。 [了解更多](../../rn/using/gold-standard.md)
* 市場活21.1.1發佈。 [了解更多](../../rn/using/latest-release.md)
* 市場活20.2.5發佈。 [了解更多](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* 市場活20.1.4發佈。 [了解更多](../../rn/using/release--2020.md#release-20-1-4-build-9126)
* 市場活19.2.4發佈。 [了解更多](../../rn/using/release--2019.md#release-19-2-4-build-9082)
* 市場活19.1.8發佈。 [了解更多](../../rn/using/release--2019.md#release-19-1-8-build-9039)

這些版本附帶了新的連接協定：升級對於市場活動伺服器和客戶端控制台來說都是必需的，以便在市場活動結束後能夠連接到市場活動 **2021年6月30日**。

瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

**如何更新？**

作為托管客戶，Adobe將與您合作，很快將您的實例升級到較新版本。

作為內部/混合型客戶，您需要升級到其中一個較新的版本，以便從新的客戶端控制台中獲益，並確保無縫過渡 **2021年6月30日前**。

升級所有實例後，客戶端控制台也需要升級到此版本。

* 瞭解如何訪問 [Adobe軟體分發](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)。

* [瞭解如何安裝市場活動客戶端控制台](../../installation/using/installing-the-client-console.md)。

## 與Experience Cloud觸發器整合 {#acc-triggers-updates}

舊版oAuth身份驗證服務已到期。 觸發器整合身份驗證最初基於訪問管道的oAUTH身份驗證設定，現已移到Adobe I/O。具有市場活動的舊式身份驗證模式 [已退休](https://experienceleaguecommunities.adobe.com/t5/adobe-analytics-discussions/adobe-analytics-legacy-api-end-of-life-notice/td-p/385411) 上 **2021年9月**。 託管環境繼續使用延伸功能，直到 **2022 年 2 月 23 日**。作為本地或混合型客戶，請與Adobe客戶服務部門聯繫，將支援期限延長至2022年2月。 您必須向 Adobe 提供 [OAuth 應用程式的 AppID](../../integrations/using/configuring-pipeline.md?lang=en#step-optional)。

**您有受到影響嗎？**

如果實例在 **舊版本高於市場活動19.1.8、20.2.4、金標標準11**，則您正在使用通過oAuth身份驗證的較舊版本的觸發器整合： **您需要升級到較新的版本，然後轉到Adobe I/O**。

必須升級到下面列出的其中一個新版本：

* 金標11。 [了解更多](../../rn/using/gold-standard.md)
* 市場活21.1.1發佈。 [了解更多](../../rn/using/latest-release.md)
* 市場活20.2.5發佈。 [了解更多](../../rn/using/release--2020.md#release-20-2-5-build-9188)
* 市場活19.1.8發佈。 [了解更多](../../rn/using/release--2019.md#release-19-1-8-build-9039)

瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

**如何更新？**

一旦實例升級到較新版本，所有客戶都需要遵循 [過程移到新的身份驗證模式](../../integrations/using/configuring-adobe-io.md)。 這要求您生成新的Adobe I/O令牌，並在實現中使用它。  

此外，對於混合環境，客戶需要確保在中間採購實例上配置管道。 [了解更多資訊](../../integrations/using/configuring-pipeline.md)。

[瞭解如何遷移到Adobe I/O](../../integrations/using/configuring-adobe-io.md)。

## APN更新 {#acc-apns-updates}

### 基於HTTP/2的APNs提供程式API

自 **2021年3月31日**,Apple推送通知服務(APN)不再支援舊式二進位協定。 [顯示全文](https://developer.apple.com/news/?id=c88acm2b)。

**您受影響嗎？**

如果實例在 **舊版本高於市場活動21.1,** 並且您使用舊式Apple二進位協定發送推送通知，您需要更新到基於HTTP/2的APNs提供程式API。

瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

**如何更新？**

作為托管客戶，如果您已升級到新生成，Adobe已將您的實例更新到基於HTTP/2的API。

作為內部/混合客戶，您需要更新配置。

### APN根證書更新

2021年3月29日，Apple推送通知服務(APNs)基礎架構更新影響了Adobe Campaign ClassiciOS頻道。 作業系統配置更改為 **強制** 避免iOS推送頻道中斷。

瞭解有關APN更改的更多資訊 [此頁](https://developer.apple.com/news/?id=7gx0a2lp)。

**您有受到影響嗎？**

如果您使用「市場活動」在iOS設備上發送推送通知，則會受到影響。

**如何更新？**

作為托管客戶，無需執行任何操作：Adobe已將新根證書併入您的環境。

作為本地/混合型客戶，您需要更新配置以確保無縫過渡 **2021年3月29日前**。

[瞭解如何合併新證書](ios-certificate-update.md)。

## 有用連結

* [升級環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [下載Campaign Classic內部版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
* [使新客戶端控制台可供用戶使用](../../installation/using/client-console-availability-for-windows.md)
