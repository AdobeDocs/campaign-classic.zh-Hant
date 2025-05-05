---
product: campaign
title: Adobe Campaign字彙表
description: Adobe Campaign字彙表
feature: Overview
role: User, Data Architect
level: Beginner
exl-id: 81f207a0-bb72-450b-abe4-0b229b6b1f3a
source-git-commit: f469689f9e8a4d805fb95a1ae120ccd35aba3731
workflow-type: tm+mt
source-wordcount: '5959'
ht-degree: 2%

---

# Adobe Campaign字彙表{#ac-glossary}

以下為Adobe Campaign中重要辭彙和概念的定義，以及相關檔案的連結。 按一下字詞以顯示其定義。

## A - D{#sec-1}

+++**A/B 測試**

A/B測試是一項功能，可讓使用者定義兩至三種電子郵件變體：每個變體都會傳送至母體樣本，以判斷哪個變體效果最佳。 一旦確定後，則會將成功變體發送至剩餘群體。

深入瞭解[A/B測試](../../delivery/using/get-started-a-b-testing.md)。
+++

+++**存取管理**

存取管理可讓管理員將存取權和許可權指派給Adobe Campaign的使用者。 許可權包括檢視和/或使用Adobe Campaign功能，例如執行工作流程、定義結構以及管理受眾的能力。

深入瞭解[存取管理](access-management.md)。
+++

<!--
+++**ACS Connector**

ACS Connector (Prime Offering) bridges Adobe Campaign v7 and Adobe Campaign Standard. It is an integrated feature in Campaign v7 that automatically replicates data to Campaign Standard, uniting the best of both applications. Campaign v7 has advanced tools to manage the primary marketing database. The data replication from Campaign v7 allows Campaign Standard to leverage the rich data in a user-friendly environment. 

Learn more about [ACS Connector](../../integrations/using/acs-connector-principles-and-data-cycle.md).
+++
-->

+++**活動**

活動是新增至工作流程的浮動視窗專案，可定義執行功能。 活動是執行任務的容器。 在工作流程中，指定的活動可以產生多個任務，尤其是當有回圈或循環（定期）動作時。

深入瞭解[工作流程活動](../../workflow/using/about-activities.md)。
+++

+++**使用中的設定檔**

如果設定檔在過去12個月期間，曾經透過任何通道而被設為目標或進行通訊，則會視為作用中。 根據您的合約，您的每個Campaign執行個體都已布建特定數量的作用中設定檔，而且會計算這些設定檔數量以結算費用。

