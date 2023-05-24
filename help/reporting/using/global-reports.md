---
product: campaign
title: 全域報告
description: 全域報告
badge: label="v7" type="資訊性" tooltip="僅適用於Campaign Classicv7"
feature: Reporting, Monitoring
exl-id: 6839fd7e-ecf4-4504-90a8-0207bc3991e4
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '2304'
ht-degree: 8%

---

# 全域報告 {#global-reports}



這些報表會涉及整個資料庫中的資料活動。 若要檢視報表控制面板，請前往 **[!UICONTROL Reports]** 標籤。

![](assets/s_ncs_user_report_delivery_link.png)

若要顯示報表，請按一下其名稱。 預設可使用下列報表：

![](assets/s_ncs_user_report_global_list.png)

>[!NOTE]
>
>此區段僅顯示連結至傳遞的報告。

* **[!UICONTROL Delivery throughput]** ：請參閱 [傳遞總處理能力](#delivery-throughput).
* **[!UICONTROL Browsers]** ：請參閱 [瀏覽器](#browsers).
* **[!UICONTROL Sharing to social networks]** ：請參閱 [分享至社交網路](#sharing-to-social-networks).
* **[!UICONTROL Statistics on sharing activities]** ：請參閱 [共用活動的統計資料](#statistics-on-sharing-activities).
* **[!UICONTROL Operating systems]** ：請參閱 [作業系統](#operating-systems).
* **[!UICONTROL URLs and click streams]** ：請參閱 [URL和點按資料流](../../reporting/using/delivery-reports.md#urls-and-click-streams).
* **[!UICONTROL Tracking indicators]** ：請參閱 [追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators).
* **[!UICONTROL Non-deliverables and bounces]** ：請參閱 [無法傳遞的專案和退信](#non-deliverables-and-bounces).
* **[!UICONTROL User activities]** ：請參閱 [使用者活動](#user-activities).
* **[!UICONTROL Subscription tracking]** ：請參閱 [訂閱追蹤](#subscription-tracking).
* **[!UICONTROL Delivery summary]** ：請參閱 [傳遞摘要](../../reporting/using/delivery-reports.md#delivery-summary).
* **[!UICONTROL Delivery statistics]** ：請參閱 [傳遞統計資料](#delivery-statistics).
* **[!UICONTROL Breakdown of opens]** ：請參閱 [開啟的劃分](#breakdown-of-opens).

## 傳遞總處理能力 {#delivery-throughput}

此報表包含指定期間內整個平台的傳遞輸送量資訊。 若要測量訊息傳遞的速度，標準是每小時傳送的訊息數和訊息的大小 (以位元/秒為單位)。在下面的範例中，第一個圖表以藍色顯示成功傳遞，以橘色顯示錯誤傳遞的數量。

![](assets/s_ncs_user_report_toolbar.png)

您可以透過變更時間表來設定顯示的值：1小時檢視、3小時檢視、24小時檢視等。 按一下 **[!UICONTROL Refresh]** 以確認您的選取。

>[!NOTE]
>
>如果您的執行個體託管在AWS上，您也可以使用Campaign Classic監控每小時傳送的傳遞數量 [控制面板](https://experienceleague.adobe.com/docs/control-panel/using/sftp-management/sftp-storage-management.html). 若要檢查您的執行個體是否託管在 AWS 上，請按照[本頁面](https://experienceleague.adobe.com/docs/control-panel/using/faq.html)詳述的步驟操作。
>
>所有管理員使用者都可存取控制面板。 授予使用者管理員存取權限的步驟已詳載於[本頁](https://experienceleague.adobe.com/docs/control-panel/using/discover-control-panel/managing-permissions.html?lang=zh-Hant#discover-control-panel)中。
>
>請注意，您的執行個體必須升級為最新的 [Gold Standard](../../rn/using/gold-standard.md) 建置或 [最新GA版本編號(21.1.3)](../../rn/using/latest-release.md). 在[本章節](../../platform/using/launching-adobe-campaign.md#getting-your-campaign-version)中瞭解如何確認您的版本。 

## 使用者活動 {#user-activities}

此報表以圖表形式顯示每半小時、每小時或每日的開啟、點按和交易劃分。

![](assets/s_ncs_user_user_report.png)

可以使用以下選項：

* **[!UICONTROL Opens]** ：已開啟的訊息總數。 未考慮文字格式的電子郵件。 如需追蹤開啟的詳細資訊，請參閱 [追蹤開啟次數](../../reporting/using/indicator-calculation.md#tracking-opens-).
* **[!UICONTROL Clicks]** ：傳遞中連結的點按總數。 對取消訂閱連結和映象頁面的點選次數不會考慮在內。
* **[!UICONTROL Transactions]** ：收到訊息後的交易總數。 若要將交易列入考量，必須將交易型別Web追蹤標籤插入相符的網頁中。 網路追蹤設定在中顯示 [本節](../../configuration/using/about-web-tracking.md).

## 傳遞失敗和退回次數 {#non-deliverables-and-bounces}

此報表顯示無法傳遞的專案的劃分以及每個網域退信的劃分。

此 **[!UICONTROL Number of messages processed]** 代表傳遞伺服器處理的訊息總數。 此值低於某些傳遞已停止或暫停（在伺服器處理之前）時要傳遞的訊息數。

![](assets/s_ncs_user_errors_report.png)

**[!UICONTROL Breakdown of errors by type]**

>[!NOTE]
>
>此報告中顯示的錯誤會觸發隔離程式。 如需隔離管理的詳細資訊，請參閱 [隔離管理](../../delivery/using/understanding-quarantine-management.md).

此報表的第一區段以值表格和圖表的形式顯示無法傳遞專案的劃分。

對於每個錯誤型別，我們有：

* 此型別的錯誤訊息數目，
* 此型別出現錯誤的訊息佔出現錯誤的訊息總數的百分比，
* 此型別的錯誤訊息佔已處理訊息總數的百分比。

使用下列指標：

* **[!UICONTROL User unknown]** ：傳送期間產生的錯誤型別，表示電子郵件地址無效。
* **[!UICONTROL Invalid domain]** ：傳送傳遞時產生的錯誤型別，指出電子郵件地址的網域錯誤或不存在。
* **[!UICONTROL Inbox full]** ：在嘗試傳送五次後產生的錯誤型別，以指出收件者的收件匣包含太多郵件。
* **[!UICONTROL Account disabled]** ：傳送傳遞時產生的錯誤型別，用以指出地址已不存在。
* **[!UICONTROL Rejected]** ：當IAP （網際網路存取提供者）拒絕位址時產生的錯誤型別，例如在套用安全性規則（反垃圾郵件軟體）之後。
* **[!UICONTROL Unreachable]** ：訊息發佈字串中發生的錯誤型別：SMTP轉送上的事件、暫時無法連線網域等
* **[!UICONTROL Not connected]** ：錯誤型別，表示收件者的行動電話在傳送時已關閉或已中斷與網路的連線。

   >[!NOTE]
   >
   >此指標僅與行動裝置頻道上的傳送有關。 如需詳細資訊，請參閱[本章節](../../delivery/using/sms-channel.md)。

   您可以按一下「 」，開啟數值表格的每一行 `[+]` 符號。 對於每個錯誤型別，您可以依網域顯示錯誤訊息的劃分。

   ![](assets/s_ncs_user_errors_report_detail.png)

**[!UICONTROL Breakdown of errors per domain]**

此報表的第二部分以值表格和圖表的形式，顯示每個網域錯誤的劃分資訊。

對於每個網域名稱，我們有：

* 此網域有錯誤的訊息數，
* 這個網域出現錯誤的訊息佔這個網域已處理訊息總數的百分比，
* 此網域的錯誤訊息佔錯誤訊息總數的百分比。

您可以按一下「 」，開啟數值表格的每一行 [+] 符號。 對於每個網域型別，您可以依錯誤型別顯示錯誤訊息的劃分。

![](assets/s_ncs_user_errors_report_detail2.png)

>[!NOTE]
>
>此報告中顯示的網域名稱是在多維資料庫層級定義的。 若要變更這些值，請編輯 **[!UICONTROL Delivery logs (broadlogrcp)]** 立方體。 如需詳細資訊，請參閱[本章節](../../reporting/using/ac-cubes.md)。此 **[!UICONTROL Others]** 類別包括不屬於特定類別的網域名稱。

## 瀏覽器 {#browsers}

此報表顯示有關期間傳遞收件者使用的網際網路瀏覽器劃分。

>[!NOTE]
>
>此報表中顯示的值是預估值：只會考慮已點按傳送的收件者。

**全域統計資料**

瀏覽器使用的全域統計資料會以值表格和圖表的形式呈現。

![](assets/dlv_explorers_report.png)

使用下列指標：

* **[!UICONTROL Visitors]** ：已鎖定目標（每個網際網路瀏覽器）並已至少點按一次傳送的收件者總數。
* **[!UICONTROL Pages viewed]** ：所有傳送的傳送中連結點選總數（每個網際網路瀏覽器）。
* **[!UICONTROL Usage rate]** ：此比率代表訪客（每個網際網路瀏覽器）相對於訪客總數的劃分。

**每個瀏覽器的統計資料**

在全域統計值表格中，您可以按一下每個瀏覽器名稱來檢視其使用狀況統計值。

![](assets/s_ncs_user_explorers_report2.png)

統計資料會以曲線、圖表和值表的形式呈現。

此 **[!UICONTROL History]** 曲線代表此瀏覽器每日的出勤率。 此比率是每日訪客數（在此瀏覽器上）與最高出席率當日所測量訪客數的比率。

此 **[!UICONTROL Breakdown per version]** 圖表代表每個版本的訪客與訪客總數（在這個瀏覽器上）的比較。

值表使用下列指標：

* **[!UICONTROL Global rate]** ：此比率代表每個版本的訪客與訪客總數（在所有瀏覽器上）的比較。
* **[!UICONTROL Relative rate]** ：此比率代表每個版本的訪客與訪客總數（在此瀏覽器上）的比較。

### 分享至社交網路 {#sharing-to-social-networks}

病毒式行銷可讓傳遞收件者與其聯絡網路共用資訊：他們可以新增連結至其設定檔(Facebook、Twitter等) 或傳送訊息給朋友。 在傳遞中會追蹤共用資訊的每個共用和每個共用資訊存取。 如需病毒式行銷的詳細資訊，請參閱 [本節](../../delivery/using/viral-and-social-marketing.md).

此報表顯示每個社交網路(Facebook、Twitter等)的共用和開啟訊息劃分 和/或每封電子郵件。

![](assets/s_ncs_user_social_report.png)

**[!UICONTROL Email delivery statistics]**

在電子郵件傳遞統計資料中，會顯示兩個值：

* **[!UICONTROL Number of messages to be delivered]** ：傳遞分析期間處理的訊息總數。
* **[!UICONTROL Number of successful deliveries]** ：成功處理的訊息數。

**[!UICONTROL Sharing activities and mail open statistics]**

中央表格顯示電子郵件共用和開啟的統計資料。

在 **[!UICONTROL Shares]** 欄中，我們有以下指標：

* **[!UICONTROL No. of sharing activities]** ：在每個社交網路上共用的訊息總數。 此值等於相符專案圖示上的總點選次數 **[!UICONTROL Links for sharing to social networks]** 個人化區塊。
* **[!UICONTROL Breakdown]** ：此比率代表每個社交網路的股份總數。
* **[!UICONTROL Sharing rate]** ：此比率代表每個社交網路的股份劃分（與要傳送的訊息數量相關）。

在 **[!UICONTROL Opens]** 欄中，我們有以下指標：

* **[!UICONTROL No. of opens]** ：由訊息轉寄對象開啟的訊息總數(透過 **[!UICONTROL Links for sharing to social networks]** 個人化區塊)。 此值等於映象頁面顯示的次數。 傳遞收件者的開啟次數不會列入考量。
* **[!UICONTROL Breakdown]** ：此比率代表每個社交網路的開啟次數與開啟總數之間的細分。
* **[!UICONTROL Rate of opens]** ：此比率代表每個社交網路的開啟次數與共用總數之間的細分。

**[!UICONTROL Breakdown of sharing activities and opens]**

本節包含兩個圖表，分別代表共用活動和每個社交網路的開啟次數。

## 共用活動的統計資料 {#statistics-on-sharing-activities}

此報表說明分享至社交網路(Facebook、Twitter、電子郵件等)的進化 即時。

如需病毒式行銷的詳細資訊，請參閱 [本節](../../delivery/using/viral-and-social-marketing.md).

![](assets/s_ncs_user_social_report2.png)

統計資料會以值表格和圖表的形式呈現。

使用下列指標：

* **[!UICONTROL New contacts]** ：收到透過電子郵件共用的訊息後的新訂閱數目。 此值符合收到透過電子郵件共用的訊息，並按一下 **[!UICONTROL Subscription link]** 並填寫訂閱表單。
* **[!UICONTROL Opens]** ：訊息傳輸對象開啟的訊息總數(透過 **[!UICONTROL Link for sharing to social networks]** 個人化區塊)。 此值等於映象頁面顯示的次數。 傳遞收件者的開啟次數不會列入考量。
* **[!UICONTROL Sharing activities]** ：透過社交網路共用的訊息總數。 此值符合「 」的「 」圖示上 **[!UICONTROL Links for sharing to social networks]** 個人化區塊。

## 作業系統 {#operating-systems}

此報表顯示相關期間內傳遞收件者使用的作業系統劃分。

>[!NOTE]
>
>此報表中顯示的值是預估值：只會考慮已點按傳送的收件者。

**全域統計資料**

作業系統的全域使用狀況統計資料會以值表格和圖表的形式呈現。

![](assets/s_ncs_user_os_report.png)

使用下列指標：

* **[!UICONTROL Visitors]** ：在傳遞中至少點按一次的目標收件者總數（每個作業系統）的每日平均數。
* **[!UICONTROL Pages viewed]** ：所有傳送的傳送連結每日平均點按總數（每個作業系統）。
* **[!UICONTROL Rate of use]** ：此比率代表相對於訪客總數的訪客劃分（每個作業系統）。

**每個作業系統的統計資料**

在全域統計值表格中，按一下每個作業系統的名稱，即可檢視每個作業系統的統計值。

![](assets/s_ncs_user_os_report2.png)

統計資料會以曲線、圖表和值表的形式呈現。

此 **[!UICONTROL History]** 曲線代表每天使用此作業系統的速率。 此比率是每日訪客數（在此作業系統上）與最高出席人數當日所測量訪客數的比率。

此 **[!UICONTROL Breakdown by version]** 圖表代表每個版本的訪客相對於此作業系統上的訪客總數的劃分。

值表使用下列指標：

* **[!UICONTROL Global rate]** ：此比率代表訪客（每個版本）與整個作業系統的訪客總數之間的劃分。
* **[!UICONTROL Relative rate]** ：此比率代表此作業系統的訪客總數（每個版本）的劃分情況。

## 訂閱追蹤 {#subscription-tracking}

此報告可讓您監視資訊服務的訂閱。 它會顯示訂閱和取消訂閱。

![](assets/s_ncs_user_services_report.png)

按一下「 」以針對訂閱顯示 **[!UICONTROL Profiles and targets > Services and subscriptions]** 首頁節點或檔案總管。 選取所需的訂閱，然後按一下 **[!UICONTROL Reports]** 標籤。 此 **[!UICONTROL Subscriptions tracking]** 報告預設為可用。 它可讓您檢視一段期間的訂閱和取消訂閱趨勢以及忠誠度。 您可以透過下拉式清單設定此資料的表示方式。 按一下 **[!UICONTROL Refresh]** 驗證選取的組態。

如需詳細資訊，請參閱[本頁面](../../delivery/using/managing-subscriptions.md)。

此 **[!UICONTROL Number subscribed to date]** 代表目前訂閱的總人數。

**[!UICONTROL Overall evolution of subscriptions]**

值表使用下列指標：

* **[!UICONTROL Subscribers]** ：相關期間的訂閱者總數。
* **[!UICONTROL Subscriptions]** ：相關期間的訂閱數目。
* **[!UICONTROL Unsubscriptions]** ：相關期間的取消訂閱數。
* **[!UICONTROL Evolution]** ：取消訂閱數減去訂閱數。 此比率是根據訂閱者總數所計算。
* **[!UICONTROL Loyalty]** ：相關期間訂閱者的忠誠度比率。

**[!UICONTROL Subscription evolution curves]**

此圖表顯示相關期間的訂閱和取消訂閱的演變。

## 傳遞統計資料 {#delivery-statistics}

此報表顯示依網際網路網域、所有已處理和已傳送訊息、硬退信和軟退信、開啟、點按和取消訂閱的劃分資訊。

![](assets/s_ncs_user_broadcast_report.png)

使用下列指標：

* **[!UICONTROL Emails processed]** ：傳遞伺服器處理的訊息總數。
* **[!UICONTROL Delivered]** ：成功處理的訊息數相對於已處理訊息總數的百分比。
* **[!UICONTROL Hard bounces]** ：相對於已處理訊息總數的「硬」退回數百分比。
* **[!UICONTROL Soft bounces]** ：相對於已處理訊息總數的「軟」退回數百分比。

   >[!NOTE]
   >
   >如需硬跳出和軟跳出的詳細資訊，請參閱 [隔離管理](../../delivery/using/understanding-quarantine-management.md).

* **[!UICONTROL Opens]** ：至少開啟過一次訊息的目標收件者人數，與成功處理的訊息數目相比的百分比。
* **[!UICONTROL Clicks]** ：與成功處理的訊息數相比，已至少點按一次傳遞的人數百分比。
* **[!UICONTROL Unsubscription]** ：取消訂閱連結的點選次數與成功處理的訊息數之間的百分比。

## 開啟次數的劃分 {#breakdown-of-opens}

此報表顯示相關期間內依作業系統、裝置和瀏覽器劃分的開啟次數。 每個類別有兩個圖表。第一個圖表顯示在電腦和行動裝置上的開啟數統計資料。第二個圖表僅顯示在行動裝置上的開啟數統計資料。

開啟次數與開啟的訊息總數相對應。 不計算文字格式電子郵件。 如需追蹤開啟的詳細資訊，請參閱 [追蹤開啟次數](../../reporting/using/indicator-calculation.md#tracking-opens-) 區段。

![](assets/dlv_useragent_report.png)

>[!NOTE]
>
>瀏覽器和作業系統名稱構成了已向其開啟訊息之瀏覽器使用者代理程式所傳送的部分資訊。 Adobe Campaign會使用其裝置資訊來推斷裝置型別。
