---
product: campaign
title: Adobe Campaign Classic v7 文件更新
description: 本頁列出了 Adobe Campaign Classic 文件中的所有新功能和更新
feature: Release Notes
role: User
level: Beginner
exl-id: 07c1f4a3-cf16-4a9b-b402-e13258799f91
source-git-commit: 98859f6452b5f1008a19a48b9b77edd9acf49261
workflow-type: tm+mt
source-wordcount: '3746'
ht-degree: 100%

---

# 文件更新{#documentation-updates}

此頁面按月及按各個 Campaign 版本列出所有新功能及文件更新。

如需版本相關更新，請參閱 [Adobe Campaign Classic 發行說明](../../rn/using/latest-release.md)。

## 2024

### 2024 年 6 月 {#june-2024}

已新增附註，以指定重新啟動工作流程時如何清除執行個體變數。 [閱讀更多](../../workflow/using/starting-a-workflow.md)

### 2024 年 4 月 {#apr-2024}

新增了使用 Adobe Identity Management System (IMS) 建立使用者的警告說明。 [閱讀更多](../../platform/using/access-management.md)

新增了 Web 下載工作流程活動缺少的選項。 [閱讀更多](../../workflow/using/web-download.md)

警告說明已新增到&#x200B;**變更維度**&#x200B;和&#x200B;**變更資料來源**&#x200B;關於它們在工作流程的使用活動。[閱讀更多](../../workflow/using/change-data-source.md)

### 2024 年 3 月 {#mar-2024}

