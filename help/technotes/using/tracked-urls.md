---
product: campaign
title: 追蹤的 URL 簽名問題
description: 追蹤的 URL 簽名問題
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 403d0b7df74b2c958bea9a2d718a15f597ca0d9c
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 35%

---

# 追蹤的 URL 簽名問題 {#tracked-urls}



在最近變更後，當URL簽名在Campaign中生效時，追蹤的URL可能會失敗。 有些信件匣受到的影響比其他信件匣大，因為有些公司有特定的安全工具，這些工具可能會影響連結並替代 URL 簽名機制。

因此，Adobe建議您停用追蹤連結的簽名機制。 此程式會修正舊的追蹤連結，但透過雙重逸出接收的追蹤連結除外。

請注意，取消訂閱的連結可能會像其他連結一樣失效，頻率根據每台主機而定，但機率小於 1%。

**您有受到影響嗎？**

為了提高安全性，在中引進了追蹤電子郵件中連結的簽名機制 [Campaign Gold Standard 8](../../rn/using/gold-standard.md#gs8) - 2020年4月 — 預設為從Build 19.1.4 (9032@3a9dc9c)和Campaign 20.2開始的所有客戶啟用和。

如果您的環境在下列其中一個版本上執行，則可能會受到影響：

* Gold Standard 8至11。 [了解更多](../../rn/using/gold-standard.md#gs-8)
* Campaign 21.1.1 (build 9277)至21.1.2 (build 9282)版本。 [了解更多](../../rn/using/latest-release.md)
* Campaign 20.3.1 (build 9228)至20.3.3 (build 9234)版本。
* Campaign 20.2.1 (build 9178)至20.2.4 (build 9187)版本。
* Campaign 20.1.1 (build 9122)至21.1.3 (build 9124)版本。
* Campaign 19.2.2 (build 9080)至19.2.3 (build 9081)版本。
* Campaign 19.1.5 (build 9033)至19.1.7 (build 9036)版本。


瞭解如何檢查您的版本 [在本節中](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version).

**如何更新？**

As a **託管客戶**，Adobe將會很快協助您更新設定。

作為 **內部部署/混合客戶**，您需要更新設定。

請遵循下列步驟：

1. 在 [伺服器設定檔](../../installation/using/the-server-configuration-file.md) (serverConf.xml)，變更 **signEmailLinks** 至 **false**.
1. 重新啟動 **nlserver** 服務。
1. 在追蹤伺服器上，重新啟動網頁伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>此 **config-`<instance>`.xml** 檔案會覆寫 **serverConf.xml** 設定。 如果 **signEmailLinks** 中存在於  **config-`<instance>`.xml** (其中 **例項** 是執行個體的名稱)，也必須切換為 **false**.
>

**會有什麼影響？**

維護作業最長需要 25 分鐘的停機時間，在此期間，所有傳送、追蹤連結和 API 呼叫都無法運作。

更新完成後，所有連結都會如預期恢復運作。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
>
