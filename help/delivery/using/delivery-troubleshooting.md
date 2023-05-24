---
product: campaign
title: 傳遞傳送疑難排解
description: 進一步瞭解傳遞效能，以及如何疑難排解與傳遞監視相關的問題
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring, Deliverability
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 傳遞傳送疑難排解 {#delivery-troubleshooting}



本節列出您在傳送傳遞時可能會遇到的常見問題，以及如何疑難排解這些問題。

此外，請務必遵循中詳細說明的最佳實務和檢查清單 [此頁面](delivery-performances.md) 以確保您的傳遞執行良好。

**相關主題：**

* [傳遞狀態](delivery-statuses.md)
* [傳遞儀表板](delivery-dashboard.md)
* [瞭解傳遞故障](understanding-delivery-failures.md)

## 傳遞緩慢 {#slow-deliveries}

按一下 **[!UICONTROL Send]** 按鈕，您的傳送時間似乎比平常長。 這可能是由於不同的元素所造成：

* 有些電子郵件提供者可能已將您的IP位址新增至封鎖清單。 在此情況下，請檢查您的broadlog並查閱 [本節](about-deliverability.md).

* 您的傳送可能太大而無法快速處理，這可能發生在高JavaScript個人化或傳送重量超過60KB時。 請參閱Adobe Campaign [傳遞最佳實務](delivery-best-practices.md) 以瞭解內容准則。

* 節流可能發生在Adobe Campaign MTA中。 原因如下：

   * 已擱置的訊息(**[!UICONTROL quotas met]** message)：已符合Campaign中定義的宣告MX規則所宣告的配額。 如需此訊息的詳細資訊，請參閱 [此頁面](deliverability-faq.md). 若要進一步瞭解MX規則，請參閱 [本節](../../installation/using/email-deliverability.md#about-mx-rules).

   * 已擱置的訊息(**[!UICONTROL dynamic flow control]** message)： Campaign MTA在嘗試傳遞給定ISP的訊息時遇到錯誤，這會造成速度變慢以避免錯誤密度太大，從而面臨潛在的封鎖清單。

* 系統問題可能會導致伺服器無法共同互動：這可能會減慢整個傳送流程的速度。 檢查伺服器，確保沒有記憶體或資源問題可能會影響Campaign取得個人化資料的程式，例如。

## 已排程的傳遞 {#scheduled-deliveries-}

如果傳送未在確切排程日期執行，這可能與伺服器時區之間的差異有關。 中間來源執行個體和生產執行個體可能位於不同的時區。

例如，如果中間來源執行個體在布里斯班時區，而生產執行個體在達爾文時區，兩個時區彼此相隔半小時，則在稽核記錄中，您會清楚地看到，如果排定在11:56生產該傳遞，則排定在mid的相同傳遞將在12:26，兩者之間有半小時的差異。

## 失敗狀態 {#failed-status}

如果電子郵件傳遞的狀態為 **[!UICONTROL Failed]**，可連結至個人化區塊的問題。 例如，當結構描述不符合傳遞對應時，傳遞中的個人化區塊可能會產生錯誤。

傳遞記錄是瞭解傳遞失敗原因的關鍵。 您可以從傳送記錄中偵測到以下可能的錯誤：

* 收件者訊息失敗，並出現「無法聯絡」錯誤訊息，指出：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   此問題的原因幾乎總是HTML內的個人化，嘗試呼叫尚未定義或對應在上游目標定位或傳送目標對應的表格或欄位。

   若要修正此問題，需要檢閱工作流程和傳遞內容，以明確決定嘗試呼叫相關表格的個人化專案，以及表格是否可以對應。 從那裡，在HTML中移除對此表格的呼叫或修正傳遞的對應將是解析的路徑。

* 在中間來源部署模型中，傳遞記錄中可能會顯示以下訊息：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因與效能問題有關。 這表示行銷執行個體在將資料傳送至中間來源伺服器之前，會花費太多時間建置資料。

   若要解決此問題，建議對資料庫執行真空並重新索引。 有關資料庫維護的詳細資訊，請參閱 [本節](../../production/using/recommendations.md).

   您也應該重新啟動所有具有已排程活動的工作流程，以及所有處於失敗狀態的工作流程。 請參閱[本節](../../workflow/using/scheduler.md)。

* 傳送失敗時，傳送記錄中可能會出現下列錯誤：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此錯誤表示電子郵件中有收件者的多個值之個人化欄位或區塊。 個人化區塊正在使用中，且正在為特定收件者擷取多個記錄。

   若要解決此問題，請檢查使用的個人化資料，然後針對任何這些欄位，檢查有多個專案的收件者目標。 您也可以使用 **[!UICONTROL Deduplication]** 活動之前的目標工作流程中的活動，以檢查一次只有一個個人化欄位。 如需重複資料刪除的詳細資訊，請參閱 [此頁面](../../workflow/using/deduplication.md).

* 部分傳送可能會因「無法聯絡」錯誤而失敗，並指出：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   這表示傳送成功，但Adobe Campaign收到收件者的自動回覆（例如「不在辦公室」回覆），符合「Auto_replies」傳入電子郵件規則。

   Adobe Campaign會忽略自動回覆電子郵件，收件者的地址不會傳送給隔離區。
