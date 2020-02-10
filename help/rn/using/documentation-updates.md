---
title: Adobe Campaign Classic檔案更新
description: 本頁列出每個Adobe Campaign Classic版本的所有新功能和檔案更新。
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
source-git-commit: 5f7f59e2341d7b68b8b28869efc5bfb04cd5ba14

---


# 文檔更新{#documentation-updates}

瞭解Adobe Campaign Classic檔案的所有最新更新。

本頁列出每個Adobe Campaign Classic版本的所有新功能和檔案更新。

您也可以參閱 [Adobe Campaign Classic發行說明](../../rn/using/latest-release.md)。

## 2020年1月 {#january-2020}

「傳送性」區段已透過更新的內容進行移動、重新組織和增強。 [閱讀更多資訊](../../delivery/using/about-deliverability.md)

現在提供新章節，說明Adobe Campaign Classic資料模型基本概念以及如何存取每個表格的說明。 [閱讀更多資訊](../../configuration/using/about-data-model.md)

Adobe Campaign Enhanced MTA文章已更新，其中包含在例項上安裝特定印刷樣式套件的詳細資訊，這些例項不會新增必要的「增強MTA」標題至每則訊息。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html#impacts)

與查詢設計相關的使用案例已重新組織為個別區段。 [閱讀更多資訊](../../workflow/using/querying-recipient-table.md)

