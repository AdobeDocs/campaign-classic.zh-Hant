---
product: campaign
title: 更新您的環境以使用IMS連線至Adobe Campaign
description: 行銷活動 — IMS更新
exl-id: ecb5a258-a150-46a3-8b83-2b2c06d873ee
source-git-commit: 1a9e0f8bf374e10af938d15dcebe943819ae327b
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 9%

---

# 如何更新您的環境以使用IMS連線至Adobe Campaign {#acc-ims-faq}

![](../../assets/v7-only.svg)

2021年6月30日起，將變更[AdobeIdentity Management系統](https://helpx.adobe.com/enterprise/using/identity.html)(IMS)登入功能，這可能影響您繼續使用Adobe Campaign的能力。 了解如何確保您能持續使用Adobe Campaign Classic v7而不中斷。

## 有什麼改變？

AdobeIdentity Management服務(IMS)將於2021年6月30日起停止支援舊版Internet Explorer。**** [深入瞭解](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)。

Adobe想要在2021年6月30日之前保留所有客戶的IMS功能。 IMS是安全架構的一部分，可讓使用者登入用戶端主控台，進而登入Adobe Campaign。

若要保留此功能，客戶必須在每台用戶的電腦上更新客戶端控制台，並確保在每台用戶的電腦上安裝了[Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)的最新更新，其中&#x200B;**Internet Explorer 11**&#x200B;內置。

## 您有受到影響嗎？

如果您透過Adobe ID](../../integrations/using/about-adobe-id.md)透過AdobeIdentity Management服務(IMS)連線至促銷活動[，並執行比下列更舊版本的促銷活動，則會受到影響。

如果您已升級但使用舊版Microsoft Internet Explorer，則必須升級到Internet Explorer 11。

## 如何更新？

* 身為托管客戶，Adobe已將您的執行個體升級至較新版本。

* 身為內部部署/混合部署客戶，您需要升級至上述任一較新版本，以便從新的用戶端主控台獲益，並在2021年6月30日之前確保順暢轉換&#x200B;****。

   必須升級至下列其中一個新版本：

   * 金標11。 [瞭解更多](../../rn/using/gold-standard.md)
   * Campaign 21.1.3版。 [瞭解更多](../../rn/using/latest-release.md)
   * Campaign 20.2.5版。 [瞭解更多](../../rn/using/release--20-2.md)
   * Campaign 20.1.4版。 [瞭解更多](../../rn/using/release--20-1.md)
   * Campaign 19.2.4版。 [瞭解更多](../../rn/using/release--19-2.md)
   * Campaign 19.1.8版。 [瞭解更多](../../rn/using/release--19-1.md)

   這些版本隨附新的連線通訊協定。 升級對於Campaign伺服器和用戶端主控台都是強制性的：升級所有執行個體後，用戶端主控台必須升級至此版本，並且在2021年6月30日&#x200B;**之後，還能連線至Campaign。**

此外，確保在每台用戶的電腦上安裝[Windows版本](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)的最新更新，並內置&#x200B;**Internet Explorer 11**。

## 常見問答集

**如何檢查我的Campaign版本？**

在本小節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。


**如何檢查我是否使用IMS?**

若要檢查連線模式，您可以：

* 啟動Campaign用戶端主控台並存取您的執行個體連線設定。 如果選取&#x200B;**連線Adobe ID**&#x200B;選項，表示您使用的是Adobe IMS。

   ![](../../integrations/using/assets/ims_1.png)

或

* 啟動Campaign用戶端主控台，並檢查您的連線視窗。 如果您連線Adobe ID（如下方畫面所示），表示您使用的是IMS。

   ![](../../integrations/using/assets/adobeID.png)

**連接警告消息**

如果用戶需要更新其客戶端控制台或使用舊版Microsoft Internet Explorer，則會顯示以下警告消息：**您需要將最新更新的安裝到Windows和/或您的Adobe應用。**

![](../../integrations/using/assets/do-not-localize/errorMsg.png)

如果出現此類警告，請確保安裝所用作業系統的最新更新。 [瞭解更多](https://helpx.adobe.com/x-productkb/global/update-operating-system-and-browser.html)

**2021年6月30日後**，您會看到下列訊息，且將無法再連線至Adobe Campaign:

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
