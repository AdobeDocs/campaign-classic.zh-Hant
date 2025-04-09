---
product: campaign
title: 管線監視
description: 管線監視
feature: Triggers
badge-v8: label="也適用於 v8" type="Positive" tooltip="亦適用於 Campaign v8"
audience: integrations
content-type: reference
level: Intermediate, Experienced
exl-id: 84399496-33fd-4936-85e7-32de8503740f
source-git-commit: 2bfcec5eaa1145cfb88adfa9c8b2f72ee3cd9469
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---

# 管線監視 {#pipeline-monitoring}



[!DNL pipelined]狀態 Web 服務提供有關進程狀態[!DNL pipelined]的資訊。

可以使用瀏覽器手動訪問它，也可以使用監視應用程式自動訪問它。

它位於 REST 格式中，如下所述。

![](assets/triggers_8.png)

## 指標 {#indicators}

本節列出了狀態 Web 服務中的指示器。

建議監控的指標會醒目提示。

* 消費者：提取觸發器的使用者端名稱。 在管道選項中設定。
* http-request
   * last-alive-ms-ago：自進行連線檢查以來的時間（以毫秒為單位）。
   * last-failed-cnx-ms-ago：上次連線檢查失敗後的時間（以毫秒為單位）。
   * 管道主機：從中提取管道数据的主機的名稱。
* 指標
   * current-offsets：每個子系螺紋的管線中指標值。
   * last-flush-ms-ago：擷取批次觸發程式後所經過的時間（以毫秒為單位）。
   * next-offsets-flush：完成時等到下一個批次的時間。
   * processed-since-last-flush：上一個批次中已處理的觸發程式數目。
* 路由
   * 觸發器： 擷取的觸發器清單。 在選項中 [!DNL pipelined] 配置。
* 統計
   * 平均指標刷新時間毫秒：一批觸髮器的平均處理時間。
   * 平均觸髮器處理時間毫秒： 分析觸髮器數據所花費的平均時間。
   * 讀取的位元組數：自進程啟動以來從佇列讀取的位元元組數。
   * 當前消息：已從佇列中提取並正在等待處理的當前掛起消息數。 **該指標應接近於零**。
   * current-重試：當前處理失敗並正在等待重試的郵件數。
   * 峰值消息：進程自啟動以來一直在處理的最大待處理消息數。
   * 指標刷新：自開始以來處理的消息批次數。
   * routing-JS-custom：由自訂JS處理的訊息數。
   * trigger-discarded：因處理錯誤而重試太多後捨棄的訊息數。
   * trigger-processed：未發生錯誤而處理的訊息數。
   * trigger-received：從佇列接收的訊息數。

這些統計資訊是按每個處理線程顯示的。

* average-trigger-processing-time-ms：剖析觸發程式資料所花費的平均時間。
* is-JS-processor：如果此執行緒使用自訂JS，則值為「1」。
* trigger-discarded：因處理錯誤而重試太多後捨棄的訊息數。 **此指標應為零**。
* trigger-failures： JS中的處理錯誤數。 **此指標應為零**。
* trigger-received：從佇列接收的訊息數。

* 設定：它們在配置文件中設置。
   * 刷新指標消息計數：批處理中的消息數。
   * flush-pointer-period-ms：兩個批次之間的時間，以毫秒為單位。
   * processing-threads-JS：運行自定義 JS 的處理線程數。
   * retry-period-ms：發生處理錯誤時兩個重試之間的時間。
   * retry-validity-duration-ms：從重試處理到丟棄消息的持續時間。
   * 管道訊息報表

## 管道訊息報表 {#pipeline-report}

此報表顯示過去五天每小時的訊息數。

![](assets/triggers_9.png)
