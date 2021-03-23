---
solution: Campaign Classic
product: campaign
title: 傳遞效能最佳實務
description: 進一步瞭解傳送效能和最佳實務。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
translation-type: tm+mt
source-git-commit: 8bf1b5b1a6763cf933d86f2af61b2bb68e870222
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 5%

---


# 傳遞效能最佳實務 {#delivery-performances}

我們建議您遵循以下准則，以確保您的傳送順利執行，並檢查您遇到傳送問題時的執行。

**相關主題：**

* [傳遞儀表板](../../delivery/using/delivery-dashboard.md)
* [傳遞疑難排解](../../delivery/using/delivery-troubleshooting.md)
* [關於傳遞能力](../../delivery/using/about-deliverability.md)

## 效能{#best-practices-performance}的最佳做法

* 請勿在實例上將交貨保持為失敗狀態，因為這會維護臨時表並影響效能。

* 移除不再需要的傳送。

* 過去12個月中非活動的收件者將從資料庫中刪除，以保持地址質量。

* 請勿嘗試排程大型傳送。 在系統上均勻分配負載需要5-10分鐘。 與團隊中的其他成員協調交貨排程，以確保最佳效能。 當行銷伺服器同時處理許多不同的工作時，可能會降低效能。

* 盡量將電子郵件的大小保持在最低。 建議的電子郵件大小上限為35KB。 電子郵件傳送的大小會在傳送伺服器中產生一定數量的卷。

* 大型傳送（例如傳送給超過1百萬個收件者）需要在傳送佇列中有空間。 僅此一項對伺服器而言並不是問題，但是，當搭配數十種其他大型傳送裝置同時進行時，可能會造成傳送延遲。

* 電子郵件中的個人化會從資料庫中提取每個收件者的資料。 如果有許多個人化元素，會增加準備傳送所需的資料量。

* 索引地址。 要優化應用程式中使用的SQL查詢的效能，可以從資料模式的主元素中聲明索引。

>[!NOTE]
>
>ISP會在閒置一段時間後停用位址。 已退回的訊息會傳送給寄件者，通知他們此新狀態。

## 效能問題檢查清單{#performance-issues}

如果傳送效能不佳，您可以檢查：

* **傳送的大小**:大型傳送可能需要更長的時間才能完成。MTA子系設定為處理預設批次大小，這適用於大部分的例項，但傳送速度持續緩慢時，需要加以檢查。
* **傳送的目標**:傳送效能禁止受到軟反彈錯誤的影響，這些錯誤會根據重試設定進行處理。錯誤數越多，則需要重試的次數越多。
* **整體平台負載**:當傳送數個大型傳送時，整體平台可能會受到影響。您也可以檢查IP信譽和傳遞性問題。 有關詳細資訊，請參閱[本部分](../../delivery/using/about-deliverability.md)和[Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。

平台與資料庫維護也會影響傳送傳送的效能。 有關詳細資訊，請參見[此頁面](../../production/using/database-performances.md)。
