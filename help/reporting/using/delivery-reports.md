---
product: campaign
title: 傳遞報告
description: 傳遞報告
feature: Reporting
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 2%

---

# 傳遞報告 {#delivery-reports}

![](../../assets/common.svg)

您可以通過從交貨概覽訪問的各種報表跟蹤交貨的執行。 要顯示報告，請應用以下過程：

1. 轉到 **[!UICONTROL Campaigns]** ，然後按一下 **[!UICONTROL Delivery]** 連結以顯示交貨清單。
1. 按一下要顯示的交貨名稱以顯示其詳細資訊。

   ![](assets/s_ncs_user_detailled_report.png)

1. 選擇 **[!UICONTROL Summary]** ，然後按一下 **[!UICONTROL Reports]** 連結以訪問特定於傳遞的報告。

   ![](assets/s_ncs_user_detailled_report2.png)

   預設情況下，以下報告可用：

   * **[!UICONTROL Delivery throughput]** :參考 [交付吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。
   * **[!UICONTROL Sharing to social networks]** :參考 [共用到社交網路](../../reporting/using/global-reports.md#sharing-to-social-networks)。
   * **[!UICONTROL Statistics on sharing activities]** :參考 [關於共用活動的統計](../../reporting/using/global-reports.md#statistics-on-sharing-activities)。
   * **[!UICONTROL Hot clicks]** :參考 [熱點擊](#hot-clicks)。
   * **[!UICONTROL Tracking statistics]** :參考 [跟蹤統計](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** :參考 [URL並按一下流](#urls-and-click-streams)。
   * **[!UICONTROL Tracking indicators]** :參考 [跟蹤指標](#tracking-indicators)。
   * **[!UICONTROL Non-deliverables and bounces]** :參考 [非交付項和回饋](../../reporting/using/global-reports.md#non-deliverables-and-bounces)。
   * **[!UICONTROL User activities]** :參考 [用戶活動](../../reporting/using/global-reports.md#user-activities)。
   * **[!UICONTROL Delivery summary]** :參考 [交貨摘要](#delivery-summary)。
   * **[!UICONTROL Subscription tracking]** :參考 [訂閱跟蹤](../../reporting/using/global-reports.md#subscription-tracking)。
   * **[!UICONTROL Delivery statistics]** :參考 [傳遞統計](../../reporting/using/global-reports.md#delivery-statistics)。
   * **[!UICONTROL Breakdown of opens]** :參考 [開啟的細目](../../reporting/using/global-reports.md#breakdown-of-opens)。

## 追蹤指標 {#tracking-indicators}

此報表合併了用於跟蹤接收者在接收交貨時的行為的主要指標。 它提供對傳送和接收統計資訊的訪問，開啟和點擊率，生成點擊流，網路跟蹤以及與社交網路共用活動。

>[!NOTE]
>
>基於消息開啟計算的值總是估計，因為以文本格式連結到電子郵件的錯誤邊距。 的 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 指標將這一誤差範圍考慮在內。 有關開啟跟蹤的詳細資訊，請參閱 [跟蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** :傳遞分析後要傳遞的郵件總數。
* **[!UICONTROL Success]** :成功處理的消息數。

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>根據成功轉發的消息數計算相關百分比。

* **[!UICONTROL Distinct opens for the population reached]** :至少一次開啟消息的目標接收者的數目的估計。 按一下取消訂閱連結和鏡像頁面時會被考慮在內。
* **[!UICONTROL Sum of opens for the population reached]** :目標接收者開啟總次數的估計。
* **[!UICONTROL Clicks on opt-out link]** :取消訂閱連結上的按一下次數。
* **[!UICONTROL Clicks on the mirror page link]** :在指向鏡像頁面的連結上按一下的次數。 要考慮到這一點，必須在傳遞嚮導（跟蹤的URL）中將連結定義為這樣。 請參閱此 [頁](../../delivery/using/about-delivery-monitoring.md)。
* **[!UICONTROL Estimation of forwards]** :目標收件人轉發的電子郵件數的估計。 此值通過減去在電子郵件中按一下的不同人員的數量和不同收件人的數量來計算。

   >[!NOTE]
   >
   >有關不同人員和目標收件人之間差異的詳細資訊，請參閱 [目標人員/收件人](../../reporting/using/indicator-calculation.md#targeted-persons---recipients)。

**[!UICONTROL 3. Open and click-through rate]**

此表顯示每個Internet域的交付、開啟、點擊和原始反應性的分解。 使用以下指標：

* **[!UICONTROL Sent]** :在此域上發送的消息總數。
* **[!UICONTROL Complaints]** :收件人報告為不希望接收的此域的郵件數。 該速率根據在此域上發送的消息總數計算。
* **[!UICONTROL Opens]** :此域至少開啟一次郵件的不同目標收件人數。 該速率根據在此域上發送的消息總數計算。
* **[!UICONTROL Clicks]** :按一下同一傳遞至少一次的不同目標收件人數。 此速率是根據在此域上發送的消息總數計算的
* **[!UICONTROL Raw reactivity]** :在傳遞中按一下至少一次的收件人數與開啟傳遞至少一次的收件人數的百分比。

>[!NOTE]
>
>此報告中顯示的域名在多維資料集級別使用的明細清單中定義。 要更改、添加或刪除預設域，請編輯 **[!UICONTROL Domains]** 逐項列出並修改值和別名。 如需詳細資訊，請參閱[本章節](../../platform/using/managing-enumerations.md)。的 **[!UICONTROL Others]** 類別包括不屬於明細清單任何值的域名。

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>根據成功轉發的消息數計算相關百分比。

* **[!UICONTROL Distinct clicks for the population reached]** :點擊遞送至少一次的不同人數。
* **[!UICONTROL Cumulated clicks]** :按目標收件人（不包括未訂閱連結和鏡像頁）按一下的總數。
* **[!UICONTROL Recipient clicks]** :按一下同一傳遞至少一次的不同目標收件人數。
* **[!UICONTROL Estimated recipient reactivity]** :在遞送中點擊至少一次的收件人數目與開啟遞送至少一次的估計收件人數目之比。 按一下「選擇退出」和「鏡像」頁面連結時，不會考慮這些連結。

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** :接收消息後訪問的網頁數。
* **[!UICONTROL Transactions]** :接收消息後的購買數。
* **[!UICONTROL Total amount]** :接收消息後的採購總額。
* **[!UICONTROL Average transaction amount]** :不同交貨收件人的平均採購。
* **[!UICONTROL Articles]** :遞送收件人購買的物品數。
* **[!UICONTROL Average count of articles per transaction]** :不同收件人每次採購的平均物料數。
* **[!UICONTROL Average amount per message]** :每封郵件生成的平均採購量。

   >[!NOTE]
   >
   >為了考慮訪問的頁面、事務、金額或項目，必須將Web跟蹤標籤插入到匹配的網頁中。 Web跟蹤配置在 [此部分](../../configuration/using/about-web-tracking.md)。

**[!UICONTROL 6. Sharing activities to email and social networks]**

此部分顯示每個社交網路上共用的消息數。 有關此內容的詳細資訊，請參閱 [共用到社交網路](../../reporting/using/global-reports.md#sharing-to-social-networks)。

## URL 和點擊流量 {#urls-and-click-streams}

此報告顯示交貨後訪問的頁的清單。

![](assets/s_ncs_user_url_report.png)

通過選擇以下內容，可以配置此報告的內容：要顯示的分數圖表、時間篩選器（自啟動操作以來，在啟動後的頭6小時內，等等） 資料顯示模式（按標籤、按URL、按類別）。 按一下 **[!UICONTROL Refresh]** 以確認您的選取。

報告的上半部分顯示以下比率：

* **[!UICONTROL Reactivity]** :在遞送中按一下的目標收件人數與已開啟遞送的目標收件人的估計數之比。 按一下「opt-out（退出）」連結時，鏡像頁面上的按一下將不被考慮在內。

   >[!NOTE]
   >
   >有關開啟跟蹤的詳細資訊，請參閱 [跟蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。

* **[!UICONTROL Distinct clicks]** :傳遞中至少按一下一次（不包括未訂閱連結和鏡像頁）的不同人數。 根據成功傳送的消息數計算顯示的速率。
* **[!UICONTROL Cumulated clicks]** :目標收件人的點擊總數（不包括未訂閱連結和鏡像頁）。 根據成功轉發的消息數計算顯示的速率。

**[!UICONTROL Platform average]** :在每個速率（反應性、不同的點擊率和累積的點擊率）下顯示的這一平均速率是為過去六個月內發送的遞送計算的。 只考慮具有相同類型和相同渠道的交貨。 排除校樣。

中心表提供以下資訊：

* **[!UICONTROL Clicks]** :每個連結的累計點擊數。
* **[!UICONTROL Clicks (in %)]** :每個連結的點擊次數與累計點擊總次數的分類。

**[!UICONTROL Breakdown of clicks in time]**

此圖表顯示每天累計點擊量的細分。

## 傳遞摘要 {#delivery-summary}

此報告提供有關交貨的所有主要資訊。

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

本節有兩個指標：

* **[!UICONTROL Initial population]** :傳遞目標的收件人總數。
* **[!UICONTROL Messages rejected by the rule]** :應用類型規則時在分析期間忽略的地址數：地址丟失、隔離、拒絕清單等。 有關類型規則的詳細資訊，請參閱此 [頁](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)。

**[!UICONTROL Causes of exclusion]**

中間圖表顯示分析期間拒絕的消息的每個規則的細分。

**[!UICONTROL Delivery statistics]**

本節包括以下指標：

* **[!UICONTROL Messages to be delivered]** :傳遞分析後要傳遞的郵件總數。
* **[!UICONTROL Success]** :成功處理的消息數。 關聯速率是要傳遞的消息數的比率。
* **[!UICONTROL Errors]** :在交貨和自動回彈處理期間累積的錯誤總數。 關聯速率是要傳遞的消息數的比率。
* **[!UICONTROL New quarantines]** :傳遞失敗後隔離的地址數（用戶未知，無效域）。 關聯速率是要傳遞的消息數的比率。

## 熱點點擊 {#hot-clicks}

此報表顯示每個連結上的HTML百分比（和/或文本）。 個性化塊取消訂閱連結、鏡像頁面連結和提供連結在累計的總點擊量中被考慮在內，但不會顯示在報告中。

>[!NOTE]
>
>如果您的交貨包含優惠（交互），則報表上方會顯示一個框，其中顯示優惠的按一下百分比。

![](assets/s_ncs_user_clic_report.png)

## 跟蹤統計 {#tracking-statistics}

此報表提供有關開啟、按一下和事務的統計資訊。

![](assets/s_ncs_user_stat_report.png)

它讓您跟蹤交付對市場營銷的影響。 您可以通過更改時間刻度（1小時、3小時或24小時視圖等）來配置值的顯示方式。 按一下 **[!UICONTROL Refresh]** 以確認您的選取。

此報表提供值表和帕累托圖，其中顯示交貨達到最高效率所需的時間。 使用以下指標：

* **[!UICONTROL Opens]** :估計達到開啟郵件總數百分比所需的時間。 不考慮文本格式的電子郵件。 有關開啟跟蹤的詳細資訊，請參閱 [跟蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :估計達到記錄的點擊總數百分比所需的時間。 按一下「opt-out（選擇退出）」連結時，鏡像頁面不會被考慮在內。
* **[!UICONTROL Transactions]** :在接收消息後達到事務處理總數百分比所需的時間。 為了考慮事務，必須將事務類型Web跟蹤標籤插入匹配的網頁中。 Web跟蹤配置在 [此部分](../../configuration/using/about-web-tracking.md)。
