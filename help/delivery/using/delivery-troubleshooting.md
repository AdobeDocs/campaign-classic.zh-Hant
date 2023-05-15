---
product: campaign
title: 傳送傳送疑難排解
description: 進一步了解傳遞效能，以及如何疑難排解與傳遞監控相關的問題
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 傳送傳送疑難排解 {#delivery-troubleshooting}



本節列出您在傳送傳遞時可能遇到的常見問題，以及如何進行疑難排解。

此外，請務必遵循最佳作法和檢查清單，詳細說明於 [本頁](delivery-performances.md) 以確保傳遞順利執行。

**相關主題：**

* [傳遞狀態](delivery-statuses.md)
* [傳遞儀表板](delivery-dashboard.md)
* [瞭解傳遞故障](understanding-delivery-failures.md)

## 傳遞緩慢 {#slow-deliveries}

按一下 **[!UICONTROL Send]** 按鈕，您的傳送似乎比平常更久。 這可能是由不同元素造成：

* 某些電子郵件提供者可能已將您的IP位址新增至封鎖清單。 在此情況下，請檢查廣播並諮詢 [本節](about-deliverability.md).

* 您的傳送可能太大，無法快速處理，這可能會在JavaScript個人化程度較高時發生，或是您的傳送重超過60KB時發生。 請參閱Adobe Campaign [傳遞最佳實務](delivery-best-practices.md) 了解內容准則。

* 在Adobe Campaign MTA內可能已發生限制。 這是由下列原因造成：

   * 已附加的訊息(**[!UICONTROL quotas met]** 消息):已滿足Campaign中定義的聲明性MX規則所宣告的配額。 如需此訊息的詳細資訊，請參閱 [本頁](deliverability-faq.md). 若要進一步了解MX規則，請參閱 [本節](../../installation/using/email-deliverability.md#about-mx-rules).

   * 已附加的訊息(**[!UICONTROL dynamic flow control]** 消息):嘗試傳送給指定ISP的訊息時，Campaign MTA發生錯誤，導致傳送速度變慢，以避免錯誤密度過大，進而面臨潛在封鎖清單。

* 系統問題會阻止伺服器相互作用：這會拖慢整個傳送程式。 檢查伺服器，確保在取得個人化資料的程式中沒有可能影響Campaign的記憶體或資源問題。

## 已排程的傳送 {#scheduled-deliveries-}

如果傳送未在確切的排程日期執行，則可能與伺服器時區之間的差異有關。 中間來源例項和生產例項可位於不同時區。

例如，如果中間來源實例位於布里斯班時區，而生產實例位於達爾文時區，則兩個時區彼此相距半小時，那麼在審核日誌中，您會清楚地看到，如果將中間來源實例安排為11:56生產，則中間來源實例安排的相同傳送將是12:26，其差異為半小時。

## 失敗狀態 {#failed-status}

如果電子郵件傳送的狀態為 **[!UICONTROL Failed]**，則可連結至個人化區塊的問題。 例如，當結構不符合傳送對應時，傳送中的個人化區塊可能會產生錯誤。

傳送記錄檔是了解傳送失敗原因的關鍵。 以下是您可從傳送記錄檔偵測的可能錯誤：

* 收件者訊息失敗，出現「無法連線」錯誤，指出：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   此問題的原因幾乎一律是HTML內嘗試呼叫未在上游鎖定目標或傳送目標對應中定義或對應的表格或欄位的個人化。

   為了修正此問題，需要審查工作流程和傳送內容，以明確決定要嘗試呼叫有問題的表格的個人化項目，以及表格是否可以對應。 從那裡，在HTML中移除對此表格的呼叫，或修正傳送的對應，都是解決方法。

* 在中間來源部署模型中，傳送記錄檔中可能會顯示下列訊息：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因與效能問題有關。 這表示行銷執行個體在將資料傳送至中間來源伺服器之前，會花太多時間建立資料。

   為此，我們建議對資料庫執行真空和重新索引。 有關資料庫維護的詳細資訊，請參閱 [本節](../../production/using/recommendations.md).

   您也應以排程活動重新啟動所有工作流程，並且所有工作流程都處於失敗狀態。 請參閱[本節](../../workflow/using/scheduler.md)。

* 傳送失敗時，傳送記錄中可能會顯示下列錯誤：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此錯誤表示電子郵件中有個人化欄位或區塊，且收件者有多個值。 正在使用個人化區塊，它正在為特定收件者擷取多個記錄。

   若要解決此問題，請檢查所使用的個人化資料，然後檢查具有以上任何欄位項目之收件者的目標。 您也可以使用 **[!UICONTROL Deduplication]** 傳送活動之前的目標工作流程中的活動，以檢查一次只有一個個人化欄位。 有關重複資料刪除的詳細資訊，請參閱 [本頁](../../workflow/using/deduplication.md).

* 某些傳送可能會失敗，並出現「無法連線」錯誤指出：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   這表示傳送成功，但Adobe Campaign收到收件者的自動回覆（例如「未辦公」回覆），符合「Auto_replies」傳入電子郵件規則。

   Adobe Campaign會忽略自動回覆電子郵件，而收件者的地址不會傳送至隔離區。
