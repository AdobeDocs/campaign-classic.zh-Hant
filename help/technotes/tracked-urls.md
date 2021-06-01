---
product: campaign
title: 技術檔案
description: 技術檔案
hide: true
hidefromtoc: true
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 35%

---

# 追蹤的 URL 簽名問題{#tracked-urls}

在最近的變更後，當URL簽名在Campaign中處於作用中狀態時，追蹤的URL可能會失敗。 有些信件匣受到的影響比其他信件匣大，因為有些公司有特定的安全工具，這些工具可能會影響連結並替代 URL 簽名機制。

因此，Adobe建議您停用追蹤連結的簽名機制。 此程式會修正除了收到含有雙重逸出之連結以外的舊追蹤連結。

請注意，取消訂閱的連結可能會像其他連結一樣失效，頻率根據每台主機而定，但機率小於 1%。

**您有受到影響嗎？**

為了改善安全性，[Campaign Gold Standard 8](../rn/using/gold-standard.md#gs8) - 2020年4月中已導入追蹤電子郵件連結的簽章機制，並針對從版本編號19.1.4(9032@3a9dc9c)和Campaign 20.2開始的所有客戶，預設啟用此機制。

如果您的環境正在下列其中一個版本上執行，您可能會受到影響：

* Gold Standard 8至11。 [瞭解更多](../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1（版本編號9277）至21.1.2（版本編號9282）版本。 [瞭解更多](../rn/using/latest-release.md)
* Campaign 20.3.1（版本編號9228）至20.3.3（版本編號9234）版本。 [瞭解更多](../rn/using/release--20-3.md)
* Campaign 20.2.1（版本編號9178）至20.2.4（版本編號9187）版本。 [瞭解更多](../rn/using/release--20-2.md)
* Campaign 20.1.1（版本編號9122）至21.1.3（版本編號9124）版本。 [瞭解更多](../rn/using/release--20-1.md)
* Campaign 19.2.2（版本編號9080）至19.2.3（版本編號9081）版本。 [瞭解更多](../rn/using/release--19-2.md)
* Campaign 19.1.5（版本編號9033）至19.1.7（版本編號9036）版本。 [瞭解更多](../rn/using/release--19-1.md)

在本小節](../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中了解如何檢查您的版本[。

**如何更新？**

作為&#x200B;**托管客戶**,Adobe會與您合作，立即更新您的設定。

身為&#x200B;**內部部署/混合客戶**，您需要更新您的設定。

請依照下列步驟操作：

1. 在[伺服器配置檔案](../installation/using/the-server-configuration-file.md)(serverConf.xml)中，將&#x200B;**signEmailLinks**&#x200B;更改為&#x200B;**false**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>**config-`<instance>`.xml**&#x200B;檔案覆蓋&#x200B;**serverConf.xml**&#x200B;設定。 如果&#x200B;**signEmailLinks**&#x200B;存在於&#x200B;**config-`<instance>`.xml**（其中&#x200B;**instance**&#x200B;是實例的名稱）中，則還必須將其轉換為&#x200B;**false**。


**會有什麼影響？**

維護作業最長需要 25 分鐘的停機時間，在此期間，所有傳送、追蹤連結和 API 呼叫都無法運作。

更新完成後，所有連結都會如預期恢復運作。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

