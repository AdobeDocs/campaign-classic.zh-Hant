---
title: Adobe Campaign Classic 文件更新
description: 本頁列出每個Adobe Campaign Classic版本的所有新功能和檔案更新
page-status-flag: never-activated
uuid: 269d590c-5a6d-40b9-a879-02f5033863fc
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: rns
content-type: reference
topic-tags: latest-documentation-updates
discoiquuid: 5df34f55-135a-4ea8-afc2-f9427ce5ae7b
translation-type: tm+mt
source-git-commit: ebec481d5a018d06e47c782627e9a9064cb0dd64
workflow-type: tm+mt
source-wordcount: '3588'
ht-degree: 95%

---


# 文件更新{#documentation-updates}

此頁面按月及按各個 Campaign 版本列出所有新功能及文件更新。

您也可以參閱 [Adobe Campaign Classic 發行說明](../../rn/using/latest-release.md) ，以瞭解更多更新詳情。

## 2020 年11月 {#nov-2020}

促銷活動資料模型概觀已改進並重新組織。 [顯示全文](../../configuration/using/about-data-model.md)。

外部帳戶配置已移至 [此區段](../../installation/using/external-accounts.md)。

Campaign Federated Data Access(FDA)檔案已經過改良，並包含每個外部資料庫組態的詳細資訊，並移至 [本節](../../installation/using/about-fda.md)。

