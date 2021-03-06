---
product: campaign
title: 管線監視
description: 管線監視
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 36b10a49fe92853f98beeb9e7d2fea3f59b10b6f
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 1%

---

# 管線監視 {#pipeline-monitoring}

![](../../assets/common.svg)

的 [!DNL pipelined] 狀態Web服務提供有關 [!DNL pipelined] 處理。

可以使用瀏覽器手動訪問它，也可以使用監視應用程式自動訪問它。

它採用REST格式，如下所述。

![](assets/triggers_8.png)

## 指標 {#indicators}

本節列出狀態Web服務中的指示器。

突出顯示了要監視的建議指標。

* 消費者：調用觸發器的客戶端的名稱。 在管線選項中配置。
* http請求
   * 「最後活著的女兒」：自進行連接檢查以來的時間（毫秒）。
   * last failed-cnx-ms-ago:自上次連接檢查失敗以來的時間（毫秒）。
   * pipeline host:從中提取管道資料的主機的名稱。
* 指針
   * 當前偏移：每個子線程中指針到管道的值。
   * 最後一個刷子：自檢索到一批觸發器以來的時間（毫秒）。
   * 下一偏移刷新：等到下一批完成時。
   * 已處理自上次刷新：上次批處理的觸發器數。
* 路由
   * 觸發器：已檢索的觸發器清單。 在 [!DNL pipelined] 的雙曲餘切值。
* 統計
   * 平均指針刷新時間 — ms:一批觸發器的平均處理時間。
   * 平均觸發處理時間 — ms:分析觸發器資料所花費的平均時間。
   * 位元組讀取：自進程啟動以來從隊列中讀取的位元組數。
   * 當前消息：當前從隊列中提取並等待處理的掛起消息數。 **此指示器應接近於零**。
   * 當前重試次數：當前處理失敗並等待重試的消息數。
   * 峰值消息：進程自啟動以來一直在處理的最大掛起消息數。
   * 指針刷新：自啟動以來處理的郵件批數。
   * routing-JS-custom:自定義JS處理的消息數。
   * 觸發器丟棄：由於處理錯誤而重試過多後丟棄的消息數。
   * 觸發器處理：未出錯處理的消息數。
   * 觸發接收：從隊列接收的消息數。

這些狀態按處理線程顯示。

* 平均觸發處理時間 — ms:分析觸發器資料所花費的平均時間。
* is-JS-processor:值「1」（如果此線程使用自定義JS）。
* 觸發器丟棄：由於處理錯誤而重試過多後丟棄的消息數。 **此指示器應為零**。
* 觸發器失敗：JS中的處理錯誤數。 **此指示器應為零**。
* 觸發接收：從隊列接收的消息數。

* 設定：它們在配置檔案中設定。
   * flush-pointer-msg-count:批中的消息數。
   * flush-pointer-period-ms:兩個批之間的時間（毫秒）。
   * processing-threads-JS:運行自定義JS的處理線程數。
   * 重試週期毫秒：處理錯誤時兩次重試的時間。
   * 重試有效期 — 毫秒：從時間處理開始的持續時間將重試，直到消息被丟棄。
   * 管道消息報告

## 管道消息報告 {#pipeline-report}

此報告顯示過去五天內每小時的消息數。

![](assets/triggers_9.png)
