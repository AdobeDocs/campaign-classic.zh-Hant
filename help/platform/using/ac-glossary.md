---
product: campaign
title: Adobe Campaign辭匯表
description: Adobe Campaign辭匯表
role: User, Data Architect
level: Beginner
hide: true
hidefromtoc: true
source-git-commit: 5e4866281fa661de6ebd344fe68d4f23ae8e876c
workflow-type: tm+mt
source-wordcount: '4246'
ht-degree: 3%

---

# Adobe Campaign字彙表{#ac-glossary}

以下是Adobe Campaign中主要術語和概念的定義，以及相關檔案的連結。 按一下詞語以顯示其定義。

## A - D{#sec-1}

+++**A/B 測試**

A/B測試是一種功能，可讓使用者定義兩到三種電子郵件變體：每個變體都會傳送至母體樣本，以判斷哪個樣本具有最佳結果。 一旦確定後，則會將成功變體發送至剩餘母體。

深入了解 [A/B測試](../../delivery/using/get-started-a-b-testing.md).
+++

+++**存取管理**

存取管理可讓管理員將存取權和權限指派給Adobe Campaign的使用者。 權限包括檢視和/或使用Adobe Campaign功能的能力，例如執行工作流程、定義結構及管理對象。

深入了解 [存取管理](access-management.md).
+++

+++**ACS 連結器**

ACS Connector(Prime Offering)橋接Adobe Campaign v7和Adobe Campaign Standard。 這是Campaign v7中的整合功能，可自動將資料複製到Campaign Standard，將兩個應用程式的最佳功能結合在一起。 Campaign v7提供進階工具，可管理主要行銷資料庫。 從Campaign v7進行資料復寫，可讓Campaign Standard在方便使用的環境中運用豐富的資料。

