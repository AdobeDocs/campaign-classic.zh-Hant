---
product: campaign
title: 重要概念
description: Campaign Classic 常見問題集
feature: Troubleshooting
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f0d884ae-0789-4ad9-a8fa-adeffbb560ea
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 96%

---

# 重要概念 {#key-concepts}



瞭解開始使用 Adobe Campaign 的關鍵步驟。

## 我可以使用 Adobe ID 連接至 Campaign Classic 嗎？ {#can-i-connect-to-campaign-classic-with-an-adobe-id-}

與 IMS（Adobe 身份管理系統）整合之後，使用者可以使用 Adobe ID 連線到 Adobe Campaign 主控台。此整合具備以下優勢︰

* 所有 Experience Cloud 解決方案都可以使用相同的 ID。
* 使用不同整合中的 Adobe Campaign 時，可以記憶連線。
* 更安全的密碼管理原則。
* 使用 Federated ID 帳戶（外部 ID 提供者）。

[按一下這裡以瞭解更多](../../integrations/using/about-adobe-id.md)如何使用 Adobe ID 存取 Campaign Classic。

## 我的 Campaign 版本是什麼？ {#what-is-my-version-of-campaign-}

從 Campaign 用戶端主控台的 **Help > About...** 功能表檢查您的[版本和建立編號](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)。

## 在內部部署環境與託管環境中運作有何不同？ {#what-are-the-differences-when-working-on-premise-vs--in-a-hosted-environment-}

Adobe Campaign Classic 隨附了一套模組和選項。這些模組及其配置是否可用將取決於安裝的[部署類型](../../installation/using/hosting-models.md)：託管（受管理的服務）還是內部部署。

[按一下這裡以瞭解更多](../../installation/using/capability-matrix.md)。

## 如何設定使用者權限? {#how-can-i-set-up-user-permissions-}

作為 Campaign 管理者，您可以為組織使用者設定權限。

有一套權限或限制可授權或拒絕執行以下操作：

* 存取特定功能，
* 存取特定資料，
* 建立、修改和/或刪除資料。

[按一下這裡以進瞭解更多](../../platform/using/access-management.md)使用者權限。

## Campaign如何確保遵循並符合隱私權規範？ {#how-to-be-gdpr-compliant-with-campaign-}

Adobe Campaign 提供一套工具，以協助您遵循隱私權法規（GDPR、CCPA 等）。

請參閱[本文件](privacy-and-recommendations.md)了解 Adobe Campaign 提供的工具、功能以及最佳實務，以協助您在使用我們的服務時能符合 GDPR 規定。[本文章](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)將說明 Campaign Classic 的實施步驟。

## 我應該了解哪些 Campaign 使用者介面概念? {#what-are-campaign-user-interface-concepts-i-should-know-}

請閱讀[本小節](../../platform/using/adobe-campaign-workspace.md)，瞭解更多 Adobe Campaign 工作區基本知識。

![](assets/do-not-localize/how-to-video.png) [在影片中探索行銷活動工作區](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/exploring-the-adobe-campaign-classic-user-interface.html)

## 如何選取訊息的對象？ {#how-can-i-select-the-target-population-of-my-messages-}

透過 Adobe Campaign，您可以使用不同策略來建立受眾，並選取收件者。

[按一下這裡以瞭解更多](../../delivery/using/steps-defining-the-target-population.md)。

## 什麼是工作流程？ {#what-is-a-workflow-}

Adobe Campaign 的工作流程包含跨應用程式伺服器的不同模組策劃所有流程和任務。使用這個全方位的圖像式環境，您可以設計各式流程，包含細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

例如，您可以使用工作流程從伺服器下載檔案、解壓縮，然後將其中的記錄匯入 Adobe Campaign 資料庫。

此外，工作流程也涉及到要進行通知的一或多個操作者，或者是可以選擇並核准流程的相關人員。如此一來就可以實行傳遞行動，將任務指派給一或多位操作者，指定目標且在傳遞前進行核准。

[按一下協瞭解更多](../../workflow/using/about-workflows.md)工作流程。您也可以閱讀[工作流程最佳實務](../../workflow/using/building-a-workflow.md)。

## 如何建立並傳送第一封電子郵件？ {#how-to-create-and-send-a-first-email-}

[按一下這裡以瞭解更多](../../delivery/using/about-email-channel.md)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此內容](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/getting-started/creating-a-campaign-and-an-email.html)

## 如何傳送 SMS 訊息？ {#how-to-send-sms-messages-}

在[本小節](../../delivery/using/sms-channel.md)瞭解如何配置您的平台以及傳送簡訊訊息。

## 如何傳送推播通知？ {#how-to-send-push-notifications-}

瞭解如何使用 Adobe Campaign 透過應用程式[將個人化推播通知傳送](../../delivery/using/create-notifications-ios.md)至 iOS 和 Android 裝置。

## 如何設計和分享線上意見調查？ {#how-to-design-and-share-an-online-survey-}

瞭解如何在 Campaign Classic 中[建立線上意見調查](../../surveys/using/getting-started-with-surveys.md)，以及設計及發佈意見調查的關鍵步驟。

## 如何建立登陸頁面？ {#how-to-create-landing-page-}

您可以使用 Adobe Campaign 數位內容編輯器來設計登陸頁面，定義與資料庫欄位的對應。

[按一下這裡以瞭解更多](../../web/using/creating-a-landing-page.md)。

## 如何追蹤傳送內容？ {#how-can-i-track-deliveries-}

在 Campaign Classic 中您可以透過專用的[傳遞報告](../../reporting/using/delivery-reports.md)追蹤並監視您的傳送內容。

前往[此頁面](https://helpx.adobe.com/tw/campaign/kb/acc-tracking.html)，瞭解更多 Campaign 的追蹤管理。

## 何為安全性最佳做法 (內部部署)？ {#what-are-security-best-practices--on-premise--}

閱讀[安全性配置檢查清單](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)，以探索有關安全性配置和強化內部部署的重點要素。

## 如何翻譯錯誤訊息？ {#how-to-translate-an-error-message-}

出現了以外文顯示的錯誤訊息？[本頁面](https://experienceleague.adobe.com/developer/campaign-errors/error_codes.html?lang=zh-Hant)列出所有錯誤訊息及其翻譯。

## 我可以在 Campaign 中製作網路表單和收集解答嗎？ {#can-i-create-a-webform-and-collect-answers-in-campaign-}

瞭解如何[建立網頁表單](../../web/using/about-web-forms.md)：設計、測試、發佈網頁表單並收集答案。

## 是否有舊功能和版本的清單？ {#is-there-a-list-of-deprecated-features-and-versions-}

Adobe 會持續評估產品功能，不斷使用更強大的版本進行替換，也可能決定重新推出部分組件，以滿足未來期望或外掛程式。由於 Campaign 與協力廠商工具合作，產品相容性將定期更新以僅實施所支援的版本。

[按一下這裡以瞭解更多](../../rn/using/deprecated-features.md)。

## 是否發行新的文件更新和說明材料？ {#are-there-new-documentation-updates-and-help-materials-released-}

在[本頁面中](https://experienceleague.adobe.com/docs/campaign-classic/using/documentation-updates.html)列出最新的 Campaign Classic 文件更新。

您也可以參照[本頁面中](https://helpx.adobe.com/tw/campaign/kb/article-list.html)列出之最新的技術附註。
