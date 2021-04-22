---
solution: Campaign Classic
product: campaign
title: Technote
description: Technote
hide: true
hidefromtoc: true
translation-type: tm+mt
source-git-commit: 5b552afa784b479853335daf13eb02e5e069eb4d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 6%

---

# 追蹤的URL簽名問題{#tracked-urls}

在最近的變更後，當URL簽名在促銷活動中作用時，追蹤的URL可能會失敗。 有些郵箱受到的影響比其他郵箱大，因為有些公司有特定的安全工具，這些工具可能會影響連結並更改URL簽名機制。

因此，Adobe建議您停用追蹤連結的簽名機制。 此程式將修正舊的追蹤連結，除了以雙重逸出方式接收的連結。

請注意，取消訂閱連結可能會像其他連結一樣失敗，頻率是從主機到主機的變數，但小於1%。

**您受影響嗎？**

為了改善安全性，[促銷活動金級標準8](../rn/using/gold-standard.md#gs8) - 2020年4月中已引入追蹤電子郵件連結的簽名機制，並預設為所有從建置版本19.1.4(9032@3a9dc9c)和促銷活動20.2開始的客戶啟用。

如果您的環境在下列其中一個版本上執行，您可能會受到影響：

* 金標7比11 [了解更多](../rn/using/gold-standard.md)
* Campaign 21.1.1和21.1.2版本。 [了解更多](../rn/using/latest-release.md)
* Campaign 20.3.1到20.3.3版本。 [了解更多](../rn/using/release--20-3.md)
* Campaign 20.2.1到20.2.3版本。 [了解更多](../rn/using/release--20-2.md)
* Campaign 20.1.1到21.1.3版本。 [了解更多](../rn/using/release--20-1.md)
* Campaign 19.2.2到19.2.3版本。 [了解更多](../rn/using/release--19-2.md)
* Campaign 19.1.5到19.1.7版。 [了解更多](../rn/using/release--19-1.md)

瞭解如何在本節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中檢查您的版本[。

**如何更新？**

身為&#x200B;**代管客戶**,Adobe將與您合作，不久將更新您的設定。

身為&#x200B;**內部部署／混合客戶**，您需要更新配置。

請遵循下列步驟：

1. 在[伺服器設定檔](../installation/using/the-server-configuration-file.md)(serverConf.xml)中，將&#x200B;**signEmailLinks**&#x200B;變更為&#x200B;**false**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>**config-`<instance>`.xml**&#x200B;檔案會覆寫&#x200B;**serverConf.xml**&#x200B;設定。 如果&#x200B;**signEmailLinks**&#x200B;存在於&#x200B;**config-`<instance>`.xml**（其中&#x200B;**instance**&#x200B;是實例的名稱）中，則還必須將其轉換為&#x200B;**false**。


**影響是什麼？**

維護作業最長需要25分鐘的停機時間，在此期間，所有傳送、追蹤連結和API呼叫將無法運作。

更新完成後，所有連結都會如預期般運作。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡[Adobe客戶服務](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

