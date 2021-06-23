---
product: campaign
title: 追蹤及監視訊息
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 3%

---

# 追蹤和監視 {#track-and-monitor}

您是否按一下了&#x200B;**Send**&#x200B;按鈕？ 讓我們看看會發生什麼。 傳送後，Adobe Campaign可讓您追蹤已傳送的訊息，並探索收件者對您傳送的反應。 這可協助您改善未來的傳送，並最佳化您的下一個促銷活動。

## 監視傳遞 {#monitoring-deliveries}

若要控制您的行銷活動，您必須確保訊息確實已傳送給收件者。

從Campaign傳遞控制面板，您可以檢查已處理的訊息和傳遞稽核記錄。
您也可以控制傳送記錄檔中訊息的狀態。 [深入瞭解](about-delivery-monitoring.md)。

如果未傳送傳送且其狀態維持&#x200B;**擱置中**，該怎麼辦？

* 執行程式正在等待某些資源的可用性。 MTA可能尚未啟動。
檢查您的mta@instance模組是否已在MTA伺服器上啟動，並視需要啟動MTA模組。 [深入瞭解](../../production/using/administration.md)。

* 傳送可能使用的相關性尚未在傳送執行個體上設定。
提示：檢查流量管理（IP相關性）的設定。 有關詳細資訊，請參閱控制傳出的SMTP流量。

>[!NOTE]
>
>這些步驟只能由專家使用者執行。

## 追蹤 {#tracking-deliveries}

若要進一步了解收件者的行為，您可以追蹤收件者對傳遞的反應：接收、開啟、點按連結、取消訂閱等。 在Campaign Classic中，此資訊會顯示在傳送所定位之收件者的「追蹤」標籤和傳送的「追蹤」標籤中。

**提示**:訊息追蹤預設為啟用。若要設定URL，請在傳送精靈的下半部選取「顯示URL」選項。 對於訊息的每個URL，您可以選擇是否啟用追蹤。

如需詳細資訊，請參閱[設定追蹤](how-to-configure-tracked-links.md)區段和[追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators)說明。

## 傳遞效能 {#delivery-performances}

若要測量訊息傳送的速度，您可以控制傳送的輸送量。 標準是每小時傳送的訊息數，以及訊息的大小（以位元/秒為單位）。 有關詳細資訊，請參閱[傳送吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 請勿在執行個體上將傳送保持為失敗狀態，因為這會維護臨時表格並影響效能。

* 從資料庫中移除不再需要的傳送和非作用中的收件者，以維持位址品質。

* 請勿嘗試將大型傳送排程在一起。 請注意，可能需要5到10分鐘才能將負載均勻地分散到系統上。

## 傳遞疑難排解 {#delivery-troubleshooting}

當傳送發生問題時，可執行特定動作：

* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [影像顯示問題](../../production/using/image-display-issues.md)

* [傳遞效能問題](delivery-performances.md)

* [臨時檔案問題](../../production/using/temporary-files.md)  — 僅 *限內部部署客戶*
