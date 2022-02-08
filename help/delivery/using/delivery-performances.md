---
product: campaign
title: 傳遞效能最佳實務
description: 瞭解有關交付效能和最佳做法的更多資訊。
feature: Deliverability
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 6%

---

# 傳遞效能最佳實務 {#delivery-performances}

![](../../assets/common.svg)

我們建議遵循以下指導原則，確保交貨順利進行，並檢查在遇到交貨問題時的執行情況。

**相關主題：**

* [傳遞儀表板](delivery-dashboard.md)
* [傳遞疑難排解](delivery-troubleshooting.md)
* [關於傳遞能力](about-deliverability.md)

## 最佳效能實踐 {#best-practices-performance}

* 不要在實例上將交貨保持為失敗狀態，因為這會維護臨時表並影響效能。

* 刪除不再需要的交貨。

* 在過去12個月中從資料庫中刪除的非活動收件人以保持地址質量。

* 不要嘗試將大型交貨安排在一起。 有5到10分鐘的間隔將負載均勻地分散到系統上。 與您團隊的其他成員協調交貨的時間安排以確保最佳效能。 當營銷伺服器同時處理許多不同的任務時，會降低效能。

* 盡可能小地保持電子郵件大小。 建議的電子郵件最大大小約為35KB。 電子郵件傳遞的大小在發送伺服器中生成一定數量的卷。

* 大型遞送（例如遞送給超過100萬收件人）需要在發送隊列中留出空間。 單單這一點對伺服器來說並不是問題，但是，如果再加上其他幾十個大型交付件同時全部送出，就會導致發送延遲。

* 電子郵件中的個性化功能可將每個收件人的資料從資料庫中取出。 如果存在許多個性化元素，則會增加準備交付所需的資料量。

* 索引地址。 要優化應用程式中使用的SQL查詢的效能，可以從資料架構的主要元素聲明索引。

>[!NOTE]
>
>ISP將在一段不活動時間後停用地址。 已退回的郵件會發送到發件人，以通知他們此新狀態。

## 效能問題核對表 {#performance-issues}

如果交貨效能不佳，您可以檢查：

* **交貨的大小**:大型交付可能需要更長時間才能完成。 MTA子級配置為處理預設批大小，該大小適用於大多數實例，但在交貨速度持續較慢時需要檢查。
* **交貨的目標**:交付效能受軟彈跳錯誤的影響，軟彈跳錯誤根據重試配置進行處理。 錯誤數越多，需要重試的次數就越多。
* **整體平台負載**:當發送多個大型交付時，整個平台可能受到影響。 您還可以檢查IP信譽和可交付性問題。 有關此內容的詳細資訊，請參閱 [此部分](about-deliverability.md) 和 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

平台和資料庫維護也會影響傳遞發送效能。 如需詳細資訊，請參閱[此頁面](../../production/using/database-performances.md)。
