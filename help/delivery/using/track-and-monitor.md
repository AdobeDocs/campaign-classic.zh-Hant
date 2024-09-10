---
product: campaign
title: 追蹤和監視訊息
description: 瞭解如何追蹤和監控訊息
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Monitoring, Reporting
role: User
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 2%

---

# 追蹤和監視 {#track-and-monitor}

您按一下&#x200B;**傳送**&#x200B;按鈕嗎？ 讓我們看看會發生什麼事。 傳送後，Adobe Campaign可讓您追蹤已傳送的訊息，並探索收件者對傳送的反應。 這可協助您改善未來的傳送，並最佳化後續的行銷活動。

## 監視傳遞 {#monitoring-deliveries}

若要控制您的行銷活動，您必須確保訊息確實已傳送給收件者。

在Campaign傳送控制面板中，您可以檢查已處理的訊息和傳送稽核記錄。
您也可以控制傳送記錄檔中訊息的狀態。 [了解更多](about-delivery-monitoring.md)。

如果未傳送傳遞且其狀態仍為&#x200B;**擱置中**，該怎麼辦？

* 執行程式正在等待某些資源的可用性。 MTA可能尚未啟動。
檢查您的mta@instance模組是否已在MTA伺服器上啟動，並視需要啟動MTA模組。 [了解更多](../../production/using/administration.md)。

* 傳遞可能使用傳送執行個體上尚未設定的相似性。
提示：檢查流量管理（IP相似性）的設定。 如需詳細資訊，請參閱控制傳出SMTP流量。

>[!NOTE]
>
>這些步驟只能由專家使用者執行。

## 追蹤行為 {#track-behaviour}

為了更清楚瞭解收件者的行為，您可以追蹤他們對傳送的反應：接收、開啟、點選連結、取消訂閱等。 在Campaign Classic中，此資訊會顯示在傳遞所目標定位的收件者的「追蹤」標籤中，以及傳遞的「追蹤」標籤中。

**提示**：訊息追蹤預設為啟用。 若要設定URL，請選取傳送助理員下方區段中的「顯示URL」選項。 對於訊息的每個URL，您可以選擇是否啟動追蹤。

如需詳細資訊，請參閱[設定追蹤](how-to-configure-tracked-links.md)區段及[追蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators)說明。

## 傳遞效能 {#delivery-performances}

若要測量傳遞訊息的速度，您可以控制傳遞輸送量。 准則是每小時傳送的訊息數目和訊息大小（以每秒位元組數為單位）。 如需詳細資訊，請參閱[傳遞輸送量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**：

* 請勿將傳遞在執行個體上維持在失敗狀態，因為這會維護臨時表格並影響效能。

* 從資料庫移除不再需要的傳遞及非作用中的收件者，以維持地址品質。

* 請勿嘗試一起排程大型傳遞。 請注意，可能需要5到10分鐘的時間才能將負載均勻分散到系統上。

## 傳遞疑難排解 {#delivery-troubleshooting}

遇到傳送問題時，可執行特定動作：

* [傳遞能力問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [影像顯示問題](../../production/using/image-display-issues.md)

* [傳遞效能問題](delivery-performances.md)

* [暫存檔案問題](../../production/using/temporary-files.md) — 僅限&#x200B;*內部部署客戶*
