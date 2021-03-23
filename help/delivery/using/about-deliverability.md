---
solution: Campaign Classic
product: campaign
title: 關於Campaign中的傳遞能力
description: 瞭解傳遞能力最佳實務
audience: delivery
content-type: reference
topic-tags: deliverability-management
translation-type: tm+mt
source-git-commit: 0420de856d1506ab92d8f0e0824bf439e0ac7dc7
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 5%

---


# 什麼是傳遞能力{#about-deliverability}

傳遞能力可讓您測量促銷活動在到達收件者收件匣時是否成功，而不會反彈或標示為垃圾訊息。 [瞭解傳遞能力為何重要](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters)。

更準確地說，電子郵件傳遞能力是指一組特性，這些特性決定了郵件通過個人電子郵件地址在短時間內到達其目的地的能力，並且在內容和格式方面具有預期的質量。

如需深入瞭解何謂可交付性，並進一步瞭解關鍵可交付性術語、概念和方法，請參閱[Adobe可交付性最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)。

## 如何提高傳遞能力{#deliverability-key-points}

傳遞能力問題通常與網際網路服務提供商和郵件伺服器管理員實施的針對垃圾郵件的保護措施有關。

* 有關如何設計成功電子郵件行銷活動的一般建議，請參閱[傳遞性策略和定義](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html)。

* 有關如何最佳化Adobe Campaign電子郵件傳遞能力的更多具體建議，Adobe建議使用本節所列的最佳實務。

>[!NOTE]
>
>由於ISP必須不斷開發新的精密過濾技術，以保護客戶免受垃圾郵件發送者的侵擾，因此電子郵件傳遞的特點是標準和規則不斷變化。 請務必參考定期更新的[Adobe交付能力最佳實踐指南。](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html)

### 可交付性率

傳遞能力比率是點擊收件者收件箱的訊息數，與傳送的訊息數相比。 為了改善傳遞能力，您可能會努力提高此比率。

在Adobe Campaign，可交付率取決於眾多因素，特別是：

* 正確配置實例：請洽詢您的Adobe代表以取得協助。
* 合法的網路配置：請參閱[本節](../../delivery/using/optimize-delivery.md#network-config)和[域設定和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy)。
* 您的IP位址信譽：請參閱[IP策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy)。
* 目標地址的質量：請參閱[隔離管理](../../delivery/using/optimize-delivery.md#quarantine-management)。
* 低[投訴](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html)和[硬反彈](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces)率。
* 您的訊息內容：請參閱[控制電子郵件內容](../../delivery/using/control-message-content.md)。
* 消息驗證(SPF、DKIM、DMARC):請參閱[本節](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。
* 發件人信譽：要瞭解主要ISP如何評估發件人信譽，請參閱[本節](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html)。

## 促銷活動傳遞性工具{#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供數種工具來追蹤並改善您平台的傳遞效能。 本頁也強調您在使用Campaign時應牢記的最佳化傳遞能力的主要原則。

### 仔細建構您的訊息

在設定、設計和測試訊息時，請務必遵循下列章節中提及的最佳實務。 運用Adobe Campaign提供的所有功能，協助您提高傳遞能力。

* [傳遞最佳實務](../../delivery/using/delivery-best-practices.md)
* [控管電子郵件內容](../../delivery/using/control-message-content.md)
* [收件匣轉譯](../../delivery/using/inbox-rendering.md)
* [傳送證明](../../delivery/using/steps-validating-the-delivery.md#sending-a-proof)

### 透過雙重選擇加入{#double-opt-in}來驗證同意

為避免將消息發送到無效地址、限制不當通信並改善發件人信譽，Adobe建議實施雙重選擇加入機制。 此方法可讓您確保收件者有意訂閱。

如需詳細資訊，請參閱[建立雙重選擇加入的訂閱表單。](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)

有關從客戶收集資料時的最佳實踐的詳細資訊，請參閱[Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene)。

### 利用隔離管理

Adobe Campaign管理的清單會收集垃圾郵件投訴、硬性回報和軟性回報，而這些回報會一貫發生。

為了保護您的傳送能力，該清單上地址的收件者預設會從所有未來傳送中排除，因為傳送給這些連絡人可能會損害您的傳送信譽。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者添加到拒絕清單。

如需詳細資訊，請參閱下列章節：

* [瞭解傳送故障](../../delivery/using/understanding-delivery-failures.md)
* [瞭解隔離管理](../../delivery/using/understanding-quarantine-management.md)
* [隔離與拒絕清單](../../delivery/using/understanding-quarantine-management.md#quarantine-vs-denylist)

### 使用監控和報告工具

使用Adobe Campaign提供的功能監控您的傳遞能力。

Adobe Campaign可讓您透過一組內建的即時指標和報表，來檢查傳送的效能，以進一步瞭解傳送。

如需詳細資訊，請參閱下列章節：

* [監視傳遞能力](../../delivery/using/monitoring-deliverability.md)
* [關於傳送監控](../../delivery/using/about-delivery-monitoring.md)
* [關於 Campaign 內建的報表](../../reporting/using/about-campaign-built-in-reports.md)

<!--TO REMOVE
## Background {#background}

Email deliverability presents a major challenge to marketers - whether they're sending a few thousand messages or several billion. One in five messages never reach the inbox, or their intended recipient.

Once relegated as a "technical issue" for the IT department, email deliverability continues to move higher on the marketing agenda. That's because savvy marketers recognize that although many of its elements are technical in nature, deliverability is ultimately a business issue with significant revenue implications.

Consider the email marketing funnel. Deliverability determines the number of messages received, which in turn impacts each subsequent stage of the funnel. Fewer emails received results in fewer opens, fewer clicks, and fewer conversions. **For companies with a large database, the difference between average and great deliverability could literally mean hundreds of thousands to millions of dollars in revenues.**

![](assets/deliverability_overview_1.png)

By settling for average (80%) deliverability, marketers are leaving significant conversions - and dollars - on the table.

What exactly is email deliverability? And how can marketers improve deliverability rates to widen the mouth of the funnel and squeeze more results from their email campaigns?

Email deliverability refers to the set of characteristics that determine a message's ability to reach its destination, via a personal e-mail address, within a short time, and with the expected quality in terms of content and format. These characteristics fall into four main categories: data quality, message and content, sending infrastructure, and reputation. Together, they form the foundation of a successful email deliverability program. This overview outlines the four fundamentals of email deliverability success and offers best practices for reaching the inbox and driving greater revenues from email marketing programs.

![](assets/deliverability_overview_2.png)-->
