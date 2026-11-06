---
keywords: Campaign Classic;home;popular topics
product: campaign
title: Adobe Campaign Classic v7 產品文件
exl-id: 6b3f1689-80de-49fd-b7ee-7a2a1931d157
TQID: 'https://experienceleague.adobe.com/Q6Oc24mo-1qDAxCWu2lGT4UvRLXB78Tr5X4sb2kHFw8'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
  - id: b12f6872-9271-4369-85e5-86969a0b99a2
    internal-label: APIs
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
    internal-label: Reporting
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
  - id: f4e6943a-c91a-4134-a2c7-f4f20cfff2f0
    internal-label: Privacy
source-git-commit: fbeb3bb6f89cd0b03d1fb4551496f96eda0cbf10
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 40%
---
# Campaign Classic v7 文件 {#campaign-classic-documentation}

本檔案說明適用於&#x200B;**內部部署和混合**&#x200B;部署的Campaign Classic v7：安裝、設定、升級、作業以及v7特有的功能。 如果您的執行個體是由Adobe (Managed Cloud Services)託管，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/campaign-home){target="_blank"}。 Campaign v8檔案相同內容的重複專案不再於此處：請參閱[從v7到v8](#from-v7-to-v8)。

<!--![](platform/using/assets/do-not-localize/banner_acc_doc.jpg) -->

## 有哪些新功能

快速一覽 Adobe Campaign Classic v7 產品和文件的最新增強功能！ 如需功能、改進項目與修正的完整清單，請參閱詳細的[發行說明](rn/using/latest-release.md)。

>[!BEGINTABS]


>[!TAB 2026年10月版本已上線！]

Campaign Classic v7.4.5 - 2026年10月建置版本（建置版本9420）針對Analytics外部帳戶、卡在個人化擱置狀態的傳送、伺服器CPU使用情況、間歇性資料模型更新失敗、傳送建立中的垃圾郵件檢查錯誤，以及週期性軟退信的隔離提供修正。

[![影像](assets/do-not-localize/learn-more-button.svg)](rn/using/latest-release.md)

>[!TAB 移至 Adobe IMS]

為了強化安全性和驗證流程，Adobe Campaign 強烈建議將一般使用者驗證模式從登入/密碼原生驗證移轉至 Adobe Identity Management System (IMS)。

[![影像](assets/do-not-localize/learn-more-button.svg)](technotes/using/ac-ims.md)


>[!ENDTABS]

## 從基礎知識開始

<table style="table-layout:fixed">
  <tr style="border: 0;">
    <td>
    <a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/start-launch.png"></a></a>
    <div><strong>啟動 Adobe Campaign</strong><br/>了解如何啟動 Campaign 用戶端主控台，然後連接至 Campaign 應用程式伺服器。</div>
    </td>
    <td>
    <a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/start-profiles.png"></a>
    <div><strong>新增和管理輪廓</strong><br/>輕鬆探索 Adobe Campaign v7 資料庫中的輪廓管理。 手動或透過匯入新增輪廓，輕鬆精簡客戶資料和自訂行銷活動。</div>
    </td>
    <td>
    <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/start-workflows.jpeg"></a>
    <div><strong>使用工作流程自動化</strong><br/>了解如何利用工作流程來設計流程，包括細分、行銷活動執行、檔案處理、人員參與等。
    </div></td>
    <td>
    <a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/start-deliveries.jpeg"></a>
    <div><strong>建立傳遞</strong><br/>了解如何跨各種管道傳送訊息，例如電子郵件、簡訊、推播通知等。</div>
    </td>
  </tr>
  <tr style="border: 0;">
    <td align="center"><a href="platform/using/launching-adobe-campaign.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="platform/using/about-profiles.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    <td align="center"><a href="delivery/using/communication-channels.md"><img src="assets/do-not-localize/learn-more-button.svg"></a></td>
    </tr>
</table>

## 探索文件

