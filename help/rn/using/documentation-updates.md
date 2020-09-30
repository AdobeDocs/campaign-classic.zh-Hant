---
title: Adobe Campaign Classic 文件更新
description: 此頁面列出 Adobe Campaign Classic 各版本的所有新功能及文件更新。
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
source-git-commit: 6483c3e2e9fd3a2951b2bc8bf6d8a3350361e86f
workflow-type: tm+mt
source-wordcount: '3704'
ht-degree: 87%

---


# 文件更新{#documentation-updates}

此頁面按月及按各個 Campaign 版本列出所有新功能及文件更新。

您也可以參閱 [Adobe Campaign Classic 發行說明](../../rn/using/latest-release.md) ，以瞭解更多更新詳情。

## 2020 年 9 月{#september-2020}

已新增附註，以指定「作用中」描述檔計數僅適用於「行銷」例項。 [顯示全文](../../platform/using/about-profiles.md#active-profiles)

已新增關於架構版本的新範例，以將欄位連結至現有的參考表。 [顯示全文](../../configuration/using/examples-of-schemas-edition.md#uc-link)

已新增附註，說明如何在傳送中搭配種子地址使用其他資料。 [顯示全文](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## 2020 年 8 月{#aug-2020}

在專屬的章節中，瞭解與傳送設計及與Campaign一起傳送有關的最佳實務。 [顯示全文](../../delivery/using/delivery-best-practices.md)

「傳遞能力」最佳實務登陸頁面已改善，以方便存取子區段。 [顯示全文](../../delivery/using/deliverability-key-points.md)

現在，有關下列主題的教學影片已可供使用：

* [如何使用類型學規則和預先定義的篩選器來設定疲勞管理](../../campaign/using/about-campaign-typologies.md)

* [如何在促銷活動中建立電子郵件](../../campaign/using/marketing-campaign-deliveries.md)

* [如何建立包含條件式內容的多語言電子報](../../delivery/using/conditional-content.md)

* [如何設定和部署傳送範本](../../delivery/using/creating-a-delivery-template.md)

* [如何啟動和使用AMP處理電子郵件](../../delivery/using/defining-interactive-content.md)

* [使用動態內容區塊個人化電子郵件](../../delivery/using/personalization-blocks.md)

* [如何使用個人化欄位個人化電子郵件](../../delivery/using/personalization-fields.md)

* [如何管理電子郵件中的種子和校樣](../../delivery/using/steps-defining-the-target-population.md)

* [如何設定循環傳送](../../workflow/using/recurring-delivery.md)

* [如何設定連續傳送](../../workflow/using/continuous-delivery.md)

已新增資訊至連線至FTP伺服器後，當收到「無法解析主機名稱」錯誤時，要執行的檢查和動作。 [顯示全文](../../platform/using/sftp-server-usage.md)

工作流程使用案例清單中已參考了新 [的使用案例](../../workflow/using/about-workflow-use-cases.md):

* 自動化內容建立、編輯和發佈
* 在傳送傳送前設定收件者核准程式
* 呼叫查詢中的例項變數
* 對人口套用分割百分比

本 **[!UICONTROL AND-join]** 活動章節已豐富其使用資訊，以及使用變數的附註。 [顯示全文](../../workflow/using/and-join.md)

## 2020 年 7 月{#july-2020}

有關如何使用增量查詢自動更新清單的使用案例已添加到工作流使用案例中。 [顯示全文](../../workflow/using/about-workflow-use-cases.md)

「發 [行說明](../../rn/using/latest-release.md) 」已重新整理：已新 [增概述頁面](../../rn/using/latest-release.md) ，其中包含有關建置狀態、升級程式、建議和重要連結的資訊。 此外，還新增 [了Gold Standard版本專用頁](../../rn/using/gold-standard.md) ，並整合 [了Compatibility Matrix](../../rn/using/compatibility-matrix.md) 。

新增了與Campaign Classic監控相關的准則。 [顯示全文](../../production/using/monitoring-guidelines.md)

「隱私權與同意」一節已增強，提供更詳細的資訊和有用的連結。 [顯示全文](../../platform/using/privacy-and-recommendations.md)。

「促銷活動傳統型」中的「隱私權管理」頁面已更新，其中包含「規則」欄位的資訊，現在使用允許設定自動隱私權要求程式的API時，此欄位已可供使用。 [顯示全文](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

「隱私權管理概述」頁面已更新，加入泰國個人資料保護法(PDPA)和巴西Lei Geral de Proteção de Dados(LGPD)的相關資訊。 [顯示全文](https://helpx.adobe.com/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

已在子工作流程記錄檔和行為中新增資訊，以防發生錯誤。 [顯示全文](../../workflow/using/sub-workflow.md)

已在「活動」區段中新增最佳 **[!UICONTROL Scheduler]** 實務。 [詳細內容](../../workflow/using/scheduler.md)

## 2020 年 6月 {#june-2020}

更新「移除已隔離的位址」章節，內容包括釐清將位址自動從隔離清單移除的案例。[顯示全文](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

新增使用案例，以說明如何使用「控制面板」及「行銷活動工作流程」進行資料[加密](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt)與[解密](../../workflow/using/importing-data.md#use-case-gpg-decrypt)。

「Whitelist」和「blacklist」兩種字詞已從 Adobe Campaign 文件移除。產品 UI、選項名稱及內部代碼仍可能出現這兩種字詞，但未來版本的 Campaign 將以「blocklist」和「allowlist」取代。

The Experience Cloud Triggers and Adobe Campaign Classic integration page has been moved [here](../../integrations/using/about-triggers.md).

## july 2020 {#release-20-2}

**20.2版本中包含的新功能**

支援表情符號——[顯示全文](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA Connector——[顯示全文](../../platform/using/specific-configuration-database.md#configure-access-to-azure-synapse)

泰國及巴西隱私權法——[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**此版本隨附的其他文件更新**

[本章節](../../message-center/using/template-unpublication.md)將介紹啟用取消發佈交易式訊息範本的新選項。

新選項可以讓您傳送包含從個人化 URL 下載的影像及附件的電子郵件時，設定限制；此新選項已新增至 Campaign Classic 選項清單。[顯示全文](../../installation/using/configuring-campaign-options.md#delivery)

[本章節](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)將介紹新的&#x200B;**「在資料庫準備傳遞組件**」選項。

釐清並更新「驗證傳遞」章節。[顯示全文](../../delivery/using/steps-validating-the-delivery.md)

[「伺服器設定檔」](../../installation/using/the-server-configuration-file.md)章節新增與新的追蹤連結簽章機制相關的參數。

更新相容性矩陣。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

更新「清理工作流程」章節。[進一步瞭解](../../production/using/database-cleanup-workflow.md)

Campaign 網路端點已移至此[章節](../../installation/using/campaign-network-endpoints.md)。

「Spam Assassin 安裝」章節更新了新的安裝檔案名稱。[進一步瞭解](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

更新有關複製環境的章節。[進一步瞭解](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## 2020 年 5 月 {#may-2020}

移動並改善「監控傳遞能力」章節。[顯示全文](../../delivery/using/monitoring-deliverability.md)

移動並改善「傳遞能力疑難排解」章節。[顯示全文](../../delivery/using/deliverability-faq.md)

加強「啟動新平台時的傳遞能力指南」章節。[顯示全文](../../delivery/using/starting-new-platform.md)

移動並更新「傳送含附件的交易式電子郵件」章節。[顯示全文](../../message-center/using/transactional-email-with-attachments.md)

移動並更新「資料套件最佳實務」章節。[顯示全文](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## 2020 年 4 月 {#april-2020}

FDA 權限表已移至「存取外部資料庫 (FDA)」文件。[顯示全文](../../platform/using/remote-database-access-rights.md)

更新常見問題集，其中包含清除軟快取及硬快取的秘訣。[顯示全文](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

改善「資料模型最佳實務」，並增加關於索引的額外資訊。[顯示全文](../../configuration/using/data-model-best-practices.md#indexes)

更新說明 Adobe Campaign 內建的資料模型的章節，其中包含各資料表的詳細資料。[顯示全文](../../configuration/using/data-model-description.md)

更新工作流程使用案例，重新組織至各主題章節。[顯示全文](../../workflow/using/about-workflow-use-cases.md)

加強[「退回郵件認證](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)」及[「電子郵件管理規則](../../delivery/using/understanding-delivery-failures.md#email-management-rules)」章節，並提供更新的資訊。

更新 Adobe Campaign Enhanced MTA 文章。該文章現在只適用於 Campaign Classic。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html)

## 2020 年 3月 {#march-2020}

更新資料模型最佳實務，其中包括[序列](../../configuration/using/data-model-best-practices.md#sequences)、[效能](../../configuration/using/data-model-best-practices.md#performance)及[大型資料表](../../configuration/using/data-model-best-practices.md#large-tables)等。[顯示全文](../../configuration/using/data-model-best-practices.md)

推出新的章節，說明 Adobe Campaign 內建的資料模型以及資料表之間的互動。[顯示全文](../../configuration/using/data-model-description.md)

文件首頁新增其他關鍵連結。[顯示全文](../../campaign-classic-home.md)

新增使用案例，說明如何將 Adobe Target 的動態優惠方案整合至 Adobe Campaign 的電子郵件。[顯示全文](../../integrations/using/inserting-a-dynamic-image.md)

推出新的章節，其中詳列 Adobe Campaign 提供的不同語言。[顯示全文](../../platform/using/adobe-campaign-workspace.md#languages)

更新存取管理準則，其中包含更多關於已命名的權限的資訊。[顯示全文](../../platform/using/access-management.md#named-rights)

## 2020 年 2 月 {#february-2020}

推出新的章節，說明設計 Adobe Campaign 資料模型時的最佳實務和主要建議。[顯示全文](../../configuration/using/data-model-best-practices.md)

推出關於「技術電子郵件設定」新章節。[顯示全文](../../installation/using/email-deliverability.md)

更新「傳遞能力常見問題集」，其中包含關於「已達配額」錯誤訊息的詳細資料。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-deliverability-faq.html#FAQ)

新的電子郵件供應商現在支援 AMP for Email：相關文件已更新。[顯示全文](../../delivery/using/defining-interactive-content.md)

改善「電子郵件封存」章節。[顯示全文](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 2020 年 1 月 {#release-20-1}

**20.1版中包含的新功能**

Snowflake FDA Connector——[顯示全文](../../platform/using/specific-configuration-database.md#configure-access-to-snowflake)

Hadoop FDA Connector 增強功能——[顯示全文](../../platform/using/specific-configuration-database.md#configure-access-to-hadoop-3)

**此版本隨附的其他文件更新**

更新「[安裝](../../installation/using/before-reading.md)、[生產](../../production/using/foreword.md)及[設定](../../configuration/using/additional-parameters.md)」指南，其中包含 nlserver 服務啟動使用的新系統單元。您仍然可以使用 /etc/init.d/nlserver6，但 Adobe 建議您現在使用 systemctl 命令與 nlserver 服務互動。

更新安裝指南，並與最新版本的相容性矩陣同步。新增了新支援的系統。移除已棄用及不支援的系統的項目。[顯示全文](../../installation/using/before-reading.md)

更新相容性矩陣，其中包含 Hadoop 3.0 及 Snowflake FDA 連接器。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

安裝指南新增了有關 IP 相似性的最佳實務。[顯示全文](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

更新「資料庫清理工作流程」章節。提供的批次圖表，現在已反映代碼實作。[顯示全文](../../production/using/database-cleanup-workflow.md)

「交易式傳訊指南」已新增 FDA over HTTP 的限制。[顯示全文](../../production/using/database-cleanup-workflow.md)

針對讓您為 **[!UICONTROL JavaScript code]** 及 **[!UICONTROL Advanced JavaScript code]** 工作流程活動定義逾時期限的新選項，新增相關資訊。[顯示全文](../../workflow/using/sql-code-and-javascript-code.md)

針對 **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** 節點提供的新的&#x200B;**[!UICONTROL Start Pending]** 檢視，新增相關資訊。[顯示全文](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

移動、重新組織並改善「[傳送推播通知](../../delivery/using/about-mobile-app-channel.md)指南」，其中包含已釐清的相關資訊。

[此處](../../reporting/using/properties-of-the-report.md#defining-additional-settings)記錄 URL 報表設定的新參數。

更新 **Campaign Classic 內部部署及託管功能矩陣**&#x200B;頁面，其中包含新的 FDA 連接器。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-on-prem-vs-hosted.html)

更新「**Campaign Classic 功能矩陣」**&#x200B;頁面。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

[此處](../../production/using/database-cleanup-workflow.md#cleanup-of-nmsaddress)記錄新的 **[!UICONTROL Cleanup of Nmsaddress]** 工作流程。

新增在工作流程使用查詢活動時的限制。[顯示全文](../../workflow/using/query.md)。

新增新章節，詳細說明增強的電子郵件地址驗證規則，以利發生軟體錯誤時將地址傳送至隔離。[顯示全文](../../delivery/using/understanding-quarantine-management.md#soft-error-management)

關於執行個體是否使用 Enhanced MTA，設定檔的參數現在已有紀錄。[顯示全文](../../installation/using/the-server-configuration-file.md#mta)

移動、重新組織及加強「傳遞能力」章節，其中包含更新的內容。[顯示全文](../../delivery/using/about-deliverability.md)

推出新的章節，說明 Adobe Campaign Classic 資料模型基本概念及如何存取各資料表的相關說明。[顯示全文](../../configuration/using/about-data-model.md)

更新 Adobe Campaign Enhanced MTA 文章，其中包含針對沒有為每則訊息新增必要的 Enhanced MTA 標題的執行個體，安裝特定的態樣套件的詳細資料。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html#impacts)

重新組織關於查詢設計的使用案例，並分成不同章節。[顯示全文](../../workflow/using/querying-recipient-table.md)

推出新的章節，說明在 Adobe Campaign Classic 管理優惠方案及使用互動模組的秘訣與訣竅。[顯示全文](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

已進一步加強「互動」文件，包含多個影片的連結，以協助您進一步瞭解如何管理優惠方案。[顯示全文](../../interaction/using/interaction-and-offer-management.md)

關於如何最佳化執行個體上執行的查詢的最佳實務文章，已整合至文件。[顯示全文](../../workflow/using/query.md#optimizing-queries)

更新並重新組織報告指南。[顯示全文](../../reporting/using/about-adobe-campaign-reporting-tools.md)

新增如何在工作流程使用執行個體變數的範例。[顯示全文](../../workflow/using/javascript-scripts-and-templates.md)

## 2019 年 12 月{#december-2019}

Campaign 選項清單已新增「WdbcOptions_TempDbName」選項。[顯示全文](../../installation/using/configuring-campaign-options.md)

「FDA 矩陣」頁面已移至[此處](../../platform/using/remote-database-access-rights.md)。

「存取權限矩陣」頁面已移至[此處](https://docs.adobe.com/content/help/zh-Hant/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)。

移動說明如何定義 AMP 互動式內容的章節。[顯示全文](../../delivery/using/defining-interactive-content.md)

**19.2版本中包含的新功能**

加州消費者隱私保護法 (CCPA) ──[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)

AMP 互動式內容——[顯示全文](../../delivery/using/defining-interactive-content.md)

工作流程即時監控——[顯示全文](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

安全的 SMS 傳訊 (TLS) ──[顯示全文](https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html)

**此版本隨附的其他文件更新**

推出 Adobe Campaign Enhanced MTA 文件。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html)

新增章節，說明如何疑難排解行銷活動中，持續顯示「盡快開始」狀態的工作流程。[顯示全文](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

Campaign 選項清單已新增新的「NmsOperation_DeliveryPreparationWindow」及「WdbcKillSessionPolicy」選項。[顯示全文](../../installation/using/configuring-campaign-options.md)

推出說明 Adobe Campaign Classic 資料模型基本概念的新文件。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-datamodel.html)

本[章節](../../delivery/using/personalization-fields.md#timing-out-personalization)記錄傳遞屬性中新的「**最大個人化執行時間**」選項。

更新使用包含 logon() 及 query() 的 **HttpServletRequest** 的 API 呼叫範例。[顯示全文](../../configuration/using/web-service-calls.md)。

針對綱要定義中的 **sqlDefault** 屬性，新增建議。[顯示全文](../../configuration/using/elements-and-attributes.md#attribute-description)。

現在「**與 Adobe Experience Cloud 整合**」指南已提及 Adobe Campaign 與 Adobe Real-time Customer Data Platform 之整合。[顯示全文](../../integrations/using/about-campaign-integrations.md)。

## 2019 年11月 {#november-2019}

「[多工處理中間來源伺服器](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server)」及「[支援數個控制執行個體](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances)」章節已新增警示訊息，說明這些部署不支援完全託管及混合型客戶。

新增新的章節，說明傳送電子郵件時，如何強制使用字元編碼。[顯示全文](../../delivery/using/sending-messages.md#character-encoding)

新增「存取管理」章節，其中包含&#x200B;**隱私資料權限**。[顯示全文](../../platform/using/access-management.md#named-rights)

新增相關資訊，以規範個人化欄位內容不得超過 1024 個字元。[顯示全文](../../delivery/using/personalization-fields.md)

控制面板文件已整合至新的共同作業文件集。[顯示全文](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/control-panel-home.html)

更新「傳遞最佳實務快速入門手冊」。[顯示全文](../../delivery/using/delivery-best-practices.md)

## 2019 年 10 月 {#october-2019}

更新 Campaign Standard 及 Campaign Classic 的錯誤訊息清單。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

改善並加強 GDPR 快速入門手冊。該手冊現在是包含 GDPR 及 CCPA 的隱私權管理文件。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy.html)

針對 Campaign Classic 追蹤功能，新增了新的疑難排解頁面。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/classic-tracking-troubleshooting.html)。

新增了 Adobe Analytics Data Connector 最佳實務頁面。[深入瞭解 Adobe Analytics Data Connector](../../platform/using/adobe-analytics-data-connector.md)

移動並更新「傳遞最佳實務快速入門手冊」。[顯示全文](../../delivery/using/delivery-best-practices.md)

SMS 頻道文件新增了建議，以避免以同一供應商帳戶利用 Extended generic SMPP 連接器使用多個外部帳戶時發生問題。[顯示全文](../../delivery/using/sms-channel.md#automatic-reply)

「排程器活動」文件新增了關於如何防止同時執行工作流程的資訊。[顯示全文](../../workflow/using/scheduler.md)

文件新增了針對內部部署安裝設定收件匣轉譯的步驟。[顯示全文](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## 2019 年 9 月{#september-2019}

新增了新的頁面，以說明維護 Campaign Classic 的一般準則。[顯示全文](../../production/using/monitoring-guidelines.md)

關於工作流程監控的相關資訊已集中至新的專屬章節。[顯示全文](../../workflow/using/monitoring-workflow-execution.md)。

已新增了新的頁面，說明 Adobe Campaign Classic 追蹤的一般準則。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-tracking.html)。

更新工作流程和傳遞效能改善的最佳實務。[深入瞭解工作流程](../../workflow/using/workflow-best-practices.md)，以及 [深入瞭解傳遞](../../delivery/using/monitoring-a-delivery.md#best-practices-performance)。

## 2019 年 5 月 {#release-19-1}

**19.1版中包含的新功能**

控制面板——[顯示全文](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/control-panel-home.html)

稽核軌跡——[顯示全文](../../production/using/audit-trail.md)

**此版本隨附的其他文件更新**

建立了新的「組建版本升級常見問題集」。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/build-upgrade-faq.html)

更新[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)。更新了支援的資料庫系統清單，以及支援的 Android/iOS 版本及相關的 SDK。封存[ 19.0 相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix-19-0.html)。

更新「已棄用和已移除的 Campaign Classic 功能」頁面。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)

《安裝指南》新增伺服器設定檔的說明。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

新增了新的章節，說明託管及混合模式的安裝及設定步驟。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

新增了新的章節，說明 Campaign 伺服器解除安裝步驟。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

更新「[安全性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、[傳遞能力](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)[及隱私權](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)」快速入門手冊。

更新預先處理工作流程選項的說明，以反映產品變更。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

更新 Marketing Cloud Triggers Technote。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html)

更新錯誤消息清單。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

新增有關交易式傳訊 SOAP 驗證方法的詳細資訊。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

更新 Apache 設定步驟已更新。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

新增了包含 Campaign Standard 和 Classic 的端點清單頁面。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/campaign-endpoints.html)

更新「資料套件最佳實務」文章。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/data-package-best-practices.html)

更新「管理優惠方案」文件，新增了列出最佳實務的新章節。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

建立了新的知識庫文章，說明如何在 Adobe Campaign Classic 使用優惠方案目錄。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/offer-best-practices.html)

加強「子工作流程活動」章節，並提供使用範例。[顯示全文](../../workflow/using/sub-workflow.md)

更新 [Campaign Classic 內部部署與托管功能矩陣](https://helpx.adobe.com/tw/campaign/kb/acc-on-prem-vs-hosted.html)知識庫文章，其中包含與封存電子郵件相關的資訊。

更新了交易式傳訊文件，其中包含關於範本發佈的說明。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

更新「未處理的退回郵件」章節，其中包含「轉寄地址」和「錯誤地址」欄位的詳細資訊。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

新增了關於工作流程規劃最佳實務的新章節。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

Campaign 選項清單新增了兩個選項： XtkSecurity_Restrict_EditXML 及 NmsOperation_OperationMgtDebug。
[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

新增了有關 Campaign Classic 可以使用的不同外部帳戶，以及如何設定這些帳戶的相關資訊。
[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

更新「Analytics Data Connector 」章節，以反映介面變更。
[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

新增了關於帳單報表的資訊。
[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

更新了「共用受眾整合」的文件。
[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

更新下列技術文件： [SMS 連接器通訊協定與設定](https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html)，以及 [序列自動產生](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)。

更新「技術工作流程」章節。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

改善並更新「Campaign 網域名稱設定程序」。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html)

更新 Android應用程式從 Google 雲端傳訊 (GCM) 移轉至 Firebase 雲端傳訊 (FCM) 的移轉程序。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/migrate-to-fcm.html)

更新「Campaign 硬體調整指南」。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)

新增關於 Teradata 外部帳戶的「查詢集區」的相關資訊。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## 2019 年 1 月{#release-doc-16-01-2019}

更新 Marketing Cloud Triggers Technote。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/triggers-and-campaign.html)

已於「優惠方案核准」章節新增說明，以指出「已核准內容」提及是代表內容核准流程已完成，不論所有優惠方案是否已啟用/核准。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

「安裝指南」新增了新的章節，列出「管理/平台/選項」節點中的選項。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

新增了使用種子地址保護郵寄清單的相關資訊。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

建立和傳送傳遞時的主要步驟已重新分組成為新章節，並視需要引述各管道。[顯示全文](../../delivery/using/steps-about-delivery-creation-steps.md)

移動、重新組織及改善「[電子郵件封存](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)」章節，並釐清相關資訊：

* 新增了有關每一連線的電子郵件及 BCC 傳送 IP 參數的最佳實務。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* 如果您已透過舊版組建版本 (Adobe Campaign 17.2之前——組建版本 8795) 來使用電子郵件封存，我們更新了升級至新版電子郵件封存系統 (BCC) 的步驟。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

「使用工作流程自動化」指南新增了使用案例：傳送個人化警報給營運商。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

更新「移轉至新版本」章節。本文件現在僅詳細說明從任何舊版移轉至 Adobe Campaign Classic v7 的步驟，因為現在已無法移轉至 Adobe Campaign v6.11。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

釐清「出現傳遞暫時性錯誤後重試」章節。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

「定義電子郵件內容」章節，新增了前往「數位內容編輯器」章節的連結。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

更新「交易式傳訊架構」章節，其中包含控制項及執行實例無法安裝在同一台電腦上的警告。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

更新「工作流程監控」章節，其中包含適用於 8700 到 8977 (18.10) 組建版本之間的說明，包括如何為這些組建版本安裝 Workflow HeatMap 套件的技術文件連結。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

新增了使用案例，說明如何使用工作流程中的「擴充活動」，傳送包含自訂資料欄位的電子郵件。[顯示全文](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

功能影片已移至[此處](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html)。

針對 [Teradata](https://helpx.adobe.com/tw/campaign/kb/campaign_fda_teradata.html) 和 [MySQL 5.7](https://helpx.adobe.com/tw/campaign/kb/campaign_fda_mysql.html) 新增了兩則技術文件。