[Campaign 20.2.3版已移至](../../rn/using/release--20-2.md#release-20-2-3-build-9182) 「一般可用性(GA)」。

「隱私權」區段已移動，並包含兩個新頁面： [隱私權管理](../../platform/using/privacy-management.md) , [以及管理隱私權要求](../../platform/using/privacy-requests.md)。

在中間來源補充伺服器設定頁面中已新增附註，以指定在伺服器設定後，不應更新外部帳戶的內部名稱。 [顯示全文](../../installation/using/mid-sourcing-server.md)

已在語法上新增資訊，以在指定外部SFTP伺服器的路徑時使用。 [顯示全文](../../platform/using/sftp-server-usage.md#external-SFTP-server)

## 2020 年 10 月 {#oct-2020}

**第 20.3 發行版本包含的新功能**

iOS 的推播通知改善 - [閱讀更多資訊](../../delivery/using/configuring-the-mobile-application.md)

Android 的推播通知改善 - [閱讀更多資訊](../../delivery/using/configuring-the-mobile-application-android.md)

**此版本隨附的其他文件更新**

更新相容性矩陣。[顯示全文](../../rn/using/compatibility-matrix.md)

更新「已棄用和已移除的功能」頁面。[顯示全文](../../rn/using/deprecated-features.md)

專屬區段現在提供了 Gold Standard 發行版本的發行說明和相容性矩陣。
[顯示全文](../../rn/using/gold-standard.md#gs-10)。

Triggers integration originally based on oAUTH authentication setup to access pipeline has now been changed and moved to Adobe I/O. [Read more](../../integrations/using/configuring-adobe-io.md)

**其他更新**

已更新文件頁面，以反映 Tomcat 8 更新。

已將詳細資訊新增至「取得 Adobe Campaign 版本」區段的「關於」方塊說明中。[顯示全文](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)

已將執行建置升級的准則新增至「更新 Adobe Campaign Classic」區段。閱讀更多資訊[閱讀更多資訊](../../production/using/build-upgrade.md)

已將有關 Campaign 版本編號升級的常見問答集新增至 Campaign 常見問題。閱讀更多資訊[閱讀更多資訊](../../platform/using/faq-build-upgrade.md)

已在專用區段中，說明 Campaign 內部部署、託管和混合託管模型。[顯示全文](../../installation/using/hosting-models.md)

已在安裝指南中，更新並移動 Campaign 功能矩陣的每個託管模型。[顯示全文](../../installation/using/capability-matrix.md)

已改善「Campaign 報告」進階功能區段，以詳細說明如何在自訂報告中使用 URL 參數和變數。[顯示全文](../../reporting/using/advanced-functionalities.md)

已重新整理報告屬性頁面並加以擴充，以方便配置。[顯示全文](../../reporting/using/properties-of-the-report.md)

已建立新的技術，其詳細說明了如何從舊的二進位通訊協定移轉至以 HTTP/2 為基礎的 APN 提供程式 API。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/migrate-to-apns-http2.html)

## 2020 年 9 月{#september-2020}

已新增附註，以指明「主要」用戶檔案計數僅適用於「行銷」執行個體。[顯示全文](../../platform/using/about-profiles.md#active-profiles)

已新增有關方案版本的新範例，以將欄位連結至現有的參考表。[顯示全文](../../configuration/using/examples-of-schemas-edition.md#uc-link)

已新增附註，說明如何在傳遞種子地址時使用其他資料。[顯示全文](../../delivery/using/creating-seed-addresses.md#defining-addresses)

## 2020 年 8 月{#aug-2020}

在專屬區段中，瞭解與傳遞設計以及與 Campaign 一同傳送相關的最佳實務。[顯示全文](../../delivery/using/delivery-best-practices.md)

已改善「傳遞」最佳實務登陸頁面，以方便存取子區段。[顯示全文](../../delivery/using/deliverability-key-points.md)

現在已提供有關下列主題的教學影片：

* [如何使用類型規則和預先定義的篩選器來設定疲勞管理](../../campaign/using/about-campaign-typologies.md)

* [如何在行銷活動中建立電子郵件](../../campaign/using/marketing-campaign-deliveries.md)

* [如何建立具有條件內容的多語言電子報](../../delivery/using/conditional-content.md)

* [如何配置和部署傳遞範本](../../delivery/using/creating-a-delivery-template.md)

* [如何啟用和使用電子郵件 AMP](../../delivery/using/defining-interactive-content.md)

* [使用動態內容區塊個人化電子郵件](../../delivery/using/personalization-blocks.md)

* [如何使用個人化欄位進行電子郵件個人化](../../delivery/using/personalization-fields.md)

* [如何管理電子郵件中的種子和校樣](../../delivery/using/steps-defining-the-target-population.md)

* [如何設定循環傳遞](../../workflow/using/recurring-delivery.md)

* [如何設定連續傳遞](../../workflow/using/continuous-delivery.md)

在連線至 FTP 伺服器且收到「無法解決主機名稱」錯誤後，已將資訊新增至要執行的檢查和動作中。[顯示全文](../../platform/using/sftp-server-usage.md)

已參考[工作流程使用案例](../../workflow/using/about-workflow-use-cases.md)清單的新使用案例：

* 自動建立、編輯和發佈內容
* 在傳送傳遞前，設定收件者核准程序
* 調用查詢中的執行個體變數
* 將分割百分比套用在人口上

已新增其他使用資訊與變數使用附註以豐富本&#x200B;**[!UICONTROL AND-join]**&#x200B;活動區段內容。[顯示全文](../../workflow/using/and-join.md)

## 2020 年 7 月{#july-2020}

已將有關如何使用增量查詢以自動更新清單的使用案例新增至工作流使用案例中。[顯示全文](../../workflow/using/about-workflow-use-cases.md)

已重新整理[發行說明](../../rn/using/latest-release.md)：已新增[概述頁面](../../rn/using/latest-release.md)，其中包含有關建置狀態、升級流程、建議和重要連結資訊。此外，也同樣新增 [Gold Standard 發行版本](../../rn/using/gold-standard.md)專用頁面，並整合[相容性矩陣](../../rn/using/compatibility-matrix.md)。

新增了與 Campaign Classic 監視相關的准則。[顯示全文](../../production/using/monitoring-guidelines.md)

已提升「隱私權與同意」一節，其提供更詳細的資訊和有用的連結。[顯示全文](../../platform/using/privacy-and-recommendations.md)。

已更新 Campaign Classic 頁面的「隱私權管理」，其中包含「規範」欄位資訊，當您使用 API 允許設定自動隱私權要求流程時，便可使用此欄位。[顯示全文](https://helpx.adobe.com/ie/campaign/kb/acc-privacy.html#ManagingPrivacyRequests)

「隱私權管理概覽」頁面已更新，其中加入泰國個人資料保護法 (PDPA) 和巴西 Lei Geral de Proteção de Dados (LGPD) 的相關資訊。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/campaign-privacy-overview.html#whatisgdpr)

已將資訊新增至子工作流程記錄和行為中，以防發生錯誤。[顯示全文](../../workflow/using/sub-workflow.md)

已將最佳實務新增至&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動區段。[詳細內容](../../workflow/using/scheduler.md)

## 2020 年 6月 {#june-2020}

更新「移除已隔離的位址」章節，內容包括釐清將位址自動從隔離清單移除的案例。[顯示全文](../../delivery/using/understanding-quarantine-management.md#removing-a-quarantined-address)

新增使用案例，以說明如何使用「控制面板」及「行銷活動工作流程」進行資料[加密](../../workflow/using/how-to-use-workflow-data.md#use-case-gpg-encrypt)與[解密](../../workflow/using/importing-data.md#use-case-gpg-decrypt)。

Experience Cloud Triggers 和 Adobe Campaign Classic 整合頁面已移至[此處](../../integrations/using/about-triggers.md)。

## 2020 年 7 月{#release-20-2}

**第 20.2 發行版本包含的新功能**

支援表情符號——[顯示全文](../../delivery/using/customizing-emoticon-list.md)

Azure Synapse FDA Connector——[顯示全文](../../installation/using/configure-fda-synapse.md)

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

FDA 權限表已移至「存取外部資料庫 (FDA)」文件。[顯示全文](../../installation/using/remote-database-access-rights.md)

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

**第 20.1 發行版本包含的新功能**

Snowflake FDA Connector——[顯示全文](../../installation/using/configure-fda-snowflake.md)

Hadoop FDA Connector 增強功能——[顯示全文](../../installation/using/configure-fda-hadoop.md)

**此版本隨附的其他文件更新**

更新「[安裝](../../installation/using/general-architecture.md)、[生產](../../production/using/foreword.md)及[設定](../../configuration/using/additional-parameters.md)」指南，其中包含 nlserver 服務啟動使用的新系統單元。您仍然可以使用 /etc/init.d/nlserver6，但 Adobe 建議您現在使用 systemctl 命令與 nlserver 服務互動。

更新安裝指南，並與最新版本的相容性矩陣同步。新增了新支援的系統。移除已棄用及不支援的系統的項目。[顯示全文](../../installation/using/general-architecture.md)

更新相容性矩陣，其中包含 Hadoop 3.0 及 Snowflake FDA 連接器。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)

安裝指南新增了有關 IP 相似性的最佳實務。[顯示全文](../../installation/using/email-deliverability.md#list-of-ip-addresses-to-use)

更新「資料庫清理工作流程」章節。提供的批次圖表，現在已反映代碼實作。[顯示全文](../../production/using/database-cleanup-workflow.md)

「交易式傳訊指南」已新增 FDA over HTTP 的限制。[顯示全文](../../production/using/database-cleanup-workflow.md)

針對讓您為 **[!UICONTROL JavaScript code]** 及 **[!UICONTROL Advanced JavaScript code]** 工作流程活動定義逾時期限的新選項，新增相關資訊。[顯示全文](../../workflow/using/sql-code-and-javascript-code.md)

針對 **[!UICONTROL Administration]** > **[!UICONTROL Audit]** > **[!UICONTROL Workflows Status]** 節點提供的新的&#x200B;**[!UICONTROL Start Pending]** 檢視，新增相關資訊。[顯示全文](../../workflow/using/monitoring-workflow-execution.md#filtering-workflows-status)

移動、重新組織並改善「[傳送推播通知](../../delivery/using/about-mobile-app-channel.md)指南」，其中包含已釐清的相關資訊。

[此處](../../reporting/using/properties-of-the-report.md#defining-additional-settings)記錄 URL 報表設定的新參數。

更新 **Campaign Classic 內部部署及託管功能矩陣**&#x200B;頁面，其中包含新的 FDA 連接器。[顯示全文](../../installation/using/capability-matrix.md).

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

「FDA 矩陣」頁面已移至[此處](../../installation/using/remote-database-access-rights.md)。

「存取權限矩陣」頁面已移至[此處](https://docs.adobe.com/content/help/zh-Hant/campaign-classic/using/getting-started/administration-basics/assets/accessrights.pdf)。

移動說明如何定義 AMP 互動式內容的章節。[顯示全文](../../delivery/using/defining-interactive-content.md)

**第 19.2 發行版本包含的新功能**

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

更新 Campaign Standard 及 Campaign Classic 的錯誤訊息清單。[顯示全文](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)

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

**第 19.1 發行版本包含的新功能**

控制面板——[顯示全文](https://docs.adobe.com/content/help/zh-Hant/control-panel/using/control-panel-home.html)

稽核軌跡——[顯示全文](../../production/using/audit-trail.md)

**此版本隨附的其他文件更新**

建立了新的「組建版本升級常見問題集」。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/build-upgrade-faq.html)

更新[相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix.html)。更新了支援的資料庫系統清單，以及支援的 Android/iOS 版本及相關的 SDK。封存[ 19.0 相容性矩陣](https://helpx.adobe.com/tw/campaign/kb/compatibility-matrix-19-0.html)。

更新「已棄用和已移除的 Campaign Classic 功能」頁面。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/deprecated-and-removed-features.html)

《安裝指南》新增伺服器設定檔的說明。[顯示全文](../../installation/using/the-server-configuration-file.md)

新增了新的章節，說明託管及混合模式的安裝及設定步驟。[顯示全文](../../installation/using/hosting-models.md)

新增了新的章節，說明 Campaign 伺服器解除安裝步驟。[顯示全文](../../installation/using/uninstalling-campaign.md)

更新「[安全性](https://helpx.adobe.com/tw/campaign/kb/acc-security.html)、[傳遞能力](../../delivery/using/deliverability-key-points.md)[及隱私權](../../platform/using/privacy-management.md)」快速入門手冊。

更新預先處理工作流程選項的說明，以反映產品變更。[顯示全文](../../workflow/using/data-loading--file-.md)

更新 Marketing Cloud Triggers Technote。[顯示全文](../../integrations/using/about-triggers.md)

更新錯誤消息清單。[顯示全文](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/error_messages/error_codes.html)

新增有關交易式傳訊 SOAP 驗證方法的詳細資訊。[顯示全文](../../message-center/using/event-description.md)

更新 Apache 設定步驟已更新。[顯示全文](../../installation/using/integration-into-a-web-server-for-linux.md)

新增了包含 Campaign Standard 和 Classic 的端點清單頁面。[顯示全文](../../installation/using/campaign-network-endpoints.md)

更新「資料套件最佳實務」文章。[顯示全文](../../configuration/using/data-model-best-practices.md)

更新「管理優惠方案」文件，新增了列出最佳實務的新章節。[顯示全文](../../interaction/using/interaction-best-practices.md)

建立了新的知識庫文章，說明如何在 Adobe Campaign Classic 使用優惠方案目錄。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/offer-best-practices.html)

加強「子工作流程活動」章節，並提供使用範例。[顯示全文](../../workflow/using/sub-workflow.md)

已更新[Campaign Classic 內部部署與托管功能矩陣](../../installation/using/capability-matrix.md)頁面，其中包含與電子郵件密件副本相關的資訊。

更新了交易式傳訊文件，其中包含關於範本發佈的說明。[顯示全文](../../message-center/using/template-publication.md)

更新「未處理的退回郵件」章節，其中包含「轉寄地址」和「錯誤地址」欄位的詳細資訊。[顯示全文](../../installation/using/deploying-an-instance.md)

新增了關於工作流程規劃最佳實務的新章節。[顯示全文](../../workflow/using/workflow-best-practices.md)

Campaign 選項清單新增了兩個選項： XtkSecurity_Restrict_EditXML 及 NmsOperation_OperationMgtDebug。
[顯示全文](../../installation/using/configuring-campaign-options.md)

新增了有關 Campaign Classic 可以使用的不同外部帳戶，以及如何設定這些帳戶的相關資訊。
[顯示全文](../../installation/using/external-accounts.md)

更新「Analytics Data Connector 」章節，以反映介面變更。
[顯示全文](../../platform/using/adobe-analytics-data-connector.md)

新增了關於帳單報表的資訊。
[顯示全文](../../production/using/monitoring-processes.md)

更新了「共用受眾整合」的文件。
[顯示全文](../../integrations/using/configuring-shared-audiences-integration-in-adobe-campaign.md)

更新下列技術文件： [SMS 連接器通訊協定與設定](https://helpx.adobe.com/tw/campaign/kb/sms-connector-protocol-and-settings.html)，以及 [序列自動產生](https://helpx.adobe.com/tw/campaign/kb/sequence_auto_generation.html#Switchtoadedicatedsequence)。

更新「技術工作流程」章節。[顯示全文](../../workflow/using/about-technical-workflows.md)

改善並更新「Campaign 網域名稱設定程序」。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/domain-name-delegation.html)

更新 Android應用程式從 Google 雲端傳訊 (GCM) 移轉至 Firebase 雲端傳訊 (FCM) 的移轉程序。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/migrate-to-fcm.html)

更新「Campaign 硬體調整指南」。[顯示全文](https://helpx.adobe.com/tw/campaign/kb/hardware-sizing-guide.html)

新增關於 Teradata 外部帳戶的「查詢集區」的相關資訊。[顯示全文](../../installation/using/external-accounts.md)

## 2019 年 1 月{#release-doc-16-01-2019}

更新 Marketing Cloud Triggers Technote。[顯示全文](../../integrations/using/about-triggers.md)

已於「優惠方案核准」章節新增說明，以指出「已核准內容」提及是代表內容核准流程已完成，不論所有優惠方案是否已啟用/核准。[顯示全文](../../interaction/using/offer-catalog-overview.md)

「安裝指南」新增了新的章節，列出「管理/平台/選項」節點中的選項。[顯示全文](../../installation/using/configuring-campaign-options.md)

新增了使用種子地址保護郵寄清單的相關資訊。[顯示全文](../../delivery/using/creating-seed-addresses.md)

建立和傳送傳遞時的主要步驟已重新分組成為新章節，並視需要引述各管道。[顯示全文](../../delivery/using/steps-about-delivery-creation-steps.md)

移動、重新組織及改善「[電子郵件封存](../../installation/using/email-archiving.md)」章節，並釐清相關資訊：

* 新增了有關每一連線的電子郵件及 BCC 傳送 IP 參數的最佳實務。

* 如果您已透過舊版組建版本 (Adobe Campaign 17.2之前——組建版本 8795) 來使用電子郵件封存，我們更新了升級至新版電子郵件封存系統 (BCC) 的步驟。

「使用工作流程自動化」指南新增了使用案例：傳送個人化警報給營運商。[顯示全文](../../workflow/using/sending-personalized-alerts-to-operators.md)

更新「移轉至新版本」章節。本文件現在僅詳細說明從任何舊版移轉至 Adobe Campaign Classic v7 的步驟，因為現在已無法移轉至 Adobe Campaign v6.11。[顯示全文](../../migration/using/about-migration.md)

釐清「出現傳遞暫時性錯誤後重試」章節。[顯示全文](../../delivery/using/understanding-delivery-failures.md)

「定義電子郵件內容」章節，新增了前往「數位內容編輯器」章節的連結。[顯示全文](../../delivery/using/defining-the-email-content.md)

更新「交易式傳訊架構」章節，其中包含控制項及執行實例無法安裝在同一台電腦上的警告。[顯示全文](../../message-center/using/transactional-messaging-architecture.md)

更新「工作流程監控」章節，其中包含適用於 8700 到 8977 (18.10) 組建版本之間的說明，包括如何為這些組建版本安裝 Workflow HeatMap 套件的技術文件連結。[顯示全文](../../workflow/using/heatmap.md)

新增了使用案例，說明如何使用工作流程中的「擴充活動」，傳送包含自訂資料欄位的電子郵件。[顯示全文](../../workflow/using/email-enrichment-with-custom-date-fields.md)

功能影片已移至[此處](https://docs.adobe.com/content/help/zh-Hant/campaign-classic-learn/tutorials/overview.html)。