<table style="table-layout:auto">
  <tr style="border: 0;">
    <td>
      <img src="assets/do-not-localize/icon-configure.svg" width="35px">
      <br/>
      <strong>管理員</strong><br/><a href="production/using/architecture-and-open-ports.md">架構原則</a> - <a href="production/using/syslogd-port-and-security-zones.md">設定Campaign</a> - <a href="platform/using/launching-adobe-campaign.md">連線至Campaign</a> - <a href="installation/using/external-accounts.md">連線至外部系統</a> - <a href="platform/using/access-management.md">許可權</a> - <a href="platform/using/privacy-management.md">隱私權和同意</a> - <a href="production/using/build-upgrade.md">執行組建升級</a> - <a href="delivery/using/about-deliverability.md">傳遞能力</a>
    </td>
    <td>
      <img src="assets/do-not-localize/icon-send.svg" width="35px">
      <br/>
      <strong>行銷人員</strong><br/><a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/new/campaign-ui" target="_blank">使用者介面</a> （Campaign v8檔案） - <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/data/import" target="_blank">匯入和匯出資料</a> （Campaign v8檔案） - <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/audience/create-audiences/create-audiences" target="_blank">建立清單</a> （Campaign v8檔案） - <a href="delivery/using/about-services-and-subscriptions.md">服務與訂閱</a> - <a href="delivery/using/communication-channels.md">通訊頻道</a> - <a href="delivery/using/about-personalization.md">Personalization</a> - <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/create-message" target="_blank">傳送校樣</a> （Campaign v8檔案） - <a href="delivery/using/get-started-a-b-testing.md">A/B測試</a> - <a href="message-center/using/about-transactional-messaging.md">異動訊息</a> - <a href="interaction/using/interaction-and-offer-management.md">互動和優惠管理</a> - <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/automation/workflows/introduction/about-workflows" target="_blank">使用工作流實現自動化</a>（Campaign v8文檔） - <a href="https://experienceleague.adobe.com/docs/campaign/automation/campaign-orchestration/set-up-campaigns.html?lang=zh-Hant" target="_blank">行銷活動</a> - <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/tracking/tracking" target="_blank">消息跟蹤</a>（Campaign v8文檔） - <a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/reports/gs-reporting" target="_blank">報表</a>（Campaign v8文檔）
    </td>
    <td>
      <img src="assets/do-not-localize/icon-dev.svg" width="35px">
      <br/>
      <strong>開發人員</strong><br/><a href="https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/datamodel" target="_blank">資料模型說明</a> （Campaign v8檔案） - <a href="configuration/using/about-schema-reference.md">結構描述結構</a> - <a href="configuration/using/editing-forms.md">輸入表單</a> - <a href="configuration/using/about-web-services.md">API</a> - <a href="https://experienceleague.adobe.com/zh-hant/tools/campaign-api" target="_blank">JSAPI參考檔案</a> - <a href="configuration/using/about-custom-recipient-table.md">自訂收件者表格</a>
    </td>
  </tr>
</table>

## 從v7到v8 {#from-v7-to-v8}

Campaign v8檔案中記錄的內容已從v7檔案中移除。 使用此表格來尋找它。

| 如果您正在尋找…… | 前往Campaign v8檔案 |
| --- | --- |
| 使用者介面 | [探索使用者介面](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/new/campaign-ui){target="_blank"} |
| 設定檔、清單、匯入和匯出 | [匯入設定檔和資料](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/data/import){target="_blank"} |
| 工作流程 | [關於工作流程](https://experienceleague.adobe.com/zh-hant/docs/campaign/automation/workflows/introduction/about-workflows){target="_blank"} |
| 行銷活動 | [開始使用行銷活動](https://experienceleague.adobe.com/zh-hant/docs/campaign/automation/campaign-orchestration/set-up-campaigns){target="_blank"} |
| 建立和傳送傳遞 | [建立訊息](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/send/create-message){target="_blank"} |
| 內建報告 | [開始使用報告](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/analytics/reports/gs-reporting){target="_blank"} |
| 權限 | [開始使用許可權](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/permissions/gs-permissions){target="_blank"} |
| 輸入表單 | [開始使用輸入表單](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/developer/schemas-forms/forms){target="_blank"} |

## 其他資源

[Adobe Campaign 產品說明](https://helpx.adobe.com/tw/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} - [相容性矩陣](rn/using/compatibility-matrix.md) - [教學課程](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant){target="_blank"} - [Campaign 控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant){target="_blank"} - [電子郵件追蹤像素與 CNIL 指南](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/new/cnil-pixel-tracking){target="_blank"}
