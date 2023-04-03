---
product: campaign
title: 技術 — 在您的Campaign環境中啟用Microsoft Edge Chromium
description: Campaign - Edge Chromium
hide: true
hidefromtoc: true
source-git-commit: 17ef8f92ab5dbecadf20140c3faff735d92c8223
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---


# 如何在您的環境中啟用Microsoft Edge Chromium {#edge-conf}

![](../../assets/v7-only.svg)


## 有什麼改變？

Microsoft Internet Explorer 11生命週期結束後，用戶端主控台中控制面板的HTML轉譯引擎即使用Edge Chromium，開始使用Campaign Classicv7.3。

除了安裝Microsoft Edge Webview 2執行階段外，現在也是 [任何客戶端控制台安裝都需要](../../installation/using/installing-the-client-console.md#webview)，您必須在執行個體上啟用Microsoft Edge Chromium 。

## 您有受到影響嗎？

如果您的環境已升級至Campaign Classicv7.3（或更新版本），您會受到影響。

## 如何更新？

* As a **托管** 客戶，Adobe已在您的執行個體上啟用Microsoft Edge Chromium。 不需要執行其他動作。

* 作為 **內部部署/混合** 客戶，您必須在執行個體上啟用Microsoft Edge Chromium。

   升級至Campaign Classicv7.3（和更新版本）時，新 `webView2Mode` 屬性可在Campaign伺服器設定檔中使用 `serverConf.xml`. 必須啟用此屬性。

   若要執行此動作，請在所有環境(MKT、MID、RT)上套用下列步驟：

   1. 編輯Campaign伺服器設定檔案(`serverConf.xml`)
   1. 在 `<web>` 模組，設定 `webView2Mode = "1"`
   1. 運行以下命令以重新載入伺服器配置：

      ```
      nlserver config -reload
      ```

   1. 運行以下命令以重新啟動Web伺服器：

      ```
      nlserver restart web
      ```

   1. 如果您的環境使用Apache作為Web伺服器，請運行以下命令以重新啟動Apache:

      ```
      /etc/init.d/apache2 restart
      ```


>[!NOTE]
>
>如對這些變更有任何疑問，請聯絡 [Adobe 客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)。

## 相關主題

* [升級您的環境](../../production/using/build-upgrade.md)
* [版本編號升級常見問答集](../../platform/using/faq-build-upgrade.md)
* [安裝 Campaign 用戶端控制台](../../installation/using/installing-the-client-console.md)

