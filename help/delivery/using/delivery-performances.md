---
product: campaign
title: 傳遞效能最佳實務
description: 進一步瞭解傳遞效能和最佳實務
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
role: User, Data Engineer
exl-id: cc793d7b-0a26-4a75-97ed-d79c87d9b3b8
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 5%

---

# 傳遞效能最佳實務 {#delivery-performances}

我們建議您遵循下列准則，以確保您的傳送執行良好，以及如果您遇到傳送問題時會檢查執行。

**相關主題：**

* [傳遞儀表板](delivery-dashboard.md)
* [傳遞疑難排解](delivery-troubleshooting.md)
* [關於傳遞能力](about-deliverability.md)

## 效能最佳實務 {#best-practices-performance}

* 請勿將傳遞在執行個體上維持在失敗狀態，因為這會維護臨時表格並影響效能。

* 移除不再需要的傳遞。

* 從資料庫移除過去12個月內非作用中的收件者，以維持地址品質。

* 請勿嘗試一起排程大型傳遞。 5-10分鐘的間隔可將負載均勻分散到系統上。 與團隊其他成員協調傳送排程，以確保最佳效能。 當行銷伺服器同時處理許多不同工作時，可能會降低效能。

* 儘可能縮小您的電子郵件。 建議的最大電子郵件大小約為35KB。 電子郵件傳遞的大小會在傳送伺服器中產生特定數量的磁碟區。

* 大型傳遞（例如傳送給超過一百萬位收件者的傳遞）需要傳送佇列中的空間。 伺服器本身不會因此發生問題，但若同時傳送數十筆其他大型郵件，可能會導致傳送延遲。

* 電子郵件中的個人化會將每個收件者的資料從資料庫中提取。 如果有許多個人化元素，會增加準備傳送所需的資料量。

* 索引位址。 為了最佳化應用程式中使用的SQL查詢效能，可以從資料結構描述的主要元素宣告索引。

>[!NOTE]
>
>ISP會在閒置一段時間後停用位址。 退回的訊息會傳送給寄件者，以通知他們此新狀態。

## 效能問題檢查清單 {#performance-issues}

如果傳送效能不佳，您可以檢查：

* **傳遞的大小**：大型傳送可能需要更長的時間才能完成。 MTA子系已設定為處理預設批次大小（這適用於大部分的執行個體），但在傳送速度持續緩慢時需要檢查。
* **傳遞的目標**：軟退信錯誤會影響傳遞效能，這些錯誤會根據重試設定處理。 錯誤數越多，所需的重試次數就越多。
* **整體平台負載**：傳送多個大型傳遞時，整體平台可能會受到影響。 您也可以檢查IP信譽和傳遞能力問題。 有關詳細資訊，請參閱 [本節](about-deliverability.md) 和 [Adobe傳遞性最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).

平台和資料庫維護也會影響傳遞傳送效能。 如需詳細資訊，請參閱[此頁面](../../production/using/database-performances.md)。