深入瞭解[作用中設定檔](../../platform/using/about-profiles.md#active-profiles)。
+++

+++**核准工作流程活動**

*內容：行銷活動分散式行銷*

本機核准活動是工作流程活動，用於在傳送訊息前設定傳遞核准流程。

深入瞭解[本機核准活動](../../workflow/using/local-approval.md)。
+++

+++**客群**

對象是根據規則和屬性，符合篩選定義條件的設定檔結果集。

深入瞭解[對象](../../campaign/using/marketing-campaign-target.md)。
+++

+++**稽核軌跡**

稽核軌跡可以即時擷取Adobe Campaign執行個體中發生之動作和事件的完整清單。 功能包括自助式存取歷史資料記錄，以協助回答下列問題：您的工作流程發生什麼事、上次更新者是誰，或您的使用者在執行個體中做了什麼。

深入瞭解[稽核軌跡](../../production/using/audit-trail.md)。
+++

<!--
----DUPLICATE WITH THE "CAMPAIGN" ENTRY?---
+++**Automated campaigns**

Campaigns that run on a schedule, such as for targeting recipients who have a birthday or an anniversary. Can also be used to execute look-ahead and look-back logic, such as who purchased yesterday or who has a payment due tomorrow.

Learn more about [Campaigns](../../campaign/using/designing-marketing-campaigns.md).
+++
-->

+++**批次模式**

*內容：行銷活動互動*

在Campaign互動的情境下，批次模式可讓優惠方案引擎為一組聯絡人選取最佳優惠方案（或優惠方案）。 資格/優先順序規則會套用至集的所有聯絡人。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**Campaign**

Campaign是協調、定義及執行行銷活動的介面。 行銷活動可以將一或多個工作流程、傳遞、檔案和其他相關資料點整合到單一、易用的介面中。

深入瞭解[行銷活動](../../campaign/using/designing-marketing-campaigns.md)。
+++

<!--
-----NOT USEFUL HERE?-----
+++**Changeover process**

*Context: Campaign Interaction*

In the context of Campaign Interaction, the changeover process is an activated process in an identified environment, responsible for directing the call to an anonymous environment if the contact has not been explicitly and/or implicitly identified.

Learn more about [Interaction](../../interaction/using/interaction-and-offer-management.md).
+++
-->

+++**頻道**

頻道是用來傳送通訊的媒體。 Adobe Campaign中的內建頻道包括電子郵件、簡訊、直接郵件、推播通知、LINE和X (以前稱為Twitter)。 可針對非標準管道需求實作自訂管道。

深入瞭解[管道](../../delivery/using/communication-channels.md)。
+++

+++**使用者端主控台**

Campaign使用者端主控台是豐富的使用者端，可讓您連線至您的Campaign應用程式伺服器。 使用者端主控台可執行檔(.exe)應用程式安裝在裝有Microsoft Windows作業系統的電腦上。 Campaign使用者端主控台可集中所有功能和設定。

深入瞭解[使用者端主控台](../../platform/using/adobe-campaign-workspace.md)。
+++

+++**內容核准**

內容核准是指在傳送傳遞內容之前，先由個別操作員或操作員群組核准傳遞內容的程式。

深入瞭解[內容核准](../../campaign/using/marketing-campaign-approval.md)。
+++

+++**控制組**

使用控制組組，透過排除其閱聽眾的一部分來評估行銷活動的影響。 操作員可以將收到訊息的目標群體的行為與未作為目標的連絡人的行為進行比較。 根據傳送記錄，操作員也可以在未來的行銷活動中以控制群組為目標。

深入瞭解[控制組](../../campaign/using/marketing-campaign-target.md#defining-a-control-group)。
+++

+++**控制面板**

「控制面板」可讓Adobe Campaign的產品管理員管理設定並追蹤每個執行個體的使用量，協助他們提高工作效率。 其直覺式介面可讓他們輕鬆監控關鍵資產的使用情況，並執行管理工作，例如IP位址允許清單新增、SFTP儲存空間監控、金鑰管理等等。

深入瞭解[控制面板](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/key-features.html?lang=zh-Hant)。
+++

+++**多維度資料集**

*內容： Marketing Analytics*

Cube是Adobe Campaign的直覺式資料探索工具，可協助使用者建立和共用動態報表。

深入瞭解[立方體](../../reporting/using/ac-cubes.md)。
+++

+++**自訂資源**

Adobe Campaign隨附預先定義的資料模型，其中資料型別是透過安裝各種套件來定義。 運運算元可以擴充資源，以新增自訂欄位或自訂表格，例如交易或產品表格，藉此豐富資料模型。

深入瞭解[自訂資源](../../configuration/using/about-schema-edition.md)。
+++

+++**資料模型**

Campaign資料模型是一組結構描述，用於定義資料型別及其關係（連結）。 資料模型是抽象定義，以包含實際資料的資料庫實際實作。

深入瞭解[資料模型](../../configuration/using/about-data-model.md)。
+++

+++**資料庫清除工作流程**

資料庫清理工作流程會刪除過時的資料，以避免資料庫內容呈指數增長。 工作流程會自動觸發，使用者無需另行干預。

深入瞭解[資料庫清理工作流程](../../production/using/database-cleanup-workflow.md)。
+++

<!--
----UNCLEAR----
+++**Dedicated server**

*Context: Transactional Messaging*

Dedicated execution server(s) to leverage Transactional Messaging. A server can typically process up to 50,000 Engine Calls per hour. The "Per-Dedicated Server" designation does not necessarily have a 1:1 correlation with a physical server as Adobe may utilize virtualization technologies to achieve the equivalent effect.

Learn more about [Transactional Messaging](../../message-center/using/about-transactional-messaging.md).
+++
-->

+++**傳遞度**

*內容：電子郵件傳遞能力*

可遞送性可讓您測量行銷活動在到達收件者收件匣時不會退回或標示為垃圾訊息的成功。 更準確地說，電子郵件傳遞能力指一組特性，這些特性決定訊息在短時間內透過個人電子郵件地址到達其目的地的能力，以及內容和格式的預期品質。

深入瞭解[傳遞能力](../../delivery/using/about-deliverability.md)。
+++

+++**傳送**

傳遞是透過特定頻道（電子郵件、簡訊、推播通知等）傳送給對象的特定行銷通訊專案。 在行銷術語中又稱為「觸控」。

深入瞭解[傳遞](../../delivery/using/communication-channels.md)。
+++

+++**傳遞分析**

傳遞分析是傳遞的準備。 此程式會將內容與收件者設定檔資料結合，以產生收件者收到的個人化電子郵件。 傳遞分析邏輯可以根據定義的邏輯，從目標中排除收件者或完全停止傳遞。 此程式也包含動態內容邏輯的評估，以及插入個別收件者設定檔專屬的優惠。

深入瞭解[傳遞分析](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。
+++

+++**傳遞記錄**

傳遞記錄檔包含傳送訊息時產生的資訊。 這些記錄會顯示傳送的詳細資料，其中訊息已準備、忽略、傳送或失敗。 可直接從傳遞控制面板存取這些值。

深入瞭解[傳遞記錄](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)。
+++

<!--
----STRANGE IN DOCS?----
+++**Delivery fundamentals**

*Context: Email Deliverability*

Adobe Campaign Deliverability Fundamentals Consulting Service provides email deliverability consultation and reputation management to support customers using Adobe Campaign deliveries.

Learn more about [Deliverability](../../delivery/using/about-deliverability.md).
+++
-->

+++**傳遞大綱**

*內容：直接郵件*

傳遞大網是由公司針對特定行銷活動建立的結構化元素集（檔案、商店、促銷優惠券等）。 它用於直接郵件傳遞的情境下。

深入瞭解[直接郵件](../../delivery/using/about-direct-mail-channel.md)。
+++

+++**部署精靈**

部署精靈會定義Campaign執行個體的引數，例如預設名稱空間、資料庫清理排程、資料保留期間和其他技術設定。

深入瞭解[部署精靈](../../installation/using/deploying-an-instance.md#deployment-assistant)。
+++

+++**描述性分析**

描述性分析是一種內容感應式報告工具，可用來檢查工作流程工作表中的資料、資料夾中選取的資料，或針對選取的傳送目標和排除進行深入探討。

深入瞭解[描述性分析](../../reporting/using/about-descriptive-analysis.md)
+++

+++**分散式行銷**

*內容：分散式行銷*

分散式行銷附加元件為Campaign操作員提供合作工作區，用於在中央實體（總部、行銷部門等）和地方實體（銷售點、區域機構等）之間實施行銷活動。 此合作基於共用工作區，稱為&#x200B;**行銷活動套件清單**，其中集中建立的行銷活動範本和執行個體提供給本機實體。

深入瞭解[分散式行銷](../../distributed/using/about-distributed-marketing.md)
+++

+++**值的分佈**

值分佈是一種工具，可顯示目前存在於資料庫中之綱要屬性的值分佈。 這可協助您判斷哪些值可供使用、其計數和百分比，並在建立查詢或運算式時避免出現值的首字母大寫和拼字問題。

深入瞭解[值的分佈](../../platform/using/defining-filter-conditions.md#selecting-data-to-extract)
+++

+++**網域委派**

子網域設定可讓您設定網域的子區段（技術上稱為「DNS區域」），以便與Adobe Campaign搭配使用。
網域委派可讓Adobe控制並維護DNS的所有層面，這些是傳遞、呈現和追蹤電子郵件行銷活動所需。

深入瞭解[網域委派](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=zh-Hant)
+++

## E - H {#sec-2}

<!--
----DEPRECATED------>
+++**E4X**

E4X是Adobe Campaign Classic中使用的Javascript版本。 它有時稱為ECMAScript，是Javascript的擴充功能，可讓您在同一程式碼中混用Javascript和XML原始程式。 請注意，E4X被分類為淘汰的語言。
+++


+++**適用性規則**

*內容：行銷活動互動*

適用性規則是套用至環境、類別或優惠的限制，涉及有效期間、目標和權重。 它們可讓操作員確保優惠方案符合目標聯絡人。 在優惠方案環境中，適用性規則包括套用至優惠方案和目標收件者的簡報規則。 在類別中，適用性規則可讓運運算元及時限制類別的有效性、定義應用程式主題並決定要定位的收件者。 它們也可以定義指定期間的乘數加權。 這可讓操作員與其他類別中的優惠方案共用規則，藉此簡化管理。 在優惠方案中，適用性規則可讓操作員及時限制優惠方案的有效性並決定要定位的收件者。

深入瞭解[適用性規則](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**合格的優惠**

*內容：行銷活動互動*

符合資格的優惠方案是符合上游定義之限制的優惠方案，可一致地提供給目標。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**電子郵件密件副本**

電子郵件密件副本功能會以EML格式傳送對應傳送電子郵件的精確副本，該副本會儲存至專用的密件副本電子郵件地址，以供寄件者於外部系統中處理和封存電子郵件。

深入瞭解[電子郵件密件副本](../../delivery/using/email-parameters.md#email-bcc)。
+++

<!--
-----STRANGE FOR DOCS?----
+++**Email volume commitment**

The anticipated emails sent per year as set forth in the Sales Order. This is the total annual email volume commitment, including emails sent but not delivered due to delivery errors such as: non-delivery of a message including but not limited to email address errors, hard bounces, soft bounces, email filters of mail clients, and email blacklists. 
+++
-->

<!--
-----USEFUL FOR DOCS?----
+++**Engine call**

An engine call is a server call that starts real-time processing on server side for the extraction of data, such as data relating to surveys, WebApps, JSSP, APIs, mobile app registrations, etc. Engine calls must be licensed in packs of 5,000 Engine Calls per day.
+++
-->

+++**擴充活動**

「擴充」活動是進階的工作流程活動，可讓運運算元擴充產生的工作表資料，以便在工作流程中處理。 此活動通常用於目標定位活動後或匯入檔案後，以及使用目標定位資料的活動前。 增強功能可以轉換入站轉變資料，並設定活動以使用增強型資料完成輸出轉變。 它可讓運運算元結合來自多個資料集的資料，或建立臨時資源的連結。

深入瞭解[擴充活動](../../workflow/using/enrichment.md)。
+++

+++**分項清單**

列舉是在結構描述中或在Platform層級定義的資料型別，可定義欄位的有效輸入值。 列舉會顯示在使用者介面中，並在查詢建置器中顯示為挑選清單。

深入瞭解[分項清單](../../platform/using/managing-enumerations.md)。
+++

+++**總管檢視**

「總管」檢視是包含Adobe Campaign成品和資料的資料夾的階層式顯示。 請注意，Adobe Campaign中的資料夾系統運作方式與典型的樹狀檢視不同，每個資料夾內含特定型別的資料，例如傳送、工作流程或選件。

深入瞭解[總管檢視](../../platform/using/adobe-campaign-explorer.md)。
+++

+++**外部帳戶**

外部帳戶是產品的入口和出口點，可連線其他環境和技術。 外部帳戶會定義產品用來傳送資料至其他來源或從中接收資料的連線引數。 典型的外部帳戶型別包括SFTP網站的連線、支援簡訊傳送的電信、處理退信箱或外部資料庫的連線。

深入瞭解[外部帳戶](../../installation/using/external-accounts.md)。
+++

+++**疲勞管理**

*內容：行銷活動最佳化*

疲勞管理可協助您控制訊息的頻率和數量，以避免收件者過度請求，且通常會套用型別規則。

深入瞭解[疲勞管理](../../campaign-opt/using/pressure-rules.md)。
+++

+++**同盟資料存取(FDA)**

同盟資料存取支援擴充使用者端資料模型，以包含協力廠商資料庫。 它會自動偵測目標表格的結構，並使用來自SQL來源的資料。 您可以在不變更Adobe Campaign資料結構的情況下存取外部資料。

深入瞭解[同盟資料存取](../../installation/using/about-fda.md)。
+++

+++**檔案擷取核准**

*內容：直接郵件*

檔案擷取核准是讓個別操作員或操作員群組核准擷取檔案的內容和設定的程式，然後再傳送給外部廠商，例如直接郵件傳送。

深入瞭解[檔案擷取核准](../../delivery/using/validating.md)。
+++

+++**正在篩選維度**

篩選維度是包含資料或屬性的結構描述，這些資料或屬性由查詢用來篩選所需的列。 篩選維度結構描述必須直接連結至定義的目標維度，以允許Adobe Campaign跨資料庫聯結並傳回回應列。

深入瞭解[篩選維度](../../workflow/using/building-a-workflow.md#targeting-and-filtering-dimensions)。
+++

+++**資料夾**

資料夾是儲存特定資料型別之資料庫記錄的「總管」檢視專案。 例外情況是用作組織元素的Generic資料夾型別，它本身不包含任何資料，只有其他資料夾。

深入瞭解[資料夾](../../platform/using/adobe-campaign-explorer.md)。
+++

+++**資料夾檢視**

「資料夾」檢視是一種特殊的「總管」資料夾型別，用來顯示選定資料型別的所有記錄，無論其屬於哪個資料夾。 資料夾檢視可做為管理工具，用來管理分散在多個資料夾中的分割資料或資料。

深入瞭解[資料夾檢視](../../platform/using/adobe-campaign-explorer.md)。
+++

+++**Forms**

Forms定義特定結構描述型別的介面表示。 Forms是用來輕鬆建立和編輯產品中資料元素的方法，例如收件者、傳遞和行銷活動。 Adobe Campaign中的所有介面元素，都是使用Forms在產品本身中建立。 請注意，表單為選用專案，並非所有結構描述都有表單。

深入瞭解[Forms](../../configuration/using/identifying-a-form.md)。
+++

<!--
-----USEFUL HERE?-----
+++**Generated SQL query**

The SQL code generated for the underlying database when an operator manipulates a schema. Schemas define the data types that are then implemented using database tables and columns. The SQL generated for schema manipulation (such as in a query) is based on the installed database type. Thus, the database can be swapped to a different type and the queries in Campaign remain unchanged. Adobe refers to this functionality as being database-agnostic.

Learn more about [Generated SQL queries](../../platform/using/steps-to-create-a-query.md#step-6---preview-data).
+++
-->

+++**熱度圖**

Campaign熱度圖是顯示24小時期間工作流程執行資訊的表格。 它會以小時和5分鐘為間隔顯示期間的工作流程分佈。 熱度圖可用來評估伺服器負載，以及判斷耗用最多資源的工作流程活動。

深入瞭解[熱度圖](../../workflow/using/heatmap.md)。
+++

+++**混合式部署**

混合式部署是隨選服務和內部部署軟體的組合，可共同運作。

深入瞭解[混合式部署](../../installation/using/hosting-models.md#hybrid)。

+++

## I - L {#sec-3}

<!-- added more details but maybe still not clear/useful here? -->
+++**識別模式**

*內容：行銷活動互動*

識別模式參考連絡人的狀態。 可以是明確、隱含或匿名。

* **explicit**：在連絡人登入通道介面後，即可識別連絡人。
* **implicit**：連絡人已由Cookie識別（永久或工作階段）。 可將它處理為匿名或識別的連絡人。
* **匿名**：無法識別連絡人。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

<!--
----NOT USEFUL HERE?----
+++**Image serving**

The functionality that supplies the images embedded in emails to the delivery's recipients. The insertion of the images based on an emails system's "download images" functionality is what generates an "open" entry in Campaign's tracking logs.

Learn more about [Image serving](../../delivery/using/defining-the-email-content.md#adding-images).
+++
-->

+++**傳入互動**

*內容：行銷活動互動*

傳入互動是指頻道中連絡人的動作（例如網路、客服中心或行動裝置）產生傳入呼叫後的互動。 這類互動通常會在單一模式下處理（即每個收件者）。

深入瞭解[傳入互動](../../interaction/using/about-inbound-channels.md)。
+++

+++**收件匣轉譯**

收件匣轉譯會產生電子郵件預覽，可確保以最佳方式在各種Web使用者端、Web郵件和裝置上向收件者顯示訊息。 Adobe Campaign運用Litmus，允許電子郵件內容建立者在70多個電子郵件轉譯器中預覽其訊息內容，例如Gmail收件匣或Apple Mail使用者端。

深入瞭解[收件匣轉譯](../../delivery/using/delivery-dashboard.md#delivery-rendering)。
+++

+++**執行個體設定**

執行個體設定是Adobe Campaign執行個體的設定詳細資料。 這些設定是在部署精靈（[工具] > [進階] > [部署精靈]）中或在伺服器和/或執行個體組態檔中定義。

深入瞭解[執行個體設定](../../installation/using/about-initial-configuration.md)。

+++

+++**個工作（匯入和匯出）**

工作由助理系統管理，可簡化將資料匯入和匯出產品的過程。 作業使用範本系統以簡化和維持一致性，並可定義成依排程執行。

深入瞭解[匯入及匯出工作](../../platform/using/get-started-data-import-export.md)。
+++

+++**清單**

清單是靜態資料集。 清單是從其他來源(Audience Manager、Experience Platform、資料庫等)匯入Campaign的對象或區段，在介面中會顯示為「匯入清單」。

深入瞭解[清單](../../platform/using/creating-and-managing-lists.md)。
+++

+++**本機快取**

本機快取是儲存在操作員電腦本機上的資訊。 主控台會使用快取資訊來減少伺服器所需的流量並改善效能。 定期清除本機快取(在「檔案」(File)功能表上)會更新儲存的資訊，並改善效能和穩定性。

深入瞭解[本機快取](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。
+++

## M - P {#sec-4}

+++**行銷資源管理(MRM)**

*內容：行銷資源管理(MRM)*

Adobe Campaign中的&#x200B;**行銷資源管理(MRM)**&#x200B;模組可讓您透過提供相關工作、預算和行銷資源的完整管理和即時追蹤，以合作模式控制行銷動作。 Adobe Campaign操作者可透過完整的驗證程式和適當的追蹤工具（報告、追蹤核准、通知、討論論壇等），協調其動作並核准所有階段的進度。

深入瞭解[MRM](../../mrm/using/about-marketing-resource-management.md)。
+++

<!--
----ACS?----
+++**Localization**

This template type is used to manage multilingual messages.  It is available for Email and SMS messages and useable in standalone mode, within a workflow or in a recurring delivery. In the multilingual feature templates, the language management is based on variants. Each variant represents one language.  This functionality is available only in Adobe Campaign Standard.  
+++
-->

+++**已命名的許可權**

用來定義操作員群組存取權和許可權（角色）的精細資料庫存取權。 已命名的許可權會在產品安裝期間填入，並藉由匯入定義工具特定功能的各種套件來填入。 可建立自訂已命名的許可權來支援客戶業務需求。

深入瞭解[已命名的許可權](../../platform/using/access-management-named-rights.md)。
+++

+++**名稱空間**

名稱空間是將客戶資料型別與Adobe Campaign在資料模型中的原生資料型別區分開的分割區。 也可用來協助定義從一個執行個體移轉至另一個執行個體，例如將結構描述或範本從開發執行個體移至生產執行個體。

深入瞭解[名稱空間](../../configuration/using/about-schema-reference.md#identification-of-a-schema)。
+++

<!--
----generic, not specific to campaign----
+++**Navigation bar**

The navigation bar is the navigation element running across the top of the interface. The navigation bar regroups the various core capabilities of the platform. Click a navigation bar link to display the set of functionalities related to this capability. The list of core capabilities you can access depends on the packages and add-ons you have installed and on your access rights. The purpose of the Navigation bar is to simplify screen management and increase productivity.

Learn more about [Navigation Bar](../../platform/using/adobe-campaign-workspace.md#browsing-pages).
+++
-->

+++**導覽樹狀結構**

導覽樹狀結構是Adobe Campaign之「總管」檢視中的主要導覽。 導覽樹狀結構的運作方式與檔案瀏覽器類似（例如Windows檔案總管）。 資料夾可能包含子資料夾。 選取節點會顯示與節點對應的檢視。 顯示的檢視是與結構描述關聯的清單，以及用來編輯所選行的輸入表單。 您可以自訂導覽樹狀結構並設定檔案夾的許可權。

深入瞭解[導覽樹狀結構](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarch)。
+++

+++**目標**

*內容：行銷資源管理(MRM)*

在行銷活動、方案或計畫中，操作員可以陳述目標清單。 這些是可達到的量化值。 在行銷活動、方案或計畫結束時，MRM模組可讓操作員比較專用報告中的目標和結果。

深入瞭解[目標](../../mrm/using/creating-and-managing-tasks.md#expenses-and-revenues)。
+++

+++**優惠方案目錄**

*內容：行銷活動互動*

優惠方案目錄是在Adobe Campaign中定義的一組優惠方案，可在互動期間加以選取。 目錄會以階層方式組織，每個節點都會與類別相對應。

深入瞭解[優惠方案目錄](../../interaction/using/offer-catalog-overview.md)。
+++

+++**優惠連絡人**

*內容：行銷活動互動*

優惠聯絡人是指來自傳入互動的聯絡人。 在引擎呼叫處理期間，聯絡人與目標維度相關聯。 未識別的匿名聯絡人會歸因於訪客目標維度。 有兩種聯絡人型別，分別是已識別和匿名：

* **已識別的連絡人**：已在頻道上自願識別的連絡人。 在對外互動中，會自動識別聯絡人。
* **匿名連絡人**：未透過頻道自願訂閱，但可透過Cookie隱含識別的連絡人。 此術語僅用於傳入的互動。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**優惠方案設計環境**

*內容：行銷活動互動*

優惠方案&#x200B;**設計環境**&#x200B;是運運算元建立優惠方案、定義型別規則，以及選取優惠方案鎖定目標的結構描述的環境。 用來儲存產生之優惠方案主張的表格也由環境定義。 依預設，Interaction附加元件會提供&#x200B;**設計**&#x200B;環境以及連結至它的&#x200B;**即時**&#x200B;環境。 這兩個環境都已預先設定為鎖定內建的收件者表格。

深入瞭解[優惠方案設計環境](../../interaction/using/fundamental-principles.md)。
+++

+++**優惠方案引擎套利**

*內容：行銷活動互動*

優惠方案引擎會選取將顯示在環境中的優惠方案（符合條件的優惠方案）。 套利原則會根據類別和優惠中定義的條件，依優先順序排列優惠方案。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**優惠方案引擎刪減**

*內容：行銷活動互動*

優惠方案引擎刪減是刪除不符合選取條件之優惠方案的程式。 在優惠方案引擎套利步驟之前執行。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**選件環境**

*內容：行銷活動互動*

優惠方案環境是根資料夾，用於定義優惠方案目錄、其可用空間和環境預先定義的篩選器。 運運算元需要為每個目標維度建立一個環境。 選件環境有兩種型別：設計和即時。

深入瞭解[優惠方案環境](../../interaction/using/fundamental-principles.md)。
+++

+++**提供即時環境**

*內容：行銷活動互動*

優惠方案即時環境已連結至行銷活動&#x200B;**設計環境**。 它包含唯讀優惠方案，其內容和資格已透過&#x200B;**設計環境**&#x200B;核准。 您可以選取它們以在網站上顯示，或插入至外寄訊息。

深入瞭解[優惠方案即時環境](../../interaction/using/fundamental-principles.md)。
+++

+++**優惠方案簡報規則**

*內容：行銷活動互動*

優惠方案呈現規則是優惠方案環境中參考的型別規則，可讓運運算元考慮收件者的主張歷程記錄以排除特定優惠方案。

深入瞭解[優惠方案簡報規則](../../interaction/using/managing-offer-presentation.md#presentation-rules-overview)。
+++

+++**優惠預覽**

*內容：行銷活動互動*

這是選件顯示在其資料夾中的預覽。 可從優惠預覽標籤或連絡人設定檔存取。

深入瞭解[優惠預覽](../../interaction/using/creating-an-offer.md#previewing-the-offer)。
+++

+++**優惠方案主張**

*內容：行銷活動互動*

優惠方案主張是動作的結果，其中包括在指定的優惠方案空間向聯絡人簡報優惠方案，例如網站上的橫幅、電子郵件或簡訊內容。 此結果會儲存在優惠方案主張表格中，該表格定義優惠方案、收件者和時間戳記，提供收件者已收到的所有優惠方案的記錄。

深入瞭解[優惠方案主張](../../interaction/using/creating-offer-spaces.md#offer-proposition-statuses)。
+++

+++**優惠方案宣告**

*內容：行銷活動互動*

優惠方案宣告是頻道用來顯示優惠方案的資訊。 優惠方案表示可從表示優惠方案的空間的演算函式建構，或直接輸入介面(例如，在HTML區塊中)。 選件可能以空格表示。

深入瞭解[互動](../../interaction/using/interaction-and-offer-management.md)。
+++

+++**優惠方案模擬**

*內容：行銷活動互動*

優惠方案模擬可讓營運商在實際傳送優惠方案之前，測試已定義範圍（傳送日期、目標區段、優惠方案數量、主題等）的優惠方案分佈。 它可用來調整優惠方案優先順序和適用性規則，以將優惠方案效益最大化。

深入瞭解[優惠方案模擬](../../interaction/using/about-offers-simulation.md)。
+++

+++**優惠方案空間**

*內容：行銷活動互動*

優惠方案空間是定義優惠方案公開位置的資料夾。 定義空間可讓您指定使用的管道、建置優惠方案的內容，以及指定顯示的優惠方案。 優惠方案空間是頻道與優惠方案引擎之間的介面。

深入瞭解[優惠方案空間](../../interaction/using/creating-offer-spaces.md)。
+++

+++**優惠方案主題**

*內容：行銷活動互動*

優惠方案主題是類別中定義的關鍵字，可讓運運算元在顯示優惠方案時篩選優惠方案。 主題允許從目錄結構非階層式選取優惠方案。

深入瞭解[優惠方案主題](../../interaction/using/integrating-an-offer-via-the-wizard.md)。
+++

+++**優惠方案權重**

*內容：行銷活動互動*

優惠權重是根據精確定義優惠相關性的公式，以便讓引擎選取最相關的優惠。 權重在選件中定義，而乘數在類別中定義。 在降低權重順序時，會考慮合格的優惠。

深入瞭解[優惠方案權重](../../interaction/using/creating-an-offer.md#offer-weight)。
+++

+++**運運算元**

運運算元是有許可權登入及執行動作的Adobe Campaign使用者。 操作員與操作員群組相關聯，並繼承這些群組的許可權和許可權。 您也可以將已命名的許可權直接歸因於運運算元。

深入瞭解[運運算元](../../platform/using/access-management-operators.md)。
+++

+++**運運算元群組**

操作員群組可讓您管理Campaign操作員的角色。 您可以定義歸屬於許可權的運運算元群組，然後將運運算元與一或多個群組建立關聯。 這可讓您重複使用許可權，並讓運運算元設定檔更加一致。 它也能促進設定檔的管理和維護。

深入瞭解[運運算元群組](../../platform/using/access-management-groups.md)。
+++

+++**選項**

選項是平台層級變數，用於定義Campaign執行個體的設定。 選項可在平台層級定義時間範圍（例如資料庫清理工作流程）或其他全域定義。

深入瞭解[選項](../../installation/using/configuring-campaign-options.md)。
+++

+++**傳出互動**

*內容：行銷活動互動*

傳出互動是從聯絡人清單（用於傳遞電子郵件、直接郵件等）對互動引擎發出的呼叫。 相同的規則和程式會套用到每個連絡人。 這類互動通常以批次模式處理。

深入瞭解[傳出互動](../../interaction/using/about-outbound-channels.md)。
+++

+++**封裝匯出/匯入**

封裝匯出是包含產生包含物件定義的XML檔案的作業。 套件可用來將功能和定義從一個執行個體移轉至另一個執行個體。 它們也可用來將重要產品定義新增至備份與原始檔控制系統。

深入瞭解[封裝匯出/匯入](../../platform/using/working-with-data-packages.md)。
+++

+++**調色盤**

工作流程浮動視窗會顯示可新增至工作流程的可用活動。 此元件以標籤格式顯示，工作流程活動按其使用邏輯分組。 浮動視窗上可用的活動取決於已安裝至Campaign執行個體的附加元件，以及顯示工作流程的前後關聯。

深入瞭解[浮動視窗](../../workflow/using/building-a-workflow.md#adding-and-linking-activities)。
+++

+++**效能監視**

效能監視資訊會顯示在「監視」頁簽上。 它會顯示基礎系統的測量結果，例如記憶體和CPU使用量、SMTP伺服器統計資料、伺服器處理作業以及其他相關資訊。

深入瞭解[效能監視](../../production/using/monitoring-processes.md)。
+++

+++**個人化區塊**

Adobe Campaign提供可插入傳遞中的內建個人化區塊。 這些變數是動態的、個人化的，並包含特定轉譯。 例如，您可以新增標誌、問候語訊息或映象頁面的連結。 預設提供數個個人化區塊。 您也可以定義自訂個人化區塊，以讓您將傳送個人化最佳化。 實際資料會在傳遞的分析階段插入每個產生的訊息中。

深入瞭解[個人化區塊](../../delivery/using/personalization-blocks.md)。
+++

+++**Personalization欄位**

個人化欄位是將特定收件者的傳遞個人化時使用的單一資料欄位參考。 實際資料值會在傳遞分析階段插入。

深入瞭解[個人化欄位](../../delivery/using/personalization-fields.md)。
+++

+++**Personalization變數**

Personalization變數是傳遞中的程式碼片段，可根據收件者的資訊向不同收件者顯示不同文字。 這些欄位可以個人化欄位或區塊的形式實作。

深入瞭解[Personalization變數](../../delivery/using/about-personalization.md)。
+++

+++**計畫**

計畫是一種資料夾型別，用於依日曆來組織行銷活動。 計畫資料夾在總管檢視中定義以時間為基礎的單位，例如年、季或月。 計畫資料夾可以是巢狀資料夾，並可包含其他Plan資料夾、計畫資料夾或行銷活動。

深入瞭解[計畫](../../campaign/using/setting-up-marketing-campaigns.md)。
+++

+++**預先定義的篩選器**

預先定義的篩選器是已儲存以供重複使用的查詢。 使用預先定義的篩選器可提升生產力（因為這些篩選器只會建立一次）、協助建立一致性（因為所有行銷人員都可以使用篩選器），並降低行銷人員所需的技能，因為他們可能會使用可能無法自行建立的程式碼或邏輯。

深入瞭解[預先定義的篩選器](../../platform/using/creating-filters.md#filtering-recipients)。
+++

<!--
----DEPRECATED----
+++**Predictive Engagement Scoring**

Predictive engagement scoring predicts the probability of a recipient engaging with a message and the probability of opting out (unsubscribing) within the next seven days after the next email send. The probabilities are further divided into buckets according to the specific risk of disengagement, medium, or low. The model also provides the risk percentile rank for the customers to understand where the rank of a certain customer in relation to others. 

Learn more about [Predictive Engagement Scoring](../../platform/using/creating-filters.md).
+++
-->

+++**主索引鍵**

主索引鍵是資料庫表格中每個記錄的唯一識別碼。 表格必須至少有一個索引鍵。 作為規則，索引鍵會在結構描述的主要元素和索引之後宣告。 主索引鍵不能是複合的（包含數個欄位）。

深入瞭解[主索引鍵](../../configuration/using/schema/key.md)。
+++

+++**輪廓**

設定檔是代表最終客戶、潛在客戶或潛在客戶的資訊記錄。 每個設定檔都對應至nmsRecipient表格或外部表格中的記錄，包含Cookie ID、客戶ID、行動識別碼或與特定頻道相關的其他資訊。

深入瞭解[設定檔](../../platform/using/about-profiles.md)。
+++

+++**方案**

計畫和子計畫資料夾會根據業務目標（例如忠誠度、贏取或交叉銷售）來組織行銷活動。 它們也可以代表會計期間或行銷活動策略，例如事件或電子報。 每個方案都包含連結至日曆的行銷活動，提供整體檢視。

深入瞭解[程式](../../campaign/using/setting-up-marketing-campaigns.md)。
+++

+++**公用資源**

Adobe Campaign中的「公用資源」資料夾內含由應用程式伺服器託管的影像。 傳遞中的影像必須發佈至應用程式伺服器（或影像託管伺服器，如果Campaign已設定），才會顯示在傳遞中，例如電子郵件。

深入瞭解[公用資源](../../installation/using/deploying-an-instance.md#managing-public-resources)。
+++

+++**推播**

*內容：行動應用程式頻道*

推播通知是行動應用程式收到的訊息。 推播通知的設定是透過在行動應用程式中包含Experience PlatformSDK程式碼來與Adobe Campaign搭配使用。 針對推播，提供兩種傳送頻道： iOS和Android。

深入瞭解[推播](../../delivery/using/about-mobile-app-channel.md)。
+++

## Q - T {#sec-5}

+++**收件者**

在Adobe Campaign中，收件者是用於傳送傳遞（電子郵件、簡訊等）給客戶的預設設定檔。 儲存在資料庫中的收件者資料可讓您篩選目標並新增個人化資料。 這通常是個人、連絡人、人口統計和交易資訊，但可能是任何型別的支援行銷和分析的資訊。

深入瞭解[收件者](../../configuration/using/about-data-model.md)。
+++

+++**演算函式**

*內容：行銷活動互動*

演算函式定義於選件空間中。 它可用來根據優惠方案中定義的屬性來建構其優惠方案表示。 有三種不同的演算功能模式：HTML、XML和文字。

深入瞭解[演算函式](../../interaction/using/creating-offer-spaces.md)。
+++

<!--
-----DID NOT FIND IN ACC DOCS, ACS?----
+++**Retargeting campaigns**

Campaigns that re-target the recipients of a previous delivery or deliveries.
+++
-->

+++**結構描述**

綱要是與資料庫表格相關聯的XML檔案。 它會定義資料結構，並描述表格的SQL定義。 操作者在Campaign中操作結構描述，產品會將其動作轉譯為必要的SQL，然後針對資料庫執行。

深入瞭解[結構描述](../../configuration/using/about-schema-reference.md)。
+++

+++**結構描述延伸**

方案擴充功能可讓您自訂現成可用的方案，以最符合您的業務使用案例。 例如，您可以將「忠誠度」欄位新增至「收件者」表格。

深入瞭解[結構描述延伸](../../configuration/using/extending-a-schema.md)。
+++

+++**種子地址**

種子地址用於鎖定不符合所定義的目標準則的收件者。如此一來，不在傳遞範圍的收件者可以像任何其他目標收件者一樣接收傳遞。 已將他們新增至訊息的對象，以偵測任何詐用收件者資料庫的行為或確保傳遞。

深入瞭解[種子地址](../../delivery/using/about-seed-addresses.md)。
+++

<!--
-------ACS?-----
+++**Send-time optimization**

To improve the open rate of your messages, you can manually define a sending time per recipient. Each profile will receive the message at the specified date and time, whenever possible. Defining a sending time can be done at the delivery level or using a workflow.

Learn more about [Send-time optimization](../../delivery/using/about-seed-addresses.md:).
+++
-->

+++**服務**

Adobe Campaign可讓您建立和管理資訊服務（例如電子報或產品更新），並管理這些服務的訂閱。 數個服務可同時定義。

深入瞭解[服務](../../delivery/using/about-services-and-subscriptions.md)。
+++

+++**SFTP管理**

在「控制面板」中，您可以與所有連線至您可存取之 Campaign 執行個體的 SFTP 伺服器互動。 「控制面板」可以讓您對SFTP伺服器執行動作，例如監視儲存容量、管理IP位址允許清單及管理公開SSH金鑰。

深入瞭解[SFTP管理](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/about-sftp-management.html?lang=zh-Hant)。
+++

+++**訂閱服務活動**

訂閱服務工作流程活動可讓您為轉變中指定的母體建立或刪除資訊服務的訂閱。

深入瞭解[訂閱服務活動](../../workflow/using/subscription-services.md)。
+++

+++**目標核准**

*內容：行銷活動分散式行銷*

目標核准是讓個別操作員或操作員群組核准傳遞的最終目標的程式（在分析階段產生目標後），然後才能傳送傳遞。

深入瞭解[目標核准](../../workflow/using/local-approval.md)。
+++

+++**目標資料**

目標資料是儲存在工作流程的工作表（轉變）中的資料。 此資料可在傳遞中使用，以個人化傳遞內容或定義傳遞的動態元素邏輯。

深入瞭解[目標資料](../../workflow/using/data-life-cycle.md#target-data)。
+++

+++**目標對應**

目標對應是傳遞管道與特定資料型別的對應。 目標對應定義不同傳遞通道如何連結至結構描述的資料欄位。 它會定義Campaign使用特定欄位或運算式傳送至該資料型別的方式。

深入瞭解[目標對應](../../delivery/using/steps-defining-the-target-population.md#select-a-target-mapping)。
+++

+++**目標定位活動**

目標定位活動是工作流程活動，專用於目標定位、操控人口資料和篩選活動。 它們可讓Operators透過定義集合，並使用交集、聯集或排除作業來分割或組合這些集合，以建立一或多個目標。

深入瞭解[目標定位活動](../../workflow/using/about-targeting-activities.md)。
+++

+++**目標維度**

目標維度是由查詢或其他工作流程活動產生（傳回）的資料型別。 請注意，無論使用什麼查詢來取得回應資料庫列，Adobe Campaign只會傳回回應資料庫列的主索引鍵。

深入瞭解[目標維度](../../workflow/using/targeting-data.md)。
+++

+++**任務活動**

*內容：行銷資源管理(MRM)*

「作業」工作流程活動會將人工作業併入工作流程的邏輯中。 您可以指定兩種情境：第一種是在任務完成時指定，第二種是在任務未完成時指定。 典型的使用案例是將離線動作併入行銷活動，或用於自訂動作，例如核准。

深入瞭解[任務活動](../../workflow/using/task.md)。
+++

<!--
-----NOT USEFUL, detail-----
+++**Task**

One iteration of the defined functionality of a workflow activity. Each execution of a task has a unique task identifier.   

Learn more about [Tasks](../../workflow/using/about-workflows.md).
+++
-->

+++**範本**

範本是用於建立物件的設計元素。 它包含物件設定，並可選擇包含物件的內容。 範本系統可用來建立傳遞、行銷活動、工作流程和Adobe Campaign的許多其他元素。 可用的工廠範本是由安裝的套件所定義。 接著，您就可以視需求，複製範本並加以自訂Campaign運運算元。
+++

<!--
-----ACS -> SEEDS IN ACC-----
+++**Test profiles**

Allows targeting of additional recipients who do not match the defined targeting criteria. They are added to a message's audience to detect any fraudulent use of your recipient database or to ensure delivery. Seen as the Seed type in the Campaign interface.

Learn more about [Test profiles](../../workflow/using/about-workflows.md).
+++
-->

<!--
-----NOT FOR DOCS?-----
+++**Total database storage**

The aggregate size of the production and non-production instance(s) database storage managed by Adobe. 

Learn more about [Total database storage](../../workflow/using/about-workflows.md).
+++
-->

+++**追蹤記錄**

傳送傳遞並啟用追蹤後，「追蹤」技術工作流程會擷取追蹤資料。 此資料可在您傳送的「追蹤」標籤中找到。 您可以找到開啟和點選電子郵件或其他與收件者所收到訊息互動的資訊。

深入瞭解[追蹤記錄](../../delivery/using/accessing-the-tracking-logs.md)。
+++

+++**交易型訊息**

異動訊息是Campaign模組，專為管理從外部資訊系統傳送的事件產生的自訂觸發通知而設計。 交易式訊息是個別且唯一的通訊，由提供者（例如網站）即時傳送。 此為特別預期行為，因為它包含收件者要檢查或確認的重要資訊。

深入瞭解[異動訊息](../../message-center/using/about-transactional-messaging.md)。
+++

&lt;！-------在這裡很有用??----->
+++**觸發的行銷活動**

觸發的行銷活動是在工作流程中收到API請求時執行的行銷活動。 API呼叫由啟動工作流程執行的工作流程中的Signal活動使用。

深入瞭解[觸發的行銷活動](../../workflow/using/external-signal.md)。
+++

<!--
-----NOT USEFUL-----
+++**Triggers**

Signals that initiate execution of a workflow, delivery or other action. Typically an API call. 

Learn more about [Triggers](../../workflow/using/about-workflows.md).
+++
-->

+++**型別**

*內容：行銷活動最佳化*

型別是一組套用至傳遞分析階段的型別規則。 行銷活動型別可包含數個型別規則，但傳遞只能參考一個型別。

深入瞭解[型別](../../campaign-opt/using/about-campaign-typologies.md#typologies)。
+++

+++**型別規則**

*內容：行銷活動最佳化*

型別規則是商務規則，會在傳遞的分析階段中實施。 型別規則是檢查傳遞的內容（控制規則）或傳遞的目標（篩選規則）或強制執行業務要求的其他邏輯（壓力規則）。 規則是可包含在一或多個型別中的精細元素。

深入瞭解[型別規則](../../campaign-opt/using/about-campaign-typologies.md#typology-rules)。
+++

## U - Z {#sec-6}

+++**單一模式**

*內容：行銷活動互動，異動訊息*

在單一模式中，單一連絡人會在執行階段由優惠方案引擎處理。 此模式通常用於傳入互動和異動訊息。

深入瞭解[單一模式](../../interaction/using/about-inbound-channels.md)。
+++

+++**網頁應用程式**

網頁應用程式是由Campaign執行個體託管的動態互動式應用程式頁面。 其中包含來自資料庫的資料，以及適合已連線使用者許可權的內容。 例如，您可以在外部網路上建立編輯表單，或建立通知表單（包含來自資料庫的資料），其中包含表格、圖表、輸入表單等。 此功能可讓您設計和張貼網頁，讓使用者在其中查閱或輸入資訊。

深入瞭解[網頁應用程式](../../web/using/about-web-applications.md)。
+++

+++**工作流程**

工作流程是行銷活動執行流程的視覺化表示。 它可讓您跨應用程式伺服器的不同模組，策劃所有流程和工作。 使用這個全方位的圖像式環境，您可以設計各式流程，包含細分、行銷活動執行、檔案處理、人力參與等。工作流程引擎將執行並追蹤這些流程。

深入瞭解[工作流程](../../workflow/using/about-workflows.md)。
+++

+++**工作流程日誌**

工作流程日誌是工作流程的逐步執行記錄。 它包含工作流程的所有歷史記錄或稽核軌跡。 它可用於開發、疑難排解或偵錯。

深入瞭解[工作流程日誌](../../workflow/using/monitoring-workflow-execution.md)。
+++

+++**工作表**

工作表包含工作流程轉變所攜帶的所有資訊。 每個工作流程會使用多個工作表。工作表會保留其原始活動的結果，且其內容會用作工作流程中下一個（已連線）活動的輸入。  操控工作表（擴充功能、自訂）是Adobe Campaign運運算元的主要技能之一。

深入瞭解[工作表](../../workflow/using/about-workflows.md)。
+++
