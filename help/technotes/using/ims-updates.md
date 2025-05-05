---
product: campaign
title: 技術檔案 — 更新您的環境，以便使用IMS連線至Adobe Campaign
description: Campaign - IMS更新
feature: Technote, Upgrade
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 5%

---

# 如何更新您的環境，以便使用IMS連線至Adobe Campaign {#acc-ims-faq}



2021年6月30日起，已對[AdobeIdentity Management系統](https://helpx.adobe.com/tw/enterprise/using/identity.html) (IMS)登入功能進行變更，可能會影響您繼續使用Adobe Campaign的能力。 瞭解如何確保您繼續使用Adobe Campaign Classic v7而不中斷。

## 哪些部分有所變更？

AdobeIdentity Management服務(IMS)已於&#x200B;**2021年6月30日**&#x200B;停止支援舊版Internet Explorer。 [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

Adobe想要為所有超過2021年6月30日的客戶保留IMS功能。 IMS是安全性架構的一部分，可讓使用者登入使用者端主控台，即Adobe Campaign。

若要保留此功能，客戶必須在每位使用者的電腦上更新使用者端主控台，並確定已在每位使用者的電腦上安裝[Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems) （內建&#x200B;**Internet Explorer 11**）的最新更新。

## 您有受到影響嗎？

如果您是透過Adobe ID[&#128279;](../../integrations/using/about-adobe-id.md)、透過AdobeIdentity Management Service (IMS)連線至Campaign ，且執行比下列版本舊的Campaign，則會受到影響。

如果您已經升級，但使用的是舊版Microsoft Internet Explorer，則必須升級至Internet Explorer 11。

## 如何更新？

* 作為託管客戶，Adobe已將您的執行個體升級至較新版本。

* 作為內部部署/混合部署客戶，您需要升級至上述較新版本之一，以受益於新的使用者端主控台，並確保在2021年6月30日之前&#x200B;**無縫轉換**。

  必須升級至下列新版本之一：

   * Gold Standard 11. [了解更多](../../rn/using/gold-standard.md)
   * Campaign 21.1.3版本。 [了解更多](../../rn/using/latest-release.md)
   * Campaign 20.2.5版。
   * Campaign 20.1.4版。
   * Campaign 19.2.4版。

  這些版本隨附新的連線通訊協定。 Campaign伺服器和使用者端主控台都必須升級：所有執行個體升級後，使用者端主控台都必須升級為此版本，並且必須在&#x200B;**2021年6月30日**&#x200B;之後連線至Campaign。

此外，請確定您的[Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems) （內建&#x200B;**Internet Explorer 11**&#x200B;版）的最新更新已安裝在每位使用者的電腦上。

## 常見問答集

**如何檢查我的Campaign版本？**

在本節[&#128279;](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。


**如何檢查我是否使用IMS？**

若要檢查您的連線模式，您可以：

* 啟動Campaign使用者端主控台並存取您的執行個體連線設定。 如果選取了&#x200B;**使用Adobe ID**&#x200B;連線，表示您使用的是Adobe IMS。

  ![](../../integrations/using/assets/ims_1.png)

或

* 啟動Campaign使用者端主控台，並檢查您的連線視窗。 如果您正在與Adobe ID連線（如以下畫面所示），則表示您使用的是IMS。

  ![](../../integrations/using/assets/adobeID.png)

**連線警告訊息**

如果使用者需要更新使用者端主控台或使用舊版Microsoft Internet Explorer，使用者可以看到下列警告訊息： **您必須安裝最新更新至Windows和/或您的Adobe應用程式。**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

如果您看到這類警告，請確定您已安裝目前使用之作業系統的最新更新。 [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

如果您未更新Internet Explorer版本，則會看到以下訊息，且無法再連線至Adobe Campaign：

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>

## 有用的連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [讓使用者可以使用新的使用者端主控台](../../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)
* [存取Adobe軟體發佈](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=zh-Hant)
* [下載Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
