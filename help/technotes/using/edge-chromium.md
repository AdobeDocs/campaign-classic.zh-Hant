---
product: campaign
title: 技術檔案 — 在您的Campaign環境中啟用Microsoft Edge Chromium
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
description: Campaign - Edge Chromium
exl-id: 22f4cbaf-ca37-47b9-b7dd-1ee73d5b348d
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '246'
ht-degree: 13%

---

# 如何在您的環境中啟用Microsoft Edge Chromium {#edge-conf}




## 哪些部分有所變更？

Microsoft Internet Explorer 11生命週期結束後，使用者端主控台中控制面板的HTML轉譯引擎使用Edge Chromium，從Campaign Classicv7.3開始。

除了安裝Microsoft Edge Webview 2執行階段，現在是 [任何使用者端主控台安裝均需要](../../installation/using/installing-the-client-console.md#webview)，您必須在執行個體上啟用Microsoft Edge Chromium。

## 您有受到影響嗎？

如果您的環境已升級至Campaign Classicv7.3 （或更新版本），則會受到影響。

## 如何更新？

* As a **託管** 客戶，Adobe已在您的執行個體上啟用Microsoft Edge Chromium。 不需要其他動作。

* 作為 **內部部署/混合** 客戶，您必須在執行個體上啟用Microsoft Edge Chromium。

   升級至Campaign Classic v7.3 （及更新版本）時，新增 `webView2Mode` 屬性可在Campaign伺服器設定檔案中使用 `serverConf.xml`. 必須啟用此屬性。

   若要執行此動作，請在您的所有環境(MKT、MID、RT)上套用下列步驟：

   1. 編輯Campaign伺服器設定檔(`serverConf.xml`)
   1. 在 `<web>` 模組，設定 `webView2Mode = "1"`
   1. 執行以下命令以重新載入伺服器組態：

      ```
      nlserver config -reload
      ```

   1. 執行以下命令以重新啟動網頁伺服器：

      ```
      nlserver restart web
      ```

   1. 如果您的環境使用Apache做為Web伺服器，請執行以下命令以重新啟動Apache：

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
