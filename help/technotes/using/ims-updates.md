---
product: campaign
title: 技術 — 更新您的環境，使用IMS連接到Adobe Campaign。
description: 活動 — IMS更新
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '585'
ht-degree: 10%

---

# 如何更新您的環境以與IMS連接到Adobe Campaign。 {#acc-ims-faq}



於二零二一年六月三十日，本集團 [AdobeIdentity Management系統](https://helpx.adobe.com/enterprise/using/identity.html) (IMS)登錄功能可能會影響您繼續使用Adobe Campaign的能力。 瞭解如何確保您繼續使用Adobe Campaign Classicv7而不中斷。

## 什麼變了？

AdobeIdentity Management服務(IMS)已停止支援舊Internet Explorer版本 **2021年6月30日**。 [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

Adobe希望在2021年6月30日之前為所有客戶保留IMS功能。 IMS是安全框架的一部分，它允許用戶登錄客戶端控制台，因此Adobe Campaign。

要保留此功能，客戶必須在每台用戶的電腦上更新客戶端控制台，並確保您的 [Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), **Internet Explorer 11** 內置，安裝在每個用戶的電腦上。

## 您有受到影響嗎？

如果要連接到市場活動 [通過Adobe ID](../../integrations/using/about-adobe-id.md)通過AdobeIdentity Management服務(IMS)，並運行比下面列出的更舊版本的營銷活動，您會受到影響。

如果已升級但使用舊版本的MicrosoftInternet Explorer，則必須升級到Internet Explorer 11。

## 如何更新？

* 作為托管客戶，Adobe已將您的實例升級到較新版本。

* 作為內部/混合型客戶，您需要升級到上面列出的一個較新版本，以便從新的客戶端控制台中獲益，並確保無縫過渡 **2021年6月30日前**。

   必須升級到下面列出的其中一個新版本：

   * 金標11。 [了解更多](../../rn/using/gold-standard.md)
   * 市場活21.1.3發佈。 [了解更多](../../rn/using/latest-release.md)
   * 市場活20.2.5發佈。 [了解更多](../../rn/using/release--2020.md#release-20-2-5-build-9188)
   * 市場活20.1.4發佈。 [了解更多](../../rn/using/release--2020.md#release-20-1-4-build-9126)
   * 市場活19.2.4發佈。 [了解更多](../../rn/using/release--2019.md#release-19-2-4-build-9082)

   這些版本附帶了新的連接協定。 對於市場活動伺服器和客戶端控制台，必須進行升級：升級所有實例後，客戶機控制台需要升級到此版本，並能夠在升級後連接到市場活動 **2021年6月30日**。

此外，確保 [Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems), **Internet Explorer 11** 內置，安裝在每個用戶的電腦上。

## 常見問答集

**如何檢查我的促銷活動版本？**

瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。


**如何檢查我是否使用IMS?**

要檢查連接模式，您可以：

* 啟動市場活動客戶端控制台並訪問實例連接設定。 如果 **連接Adobe ID** 選項，您正在使用Adobe IMS。

   ![](../../integrations/using/assets/ims_1.png)

或

* 啟動市場活動客戶端控制台，並檢查連接窗口。 如下面的螢幕所示，如果您正在與Adobe ID連接，則您正在使用IMS。

   ![](../../integrations/using/assets/adobeID.png)

**連接警告消息**

如果用戶需要更新其客戶端控制台或使用舊版本的MicrosoftInternet Explorer，則以下警告消息將可見： **您需要安裝Windows和/或您的Adobe應用的最新更新。**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

如果您看到此類警告，請確保安裝所使用的作業系統的最新更新。 [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

如果您未更新Internet Explorer版本，則會看到以下消息，並且無法再連接到Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 有用連結

* [升級環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [使新客戶端控制台可供用戶使用](../../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)
* [訪問Adobe軟體分發](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)
* [下載Campaign Classic內部版本](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
