---
title: Adobe Campaign Classic資料模型說明
description: 本檔案說明Adobe Campaign Classic資料模型。
page-status-flag: never-activated
uuid: faddde15-59a1-4d2c-8303-5b3e470a0c51
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: schema-reference
discoiquuid: 5957b39e-c2c6-40a2-b81a-656e9ff7989c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 15581517df8d2f397285bbadebd83b7f4539dfd7
workflow-type: tm+mt
source-wordcount: '2375'
ht-degree: 0%

---


# 促銷活動資料模型說明{#data-model-description}

Adobe Campaign隨附預先定義的資料模型。 本節提供Adobe Campaign資料模型內建表格及其互動的詳細資訊。

要訪問每個表的說明，請轉至 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選擇資源，然後按一下選 **[!UICONTROL Documentation]** 項卡。

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>在XML中描述了應用中資料的物理和邏輯結構。 它遵循Adobe Campaign專屬的語法，稱為結構。 如需Adobe Campaign結構描述的詳細資訊，請閱讀 [本節](../../configuration/using/about-schema-reference.md)。

## 主表的說明 {#description-main-tables}

Adobe Campaign依賴包含連結在一起的表格的關係式資料庫。

下圖顯示Adobe Campaign資料模型的主要商業表格與各主要欄位之間的連結。

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

預先定義的Adobe Campaign資料模型包含下列主要表格。

### NmsRecipient {#NmsRecipient}

此表與 **nms:recipient模式匹配** 。

此為傳送收件者的預 **設表格**。 因此，它包含透過各種管道傳送所需的資訊：

* 電子郵件： 電子郵件地址。
* iEmailFormat: 電子郵件的偏好格式（1代表文字，2代表HTML，若未定義則為0）。
* sAddress1、sAddress2、sAddress3、sAddress4、sZipCode、sCity用於建立郵遞區號（與1997年5月的XPZ 10-011 AFNOR標準一致）。
* sPhone、sMobilePhone、sFax分別包含手機、行動電話和傳真號碼。
* iBlackList是用於描述檔的預設退出標幟（1表示「未訂閱」，否則為0）。