針對 iOS 權杖型 APN 連線行動應用程式設定部分已更新。 [閱讀更多](../../delivery/using/configuring-the-mobile-application.md#creating-ios-app)

### 2024 年 1 月 {#jan-2024}

已新增有關如何定義直接郵件的預設 postalAddress 欄位，以及確保地址完整的重要原因。 [深入了解](../../delivery/using/about-direct-mail-channel.md)

新增如何在中間來源基礎結構的 Campaign 中，設定簡訊頻道的新頁面。 [深入了解](../../delivery/using/sms-set-up-mid.md)

## 2023 年

### 2023 年 12 月 {#dec-2023}

JWT (JSON Web 權杖) 目前正在折舊中，並即將由 OAuth 取代。此轉變會在 Campaign 即將發行的版本中逐步執行，並更新文件以反映這些更新。

新增 Amazon Redshift 的 FDA 外部帳戶設定。[深入了解](../../installation/using/configure-fda-redshift.md)

### 2023 年 8 月 {#aug-2023}

已新增限制，以指明無法使用 Adobe Campaign 解壓縮大於 4GB 的壓縮檔案。 [深入了解](../../platform/using/unzip-decrypt.md)

### 2023 年 4 月 {#apr-2023}

新增如何在內部部署/混合環境中啟用 Microsoft Edge Chromium 的技術說明。 [深入了解](../../technotes/using/edge-chromium.md)

### 2023 年 3 月 {#mar-2023}

更新發行說明一節，提供 7.3.3 改善與修補程式。 [深入了解](latest-release.md)


+++ 2022


## 2022 年 11 月 {#nov-2022}

更新發行說明一節，提供 7.3.2 改善與修補程式。 [深入了解](latest-release.md)

更新相容性比較表，提供 Teradata 17 支援。 [深入了解](compatibility-matrix.md)

已更新「檔案與資源管理」一節，包含 **uploadWhiteList** 屬性的額外資訊。 [深入了解](../../installation/using/file-res-management.md)

已更新安全性區域文件，包含 **allowDebug** 屬性的額外資訊。 [深入了解](../../installation/using/security-zones.md#recommendations)

已更新移轉指南。 針對不支援的 Adobe Campaign 版本，已移除相關參考。 [深入了解](../../migration/using/about-migration.md)


## 2022 年 7 月 {#july-2022}

<!--Transition to the new deliverability server is detailed in a new technote. [Read more](../../technotes/using/deliverability-server.md)-->

**7.3.1 版本隨附的文件更新**

已更新相容性對照表。 [閱讀全文](compatibility-matrix.md)

更新發行說明一節。 [閱讀全文](rn-overview.md)

iOS 15 的即時通知。 [閱讀全文](../../delivery/using/create-notifications-ios.md)


## 2022 年 3 月 {#mar-2022}

新增 **[!UICONTROL Test SMTP delivery]** 選項的詳細說明。 [閱讀全文](../../delivery/using/steps-sending-the-delivery.md#delivery-additiona-parameters)

「開始升級」頁面已更新，以澄清 Campaign 主控台升級指引。 [閱讀全文](../../rn/using/rn-overview.md)

現已推出新的 Campaign v7.2.2 版本。 [閱讀全文](../../rn/using/latest-release.md)

<!--Added troubleshooting information related to the ACS connector. [Read more](../../integrations/using/troubleshooting-the-acs-connector.md)-->

已將已到期的舊版 PostgreSQL 版本新增至 [已棄用和已移除的功能](../../rn/using/deprecated-features.md#dbe-eol) 的頁面。

## 2022 年 2 月 {#february-2022}

更新&#x200B;**檔案傳輸**&#x200B;活動部分，在&#x200B;**傳輸後刪除來源檔案**&#x200B;的情況下，提示在 SFTP 目錄中手動監視封存內容的大小。 [閱讀全文](../../workflow/using/file-transfer.md#properties)

釐清隔離與封鎖清單章節。[閱讀全文](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

有關如何把位址加入隔離清單以及如何從隔離清單刪除位址的部分已更新。 [閱讀全文](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

加入工作流程最佳實務，建議不要在同一工作流程上執行多個停止請求。 [閱讀全文](../../workflow/using/workflow-best-practices.md)

新增有關如何阻止在行銷活動中執行定期傳遞的資訊。 [閱讀全文](../../workflow/using/recurring-delivery.md)

## 2022 年 1 月 {#january-2022}

**7.2.1 版本隨附的其他文件更新**

已更新相容性對照表。 [閱讀全文](compatibility-matrix.md)

更新發行說明一節。 [閱讀全文](rn-overview.md)

已針對 Snowflake 更新 FDA 外部帳戶設定。 [閱讀全文](../../installation/using/configure-fda-snowflake.md)

已針對 Azure Synapse 分析更新 FDA 外部帳戶設定。 [閱讀全文](../../installation/using/configure-fda-synapse.md#azure-external)

已更新 Google BigQuery FDA 連接器。 [閱讀全文](../../installation/using/configure-fda-google-big-query.md)

在棄用後，Microsoft CRM、Salesforce、Oracle CRM 隨選操作活動已從文件中移除。

新選項&#x200B;**錯誤時中止**&#x200B;已新增至工作流程「錯誤管理」區段。 [閱讀全文](../../workflow/using/advanced-parameters.md#in-case-of-errors)

已在 CRM 連接器活動中新增批次更新選項。 [閱讀全文](../../workflow/using/crm-connector.md)

+++

+++ 2021 年

## 2021 年 12 月{#dec-2021}

Campaign Classic v7 版本說明已重新整理，以簡化導覽。 [閱讀全文](rn-overview.md)

更新並改善 Campaign 中表單版本的相關文件。 [閱讀全文](../../configuration/using/editing-forms.md)

CentOs 8 已到期，現已被 Adobe Campaign Classic 淘汰。 [閱讀全文](deprecated-features.md)

## 2021 年 11 月{#nov-2021}

新增傳入簡訊(MO) 的限制。 [閱讀全文](../../delivery/using/sms-protocol.md#multipart)

更新 CRM 連接器部署的移轉流程記錄檔詳細資料。 [閱讀全文](../../migration/using/testing-the-migration.md#verification-process)

新增關於 IMS 權限的需求，以實施 Adobe Campaign-Adobe Analytics 整合。 [閱讀全文](../../integrations/using/adobe-analytics-provisioning.md)

更新 Adobe Analytics 資料連接器服務終止日期 (2022 年 3 月 1 日至 2022 年 8 月 17 日)。 [閱讀全文](deprecated-features.md)

新增了關於如何使用 JavaScript 計算值、交換資料，以及使用 SOAP 呼叫執行特定作業的章節。[閱讀全文](../../workflow/using/javascript-scripts-and-templates.md)

在工作流程中新增 JavaScript 程式碼實施範例。 [閱讀全文](../../workflow/using/javascript-in-workflows.md)


## 2021 年 10 月{#oct-2021}

現有技術已分組到新的 **Technote** 部分。

更新「**硬體調整建議**」頁面，並將其新增至「**技術備註**」段落。 [閱讀全文](../../technotes/using/hardware-sizing.md)

## 2021 年 9 月{#sept-2021}

**21.1.4 版本隨附的其他文件更新**

已刪除&#x200B;**儀表**&#x200B;圖表類型。

移除 Adobe Flash 後，已更新報表和 Web 應用程式螢幕擷取畫面和參數。

[帳單技術工作流程](../../production/using/monitoring-processes.md#billing-report)說明已更新為新的護欄。

## 2021 年 8 月{#aug-2021}

新增新的工作流程活動：變更資料來源 — [了解更多](../../workflow/using/change-data-source.md)

可用性徽章已新增至文件頁面： **僅適用於 v7**&#x200B;的 Campaign Classic v7 功能，而&#x200B;**適用於 v7 和 v8** 的常見功能。

已新增關於 Campaign 與 AEM Assets 之間整合的附註，此整合已從 Adobe Experience Manager 6.4 開始解壓縮。 [了解更多](../../integrations/using/configuring-access-to-assets.md)


## 2021 年 7 月 {#july-2021}

[Campaign 21.1.3 版本已移至](../../rn/using/latest-release.md#release-21-1-3-build-9330)「一般可用性」(GA)。


## 2021 年 6 月 {#june-2021}

**異動訊息**&#x200B;區段已重新組織，並以新的「開始使用」區段加以釐清，包括[擴充型方案](../../message-center/using/about-transactional-messaging.md#transactional-messaging-operating-principle)，以便更清楚瞭解此流程。 [顯示全文](../../message-center/using/about-transactional-messaging.md)

**21.1.3 版本隨附的其他文件更新**

與 Adobe Journey Orchestration 整合 — [深入瞭解](https://experienceleague.adobe.com/docs/journeys/using/action-journeys/acc-action.html?lang=zh-Hant)。 [此頁面](https://experienceleague.adobe.com/docs/journeys/using/use-cases-journeys/campaign-classic-use-case.html?lang=zh-Hant)中提供逐步使用案例

LINE 頻道增強功能 — [深入瞭解](../../delivery/using/line-channel.md)

全新 Vertica Analytics FDA 連接器 — [深入瞭解](../../installation/using/configure-fda-vertica.md)

全新 Google BigQuery FDA 連接器 - [了解更多](../../installation/using/configure-fda-google-big-query.md)

「帳單 (帳單)」技術工作流程描述現在包括最初由「活動帳單設定檔案數 (billingActiveContactCount)」執行的任務。 [深入了解](../../workflow/using/about-technical-workflows.md)

## 2021 年 5 月 {#may-2021}

更新並改善「工作流程熱度圖」報告文件。 [顯示全文](../../workflow/using/heatmap.md)

「相容性對照表」中更新了 Campaign 用戶端主控台需求。 [顯示全文](../../rn/using/compatibility-matrix.md#ClientConsoleoperatingsystems)

改善並釐清 Campaign 用戶端主控台安裝的步驟。 [顯示全文](../../installation/using/installing-the-client-console.md)

已建立有關追蹤 URL 簽名問題的新技術。 [顯示全文](../../technotes/using/tracked-urls.md)

## 2021 年 4 月 {#april-2021}

本節將討論如何與 Adobe Experience Platform 來源及目標合作，以便在 Campaign Classic 和 Adobe 即時客戶資料平台 (RTCDP) 之間共用資料。 [顯示全文](../../integrations/using/get-started-sources-destinations.md)

已建立新技術以瞭解如何在 ISP 中斷後更新彈回資格。 [顯示全文](../../delivery/using/update-bounce-qualification.md)

## 2021 年 3 月 {#march-2021}

[開始使用簡訊章節](../../delivery/using/sms-channel.md)已重新整理並改善。 您現在可以在專屬章節中學習如何[設定簡訊頻道](../../delivery/using/sms-set-up.md)、[建立簡訊](../../delivery/using/sms-create.md)、[傳送及追蹤簡訊](../../delivery/using/sms-send.md)。

Campaign Classic 的「說明與支援選項」頁面已整合至核心文件。 [顯示全文](../../support.md)

新增了一個新的部分，其中包含最佳實務，以及有關安全性和隱私權要執行的檢查。[顯示全文](../../installation/using/get-started-security-privacy.md)

[權限管理章節](../../platform/using/access-management.md)已已改進並分成幾個部分，包括有關[操作員](../../platform/using/access-management-operators.md)、[操作員群組](../../platform/using/access-management-groups.md)、[已命名的權限](../../platform/using/access-management-named-rights.md)和[資料夾管理](../../platform/using/access-management-folders.md)的詳細資訊。

瞭解如何透過這些新頁面建立及管理您的行銷活動：
* [建立及設定行銷活動範本](../../campaign/using/marketing-campaign-templates.md)
* [行銷活動傳遞](../../campaign/using/marketing-campaign-deliveries.md)
* [選取行銷活動的對象](../../campaign/using/marketing-campaign-target.md)
* [管理相關文件](../../campaign/using/marketing-campaign-assets.md)
* [設定及管理核准流程](../../campaign/using/marketing-campaign-approval.md)

在&#x200B;**[!UICONTROL Advanced JavaScript]**&#x200B;活動部分中已新增了有關如何使用 task.setCompleted() 方法終止任務及防止將來重新呼叫的資訊。 [顯示全文](../../workflow/using/sql-code-and-javascript-code.md#adv-js-code-desc)

[傳遞能力](../../delivery/using/about-deliverability.md)區段已更新，現在包含新 [Adobe 傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)的連結。 針對適用各種 Adobe 解決方案的傳遞能力其所有一般資訊都已移至[最佳實務指南附錄](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/general-resources.html?lang=zh-Hant#additional-resources)。

## 2021 年 2 月 {#release-21.1}

**21.1 版本隨附的其他文件更新**

新的&#x200B;**電子郵件回饋服務**&#x200B;功能 (私人測試版) 已記錄在[此處](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service)。

**「伺服器設定檔」**&#x200B;區段已更新，其中包含 Campaign 使用 IMS 連線至其他服務所需的設定參數。 [顯示全文](../../installation/using/the-server-configuration-file.md#ims)

在傳遞狀態清單中，**服務提供者須考慮**&#x200B;的說明已更新：此狀態現在也用於使用[電子郵件回饋服務](../../delivery/using/sending-with-enhanced-mta.md#email-feedback-service)傳送的電子郵件傳遞。 [顯示全文](../../delivery/using/delivery-statuses.md#list-delivery-statuses)

現在已記錄新登入畫面上可用來連線至 Adobe Campaign 的鍵盤快速鍵。 [顯示全文](../../platform/using/launching-adobe-campaign.md#connecting-to-adobe-campaign)

**其他更新**

新增了一個部分，其中包含如何使用工作流程執行 A/B 測試的詳細資訊。 [顯示全文](../../delivery/using/get-started-a-b-testing.md)

「Adobe Campaign 增強型 MTA」部分已移至[此處](../../delivery/using/sending-with-enhanced-mta.md)。

已新增頁面，以提供[!DNL Campaign Classic]中追蹤功能的概述。 [顯示全文](../../delivery/using/about-message-tracking.md)

已新增疑難排解部分，用以協助您解決與追蹤相關的常見問題。 [顯示全文](../../delivery/using/tracking-troubleshooting.md)

**「傳送電子郵件」**&#x200B;部分已重新整理，並以新的子部分加以釐清。 [顯示全文](../../delivery/using/sending-messages.md)

已新增有關如何新增可個人化且支援追蹤的電子郵件連結的資訊。 [顯示全文](../../delivery/using/tracking-personalized-links.md)。

## 2021 年 1 月 {#jan-2021}

**[!UICONTROL Fork]**　活動區段已新增最佳實務而更加豐富。[顯示全文](../../workflow/using/fork.md)

**CRM 連接器**&#x200B;區段已更新、改進並重新組織。[顯示全文](../../platform/using/crm-connectors.md)。

連接 **Adobe Campaign 和 Microsoft Dynamics** 的步驟現在會在專用頁面中詳細說明。[顯示全文](../../platform/using/crm-ms-dynamics.md)。

Oracle On Demand API 現在已不再作為與 Campaign 連接的 CRM。[顯示全文](../../rn/using/deprecated-features.md)。

在[此處](../../production/using/locate-tomcat-version.md)了解如何確定 Adobe Campaign 執行個體中使用之內嵌 Tomcat Web Servlet 的目前版本。

已將技術工作流程清單及其相關聯套件增強並集中至單一頁面。[顯示全文](../../workflow/using/about-technical-workflows.md)

已重新整理&#x200B;**監視**&#x200B;指南的疑難排解區段，並利用登陸頁面使其內容更加豐富。[顯示全文](../../production/using/troubleshooting.md)。

新的&#x200B;**匯入和匯出資料**&#x200B;區段可用於與工作流程、資料壓縮、加密和匯入最佳實務相關的新頁面。[顯示全文](../../platform/using/get-started-data-import-export.md)

+++


+++ 2020 年


## 2020 年 12 月 {#dec-2020}

**傳遞監控**&#x200B;區段已改編為專題。[顯示全文](../../delivery/using/about-delivery-monitoring.md)

已新增使用案例，說明如何將傳送者的　IP　位址新增至傳遞記錄日誌中。[顯示全文](../../delivery/using/delivery-dashboard.md#use-case)

隱私權常見問答已移至[本節](../../platform/using/privacy-faq.md)。

已新增使用個案，讓您了解如何使用 **[!UICONTROL Deduplication]** 活動的合併功能。[顯示全文](../../workflow/using/deduplication-merge.md)

現在，[此處](../../delivery/using/sms-protocol.md)提供簡訊連接器通訊協定和設定頁面的完整說明。

已對&#x200B;**異動訊息**&#x200B;區段新增附註，以警告事件資料夾不得被設定為執行個體的檢視，進而避免存取權限問題。[顯示全文](../../message-center/using/about-event-processing.md#event-collection)

## 2020 年 11 月 {#nov-2020}

Campaign 資料模型概觀已改進並重新組織。[顯示全文](../../configuration/using/about-data-model.md)。

外部帳戶配置已移至[此區段](../../installation/using/external-accounts.md)。

Campaign Federated Data Access (FDA) 文件已經過改良，並包含每個外部資料庫組態的詳細資訊，且已移至[此區段](../../installation/using/about-fda.md)。

Campaign 20.2.3 版本已移至「一般可用性」(GA)。

「隱私權」區段已移動，並包含兩個新頁面：[隱私權管理](../../platform/using/privacy-management.md)及[管理隱私權要求](../../platform/using/privacy-requests.md)。

在中間來源補充伺服器設定頁面中已新增附註，以指定在伺服器設定後，不應更新外部帳戶的內部名稱。[顯示全文](../../installation/using/mid-sourcing-server.md)

已在語法上新增資訊，以在指定外部 SFTP 伺服器的路徑時使用。[顯示全文](../../platform/using/sftp-server-usage.md#external-SFTP-server)

「個人資料與角色」區段已更新為使用案例，以說明不同角色在隱私權方面如何進行互動。[顯示全文](../../platform/using/privacy-and-recommendations.md#use-case-scenario)

已新增一個區段，其中列出「隱私權」的常見問題集。[顯示全文](../../platform/using/privacy-faq.md)

## 2020 年 10 月 {#oct-2020}

**第 20.3 發行版本包含的新功能**

iOS 的推播通知改善 - [閱讀更多資訊](../../delivery/using/configuring-the-mobile-application.md)

Android 的推播通知改善 - [閱讀更多資訊](../../delivery/using/configuring-the-mobile-application-android.md)

**此版本隨附的其他文件更新**

更新相容性矩陣。[顯示全文](../../rn/using/compatibility-matrix.md)

更新「已棄用和已移除的功能」頁面。[顯示全文](../../rn/using/deprecated-features.md)

 [!DNL Gold Standard] 發行版本的發行說明和相容性對照表已於專屬頁面顯示。
[顯示全文](../../rn/using/gold-standard.md)。

已變更原本以 oAUTH 驗證設定為基礎而用於存取管道的觸發器驗證，並將其移動至 Adobe I/O。[閱讀更多資訊](../../integrations/using/about-triggers.md#implement)

**其他更新**

已更新文件頁面，以反映 Tomcat 8 更新。

已將詳細資訊新增至「取得 Adobe Campaign 版本」區段的「關於」方塊說明中。[顯示全文](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

已將執行建置升級的准則新增至「更新 Adobe Campaign Classic」區段。[閱讀全文](../../production/using/build-upgrade.md)

已將有關 Campaign 版本編號升級的常見問答集新增至 Campaign 常見問題。閱讀更多資訊[閱讀更多資訊](../../platform/using/faq-build-upgrade.md)

已在專用區段中，說明 Campaign 內部部署、託管和混合託管模型。[顯示全文](../../installation/using/hosting-models.md)

已在安裝指南中，更新並移動 Campaign 功能矩陣的每個託管模型。[顯示全文](../../installation/using/capability-matrix.md)

已改善「Campaign 報告」進階功能區段，以詳細說明如何在自訂報告中使用 URL 參數和變數。[顯示全文](../../reporting/using/advanced-functionalities.md)

已重新整理報告屬性頁面並加以擴充，以方便配置。[顯示全文](../../reporting/using/properties-of-the-report.md)

## 2020 年 9 月 {#september-2020}

已新增附註，以指明「主要」用戶檔案計數僅適用於「行銷」執行個體。[顯示全文](../../platform/using/about-profiles.md#active-profiles)

已新增有關方案版本的新範例，以將欄位連結至現有的參考表。[顯示全文](../../configuration/using/examples-of-schemas-edition.md#uc-link)

已新增附註，說明如何在傳遞種子地址時使用其他資料。[顯示全文](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## 2020 年 8 月 {#aug-2020}

在專屬區段中，了解與傳遞設計以及與 Campaign 一同傳送相關的最佳實務。[顯示全文](../../delivery/using/delivery-best-practices.md)

已改善「傳遞」最佳實務登陸頁面，以方便存取子區段。[顯示全文](../../delivery/using/about-deliverability.md)

現在已提供有關下列主題的教學影片：

* [如何使用類型規則和預先定義的篩選器來設定疲勞管理](../../campaign-opt/using/about-campaign-typologies.md)

* [如何在行銷活動中建立電子郵件](../../campaign/using/marketing-campaign-deliveries.md)

* [如何建立具有條件式內容的多語言電子報](../../delivery/using/conditional-content.md)

* [如何設定及部署傳遞範本](../../delivery/using/creating-a-delivery-template.md)

* [如何啟用及使用電子郵件 AMP](../../delivery/using/defining-interactive-content.md)

* [使用動態內容區塊個人化電子郵件](../../delivery/using/personalization-blocks.md)

* [如何使用個人化欄位進行電子郵件個人化](../../delivery/using/personalization-fields.md)

* [如何管理電子郵件中的種子和證明](../../delivery/using/steps-defining-the-target-population.md)

* [如何設定循環傳送](../../workflow/using/recurring-delivery.md)

* [如何設定連續傳送](../../workflow/using/continuous-delivery.md)

在連線至 FTP 伺服器且收到「無法解決主機名稱」錯誤後，已將資訊新增至要執行的檢查和動作中。[顯示全文](../../platform/using/sftp-server-usage.md)

已參考[工作流程使用案例](../../workflow/using/about-workflow-use-cases.md)清單的新使用案例：

* 自動建立、編輯和發佈內容
* 在傳送傳遞前，設定收件者核准程序
* 調用查詢中的執行個體變數
* 將分割百分比套用在人口上

已新增其他使用資訊與變數使用附註以豐富本&#x200B;**[!UICONTROL AND-join]**&#x200B;活動章節內容。[閱讀全文](../../workflow/using/and-join.md)

## 2020 年 7 月 {#july-2020}

已將有關如何使用增量查詢以自動更新清單的使用案例新增至工作流使用案例中。[顯示全文](../../workflow/using/about-workflow-use-cases.md)

已重新整理[發行說明](../../rn/using/latest-release.md)：已新增[概述頁面](../../rn/using/latest-release.md)，其中包含有關建置狀態、升級流程、建議和重要連結資訊。此外，也新增了 [[!DNL Gold Standard]  發行版本](../../rn/using/gold-standard.md)專屬頁面，並整合[相容性矩陣](../../rn/using/compatibility-matrix.md)。

新增了與 Campaign Classic 監視相關的准則。[顯示全文](../../production/using/monitoring-guidelines.md)

已提升「隱私權與同意」一節，其提供更詳細的資訊和有用的連結。[顯示全文](../../platform/using/privacy-and-recommendations.md)

已更新 Campaign Classic 頁面的「隱私權管理」，其中包含「規範」欄位資訊，當您使用 API 允許設定自動隱私權要求流程時，便可使用此欄位。[深入了解](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

「隱私權管理概覽」頁面已更新，其中加入泰國個人資料保護法 (PDPA) 與巴西 Lei Geral de Proteção de Dados (LGPD) 的相關資訊。[深入了解](../../platform/using/privacy-and-recommendations.md)

已將資訊新增至子工作流程記錄和行為中，以防發生錯誤。[顯示全文](../../workflow/using/sub-workflow.md)

已將最佳實務新增至&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動區段。[顯示全文](../../workflow/using/scheduler.md)

## 2020 年 6 月 {#june-2020}

更新「移除已隔離的位址」章節，內容包括釐清將位址自動從隔離清單移除的案例。[顯示全文](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

新增使用案例，以說明如何使用「控制面板」及「行銷活動工作流程」進行資料[加密](../../platform/using/zip-encrypt.md)與[解密](../../platform/using/unzip-decrypt.md)。

Experience Cloud Triggers 和 Adobe Campaign Classic 整合頁面已移至[此處](../../integrations/using/about-triggers.md)。

## 2020 年 7 月 {#release-20-2}

**第 20.2 發行版本包含的新功能**

支援表情符號 - [顯示全文](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA Connector - [顯示全文](../../installation/using/configure-fda-synapse.md)

泰國及巴西隱私權法 - [顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

**此版本隨附的其他文件更新**

[本章節](../../message-center/using/publishing-message-templates.md#template-unpublication)將介紹啟用取消發佈交易式訊息範本的新選項。

新選項可以讓您傳送包含從個人化 URL 下載的影像及附件的電子郵件時，設定限制；此新選項已新增至 Campaign Classic 選項清單。[顯示全文](../../installation/using/configuring-campaign-options.md#delivery)

[本章節](../../delivery/using/steps-validating-the-delivery.md#improving-delivery-analysis)將介紹新的&#x200B;**「在資料庫準備傳遞組件**」選項。

釐清並更新「驗證傳遞」章節。[顯示全文](../../delivery/using/steps-validating-the-delivery.md)

[「伺服器設定檔」](../../installation/using/the-server-configuration-file.md)章節新增與新的追蹤連結簽章機制相關的參數。

更新相容性矩陣。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

更新「清理工作流程」章節。[進一步了解](../../production/using/database-cleanup-workflow.md)

Campaign 網路端點已移至此[章節](../../installation/using/campaign-network-endpoints.md)。

「Spam Assassin 安裝」章節更新了新的安裝檔案名稱。[進一步了解](../../installation/using/configuring-spamassassin.md#installing-spamassassin)

更新有關複製環境的章節。[進一步了解](../../production/using/duplicating-environments.md#step-2---export-the-target-environment-configuration--dev-)

## 2020 年 5 月 {#may-2020}

移動並改善「監控傳遞能力」章節。[顯示全文](../../delivery/using/monitoring-deliverability.md)

移動並改善「傳遞能力疑難排解」章節。[顯示全文](../../delivery/using/deliverability-faq.md)

改善啟動新平台時的傳遞能力指南內容。[顯示全文](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant#transition-process)

移動並更新「傳送含附件的交易式電子郵件」章節。[顯示全文](../../message-center/using/transactional-email-with-attachments.md)

移動並更新「資料套件最佳實務」章節。[顯示全文](../../platform/using/working-with-data-packages.md#data-package-best-practices)

## 2020 年 4 月 {#april-2020}

FDA 權限表已移至「存取外部資料庫 (FDA)」文件。[顯示全文](../../installation/using/remote-database-access-rights.md)

更新常見問題集，其中包含清除軟快取及硬快取的秘訣。[顯示全文](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)

改善「資料模型最佳實務」，並增加關於索引的額外資訊。[顯示全文](../../configuration/using/data-model-best-practices.md#indexes)

更新說明 Adobe Campaign 內建的資料模型的章節，其中包含各資料表的詳細資料。[顯示全文](../../configuration/using/data-model-description.md)

更新工作流程使用案例，重新組織至各主題章節。[顯示全文](../../workflow/using/about-workflow-use-cases.md)

加強[「退回郵件認證](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)」及[「電子郵件管理規則](../../delivery/using/understanding-delivery-failures.md#email-management-rules)」章節，並提供更新的資訊。

更新 Adobe Campaign Enhanced MTA 文章。該文章現在只適用於 Campaign Classic。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html)

## 2020 年 3 月 {#march-2020}

更新資料模型最佳實務，其中包括[序列](../../configuration/using/data-model-best-practices.md#sequences)、[效能](../../configuration/using/data-model-best-practices.md#performance)及[大型資料表](../../configuration/using/data-model-best-practices.md#large-tables)等。[顯示全文](../../configuration/using/data-model-best-practices.md)

推出新的章節，說明 Adobe Campaign 內建的資料模型以及資料表之間的互動。[顯示全文](../../configuration/using/data-model-description.md)

文件首頁新增其他關鍵連結。[顯示全文](../../campaign-classic-home.md)

新增使用案例，說明如何將 Adobe Target 的動態優惠方案整合至 Adobe Campaign 的電子郵件。[顯示全文](../../integrations/using/inserting-a-dynamic-image.md)

推出新的章節，其中詳列 Adobe Campaign 提供的不同語言。[顯示全文](../../platform/using/adobe-campaign-workspace.md#languages)

更新存取管理準則，其中包含更多關於已命名的權限的資訊。[顯示全文](../../platform/using/access-management-named-rights.md)

## 2020 年 2 月 {#february-2020}

推出新的章節，說明設計 Adobe Campaign 資料模型時的最佳實務和主要建議。[顯示全文](../../configuration/using/data-model-best-practices.md)

推出關於「技術電子郵件設定」新章節。[顯示全文](../../installation/using/email-deliverability.md)

更新「傳遞能力常見問題集」，其中包含關於「已達配額」錯誤訊息的詳細資料。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/acc-deliverability-faq.html#FAQ)

新的電子郵件供應商現在支援 AMP for Email：相關文件已更新。[顯示全文](../../delivery/using/defining-interactive-content.md)

改善「電子郵件封存」章節。[顯示全文](../../installation/using/email-archiving.md#recommendations-and-limitations)

## 2020 年 1 月 {#release-20-1}

**第 20.1 發行版本包含的新功能**

Snowflake FDA Connector - [顯示全文](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA Connector 增強功能 - [顯示全文](../../installation/using/configure-fda-hadoop.md)

**此版本隨附的其他文件更新**

更新「[安裝](../../installation/using/general-architecture.md)、[生產](../../production/using/foreword.md)及[設定](../../configuration/using/additional-parameters.md)」指南，其中包含 nlserver 服務啟動使用的新系統單元。您仍然可以使用 /etc/init.d/nlserver6，但 Adobe 建議您現在使用 systemctl 命令與 nlserver 服務互動。

已更新安裝指南，並與最新版本的相容性比較表同步。新增了新的可支援系統。移除已棄用及不支援的系統。[顯示全文](../../installation/using/general-architecture.md)

更新相容性矩陣，其中包含 Hadoop 3.0 及 Snowflake FDA 連接器。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

安裝指南新增了有關 IP 相似性的最佳實務。[顯示全文](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

更新「資料庫清理工作流程」章節。提供的批次圖表，現在已反映代碼實作。[顯示全文](../../production/using/database-cleanup-workflow.md)

「交易式傳訊指南」已新增 FDA over HTTP 的限制。[顯示全文](../../production/using/database-cleanup-workflow.md)

針對讓您為 **[!UICONTROL JavaScript code]** 及 **[!UICONTROL Advanced JavaScript code]** 工作流程活動定義逾時期限的新選項，新增相關資訊。[顯示全文](../../workflow/using/sql-code-and-javascript-code.md)

針對 **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** 節點提供的新的&#x200B;**[!UICONTROL Start Pending]** 檢視，新增相關資訊。[顯示全文](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

移動、重新組織並改善「[傳送推播通知](../../delivery/using/about-mobile-app-channel.md)指南」，其中包含已釐清的相關資訊。

[此處](../../reporting/using/properties-of-the-report.md#defining-additional-settings)記錄 URL 報表設定的新參數。

更新 **Campaign Classic 內部部署及託管功能矩陣**&#x200B;頁面，其中包含新的 FDA 連接器。[顯示全文](../../installation/using/capability-matrix.md)。

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

已進一步加強「互動」文件，包含多個影片的連結，以協助您進一步了解如何管理優惠方案。[顯示全文](../../interaction/using/interaction-and-offer-management.md)

關於如何最佳化執行個體上執行的查詢的最佳實務文章，已整合至文件。[顯示全文](../../workflow/using/query.md#optimizing-queries)

更新並重新組織報告指南。[顯示全文](../../reporting/using/about-adobe-campaign-reporting-tools.md)

新增如何在工作流程使用執行個體變數的範例。[顯示全文](../../workflow/using/javascript-scripts-and-templates.md)

+++