現在提供有關管理選件和使用Adobe Campaign Classic互動模組的秘訣與訣竅的新章節。 [閱讀更多資訊](../../interaction/using/interaction-best-practices.md#tips-managing-offers)

「互動」檔案已包含多個影片的連結，可協助您進一步瞭解如何管理選件。 [閱讀更多資訊](../../interaction/using/interaction-and-offer-management.md)

有關如何最佳化執行在例項上執行之查詢的最佳範例文章已整合在檔案中。 [閱讀更多資訊](../../workflow/using/query.md#optimizing-queries)

報告指南已更新並重新整理。 [閱讀更多資訊](../../reporting/using/about-adobe-campaign-reporting-tools.md)

新增了如何在工作流程中使用例項變數的範例。 [閱讀更多資訊](../../workflow/using/javascript-scripts-and-templates.md)

## 2019年12月 {#december-2019}

「WdbcOptions_TempDbName」選項已新增至促銷活動選項清單。 [閱讀更多資訊](../../installation/using/configuring-campaign-options.md)

FDA矩陣頁面已移至此 [處](/help/rn/using/assets/fda_rdbms_rights.pdf)。

「存取權限矩陣」頁面已移至 [此處](https://docs.adobe.com/content/help/en/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)。

說明如何使用AMP定義互動式內容的章節已移除。 [閱讀更多資訊](../../delivery/using/defining-interactive-content.md)

## 19.2 - 02/12/2019{#release-19-2}

**發行中包含的新功能**

加州消費者隱私法(CCPA)-詳 [細內容](https://helpx.adobe.com/campaign/kb/acc-privacy.html)

使用AMP的互動式內容——閱 [讀更多](../../delivery/using/defining-interactive-content.md)

工作流程即時監控——詳 [細內容](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

安全的SMS訊息(TLS)-閱讀 [更多資訊](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

**此版本隨附的其他檔案更新**

Adobe Campaign Enhanced MTA檔案現已推出。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html)

已新增一節，說明如何疑難排解促銷活動中「盡快開始」狀態的工作流程。 閱[讀更多](../../production/using/workflow-execution.md#start-as-soon-as-possible-in-campaigns)

新的「NmsOperation_DeliveryPreparationWindow」和「WdbcKillSessionPolicy」選項已新增至「促銷活動」選項清單。 [閱讀更多資訊](../../installation/using/configuring-campaign-options.md)

現在提供描述Adobe Campaign Classic資料模型基礎的新檔案。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/acc-datamodel.html)

傳送屬 **性中新的「最大個人化執行時間** 」選項會記錄在本 [節中](../../delivery/using/personalization-fields.md#timing-out-personalization)。

已更新使用 **HttpServletRequest** with logon()和query()的API呼叫範例。 [閱讀更多資訊](../../configuration/using/web-service-calls.md)。

在模式定 **義中添加了sqlDefault** 屬性的建議。 [閱讀更多資訊](../../configuration/using/elements-and-attributes.md#attribute-description)。

Adobe Campaign與Adobe即時客戶資料平台的整合現在已在「與Adobe Experience cloud整合」 **指南中提及** 。 [閱讀更多資訊](../../integrations/using/about-campaign-integrations.md)。

## 2019年11月 {#november-2019}

Multiplesing the mid-sourcing [server and](../../installation/using/mid-sourcing-server.md#multiplexing-the-mid-sourcing-server) Supporting forse control instances [](../../message-center/using/transactional-messaging-architecture.md#supporting-several-control-instances) sections adde to the these deployments are not supported for fully hosted and hybrid clients.

已新增新區段，說明如何強制傳送電子郵件時使用字元編碼。 [閱讀更多資訊](../../delivery/using/sending-messages.md#character-encoding)

「存取管理」區段已更新為「隱 **私資料」權限**。 [閱讀更多資訊](../../platform/using/access-management.md#named-rights)

已新增資訊，以指定個人化欄位內容不能超過1024個字元。 [閱讀更多資訊](../../delivery/using/personalization-fields.md)

控制面板文檔已整合到新的協作文檔集中。 [閱讀更多資訊](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

已更新「傳送最佳實務」快速入門手冊。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

## 2019年10月 {#october-2019}

「促銷活動標準」和「促銷活動經典」的錯誤訊息清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

GDPR快速入門手冊已經過改進並充實。 它現在是包含GDPR和CCPA的隱私權管理檔案。 [閱讀更多資訊](https://helpx.adobe.com/content/help/en/campaign/kb/campaign-privacy.html)

已新增一個疑難排解頁面，以便在Campaign Classic中追蹤。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/classic-tracking-troubleshooting.html)。

已新增Adobe Analytics Data Connector的最佳實務新頁面。 [閱讀更多有關Adobe Analytics Data Connector的資訊](../../platform/using/adobe-analytics-data-connector.md)

「傳送最佳實務」快速入門手冊已移動並更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/delivery-best-practices.html)

已在SMS頻道檔案中新增建議，以避免在使用多個外部帳戶時使用具有相同提供者帳戶的延伸通用SMPP連接器時發生問題。 [閱讀更多資訊](../../delivery/using/sms-channel.md#automatic-reply)

已在「排程器」活動文檔中添加有關如何防止同時執行工作流的資訊。 [閱讀更多資訊](../../workflow/using/scheduler.md)

已將配置內部部署安裝收件箱轉換的步驟添加到文檔中。 [閱讀更多資訊](../../delivery/using/inbox-rendering.md#activating-inbox-rendering)

## 2019年9月 {#september-2019}

已新增新頁面，以提供維護Campaign Classic的一般准則。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/acc-maintenance.html)

與工作流程監控相關的資訊已集中在新的專屬區段中。 [閱讀更多資訊](../../workflow/using/monitoring-workflow-execution.md)。

已新增有關Adobe Campaign Classic中追蹤一般准則的新頁面。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/acc-tracking.html)。

已更新改善工作流程和傳送效能的最佳實務。 [閱讀更多有關工作流程](../../workflow/using/workflow-best-practices.md) ，以 [及更多有關傳送的資訊](../../delivery/using/monitoring-a-delivery.md#best-practices-performance)。

## 19.1 - 30/05/2019{#release-19-1}

**發行中包含的新功能**

控制面板——閱 [讀更多](https://docs.adobe.com/content/help/en/control-panel/using/control-panel-home.html)

稽核記錄——詳 [細資訊](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Audit_trail.html)

**此版本隨附的其他檔案更新**

已建立新的「建置」升級常見問答集。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/build-upgrade-faq.html)

已 [更新Compatibility](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html) matrix。 支援的資料庫系統清單已更新，以及Android/iOS版本和相關SDK。 已 [歸檔19.0相容性表](https://helpx.adobe.com/campaign/kb/compatibility-matrix-19-0.html) 。

「已過時和已移除的Campaign Classic功能」頁面已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

伺服器配置檔案的說明已添加到《安裝指南》中。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_The_server_configuration_file.html)

已新增一節，說明代管和混合機型的安裝與設定步驟。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Hybrid_and_Hosted_models_Introduction.html)

已新增一節，說明Campaign伺服器解除安裝步驟。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Uninstalling_Campaign.html)

安全 [性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、 [傳遞性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 和 [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html) GDPR快速入門手冊已更新。

已更新前處理工作流程選項的說明，以反映產品變更。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Data_loading__file_)

Marketing cloud觸發器技術已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

錯誤消息清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

已新增有關交易傳訊的SOAP驗證方法的詳細資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Event_description.html)

Apache配置步驟已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Integration_into_a_Web_server.html#Configuring_Apache_web_server_in_RHEL)

已新增新頁面，包括Campaign Standard和Classic的端點清單。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/campaign-endpoints.html)

資料套件最佳實務文章已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/data-package-best-practices.html)

「管理選件」檔案已更新，並新增了列出最佳實務的新章節。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITA_Interaction_Overview_Interaction_best_practices.html)

已建立新的知識庫文章，說明如何在Adobe Campaign Classic中使用選件目錄。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/offer-best-practices.html)

「子工作流程」活動區段已增強，並提供使用範例。 [閱讀更多資訊](../../workflow/using/sub-workflow.md)

Campaign [](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html) Classic內部部署與托管功能表知識庫文章已更新，其中包含與封存電子郵件相關的資訊。

Transactional Messaging文檔已更新，其中包含有關模板發佈的說明。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/MCE_Template_publication.html)

「未處理的彈回郵件」區段已更新，其中包含「轉送位址」和「錯誤位址」欄位的詳細資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Deploying_an_instance.html#Unprocessed_bounce_mails)

新增了有關工作流程規劃最佳實務的新章節。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Workflow_best_practices.html#Execution_and_performance)

在促銷活動選項清單中新增兩個選項：XtkSecurity_Restrict_EditXML和NmsOperation_OperationMgtDebug。
[閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

已新增有關Campaign Classic中可用之不同外部帳戶的資訊，以及如何設定這些帳戶。
[閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html)

更新「Analytics資料連接器」區段以反映介面變更。
[閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

已新增有關帳單報表的資訊。
[閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Billing_report)

已更新「共用觀眾」整合的檔案。
[閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

下列技術已更新： [SMS連接器通訊協定與設定](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html) , [以及序列自動產生](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)。

「技術工作流程」區段已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

「促銷活動網域名稱設定」程式已經過改良和更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/domain-name-delegation.html)

Android應用程式從Google雲端傳訊(GCM)移轉至Firebase雲端傳訊(FCM)的程式已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/migrate-to-fcm.html)

促銷活動硬體調整指南已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/hardware-sizing-guide.html)

已在Teradata外部帳戶的「查詢分段」中新增資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_External_accounts.html#External_database_external_account)

## 2019年1月{#release-doc-16-01-2019}

Marketing cloud觸發器技術已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

已在選件核准區段中新增附註，以指定「已核准內容」提及表示內容核准程式已完成，不論所有選件皆已啟用／核准。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITA_Managing_an_offer_catalog_Approving_and_activating_an_offer.html#Approving_offer_content)

「安裝指南」中新增了一個章節，列出「管理／平台／選項」節點中的選項。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Appendices_Configuring_Campaign_options.html)

已新增有關使用種子地址保護郵件清單的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

建立和傳送傳送時的主要步驟已重新分組為新區段，並會視需要參考各種管道。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Key_steps_when_creating_a_delivery.html)

「電 [子郵件封存](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) 」區段已移動、重新整理並改良，其資訊已明確：

* 已新增有關每次連線電子郵件和密件副本傳送IP參數的最佳實務。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Best_practices)

* 如果您已使用舊版電子郵件封存（在Adobe Campaign 17.2之前——組建版本8795），我們已更新升級至新電子郵件封存系統(BCC)的步驟。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

「使用工作流自動化」指南中已新增使用案例：傳送個人化警報給營運商。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_personalized_alerts_to_operators.html)

