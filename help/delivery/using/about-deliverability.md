---
product: campaign
title: 開始使用Campaign中的傳遞能力
description: 了解傳遞能力最佳實務
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Deliverability
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 8%

---

# 什麼是傳遞性{#about-deliverability}



傳遞能力可讓您測量到達收件者收件匣的促銷活動是否成功，而不會反彈或標示為垃圾訊息。 [了解傳遞能力為何重要](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters).

更準確地說，電子郵件傳遞是指一組特性，這些特性決定了郵件通過個人電子郵件地址在短時間內到達目的地的能力，並且在內容和格式方面具有預期的質量。

如需深入了解什麼是傳遞能力，以及深入了解關鍵傳遞能力條款、概念和方法，請參閱 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).

## 如何改善傳遞能力 {#deliverability-key-points}

傳遞能力問題通常與網際網路服務提供商和郵件伺服器管理員實施的針對垃圾郵件的保護措施有關。

* 如需如何設計成功的電子郵件行銷活動的一般建議，請參閱 [傳遞能力策略和定義](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html).

* 如需如何最佳化Adobe Campaign電子郵件傳遞能力的更具體建議，Adobe建議使用本節所列的最佳實務。

>[!NOTE]
>
>由於ISP必須不斷開發新的複雜過濾技術來保護其客戶免受垃圾郵件發送者的侵害，因此電子郵件傳遞的特徵是不斷變化的標準和規則。 請務必參閱 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant) 定期更新。

### 傳遞率

傳遞率是點擊收件者收件匣的訊息數，與已傳遞的訊息數相比。 為了改善傳遞能力，您可以提高此速率。

有了Adobe Campaign，傳遞率取決於眾多因素，尤其是：

* 正確配置實例：請連絡您的Adobe代表以取得協助。
* 合法的網路配置：請參閱 [本節](optimize-delivery.md#network-config) 和 [域設定和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy).
* 您的IP地址信譽：請參閱 [IP策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy).
* 目標地址的質量：請參閱 [隔離管理](optimize-delivery.md#quarantine-management).
* 低 [投訴](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) 和 [硬跳出](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) 比率。
* 您的訊息內容：請參閱 [控制電子郵件內容](control-message-content.md).
* 報文驗證(SPF、DKIM、DMARC):請參閱 [本節](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).
* 發件人信譽：若要了解主要ISP如何評估寄件者信譽，請參閱 [本節](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html).

## Campaign傳遞工具 {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供數種工具，可追蹤及改善您平台的傳遞效能。 本頁也著重說明使用Campaign時，您應謹記的主要原則，以最佳化傳遞能力。

### 小心建立訊息

設定、設計和測試訊息時，請務必遵循以下各節提及的最佳實務。 運用Adobe Campaign提供的所有功能，協助您改善傳遞能力。

* [關於傳遞的最佳實務](delivery-best-practices.md)
* [控制電子郵件內容](control-message-content.md)
* [收件匣轉譯](inbox-rendering.md)
* [傳送證明](steps-validating-the-delivery.md#sending-a-proof)

### 透過雙重加入驗證同意 {#double-opt-in}

為避免傳送訊息至無效位址、限制不當通訊並改善寄件者信譽，Adobe建議實作雙重加入機制。 此方法可讓您確保收件者有意訂閱。

如需詳細資訊，請參閱[建立雙重選擇加入的訂閱表單](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

如需從客戶收集資料時的最佳實務，請參閱 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene).

### 利用隔離管理

Adobe Campaign會管理可收集持續發生的垃圾訊息投訴、硬退信及軟退信的清單。

為了保護您的傳遞能力，預設情況下，將排除其地址在該清單上的收件人，使其不參與將來的所有傳遞，因為向這些聯繫人發送郵件可能會損害您的發送信譽。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者新增至封鎖清單。

如需詳細資訊，請參閱下列章節：

* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [認識隔離管理](understanding-quarantine-management.md)
* [隔離與封鎖清單](understanding-quarantine-management.md#quarantine-vs-denylist)

### 使用監控和報告工具

使用Adobe Campaign提供的功能監控您的傳遞能力。

Adobe Campaign可讓您透過一組內建的即時指標和報表，來檢查傳送的成效，以改善傳送的深入分析。

如需詳細資訊，請參閱下列章節：

* [監視傳遞能力](monitoring-deliverability.md)
* [開始使用傳遞監視](about-delivery-monitoring.md)
* [開始使用Campaign內建的報表](../../reporting/using/about-campaign-built-in-reports.md)
