---
solution: Campaign Classic
product: campaign
title: 疑難排解
description: 進一步瞭解傳送效能，以及如何疑難排解與傳送監控相關的問題。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: d1b38acc5209a5c96ab7a35fe9640159141b110f
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---


# 傳送傳送疑難排解{#delivery-troubleshooting}

本節列出傳送傳送時可能遇到的常見問題，以及如何進行疑難排解。

此外，請務必遵循[本頁](../../delivery/using/delivery-performances.md)中詳細說明的最佳實務和檢查清單，以確保您的傳送順利執行。

**相關主題：**

* [傳遞狀態](../../delivery/using/delivery-statuses.md)
* [傳遞儀表板](../../delivery/using/delivery-dashboard.md)
* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)

## 傳送速度緩慢{#slow-deliveries}

按一下&#x200B;**[!UICONTROL Send]**&#x200B;按鈕後，您的傳送似乎比往常花了更長的時間。 這可能是由不同的元素所造成：

* 有些電子郵件提供者可能已將您的IP位址新增至密碼清單。 在這種情況下，請檢查您的廣播並咨詢[本節](../../delivery/using/about-deliverability.md)。

* 您的傳送量可能太大，無法快速處理，這可能是透過高度的JavaScript個人化，或是您的傳送量超過60KB而發生。 請參閱Adobe Campaign[傳遞最佳實務](../../delivery/using/delivery-best-practices.md)以瞭解內容准則。

* 在Adobe CampaignMTA中可能發生頻寬限制。 這是由以下原因造成：

   * 附加的消息（**[!UICONTROL quotas met]**&#x200B;消息）:已符合Campaign中定義的宣告性MX規則所宣告的配額。 有關此消息的詳細資訊，請參閱[此頁](../../delivery/using/deliverability-faq.md)。 若要進一步瞭解MX規則，請參閱[本節](../../installation/using/email-deliverability.md#about-mx-rules)。

   * 附加的消息（**[!UICONTROL dynamic flow control]**&#x200B;消息）:Campaign MTA嘗試傳送給特定ISP的訊息時發生錯誤，造成延遲，以避免錯誤密度過大，進而面臨潛在的拒絕清單。

* 系統問題可能會阻止伺服器進行交互：這會拖慢整個傳送程式。 檢查伺服器，以確保沒有記憶體或資源問題，例如，在取得個人化資料的過程中，這些問題可能會影響促銷活動。

## 排程的傳送{#scheduled-deliveries-}

如果傳送未在精確的排程日期執行，則可能與伺服器時區之間的差異相關。 中間來源補充實例和生產實例可以位於不同的時區。

例如，如果中間採購實例位於布里斯班時區，生產實例位於達爾文時區，兩個時區彼此相距半小時，那麼在審計日誌中，您會清楚地看到，如果將中間採購的交貨時間安排在11:56，那麼中間採購的相同交貨時間將是12:26，差半小時。

## 失敗狀態{#failed-status}

如果電子郵件傳送的狀態為&#x200B;**[!UICONTROL Failed]**，則可以連結至個人化區塊的問題。 例如，當結構不符合傳送對應時，傳送中的個人化區塊可能會產生錯誤。

傳送記錄檔是瞭解傳送失敗原因的關鍵。 您可從傳送記錄中偵測到以下可能錯誤：

* 收件者訊息失敗，並出現「無法存取」錯誤，指出：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   造成此問題的原因幾乎總是HTML中的個人化，嘗試呼叫未在上游定位或傳送的目標對應中定義或映射的表格或欄位。

   為了修正此問題，必須審查工作流程和傳送內容，以明確決定個人化嘗試呼叫相關表格的方式，以及表格是否可以映射。 在此處，移除HTML中對此表格的呼叫或修正對應至傳送，都是解析的路徑。

* 在中部採購部署模型中，傳送記錄檔中會顯示下列訊息：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因與效能問題有關。 這表示行銷實例在將資料傳送至中端來源伺服器之前，會花費太多時間建立資料。

   為解決此問題，我們建議對資料庫執行真空並重新索引。 有關資料庫維護的詳細資訊，請參閱[本節](../../production/using/recommendations.md)。

   您也應以排程的活動重新啟動所有工作流程，並且所有工作流程都處於失敗狀態。 請參閱[本區段](../../workflow/using/scheduler.md)。

* 當傳送失敗時，傳送記錄中可能會出現下列錯誤：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此錯誤表示電子郵件中有個人化欄位或區塊，其中包含收件者的多個值。 個人化區塊正在使用中，它正在為特定接收者擷取多個記錄。

   若要解決此問題，請檢查使用的個人化資料，然後檢查針對任何欄位有多個項目的收件者的目標。 您也可以在傳送活動之前的定位工作流程中使用&#x200B;**[!UICONTROL Deduplication]**&#x200B;活動，以檢查一次只有一個個人化欄位。 有關重複資料消除的詳細資訊，請參閱[本頁](../../workflow/using/deduplication.md)。

* 某些傳送可能失敗，並出現「無法連線」錯誤，指出：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   這表示傳送成功，但Adobe Campaign收到來自接收者的自動回覆（例如，「不在辦公室」回覆），符合「Auto_ryples」傳入電子郵件規則。

   自動回覆電子郵件被Adobe Campaign忽略，收件人的地址不會被傳送給隔離。
