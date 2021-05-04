---
solution: Campaign Classic
product: campaign
title: 追蹤及監控訊息
audience: delivery
content-type: reference
topic-tags: deliveries-best-practices
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
translation-type: tm+mt
source-git-commit: d5579fa1928888a088fe99b685f4d12bf2bde25b
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 3%

---

# 追蹤和監視 {#track-and-monitor}

您是否按一下了&#x200B;**Send**&#x200B;按鈕？ 讓我們看看會發生什麼。 傳送後，Adobe Campaign可讓您追蹤傳送的訊息，並瞭解收件者對傳送的反應。 這可協助您改善未來的傳送方式，並最佳化您的下一個促銷活動。

## 監視傳遞{#monitoring-deliveries}

若要控制您的促銷活動，您必須確保訊息確實已傳送給收件者。

從「促銷活動傳送」控制面板，您可以檢查已處理的訊息和傳送稽核記錄。
您也可以控制傳送記錄檔中訊息的狀態。 [了解更多](../../delivery/using/about-delivery-monitoring.md)。

如果傳送未傳送，且狀態仍為&#x200B;**待定**，該怎麼辦？

* 執行進程正在等待某些資源的可用性。 MTA可能尚未啟動。
檢查您的mta@instance模組是否已在MTA伺服器上啟動，並視需要啟動MTA模組。 [了解更多](../../production/using/administration.md)。

* 傳送可能使用傳送例項上未設定的相似性。
提示：檢查流量管理（IP相似性）的設定。 有關詳細資訊，請參閱控制傳出SMTP通信。

>[!NOTE]
>
>這些步驟只能由專家使用者執行。

## 追蹤 {#tracking-deliveries}

若要深入瞭解收件者的行為，您可以追蹤他們對遞送的反應：接收、開啟、點按連結、取消訂閱等。 在Campaign Classic中，此資訊會顯示在傳送所定位之收件者的「追蹤」標籤和傳送的「追蹤」標籤中。

**提示**:預設會啟用訊息追蹤。若要設定URL，請在傳送精靈的下方區段中選取「顯示URL」選項。 對於訊息的每個URL，您可以選擇是否啟用追蹤。

有關詳細資訊，請參閱[設定追蹤](../../delivery/using/how-to-configure-tracked-links.md)區段和[追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators)說明。

## 傳送效能{#delivery-performances}

要測量消息的傳送速度，您可以控制傳送吞吐量。 標準是每小時發送的消息數和消息的大小（以位／秒為單位）。 有關詳細資訊，請參閱[傳送吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 請勿在實例上將交貨保持為失敗狀態，因為這會維護臨時表並影響效能。

* 從資料庫移除不再需要的傳送和非作用中收件者，以維持位址品質。

* 請勿嘗試排程大型傳送。 請注意，在系統上均勻分配負載可能需要5到10分鐘。

## 傳遞疑難排解 {#delivery-troubleshooting}

當傳送發生問題時，可執行特定動作：

* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [影像顯示問題](../../production/using/image-display-issues.md)

* [傳送效能問題](../../delivery/using/delivery-performances.md)

* [臨時檔案問題](../../production/using/temporary-files.md) -僅 *限內部部署客戶*
