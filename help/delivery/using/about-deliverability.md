---
product: campaign
title: 開始使用Campaign中的傳遞能力
description: 瞭解傳遞能力最佳實務
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Deliverability
role: User
exl-id: f301b34c-244c-4279-b23f-8224ea8eedbe
source-git-commit: b2b188ee3f202c247ceac1f59a49b7ad1771d537
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 6%

---

# 什麼是傳遞性{#about-deliverability}

可遞送性可讓您測量行銷活動在到達收件者收件匣時不會退回或標示為垃圾訊息的成功。 [瞭解傳遞能力重要的原因](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=zh-Hant#why-deliverability-matters)。

更準確地說，電子郵件傳遞能力指一組特性，這些特性決定訊息在短時間內透過個人電子郵件地址到達其目的地的能力，以及內容和格式的預期品質。

如需深入瞭解什麼是傳遞能力，並深入瞭解傳遞能力的重要術語、概念和方法，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

## 如何改善傳遞能力 {#deliverability-key-points}

傳遞能力問題通常與網際網路服務提供者和郵件伺服器管理員所實施的防止垃圾郵件的措施有關。

* 如需如何設計成功電子郵件行銷活動的一般建議，請參閱[傳遞能力策略和定義](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/deliverability-strategy-and-definition.html?lang=zh-Hant)。

* 如需如何最佳化Adobe Campaign電子郵件傳遞能力的更具體建議，Adobe建議使用本節所列的最佳實務。

>[!NOTE]
>
>由於ISP必須持續開發新的複雜篩選技術，以保護其客戶免受垃圾郵件傳送者的傷害，因此電子郵件傳遞能力的特點是標準和規則不斷變化。 請務必參閱定期更新的[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant)。

### 傳遞率

傳遞率是點選收件者收件匣的訊息數，與已傳遞的訊息數比較。 若要改善傳遞能力，您可以致力於提高此比率。

使用Adobe Campaign時，傳遞率取決於許多因素，特別是：

* 正確設定您的執行個體：請聯絡您的Adobe代表以尋求協助。
* 合法的網路組態：請參閱[網域設定和策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=zh-Hant#domain-setup-and-strategy)。
* 您的IP位址信譽：請參閱[IP策略](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=zh-Hant#ip-strategy)。
* 低[投訴](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/complaints.html?lang=zh-Hant)和[硬退信](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/metrics-for-deliverability/bounces.html?lang=zh-Hant#hard-bounces)率。
* 您的郵件內容：請參閱[控制電子郵件內容](control-message-content.md)。
* 訊息驗證(SPF、DKIM、DMARC)：請參閱[本節](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html?lang=zh-Hant#authentication)。
* 寄件者信譽：若要瞭解主要ISP如何評估寄件者信譽，請參閱[本節](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/internet-service-provider-specifics/overview.html?lang=zh-Hant)。

## Campaign傳遞工具 {#deliverability-tools}

<!--Adobe Campaign provides a number of tools designed to ensure optimal deliverability.-->
Adobe Campaign提供數個工具，用於追蹤及改善平台的可遞送性效能。 本頁也強調使用Campaign時，要最佳化傳遞能力應遵循的主要原則。

### 謹慎建立您的訊息

設定、設計和測試訊息時，請務必遵循下列區段提及的最佳實務。 運用Adobe Campaign提供的所有功能，協助您改善傳遞能力。

* [傳遞最佳實務](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=zh-Hant){target="_blank"}。
* [控制電子郵件內容](control-message-content.md)
* [收件匣轉譯](inbox-rendering.md)
* [傳送校樣](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/validate/preview-and-proof.html?lang=zh-Hant){target="_blank"}

### 透過雙重選擇加入驗證同意 {#double-opt-in}

為避免傳送訊息至無效地址、限制不當通訊並改善寄件者信譽，Adobe建議實作雙重選擇加入機制。 此方法可讓您確保收件者會刻意訂閱。

如需詳細資訊，請參閱[建立雙重選擇加入的訂閱表單](../../web/using/use-cases-web-forms.md#create-a-subscription--form-with-double-opt-in)。

如需從客戶收集資料的最佳實務的詳細資訊，請參閱[Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/first-impressions/address-collection-and-list-growth.html?lang=zh-Hant#data-quality-and-hygiene)。

### 利用隔離管理

Adobe Campaign管理的清單會收集持續發生的垃圾郵件投訴、硬跳出和軟跳出。

為了保護您的傳送能力，該清單中地址在清單中的收件者預設會從所有未來的傳送中排除，因為傳送給這些聯絡人可能會損害您的傳送信譽。

如果無效地址的比率過高，某些網際網路存取提供者會自動將電子郵件視為垃圾郵件。因此，隔離可讓您避免被這些提供者新增到封鎖清單中。

如需詳細資訊，請參閱下列章節：

* [瞭解傳遞失敗](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/delivery-failures){target="_blank"} （Campaign v8檔案 — 完整指南）
* [瞭解隔離管理](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/monitor/quarantines){target="_blank"} （Campaign v8檔案 — 完整指南）

### 使用監控和報告工具

使用Adobe Campaign提供的功能來監控您的傳送能力。

Adobe Campaign可讓您透過一組內建的即時指標和報表，檢查傳遞的執行方式，以改進傳遞的insight。

如需詳細資訊，請參閱下列章節：

* [開始使用傳遞監視](about-delivery-monitoring.md)
* [開始使用Campaign內建報告](../../reporting/using/about-campaign-built-in-reports.md)