「移轉至新版本」區段已更新。 本檔案現在只詳細說明從任何舊版移轉至Adobe Campaign Classic v7的步驟，因為無法再移轉至Adobe Campaign v6.11。閱 [讀更多](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

「傳送暫時失敗後重試」區段已釐清。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Retries_after_a_delivery_temporary_failure)

「數位內容編輯器」區段的連結已新增至「定義電子郵件內容」區段。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Message_content)

「事務性消息傳遞體系結構」部分已更新，並出現警告，指定不能將控制項和執行實例安裝在同一台電腦上。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/MCE_Introduction_Transactional_messaging_architecture.html)

「工作流程監控」區段已更新，其中包含8700到8977(18.10)之間之建置的附註，包括如何為這些建置安裝Workflow HeatMap套件的技術連結。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#About_the_Workflow_HeatMap)

已新增如何使用工作流程中的「擴充」活動，傳送包含自訂資料欄位的電子郵件的使用案例。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Email_enrichment_with_custom_date_fields.html)

功能影片已移至此 [處](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/overview.html)。

在 [Teradata](https://helpx.adobe.com/campaign/kb/campaign_fda_teradata.html) 和 [MySQL 5.7上新增了兩項技術](https://helpx.adobe.com/campaign/kb/campaign_fda_mysql.html)。

## 18.10 - 05/11/2018{#release-18-10}

**發行中包含的新功能**

推播通知改進——閱 [讀更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Integrating_the_SDK_into_the_mobile_application)

SQL資料管理活動——詳 [細內容](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#SQL_Data_Management)

工作流程監控- [閱讀更多](https://docs.campaign.adobe.com/doc/AC/en/PRO_Production_procedures_Monitoring_processes.html#Workflow_monitoring)

**此版本隨附的其他檔案更新**

Campaign Classic API現在可在專用頁 [面中使用](https://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。 如果您使用jsapi.chm檔案，現在應參考新的線上版本。

已更新相容性矩陣。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

「已過時和已移除的Campaign Classic功能」頁面已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

在發行 [說明](https://docs.campaign.adobe.com/doc/AC/en/RN.html)[和舊版發行說明中](http://docs.campaign.adobe.com/doc/AC/en/RN_legacy.html)，已針對已回調的建置新增警告。 還添加了17.9、18.4和18.6的累積版本。

安全 [性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)、 [可傳遞性](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) ，以及建 [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html) 置升級入門指南已更新。

GDPR [](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html) 快速入門手冊已更新，其中包含如何從外部叫用API以及如何使用queryDef來查詢狀態及下載GDPR檔案的資訊。

已新增交易式訊息使用案例，以即時新增電子郵件附件至出站派單。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/MCE_Use_case_Purpose.html)

已更新連線臨界值疑難排解區段。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Connection_thresholds.html)

已新增一節，說明如何設定代理連線。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Proxy_connection_configuration)

更新授權外部命令限制一節。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Restricting_authorized_external_commands)

已新增與SFTP使用相關的疑難排解區段。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

「傳送訊息」指南的概述區段已重新整理。 已新增有關傳送建立全域程式和不同傳送類型的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_About_deliveries_and_channels_Communication_channels.html)

