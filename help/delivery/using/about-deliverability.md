---
product: campaign
title: 在市場活動中開始提供性
description: 瞭解交付能力最佳做法
feature: Deliverability
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 8%

---

# 什麼是傳遞性{#about-deliverability}

![](../../assets/common.svg)

可遞送性允許您測量活動到達收件人收件箱的成功程度，而不會彈跳或標籤為垃圾郵件。 [瞭解為什麼交付性很重要](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html#why-deliverability-matters)。

更準確地說，電子郵件傳送能力是指一組特徵，這些特徵決定了郵件在短時間內通過個人電子郵件地址到達其目的地的能力，並且在內容和格式方面具有預期的質量。

要深入瞭解什麼是可交付性，並瞭解關鍵可交付性術語、概念和方法的更多資訊，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

## 如何提高可交付性 {#deliverability-key-points}

傳遞性問題通常與網際網路服務提供商和郵件伺服器管理員實施的針對垃圾郵件的保護措施有關。

* 有關如何設計成功的電子郵件營銷活動的一般建議，請參閱 [可交付性策略和定義](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html)。

* 有關如何優化Adobe Campaign電子郵件的可傳送性的更具體建議，Adobe建議使用本節中列出的最佳做法。

>[!NOTE]
>
>由於ISP必須不斷開發新的複雜過濾技術來保護其客戶免受垃圾郵件發送者的侵害，因此電子郵件發送能力的特點是標準和規則不斷變化。 確保您引用 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html) 定期更新。

### 交付率

Deliverability rate是與已傳送的郵件數相比，命中收件人收件箱的郵件數。 為了提高交付能力，您可以努力提高此速率。

在Adobe Campaign，供應率取決於諸多因素，特別是：

* 正確配置實例：請與Adobe代表聯繫以獲得幫助。
* 合法網路配置：見 [此部分](optimize-delivery.md#network-config) 和 [域設定和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#domain-setup-and-strategy)。
* 您的IP地址信譽：見 [IP策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#ip-strategy)。
* 目標地址的質量：見 [隔離管理](optimize-delivery.md#quarantine-management)。
* 低 [投訴](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html) 和 [硬彈](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html#hard-bounces) 利率。
* 您的消息內容：見 [控制電子郵件內容](control-message-content.md)。
* 消息驗證(SPF、DKIM、DMARC):見 [此部分](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。
* 發件人信譽：要瞭解主要ISP如何評估發件人信譽，請參閱 [此部分](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html)。

## 市場活動交付工具 {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供了多種工具來跟蹤和改進您的平台的交付效能。 此頁還重點介紹了在使用市場活動時優化交付能力時應牢記的主要原則。

### 小心構建您的消息

在配置、設計和測試消息時，請確保遵循下面各節中提到的最佳做法。 利用Adobe Campaign提供的所有功能可幫助您提高交付能力。

* [關於傳遞的最佳實務](delivery-best-practices.md)
* [控制電子郵件內容](control-message-content.md)
* [收件匣轉譯](inbox-rendering.md)
* [傳送證明](steps-validating-the-delivery.md#sending-a-proof)

### 通過雙重選擇加入驗證同意 {#double-opt-in}

為避免向無效地址發送消息、限制不當通信並改善發送者信譽，Adobe建議實施雙重選擇加入機制。 通過此方法，您可以確保您的收件人有意訂閱。

如需詳細資訊，請參閱[建立雙重選擇加入的訂閱表單](../../web/using/use-cases--web-forms.md#create-a-subscription--form-with-double-opt-in)。

有關從客戶收集資料時的最佳做法的詳細資訊，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html#data-quality-and-hygiene)。

### 利用隔離管理

Adobe Campaign管理一個收集垃圾郵件投訴、硬回報和軟回報的清單，這些內容始終如一地發生。

為了保護您的交貨能力，預設情況下，其地址位於該清單中的收件人將排除在所有將來的交貨之外，因為發送到這些聯繫人可能會損害您的發送信譽。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離允許您避免被這些提供程式添加到denylist中。

有關詳細資訊，請參閱以下各節：

* [瞭解傳遞失敗](understanding-delivery-failures.md)
* [認識隔離管理](understanding-quarantine-management.md)
* [隔離與密文清單](understanding-quarantine-management.md#quarantine-vs-denylist)

### 使用監控和報告工具

使用Adobe Campaign提供的功能監控您的交付能力。

Adobe Campaign允許您通過一組內置即時指示器和報告來檢查交貨的情況，以便更好地瞭解交貨情況。

有關詳細資訊，請參閱以下各節：

* [監視可交付性](monitoring-deliverability.md)
* [開始使用傳遞監視](about-delivery-monitoring.md)
* [開始使用活動內置報告](../../reporting/using/about-campaign-built-in-reports.md)
