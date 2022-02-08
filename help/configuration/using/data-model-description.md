---
product: campaign
title: Adobe Campaign Classic資料模型描述
description: 本文檔介紹Adobe Campaign資料模型
feature: Data Model
exl-id: fc0fd23c-f9ea-4e30-b47b-a84143d882ca
source-git-commit: 3997412f14666fa61bf71d0f0a0653f5cc042e19
workflow-type: tm+mt
source-wordcount: '2374'
ht-degree: 1%

---

# 市場活動資料模型說明{#data-model-description}

![](../../assets/v7-only.svg)

Adobe Campaign 附有預定義的資料模型。本節介紹了Adobe Campaign資料模型的內置表及其相互作用。

要訪問每個表的說明，請轉到 **[!UICONTROL Admin > Configuration > Data schemas]**，從清單中選擇資源，然後按一下 **[!UICONTROL Documentation]** 頁籤。

![](assets/data-model_documentation-tab.png)

>[!NOTE]
>
>並以 XML 描述了應用程式中資料的實體和邏輯結構。並且遵循 Adobe Campaign 專屬的語法，稱為綱要 (schema)。有關Adobe Campaign架構的詳細資訊，請閱讀 [此部分](../../configuration/using/about-schema-reference.md)。

## 主表的說明 {#description-main-tables}

Adobe Campaign依賴於一個關係資料庫，該資料庫包含連結在一起的表。

下圖顯示了Adobe Campaign資料模型的主業務表與每個主欄位之間的聯接。

<!--![](assets/data-model_diagram.png)-->

![](assets/data-model_simplified-diagram.png)

預定義的Adobe Campaign資料模型包括下面列出的主表。

### Nms收件人 {#NmsRecipient}

此表與 **nms：收件人** 架構。

它是用於 **交貨收件人**。 因此，它包含通過各種渠道交付所需的資訊：

* 電子郵件：電子郵件地址。
* iEmailFormat:電子郵件的首選格式(文本為1,HTML為2，未定義時為0)。
* sAddress1、sAddress2、sAddress3、sAddress4、sZipCode、sCity用於構建郵政地址（從1997年5月起遵照XPZ 10-011 AFNOR標準）。
* sPhone、sMobilePhone、sFax分別包含電話、行動電話和傳真號碼。
* iBlackList是用於配置檔案的預設選擇退出標誌（1表示「未訂閱」，否則為0）。