深入了解 [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++

+++**活動**

活動是浮動視窗項目，會新增至工作流程以定義執行功能。 活動是執行任務的容器。 在工作流程中，指定的活動可產生多個任務，尤其是當有循環或循環（定期）動作時。

深入了解 [工作流程活動](../../workflow/using/about-activities.md).
+++

+++**作用中設定檔**

如果設定檔在過去 12 個月期間，曾經透過任何通道而被設為目標或進行通訊，請將此類設定檔視為「作用中」。根據您的合約，您的每個Campaign執行個體都布建了特定數量的作用中設定檔，這些設定檔會計入以結算費用。

深入了解 [作用中設定檔](about-profiles.md#active-profiles).
+++

+++**核准工作流程活動**

*內容：行銷活動分散式行銷*

「本機核准」活動是工作流程活動，用於在傳送訊息前設定傳遞核准流程。

深入了解 [本機核准活動](../../workflow/using/local-approval.md).
+++

+++**閱聽眾**

對象是根據規則和屬性，為符合篩選器定義條件的一組產生的設定檔。

深入了解 [對象](../../campaign/using/marketing-campaign-target.md).
+++

+++**稽核軌跡**

稽核軌跡會即時擷取在您的Adobe Campaign例項中發生之動作和事件的完整清單。 其中包括自助式存取資料記錄，以協助回答下列問題：工作流程的變更，以及上次更新工作流程的使用者，或您的使用者在例項中執行的動作。

深入了解 [稽核軌跡](../../production/using/audit-trail.md).
+++

+++**自動化行銷活動**

依排程執行的促銷活動，例如針對生日或週年的收件者。 也可用於執行前瞻和回顧邏輯，例如昨天購買的客戶或明天到期的付款人。

深入了解 [行銷活動](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**批次模式**

*內容：行銷活動互動*

在促銷活動互動的內容中，批次模式可讓優惠方案引擎為一組連絡人選取最佳優惠方案（或優惠方案）。 適用性/優先順序規則適用於集的所有聯繫人。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**Campaign**

促銷活動是協調、定義及執行行銷促銷活動的介面。 行銷活動可將一或多個工作流程、傳遞、檔案和其他相關資料點包含在單一且簡單易用的介面中。

深入了解 [行銷活動](../../campaign/using/designing-marketing-campaigns.md).
+++

+++**轉換過程**

*內容：行銷活動互動*

在促銷活動互動的情境中，轉換程式是已識別環境中已啟動的程式，負責在未明確和/或隱含識別連絡人時，將呼叫導向匿名環境。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**通道**

通道是通過其發送通信的介質。 Adobe Campaign中的內建通道包括電子郵件、簡訊、直接郵件、推播通知、LINE和Twitter。 可根據非標準通道需求實作自訂通道。

深入了解 [管道](../../delivery/using/communication-channels.md).
+++

+++**用戶端主控台**

Campaign用戶端主控台是一個豐富用戶端，可讓您連線至您的Campaign應用程式伺服器。 客戶端控制台執行檔(.exe)應用程式安裝在具有Microsoft Windows作業系統的電腦上。 Campaign用戶端主控台會集中所有功能和設定。

深入了解 [用戶端主控台](../../platform/using/adobe-campaign-workspace.md).
+++

+++**內容核准**

內容核准是指讓個別的「運算元」或「運算元」群組在傳送傳遞內容之前先核准傳遞內容的程式。

深入了解 [內容核准](../../campaign/using/marketing-campaign-approval.md).
+++

+++**控制組**

使用控制組群組透過排除其閱聽眾的一部分來評估行銷活動的影響。 操作員可以比較收到消息的目標人口的行為與未定位的聯繫人的行為。 運算子也可以根據傳送記錄，在未來的行銷活動中鎖定控制組。

深入了解 [內容核准](../../campaign/using/marketing-campaign-target.md#defining-a-control-group).
+++

+++**控制面板**

「控制面板」可讓您管理每個執行個體的設定並追蹤其使用方式，協助您以Adobe Campaign產品管理員的身分提高工作效率。 其直覺式介面可讓您輕鬆監視主要資產的使用情況，並執行管理工作，例如 IP 位址允許清單新增、SFTP 儲存空間監控、金鑰管理等等。

深入了解 [內容核准](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant).
+++

+++**立方體**

*內容：行銷分析*

多維資料集是Adobe Campaign直覺式資料探索工具，可協助使用者建立和共用動態報表。

深入了解 [立方體](../../reporting/using/about-cubes.md).
+++

+++**自訂資源**

Adobe Campaign隨附預先定義的資料模型，可透過安裝各種套件來定義資料類型。 運算子可擴充資源以新增自訂欄位或自訂表格（例如交易表或產品表格），以豐富資料模型。

深入了解 [自訂資源](../../configuration/using/about-schema-edition.md).
+++

+++**資料模型**

Campaign資料模型是一組結構，可定義資料類型及其關係（連結）。 資料模型是抽象定義，實際上是使用包含實際資料的資料庫實現的。

深入了解 [自訂資源](../../configuration/using/about-data-model.md).
+++

+++**資料庫清除工作流程**

資料庫清理工作流程會刪除過時的資料，以避免資料庫呈指數增長。 工作流程會自動觸發，使用者不需干預。

深入了解 [資料庫清理工作流程](../../production/using/database-cleanup-workflow.md).
+++

+++**專用伺服器**

*內容：交易式訊息傳送*

專用執行伺服器以利用交易式訊息傳送。 伺服器通常每小時最多可處理50,000個引擎呼叫。 「每專用伺服器」的指定不一定與物理伺服器有1:1的關聯，因為Adobe可能利用虛擬化技術來達到同等的效果。

深入了解 [交易式訊息傳送](../../message-center/using/about-transactional-messaging.md).
+++

+++**傳遞度**

*內容：電子郵件傳遞*

一種量度，可讓運算子在到達收件者收件匣時測量促銷活動的成功，而不會反彈或標示為垃圾訊息。

深入了解 [傳遞能力](../../delivery/using/about-deliverability.md).
+++

+++**傳送**

傳送是特定行銷通訊項目，會透過特定通道（電子郵件、簡訊、推播通知等）傳送給對象。 在行銷術語中也稱為「接觸」。

深入了解 [傳遞](../../delivery/using/communication-channels.md).
+++

+++**傳遞分析**

傳遞分析是準備傳遞。 此程式會將內容與收件者設定檔資料結合，以產生收件者收到的個人化電子郵件。 傳遞分析邏輯可以根據定義的邏輯，從目標中排除收件者或完全停止傳遞。 此程式也包括評估動態內容邏輯以及插入個別收件者設定檔專用的選件。

深入了解 [傳遞分析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery).
+++

+++**傳送記錄檔**

傳送記錄檔包含傳送訊息時產生的資訊。 這些記錄會顯示傳送的詳細資訊，包括已準備、已忽略、已傳送或已失敗的訊息。 可直接從傳送控制面板存取。

深入了解 [傳送記錄檔](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history).
+++

+++**傳遞基礎知識**

*內容：電子郵件傳遞*

Adobe Campaign傳遞基礎諮詢服務提供電子郵件傳遞諮詢與信譽管理，以支援使用Adobe Campaign傳送的客戶。

深入了解 [傳遞能力](../../delivery/using/about-deliverability.md).
+++

+++**傳遞大綱**

*內容：直接郵件*

傳遞大綱是一組結構化元素（文檔、商店、促銷優惠券等） 由公司建立，並用於特定促銷活動。 用於直接郵件傳送的情境中。

深入了解 [直接郵件](../../delivery/using/about-direct-mail-channel.md).
+++

+++**部署嚮導**

部署精靈會定義Campaign執行個體的參數，例如預設命名空間、資料庫清理排程、資料保留期間和其他技術設定。

深入了解 [部署嚮導](../../installation/using/deploying-an-instance.md#deployment-wizard).
+++

+++**描述性分析**

描述性分析是一種上下文相關的報告工具，可用於檢查工作流的工作表中的資料、資料夾中選擇的資料，或對選定傳送的目標和排除項進行深入分析。

深入了解 [描述性分析](../../reporting/using/about-descriptive-analysis.md)
+++

+++**分散式行銷**

*內容：分散式行銷*

Distributed Marketing附加元件提供給Campaign運營商的協作工作區，用於在中央實體（總部、行銷部門等）之間實作行銷活動 本地實體 (銷售地點、地區代理等)。 此合作以共用工作區為基礎，稱為 **Campaign套件清單**，中央建立的行銷活動範本和執行個體會提供給當地實體。

深入了解 [分散式行銷](../../distributed/using/about-distributed-marketing.md)
+++

+++**值分佈**

值的分佈是一種工具，它顯示當前存在於資料庫中的架構屬性的值分佈。 這可協助您判斷哪些值可用、其計數和百分比，並避免在建立查詢或運算式時值的大小寫和拼字問題。

深入了解 [分散式行銷](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**網域委派**

子網域設定可讓您設定網域的子區段（技術上稱為「DNS區域」），以便與Adobe Campaign搭配使用。
網域委派可讓Adobe控制並維護傳送、轉譯及追蹤電子郵件促銷活動所需的DNS所有層面。

深入了解 [網域委派](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hant)
+++

## E - H {#sec-2}

<!--
+++**E4X**

The version of Javascript that is used in Adobe Campaign Classic. Sometimes called ECMAScript, it is an extension of Javascript that allows the mixing of Javascript and XML primitives in the same code. Note that E4X is classified as a deprecated language. 
+++
-->

+++**適用性規則**

*內容：行銷活動互動*

適用性規則是套用至環境、類別或優惠方案的限制，內容涉及有效期、目標和權重。 它們可讓營運商確保選件與目標連絡人一致。 在優惠方案環境中，適用性規則包括套用至優惠方案和要鎖定的收件者的簡報規則。 在類別中，適用性規則可讓運算子及時限制類別的有效性、定義應用程式主題並決定要鎖定的收件者。 它們也可以定義指定時段的乘數權重。 這可讓運算子共用其他類別中選件的規則，以簡化其管理。 在優惠方案中，適用性規則可讓運算子及時限制優惠方案的有效性，並決定要鎖定的收件者。

深入了解 [適用性規則](../../interaction/using/interaction-and-offer-management.md).
+++

+++**合格優惠方案**

*內容：行銷活動互動*

合格優惠方案是指符合上游定義之限制的優惠方案，可以一致地提供給目標。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**電子郵件密件副本**

電子郵件密件副本功能會以電子郵件格式傳送對應傳送電子郵件的完整副本，該副本會儲存至專用的密件副本電子郵件地址，讓寄件者可在外部系統中處理及封存電子郵件。

深入了解 [電子郵件密件副本](../../delivery/using/email-parameters.md#email-bcc).
+++

+++**電子郵件量承諾**

銷售訂單中規定的預計每年傳送的電子郵件。 這是年度電子郵件總量承諾使用量，包括因傳送錯誤而傳送但未傳送的電子郵件，例如：未傳送訊息，包括但不限於電子郵件地址錯誤、硬退信、軟退信、郵件用戶端的電子郵件篩選器，以及電子郵件黑名單。
+++

+++**引擎呼叫**

引擎呼叫是伺服器呼叫，會在伺服器端啟動即時處理，以擷取資料，例如與調查、WebApps、JSSP、API、行動應用程式註冊等相關的資料。 引擎呼叫必須授權包含每天5,000個引擎呼叫。
+++

+++**擴充活動**

「擴充」活動是進階的工作流程活動，可讓運算子擴充所產生工作台資料，以便在工作流程中處理。 此活動通常用於目標定位活動後或匯入檔案後，以及使用目標定位資料之活動前。 擴充功能可轉換入站轉變資料，並設定活動以使用增強資料完成輸出轉變。 它可讓運算子結合來自多個資料集的資料，或建立臨時資源的連結。

深入了解 [擴充活動](../../workflow/using/enrichment.md).
+++

+++**分項清單**

分項清單是在結構中或平台層級定義的資料類型，可定義欄位的有效輸入值。 列舉在使用者介面和查詢產生器中顯示為選擇清單。

深入了解 [列舉](../../platform/using/managing-enumerations.md).
+++

+++**瀏覽器視圖**

Explorer視圖是包含Adobe Campaign對象和資料的資料夾的分層顯示。 請注意，Adobe Campaign中的資料夾系統不像一般樹狀檢視一樣運作，因為每個資料夾都包含特定類型的資料，例如傳送、工作流程或選件。

深入了解 [瀏覽器視圖](../../platform/using/adobe-campaign-explorer.md).
+++

+++**外部帳戶**

外部帳戶是產品連接到其他環境和技術的入口和出口點。 外部帳戶定義產品用於傳送資料至或從其他來源接收資料的連線參數。 一般的外部帳戶類型是SFTP網站的連線、電信以支援傳送SMS、處理退信的郵箱，或外部資料庫的連線。

深入了解 [外部帳戶](../../installation/using/external-accounts.md).
+++

+++**疲勞管理**

*內容：促銷活動最佳化*

疲勞管理可協助您控制訊息的頻率和數量，以避免收件者過度請求，且通常會使用類型規則套用。

深入了解 [疲勞管理](../../campaign-opt/using/pressure-rules.md).
+++

+++**同盟資料存取 (FDA)**

同盟資料存取支援用戶端資料模型的擴充功能，以包含協力廠商資料庫。 它將自動檢測目標表的結構，並使用來自SQL源的資料。 您不需變更Adobe Campaign資料的結構，即可存取外部資料。

深入了解 [同盟資料存取](../../installation/using/about-fda.md).
+++

+++**檔案擷取核准**

*內容：直接郵件*

檔案提取核准是指在將擷取的檔案傳送給外部供應商（例如直接郵件傳送）之前，讓個別的運算子或運算子群組核准其內容和設定的程式。

深入了解 [檔案擷取核准](../../delivery/using/validating.md).
+++

+++**篩選維度**

篩選維度是包含查詢用來篩選所需列的資料或屬性的結構。 篩選維度結構必須直接連結至定義的目標維度，才能讓Adobe Campaign跨資料庫連結並傳回回應者列。

深入了解 [篩選維度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions).
+++

+++**資料夾**

資料夾是Explorer視圖項，它保存特定資料類型的資料庫記錄。 例外是一般資料夾類型，它用作組織元素，不包含任何資料本身，只包含其他資料夾。

深入了解 [資料夾](../../platform/using/adobe-campaign-explorer.md).
+++

+++**資料夾檢視**

「資料夾視圖」是一個特殊的「資源管理器」資料夾類型，用於顯示選定資料類型的所有記錄，無論它屬於哪個資料夾。 資料夾視圖用作管理分區資料或分佈在多個資料夾中的資料的管理工具。

深入了解 [資料夾檢視](../../platform/using/adobe-campaign-explorer.md).
+++

+++**Forms**

Forms會定義特定結構類型的介面表示法。 Forms是輕鬆建立及編輯產品中資料元素（例如收件者、傳送和行銷活動）的工具。 Adobe Campaign中的所有介面元素都是使用Forms在產品本身中建立。 請注意，表單是選用的，並非所有結構都有表單。

深入了解 [Forms](../../configuration/using/identifying-a-form.md).
+++

+++**生成的SQL查詢**

操作符操作架構時為基礎資料庫生成的SQL代碼。 結構定義然後使用資料庫表和列實施的資料類型。 為架構操作（如查詢中）生成的SQL基於安裝的資料庫類型。 因此，資料庫可以交換為不同類型，而Campaign中的查詢維持不變。 Adobe將此功能稱為資料庫無關功能。

深入了解 [生成的SQL查詢](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++

+++**熱度圖**

「促銷活動熱度圖」是一個表格，顯示24小時期間的工作流程執行資訊。 它會依小時和5分鐘間隔顯示整個時段的工作流程分佈。 熱度圖可用來評估伺服器負載，以及判斷耗用最多資源的工作流程活動。

深入了解 [熱度圖](../../workflow/using/heatmap.md).
+++

+++**混合部署**

混合部署是按需服務和部署以一起運行的內部部署軟體的組合。

深入了解 [混合部署](../../installation/using/hosting-models.md#hybrid).

+++

## I - L {#sec-3}

+++**識別模式**

*內容：行銷活動互動*

指連絡人的狀態。 可以是明確、隱含或匿名。

* **顯式**:在聯絡人登入管道介面後即可識別。
* **隱含**:已透過cookie（永久或工作階段）識別連絡人。 可以以匿名或已識別的聯絡人處理。
* **匿名**:無法識別該聯繫人。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**影像提供**

為傳送的收件者提供電子郵件內嵌影像的功能。 根據電子郵件系統的「下載影像」功能插入影像，是在Campaign的追蹤記錄中產生「開啟」項目的原因。

深入了解 [影像提供](../../delivery/using/defining-the-email-content.md#adding-images).
+++

+++**入站互動**

*內容：行銷活動互動*

入站互動是指在連絡人在網路、客服中心或行動裝置等通道中的動作所產生的來電之後的互動。 這類互動通常以統一模式（即每個收件者）處理。

深入了解 [入站互動](../../interaction/using/about-inbound-channels.md).
+++

+++**收件匣轉譯**

收件匣轉譯是產生電子郵件預覽，可確保以最佳方式在各種Web用戶端、網頁郵件和裝置上向收件者顯示訊息。 Adobe Campaign運用Litmus，可讓電子郵件內容建立者在超過70個電子郵件轉譯器中預覽其郵件內容，例如Gmail收件匣或Apple郵件用戶端。

深入了解 [收件匣轉譯](../../delivery/using/delivery-dashboard.md#delivery-rendering).
+++

+++**執行個體設定**

執行個體設定是Adobe Campaign執行個體的組態詳細資訊。 這些設定在「部署」嚮導（「工具」>「高級」>「部署嚮導」）或伺服器和/或實例配置檔案中定義。

深入了解 [執行個體設定](../../installation/using/about-initial-configuration.md).

+++

+++**作業（匯入和匯出）**

作業由精靈系統管理，可簡化資料匯入和匯出產品的程式。 作業使用模板系統以實現簡單和一致性，並可定義為按計畫執行。

深入了解 [匯入和匯出作業](../../platform/using/get-started-data-import-export.md).
+++

+++**清單**

清單是靜態資料集。 清單是從其他來源(Audience Manager、Experience Platform、資料庫等)匯入至Campaign，並在介面中顯示為匯入清單的對象或區段。

深入了解 [清單](../../platform/using/creating-and-managing-lists.md).
+++

+++**本機快取**

儲存在操作員電腦上的本地資訊。 主控台會使用快取資訊來減少傳送至伺服器所需的流量並改善效能。 定期清除本地快取(在「檔案」(File)菜單上)更新儲存的資訊，並提高效能和穩定性。

深入了解 [本機快取](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).
+++

## M - P {#sec-4}

+++**行銷資源管理(MRM)**

*內容：行銷資源管理(MRM)*

此 **行銷資源管理(MRM)** Adobe Campaign中的模組可讓您以協作模式控制行銷動作，提供相關任務、預算和行銷資源的完整管理和即時追蹤。 Adobe Campaign運算子可以透過完整的驗證程式和適當的追蹤工具，協調其動作並核准其所有階段的進度：報告、核准追蹤、通知、論壇等。

深入了解 [MRM](../../mrm/using/about-marketing-resource-management.md).
+++

<!--
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**已命名的權限**

用於定義操作員組訪問權限和權限（角色）的精細資料庫訪問權限。 在產品安裝期間，以及透過匯入定義工具特定功能的各種套件，會填入命名權限。 可以建立自訂命名權限以支援用戶端業務需求。

深入了解 [已命名的權限](../../platform/using/access-management-named-rights.md).
+++

+++**命名空間**

將客戶資料類型與資料模型中Adobe Campaign的原生資料類型分開的分區。 也可用來促進定義從一個例項移轉至另一個例項，例如將結構或範本從開發例項移至生產例項。

深入了解 [命名空間](../../configuration/using/about-schema-reference.md#identification-of-a-schema).
+++

+++**導覽列**

在介面頂端執行的導覽元素。 導覽列會重新分組平台的各種核心功能。 按一下導覽列連結，以顯示與此功能相關的功能集。 哪些核心功能可用取決於您所安裝的套件、附加元件以及您的存取權。導覽列的用途是簡化螢幕管理並提高生產力。

深入了解 [導覽列](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++

+++**導航樹**

Adobe Campaign的「瀏覽器」檢視中的主導覽。 導航樹的工作方式與檔案瀏覽器（如Windows資源管理器）類似。 資料夾可能包含子資料夾。 選取節點會顯示與該節點對應的檢視。 顯示的視圖是與架構關聯的清單，以及用於編輯所選行的輸入表單。 您可以自訂導覽樹狀結構並設定資料夾的權限。

深入了解 [導航樹](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch).
+++

+++**目標**

*內容：行銷資源管理(MRM)*

在促銷活動、方案或計畫內，運算子可以列出目標清單。 這些是要達到的量化值。 在促銷活動、方案或計畫結束時，MRM模組可讓運算子比較目標，並產生專用的報表。

深入了解 [目標](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues).
+++

+++**優惠方案目錄**

*內容：行銷活動互動*

在Adobe Campaign中定義的選件集，可在互動期間加以選取。 該目錄與對應於一個類別的每個節點分層地組織。

深入了解 [優惠方案目錄](../../interaction/using/offer-catalog-overview.md).
+++

+++**優惠方案聯絡人**

*內容：行銷活動互動*

入站互動的連絡人。 在引擎呼叫處理期間，連絡人與目標維度相關聯。 未識別的匿名聯絡人會歸因於訪客鎖定目標維度。 有兩種類型的聯繫人，分別是已識別的和匿名的：

* **已識別的聯絡人**:在頻道上自願識別的聯繫人。 在對外互動中，會自動識別聯絡人。
* **匿名聯繫人**:尚未透過管道自願訂閱，但可透過Cookie隱含識別的連絡人。 此術語僅用於傳入的互動。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**選件設計環境**

*內容：行銷活動互動*

選件 **設計環境** 是運算子建立選件、定義類型規則，以及選取將由選件鎖定的結構的環境。 儲存生成的優惠方案的表也由環境定義。 依預設，Interaction附加元件會隨 **設計** 環境與 **即時** 環境。 兩個環境都已預先設定為鎖定內建的收件者表格。

深入了解 [設計環境](../../interaction/using/fundamental-principles.md).
+++

+++**優惠方案引擎套利**

*內容：行銷活動互動*

選取將顯示在環境中的選件（合格的選件）。 套利原則根據類別和報價中定義的標準，按優先順序對報價進行排序。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**優惠方案引擎修剪**

*內容：行銷活動互動*

刪除不符合選取資格的優惠方案的程式。 在優惠方案引擎套利步驟之前執行。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**選件環境**

*內容：行銷活動互動*

定義選件目錄、其可用空格和環境預先定義篩選器的根資料夾。 運算子需要為每個目標維度建立一個環境。 選件環境有兩種類型：設計與即時。

深入了解 [環境](../../interaction/using/fundamental-principles.md).
+++

+++**選件即時環境**

*內容：行銷活動互動*

連結至行銷活動的環境 **設計環境**. 其內容和資格已透過 **設計環境**. 可以選擇它們以在網站上演示，或者插入到出站消息中。

深入了解 [即時環境](../../interaction/using/fundamental-principles.md).
+++

+++**優惠預覽**

*內容：行銷活動互動*

選件在其資料夾中顯示時的預覽。 您可從選件預覽標籤或聯絡人設定檔存取。

深入了解 [選件預覽](../../interaction/using/creating-an-offer.md#previewing-the-offer).
+++

+++**優惠方案簡報規則**

*內容：行銷活動互動*

選件環境中參考的類型規則，可讓運算子考慮收件者的主張歷史記錄，以排除特定選件。

深入了解 [優惠方案簡報規則](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview).
+++

+++**優惠方案主張**

*內容：行銷活動互動*

優惠方案主張是此動作的結果，包括在指定優惠方案空間向聯絡人呈現優惠方案，例如網站上的橫幅、電子郵件或簡訊內容。 此結果儲存在優惠方案主張表格中，定義優惠方案、收件者和時間戳記，提供收件者已收到之所有優惠方案的記錄。

深入了解 [提供建議](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses).
+++

+++**優惠方案聲明**

*內容：行銷活動互動*

優惠方案主張是此動作的結果，包括在指定優惠方案空間向聯絡人呈現優惠方案，例如網站上的橫幅、電子郵件或簡訊內容。 此結果儲存在優惠方案主張表格中，定義優惠方案、收件者和時間戳記，提供收件者已收到之所有優惠方案的記錄。

深入了解 [互動](../../interaction/using/interaction-and-offer-management.md).
+++

+++**優惠方案模擬**

*內容：行銷活動互動*

優惠方案模擬可讓營運商測試定義範圍（傳送日期、目標區段、優惠方案數量、主題等）內的優惠方案分佈 才能傳送優惠方案。 它可用來調整優惠方案的優先順序和適用性規則，以發揮優惠方案的效益。

深入了解 [選件模擬](../../interaction/using/about-offers-simulation.md).
+++

+++**優惠方案空間**

*內容：行銷活動互動*

選件空間是一個資料夾，用於定義公開選件的位置。 定義空格可讓您指定使用的頻道、建立選件的內容，以及指定呈現的選件。 優惠方案空間是通道與優惠方案引擎之間的介面。

深入了解 [選件模擬](../../interaction/using/creating-offer-spaces.md).
+++

+++**選件主題**

*內容：行銷活動互動*

選件主題是類別中定義的關鍵字，可讓運算子在顯示選件時篩選選件。 主題允許從目錄結構中非階層式選擇選件。

深入了解 [選件主題](../../interaction/using/integrating-an-offer-via-the-wizard.md).
+++

+++**選件權重**

*內容：行銷活動互動*

優惠方案權重是以公式為基礎，公式可精確定義優惠方案的相關性，以便讓引擎選取最相關的優惠方案。 權數在選件中定義，而乘數在類別中定義。 在減輕重量順序時，會考慮合格優惠方案。

深入了解 [選件權重](../../interaction/using/creating-an-offer.md#offer-weight).
+++

## Q - T {#sec-5}

## U - Z {#sec-6}
