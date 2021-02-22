---
solution: Campaign Classic
product: campaign
title: 配置整合
description: 配置整合
audience: integrations
content-type: reference
translation-type: tm+mt
source-git-commit: d7de46abb71ca25ef765c6fb5443f6e338fba56e
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 1%

---


# 管線監視 {#pipeline-monitoring}

[!DNL pipelined]狀態web服務提供有關[!DNL pipelined]進程狀態的資訊。

它可以使用瀏覽器手動存取，也可以自動與監控應用程式一起存取。

它採用REST格式，如下所述。

![](assets/triggers_8.png)

## 指標{#indicators}

本節列出狀態Web服務中的指示器。

反白顯示建議的監控指標。

* 消費者：提取觸發器的客戶端的名稱。 在管線選項中配置。
* http-request
   * last-alive-ms-ago:進行連接檢查後的毫秒數時間。
   * last-failed-cnx-ms-ago:自上次連接檢查失敗以來的毫秒數時間。
   * pipeline-host:提取管線資料的主機的名稱。
* 指針
   * 當前偏移：指針的值，每個子線程進入管線。
   * last flush-ms-ago:自擷取一批觸發器以來的毫秒數時間。
   * 下一偏移齊平：等到下一批完成時。
   * processed-since-last-flush:上一批處理的觸發器數。
* 路由
   * 觸發器：已檢索的觸發器清單。 在[!DNL pipelined]選項中配置。
* 統計
   * average-pointer-flush-time-ms:一批觸發器的平均處理時間。
   * average-trigger-processing-time-ms:解析觸發器資料的平均時間。
   * 位元組讀取：自進程啟動以來從隊列中讀取的位元組數。
   * current-messages:已從佇列提取並正在等待處理的待處理訊息的目前數目。 **此指標應接近零**。
   * current-retries:當前處理失敗並正在等待重試的消息數。
   * 峰值消息：進程自啟動以來處理的待處理消息的最大數量。
   * 指針刷新：自啟動以來處理的消息批數。
   * routing-JS-custom:自訂JS處理的訊息數。
   * trigger-incolled:因處理錯誤而在重試次數過多後被丟棄的消息數。
   * trigger-processed:未出現錯誤的消息數。
   * trigger-received:從隊列中接收的消息數。

這些統計資料會依處理執行緒顯示。

* average-trigger-processing-time-ms:解析觸發器資料的平均時間。
* is-JS-processor:值&quot;1&quot;（如果此執行緒使用自訂JS）。
* trigger-incolled:因處理錯誤而在重試次數過多後被丟棄的消息數。 **此指標應為零**。
* 觸發器失敗：JS中的處理錯誤數。 **此指標應為零**。
* trigger-received:從隊列中接收的消息數。

* 設定：它們被設定在配置檔案中。
   * flush-pointer-msg-count:批中的消息數。
   * flush-pointer-period-ms:兩批之間的時間（以毫秒為單位）。
   * processing-threads-JS:執行自訂JS的處理執行緒數。
   * retry-period-ms:兩次重試之間的時間。
   * retry-validity-duration-ms:從時間處理開始的持續時間會重試，直到消息被丟棄。
   * 管線消息報告

## 管線消息報告{#pipeline-report}

此報表顯示過去五天內每小時的訊息數。

![](assets/triggers_9.png)
