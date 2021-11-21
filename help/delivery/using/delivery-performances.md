---
product: campaign
title: 傳遞效能最佳實務
description: 進一步了解傳遞效能和最佳實務。
audience: delivery
content-type: reference
topic-tags: monitoring-deliveries
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 6%

---

# 傳遞效能最佳實務 {#delivery-performances}

![](../../assets/common.svg)

建議您遵循下列准則，確保您的傳送順利執行，並在您遇到傳送問題時檢查執行。

**相關主題：**

* [傳遞儀表板](delivery-dashboard.md)
* [傳遞疑難排解](delivery-troubleshooting.md)
* [關於傳遞能力](about-deliverability.md)

## 效能最佳實務 {#best-practices-performance}

* 請勿在執行個體上將傳送保持為失敗狀態，因為這會維護臨時表格並影響效能。

* 移除不再需要的傳送。

* 過去12個月內非活動的收件者，將從資料庫中移除，以維持地址品質。

* 請勿嘗試將大型傳送排程在一起。 有5-10分鐘的間隔，使負載均勻地分佈在系統上。 與團隊的其他成員協調傳送排程，以確保最佳效能。 當行銷伺服器同時處理許多不同的工作時，可能會降低效能。

* 盡可能縮小電子郵件的大小。 建議的電子郵件大小上限約為35KB。 電子郵件傳送的大小會在傳送伺服器中產生特定數量的卷。

* 大型傳送（例如傳送給超過100萬個收件者）需要在傳送佇列中有空間。 僅此對伺服器而言並不重要，但若與數十個其他大型傳送同時進行，可能會造成傳送延遲。

* 電子郵件中的個人化會將每個收件者的資料從資料庫中提取。 如果有許多個人化元素，會增加準備傳送所需的資料量。

* 索引地址。 要優化應用程式中使用的SQL查詢的效能，可以從資料架構的主要元素聲明索引。

>[!NOTE]
>
>ISP會在閒置一段時間後停用位址。 已跳出的郵件將發送到發件人，以通知他們此新狀態。

## 效能問題檢查清單 {#performance-issues}

如果傳送效能不佳，您可以檢查：

* **傳送的大小**:大型傳送可能需要更長的時間才能完成。 MTA子項設定為處理預設批次大小，此大小適用於大部分執行個體，但當傳送持續緩慢時，需要加以檢查。
* **傳遞的目標**:傳送效能禁止受軟退信錯誤影響，這些錯誤會根據重試配置處理。 錯誤數越多，重試次數就越多。
* **整體平台負載**:當傳送數個大型傳送時，整體平台可能會受到影響。 您也可以檢查IP信譽和傳遞能力問題。 有關詳細資訊，請參閱 [本節](about-deliverability.md) 和 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).

平台和資料庫維護也會影響傳遞傳送效能。 如需詳細資訊，請參閱[此頁面](../../production/using/database-performances.md)。
