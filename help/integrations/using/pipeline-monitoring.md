---
product: campaign
title: 管線監視
description: 管線監視
feature: Triggers
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: integrations
content-type: reference
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# 管線監視 {#pipeline-monitoring}



此 [!DNL pipelined] 狀態web服務提供 [!DNL pipelined] 程式。

您可以使用瀏覽器手動存取，或透過監控應用程式自動存取。

它採用REST格式，如下所述。

![](assets/triggers_8.png)

## 指標 {#indicators}

此段落列示狀態Web服務中的指示器。

建議監控的指標會醒目提示。

* 消費者：提取觸發器的使用者端名稱。 在管道選項中設定。
* http-request
   * last-alive-ms-ago：自進行連線檢查以來的時間（以毫秒為單位）。
   * last-failed-cnx-ms-ago：上次連線檢查失敗後的時間（以毫秒為單位）。
   * pipeline-host：從中提取管道資料的主機的名稱。
* 指標
   * current-offsets：每個子系螺紋的管線中指標值。
   * last-flush-ms-ago：擷取批次觸發程式後所經過的時間（以毫秒為單位）。
   * next-offsets-flush：完成時等到下一個批次的時間。
   * processed-since-last-flush：上一個批次中已處理的觸發程式數目。
* 路由
   * triggers：擷取的觸發器清單。 在中設定 [!DNL pipelined] 選項。
* 統計資料
   * average-pointer-flush-time-ms：一個觸發程式批次的平均處理時間。
   * average-trigger-processing-time-ms：剖析觸發程式資料所花費的平均時間。
   * bytes-read：自處理程式啟動後，從佇列讀取的位元組數。
   * current-messages：目前從佇列提取並等待處理的擱置訊息數目。 **此指標應接近零**.
   * current-retries：處理失敗並等待重試的目前訊息數。
   * peak-messages：處理程式自啟動後已處理的最大擱置訊息數。
   * pointer-flushes：自開始以來處理的訊息批次數量。
   * routing-JS-custom：由自訂JS處理的訊息數。
   * trigger-discarded：因處理錯誤而重試太多後捨棄的訊息數。
   * trigger-processed：未發生錯誤而處理的訊息數。
   * trigger-received：從佇列接收的訊息數。

這些統計資料會依處理執行緒顯示。

* average-trigger-processing-time-ms：剖析觸發程式資料所花費的平均時間。
* is-JS-processor：如果此執行緒使用自訂JS，則值為「1」。
* trigger-discarded：因處理錯誤而重試太多後捨棄的訊息數。 **此指標應為零**.
* trigger-failures： JS中的處理錯誤數。 **此指標應為零**.
* trigger-received：從佇列接收的訊息數。

* 設定：在設定檔案中設定。
   * flush-pointer-msg-count：批次中的訊息數。
   * flush-pointer-period-ms：兩個批次之間的時間（毫秒）。
   * processing-threads-JS：執行自訂JS的處理執行緒數目。
   * retry-period-ms：發生處理錯誤時兩次重試之間的時間。
   * retry-validity-duration-ms：重試時間處理，直到捨棄訊息為止。
   * 管道訊息報表

## 管道訊息報表 {#pipeline-report}

此報表顯示過去五天每小時的訊息數。

![](assets/triggers_9.png)