錯誤消息清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

已將有關如何使用種子地址的部分移至「發送消息」指南概述章節。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Using_seed_addresses_About_seed_addresses.html)

新增工作流程使用案例：管理伴隨工作流程執行的更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Coordinating_data_updates.html)

「收件匣轉換」區段已更新，其中包含更多有關Litmus的資訊，以及更詳細的程式。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html#Multiplexing_the_mid-sourcing_server)

「SpamAssassin」區段已改善。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_SpamAssassin.html)

「使用壓力規則管理行銷疲勞」區段已新增使用案例。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/CMP_Campaign_Optimization_Pressure_rules.html#Sending_only_the_highest-weighted_messages)

現在提供新的使用案例，說明如何建立跨通道傳送工作流程。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Cross-channel_delivery_workflow.html)

在「封存電子郵件」區段中新增了一些建議。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_deliverability.html#Activating_emails_BCC_archiving)

已新增建議，說明Adobe Campaign最佳使用的最低螢幕解析度。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Screen_resolution)

Experience manager整合指南已更新，此整合的設定已新增一些說明。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Adobe_Experience_Manager_About_Adobe_Experience_Manager.html)

已新增群組類型清單和清單類型清單之間差異的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_Creating_and_managing_lists.html#About_lists_in_Adobe_Campaign)

更新程式碼，以透過電子郵件傳送報表擷取作為附件。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Sending_a_report_to_a_list.html#Step_3-_Creating_the_workflow)

已新增如何建立查詢的範例，以篩選在過去7天內未開啟電子郵件的收件者。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Recipients_who_did_not_open_any_delivery)

已更新「使用Adobe Experience cloud整合指南分享觀眾」。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Sharing_audiences_with_Adobe_Experience_Cloud.html)

「常見問題」說明頁面現在包含有關Campaign可用語言、網頁表單翻譯和多語言電子郵件的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Common_questions.html)

美國英文與英國英文例項之間的差異現在會列在專屬區段中。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Adobe_Campaign_workspace.html#Formats_and_units)

