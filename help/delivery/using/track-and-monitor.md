---
product: campaign
title: 跟蹤和監視消息
description: 瞭解如何跟蹤和監視郵件
feature: Monitoring
exl-id: a039a288-2e7b-4f35-9885-ead3ed4347af
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 3%

---

# 追蹤和監視 {#track-and-monitor}

![](../../assets/common.svg)

你點擊了 **發送** 按鈕？ 讓我們看看會發生什麼。 發送後，Adobe Campaign將使您能夠跟蹤已發送的郵件並瞭解收件人對您的發送有何反應。 這將幫助您改進未來的發送，並優化您的下一次活動。

## 監視傳遞 {#monitoring-deliveries}

要控制您的市場活動，您必須確保郵件確實已發送給您的收件人。

在「市場活動傳遞」控制面板中，您可以檢查已處理的消息和傳遞審核日誌。
您還可以控制傳遞日誌中消息的狀態。 [了解更多](about-delivery-monitoring.md)。

如果未發送交貨，且其狀態仍為 **待定**?

* 執行過程正在等待某些資源的可用性。 MTA可能尚未啟動。
檢查mta@instance模組是否已在MTA伺服器上啟動，並在必要時啟動MTA模組。 [了解更多](../../production/using/administration.md)。

* 傳遞可能使用在發送實例上尚未配置的關聯。
提示：檢查流量管理（IP關聯）的配置。 有關詳細資訊，請參閱控制傳出SMTP通信。

>[!NOTE]
>
>這些步驟只能由專家用戶執行。

## 跟蹤行為 {#track-behaviour}

為了更好地瞭解收件人的行為，您可以跟蹤他們對遞送的反應：接收、開啟、點擊連結、取消訂閱等。 在Campaign Classic中，此資訊顯示在遞送目標收件人的「跟蹤」頁籤和遞送的「跟蹤」頁籤中。

**提示**:預設情況下啟用消息跟蹤。 要配置URL，請在傳遞嚮導的下半部分選擇「顯示URL」選項。 對於消息的每個URL，您可以選擇是否激活跟蹤。

有關詳細資訊，請參閱 [配置跟蹤](how-to-configure-tracked-links.md) 的 [跟蹤指標](../../reporting/using/delivery-reports.md#tracking-indicators) 說明。

## 交付效能 {#delivery-performances}

要測量消息傳送的速度，可以控制傳送吞吐量。 標準是每小時發送的消息數和消息的大小（以位/秒為單位）。 有關此的詳細資訊，請參閱 [交付吞吐量](../../reporting/using/global-reports.md#delivery-throughput)。

**提示**:

* 不要在實例上將交貨保持為失敗狀態，因為這會維護臨時表並影響效能。

* 從資料庫中刪除不再需要的遞送和非活動收件人以保持地址質量。

* 不要嘗試將大型交貨安排在一起。 請注意，可能需要5到10分鐘才能將負載均勻地分佈在系統上。

## 傳遞疑難排解 {#delivery-troubleshooting}

遇到交貨問題時，可執行特定操作：

* [可交付性問題](../../production/using/performance-and-throughput-issues.md#deliverability_issues)

* [影像顯示問題](../../production/using/image-display-issues.md)

* [交付效能問題](delivery-performances.md)

* [臨時檔案問題](../../production/using/temporary-files.md) - *僅限本地客戶*
