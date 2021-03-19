---
solution: Campaign Classic
product: campaign
title: Gold Standard發行說明
description: Campaign Classic金標發行說明
feature: 概觀
role: 業務從業人員
level: 初學者
translation-type: tm+mt
source-git-commit: 1f718e26aeaa5ed5a58dfd0e3bc29d2dd9e995ee
workflow-type: tm+mt
source-wordcount: '1055'
ht-degree: 85%

---


# Gold Standard 版本{#gold-standard}

本頁面列出的 Gold Standard 發行版本。在本頁](gs-overview.md)中進一步瞭解促銷活動金級標準[。

## ![](assets/do-not-localize/green_2.png)Gold Standard 第 11 發行版本{#gs-11}

_2021年3月2日_

建置 9032@10c2709 包含以下修正：

* 修正回歸，防止在傳送中使用主控台的某些元件，例如日期選擇器和影像管理。 (NEO-31453、NEO-31454)

**僅控制台升級是強制性的。不需要伺服器升級。**

>[!NOTE]
>
> 連線至[Adobe軟體分發](https://experience.adobe.com/#/downloads/content/software-distribution/en/campaign.html)以下載新版本。 瞭解如何在本頁](../../installation/using/client-console-availability-for-windows.md)中向所有最終用戶[建議控制台更新。


_2020年12月22日_

>[!CAUTION]
>
> * 此版本隨附新的連線通訊協定：如果您透過Adobe身分服務(IMS)連線至促銷活動，則促銷活動伺服器和用戶端主控台都必須進行升級，才能在2021年6月30日&#x200B;**之後連線至促銷活動。**
> * 此版本隨附於[安全性修正](https://helpx.adobe.com/security/products/campaign/apsb21-04.html)：升級是強化環境安全的必備條件。
> * 如果您正透過驗證使用Experience Cloud觸發器整合，則需依照本頁[所述移至Adobe I/O。 ](../../integrations/using/configuring-adobe-io.md)具有促銷活動的舊式驗證模式將於2021年11月30日&#x200B;****&#x200B;淘汰。

>
>
進一步瞭解 [Gold Standard 11 升級常見問答集](https://helpx.adobe.com/tw/campaign/kb/gold-standard-upgrade.html)。

版本編號 9032@d3b452f 包含下列增強功能及修正檔：

* 已更新連線通訊協定，以遵循新的 IMS 驗證機制。

* 已變更原本以 oAUTH 驗證設定為基礎而用於存取管道的觸發器整合驗證，並將其移動至 Adobe I/O。[瞭解更多](../../integrations/using/configuring-adobe-io.md)

* [在 iOS APN 舊版二進位通訊協定支援結束之後，在升級後期間，](https://developer.apple.com/news/?id=c88acm2b)使用此通訊協定的所有執行個體都會更新為 HTTP/2 通訊協定。

* 修正了安全性問題，以針對伺服器端請求偽造 (SSRF) 問題而加強保護。(NEO-27777)

* 修正執行&#x200B;**擴充**&#x200B;活動時，工作流程可能失敗的問題。(NEO-17338)

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 10 發行版本{#gs-10}

_2020 年 7 月 7 日_

建置 9032@efd8a94 包含以下修正：

修正了在停用簽名功能時，無法進行追蹤的問題。(NEO-26411)

>[!CAUTION]
>
>我們建議您使用此版本中可用的用戶端控制台進行升級。請參見[此頁面](../../installation/using/installing-the-client-console.md)。

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 9 發行版本{#gs-9}

_2020 年 6 月 22 日_

建置 9032@800be2e 包含以下修正：

* 改善了 iOS HTTP2 連接器（協力廠商更新和錯誤管理）。(NEO-25904、NEO-25903、NEO-25799)

以下為與追蹤連結安全性機制相關之修正（參閱[「安全性與隱私權檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html#signature-mechanism)」以瞭解更多）：

* 修正了「通知單擊」無法進行追蹤的問題（iOS 和 Android 推播通知）。(NEO-25965)
* 修正了在使用某些特定 Outlook 舊版本時，無法開啟/按一下追蹤 URL 的問題。(NEO-25688)
* 修正了在個人化參數（井字鍵符號的錨點標記）中無法使用片段追蹤 URL 的問題。(NEO-25774)
* 修正了反網路釣魚服務的問題。(NEO-25283)
* 修正了在使用特定自訂追蹤公式時的追蹤問題。(NEO-25277)

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 8 發行版本{#gs-8}

_2020年4月29日_

建置 9032@3a9dc9c 包含以下修正：

* 改善了電子郵件中追蹤連結的安全性。依預設為所有客戶啟用此功能。另外還提供增強的安全性功能，您可以透過連絡客戶服務來啟用此功能。有關非托管客戶啟用此功能的詳細資訊和步驟，請參閱 [「安全性與隱私權」檢查清單](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)。

>[!CAUTION]
>
>如果您在使用追蹤連結或使用錨點標籤時，遇到推播通知的問題，我們建議您停用追蹤連結的新簽名機制。[本頁面](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)詳細介紹此程序

* 修正了無法在 Line 傳遞顯示影像的問題。(NEO-23207)
* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)
* 修正了在高頻率傳送時，可能影響推播通知的問題。(NEO-20516)
* 修正了在優惠方案回應管理中，可能導致 Web 伺服器當機的問題。(NEO-19482)
* 修正了在 LibreOffice 管理中，無法匯出報告的錯誤。(NEO-20982)
* 修正了使用意見調查活動升級許多工作流程時，而導致錯誤的問題。
* 改善了 LibreOffice 管理，以防止在電子郵件預覽時，無法預覽 .odt 檔案。
* 改善了 Apache 連線管理，以防止網站服務的延遲。
* 改善了在&#x200B;**「關於」**&#x200B;功能表中的版本標籤顯示（7 位數）。
* 修正了清單管理中，造成無法發佈優惠方案的迴歸。
* 修正了造成清理工作流程當機的迴歸。
* 修正了清理工作流程記錄檔的次要迴歸。

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 6 發行版本{#gs-6}

_2020年3月9日_

建置 9032@19f73c5 包含以下修正：

* 修正了使用 FTP over SSL 的外部帳戶的問題。(NEO-20498)

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 5 發行版本{#gs-5}

_2019年12月17日_

建置 9032@d6b8062 包含以下修正：

* 修正以下通訊頻道的追蹤問題：行動（SMS、MMS）、推播（iOS、Android）和社交網路（Facebook、Twitter）。(NEO-19595)

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 4 發行版本{#gs-4}

_2019年12月11日_

建置 9032@bc4a935 包含以下修正：

* 修正了在使用 MSSQL 資料庫傳送訊息時，所導致的效能問題。(NEO-17558)

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 3 發行版本{#gs-3}

_2019年11月20日_

建置 9032@3468c7b 包含以下修正：

* 修正了透過 IMS 驗證的登入問題。(NEO-17312)
* 修正了在多個傳遞顯示累積報告時所產生的問題。(NEO-18165)
* 修正了可能封鎖或造成 Web 伺服器當機的問題。

## ![](assets/do-not-localize/red_2.png)Gold Standard 第 2 發行版本{#gs-2}

_2019 年 9 月 19 日_

建置 9032@cee805c 包含以下修正：

* 修正了為 Salesforce 而使用 CRM 連接器所產生的問題。(NEO-17712)
* 修正了正在傳送異動訊息時，可能導致效能問題的索引問題。

## ![](assets/do-not-localize/red_2.png) 版本 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_2019年8月13日_

初始 19.1.4 版本編號包含以下修正：

* 修正了在配置精靈時，排程器活動產生無用錯誤訊息的問題。正在還原 NEO-11662 更新。(NEO-17097)
* 修正了 NEO-12727 所導致的迴歸，其在執行兩次測試活動時，可能會導致工作流程停止運行。(NEO-16835)
* 修正了在 API 調用中使用無效或過期的續存期間權杖時，導致回傳錯誤 HTTP 代碼的問題（為 HTTP 200 OK，而非 HTTP 403 Forbidden）。(NEO-16826)
* 修正了 DKIM 金鑰不再內嵌在電子郵件中的問題，其導致的傳遞問題。(NEO-16804)
* 修正了各種工作流程排程的問題。排程工作流程以進行每天一次的運行，無需考慮排程器配置。(NEO-16619、NEO-16426)
