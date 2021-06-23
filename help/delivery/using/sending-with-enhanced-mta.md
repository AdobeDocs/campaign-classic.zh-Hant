---
product: campaign
title: 在Adobe Campaign Classic中使用Enhanced MTA傳送
description: 了解使用Adobe Campaign Enhanced MTA傳送電子郵件的範圍和特性。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: a129f49d4f045433899fd7fdbd057fb16d0ed36a
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 3%

---

# 使用增強的 MTA 傳送 {#sending-with-enhanced-mta}

**Adobe Campaign Enhanced MTA**（郵件傳輸代理）提供了升級的發送基礎架構，可改善傳遞能力、信譽、吞吐量、報告、退信處理、IP升級和連接設定管理。

實作該指南的目的是改善可擴充性、提高傳遞吞吐量，並協助更快傳送更多電子郵件。 這是透過新的最適化傳送技術來達成，這些技術會根據來自網際網路服務提供者的意見即時變更電子郵件傳送設定。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA僅適用於托管Campaign Classic或混合型客戶。 Campaign Classic內部部署安裝無法升級為使用Enhanced MTA。

如果您在2018年9月之後布建了Campaign Classic例項，表示您使用的是Enhanced MTA。 對於所有其他Campaign Classic客戶，請參閱下方的[常見問題集](#enhanced-mta-faq)。

Enhanced MTA實作可能會影響部分現有的Campaign功能。 有關詳細資訊，請參閱[Enhanced MTA特異性](#enhanced-mta-impacts)。

>[!NOTE]
>
>如果您是Adobe Campaign的一般使用者，且想知道您的執行個體是否已升級至Enhanced MTA，請連絡您的內部Campaign管理員。

## 常見問題 {#enhanced-mta-faq}

### 使用與優點

**什麼是Enhanced MTA?**

Adobe Campaign現在可以升級為使用新的MTA（郵件傳輸代理），該代理會執行SparkPost名為&#x200B;**Momentum**&#x200B;的商業電子郵件MTA。

Momentum代表創新、高效能的MTA技術，包括更智慧的退信處理和自動化的傳遞能力優化功能，可幫助發件人實現並保持最佳的收件箱傳送率。<!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**有什麼好處？**

* 使用Enhanced MTA的Adobe Campaign用戶端整體吞吐速度大幅提升，而軟退信則大幅降低。<!--300%--><!--90%+-->
* Enhanced MTA使用最新的MTA技術，為您的電子郵件傳送提供最佳的吞吐量速度。
* 借由即時且自動地適應收到的意見反應，還可確保以即時傳送資料傳送更精確且智慧的電子郵件。

**我可以同時使用原生Adobe Campaign MTA和Enhanced MTA嗎？**

否. 在執行個體升級後，您的電子郵件傳遞只能使用Enhanced MTA。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升級至增強的MTA

**升級至Enhanced MTA需要什麼？**

如果您在2018年9月之後布建了Campaign Classic例項，則不需要任何動作，因為您已使用Enhanced MTA。

針對所有其他托管或部分托管（混合）客戶，Adobe Campaign團隊將聯絡協調移轉日期，並提供移轉所需適當步驟的詳細資訊。

>[!IMPORTANT]
>
>內部部署安裝不提供Enhanced MTA。

**將我的執行個體升級至Enhanced MTA的程式為何？**

托管執行個體的整個程式需要幾分鐘的停機時間。 Adobe在升級後最多24小時內會監控電子郵件的輸送量和傳遞能力，以評估對電子郵件傳送的任何影響。

如果發現任何問題，Adobe可以快速將您的執行個體還原回原生Adobe Campaign MTA。

目前，Enhanced MTA只會影響電子郵件通道。 您的推播通知和簡訊傳送將繼續使用原生Campaign MTA，且不會因升級而受到任何影響。

**升級至Enhanced MTA後，是否需要再次進行IP加熱？**

否. 升級不需要切換至新IP，因此您可以繼續使用現有的熱電子郵件IP。

**升級至Enhanced MTA是否會影響目前進行中的任何促銷活動或傳送？**

在執行個體升級為使用Enhanced MTA之前所準備的任何傳送都必須重新準備，才能正確使用新的MTA。

對於使用Adobe Campaign交易式訊息功能的客戶，任何觸發電子郵件的API呼叫都會在短暫的升級停機期間排入佇列，並在升級完成時嘗試。

## 增強的MTA特異性 {#enhanced-mta-impacts}

### 增強的MTA標題

最新的Campaign Classic例項包含的程式碼會將必要的Enhanced MTA標題新增至每則訊息。 如果您使用Adobe Campaign 19.1(build 9032)或更新版本，而且若非如此，則必須要求[Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html)將&quot;useMomentum=true&quot;參數新增至您的執行執行執行個體設定（在[serverConf.xml](../../installation/using/the-server-configuration-file.md#mta)檔案中），這可能是您的行銷執行個體[中間執行個體](../../installation/using/mid-sourcing-server.md)或[交易式傳訊執行執行個體，具體取決於您的設定。](../../message-center/using/configuring-instances.md#execution-instance)

不過，如果您使用的舊例項不包含此程式碼，則必須將名為&#x200B;**[!UICONTROL Typology Rule for Enhanced MTAs]**的新類型規則新增至您的Campaign例項中的所有現有類型。
此規則由安裝為升級至Enhanced MTA的**[!UICONTROL Typology]**&#x200B;套件新增。

>[!IMPORTANT]
>
>如果您在類型中看到此類型規則，請勿以任何方式刪除或修改它。 否則，您的電子郵件傳送可能會受到不利影響。

此&#x200B;**[!UICONTROL Typology]**&#x200B;套件必須安裝在Adobe Campaign行銷執行個體上。

如果您是混合式客戶，Adobe Campaign團隊會提供指示，說明如何在行銷執行個體上安裝&#x200B;**[!UICONTROL Typology]**&#x200B;套件，以作為升級至Enhanced MTA的一部分。 請連絡您的客戶經理以取得完整指示。

>[!IMPORTANT]
>
>應謹慎遵循Adobe Campaign團隊提供的&#x200B;**[!UICONTROL Typology]**&#x200B;套件安裝說明。 否則，您傳送電子郵件時所使用的IP可能會遇到重大問題。

有關類型的詳細資訊，請參閱[此部分](../../campaign/using/about-campaign-typologies.md)。

### 新MX規則

不再使用MX管理傳送吞吐量規則。 Enhanced MTA有其專屬的MX規則，可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時意見，依網域自訂您的輸送量。

有關MX配置的詳細資訊，請參閱[此部分](../../installation/using/email-deliverability.md#mx-configuration)。

### 退信資格

促銷活動&#x200B;**[!UICONTROL Delivery log qualification]**&#x200B;表格中的退信限定不再用於&#x200B;**synchronous**&#x200B;傳送失敗錯誤訊息。 Enhanced MTA會決定退信類型和資格，並將該資訊傳回至Campaign。

>[!NOTE]
>
>Enhanced MTA會符合SMTP退信的資格，並以對應至促銷活動退信原因和資格的退信代碼形式，將該資格傳回Campaign。

有關退信資格的詳細資訊，請參閱[本節](understanding-delivery-failures.md#bounce-mail-qualification)。

### 傳遞總處理能力

「促銷活動傳送」輸送量圖表將不再向電子郵件收件者顯示輸送量。 該圖表現在會顯示從Campaign轉送至Enhanced MTA之訊息的輸送速度。

有關傳送吞吐量的詳細資訊，請參閱[此部分](../../reporting/using/global-reports.md#delivery-throughput)。

### 有效期

只有在設為&#x200B;**3.5天或更短時間**&#x200B;時，Enhanced MTA才會使用Campaign傳送中的有效期設定。 如果您在Campaign中定義的值超過3.5天，則不會考慮該值。

例如，如果有效期在Campaign中設為5天的預設值，則軟跳出訊息會進入Enhanced MTA重試佇列，並在訊息到達Enhanced MTA後，僅重試最多3.5天。 在此情況下，將不會使用Campaign中設定的值。

當訊息在 Enhanced MTA 佇列中停留 3.5 天且無法傳送時，訊息會逾時，其狀態會從傳送記錄檔中的 **[!UICONTROL Sent]** 更新為 **[!UICONTROL Failed]**。

有關有效期的詳細資訊，請參閱[此部分](steps-sending-the-delivery.md#defining-validity-period)。

### DKIM簽名

DKIM(DomainKeys Indified Mail)電子郵件驗證簽署是由Enhanced MTA完成。 在Enhanced MTA升級過程中，由原生Campaign MTA簽署的DKIM將在網域管理表格中關閉。
有關DKIM的詳細資訊，請參閱[Adobe傳遞能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 傳送成功報表

在電子郵件傳送[dashboard](delivery-dashboard.md)的&#x200B;**[!UICONTROL Summary]**&#x200B;檢視中，**[!UICONTROL Success]**&#x200B;百分比從100%開始，然後在傳送[有效期](steps-sending-the-delivery.md#defining-validity-period)期間逐步下降，因為軟退信和硬退信會從Enhanced MTA回報至Campaign。

事實上，從Campaign成功中繼至Enhanced MTA時，所有訊息在[傳送記錄檔](delivery-dashboard.md#delivery-logs-and-history)中都會顯示為&#x200B;**[!UICONTROL Sent]**。 除非或直到該訊息的[bounce](understanding-delivery-failures.md#delivery-failure-types-and-reasons)從Enhanced MTA傳回至Campaign，否則它們會維持該狀態。

當從Enhanced MTA返回硬跳報文時，其狀態從&#x200B;**[!UICONTROL Sent]**&#x200B;變更為&#x200B;**[!UICONTROL Failed]**，並相應地降低&#x200B;**[!UICONTROL Success]**&#x200B;百分比。

從Enhanced MTA回報軟彈跳訊息時，仍會顯示為&#x200B;**[!UICONTROL Sent]**，且&#x200B;**[!UICONTROL Success]**&#x200B;百分比尚未更新。 然後，在傳送有效期間內，軟彈跳消息將[retried](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure):

* 如果在有效期結束前重試成功，則消息狀態將保持為&#x200B;**[!UICONTROL Sent]**，而&#x200B;**[!UICONTROL Success]**&#x200B;百分比將保持不變。

* 否則，狀態變為&#x200B;**[!UICONTROL Failed]**，並相應地降低&#x200B;**[!UICONTROL Success]**&#x200B;百分比。

因此，您應等到有效期結束，才能看到最終的&#x200B;**[!UICONTROL Success]**&#x200B;百分比，以及實際的&#x200B;**[!UICONTROL Sent]**&#x200B;和&#x200B;**[!UICONTROL Failed]**&#x200B;訊息的最終數量。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 電子郵件意見回饋服務（測試版） {#email-feedback-service}

利用電子郵件反饋服務(EFS)功能，可以準確報告每封電子郵件的狀態，因為反饋是直接從增強MTA（郵件傳輸代理）中捕獲的。

>[!IMPORTANT]
>
>電子郵件意見回饋服務目前提供測試版功能。
>
>如果您有興趣參加此測試版計畫，請填寫[此表格](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u)，我們會回復給您。

傳送開始後，當訊息從促銷活動成功中繼至增強MTA時，**[!UICONTROL Success]**&#x200B;百分比沒有變更。

<!--![](assets/efs-sending.png)-->

傳送記錄會顯示每個目標位址的&#x200B;**[!UICONTROL Taken into account by the service provider]**&#x200B;狀態。

<!--![](assets/efs-pending.png)-->

當訊息實際傳送至目標設定檔，並從Enhanced MTA即時回報此資訊後，傳送記錄會顯示成功接收訊息之每個位址的&#x200B;**[!UICONTROL Sent]**&#x200B;狀態。 每次成功傳送時，**[!UICONTROL Success]**&#x200B;百分比會隨之增加。

從Enhanced MTA回報硬跳出訊息時，其記錄狀態會從&#x200B;**[!UICONTROL Taken into account by the service provider]**&#x200B;變更為&#x200B;**[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->。

當從Enhanced MTA回報軟跳出訊息時，其記錄狀態維持不變(**[!UICONTROL Taken into account by the service provider]**):僅更新[錯誤原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons)<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->。 **[!UICONTROL Success]**&#x200B;百分比保持不變。 然後，在傳送[有效期間](steps-sending-the-delivery.md#defining-validity-period)期間重試軟跳出消息：

* 如果在有效期結束前重試成功，則消息狀態將變為&#x200B;**[!UICONTROL Sent]**，並相應地增加&#x200B;**[!UICONTROL Success]**&#x200B;百分比。

* 否則，狀態會變更為&#x200B;**[!UICONTROL Failed]**。 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不變。

>[!NOTE]
>
>如需硬跳出和軟跳出的詳細資訊，請參閱[此區段](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
>
>如需傳送暫時失敗後重試的詳細資訊，請參閱[此區段](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。


下表顯示了EFS功能引入的KPI和發送日誌狀態的更改。

**使用電子郵件反饋服務**

| 傳送程式的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從促銷活動中繼至增強MTA | **[!UICONTROL Success]** 百分比未顯示（從0%開始） | 由服務提供者考慮 |
| 從Enhanced MTA返回硬跳報文 | **[!UICONTROL Success]**&#x200B;百分比中無變化 | 失敗 |
| 從Enhanced MTA返回軟彈跳報文 | **[!UICONTROL Success]**&#x200B;百分比中無變化 | 由服務提供者考慮 |
| 軟跳出消息重試成功 | **[!UICONTROL Success]** 百分比相應增加 | 已傳送 |
| 軟跳出訊息重試失敗 | **[!UICONTROL Success]**&#x200B;百分比中無變化 | 失敗 |

**不提供電子郵件反饋服務**

| 傳送程式的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從促銷活動中繼至增強MTA | **[!UICONTROL Success]** 百分比從100%開始 | 已傳送 |
| 從Enhanced MTA返回硬跳報文 | **[!UICONTROL Success]** 百分比相應地減少 | 失敗 |
| 從Enhanced MTA返回軟彈跳報文 | **[!UICONTROL Success]**&#x200B;百分比中無變化 | 已傳送 |
| 軟跳出消息重試成功 | **[!UICONTROL Success]**&#x200B;百分比中無變化 | 已傳送 | **[!UICONTROL Success]** 百分比相應增加 | 已傳送 |
| 軟跳出訊息重試失敗 | **[!UICONTROL Success]** 百分比相應地減少 | 失敗 |
