---
product: campaign
title: '追蹤的 URL 簽名問題 '
description: '追蹤的 URL 簽名問題 '
hide: true
hidefromtoc: true
exl-id: e7d4331b-7149-4768-8e46-2e2911319074
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 36%

---

# 追蹤的 URL 簽名問題 {#tracked-urls}

![](../../assets/v7-only.svg)

在最近的更改後，當市場活動中URL簽名處於活動狀態時，跟蹤的URL可能會失敗。 有些信件匣受到的影響比其他信件匣大，因為有些公司有特定的安全工具，這些工具可能會影響連結並替代 URL 簽名機制。

因此，Adobe建議禁用跟蹤連結的簽名機制。 此過程修復舊的跟蹤連結，但接收到的雙重轉義連結除外。

請注意，取消訂閱的連結可能會像其他連結一樣失效，頻率根據每台主機而定，但機率小於 1%。

**您有受到影響嗎？**

為了提高安全性，本文引入了電子郵件連結的簽名機制 [市場活動金本位8](../../rn/using/gold-standard.md#gs8) - 2020年4月 — 預設啟用，並且啟動版本19.1.4(9032@3a9dc9c)和市場活動20.2的所有客戶。

如果您的環境運行在下面列出的版本之一上，則可能會影響您：

* 金本位8至11 [了解更多](../../rn/using/gold-standard.md#gs-8)
* 市場活21.1.1(build 9277)到21.1.2(build 9282)版本。 [了解更多](../../rn/using/latest-release.md)
* 市場活20.3.1(build 9228)到20.3.3(build 9234)版本。 [了解更多](../../rn/using/release--2020.md#release-20-3)
* 市場活20.2.1(build 9178)到20.2.4(build 9187)版本。 [了解更多](../../rn/using/release--2020.md#release-20-2)
* 市場活20.1.1(build 9122)到21.1.3(build 9124)版本。 [了解更多](../../rn/using/release--2020.md#release-20-1)
* 市場活19.2.2(build 9080)到19.2.3(build 9081)版本。 [了解更多](../../rn/using/release--2019.md#release-19-2)
* 市場活19.1.5(build 9033)到19.1.7(build 9036)版本。 [了解更多](../../rn/using/release--2019.md#release-19-1)


瞭解如何檢查您的版本 [此部分](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

**如何更新？**

作為 **托管客戶**,Adobe將與您合作，不久將更新您的配置。

作為 **本地/混合客戶**，您需要更新配置。

執行以下步驟：

1. 在 [伺服器配置檔案](../../installation/using/the-server-configuration-file.md) (serverConf.xml)，更改 **簽名電子郵件連結** 至 **假**。
1. 重新啟動 **nlserver** 服務。
1. 在跟蹤伺服器上，重新啟動Web伺服器（Debian上的apache2、CentOS/RedHat上的httpd、Windows上的IIS）。

   ```
   nlserver restart web
   ```

>[!NOTE]
>
>的 **配置`<instance>`.xml** 檔案覆蓋 **serverConf.xml** 的子菜單。 如果 **簽名電子郵件連結** 在  **配置`<instance>`.xml** ( **實例** 是實例的名稱)，還必須將其轉換為 **假**。

**會有什麼影響？**

維護作業最長需要 25 分鐘的停機時間，在此期間，所有傳送、追蹤連結和 API 呼叫都無法運作。

更新完成後，所有連結都會如預期恢復運作。

>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。
