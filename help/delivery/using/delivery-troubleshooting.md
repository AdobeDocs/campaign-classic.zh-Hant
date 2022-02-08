---
product: campaign
title: 傳遞發送疑難解答
description: 瞭解有關交付效能的詳細資訊以及如何排除與交付監控相關的問題
exl-id: 37b1d7fb-7ceb-4647-9aac-c8a80495c5bf
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '791'
ht-degree: 1%

---

# 傳遞發送疑難解答 {#delivery-troubleshooting}

![](../../assets/common.svg)

本節列出了在發送交貨時可能遇到的常見問題，以及如何排除這些問題。

此外，確保遵循中詳細介紹的最佳做法和核對表 [此頁](delivery-performances.md) 確保交貨順利進行。

**相關主題：**

* [傳遞狀態](delivery-statuses.md)
* [傳遞儀表板](delivery-dashboard.md)
* [瞭解傳遞故障](understanding-delivery-failures.md)

## 交貨緩慢 {#slow-deliveries}

按一下 **[!UICONTROL Send]** 按鈕，你的送貨時間似乎比平時長。 這可能是由以下不同元素引起的：

* 某些電子郵件提供商可能已將您的IP地址添加到密碼清單。 在這種情況下，檢查一下你的廣播 [此部分](about-deliverability.md)。

* 您的交付量可能太大，無法快速處理，這可能是由於JavaScript高度個性化或交付量超過60KB而導致的。 請參閱Adobe Campaign [提供最佳做法](delivery-best-practices.md) 瞭解內容指南。

* 在Adobe CampaignMTA中可能已發生限制。 這是由於：

   * 消息已掛起(**[!UICONTROL quotas met]** 消息):已滿足「活動」中定義的聲明性MX規則聲明的配額。 有關此消息的詳細資訊，請參閱 [此頁](deliverability-faq.md)。 要瞭解有關MX規則的詳細資訊，請參閱 [此部分](../../installation/using/email-deliverability.md#about-mx-rules)。

   * 消息已掛起(**[!UICONTROL dynamic flow control]** 消息):市場活動MTA在嘗試為指定ISP發送消息時遇到錯誤，這會導致延遲以避免錯誤密度過大，從而面臨潛在的密度清單。

* 系統問題可以阻止伺服器交互：這會減緩整個發送過程。 檢查伺服器以確保在獲取個性化資料的過程中不存在可能影響市場活動的記憶體或資源問題。

## 計畫交貨 {#scheduled-deliveries-}

如果交貨不在精確的預定日期執行，則可能與伺服器時區之間的差異有關。 中間來源補充常式和生產常式可以位於不同的時區。

例如，如果中間採購實例在布里斯班時區，生產實例在達爾文時區，兩個時區相距半小時，那麼在審計日誌中您可以清楚地看到，如果將交貨計畫在11:56進行生產，則中間計畫的相同交貨將是12:26，相差半小時。

## 失敗狀態 {#failed-status}

如果電子郵件傳遞的狀態為 **[!UICONTROL Failed]**，它可以連結到個性化塊的問題。 例如，當架構與傳遞映射不匹配時，傳遞中的個性化塊可能會生成錯誤。

傳遞日誌是瞭解傳遞失敗原因的關鍵。 以下是可從傳遞日誌中檢測到的可能錯誤：

* 收件者郵件失敗，出現「Unreachable（無法訪問）」錯誤，指出：

   ```
   Error while compiling script 'content htmlContent' line X: `[table]` is not defined. JavaScript: error while evaluating script 'content htmlContent
   ```

   此問題的原因幾乎總是HTML內的個性化設定，試圖調用在上游目標或傳遞的目標映射中未定義或映射的表或欄位。

   要更正此問題，需要檢查工作流和傳遞內容，以確定具體是什麼個性化正在嘗試調用有問題的表，以及表是否可以映射。 從那裡，刪除HTML中對此表的調用或將映射固定到傳遞將成為解決方法。

* 在中間採購部署模型中，以下消息可以出現在傳遞日誌中：

   ```
   Error during the call of method 'AppendDeliveryPart' on the mid sourcing server: 'Communication error with the server: please check this one is correctly configured. Code HTTP 408 'Service temporarily unavailable'.
   ```

   原因與效能問題有關。 這意味著在將資料發送到中間採購伺服器之前，市場營銷實例花費了太多的時間來構建資料。

   為此，我們建議對資料庫執行真空和重新索引。 有關資料庫維護的詳細資訊，請參閱 [此部分](../../production/using/recommendations.md)。

   您還應該重新啟動所有具有計畫活動的工作流，以及所有處於失敗狀態的工作流。 請參閱[本節](../../workflow/using/scheduler.md)。

* 傳遞失敗時，在傳遞日誌中可能會出現以下錯誤：

   ```
   DLV-XXXX The count of message prepared (123) is greater than the number of messages to send (111). Please contact support.
   ```

   通常，此錯誤意味著電子郵件中存在一個為收件人具有多個值的個性化欄位或塊。 正在使用個性化塊，它正在為特定接收者提取多個記錄。

   要解決此問題，請檢查使用的個性化資料，然後檢查目標接收者是否具有這些欄位中任意一個以上條目。 您還可以使用 **[!UICONTROL Deduplication]** 在交貨活動之前在目標工作流中執行活動以檢查一次只有一個個性化欄位。 有關重複資料消除的詳細資訊，請參閱 [此頁](../../workflow/using/deduplication.md)。

* 某些傳遞可能失敗，並出現「無法訪問」錯誤：

   ```
   Inbound email bounce (rule 'Auto_replies' has matched this bounce).
   ```

   這表示傳送成功，但Adobe Campaign收到了與「Auto_replies」入站電子郵件規則匹配的收件人的自動答復（例如「外出」答復）。

   自動回復電子郵件被Adobe Campaign忽略，並且收件人的地址不會被發送到隔離區。
