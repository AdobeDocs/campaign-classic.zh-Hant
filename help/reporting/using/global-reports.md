---
product: campaign
title: 全域報告
description: 全域報告
audience: reporting
content-type: reference
topic-tags: accessing-built-in-reports
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '2183'
ht-degree: 2%

---

# 全域報告 {#global-reports}

這些報告涉及整個資料庫中資料的活動。 若要檢視報表控制面板，請前往&#x200B;**[!UICONTROL Reports]**&#x200B;標籤。

![](assets/s_ncs_user_report_delivery_link.png)

若要顯示報表，請按一下其名稱。 預設可使用下列報表：

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>此區段只會顯示連結至傳送的報表。

* **[!UICONTROL Delivery throughput]** :請參閱 [傳送總處理能力](#delivery-throughput)。
* **[!UICONTROL Browsers]** :請參閱 [瀏覽器](#browsers)。
* **[!UICONTROL Sharing to social networks]** :請參閱 [分享至社交網路](#sharing-to-social-networks)。
* **[!UICONTROL Statistics on sharing activities]** :請參閱 [共用活動的統計資料](#statistics-on-sharing-activities)。
* **[!UICONTROL Operating systems]** :請參閱 [作業系統](#operating-systems)。
* **[!UICONTROL URLs and click streams]** :請參閱 [URL並按一下串流](../../reporting/using/delivery-reports.md#urls-and-click-streams)。
* **[!UICONTROL Tracking indicators]** :請參閱 [追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators)。
* **[!UICONTROL Non-deliverables and bounces]** :請參閱 [無法交付的項目和退信](#non-deliverables-and-bounces)。
* **[!UICONTROL User activities]** :請參閱使 [用者活動](#user-activities)。
* **[!UICONTROL Subscription tracking]** :請參閱 [訂閱追蹤](#subscription-tracking)。
* **[!UICONTROL Delivery summary]** :請參閱 [傳送摘要](../../reporting/using/delivery-reports.md#delivery-summary)。
* **[!UICONTROL Delivery statistics]** :請參閱傳 [送統計資料](#delivery-statistics)。
* **[!UICONTROL Breakdown of opens]** :請參閱 [開啟次數劃分](#breakdown-of-opens)。

## 傳送總處理能力 {#delivery-throughput}

此報表包含指定期間整個平台的傳送輸送量資訊。 為了測量傳送訊息的速度，標準是每小時傳送的訊息數量和訊息的大小（以位元/秒為單位）。 在以下範例中，第一個圖表以藍色顯示成功的傳送，以橘色顯示錯誤傳送的次數。

![](assets/s_ncs_user_report_toolbar.png)

您可以透過變更時標來設定顯示的值：1小時檢視、3小時檢視、24小時檢視等。 按一下 **[!UICONTROL Refresh]** 以確認您的選取。

## 用戶活動{#user-activities}

此報表以圖表形式顯示每半小時、小時或每天開啟、點按和交易的劃分。

![](assets/s_ncs_user_user_report.png)

可以使用以下選項：

* **[!UICONTROL Opens]** :已開啟的郵件總數。不會考慮文字格式的電子郵件。 有關追蹤開啟的詳細資訊，請參閱[追蹤開啟](../../reporting/using/indicator-calculation.md#tracking-opens-)。
* **[!UICONTROL Clicks]** :傳遞中連結的點按總次數。取消訂閱連結和鏡像頁面的點按次數並未納入考量。
* **[!UICONTROL Transactions]** :接收消息後的事務總數。為了考慮事務，必須將事務類型Web追蹤標籤插入到匹配的網頁中。 網路追蹤設定顯示在[此小節](../../configuration/using/about-web-tracking.md)中。

## 傳送失敗和退回的郵件 {#non-deliverables-and-bounces}

此報表顯示無法交付項的劃分，以及每個網際網路網域的退信的劃分。

**[!UICONTROL Number of messages processed]**&#x200B;代表傳遞伺服器處理的訊息總數。 此值低於某些傳送停止或暫停時（伺服器處理之前）要傳送的訊息數。

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>此報告中顯示的錯誤會觸發隔離程式。 有關隔離管理的詳細資訊，請參閱[隔離管理](../../delivery/using/understanding-quarantine-management.md)。

此報告的第一部分以值表和圖表的形式顯示未交付項的劃分。

對於每種錯誤類型，我們都有：

* 此類型的錯誤消息數，
* 具有此類型錯誤的消息的百分比與具有錯誤的消息的總數相比，
* 此類型的錯誤訊息與已處理訊息總數的百分比。

已使用下列指標：

* **[!UICONTROL User unknown]** :傳送期間產生錯誤類型，指出電子郵件地址無效。
* **[!UICONTROL Invalid domain]** :傳送傳送時產生錯誤類型，以指出電子郵件地址的網域錯誤或不存在。
* **[!UICONTROL Inbox full]** :在五次傳送嘗試指出收件者的收件匣包含太多訊息後，產生錯誤類型。
* **[!UICONTROL Account disabled]** :傳送傳遞時產生錯誤類型，指出該位址已不存在。
* **[!UICONTROL Rejected]** :當地址被IAP（Internet訪問提供程式）拒絕時(例如在應用安全規則（反垃圾郵件軟體）之後)生成的錯誤類型。
* **[!UICONTROL Unreachable]** :消息分發字串中出現的錯誤類型：SMTP中繼事件、暫時無法存取網域等
* **[!UICONTROL Not connected]** :指示發送時收件人的行動電話被關閉或斷開與網路的連接的錯誤類型。

   >[!NOTE]
   >
   >此指標只與行動通道上的傳送有關。 如需詳細資訊，請參閱[本章節](../../delivery/using/sms-channel.md)。

   按一下`[+]`符號，可開啟值表的每一行。 對於每個錯誤類型，您可以依網域顯示錯誤訊息的劃分。

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

此報表的第二節以值表和圖表的形式，顯示每個網際網路網域的錯誤劃分。

對於每個域名，我們有：

* 此域有錯誤的消息數，
* 此域有錯誤的消息數與為此域處理的消息總數的百分比，
* 此域的錯誤消息與錯誤消息總數的百分比。

您可以按一下[+]符號，以開啟值表的每一行。 對於每種網域類型，您可以依錯誤類型顯示錯誤訊息的劃分。

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>此報告中顯示的域名在多維資料集級別定義。 要更改這些值，請編輯&#x200B;**[!UICONTROL Delivery logs (broadlogrcp)]**&#x200B;多維資料集。 如需詳細資訊，請參閱[本章節](../../reporting/using/about-cubes.md)。**[!UICONTROL Others]**&#x200B;類別包含不屬於特定類的域名。

## 瀏覽器 {#browsers}

此報表顯示傳送收件者在相關期間使用之網際網路瀏覽器的劃分。

>[!NOTE]
>
>此報告中顯示的值是估計值：只有已點按傳送的收件者才會納入考量。

**全局統計**

有關瀏覽器使用的全域統計資料以值表和圖表的形式呈現。

![](assets/dlv_explorers_report.png)

已使用下列指標：

* **[!UICONTROL Visitors]** :已定位（每個網際網路瀏覽器）且至少按一下傳送一次的收件者總數。
* **[!UICONTROL Pages viewed]** :所有傳送中，傳送中連結的點按總數（每個網際網路瀏覽器）。
* **[!UICONTROL Usage rate]** :此比率代表訪客總數（每個網際網路瀏覽器）的劃分。

**每個瀏覽器的統計資訊**

在全域統計值表格中，您可以按一下每個瀏覽器名稱以檢視其使用量統計資料。

![](assets/s_ncs_user_explorers_report2.png)

統計資料以曲線、圖表和值表的形式顯示。

**[!UICONTROL History]**&#x200B;曲線代表此瀏覽器每天的出勤率。 此比率是每天（在此瀏覽器上）訪客數量與以最高出席率測量的訪客數量之比。

**[!UICONTROL Breakdown per version]**&#x200B;圖表代表每個版本的訪客劃分，與訪客總數（在此瀏覽器上）比較。

值表使用下列指標：

* **[!UICONTROL Global rate]** :此比率代表每個版本的訪客劃分，與訪客總數（在所有瀏覽器上）比較。
* **[!UICONTROL Relative rate]** :此比率代表每個版本的訪客劃分，與訪客總數（在此瀏覽器上）比較。

### 共用至社交網路{#sharing-to-social-networks}

病毒式行銷可讓傳遞收件者與其聯絡網路共用資訊：他們可以將連結新增至其設定檔(Facebook、Twitter等) 或者給朋友發個資訊。 傳送內會追蹤每個共用和每個對共用資訊的存取。 如需病毒式行銷的詳細資訊，請參閱[此區段](../../delivery/using/viral-and-social-marketing.md)。

此報表顯示每個社交網路(Facebook、Twitter等)之已共用和已開啟訊息的劃分 和/或每封電子郵件。

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

在電子郵件傳送統計資料中，會顯示兩個值：

* **[!UICONTROL Number of messages to be delivered]** :傳遞分析期間處理的訊息總數。
* **[!UICONTROL Number of successful deliveries]** :已成功處理的郵件數。

**[!UICONTROL Sharing activities and mail open statistics]**

中央表格顯示電子郵件共用和開啟的統計資料。

在&#x200B;**[!UICONTROL Shares]**&#x200B;欄中，我們有下列指標：

* **[!UICONTROL No. of sharing activities]** :每個社交網路上共用的訊息總數。此值等於相符&#x200B;**[!UICONTROL Links for sharing to social networks]**&#x200B;個人化區塊圖示的點按總數。
* **[!UICONTROL Breakdown]** :此比率代表每個社交網路的分享次數，與分享總數的關係。
* **[!UICONTROL Sharing rate]** :此比率代表每個社交網路分享次數的劃分，與要傳送的訊息數量相關。

在&#x200B;**[!UICONTROL Opens]**&#x200B;欄中，我們有下列指標：

* **[!UICONTROL No. of opens]** :由轉送訊息的對象（透過個人化區塊）開啟的 **[!UICONTROL Links for sharing to social networks]** 訊息總數。此值等於鏡像頁面的顯示次數。 傳送收件者開啟的次數不會納入考量。
* **[!UICONTROL Breakdown]** :此比率代表每個社交網路的開啟次數，與開啟總次數的關聯。
* **[!UICONTROL Rate of opens]** :此比率代表每個社交網路的開啟次數，與分享總數相關。

**[!UICONTROL Breakdown of sharing activities and opens]**

本節包含兩個圖表，分別代表分享活動的劃分和每個社交網路開啟的次數。

## 共用活動統計資料{#statistics-on-sharing-activities}

此報表顯示分享至社交網路(Facebook、Twitter、電子郵件等)的演變 及時。

如需病毒式行銷的詳細資訊，請參閱[此區段](../../delivery/using/viral-and-social-marketing.md)。

![](assets/s_ncs_user_social_report2.png)

統計資料以值表和圖表的形式顯示。

已使用下列指標：

* **[!UICONTROL New contacts]** :接收透過電子郵件共用的訊息後的新訂閱數。此值與收到透過電子郵件共用的訊息、按一下&#x200B;**[!UICONTROL Subscription link]**&#x200B;並填入訂閱表單的人數相符。
* **[!UICONTROL Opens]** :由傳送訊息的對象（透過個人化區塊）開啟的訊 **[!UICONTROL Link for sharing to social networks]** 息總數。此值等於鏡像頁面的顯示次數。 傳送收件者開啟的次數不會納入考量。
* **[!UICONTROL Sharing activities]** :透過社交網路共用的訊息總數。此值與&#x200B;**[!UICONTROL Links for sharing to social networks]**&#x200B;個人化區塊圖示的點按總數相符。

## 作業系統 {#operating-systems}

此報表顯示傳送收件者在相關期間所使用的作業系統劃分。

>[!NOTE]
>
>此報告中顯示的值是估計值：只有已點按傳送的收件者才會納入考量。

**全局統計**

作業系統的全局使用統計資料以值表和圖表的形式顯示。

![](assets/s_ncs_user_os_report.png)

已使用下列指標：

* **[!UICONTROL Visitors]** :每日點按傳遞至少一次之目標收件者總數（每個作業系統）的平均值。
* **[!UICONTROL Pages viewed]** :所有傳送的傳送連結點按總次數（每個作業系統）的每日平均值。
* **[!UICONTROL Rate of use]** :此比率代表訪客總數（依作業系統）的劃分。

**每個作業系統的統計資訊**

在全局統計值表中，按一下每個作業系統的名稱以查看每個作業系統的統計資訊。

![](assets/s_ncs_user_os_report2.png)

統計資料以曲線、圖表和值表的形式顯示。

**[!UICONTROL History]**&#x200B;曲線表示此作業系統每天的使用率。 此比率是每天（在此作業系統上）訪客數量與在考勤率最高的當天所測量訪客數量的比率。

**[!UICONTROL Breakdown by version]**&#x200B;圖表代表每個版本的訪客劃分，與此作業系統上的訪客總數比較。

值表使用下列指標：

* **[!UICONTROL Global rate]** :此比率代表訪客（每個版本）與整個作業系統中訪客總數的劃分。
* **[!UICONTROL Relative rate]** :此比率代表訪客（每個版本）與此作業系統的訪客總數之比較。

## 訂閱追蹤{#subscription-tracking}

此報告可讓您監視資訊服務的訂閱。 它會顯示訂閱和取消訂閱。

![](assets/s_ncs_user_services_report.png)

按一下首頁的&#x200B;**[!UICONTROL Profiles and targets > Services and subscriptions]**&#x200B;節點或瀏覽器，即可針對訂閱顯示訂閱。 選擇所需訂閱，然後按一下&#x200B;**[!UICONTROL Reports]**&#x200B;頁簽。 預設可用&#x200B;**[!UICONTROL Subscriptions tracking]**&#x200B;報告。 它可讓您查看訂閱和取消訂閱趨勢，以及一段時間內的忠誠度。 您可以透過下拉式清單來設定此資料的表示方式。 按一下&#x200B;**[!UICONTROL Refresh]**&#x200B;以驗證所選配置。

如需詳細資訊，請參閱[本頁面](../../delivery/using/managing-subscriptions.md)。

**[!UICONTROL Number subscribed to date]**&#x200B;代表目前訂閱的總人數。

**[!UICONTROL Overall evolution of subscriptions]**

值表使用下列指標：

* **[!UICONTROL Subscribers]** :有關期間的訂戶總數。
* **[!UICONTROL Subscriptions]** :有關期間的訂閱數。
* **[!UICONTROL Unsubscriptions]** :有關期間的取消訂閱數。
* **[!UICONTROL Evolution]** :取消訂閱的數量減去訂閱的數量。此比率是根據訂閱者總數計算。
* **[!UICONTROL Loyalty]** :相關期間的訂閱者忠誠度。

**[!UICONTROL Subscription evolution curves]**

此圖表顯示相關期間訂閱和取消訂閱的演變。

## 傳送統計資料{#delivery-statistics}

此報表依網際網路網域、處理及傳送的所有訊息、硬退信、開啟、點按和取消訂閱顯示劃分。

![](assets/s_ncs_user_broadcast_report.png)

已使用下列指標：

* **[!UICONTROL Emails processed]** :傳送伺服器處理的訊息總數。
* **[!UICONTROL Delivered]** :成功處理的訊息數與已處理訊息總數的百分比。
* **[!UICONTROL Hard bounces]** :「硬」退信數與已處理訊息總數的百分比。
* **[!UICONTROL Soft bounces]** :「軟」彈回數與已處理訊息總數的百分比。

   >[!NOTE]
   >
   >有關硬跳出和軟跳出的詳細資訊，請參閱[隔離管理](../../delivery/using/understanding-quarantine-management.md)。

* **[!UICONTROL Opens]** :至少開啟一次訊息的目標收件者數目與成功處理之訊息數目的百分比。
* **[!UICONTROL Clicks]** :至少按一下傳送一次的人數百分比，與成功處理的訊息數量相比。
* **[!UICONTROL Unsubscription]** :取消訂閱連結的點按次數與成功處理的訊息次數的百分比。

## 開啟次數{#breakdown-of-opens}

此報表依作業系統、裝置和瀏覽器顯示相關期間的開啟次數劃分。 對於每個類別，會使用兩個圖表。 第一個會顯示有關電腦和行動裝置上開啟的統計資料。 第二個則只顯示與行動裝置上開啟次數相關的統計資料。

開啟的次數與已開啟的訊息總數相對應。 不會計算文字格式電子郵件。 如需「追蹤」開啟的詳細資訊，請參閱[「追蹤開啟的](../../reporting/using/indicator-calculation.md#tracking-opens-)」區段。

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>瀏覽器和作業系統名稱構成瀏覽器使用者代理所傳送且已開啟訊息的資訊的一部分。 Adobe Campaign利用其裝置資訊來推導裝置類型。