iFolderId欄位是將收件人連結到其執行資料夾的外鍵。 有關此的詳細資訊，請參閱 [Xtk資料夾](#XtkFolder)。

sCountryCode欄位是與接收方關聯的國家/地區的3166-1 Alpha 2 ISO代碼（2個字元）。 此欄位實際上是國家/地區參考表(NmsCountry)上的外鍵，該表包含國家/地區標籤和其他國家/地區代碼資料。 如果未填充國家/地區，則儲存值「XX」（並使用它代替零ID記錄）。

有關「收件人」(Recipient)表格的詳細資訊，請參見 [此部分](../../configuration/using/about-data-model.md#default-recipient-table)。

### NMS組 {#NmsGroup}

此表與 **nms:group** 架構。

它使您能夠建立 **收件人靜態組**。 收件人和組之間存在多對多關係。 例如，一個收件人可以屬於多個組，一個組可以包含多個收件人。 可以通過導入或傳遞目標手動建立組。 組通常用作傳遞目標。 欄位上有一個唯一索引，它表示sName組的內部名稱。 該組連結到資料夾（密鑰為iFolderId）。 有關此的詳細資訊，請參閱 [Xtk資料夾](#XtkFolder))。

### NmsRcpGrpRel {#NmsRcpGrpRel}

NmsRcpGrpRel關係表只包含與iRecipientId和iGroupId連結表的標識符對應的兩個欄位。

### NMS服務 {#NmsService}

此表與 **nms：服務** 架構。

在Adobe Campaign，您可以建立和管理資訊服務（主題）的訂閱。 NmsService表儲存您為收件人提供的訂閱資訊服務（主題）的定義（例如新聞簡訊）。

服務是與組（靜態收件者分組）類似的實體，但它們可循環更多資訊，並允許通過表單輕鬆管理訂閱和取消訂閱。

欄位上有一個唯一索引，它表示sName服務的內部名稱。 該服務連結到資料夾（密鑰為iFolderId）。 有關此的詳細資訊，請參閱 [Xtk資料夾](#XtkFolder))。 最後， iType欄位指定此服務的傳遞渠道（0代表電子郵件，1代表SMS,2代表電話，3代表直郵，4代表傳真）。

### Nms訂閱 {#NmsSubscription}

此表與 **nms：訂閱** 架構。

它使您能夠管理資訊服務的收件人訂閱。

### NmsSubHisto {#NmsSubHisto}

此表與 **nms:subHisto** 架構。

如果使用Web表單或應用程式的介面管理預訂，則所有預訂和未預訂都在NmsSubHisto表中歷史化。 iAction欄位指定在tsDate欄位中儲存的日期執行的操作（0表示未訂閱，1表示訂閱）。

### Nms交付 {#NmsDelivery}

此表與 **nms：交付** 架構。

此表中的每個記錄都表示 **交付操作** 或 **交貨模板**。 它包含執行遞送所需的所有參數（目標、內容等）。 在分析階段建立交付（廣播）日誌(NmsBroadLog)和關聯的跟蹤URL(NmsTrackingUrl)（有關這兩個表的進一步詳細資訊，請參閱下文）。

欄位上有一個唯一索引，它表示sInternalName傳遞或方案的內部名稱。 傳遞連結到執行資料夾(外鍵為iFolderProcessId。 有關此的詳細資訊，請參閱 [Xtk資料夾](#XtkFolder))。

### Xtk資料夾 {#XtkFolder}

它包含 **樹中的所有資料夾** 在 **導航** 頁籤。

資料夾已鍵入：sModel欄位的值指定可包含在資料夾中的資料類型。 此欄位還使客戶端控制台能夠使用相應的表單正確顯示資料。 此欄位的可能值在navTree中定義。

樹由iParentId和iChildCount欄位管理。 sFullName欄位提供樹中資料夾的完整路徑。 最後，欄位上有一個唯一索引，它表示sName資料夾的內部名稱。

## 交付和跟蹤 {#delivery-and-tracking}

此組表連結到 **交貨** 模組，用於監視發送消息時遇到的交貨和最終問題。 有關此的詳細資訊，請參閱 [監視交貨](../../delivery/using/about-delivery-monitoring.md)。 有關跟蹤的詳細資訊，請參見 [跟蹤消息](../../delivery/using/about-message-tracking.md)。

![](assets/data-model_delivery.png)

**NmsBroadLogMsg**:此表與 **nms:broadLogMsg** 架構。 它是傳遞日誌表的擴展。

## 市場活動管理 {#campaign-management}

此組表連結到 **市場營銷活動** 模組，它允許定義、優化、執行和分析通信和營銷活動。 有關此的詳細資訊，請參閱 [關於市場營銷活動](../../campaign/using/designing-marketing-campaigns.md)。

![](assets/data-model_campaign.png)

* **Nms操作**:此表與 **nms：操作** 架構。 它包含市場活動資料。
* **NmsDelivery大綱**:此表與 **nms:deliveryOutline** 架構。 它包含交貨（交貨大綱）的擴展屬性。
* **NmsDlvOutlineItem**:此表與 **nms:dlvOutlineItem** 架構。 它包含交貨大綱的條目。
* **NmsDelivery自定義**:此表與 **nms：交付定制** 架構。 它包含交貨的個性化欄位。
* **NMS預算**:此表與 **nms：預算** 架構。 它包含有關市場活動、計畫、方案、任務和/或交貨的預算資料。
* **Nms文檔**:此表與 **nms：文檔** 架構。 它以檔案（影像、excel或word檔案等）的形式包含市場活動的營銷文檔
* **XtkWorkflow**:此表與 **xtk：工作流** 架構。 它包含市場活動目標。
* **Nms任務**:此表與 **nms：任務** 架構。 它包含市場營銷任務的定義。
* **Nms資產**:此表與 **nms:asset** 架構。 它包含市場營銷資源的定義。

## 通信一致性 {#communication-consistency}

此組表連結到 **市場活動優化** 模組，用於控制、過濾和監控遞送的發送。 有關此的詳細資訊，請參閱 [關於活動類型](../../campaign-opt/using/about-campaign-typologies.md)。

![](assets/data-model_typology.png)

* **Nms類型規則**:此表與 **nms：類型規則** 架構。 它包含根據類型適用於交貨的規則。
* **NMS類型**:此表與 **nms：類型** 架構。 它包含要應用於與類型匹配的交貨的規則集。
* **Nms類型規則**:此表與 **nms：類型規則** 架構。 它包含類型與規則之間的關係。
* **Nms卷線**:此表與 **nms:volumeLine** 架構。 它包含容量規則的可用性行集。
* **已使用的Nms卷**:此表與 **nms：卷已使用** 架構。 它包含能力規則的所有衝減行。

## 響應管理 {#response-management}

此組表連結到 **響應管理器** 模組，它允許衡量營銷活動的成功和收益，或為所有溝通渠道提供建議。 有關此的詳細資訊，請參閱 [關於響應管理器](../../response/using/about-response-manager.md)。

![](assets/data-model_response.png)

### NMSrema假設 {#NmsRemaHypothesis}

此表與 **nms:rema假設** 架構。 它包含了測量假設的定義。

此表包含以XML儲存的重要資訊，包括：

**執行上下文（儲存在XML中的資訊）**

執行上下文將填充要考慮用於計量計算的表和欄位，即：
* nms:remaMatchRcp反應日誌儲存架構。
* 事務表架構（例如採購）。
* 查詢架構，用於定義假設條件的開始表。
* 到個人的連結，使您可以基於查詢架構來識別個人。
* 交易記錄日期。 此欄位不是強制欄位，但建議您使用它來限制計算周長。
* 交易記錄金額：它是自動計算收入指標的可選欄位。

**假設周界（以XML儲存的資訊）**

假設周界包括基於查詢模式表的假設過濾。

**假設重載指令碼（儲存在XML中的資訊）**

假設重載指令碼是JavaScript代碼，它使您能夠在執行期間重載假設的內容。

**計量指標**

在假設執行期間，將自動更新以下指標：

* 反應數： **iTransaction**。 反應日誌表中的行數。
* 聯繫的次數： **iContactRepacted**。 假設中目標接觸的不同數目。
* 控制組計數： **iProofReacted**。 假設中目標控制組接觸的不同數目。
* 聯繫的響應率： **dContactRefacedRate**。 假設中目標接觸的響應率。
* 控制組的響應速率： **dProofRematedRate**。 假設控制組的響應率。
* 聯繫人口總收入： **dContactRepatedTotalAmount**。 假設中目標聯繫人的總收入。
* 控制組的平均收益： **dContactRefactedAvgAmount**。 假設中目標控制組聯繫人的平均收入。
* 控制組之總收益： **dProofRematedTotalAmount**。 假設控制組的總收入。
* 控制組的平均收益： **dProofRefactedAvgAmount**。 假設控制組的平均收入。
* 每個聯繫人的毛利總額： **dContactRefactedTotalMargin**。 假設中目標的每個接觸的總餘量。
* 每個聯繫人的平均毛利： **dContactRefactedAvgMargin**。 假設中目標的每個接觸的平均邊距。
* 控制組的毛利總額： **dProofReactedTotalMargin**。 假設中目標控制組的總餘量。
* 控制組的平均毛利： **dProofRefactedAvgMargin**。 假設中目標的控制組的平均裕度。
* 額外收入： **附加金額**。 （聯繫人的平均收入 — 控制組的平均收入）*聯繫人數。
* 附加利潤： **附加毛利**。 （平均聯繫邊距 — 控制組的平均聯繫邊距）/聯繫數。
* 每個聯繫人的平均成本（SQL表達式）。 已計算的交貨成本/聯繫的數量。
* ROI（SQL表達式）。 已計算交貨成本/聯繫的毛利總額。
* 有效ROI（SQL表達式）。 已計算交貨成本/附加毛利。
* 意義： **重要** （SQL表達式）。 包含0到3的值，具體取決於市場活動的重要性。

### NmsRemaMatchRcp {#NmsRemaMatchRcp}

此表與 **nms:remaMatchRcp** 架構。

它包含一條記錄，表示個體對給定假設的反應。 這些記錄是在假設執行期間建立的。

## 模擬和交付 {#simulation-and-delivery}

此組表連結到 **模擬** 模組，它允許在將您的建議發送給收件人之前test屬於某個類別或環境的優惠的分發。 有關此的詳細資訊，請參閱 [關於提供模擬](../../interaction/using/about-offers-simulation.md)。

![](assets/data-model_simulation.png)

* **Nms模擬**:此表與 **nms：模擬** 架構。 它代表一組在給定人口上交貨或報價的模擬。
* **NmsDlvSimulationRel**:此表與 **nms:dlvSimulationRel** 架構。 它包含模擬中考慮的交貨清單。 模擬的範圍以XML形式儲存。
* **NmsOfferSimulationRel**:此表與 **nms:offerSimulationRel** 架構。 它讓你把模擬和報價聯繫起來。

## 交互模組 {#interaction-module}

此組表連結到 **交互** 模組，允許在與給定聯繫人的交互期間通過使其成為單個或多個適應的提供而即時響應。 有關此的詳細資訊，請參閱 [交互和服務管理](../../interaction/using/interaction-and-offer-management.md)。

* **NMS服務**:此表與 **nms：提供** 架構。 它包含每個營銷優惠的定義。
* **NMS命題RCP**:此表與 **nms：命題Rcp** 架構。 它包含發送給每個人的營銷建議的跨渠道日誌。 當準備或有效地向個人提出建議時，便建立記錄。
* **NmsOfferSpace**:此表與 **nms:offerSpace** 架構。 它包含提出建議的位置的定義。
* **NmsOfferContext**:此表與 **nms:offerContext** 架構。 它包含關於命題適用性的附加標準以及權重計算公式的定義。
* **NmsOfferView**:此表與 **nms:offerView**。 它包含要約陳述。
* **NmsOfferCategory**:此表與 **nms:offerCategory**。 它包含優惠類別。
* **NmsOfferEnv**:此表與 **nms:offerEnv**。 它包含服務環境。

## 消息中心模組 {#message-center-module}

以下一組表連結到 **事務性消息** （消息中心）模組，它允許管理發送給用戶並由從資訊系統觸發的事件生成的個別和唯一通信。 有關此的詳細資訊，請參閱 [關於事務性消息傳遞](../../message-center/using/about-transactional-messaging.md)。

### NmsRtEvent {#NmsRtEvent}

![](assets/data-model_message-center_rt.png)

此表與 **nms:rtEvent** 架構。 它包含即時事件的定義。

### NmsBatchEvent {#NmsBatchEvent}

![](assets/data-model_message-center_batch.png)

此表與 **nms:batchEvent** 架構。 它包含按批處理的事件定義。

<!--## Microsites Module {#microsites-module}

This set of tables is linked to the **Web applications** functionality, which allows to create and publish dynamic and interactive web applications with data from the database and content adapted to the rights of the connected user. For more on this, see [About web applications](../../web/using/about-web-applications.md).

![](assets/data-model_microsites.png)

* **NmsTrackingUrl**: This table matches the **nms:trackingUrl** schema.

* **NmsPurl**: This table matches the **nms:purl** schema.-->

## NMAC模組 {#nmac-module}

此組表連結到 **移動應用頻道**&#x200B;它允許通過應用向iOS和安卓終端發送個性化通知。 有關此的詳細資訊，請參閱 [關於移動應用頻道](../../delivery/using/about-mobile-app-channel.md)。

* **NmsMobileApp**:此表與 **nms:mobileApp** 架構。 它包含Adobe Campaign定義的移動應用。
* **NmsAppSubscription**:此表與 **nms:appSubscription** 架構。 它包含關於一個或多個應用程式的訂戶資訊。
* **NmsAppSubscriptionRcp**:此表與 **nms:appSubscriptionRcp** 架構。 它使您能夠將訂閱應用程式的訪問者與收件人表連結起來。
* **NmsExcludeLogAppSubRcp**:此表與 **nms:excludeLogAppSubRcp** 架構。
* **NmsTrackingLogAppSubRcp**:此表與 **nms:trackingLogAppSubRcp** 架構。
* **NmsBroadLogAppSubRcp**:此表與 **nms:broadLogAppSubRcp** 架構。

## 社會營銷模組 {#social-marketing-module}

此組表連結到 **管理社交網路** 模組，可通過Facebook和Twitter與客戶和潛在客戶進行互動。 有關此的詳細資訊，請參閱 [關於社會營銷](../../social/using/about-social-marketing.md)。

![](assets/data-model_social.png)

* **NMS訪問者**:此表與 **nms：訪問者** 架構。 它包含訪問者的資訊。
* **NmsVisitorSub**:此表與 **nms:visitorSub** 架構。 它使您能夠將訪問者連結到他們訂閱的服務(Twitter或Facebook)。
* **NmsFriendShipRel**:此表與 **nms:friendshipRel** 架構。 它使您能夠在Facebook服務的上下文中將訪問者與其朋友聯繫起來。
* **NmsVisitorInterestRel**:此表與 **nms:visitorInterestRel** 架構。 它使您能夠將訪問者及其興趣聯繫起來。
* **NmsInterest**:此表與 **nms：興趣** 架構。 它包含每個訪問者的興趣清單。
