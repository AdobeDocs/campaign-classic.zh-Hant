---
product: campaign
title: 傳遞報告
description: 傳遞報告
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Reporting
exl-id: 74feb13f-0994-4a6a-ae4f-2538b07cc9c0
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1451'
ht-degree: 7%

---

# 傳遞報告 {#delivery-reports}



您可以透過各種可從傳送概述存取的報表來追蹤傳送的執行。 要顯示報告，請應用以下過程：

1. 前往 **[!UICONTROL Campaigns]** ，然後按一下 **[!UICONTROL Delivery]** 連結以顯示傳送清單。
1. 按一下您要顯示的傳送名稱，以顯示其詳細資料。

   ![](assets/s_ncs_user_detailled_report.png)

1. 選取 **[!UICONTROL Summary]** ，然後按一下 **[!UICONTROL Reports]** 連結以存取傳送專屬的報表。

   ![](assets/s_ncs_user_detailled_report2.png)

   依預設，可使用下列報表：

   * **[!UICONTROL Delivery throughput]** :請參閱 [傳送總處理能力](../../reporting/using/global-reports.md#delivery-throughput).
   * **[!UICONTROL Sharing to social networks]** :請參閱 [分享至社交網路](../../reporting/using/global-reports.md#sharing-to-social-networks).
   * **[!UICONTROL Statistics on sharing activities]** :請參閱 [共用活動統計](../../reporting/using/global-reports.md#statistics-on-sharing-activities).
   * **[!UICONTROL Hot clicks]** :請參閱 [熱點點按](#hot-clicks).
   * **[!UICONTROL Tracking statistics]** :請參閱 [追蹤統計資料](#tracking-statistics)
   * **[!UICONTROL URLs and click streams]** :請參閱 [URL和點按資料流](#urls-and-click-streams).
   * **[!UICONTROL Tracking indicators]** :請參閱 [追蹤指標](#tracking-indicators).
   * **[!UICONTROL Non-deliverables and bounces]** :請參閱 [無法交付和退信](../../reporting/using/global-reports.md#non-deliverables-and-bounces).
   * **[!UICONTROL User activities]** :請參閱 [使用者活動](../../reporting/using/global-reports.md#user-activities).
   * **[!UICONTROL Delivery summary]** :請參閱 [傳送摘要](#delivery-summary).
   * **[!UICONTROL Subscription tracking]** :請參閱 [訂閱追蹤](../../reporting/using/global-reports.md#subscription-tracking).
   * **[!UICONTROL Delivery statistics]** :請參閱 [傳送統計資料](../../reporting/using/global-reports.md#delivery-statistics).
   * **[!UICONTROL Breakdown of opens]** :請參閱 [開啟次數劃分](../../reporting/using/global-reports.md#breakdown-of-opens).

## 追蹤指標 {#tracking-indicators}

此報表結合了在收到傳遞時追蹤收件者行為的關鍵指標。 它可以存取傳遞和接收統計資料、開啟及點進率、產生的點按資料流、網頁追蹤以及與社交網路的分享活動。

>[!NOTE]
>
>根據訊息開啟次數計算的值一律會經過估計，因為以文字格式連結至電子郵件的錯誤邊界。 此 **[!UICONTROL Distinct opens/Sum of opens for the population reached]** 指標會將此誤差幅度納入考量。 如需追蹤開啟的詳細資訊，請參閱 [追蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-).

![](assets/s_ncs_user_tracking_synth_report.png)

**[!UICONTROL 1. Delivery statistics]**

* **[!UICONTROL Messages to deliver]** :傳遞分析後要傳送的訊息總數。
* **[!UICONTROL Success]** : 已成功處理的訊息數.

**[!UICONTROL 2. Reception statistics]**

>[!NOTE]
>
>相關百分比是根據成功轉送的訊息數量計算。

* **[!UICONTROL Distinct opens for the population reached]** :估計已至少開啟消息一次的目標接收者的數量。 由於必須開啟電子郵件才能點按連結，因此系統會考慮對追蹤URL的點按次數。
* **[!UICONTROL Sum of opens for the population reached]** :目標收件者開啟總數的估計。
* **[!UICONTROL Clicks on opt-out link]** :取消訂閱連結的點按次數。
* **[!UICONTROL Clicks on the mirror page link]** :點擊鏡像頁面連結的次數。 若想納入考量，必須在傳送精靈（追蹤的URL）中將連結定義為。 請參閱 [頁面](../../delivery/using/about-delivery-monitoring.md).
* **[!UICONTROL Estimation of forwards]** :目標收件者轉送的電子郵件估計數。 此值的計算方式是減去不同人員的數量以及在電子郵件中點按的不同收件者數量。

   >[!NOTE]
   >
   >如需不同人員與目標收件者之間差異的詳細資訊，請參閱 [目標人員/收件者](../../reporting/using/indicator-calculation.md#targeted-persons---recipients).

**[!UICONTROL 3. Open and click-through rate]**

此值表格顯示每個網際網路網域的傳送、開啟、點按和原始再活動的劃分。 已使用下列指標：

* **[!UICONTROL Sent]** :在此域上發送的消息總數。
* **[!UICONTROL Complaints]** :收件人報告為不希望的此域的消息數。 此速率是根據在此網域上傳送的訊息總數計算。
* **[!UICONTROL Opens]** :此域中至少開啟一次郵件的不重複目標收件人數。 此速率是根據在此網域上傳送的訊息總數計算。
* **[!UICONTROL Clicks]** :在相同傳送中至少按一下一次的不同目標收件者數目。 此速率是根據在此網域上傳送的訊息總數計算
* **[!UICONTROL Raw reactivity]** :至少按一次傳遞的收件者人數，與至少開啟一次傳遞的收件者人數之比。

>[!NOTE]
>
>此報告中顯示的域名在多維資料集級別使用的明細清單中定義。 若要變更、新增或移除預設網域，請編輯 **[!UICONTROL Domains]** 逐項列出並修改值和別名。 如需詳細資訊，請參閱[本章節](../../platform/using/managing-enumerations.md)。此 **[!UICONTROL Others]** 類別包含不屬於分項清單任何值的網域名稱。

**[!UICONTROL 4. Generated click streams]**

>[!NOTE]
>
>相關百分比是根據成功轉送的訊息數量計算。

* **[!UICONTROL Distinct clicks for the population reached]** :已點按至少一次傳遞的不重複人員數量。
* **[!UICONTROL Cumulated clicks]** :目標收件者點按的總次數，不包括取消訂閱連結和鏡像頁面。
* **[!UICONTROL Recipient clicks]** :在相同傳送中至少按一下一次的不同目標收件者數目。
* **[!UICONTROL Estimated recipient reactivity]** :在傳遞中點擊至少一次的接收者數目與至少開啟傳遞一次的估計接收者數目的比率。 退出和鏡像頁面連結上的點按次數並未納入考量。

**[!UICONTROL 5. Web tracking]**

* **[!UICONTROL Visited pages]** :接收訊息後瀏覽的網頁數。
* **[!UICONTROL Transactions]** :訊息接收後的購買次數。
* **[!UICONTROL Total amount]** :接收訊息後的購買總量。
* **[!UICONTROL Average transaction amount]** :由不同傳送收件者進行的平均購買。
* **[!UICONTROL Articles]** :傳遞收件者購買的文章數。
* **[!UICONTROL Average count of articles per transaction]** :不同收件者每次購買的平均項目數。
* **[!UICONTROL Average amount per message]** :每則訊息產生的平均購買量。

   >[!NOTE]
   >
   >為了考慮已造訪的頁面、交易、金額或文章，必須將網路追蹤標籤插入相符的網頁中。 網路追蹤設定如下所示： [本節](../../configuration/using/about-web-tracking.md).

**[!UICONTROL 6. Sharing activities to email and social networks]**

本節顯示每個社交網路上共用的訊息數量。 有關詳細資訊，請參閱 [分享至社交網路](../../reporting/using/global-reports.md#sharing-to-social-networks).

## URL 和點擊流量 {#urls-and-click-streams}

此報表顯示傳送後所造訪的頁面清單。

![](assets/s_ncs_user_url_report.png)

您可以選取以下項目，以設定此報表的內容：要顯示的分數圖表、時間篩選（自動作啟動以來，在啟動後的前6小時） 以及資料顯示模式（依標籤、URL、類別）。 按一下 **[!UICONTROL Refresh]** 以確認您的選取。

報表的上方區段會顯示下列比率：

* **[!UICONTROL Reactivity]** :已點擊傳遞的目標接收者數量與已開啟傳遞的目標接收者估計數量之比。 選擇退出連結和鏡像頁面上的點按不會納入考量。

   >[!NOTE]
   >
   >如需追蹤開啟的詳細資訊，請參閱 [追蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-).

* **[!UICONTROL Distinct clicks]** :傳遞中至少點擊過一次（不包括取消訂閱連結和鏡像頁面）的不同訪客的數量。 顯示的速率是根據成功傳送的訊息數量計算。
* **[!UICONTROL Cumulated clicks]** :目標收件者點按的總次數（不包括取消訂閱連結和鏡像頁面）。 顯示的速率是根據成功轉送的訊息數計算。

**[!UICONTROL Platform average]** :此平均比率（反應性、不重複點按和累積點按）會針對過去6個月傳送的傳送計算。 只會考慮具有相同類型和相同管道的傳送。 會排除校樣。

中央表格提供下列資訊：

* **[!UICONTROL Clicks]** :每個連結的累積點按次數。
* **[!UICONTROL Clicks (in %)]** :與累積點按總數相關的每個連結點按次數劃分。

**[!UICONTROL Breakdown of clicks in time]**

此圖表顯示每日累積點按次數的劃分。

## 傳遞摘要 {#delivery-summary}

此報告提供傳送的所有主要資訊。

![](assets/s_ncs_user_synth_report.png)

**[!UICONTROL Target population]**

本節包含兩個指標：

* **[!UICONTROL Initial population]** :傳遞鎖定的收件者總數。
* **[!UICONTROL Messages rejected by the rule]** :套用類型規則時，分析期間忽略的地址數：地址遺失、隔離、封鎖清單上等。 如需類型規則的詳細資訊，請參閱 [頁面](../../delivery/using/steps-validating-the-delivery.md#validation-process-with-typologies).

**[!UICONTROL Causes of exclusion]**

中圖顯示分析期間拒絕之訊息的每個規則劃分。

**[!UICONTROL Delivery statistics]**

本節包含下列指標：

* **[!UICONTROL Messages to be delivered]** :傳遞分析後要傳送的訊息總數。
* **[!UICONTROL Success]** :已成功處理的郵件數。 關聯速率是要傳遞的報文數的比率。
* **[!UICONTROL Errors]** :傳遞和自動反彈處理期間累積的錯誤總數。 關聯速率是要傳遞的報文數的比率。
* **[!UICONTROL New quarantines]** :傳送失敗後隔離的地址數（用戶未知、無效域）。 關聯速率是要傳遞的報文數的比率。

## 熱點點擊 {#hot-clicks}

此報告顯示訊息內容 (HTML 和/或文字) 以及每個連結的連結點按百分比。個人化區塊取消訂閱連結、鏡像頁面連結和優惠連結有計入總累計點按數，但不顯示在報告中。

>[!NOTE]
>
>如果您的傳送包含選件（互動），則報表上方會顯示一個方塊，顯示選件的點按百分比。

![](assets/s_ncs_user_clic_report.png)

## 追蹤統計資料 {#tracking-statistics}

此報表提供開啟、點按和交易的統計資料。

![](assets/s_ncs_user_stat_report.png)

它可讓您追蹤傳送對行銷的影響。 您可以透過變更時標（1小時、3小時或24小時檢視等），來設定值的顯示方式。 按一下 **[!UICONTROL Refresh]** 以確認您的選取。

此報表提供值表和排列圖，顯示傳送達到最高效率所需的時間。 已使用下列指標：

* **[!UICONTROL Opens]** :估計達到已開啟訊息總數百分比所需的時間。 未考慮文字格式的電子郵件。 如需追蹤開啟的詳細資訊，請參閱 [追蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** :預估達到記錄點按總數百分比所需的時間。 點按選擇退出連結和鏡像頁面時不會納入考量。
* **[!UICONTROL Transactions]** :在接收消息後達到事務總數的百分比所需時間。 為了考慮事務，必須將事務類型Web追蹤標籤插入到匹配的網頁中。 網路追蹤設定如下所示： [本節](../../configuration/using/about-web-tracking.md).