「常 [見問題](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Common_questions.html) 」說明頁面現在會連結至錯誤訊息頁面。

已新增「開啟」追蹤模式的相關資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_Personalizing_URL_tracking.html)

新增有關網頁應用程式和網頁表單最低解析度的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_About_web_forms.html)

Campaign和Adobe Experience cloud解決方案整合指南已更新並重新組織。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Campaign_integrations_About_Campaign_integrations.html)

已新增有關網頁表單中文字變數使用的章節。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WEB_Web_forms_Static_elements_in_a_web_form.html#Using_text_variables)

訊息中的URL追蹤模式現在已詳細說明。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Tracking_messages_How_to_configure_tracked_links.html)

例項建立區段已重新組織。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Creating_an_instance_and_logging_on.html)

在日文行動裝置上傳送電子郵件，現在會記錄在新章節中。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Defining_the_email_content.html#Sending_emails_on_Japanese_mobiles)

「最佳化個人化」區段已更新，並提供更多資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_fields.html#Optimizing_personalization)

## 18.6 - 09/07/2018{#release-18-6}

**發行中包含的新功能**

已更新相容性矩陣。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

JSAPI檔案已更新。 [閱讀更多資訊](https://support.neolane.net/webApp/extranetLogin)

「已過時和已移除的功能」頁面已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

**此版本隨附的其他檔案更新**

Campaign Classic使用手冊已重新命名，以簡化導覽、改善使用體驗、存取資訊和自助服務。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/browseAC.html)

運算式編輯器中可用的函式清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Creating_queries_Defining_filter_conditions.html#List_of_functions)

安全性快速入門手冊已更新，其中包含如何保護包含PI之頁面的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

錯誤消息清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

IMS整合檔案中已新增疑難排解區段。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Connecting_via_an_Adobe_ID_IMS_troubleshooting.html)

已更新「建置升級快速入門」指南。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)

IP相似性設定區段已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Mid-sourcing_server.html#Multiplexing_the_mid-sourcing_server)

已添加「效能和吞吐量」故障排除部分。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PRO_Troubleshooting_Performance_and_throughput_issues.html)

內建個人化區塊清單已更新為範例。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html#Out-of-the-box_personalization_blocks)

已更新傳送失敗原因清單。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_delivery_failures.html#Delivery_failure_types_and_reasons)

新增了「套件定義管理」的章節。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Administration_basics_Working_with_data_packages.html#Managing_package_definitions)

「促銷活動」與Adobe Analytics -「資料」連接器區段的整合已經過改良並重新組織。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Adobe_Analytics_Data_Connector.html)

已新增「教學課程」區段，其中包含逐步指南和教學影片的連結。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

SMS連接器通訊協定與設定的新技術已經建立。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/sms-connector-protocol-and-settings.html)

已更新「傳送最佳實務快速入門」指南。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

已更新Microsoft Dynamics 365帳戶設定及Web API部署。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

在Windows平台上安裝Adobe Campaign Classic的程式已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Windows__Installing_the_server.html)

Adobe Experience cloud和Campaign Classic之間的受眾分享時間範圍已詳細說明。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Importing_and_exporting_audiences.html)

已更新Campaign Classic清單的知識庫文章完整版。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/article-list.html)

有關效能改進和最佳實務的新技術已上線。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/best-practices-for-performance-improvement.html)

A/B測試範例已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

Campaign Classic常見問題／常見問答集頁面已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Common_questions.html)

## 18.4 - 24/04/2018{#release-18-4}

**發行中包含的新功能**

歐盟通用資料保護規則(GDPR)-詳 [細內容](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/ACC_GDPR.html)

作用中描述檔- [閱讀更多](https://docs.campaign.adobe.com/doc/AC/en/PTF_Profile_management_About_profiles.html#Active_profiles)

Android推播連接器增強功能——詳 [細資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Android_connectors)

**此版本隨附的其他檔案更新**

版本注意事項已經過改良，提供更佳的使用者體驗，現在包含所有與客戶要求相關的修補程式。  [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/RN.html)

新增了一個頁面，其中包含有關Campaign Classic的最常見問題。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Common_questions.html)

錯誤消息清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing cloud觸發器技術已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

有關如何在舊版Campaign Classic上安裝和部署隱私權(GDPR)套件的技術已經加入。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/how-to-install-gdpr-package-on-legacy-versions.html)

對新型序列自動生成機制進行了研究。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/sequence_auto_generation.html)

