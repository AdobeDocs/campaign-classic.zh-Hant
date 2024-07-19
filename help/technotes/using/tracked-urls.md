---
product: campaign
title: 追蹤的 URL 簽名問題
description: 追蹤的 URL 簽名問題
feature: Technote
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 30%

---

# 追蹤的 URL 簽名問題 {#tracked-urls}



在最近變更後，當Campaign中的URL簽名作用中時，追蹤的URL可能會失敗。 有些信件匣受到的影響比其他信件匣大，因為有些公司有特定的安全工具，這些工具可能會影響連結並替代 URL 簽名機制。

因此，Adobe建議您停用追蹤連結的簽名機制。 此程式會修正舊的追蹤連結，除了以雙重逸出收到的追蹤連結以外。

請注意，取消訂閱的連結可能會像其他連結一樣失效，頻率根據每台主機而定，但機率小於 1%。

**您有受到影響嗎？**

為了改善安全性，追蹤電子郵件中連結的簽名機制已在[Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - 2020年4月中匯入，並預設對從Build 19.1.4 (9032@3a9dc9c)和Campaign 20.2開始的所有客戶啟用。

如果您的環境在下列其中一個版本上執行，則可能會受到影響：

* Gold Standard 8至11。 [了解更多](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1 (build 9277)至21.1.2 (build 9282)版本。 [了解更多](../../rn/using/latest-release.md)
* Campaign 20.3.1 (build 9228)至20.3.3 (build 9234)版本。
* Campaign 20.2.1 (build 9178)至20.2.4 (build 9187)版本。
* Campaign 20.1.1 (build 9122)至21.1.3 (build 9124)版本。
* Campaign 19.2.2 (build 9080)至19.2.3 (build 9081)版本。
* Campaign 19.1.5 (build 9033)至19.1.7 (build 9036)版本。


在本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的[版本。

**如何更新？**

作為&#x200B;**託管客戶**，Adobe將儘快與您合作更新您的設定。

作為&#x200B;**內部部署/混合式客戶**，您需要更新設定。

請依照下列步驟操作：

1. 在[伺服器設定檔](../../installation/using/the-server-configuration-file.md) (serverConf.xml)中，將&#x200B;**signEmailLinks**&#x200B;變更為&#x200B;**false**。
1. 重新啟動&#x200B;**nlserver**&#x200B;服務。
1. 在追蹤伺服器上，重新啟動網頁伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>**config-`<instance>`.xml**&#x200B;檔案會覆寫&#x200B;**serverConf.xml**&#x200B;設定。 如果&#x200B;**signEmailLinks**&#x200B;存在於&#x200B;**config-`<instance>`.xml**&#x200B;中（其中&#x200B;**instance**&#x200B;是您執行個體的名稱），它也必須轉換為&#x200B;**false**。
>

**會有什麼影響？**

維護作業最長需要 25 分鐘的停機時間，在此期間，所有傳送、追蹤連結和 API 呼叫都無法運作。

更新完成後，所有連結都會如預期恢復運作。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>
