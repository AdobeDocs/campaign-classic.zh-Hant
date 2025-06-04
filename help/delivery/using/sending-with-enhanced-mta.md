---
product: campaign
title: 使用Adobe Campaign Classic中的增強型MTA傳送
description: 瞭解使用Adobe Campaign Enhanced MTA傳送電子郵件的範圍和特性
feature: Email
role: User, Admin, Developer
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: b353b562bd2f0b0bd2dfde22c6477ab66d499483
workflow-type: tm+mt
source-wordcount: '1368'
ht-degree: 1%

---

# 使用增強的MTA傳送 {#sending-with-enhanced-mta}

**Adobe Campaign Enhanced MTA** （郵件傳輸代理程式）提供升級的傳送基礎架構，可改善傳遞能力、信譽、輸送量、報告、退信處理、IP提升及連線設定管理。

實作它可改善擴充性、提高傳送輸送量，並協助更快速地傳送更多電子郵件。 這是透過新的適應性傳送技術達成，該技術會根據網際網路服務提供者的意見來即時變更電子郵件傳送設定。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA僅適用於Campaign Classic託管或混合型客戶。 Campaign Classic內部部署安裝無法升級為使用增強型MTA。

如果您在2018年9月之後布建Campaign Classic執行個體，則使用增強型MTA。 若是其他所有Campaign Classic客戶，請參閱下列[常見問題](#enhanced-mta-faq)。

增強的MTA實作可能會影響部分現有的Campaign功能。 如需詳細資訊，請參閱[增強型MTA規格](#enhanced-mta-impacts)。

>[!NOTE]
>
>如果您是Adobe Campaign的一般使用者，且想瞭解您的執行個體是否已升級至增強型MTA，請聯絡您的內部Campaign管理員。

## 常見問題 {#enhanced-mta-faq}

### 使用狀況和優點

**什麼是Enhanced MTA？**

Adobe Campaign現在可以升級，使用新的MTA （郵件傳輸代理程式），執行SparkPost的商業電子郵件MTA （稱為&#x200B;**Momentum**）。

Momentum代表創新的高效能MTA技術，包括更聰明的彈回處理以及自動化傳遞能力最佳化功能，可協助寄件者達成並維持最佳收件匣傳遞率。<!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**有哪些優點？**

* 使用Enhanced MTA的Adobe Campaign使用者端已發現<!--300%-->整體輸送量速度大幅提升，以及<!--90%+-->軟跳出大幅減少。
* Enhanced MTA使用最新的MTA技術，為您提供最佳的電子郵件傳送輸送速度。
* 透過即時且自動地調整它收到的意見回饋，它還可以確保使用即時傳遞資料進行更精確且更智慧的電子郵件傳遞。

**我可以同時使用原生Adobe Campaign MTA和Enhanced MTA嗎？**

沒有。升級執行個體後，只有增強型MTA可用於電子郵件傳遞。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升級至增強的MTA

**升級為增強型MTA需要哪些條件？**

如果您在2018年9月之後布建Campaign Classic執行個體，則不需要採取任何動作，因為您已使用增強型MTA。

對於所有其他託管或部分託管（混合）客戶，Adobe Campaign團隊會聯絡以協調移轉日期，並提供移轉所需適當步驟的詳細資訊。

>[!IMPORTANT]
>
>Enhanced MTA不適用於內部部署。

**將我的執行個體升級至增強型MTA的程式為何？**

託管執行個體的整個程式需要幾分鐘的停機時間。 Adobe在升級後最多24小時都會監控電子郵件輸送量和傳遞能力，以評估對電子郵件傳遞的任何影響。

如果發現任何問題，Adobe可以快速將您的執行個體暫時恢復為原生Adobe Campaign MTA。

目前，增強型MTA只會影響電子郵件頻道。 您的推播通知和SMS傳送將繼續使用原生Campaign MTA，且不會受到升級任何影響。

**升級為增強型MTA後，我是否需要再次進行IP預熱？**

沒有。升級不需要切換到新的IP，因此您可以繼續使用現有的已預熱電子郵件IP。

**升級到增強型MTA是否會影響目前進行中的任何行銷活動或傳遞？**

對於使用Adobe Campaign交易訊息功能的客戶，任何觸發電子郵件的API呼叫都將在極短的升級停機期間排入佇列，並將在升級完成後嘗試。

## 增強的MTA規格 {#enhanced-mta-impacts}

### 新MX規則

不再使用MX管理傳遞輸送量規則。 Enhanced MTA有自己的MX規則，可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時回饋，而依網域來自訂您的輸送量。

有關MX組態的詳細資訊，請參閱[本節](../../installation/using/email-deliverability.md#mx-configuration)。

### 退信資格

促銷活動&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;資料表中的退信限定不再用於&#x200B;**同步**&#x200B;傳遞失敗錯誤訊息。 增強型MTA會決定退信型別和資格，並將該資訊傳回至Campaign。

>[!NOTE]
>
>Enhanced MTA會符合SMTP退回資格，並以對應至Campaign退回原因和資格的退回代碼形式將該資格傳送回Campaign。

如需退信資格的詳細資訊，請參閱[本節](understanding-delivery-failures.md#bounce-mail-qualification)。

### 傳遞

一旦傳遞已傳輸至Enhanced MTA，就無法停止 — 即使它在Campaign中顯示為&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態。

### 傳遞總處理能力

Campaign傳送輸送量圖表將不再顯示傳送給電子郵件收件者的輸送量。 該圖表現在會顯示從Campaign轉送訊息至Enhanced MTA的輸送量速度。

如需傳遞輸送量的詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。

### 重試次數

Campaign不再使用傳送中的重試設定。 軟退信重試次數和兩次之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

如需重試的詳細資訊，請參閱[本節](steps-sending-the-delivery.md#configuring-retries)。

### 有效期限

只有當設定為&#x200B;**3.5天或更短時間時，Enhanced MTA才會使用您的Campaign傳遞中的有效期間設定**。 如果您在Campaign中定義的值超過3.5天，則不會考慮該值。

例如，如果有效期間在Campaign中設定為預設值5天，則軟退信訊息將進入Enhanced MTA重試佇列，並從該訊息達到Enhanced MTA時起最多只重試3.5天。 在此情況下，將不會使用Campaign中設定的值。

當訊息在Enhanced MTA佇列中停留3.5天且無法傳送時，訊息會逾時，其狀態會從傳送記錄檔中的&#x200B;**[!UICONTROL Sent]**&#x200B;更新為&#x200B;**[!UICONTROL Failed]**。

如需有效期的詳細資訊，請參閱[本節](steps-sending-the-delivery.md#defining-validity-period)。

### DKIM簽署

DKIM (DomainKeys Indified Mail)電子郵件驗證簽署是由Enhanced MTA完成。 原生Campaign MTA的DKIM簽署功能將會在Enhanced MTA升級過程中，於網域管理表格內關閉。
如需DKIM的詳細資訊，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 傳遞成功報告

在電子郵件傳遞[儀表板](delivery-dashboard.md)的&#x200B;**[!UICONTROL Summary]**&#x200B;檢視中，**[!UICONTROL Success]**&#x200B;百分比從100%開始，然後在傳遞[有效期間](steps-sending-the-delivery.md#defining-validity-period)內逐步下降，因為軟跳出和硬跳出會從Enhanced MTA回報回Campaign。

事實上，一旦訊息成功從Campaign轉送至Enhanced MTA，在[傳送記錄檔](delivery-dashboard.md#delivery-logs-and-history)中，所有訊息都會顯示為&#x200B;**[!UICONTROL Sent]**。 除非或直到該訊息的[跳出](understanding-delivery-failures.md#delivery-failure-types-and-reasons)從Enhanced MTA傳回Campaign，否則它們會維持該狀態。

當硬退信從Enhanced MTA回傳時，其狀態會從&#x200B;**[!UICONTROL Sent]**&#x200B;變更為&#x200B;**[!UICONTROL Failed]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比會因此減少。

當從Enhanced MTA回報軟退信時，訊息仍顯示為&#x200B;**[!UICONTROL Sent]**，且&#x200B;**[!UICONTROL Success]**&#x200B;百分比尚未更新。 然後，軟退信會在整個傳遞有效期內重試[&#128279;](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)：

* 如果在有效期間結束前重試成功，則訊息狀態會維持為&#x200B;**[!UICONTROL Sent]**，**[!UICONTROL Success]**&#x200B;百分比會維持不變。

* 否則，狀態會變更為&#x200B;**[!UICONTROL Failed]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比會相應減少。

因此，您應該等到有效期間結束，才能看到最後&#x200B;**[!UICONTROL Success]**&#x200B;個百分比，以及實際&#x200B;**[!UICONTROL Sent]**&#x200B;和&#x200B;**[!UICONTROL Failed]**&#x200B;個訊息的最終數量。

下表顯示傳送程式的不同步驟以及對應的KPI和傳送記錄檔狀態。

| 傳送程式中的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從Campaign轉送至增強型MTA | **[!UICONTROL Success]**&#x200B;百分比從100%開始 | 已傳送 |
| 系統會從Enhanced MTA回報硬跳出訊息 | **[!UICONTROL Success]**&#x200B;百分比會相應減少 | 失敗 |
| 系統會從Enhanced MTA回報軟退信訊息 | **[!UICONTROL Success]**&#x200B;百分比沒有變更 | 已傳送 |
| 軟退信重試成功 | **[!UICONTROL Success]**&#x200B;百分比沒有變更 | 已傳送 | **[!UICONTROL Success]**&#x200B;百分比會相應增加 | 已傳送 |
| 軟退信重試失敗 | **[!UICONTROL Success]**&#x200B;百分比會相應減少 | 失敗 |