已更新JSAPI檔案。 [閱讀更多資訊](https://support.neolane.net/webApp/extranetLogin)

已更新相容性矩陣。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

現在有新頁面列出已過時的功能和版本。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/deprecated-and-removed-features.html)

已添加一些有關RDBMS的已知限制和最佳做法。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/en/INS_Prerequisites_and_recommendations__Database.html)

瞭解有關SFTP使用的最佳實務。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Importing_and_exporting_data_SFTP_server_usage.html)

技術工作流程清單已更新。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_About_technical_workflows.html)

知識庫文章清單（先前稱為「技術人員」）現在可從這裡取得。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/article-list.html)

已 [更新How-to影片](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 。

LINE文檔在LINE包折舊後已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

更新報告指標計算檔案。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/RPT_Accessing_built-in_reports_Reports_on_deliveries.html#Indicator_calculation)

已添加有關與Oracle對齊的時區檔案的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/MIG_Configuration_General_configurations.html#Oracle)

新增「監控傳送」區段，其中包含有關傳送失敗和隔離管理的更新資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

使用現成可用的個人化區塊的新資訊重新組織「個人化區塊」區段。
[閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalization_blocks.html)

使用檔案設定的新資訊重新整理「封存電子郵件」 ```config-<instance name>.xml``` 區段。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Activating_email_archiving__on_premise_)

更新訊息中心（控制項）技術工作流程的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Technical_workflows_Message_Center__Control_.html)

已添加有關設定SMTP中繼時吞吐量限制的資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html#Personalizing_delivery_parameters)

## 17.12 - 14/12/2017{#release-doc-14-12-2017}

Adobe [Campaign Classic檔案集已重新整理](https://helpx.adobe.com/support/campaign/classic.html) ，以改善可用性。

已新增「教學課程」區段，以方便存取核心的Campaign功能說明教材、操作說明、範例和影片。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Starting_with_Adobe_Campaign_Tutorials.html)

已新增一個章節，協助您監控傳送狀態，但也可能發生錯誤，並瞭解如何修正錯誤。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Monitoring_a_delivery.html)

錯誤消息清單已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/error_messages/error_codes.html)

Marketing cloud觸發器技術已更新。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

Campaign Classic移轉指南已新增至系列。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/MIG_Migration_overview_About_migration.html)

已更新促銷活動相容性矩陣。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

如果適用，設定和安裝指示現在會提及它們套用的代管模型。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Configuring_Campaign_server.html)

新的知識庫文章，強調內部部署、混合部署和受管理服務之間的配置和功能差異。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/acc-on-prem-vs-hosted.html)

已新增如何安裝標準套件的指示。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Initial_configuration_Installing_packages.html)

已新增有關如何設定與Audience manager或People核心服務整合的詳細資訊。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/ITG_Audience_sharing_Configuring_shared_audiences_integration_in_Adobe_Campaign.html)

已更新安裝檔案，提到使用PostreSQL時，促銷活動安裝現在需要pgcrypto。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Installing_Campaign_in_Linux__Prerequisites.html#Database_access_layers)

## 17.9 - 25/09/2017{#release-17-9}

**發行中包含的新功能**

ACS連接器增強功能

SAP HANA連接器——詳 [細內容](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#SAP_HANA)

通過HiveSQL的Hadoop Connector —— 詳 [細內容](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_Accessing_an_external_database.html#Hadoop)

線路頻道：訊息增強功能- [閱讀更多](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_LINE_channel.html)

**此版本隨附的其他檔案更新**

新增查詢範例。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_Designing_queries.html#Filtering_duplicated_recipients)

已更新傳送最佳實務指南。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

A/B測試範例已更新，但遺失指示。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Use_cases_A-B_testing.html)

操作說明影片已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

更新電子郵件封存區段。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html)

釐清工作流程中的排程器使用情形。 [閱讀更多資訊](../../workflow/using/scheduler.md)

新增暫停的工作流程最佳實務。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)

在匯入檔案時預先處理檔案的新程式，在匯出工作流程中的資料時進行後處理。 請 [在這裡](http://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)。

SMS訊息檔案的隔離機制已更新，以反映Extended一般SMPP連接器錯誤管理的特定性。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)。

「行動應用程式頻道」檔案已增強，並提供在Android上傳送豐富式通知的詳細程式。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_push_notifications_Setting_up_mobile_app_channel.html#Rich_notifications)。

