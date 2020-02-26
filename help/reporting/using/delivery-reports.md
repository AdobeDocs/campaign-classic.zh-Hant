---
title: 傳送報表
seo-title: 傳送報表
description: 傳送報表
seo-description: null
page-status-flag: never-activated
uuid: 83ea834e-08f7-441b-8f15-a25ec07c4aab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
discoiquuid: cc832666-ad18-49ce-afcc-f9169b683ae8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b74ea9a6b079bbe88ed17a79e532bd8ce6ce13ae

---


# 傳送報表 {#delivery-reports}

您可以透過從傳送概述存取的各種報表來追蹤傳送的執行。 若要顯示報表，請套用下列程式：

1. 前往宇宙 **[!UICONTROL Campaigns]** 並按一下連結， **[!UICONTROL Delivery]** 以顯示傳送清單。
1. 按一下您要顯示的傳送名稱，以顯示其詳細資訊。

   ![](assets/s_ncs_user_detailled_report.png)

1. 選取標 **[!UICONTROL Summary]** 簽，然後按一 **[!UICONTROL Reports]** 下連結以存取特定於傳送的報表。

   ![](assets/s_ncs_user_detailled_report2.png)

   依預設，可使用下列報表：

   * **[!UICONTROL Delivery throughput]** :請參閱「 [傳送吞吐量」](../../reporting/using/global-reports.md#delivery-throughput)。
   * **[!UICONTROL Sharing to social networks]** :請參閱 [分享至社交網路](../../reporting/using/global-reports.md#sharing-to-social-networks)。
   * **[!UICONTROL Statistics on sharing activities]** :請參閱分享 [活動的統計資料](../../reporting/using/global-reports.md#statistics-on-sharing-activities)。
   * **[!UICONTROL Hot clicks]** :請參閱「 [熱點按](#hot-clicks)」。
   * **[!UICONTROL Tracking statistics]** :請參閱追蹤 [統計資料](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** :請參閱 [URL並按一下串流](#urls-and-click-streams)。
   * **[!UICONTROL Tracking indicators]** :請參閱 [追蹤指標](#tracking-indicators)。
   * **[!UICONTROL Non-deliverables and bounces]** :請參閱 [非交付項和彈回](../../reporting/using/global-reports.md#non-deliverables-and-bounces)。
   * **[!UICONTROL User activities]** :請參閱使 [用者活動](../../reporting/using/global-reports.md#user-activities)。
   * **[!UICONTROL Delivery summary]** :請參閱「 [傳送摘要](#delivery-summary)」。
   * **[!UICONTROL Subscription tracking]** :請參閱 [訂閱追蹤](../../reporting/using/global-reports.md#subscription-tracking)。
   * **[!UICONTROL Delivery statistics]** :請參閱「 [傳送統計資料](../../reporting/using/global-reports.md#delivery-statistics)」。
   * **[!UICONTROL Breakdown of opens]** :請參閱「 [開啟的劃分」](../../reporting/using/global-reports.md#breakdown-of-opens)。

## 追蹤指標 {#tracking-indicators}

此報告結合了關鍵指標，可追蹤收件者在收到遞送時的行為。 它可存取傳送和接收統計資料、開啟和點進率、產生的點按串流、網路追蹤，以及將活動分享至社交網路。

>[!NOTE]
>
>根據訊息開啟次數計算的值一律是估計值，因為連結至文字格式電子郵件的錯誤範圍。 指 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 標會考慮此誤差範圍。 有關追蹤開啟的詳細資訊，請參閱追蹤 [開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** :傳送分析後要傳送的訊息總數。
* **[!UICONTROL Success]** :成功處理的消息數。

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>相關百分比是根據成功轉發的消息數計算的。

* **[!UICONTROL Distinct opens for the population reached]** :估計至少開啟一次消息的目標接收者的數目。 取消訂閱連結和鏡像頁面的點按次數會納入考量。
* **[!UICONTROL Sum of opens for the population reached]** :目標收件者開啟總數的估計。
* **[!UICONTROL Clicks on opt-out link]** :取消訂閱連結的點按次數。
* **[!UICONTROL Clicks on the mirror page link]** :鏡像頁面的連結點按次數。 若要考量連結，必須在傳送精靈（追蹤的URL）中定義此連結。 Refer to this [page](../../delivery/using/monitoring-a-delivery.md).
* **[!UICONTROL Estimation of forwards]** :估計目標收件者轉送的電子郵件數。 此值的計算方式是減去不同人員的數目和在電子郵件中點按的不同收件者數目。

   >[!NOTE]
   >
   >有關不同人員與目標接收者之間差異的詳細資訊，請參閱「目標 [人員／接收者」](../../reporting/using/indicator-calculation.md#targeted-persons---recipients)。

**[!UICONTROL 3. Open and click-through rate]**

此表顯示每個網際網路網域的傳送、開啟、點按和原始反應的劃分。 使用下列指標：

* **[!UICONTROL Sent]** :在此域上發送的消息總數。
* **[!UICONTROL Complaints]** :收件者回報為不需要此網域的訊息數。 速率是根據在此網域上傳送的訊息總數來計算。
* **[!UICONTROL Opens]** :此網域已開啟訊息至少一次的不同目標收件者數目。 速率是根據在此網域上傳送的訊息總數來計算。
* **[!UICONTROL Clicks]** :點按相同傳送至少一次的不同目標收件者數目。 速率是根據在此網域上傳送的訊息總數來計算
* **[!UICONTROL Raw reactivity]** :點選至少一次傳送的收件者人數與開啟傳送至少一次的收件者人數的百分比。

>[!NOTE]
>
>此報告中顯示的域名在立方級別使用的明細清單中定義。 若要變更、新增或移除預設網域，請編輯 **[!UICONTROL Domains]** 項目清單並修改值和別名。 如需詳細資訊，請參閱[本小節](../../platform/using/managing-enumerations.md)。類 **[!UICONTROL Others]** 別包含不屬於項目清單任何值的網域名稱。

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>相關百分比是根據成功轉發的消息數計算的。

* **[!UICONTROL Distinct clicks for the population reached]** :點進傳送至少一次的不同人數。
* **[!UICONTROL Cumulated clicks]** :目標收件者點按的總次數，不包括取消訂閱的連結和鏡像頁面。
* **[!UICONTROL Recipient clicks]** :點按相同傳送至少一次的不同目標收件者數目。
* **[!UICONTROL Estimated recipient reactivity]** :在遞送中點擊至少一次的接收者的數量與開啟遞送至少一次的估計接收者的數量之比。 不會考慮退出和鏡像頁面連結的點按次數。

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** :接收消息後瀏覽的網頁數。
* **[!UICONTROL Transactions]** :訊息接收後的購買次數。
* **[!UICONTROL Total amount]** :訊息接收後的購買總數。
* **[!UICONTROL Average transaction amount]** :不同傳送收件者的平均購買次數。
* **[!UICONTROL Articles]** :傳送收件者購買的文章數。
* **[!UICONTROL Average count of articles per transaction]** :不同收件者每次購買的項目平均數。
* **[!UICONTROL Average amount per message]** :每則訊息產生的購買量平均。

   >[!NOTE]
   >
   >為了將已瀏覽的頁面、交易、金額或文章納入考量，必須將網頁追蹤標籤插入相符的網頁。 網路追蹤設定會顯示 [在本節中](../../configuration/using/about-web-tracking.md)。

**[!UICONTROL 6. Sharing activities to email and social networks]**

本節顯示每個社交網路上共用的訊息數。 如需詳細資訊，請參閱「共 [用至社交網路」](../../reporting/using/global-reports.md#sharing-to-social-networks)。

## URL 和點按流 {#urls-and-click-streams}

此報表顯示傳送後所瀏覽的頁面清單。

![](assets/s_ncs_user_url_report.png)

您可以選取下列項目來設定此報表的內容：要顯示的分數圖表、時間篩選（自動作啟動以來，在啟動後的前6小時，等等）和資料顯示模式（依標籤、依URL、依類別），如需詳細資訊，請參閱 [本頁](../../delivery/using/monitoring-a-delivery.md)。 按一 **[!UICONTROL Refresh]** 下以確認您的選擇。

以下比率顯示在報表的上方區段：

* **[!UICONTROL Reactivity]** :點進遞送的目標收件人數與已開啟遞送的目標收件人數的估計數之比。 不會考慮退出連結和鏡像頁面上的點按次數。

   >[!NOTE]
   >
   >有關追蹤開啟的詳細資訊，請參閱追蹤 [開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。

* **[!UICONTROL Distinct clicks]** :在傳送中點按至少一次（排除取消訂閱連結和鏡像頁面）的不同人數。 顯示的速率是根據成功傳送的訊息數量來計算。
* **[!UICONTROL Cumulated clicks]** :目標收件者點按的總次數（不包括取消訂閱連結和鏡像頁面）。 根據成功轉發的消息數計算顯示的速率。

**[!UICONTROL Platform average]** :此平均比率（顯示在每個比率下）（反應性、不同點按次數和累積點按次數）會針對過去六個月內傳送的傳送量計算。 只會考慮具有相同類型和相同管道的遞送。 校樣會排除在外。

中央表格提供下列資訊：

* **[!UICONTROL Clicks]** :每個連結的累計點按次數。
* **[!UICONTROL Clicks (in %)]** :與累計點按總數相關的每個連結點按次數劃分。

**[!UICONTROL Breakdown of clicks in time]**

此圖表顯示每日累計點按次數的劃分。

## 傳送摘要 {#delivery-summary}

此報告提供傳送的所有主要資訊。

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

本節提供兩個指標：

* **[!UICONTROL Initial population]** :傳送所定位的收件者總數。
* **[!UICONTROL Messages rejected by the rule]** :套用類型學規則時，分析期間忽略的地址數：地址丟失、隔離、黑名單等。 有關類型學規則的詳細資訊，請參閱本 [頁](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies)。

**[!UICONTROL Causes of exclusion]**

中間圖表顯示分析期間拒絕之訊息的每個規則劃分。

**[!UICONTROL Delivery statistics]**

本節包含下列指標：

* **[!UICONTROL Messages to be delivered]** :傳送分析後要傳送的訊息總數。
* **[!UICONTROL Success]** :成功處理的消息數。 關聯速率是要傳送的消息數的比率。
* **[!UICONTROL Errors]** :傳送和自動回彈處理期間累積的錯誤總數。 關聯速率是要傳送的消息數的比率。
* **[!UICONTROL New quarantines]** :傳送失敗後隔離的地址數（用戶未知，無效域）。 關聯速率是要傳送的消息數的比率。

## 熱點點按 {#hot-clicks}

此報表顯示訊息內容（HTML和／或文字），在每個連結上包含點按連結的百分比。 個人化會封鎖未訂閱連結、鏡像頁面連結和選件連結，這些會納入累計的點按總數中，但不會顯示在報表中。

>[!NOTE]
>
>如果您的傳送包含選件（互動），報表上方會出現一個方塊，顯示選件的點按百分比。

![](assets/s_ncs_user_clic_report.png)

## 追蹤統計資料 {#tracking-statistics}

此報表提供開啟、點按和交易的統計資料。

![](assets/s_ncs_user_stat_report.png)

它可讓您追蹤傳送的行銷影響。 您可以變更時標（1小時、3小時或24小時檢視等），來設定值的顯示方式。 按一 **[!UICONTROL Refresh]** 下以確認您的選擇。

此報表提供值表和排列圖，顯示傳送達到最高效率所需的時間。 使用下列指標：

* **[!UICONTROL Opens]** :估計達到開啟訊息總數百分比所需時間。 文字格式的電子郵件並未納入考量。 有關追蹤開啟的詳細資訊，請參閱追蹤 [開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :估計達到所記錄點按總數的百分比所需時間。 不會考慮退出連結和鏡像頁面的點按次數。
* **[!UICONTROL Transactions]** :接收消息後達到事務總數的百分比所需時間。 為了考慮事務，必須將事務類型Web跟蹤標籤插入匹配的Web頁。 網路追蹤設定會顯示 [在本節中](../../configuration/using/about-web-tracking.md)。
