---
title: Gold Standard版本
seo-title: Gold Standard版本
description: Gold Standard版本
seo-description: null
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-release-notes
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 7f7b53f0a7ec0f50bf3a99314606272b8ebdc8d7
workflow-type: tm+mt
source-wordcount: '815'
ht-degree: 14%

---


# Gold Standard版本{#gold-standard}

身為Gold Standard使用者，您可以透過最新穩定版本自動受益於Gold Standard升級，而不需採取任何動作。

內部部署和Hybrid客戶也可從Gold Standard版本中獲益。

這是我們的長期支援版本。 如果您從舊版本移轉，建議您先升級至此版本。

本頁列出Gold Standard版本。

有關Gold Standard升級的詳細資訊，請參閱本 [文](https://helpx.adobe.com/tw/campaign/kb/gold-standard.html)。

## ![](assets/do-not-localize/green_2.png) Gold Standard 10版{#gs-10}

_2020年7月7日_

建置9032@efd8a94包含下列修正：

修正在停用簽名功能時無法運作追蹤的問題。 (NEO-26411)

>[!CAUTION]
>
>我們建議您使用此版本中提供的客戶端控制台升級。 Refer to this [page](../../installation/using/installing-the-client-console.md)

## ![](assets/do-not-localize/red_2.png) Gold Standard 9版{#gs-9}

_2020年6月22日_

建置9032@800be2e包含下列修正：

* iOS HTTP2連接器已改善（協力廠商更新和錯誤管理）。 (NEO-25904、NEO-25903、NEO-25799)

下列修正與追蹤連結安全性機制相關(請參閱「安全性與隱 [私權」檢查清單](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)):

* 修正追蹤「通知點按」無法運作的問題（iOS和Android推播通知）。 (NEO-25965)
* 修正使用某些舊版Outlook時，無法開啟／按一下追蹤URL的問題。  (NEO-25688)
* 修正在個人化參數（具有井字型大小的錨記）中使用片段追蹤URL無法運作的問題。 (NEO-25774)
* 已修正反網路釣魚服務的問題。 (NEO-25283)
* 修正使用特定自訂追蹤公式時的追蹤問題。 (NEO-25277)

## ![](assets/do-not-localize/red_2.png) Gold Standard 8版{#gs-8}

_2020年4月29日_

建置9032@3a9dc9c包含下列修正：

* 已改善電子郵件中追蹤連結的安全性。 預設會為所有客戶啟用此功能。 另外還提供增強的安全性功能，您可以透過連絡客戶服務來啟用此功能。有關非托管客戶啟用此功能的詳細資訊和步驟，請參閱 [「安全性與隱私權」檢查清單](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)。

>[!CAUTION]
>
>如果您在使用追蹤連結的推播通知或使用錨點標籤的傳送時遇到問題，建議您停用追蹤連結的新簽名機制。 本頁詳細介紹了該過 [程](https://helpx.adobe.com/campaign/kb/acc-security.html#signature-mechanism)

* 修正影像無法顯示在「行」傳送上的問題。 (NEO-23207)
* 修正&#x200B;**檔案傳輸**&#x200B;活動使 SFTP 金鑰驗證無法在 Debian 9 運作的問題。(NEO-23183)
* 已修正在高頻率傳送時，可能會影響推播通知的問題。 (NEO-20516)
* 修正選件回應管理中可能導致Web伺服器當機的問題。 (NEO-19482)
* 修正LibreOffice管理中無法匯出報表的錯誤。 (NEO-20982)
* 修正使用調查活動升級許多工作流程時發生錯誤的問題。
* 已改善LibreOffice管理，以避免使用。odt檔案進行電子郵件預覽時發生失敗。
* 已改善Apache連線的管理，以避免Web服務上的延遲。
* 已改善版本標籤（7位數）在「關於」功能表 **中的顯** 示。
* 修正清單管理中的回歸，使選件無法發佈。
* 修正了造成清理工作流程當機的迴歸。
* 修正了清理工作流程記錄檔的次要迴歸。

## ![](assets/do-not-localize/orange_2.png) Gold Standard 6版本{#gs-6}

_2020年3月9日_

建置9032@19f73c5包含下列修正：

* 修正使用 FTP over SSL 的外部帳戶的問題。(NEO-20498)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 5版本{#gs-5}

_2019年12月17日_

建置9032@d6b8062包含下列修正：

* 修正下列通訊管道的追蹤問題：行動(SMS、MMS)、推播(iOS、Android)和社交網路(Facebook、Twitter)。 (NEO-19595)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 4版本{#gs-4}

_2019年12月11日_

建置9032@bc4a935包含下列修正：

* 修正了使用MSSQL資料庫發送消息時的效能問題。 (NEO-17558)

## ![](assets/do-not-localize/orange_2.png) Gold Standard 3版{#gs-3}

_2019年11月20日_

建置9032@3468c7b包含下列修正：

* 已修正透過IMS驗證的登入問題。 (NEO-17312)
* 修正在多個傳送上顯示累積報表的問題。 (NEO-18165)
* 已修正可能會封鎖或造成Web伺服器當機的問題。

## ![](assets/do-not-localize/red_2.png) Gold Standard 2版{#gs-2}

_2019年9月19日_

建置9032@cee805c包含下列修正：

* 修正使用Salesforce的CRM連接器時的問題。 (NEO-17712)
* 修正在傳送事務性訊息時，可能導致效能問題的索引問題。

## ![](assets/do-not-localize/red_2.png) 版本 19.1.4 - Build 9032{#release-19-1-4-build-9032}

_2019年8月13日_

初始19.1.4版本包含下列修正：

* 修正在精靈設定期間，排程器活動產生不想要的錯誤訊息的問題。 回復NEO-11662的更新。 (NEO-17097)
* 修正NEO-12727造成的回歸，當執行兩次測試活動時，此回歸可能導致工作流程停止。 (NEO-16835)
* 修正當API呼叫中使用無效或過期的作業Token時，會傳回錯誤的HTTP程式碼（HTTP 200 OK，而非HTTP 403 Forbidden）的問題。 (NEO-16826)
* 已修正DKIM金鑰不再內嵌在電子郵件中的問題，因此造成傳遞能力問題。 (NEO-16804)
* 已修正工作流程排程的各種問題。 排程的工作流程會排程為每天執行一次，而不會考慮排程器設定。 (NEO-16619、NEO-16426)