「收件箱」呈現文檔已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Inbox_rendering.html)。

「設定網頁追蹤」檔案已增強，並提供更新的範例和附註。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/CFG_Setting_up_web_tracking_Additional_parameters.html#Redirection_server_configuration)。

SMS頻道檔案已更新，在套用至延伸通用SMPP連接器的「自動回覆」區段中增加了一些說明。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_messages_on_mobiles_SMS_channel.html#Creating_an_SMPP_external_account)。

Social行銷檔案已更新。 [閱讀更多資訊](../../social/using/about-social-marketing.md)。

IP變暖的新技術已經增加。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_Deliverability_IP_Warming_overview.pdf)。

已新增建置升級入門。 [閱讀更多資訊](http://docs.campaign.adobe.com/doc/AC/getting_started/EN/buildUpgrade.html)。

## 2017年5月{#release-doc-30-05-2017}

有新的快速入門手冊可供使用：它提供一些最佳實務，可用於透過Adobe Campaign傳遞，從建立和鎖定到傳送和監控。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)

安全性快速入門手冊已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/security.html)

「封 [存電子郵件」檔案](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html) 「已更新為 [「電子郵件密件副本」區段](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Configuring_the_BCC_email_address__on_premise_) ，以及啟動 [功能的詳細步驟](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Archiving_emails)。

已新增和更新部分影片。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html)

瞭解如何將傳送內容傳送給從外部檔案載入的收件者，而不需更新資料庫。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Identifying_target_populations.html#Selecting_external_recipients)

已更新雙重選擇加入範例。 [閱讀更多資訊](../../web/using/use-cases--web-forms.md)

## 2017年3月{#release-doc-31-03-2017}

可傳遞性：開始 [使用指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) ，已更新。 可傳送性檔案現在包含更詳細 [的概述](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_About_deliverability.html) ，以及實作 [程式和主要步驟的說明](https://docs.campaign.adobe.com/doc/AC/en/DLV_Deliverability_management_Implementation.html)。

「使用波傳送」區段已移動並增強，其中包含詳細的範例、建議和使用案例。    [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Sending_emails_Sending_messages.html#Sending_using_multiple_waves)

「隔離管理」部分已添加了一個表，說明SMS消息的特定錯誤。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Monitoring_deliveries_Understanding_quarantine_management.html#SMS_quarantines)

工作流程：已新增多頻道工作流程範例。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Action_activities.html#Cross-channel_deliveries)

Marketing cloud觸發器：已新增有關如何設定及搭配Adobe Campaign使用的技術。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/triggers-and-campaign.html)

工作流程手冊已重新整理和擴充。 輕鬆瞭解如何建立並執行工作流程 [、如何](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Building_a_workflow.html) 建立並管理您的 [](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Executing_a_workflow.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Targeting_data.html#Data_Management)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Updating_the_database)[](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow)Target Deliverations、資料匯入ImportData、資料使用方式以及資料使用方式的Adobe ReduptageThergDeliversDeliverationsDightPremizations。

現在提供匯 [入最佳實務](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_How_to_use_workflow_data.html#Delivering_via_a_workflow) 後建立的 [匯入工作流程範例](https://docs.campaign.adobe.com/doc/AC/en/WKF__General_operation_Importing_data.html#Import_best_practices) 。
此新版本的安裝指南已更新。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/INS_Architecture_and_hosting_models_General_architecture.html)

已更新相容性矩陣。 [閱讀更多資訊](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html)

收件者會在電子郵件傳送中加入抵用券時獲得附加值。 [閱讀更多資訊](https://docs.campaign.adobe.com/doc/AC/en/DLV_Personalizing_deliveries_Personalized_coupons.html)

## Adobe Campaign v7 - 16/03/2017{#release-17-2}

**發行中包含的新功能**

ACS連接器

適用於Microsoft Dynamics的網頁API —— 詳 [細資訊](https://docs.campaign.adobe.com/doc/AC/en/PTF_Connectors_CRM_Connectors.html#Example_for_Microsoft_Dynamics)

電子郵件封存BCC方法——詳 [細內容](https://docs.campaign.adobe.com/doc/AC/en/INS_Additional_configurations_Email_archiving.html#Updated_email_archiving_system__BCC_)

Amazon Simple Storage Service(S3)連接器——詳 [細內容](https://docs.campaign.adobe.com/doc/AC/en/WKF_Repository_of_activities_Event_activities.html#File_transfer)

