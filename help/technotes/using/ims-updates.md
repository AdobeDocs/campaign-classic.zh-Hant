---
product: campaign
title: Technote — 更新您的環境以使用IMS連線至Adobe Campaign
description: 行銷活動 — IMS更新
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 70240d5f62fd3d7b755389b5ad8c4b499c94657d
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 9%

---

# 如何更新您的環境以使用IMS連線至Adobe Campaign {#acc-ims-faq}

![](../../assets/v7-only.svg)

2021年6月30日變更 [AdobeIdentity Management系統](https://helpx.adobe.com/enterprise/using/identity.html) (IMS)登入功能可能會影響您繼續使用Adobe Campaign的能力。 了解如何確保您能持續使用Adobe Campaign Classic v7而不中斷。

## 有什麼改變？

AdobeIdentity Management服務(IMS)已停止支援舊版Internet Explorer **2021年6月30日**. [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

Adobe想要在2021年6月30日之前保留所有客戶的IMS功能。 IMS是安全架構的一部分，可讓使用者登入用戶端主控台，進而登入Adobe Campaign。

若要保留此功能，客戶必須更新每個使用者電腦上的用戶端主控台，並確保您的 [Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)，使用 **Internet Explorer 11** 內建，安裝在每個使用者的電腦上。

## 您有受到影響嗎？

如果您要連線至Campaign [透過Adobe ID](../../integrations/using/about-adobe-id.md)，透過AdobeIdentity Management服務(IMS)，以及執行比下列更舊版本的Campaign，您會受到影響。

如果您已升級但使用舊版Microsoft Internet Explorer，則必須升級至Internet Explorer 11。

## 如何更新？

* 身為托管客戶，Adobe已將您的執行個體升級至較新版本。

* 身為內部部署/混合部署客戶，您需要升級至上述任一較新版本，以受益於新的用戶端主控台，並確保順暢轉換 **2021年6月30日前**.

   必須升級至下列其中一個新版本：

   * 金標11。 [了解更多](../../rn/using/gold-standard.md)
   * Campaign 21.1.3版。 [了解更多](../../rn/using/latest-release.md)
   * Campaign 20.2.5版。 [了解更多](../../rn/using/release--2020.md#release-20-2-5-build-9188)
   * Campaign 20.1.4版。 [了解更多](../../rn/using/release--2020.md#release-20-1-4-build-9126)
   * Campaign 19.2.4版。 [了解更多](../../rn/using/release--2019.md#release-19-2-4-build-9082)

   這些版本隨附新的連線通訊協定。 升級對於Campaign伺服器和用戶端主控台都是強制性的：升級所有執行個體後，用戶端主控台必須升級至此版本，並且在升級後還能連線至Campaign **2021年6月30日**.

此外，請確定您的 [Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)，使用 **Internet Explorer 11** 內建，安裝在每個使用者的電腦上。

## 常見問答集

**如何檢查我的Campaign版本？**

了解如何檢查您的版本 [在本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).


**如何檢查我是否使用IMS?**

若要檢查連線模式，您可以：

* 啟動Campaign用戶端主控台並存取您的執行個體連線設定。 若 **連線至Adobe ID** 選項，則您會使用Adobe IMS。

   ![](../../integrations/using/assets/ims_1.png)

或

* 啟動Campaign用戶端主控台，並檢查您的連線視窗。 如果您連線Adobe ID（如下方畫面所示），表示您使用的是IMS。

   ![](../../integrations/using/assets/adobeID.png)

**連接警告消息**

如果使用者需要更新其用戶端主控台或使用舊版Microsoft Internet Explorer，將會看到下列警告訊息： **您需要將最新更新的安裝到Windows和/或您的Adobe應用程式。**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

如果出現此類警告，請確保安裝所用作業系統的最新更新。 [了解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

如果您未更新Internet Explorer版本，會看到下列訊息，且無法再連線至Adobe Campaign:

![](../../integrations/using/assets/do-not-localize/errorUpdateReq.png)

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 實用連結

* [升級您的環境](../../production/using/build-upgrade.md)
* [建置升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [讓使用者能使用新的用戶端主控台](../../installation/using/client-console-availability-for-windows.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)
* [訪問AdobeSoftware Distribution](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=en)
* [下載Campaign Classic組建](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)
