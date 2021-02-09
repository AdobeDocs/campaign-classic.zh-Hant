---
solution: Campaign Classic
product: campaign
title: 在Adobe Campaign Classic中使用增強的MTA傳送
description: 瞭解使用Adobe Campaign Enhanced MTA傳送電子郵件的範圍和特定性。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 07ed17a093cb6fb2d7aae376325a127c61b1dcc2
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 2%

---


# 使用增強的MTA發送{#sending-with-enhanced-mta}

**Adobe Campaign Enhanced MTA**（郵件傳輸代理）提供升級的傳送基礎架構，可改善傳送能力、信譽、吞吐量、報告、彈回處理、IP提升和連線設定管理。

它的實作目的在於改善擴充性、提高傳送的總處理能力，並協助更快傳送更多電子郵件。 這是透過新的可調式傳送技術實現的，可根據來自網際網路服務供應商的意見回應即時變更電子郵件傳送設定。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA僅適用於Campaign Classic代管或混合型客戶。 無法升級Campaign Classic內部部署安裝，以使用增強的MTA。

如果您在2018年9月後已布建Campaign Classic例項，則您會使用增強的MTA。 對於所有其他Campaign Classic客戶，請參閱以下[常見問答](#enhanced-mta-faq)。

增強的MTA實作可能會影響部分現有的促銷活動功能。 有關詳細資訊，請參閱[增強的MTA特性](#enhanced-mta-impacts)。

## 常見問題 {#enhanced-mta-faq}

### 使用與優點

**什麼是增強的MTA?**

Adobe Campaign現在可升級為使用新的MTA（郵件傳輸代理），此MTA會執行SparkPost的商業電子郵件MTA，稱為&#x200B;**Momentum**。

Momentum代表創新、高效能的MTA技術，包括更聰明的彈回處理以及自動化傳送能力最佳化功能，可協助傳送者達到並維持最佳的收件匣傳送率。<!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**有哪些好處？**

* 使用「增強型MTA」的Adobe Campaign用戶端看到整體總處理能力速度大幅提升，軟彈回彈率大幅降低。<!--300%--><!--90%+-->
* 增強型MTA採用最新的MTA技術，為您的電子郵件傳送提供最佳的總處理能力。
* 它可立即自動地調整，以符合收到的意見，確保以即時傳送資料傳送更精確、更智慧的電子郵件。

**我是否可同時使用原生的Adobe Campaign MTA和增強的MTA?**

否. 在您的例項升級後，您的電子郵件傳送只能使用增強的MTA。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升級至增強的MTA

**升級至增強型MTA需要什麼？**

如果您在2018年9月後已布建Campaign Classic例項，則不需要採取任何動作，因為您已使用增強的MTA。

對於所有其他代管或部分代管（混合）客戶，Adobe Campaign團隊將會聯絡以協調移轉日期，並提供移轉所需適當步驟的詳細資訊。

>[!IMPORTANT]
>
>增強型MTA不適用於內部部署安裝。

**將我的實例升級到增強型MTA的過程是什麼？**

托管實例的整個流程需要幾分鐘的停機時間。 Adobe會在升級後24小時內監控電子郵件的吞吐量和傳遞能力，以評估對您電子郵件傳遞的任何影響。

如果發現任何問題，Adobe可以快速並暫時將您的例項回復回原生的Adobe Campaign MTA。

目前，「增強型MTA」只會影響電子郵件通道。 您的推播通知和簡訊傳送將繼續使用原生的促銷活動MTA，而且升級不會對它造成任何影響。

**升級至「增強的MTA」後，是否需要再次經歷IP變暖？**

否. 升級不需要切換到新的IP，因此您可以繼續使用現有的溫暖電子郵件IP。

**升級至「增強型MTA」是否會影響目前進行中的促銷活動或傳送？**

在您的實例升級為使用增強型MTA之前準備的任何交貨都需要重新準備，才能正確使用新的MTA。

對於使用Adobe Campaign交易傳訊功能的客戶，任何觸發電子郵件的API呼叫都會在短暫的升級停機期間排入佇列，並在升級完成時嘗試進行。

## 增強的MTA特異性{#enhanced-mta-impacts}

### 增強的MTA標題

最新的「促銷活動傳統型」例項包含程式碼，可將必要的「增強型MTA」標題新增至每則訊息。 如果您使用Adobe Campaign 19.1(build 9032)或更新版本，而且不是這樣，您必須將&quot;useMomentum=true&quot;參數新增至您的行銷實例設定（在[serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)檔案中）。

不過，如果您使用的舊例項不包含此程式碼，則必須將名為&#x200B;**[!UICONTROL Typology Rule for Enhanced MTAs]**的新排版規則新增至促銷活動例項中的所有現有排版。
此規則由作為升級至增強型MTA的一部分安裝的**[!UICONTROL Typology]**&#x200B;軟體包添加。

>[!IMPORTANT]
>
>如果您在您的排版中看到此排版規則，請勿以任何方式刪除或修改。 否則，您的電子郵件傳送可能會受到負面影響。

此&#x200B;**[!UICONTROL Typology]**&#x200B;套件必須安裝在Adobe Campaign行銷實例上。

如果您是混合式用戶端，Adobe Campaign團隊將提供如何在行銷實例上安裝&#x200B;**[!UICONTROL Typology]**&#x200B;套件的指示，以做為升級至增強型MTA的一部分。 請洽詢您的帳戶管理員以取得完整指示。

>[!IMPORTANT]
>
>Adobe Campaign團隊針對如何安裝&#x200B;**[!UICONTROL Typology]**&#x200B;套件提供的指示應謹慎遵循。 否則，您的IP傳送電子郵件時可能會遇到重大問題。

有關類型的詳細資訊，請參閱[本節](../../campaign/using/about-campaign-typologies.md)。

### 新的MX規則

不再使用MX管理傳送總處理能力規則。 增強型MTA有其專屬的MX規則，可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件的網域所提供的即時回應，依網域自訂您的吞吐量。

有關MX配置的詳細資訊，請參見[本節](../../installation/using/email-deliverability.md#mx-configuration)。

### 反彈資格

促銷活動&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表格中的反彈資格不再用於&#x200B;**synchronous**&#x200B;傳送失敗錯誤訊息。 「增強型MTA」會決定反彈類型和資格，並將該資訊傳回至「促銷活動」。

>[!NOTE]
>
>增強型MTA可讓SMTP彈回符合資格，並以對應至促銷活動彈回原因和資格的彈回碼形式，將該資格傳回促銷活動。

如需反彈資格的詳細資訊，請參閱[本節](../../delivery/using/understanding-delivery-failures.md#bounce-mail-qualification)。

### 使用增強的MTA傳送狀態

在電子郵件傳送[控制面板](../../delivery/using/delivery-dashboard.md)的&#x200B;**[!UICONTROL Summary]**&#x200B;檢視中，**[!UICONTROL Success]**&#x200B;百分比從100%開始，然後在傳送[有效期](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)期間逐漸降低，因為軟彈回彈和硬彈回會從增強的MTA回報至促銷活動。

事實上，當所有訊息從「促銷活動」成功中繼至「增強型MTA」時，傳送記錄檔[中的訊息都會顯示為&#x200B;**[!UICONTROL Sent]**。 ](../../delivery/using/delivery-dashboard.md#delivery-logs-and-history)除非或直到該訊息的[bounce](../../delivery/using/understanding-delivery-failures.md#delivery-failure-types-and-reasons)從增強的MTA傳回至促銷活動，否則這些訊息仍維持該狀態。

當硬彈回訊息從增強的MTA回報時，其狀態會從&#x200B;**[!UICONTROL Sent]**&#x200B;變更為&#x200B;**[!UICONTROL Failed]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比會相應降低。

當從增強的MTA回報軟反彈訊息時，仍會顯示為&#x200B;**[!UICONTROL Sent]**，且&#x200B;**[!UICONTROL Success]**&#x200B;百分比尚未更新。 然後，在傳送有效期間內，將[retryed](../../delivery/using/understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)軟彈跳消息：

* 如果重試在有效期結束前成功，則消息狀態將保持為&#x200B;**[!UICONTROL Sent]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比將保持不變。

* 否則，狀態變化為&#x200B;**[!UICONTROL Failed]**&#x200B;並相應地降低&#x200B;**[!UICONTROL Success]**&#x200B;百分比。

因此，您應等到有效期結束時，才能查看最終的&#x200B;**[!UICONTROL Success]**&#x200B;百分比，以及實際的&#x200B;**[!UICONTROL Sent]**&#x200B;和&#x200B;**[!UICONTROL Failed]**&#x200B;訊息的最終數字。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 傳送總處理能力

「促銷活動傳送」總處理量圖表將不再顯示您電子郵件收件者的總處理量。 該圖表現在會顯示從促銷活動傳送至增強MTA的訊息的中繼處理速度。

有關傳送吞吐量的詳細資訊，請參閱[本節](../../reporting/using/global-reports.md#delivery-throughput)。

### 有效期

只有在設為&#x200B;**3.5天或更短時間**&#x200B;時，「增強型MTA」才會使用「促銷活動」傳送中的有效期設定。 如果您在促銷活動中定義超過3.5天的值，則不會將其納入考量。

例如，如果有效期間設為促銷活動中5天的預設值，則軟反彈訊息會進入「增強的MTA」重試佇列，並在該訊息到達「增強的MTA」後，重試最多3.5天。 在這種情況下，將不會使用促銷活動中設定的值。

當訊息在 Enhanced MTA 佇列中停留 3.5 天且無法傳送時，訊息會逾時，其狀態會從傳送記錄檔中的 **[!UICONTROL Sent]** 更新為 **[!UICONTROL Failed]**。

有關有效期的詳細資訊，請參閱[本節](../../delivery/using/steps-sending-the-delivery.md#defining-validity-period)。

### DKIM簽署

DKIM(DomainKeys Indified Mail)電子郵件驗證簽署由增強的MTA完成。 在「增強的MTA」升級中，原生Campaign MTA的DKIM簽署將會在「網域管理」表格中關閉。
有關DKIM的詳細資訊，請參閱[本節](../../delivery/using/technical-recommendations.md#dkim)。