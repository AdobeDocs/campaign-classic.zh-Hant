---
title: 監控傳送
seo-title: 監控傳送
description: 監控傳送
seo-description: null
page-status-flag: never-activated
uuid: 7cb409eb-a01c-4b4d-bb62-760e0bafdc8a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
discoiquuid: 3aab3d47-76fd-4c68-add4-9c14240c936e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4c4e2cfaa9603c42e5e97de1e13318f8541921ca

---


# 監控傳送{#monitoring-a-delivery}

傳送 **控制面板** ，是監控傳送以及傳送訊息時最終遇到的問題的關鍵。

**相關主題**

* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
* [瞭解隔離管理](../../delivery/using/understanding-quarantine-management.md)
* [提供最佳實務](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html)
* [快速入門：管理傳遞能力](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html)

## 傳送控制面板 {#delivery-dashboard}

若要檢視傳送的資訊，請加以編輯、檢視控制面板，然後按一下可用的標籤。

傳送後，標籤內容不再變更。

![](assets/s_ncs_user_del_details.png)

### 傳送摘要 {#delivery-summary}

此標 **[!UICONTROL Summary]** 簽包含傳送的特性：傳送狀態、使用的頻道、傳送者的資訊、主旨、執行的相關資訊。 有關詳細資訊，請參 [閱已發送的消息數](#number-of-messages-sent)。

此連 **[!UICONTROL reports]** 結可讓您檢視一組與傳送動作相關的報表：一般傳送報表、詳細報表、傳送報表、失敗訊息的分發、開啟率、點按次數和交易等。 此標籤的內容可依您的需求進行設定。 有關更多資訊，請參見[本節](../../reporting/using/delivery-reports.md)。

### 傳送記錄檔和記錄 {#delivery-logs-and-history}

此標 **[!UICONTROL Delivery]** 簽會列出此傳送中的發生次數記錄。 它包含傳送記錄，即已傳送訊息的清單、其狀態及相關訊息。

對於傳送，您只能顯示（例如）傳送失敗或隔離中有地址的收件者。 若要這麼做，請按一下按 **[!UICONTROL Filters]** 鈕並選取 **[!UICONTROL By state]**。 然後在下拉式清單中選取狀態。

![](assets/s_ncs_user_delivery_delivery_tab.png)

本頁列出各種 [狀態](#delivery-statuses)。

>[!NOTE]
>
>此 **[!UICONTROL Display the mirror page for this message...]** 連結可讓您在新視窗中檢視從清單選取之傳送內容的鏡像頁面。 鏡像頁面僅適用於已定義HTML內容的傳送。 有關詳細資訊，請參閱 [生成鏡像頁](../../delivery/using/sending-messages.md#generating-the-mirror-page)。

### Tracking logs {#tracking-logs}

標籤 **[!UICONTROL Tracking]** 會列出此傳送的追蹤歷史記錄。 此標籤會顯示所傳送訊息的追蹤資料，亦即所有受Adobe Campaign追蹤的URL。 追蹤資料會每小時更新一次。

>[!NOTE]
>
>如果傳送未啟用追蹤，則不會顯示此標籤。

追蹤設定是在傳送精靈的適當階段執行。 請參 [閱如何設定追蹤的連結](../../delivery/using/how-to-configure-tracked-links.md)。

**[!UICONTROL Tracking]** 資料會在傳送報表中解譯。 請參 [閱本節](../../reporting/using/delivery-reports.md)。

![](assets/s_ncs_user_delivery_tracking_tab.png)

### 傳送審核 {#delivery-audit-}

此標 **[!UICONTROL Audit]** 簽包含傳送記錄檔和所有與校樣相關的訊息。 此按 **[!UICONTROL Refresh]** 鈕可讓您更新資料。 使用按 **[!UICONTROL Filters]** 鈕可定義資料的篩選。

特殊圖示可讓您識別錯誤或警告。 請參閱 [分析傳送](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

子標 **[!UICONTROL Proofs]** 簽可讓您檢視已傳送校樣的清單。

![](assets/s_ncs_user_delivery_log_tab.png)

通過選擇要顯示的列，可以修改此窗口(以及 **[!UICONTROL Delivery]** 和 **[!UICONTROL Tracking]** 頁籤的資訊)中顯示的資訊。 若要這麼做，請按 **[!UICONTROL Configure list]** 一下右下角的圖示。 如需設定清單顯示的詳細資訊，請參閱 [本節](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

### 傳送控制面板同步化 {#delivery-dashboard-synchronization}

在您的傳送控制面板中，您要檢查已處理的訊息和傳送記錄，以確定傳送成功。

某些指標或狀態可能不正確或不是最新，這可透過下列解決方案解決：

* 如果您的傳送狀態不正確，請檢查是否已完成此傳送的所有必要核准，或是執行 **[!UICONTROL operationMgt]** 和工 **[!UICONTROL deliveryMgt]** 作流程時未出現錯誤。 這也可能是因為傳送時使用了傳送執行個體上未設定的相似性。
* 如果您的交貨指標仍為零，並且您處於中間採購配置中，請檢查技術工 **[!UICONTROL Mid-sourcing (delivery counters)]** 作流程。 如果狀態不是，請啟動它 **[!UICONTROL Started]**。 然後，您可以嘗試在Adobe Campaign瀏覽器中按一下滑鼠右鍵並選取 **[!UICONTROL Actions]** >，重新計算指標 **[!UICONTROL Recompute delivery and tracking indicators]**。 For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* 如果您的傳送計數器與您的傳送不符，請嘗試在Adobe Campaign檔案總管中以滑鼠右鍵按一下相關傳送，然後選取 **[!UICONTROL Actions]** > **[!UICONTROL Recompute delivery and tracking indicators]** 重新同步。 For more information on tracking indicators, refer to this [section](../../reporting/using/delivery-reports.md#tracking-indicators).
* 如果您的傳送計數器不是中部採購部署的最新版本，請檢查技術工作 **[!UICONTROL Mid-Sourcing (Delivery counters)]** 流程是否正在執行。 For more on this, refer to this [page](../../installation/using/mid-sourcing-deployment.md).

您也可以透過傳送控制面板，使用不同的報表來追蹤傳送。 For more on this, refer to this [section](../../reporting/using/delivery-reports.md).

## 效能問題 {#performance-issues}

### 檢查清單 {#checklist-}

如果傳送效能不佳，您可以檢查：

* **傳送的大小**:大型傳送可能需要更長的時間才能完成。 MTA子系設定為處理預設批次大小，這適用於大部分的例項，但傳送速度持續緩慢時，需要加以檢查。
* **傳送的目標**:傳送效能禁止受到軟反彈錯誤的影響，這些錯誤會根據重試設定進行處理。 錯誤數越多，則需要重試的次數越多。
* **整體平台負載**:當傳送數個大型傳送時，整體平台可能會受到影響。 您也可以檢查IP信譽和傳遞性問題。 如需詳細資訊，請參閱Adobe Campaign [Deliverability最佳實務指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) ，以 [及本頁](../../delivery/using/about-deliverability.md)。

平台與資料庫維護也會影響傳送傳送的效能。 有關詳細資訊，請參見[此頁面](../../production/using/database-performances.md)。

### 傳送速度緩慢 {#slow-deliveries}

按一下按 **[!UICONTROL Send]** 鈕後，您的傳送似乎比往常花了更長的時間。 這可能是由不同的元素所造成：

* 有些電子郵件提供者可能已將您的IP位址列入黑名單。 在這種情況下，請檢查您的廣播，並參 [閱此快速入門](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) 。
* 您的傳送量可能太大，無法快速處理，這可能是透過高度的JavaScript個人化，或是您的傳送量超過60KB而發生。 請參閱Adobe Campaign傳遞 [最佳實務](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliveryBestPractices.html) ，以瞭解內容准則。
* Adobe Campaign MTA中可能已發生調節。 這是由以下原因造成：

   * 附加的消息(**[!UICONTROL quotas met]** 消息):已符合Campaign中定義的宣告性MX規則所宣告的配額。 For more information about this message, refer to [this page](https://helpx.adobe.com/campaign/kb/acc-deliverability-faq.html#FAQ). 若要進一步瞭解MX規則，請參 [閱本頁](../../delivery/using/technical-recommendations.md#mx-rules)。
   * 附加的消息(**[!UICONTROL dynamic flow control]** 消息):Campaign MTA嘗試傳送給特定ISP的訊息時發生錯誤，造成延遲，以避免錯誤密度過大，因而面臨潛在黑名單。

* 系統問題可能會阻止伺服器進行交互：這會拖慢整個傳送程式。 檢查伺服器，以確保沒有記憶體或資源問題，例如在取得個人化資料的過程中會影響促銷活動。

### 最佳效能實務 {#best-practices-performance}

* 請勿在實例上將交貨保持為失敗狀態，因為這會維護臨時表並影響效能。

* 移除不再需要的傳送。

* 過去12個月中非活動的收件者將從資料庫中刪除，以保持地址質量。

* 請勿嘗試排程大型傳送。 在系統上均勻分配負載需要5-10分鐘。 與團隊中的其他成員協調交貨排程，以確保最佳效能。 當行銷伺服器同時處理許多不同的工作時，可能會降低效能。

* 盡量將電子郵件的大小保持在最低。 建議的電子郵件大小上限為35KB。 電子郵件傳送的大小會在傳送伺服器中產生一定數量的卷。

* 大型傳送（例如傳送給超過1百萬個收件者）需要在傳送佇列中有空間。 僅此一項對伺服器而言並不是問題，但是，當搭配數十種其他大型傳送裝置同時進行時，可能會造成傳送延遲。

* 電子郵件中的個人化會從資料庫中提取每個收件者的資料。 如果有許多個人化元素，會增加準備傳送所需的資料量。

* 索引地址。 要優化應用程式中使用的SQL查詢的效能，可以從資料模式的主元素中聲明索引。

>[!NOTE]
>
>ISP會在閒置一段時間後停用位址。 已退回的訊息會傳送給寄件者，通知他們此新狀態。

## 傳送狀態 {#delivery-statuses}

傳送傳送時，您可能會在傳送控制面板上面臨下列狀態：

<table> 
 <thead> 
  <tr> 
   <th> 狀態<br /> </th> 
   <th> 定義與解決方案<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 不適用<br /> </td> 
   <td> 伺服器(MTA)已考慮傳送，但未處理。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已忽略<br /> </td> 
   <td> 由於收件者的地址發生錯誤，因此未將傳送內容傳送給收件者。 它被列入黑名單、隔離、未提供或複製。 <br /> </td> 
  </tr> 
  <tr> 
   <td> 已傳送<br /> </td> 
   <td> 傳送內容已正確傳送給訊息提供者（但收件者不一定會收到）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 失敗<br /> </td> 
   <td> 例如，由於地址無效或收件匣已滿，傳送無法送達收件者。 它也可以連結至個人化區塊的問題，因為當結構不符合傳送對應時，這些區塊會產生錯誤。 請參閱 <a href="#failed-status" target="_blank">失敗狀態</a><br /> </td> 
  </tr> 
  <tr> 
   <td> 服務提供者已考慮到<br /> </td> 
   <td> SMS服務提供商收到了發送。<br /> </td> 
  </tr> 
  <tr> 
   <td> 在行動裝置上收到<br /> </td> 
   <td> 收件者在其行動裝置上收到SMS。<br /> </td> 
  </tr> 
  <tr> 
   <td> 待定<br /> </td> 
   <td> 傳送已準備好可傳送，且將由傳送伺服器(MTA)處理。 請參 <a href="#pending-status" target="_blank">閱待定狀態</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 已取消傳送<br /> </td> 
   <td> 交貨已由營運商取消。<br /> </td> 
  </tr> 
  <tr> 
   <td> 準備好<br /> </td> 
   <td> 中介狀態僅用於外部連接器，例如行動頻道。 它遵循「待定」狀態，是決定下列狀態的外部連接器。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傳送至服務供應商<br /> </td> 
   <td> 傳送內容已傳送至SMS服務供應商，但尚未收到。<br /> </td> 
  </tr> 
 </tbody> 
</table>

如要瞭解如何最佳化Adobe Campaign電子郵件的傳遞能力，請參閱Adobe Campaign [Deliverability最佳實務指南](https://docs.campaign.adobe.com/doc/AC/getting_started/EN/deliverability.html) ，以 [及本頁](../../delivery/using/about-deliverability.md)。

### 待定狀態 {#pending-status}

在確認您的傳送後，您會看到傳送狀態為 **[!UICONTROL Pending]**。 此狀態表示執行進程正在等待某些資源的可用性。

狀 **[!UICONTROL Pending]** 態可以先表示您的傳送已排程，且待定至指定日期。 如需詳細資訊，請參閱「傳送 [排程」](../../delivery/using/steps-sending-the-delivery.md#scheduling-the-delivery-sending) 。

如果您的傳送未傳送且其狀態仍 **[!UICONTROL Pending]**&#x200B;然維持，則可能是：

* 在傳送伺服器上執行模組和程式並管理電子郵件傳送的MTA（訊息傳送代理）可能尚未啟動，或需要重新啟動。 要檢查此問題並在必要時啟動模組，請應用以下步驟：

   * 檢查您的 `mta@<instance>` 模組是否已在MTA伺服器上啟動。

   ```
   nlserver pdump
   HH:MM:SS > Application server for Adobe Campaign Classic (X.Y.Z YY.R build nnnn@SHA1) of DD/MM/YYYY
   [...]
   mta@<INSTANCENAME> (9268) - 23.0 Mb
   [...]
   ```

   * 如果未列出MTA，請使用下列命令啟動它：

   ```
   nlserver start mta@<INSTANCENAME>
   ```

   >[!NOTE]
   >
   >以 `<INSTANCENAME>` 例項名稱取代（生產、開發等）。 實例名稱通過配置檔案標識： `[path of application]nl6/conf/config-<INSTANCENAME>.xml`

* 傳送可能使用未在傳送伺服器上設定的相似性。 在此例中，請檢查流量管理（IP相似性）的設定，並使用欄 **[!UICONTROL Managing affinities with IP addresses]** 位將傳送連結至管理相似性的MTA。 For more information on affinities, refer to [this section](../../installation/using/configuring-campaign-server.md#personalizing-delivery-parameters).
* 當傳送準備擱置中時，可能會執行太多促銷活動，因而封鎖傳送的狀態更新。 若要解決此問題，請 **[!UICONTROL Options]** 移至並增加值(預 **[!UICONTROL NmsOperation_LimitConcurrency]** 設值為10)。 請勿執行指派給此特定選項的值以外的促銷活動。

### 失敗狀態 {#failed-status}

如果電子郵件傳送的狀態 **[!UICONTROL Failed]**&#x200B;為，則可連結至個人化區塊的問題。 例如，當結構不符合傳送對應時，傳送中的個人化區塊可能會產生錯誤。

傳送記錄檔是瞭解傳送失敗原因的關鍵。 您可從傳送記錄中偵測到以下可能錯誤：

* 如果收件者訊息失敗，並出現「無法存取」錯誤，指出：編 **譯指令碼&#39;content htmlContent&#39;行X時出錯：未`[table]`定義。 JavaScript:評估指令碼&#39;content htmlContent**&#39;時出錯，此問題的原因幾乎總是HTML中的個人化，嘗試呼叫未在上游定位或傳送的目標對應中定義或映射的表或欄位。

   為了修正此問題，必須審查工作流程和傳送內容，以明確決定個人化嘗試呼叫相關表格的方式，以及表格是否可以映射。 在此處，移除HTML中對此表格的呼叫或修正對應至傳送，都是解析的路徑。

* 在中部採購部署模型中，傳送記錄檔中會顯示下列訊息：在 **中間採購伺服器上調用方法&#39;AppendDeliveryPart&#39;時出錯：&#39;與伺服器的通信錯誤：請檢查此項設定是否正確。 代碼HTTP 408 &#39;服務暫時不可用&#39;**。

   原因與效能問題有關。 這表示行銷實例在將資料傳送至中端來源伺服器之前，會花費太多時間建立資料。

   為解決此問題，我們建議對資料庫執行真空並重新索引。 For more information on database maintenance, refer to [this section](../../production/using/recommendations.md).

   您也應以排程的活動重新啟動所有工作流程，並且所有工作流程都處於失敗狀態。 Refer to [this section](../../workflow/using/scheduler.md).

* 當傳送失敗時，傳送記錄中可能會出現下列錯誤： **DLV-XXXX準備的消息數(123)大於要發送的消息數(111)。 請聯絡支援。**

   通常，此錯誤表示電子郵件中有個人化欄位或區塊，其中包含收件者的多個值。 個人化區塊正在使用中，它正在為特定接收者擷取多個記錄。

   若要解決此問題，請檢查使用的個人化資料，然後檢查針對任何欄位有多個項目的收件者的目標。 您也可以在傳送活 **[!UICONTROL Deduplication]** 動之前，在定位工作流程中使用活動，以檢查一次只有一個個人化欄位。 For more information on deduplication, refer to [this page](../../workflow/using/deduplication.md).

* 某些傳送可能失敗，並出現「無法連線」錯誤，指出：&quot;入站電子郵件彈回數（規則&#39;Auto_replies&#39;已符合此彈回數）。 這表示傳送成功，但Adobe Campaign卻收到來自收件者的自動回覆（例如「不在辦公室」回覆），符合「Auto_ryples」傳入電子郵件規則。 Adobe Campaign會忽略自動回覆電子郵件，而且不會將收件者的位址傳送至隔離。

**相關主題：**

* [傳送記錄檔和記錄](#delivery-logs-and-history)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
* [傳送失敗類型和原因](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)

## 已發送的消息數 {#number-of-messages-sent}

您可以透過樹狀結構的節點，從傳送清單 **[!UICONTROL Campaign Management > Deliveries]** 存取傳送。

依預設，傳送清單會包含所選節點中建立之傳送的名稱和狀態。 它還顯示成功發送、處理和發送的消息數。

* 數目與分 **[!UICONTROL Messages to send]** 析後和傳送前的目標收件者數目相對應。
* 列中的消息數與服 **[!UICONTROL success]** 務器發送的、接收者接收的消息數相對應。
* 消息數 **[!UICONTROL processed]** 與收到的消息數以及出錯消息數相對應。

傳送控制面板可讓您追蹤傳送的訊息數目。

>[!NOTE]
>
>若是大型傳送，您可能想要更新這些值。 若要這麼做，請選取相關的傳送，然後以滑鼠右鍵按一下。 選 **[!UICONTROL Action > Recompute delivery and tracking indicators...]** 擇，然後使用嚮導更新此資訊。

## 排程的傳送 {#scheduled-deliveries-}

如果傳送未在精確的排程日期執行，則可能與伺服器時區之間的差異相關。 中間來源補充實例和生產實例可以位於不同的時區。

例如，如果中間採購實例位於布里斯班時區，生產實例位於達爾文時區，兩個時區彼此相距半小時，那麼在審計日誌中，您會清楚地看到，如果中間採購實例排程在11:56生產，那麼中間採購實例排程在12:26的交貨將相差半小時。