iFolderId欄位是將收件者連結至其執行資料夾的外鍵。 如需詳細資訊，請參 [閱XtkFolder](#XtkFolder)。

sCountryCode欄位是與收件者相關聯之國家／地區的3166-1 Alpha 2 ISO程式碼（2個字元）。 此欄位實際上是國家參考表(NmsCountry)上的外鍵，該表包含國家標籤和其他國家代碼資料。 如果未填入國家，則會儲存值&#39;XX&#39;（並用來取代零ID記錄）。

如需「收件者」表格的詳細資訊，請參 [閱本節](../../configuration/using/about-data-model.md#default-recipient-table)。

### NmsGroup {#NmsGroup}

此表與 **nms:group架構匹配** 。

它可讓您建立收 **件者的靜態群組**。 收件者和群組之間有多對多的關係。 例如，一個收件者可以屬於數個群組，而一個群組可以包含數個收件者。 您可以透過匯入或傳送定位，手動建立群組。 群組通常用作傳送目標。 在表示sName組內部名稱的欄位上有一個唯一索引。 群組會連結至資料夾（金鑰為iFolderId）。 如需詳細資訊，請參 [閱XtkFolder](#XtkFolder))。

### NmsRcpGrpRel {#NmsRcpGrpRel}

NmsRcpGrpRel關係表僅包含與iRecipientId和iGroupId連結表的標識符對應的兩個欄位。

### NmsService {#NmsService}

此表與 **nms:service架構匹配** 。

在Adobe Campaign中，您可以建立並管理資訊服務（主題）的訂閱。 NmsService表儲存您為收件人提供的資訊服務（主題）的定義（例如電子報）。

服務是與群組（靜態收件者群組）類似的實體，但它們會循環更多資訊，並可透過表單輕鬆管理訂閱和取消訂閱。

在表示sName服務內部名稱的欄位上有一個唯一索引。 服務會連結至資料夾（金鑰為iFolderId）。 如需詳細資訊，請參 [閱XtkFolder](#XtkFolder))。 最後， iType欄位會指定此服務的傳送管道（0代表電子郵件，1代表簡訊，2代表電話，3代表直效郵件，4代表傳真）。

### NmsSubscription {#NmsSubscription}

此表與 **nms:subscription架構匹配** 。

它可讓您管理資訊服務的收件者訂閱。

### NmsSubHisto {#NmsSubHisto}

此表與 **nms:subHisto架構匹配** 。

如果使用Web表單或應用程式的介面管理預訂，則所有預訂和取消預訂都將在NmsSubHisto表中歷史記錄。 iAction欄位會指定在儲存於tsDate欄位的日期上執行的動作（取消訂閱為0，訂閱為1）。

### NmsDelivery {#NmsDelivery}

此表與 **nms:delivery架構匹配** 。

此表中的每個記錄都代 **表傳送操作** 或傳 **送模板**。 它包含執行傳送的所有必要參數（目標、內容等）。 分析階段會建立傳送（廣播）記錄檔(NmsBroadLog)和相關的追蹤URL(NmsTrackingUrl)（請參閱下方，以取得這兩個表格的詳細資訊）。

在表示sInternalName傳送或藍本內部名稱的欄位上有一個唯一索引。 傳送會連結至執行資料夾(外鍵是iFolderProcessId。 如需詳細資訊，請參 [閱XtkFolder](#XtkFolder))。

### XtkFolder {#XtkFolder}

它包含 **樹狀結構中所有可見的資料夾** ，這些資料夾位於 **控制台的「導航** 」頁籤中。

已鍵入資料夾： sModel欄位的值指定可包含在資料夾中的資料類型。 此欄位也可讓用戶端主控台以對應的表單正確顯示資料。 此欄位的可能值在navTree中定義。

樹由iParentId和iChildCount欄位管理。 sFullName欄位提供樹中資料夾的完整路徑。 最後，欄位上有一個唯一索引，代表sName檔案夾的內部名稱。

## 傳送與追蹤 {#delivery-and-tracking}

這組表連結到 **Delivery** 模組，它允許監視傳送以及發送消息時最終遇到的問題。 如需詳細資訊，請參閱「監 [控傳送」](../../delivery/using/monitoring-a-delivery.md)。 如需追蹤的詳細資訊，請參閱 [追蹤訊息](../../delivery/using/about-message-tracking.md)。

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**: 此表與 **nms:broadLogMsg模式匹配** 。 它是傳送記錄表的擴充功能。

## 促銷活動管理 {#campaign-management}

這組表格會連結至 **Marketing促銷活動模組** ，可定義、最佳化、執行及分析通訊和行銷活動。 如需詳細資訊，請參閱關於 [行銷促銷活動](../../campaign/using/designing-marketing-campaigns.md)。

![](assets/data-model_campaign.png)

* **NmsOperation**: 此表與 **nms:operation架構匹配** 。 它包含行銷促銷活動的資料。
* **NmsDeliveryOutline**: 此表與 **nms:deliveryOutline架構匹配** 。 它包含傳送的延伸屬性（傳送大綱）。
* **NmsDlvOutlineItem**: 此表與 **nms:dlvOutlineItem模式匹配** 。 它包含傳送大綱的文章。
* **NmsDeliveryCustomization**: 此表與 **nms:deliveryCustomization架構匹配** 。 它包含遞送的個人化欄位。
* **NmsBudget**: 此表與 **nms:budget架構匹配** 。 它包含促銷活動、計畫、方案、任務和／或傳送的預算資料。
* **NmsDocument**: 此表與 **nms:document架構匹配** 。 它以檔案（影像、Excel或Word檔案等）的形式包含促銷活動的行銷檔案
* **XtkWorkflow**: 此表與 **xtk:workflow架構相符** 。 它包含促銷活動定位。
* **NmsTask**: 此表與 **nms:task架構匹配** 。 它包含行銷工作的定義。
* **NmsAsset**: 此表與 **nms:asset架構匹配** 。 它包含行銷資源的定義。

## 通訊一致性 {#communication-consistency}

這組表格會連結至促銷活動最 **佳化模組** ，可讓您控制、篩選及監控傳送的傳送。 如需詳細資訊，請參閱關於 [促銷活動類型](../../campaign/using/about-campaign-typologies.md)。

![](assets/data-model_typology.png)

* **NmsTypelogy規則**: 此表與 **nms:typelogyRule** Schema匹配。 它包含根據類型套用至傳送的規則。
* **NmsTypelogy**: 此表與 **nms：類型學架構匹配** 。 它包含要套用至符合類型學之傳送的規則集。
* **NmsTypelogyRuleRel**: 此表與 **nms:typelogyRuleRel模式匹配** 。 它包含了類型及其規則之間的關係。
* **NmsVolumeLine**: 此表與 **nms:volumeLine模式匹配** 。 它包含容量規則的可用行集。
* **已使用NmsVolume**: 此表與 **nms:volumeUnced模式匹配** 。 它包含能力規則的所有衝減行。

## 回應管理 {#response-management}

這組表連結到 **Response Manager** （響應管理器）模組，該模組允許衡量行銷活動的成功和獲利能力，或為所有通信通道提供建議。 如需此方面的詳細資訊，請參 [閱關於回應管理員](../../campaign/using/about-response-manager.md)。

![](assets/data-model_response.png)

### NmsRemaHosheption {#NmsRemaHypothesis}

此表與 **nms:remaHoxposition** schema一致。 它包含測量假設的定義。

此表包含儲存在XML中的重要資訊，包括：

**執行上下文（儲存在XML中的資訊）**

執行上下文會填入要納入測量計算的表和欄位，即：
* nms:remaMatchRcp反應日誌儲存模式。
* 事務表結構（例如購買）。
* 查詢模式，它允許您定義假設條件的啟動表。
* 個人的連結，可讓您根據查詢結構來識別個人。
* 交易日期。 此欄位並非必填欄位，但建議您使用此欄位來限制計算周長。
* 事務處理金額： 這是自動計算收入指標的可選欄位。

**假設周長（儲存在XML中的資訊）**

假設周長由基於查詢模式表的假設過濾組成。

**假設過載指令碼（儲存在XML中的資訊）**

假設超載指令碼是JavaScript程式碼，可讓您在執行期間超載假設的內容。

**測量指標**

在假設執行期間，會自動更新下列指標：

* 反應次數： **iTransaction**。 反應日誌表中的行數。
* 已聯繫的數量： **iContactRenacted**。 假設中目標連絡的不同數目。
* 控制組計數： **iProofRenacted**。 假設中目標控制組接觸的不同數目。
* 聯絡的回應率： **dContactRenatedRate**。 假設中目標接觸的響應率。
* 控制組的響應率： **dProofRenatedRate**。 假設控制組的響應率。
* 已聯繫的總人口收入： **dContactRenatedTotalAmount**。 假設中目標連絡的總收入。
* 控制組平均收入： **dContactRenatedAvgAmount**。 假設中目標控制組的平均收入。
* 控制組之總收益： **dProofRenatedTotalAmount**。 假設控制組的總收入。
* 控制組平均收入： **dProofRenactedAvgAmount**。 假設控制群組的平均收入。
* 每位連絡人的總利潤： **dContactRenatedTotalMargin**。 假設中定位的每次接觸總利潤。
* 每位連絡人的平均利潤： **dContactRenatedAvgMargin**. 假設中定位的每次接觸平均邊界。
* 控制組毛利： **dProofRenactedTotalMargin**。 在假設中定位的控制組的總餘量。
* 控制組平均利潤： **dProofRenactedAvgMargin**. 在假設中定位的控制組的平均裕度。
* 額外收入： **dAdditionalAmount**。 （已聯繫的平均收入——控制組的平均收入）*已聯繫的數量。
* 額外利潤： **dAdditionalMargin**。 （已聯繫的平均利潤——控制組的平均利潤）/已聯繫的數量。
* 每個聯繫人的平均成本（SQL表達式）。 已計算傳送成本／已聯絡的數量。
* ROI（SQL運算式）。 交貨的計算成本／聯絡的總利潤。
* 有效的投資報酬率（SQL運算式）。 交貨的計算成本／附加毛利。
* 重要性： **iInvertivaty** （SQL表達式）。 包含0到3的值，視促銷活動的重要性而定。

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

此表與 **nms:remaMatchRcp架構匹配** 。

它包含代表個人對特定假設反應的記錄。 這些記錄是在假設執行期間建立的。

## 模擬與傳送 {#simulation-and-delivery}

這組表格會連結至 **Simulation** （模擬）模組，可讓您在將提案傳送給收件者之前，先測試屬於類別或環境的選件的分佈。 如需詳細資訊，請參閱關於 [選件模擬](../../interaction/using/about-offers-simulation.md)。

![](assets/data-model_simulation.png)

* **NmsSimulation**: 此表與 **nms:simulation架構匹配** 。 它代表一組交貨或選件在指定人口上的模擬。
* **NmsDlvSimulationRel**: 此表與 **nms:dlvSimulationRel模式匹配** 。 它包含模擬中考慮的交貨清單。 模擬範圍會儲存在XML中。
* **NmsOfferSimulationRel**: 此表與 **nms:offerSimulationRel架構匹配** 。 它可讓您將模擬與選件連結。

## 互動模組 {#interaction-module}

這組表格會連結至 **Interaction** 模組，讓其成為單一或數個適合的選件，以便在與特定連絡人互動時即時回應。 如需詳細資訊，請參閱「互 [動與選件管理」](../../interaction/using/interaction-and-offer-management.md)。

* **NmsOffer**: 此表與 **nms:offer架構匹配** 。 它包含每個行銷選件的定義。
* **NmsCompotationRcp**: 此表與 **nms:compositionRcp模式匹配** 。 它包含傳送給每個人的跨通道行銷建議記錄。 記錄是在準備或有效地向個人提出建議時建立的。
* **NmsOfferSpace**: 此表與 **nms:offerSpace架構匹配** 。 它包含了提出建議的位置的定義。
* **NmsOfferContext**: 此表與 **nms:offerContext架構相符** 。 它包括關於命題適用性的附加准則以及權計算公式的定義。
* **NmsOfferView**: 此表與 **nms:offerView匹配**。 它包含選件表示法。
* **NmsOfferCategory**: 此表與 **nms:offerCategory匹配**。 它包含選件類別。
* **NmsOfferEnv**: 此表與 **nms:offerEnv匹配**。 它包含選件環境。

## 消息中心模組 {#message-center-module}

以下一組表連結到 **Transactional messaging** (Message Center)模組，該模組允許管理發送給用戶並由從資訊系統觸發的事件生成的單個和唯一的通信。 有關詳細資訊，請參閱關於 [事務性消息傳遞](../../message-center/using/about-transactional-messaging.md)。

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

此表與 **nms:rtEvent架構匹配** 。 它包含即時事件的定義。

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

此表與 **nms:batchEvent模式匹配** 。 它包含事件的批次定義。

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC模組 {#nmac-module}

這組表格會連結至行動應用 **程式頻道**，可透過應用程式將個人化通知傳送至iOS和Android終端。 如需詳細資訊，請參閱關於 [行動應用程式頻道](../../delivery/using/about-mobile-app-channel.md)。

* **NmsMobileApp**: 此表與 **nms:mobileApp架構相符** 。 它包含Adobe Campaign中定義的行動應用程式。
* **NmsAppSubscription**: 此表與 **nms:appSubscription架構相符** 。 它包含有關一或多個應用程式的訂閱者資訊。
* **NmsAppSubscriptionRcp**: 此表與 **nms:appSubscriptionRcp架構相符** 。 它可讓您將訂閱應用程式的訪客連結至收件者表格。
* **NmsExcludeLogAppSubRcp**: 此表與 **nms:excludeLogAppSubRcp架構相符** 。
* **NmsTrackingLogAppSubRcp**: 此表與 **nms:trackingLogAppSubRcp架構相符** 。
* **NmsBroadLogAppSubRcp**: 此表與 **nms:broadLogAppSubRcp架構匹配** 。

## 社交行銷模組 {#social-marketing-module}

這組表格會連結至「管理社交網 **路」模組** ，此模組可透過Facebook和Twitter與客戶和潛在客戶互動。 如需詳細資訊，請參閱關於 [社交行銷](../../social/using/about-social-marketing.md)。

![](assets/data-model_social.png)

* **NmsVisitor**: 此表與 **nms:visitor架構相符** 。 它包含訪客的相關資訊。
* **NmsVisitorSub**: 此表與 **nms:visitorSub架構相符** 。 它可讓您將訪客連結至他們所訂閱的服務（Twitter或Facebook）。
* **NmsFriendShipRel**: 此表與 **nms:friendshipRel架構匹配** 。 它可讓您在Facebook服務的內容中連結訪客與其朋友。
* **NmsVisitorInterestRel**: 此表格符合 **nms:visitorInterestRel** 架構。 它可讓您連結訪客及其興趣。
* **NmsInterest**: 此表與 **nms:interest模式匹配** 。 它包含每位訪客的興趣清單。