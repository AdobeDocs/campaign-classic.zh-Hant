---
product: campaign
title: 管線監視
description: 管線監視
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 1%

---

# 管線監視 {#pipeline-monitoring}



此 [!DNL pipelined] 狀態web服務提供 [!DNL pipelined] 程式。

您可以使用瀏覽器手動存取，或使用監控應用程式自動存取。

它採用REST格式，如下所述。

![](assets/triggers_8.png)

## 指標 {#indicators}

此段落列出狀態Web服務中的指示器。

建議監控的指標會反白顯示。

* 消費者：提取觸發器的使用者端名稱。 在管道選項中設定。
* http-request
   * last-alive-ms-ago：自進行連線檢查以來的時間（以毫秒為單位）。
   * last-failed-cnx-ms-ago：上次連線檢查失敗後的時間（以毫秒為單位）。
   * pipeline-host：從中提取管道資料的主機的名稱。
* 指標
   * current-offsets：每個子系螺紋的進入配管的指標值。
   * last-flush-ms-ago：自擷取批次觸發器以來的時間（以毫秒為單位）。
   * next-offsets-flush：完成時等到下一個批次的時間。
   * processed-since-last-flush：上一個批次中處理的觸發程式數目。
* 路由
   * triggers：擷取的觸發器清單。 在中設定 [!DNL pipelined] 選項。
* 統計資料
   * average-pointer-flush-time-ms：一次觸發程式的平均處理時間。
   * average-trigger-processing-time-ms：剖析觸發程式資料所花費的平均時間。
   * bytes-read：自處理程式啟動後，從佇列讀取的位元組數。
   * current-messages：目前已從佇列提取且等待處理的擱置訊息數目。 **此指標應接近零**.
   * current-retries：處理失敗並等待重試的目前訊息數。
   * peak-messages：處理程式啟動後已處理的最大擱置訊息數。
   * 指標排清：自開始以來已處理的訊息批次數量。
   * routing-JS-custom：由自訂JS處理的訊息數。
   * trigger-discarded：因處理錯誤而在重試過多後捨棄的訊息數。
   * trigger-processed：已處理但無錯誤的訊息數。
   * trigger-received：從佇列接收的訊息數。

這些統計值會依處理執行緒顯示。

* average-trigger-processing-time-ms：剖析觸發程式資料所花費的平均時間。
* is-JS-processor：如果此執行緒使用自訂JS，則值為「1」。
* trigger-discarded：因處理錯誤而在重試過多後捨棄的訊息數。 **此指標應為零**.
* trigger-failures： JS中的處理錯誤數。 **此指標應為零**.
* trigger-received：從佇列接收的訊息數。

* 設定：在設定檔案中設定。
   * flush-pointer-msg-count：批次中的訊息數。
   * flush-pointer-period-ms：兩個批次之間的時間（毫秒）。
   * processing-threads-JS：執行自訂JS的處理執行緒數目。
   * retry-period-ms：發生處理錯誤時兩次重試之間的時間。
   * retry-validity-duration-ms：重試時間處理，直到訊息捨棄的持續時間。
   * 管道訊息報表

## 管道訊息報表 {#pipeline-report}

此報表顯示過去五天每小時的訊息數。

![](assets/triggers_9.png)
