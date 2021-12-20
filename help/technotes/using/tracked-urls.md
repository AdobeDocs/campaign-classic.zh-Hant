---
product: campaign
title: 技術檔案
description: 技術檔案
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 70240d5f62fd3d7b755389b5ad8c4b499c94657d
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 35%

---

# 追蹤的 URL 簽名問題 {#tracked-urls}

![](../../assets/v7-only.svg)

在最近的變更後，當URL簽名在Campaign中處於作用中狀態時，追蹤的URL可能會失敗。 有些信件匣受到的影響比其他信件匣大，因為有些公司有特定的安全工具，這些工具可能會影響連結並替代 URL 簽名機制。

因此，Adobe建議您停用追蹤連結的簽名機制。 此程式會修正除了收到含有雙重逸出之連結以外的舊追蹤連結。

請注意，取消訂閱的連結可能會像其他連結一樣失效，頻率根據每台主機而定，但機率小於 1%。

**您有受到影響嗎？**

為提高安全性，已在 [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - 2020年4月 — 並預設為從Build 19.1.4(9032@3a9dc9c)和Campaign 20.2開始的所有客戶啟用。

如果您的環境正在下列其中一個版本上執行，您可能會受到影響：

* Gold Standard 8至11。 [了解更多](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1（版本編號9277）至21.1.2（版本編號9282）版本。 [了解更多](../../rn/using/latest-release.md)
* Campaign 20.3.1（版本編號9228）至20.3.3（版本編號9234）版本。 [了解更多](../../rn/using/release--2020.md#release-20-3)
* Campaign 20.2.1（版本編號9178）至20.2.4（版本編號9187）版本。 [了解更多](../../rn/using/release--2020.md#release-20-2)
* Campaign 20.1.1（版本編號9122）至21.1.3（版本編號9124）版本。 [了解更多](../../rn/using/release--2020.md#release-20-1)
* Campaign 19.2.2（版本編號9080）至19.2.3（版本編號9081）版本。 [了解更多](../../rn/using/release--2019.md#release-19-2)
* Campaign 19.1.5（版本編號9033）至19.1.7（版本編號9036）版本。 [了解更多](../../rn/using/release--2019.md#release-19-1)


了解如何檢查您的版本 [在本節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**如何更新？**

As a **托管客戶**,Adobe會與您合作，立即更新您的設定。

作為 **內部部署/混合客戶**，您需要更新您的設定。

請依照下列步驟操作：

1. 在 [伺服器配置檔案](../../installation/using/the-server-configuration-file.md) (serverConf.xml)，變更 **signEmailLinks** to **false**.
1. 重新啟動 **nlserver** 服務。
1. 在追蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>此 **config-`<instance>`.xml** 檔案會覆寫 **serverConf.xml** 設定。 若 **signEmailLinks** 存在於  **config-`<instance>`.xml** (其中 **執行個體** 為執行個體的名稱)，也必須轉換為 **false**.

**會有什麼影響？**

維護作業最長需要 25 分鐘的停機時間，在此期間，所有傳送、追蹤連結和 API 呼叫都無法運作。

更新完成後，所有連結都會如預期恢復運作。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
