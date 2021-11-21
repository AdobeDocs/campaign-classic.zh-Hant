---
product: campaign
title: 在Adobe Campaign Classic中使用Enhanced MTA傳送
description: 了解使用Adobe Campaign Enhanced MTA傳送電子郵件的範圍和特性。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 3%

---

# 使用增強的 MTA 傳送 {#sending-with-enhanced-mta}

![](../../assets/common.svg)

此 **Adobe Campaign Enhanced MTA** （郵件傳輸代理）提供了升級的發送基礎結構，可改善傳遞能力、信譽、吞吐量、報告、退信處理、IP升級和連接設定管理。

實作該指南的目的是改善可擴充性、提高傳遞吞吐量，並協助更快傳送更多電子郵件。 這是透過新的最適化傳送技術來達成，這些技術會根據來自網際網路服務提供者的意見即時變更電子郵件傳送設定。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA僅適用於托管Campaign Classic或混合型客戶。 Campaign Classic內部部署安裝無法升級為使用Enhanced MTA。

如果您在2018年9月之後布建了Campaign Classic例項，表示您使用的是Enhanced MTA。 對於所有其他Campaign Classic客戶，請參閱 [常見問題](#enhanced-mta-faq) 下方。

Enhanced MTA實作可能會影響部分現有的Campaign功能。 如需詳細資訊，請參閱 [增強的MTA特異性](#enhanced-mta-impacts).

>[!NOTE]
>
>如果您是Adobe Campaign的一般使用者，且想知道您的執行個體是否已升級至Enhanced MTA，請連絡您的內部Campaign管理員。

## 常見問題 {#enhanced-mta-faq}

### 使用與優點

**什麼是Enhanced MTA?**

Adobe Campaign現在可升級為使用新的MTA（郵件轉移代理），此MTA會執行SparkPost的商業電子郵件MTA，稱為 **動量**.

Momentum代表創新、高效能的MTA技術，包括更智慧的退信處理和自動化的傳遞能力優化功能，可幫助發件人實現並保持最佳的收件箱傳送率。 <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**有什麼好處？**

* Adobe Campaign用戶端使用Enhanced MTA時， <!--300%-->總吞吐量速度的大幅提升， <!--90%+-->軟彈性顯著降低。
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

最新的Campaign Classic例項包含的程式碼會將必要的Enhanced MTA標題新增至每則訊息。 如果您使用Adobe Campaign 19.1（組建版本9032）或更新版本，但情況並非如此，您必須要求 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 將&quot;useMoment=true&quot;參數新增至您的執行例項設定(在 [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 檔案)，可能是您的行銷執行個體， [中間來源例項](../../installation/using/mid-sourcing-server.md)，或 [異動訊息執行執行例項](../../message-center/using/configuring-instances.md#execution-instance)，視您的設定而定。

不過，如果您使用的舊例項不包含此程式碼，則會有名為的新類型規則 **[!UICONTROL Typology Rule for Enhanced MTAs]** 必須新增至Campaign執行個體中的所有現有類型。
此規則由 **[!UICONTROL Typology]** 已安裝的套件，作為升級至Enhanced MTA的一部分。

>[!IMPORTANT]
>
>如果您在類型中看到此類型規則，請勿以任何方式刪除或修改它。 否則，您的電子郵件傳送可能會受到不利影響。

此 **[!UICONTROL Typology]** 套件必須安裝在Adobe Campaign行銷執行個體上。

如果您是混合式客戶，Adobe Campaign團隊會提供如何安裝的指示 **[!UICONTROL Typology]** 行銷執行個體上的套件，作為升級至Enhanced MTA的一部分。 請連絡您的客戶經理以取得完整指示。

>[!IMPORTANT]
>
>Adobe Campaign團隊提供的安裝指示 **[!UICONTROL Typology]** 應仔細遵守包裝。 否則，您傳送電子郵件時所使用的IP可能會遇到重大問題。

如需類型的詳細資訊，請參閱 [本節](../../campaign-opt/using/about-campaign-typologies.md).

### 新MX規則

不再使用MX管理傳送吞吐量規則。 Enhanced MTA有其專屬的MX規則，可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時意見，依網域自訂您的輸送量。

有關MX配置的詳細資訊，請參見 [本節](../../installation/using/email-deliverability.md#mx-configuration).

### 退信資格

Campaign中的退信資格 **[!UICONTROL Delivery log qualification]** 表格不再用於 **同步** 傳遞失敗錯誤訊息。 Enhanced MTA會決定退信類型和資格，並將該資訊傳回至Campaign。

>[!NOTE]
>
>Enhanced MTA會符合SMTP退信的資格，並以對應至促銷活動退信原因和資格的退信代碼形式，將該資格傳回Campaign。

有關退信資格的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#bounce-mail-qualification).

### 傳遞總處理能力

「促銷活動傳送」輸送量圖表將不再向電子郵件收件者顯示輸送量。 該圖表現在會顯示從Campaign轉送至Enhanced MTA之訊息的輸送速度。

如需傳送輸送量的詳細資訊，請參閱 [本節](../../reporting/using/global-reports.md#delivery-throughput).

### 有效期

只有在設為時，Enhanced MTA才會使用Campaign傳送中的有效期設定 **3.5天或更少**. 如果您在Campaign中定義的值超過3.5天，則不會考慮該值。

例如，如果有效期在Campaign中設為5天的預設值，則軟跳出訊息會進入Enhanced MTA重試佇列，並在訊息到達Enhanced MTA後，僅重試最多3.5天。 在此情況下，將不會使用Campaign中設定的值。

當訊息在 Enhanced MTA 佇列中停留 3.5 天且無法傳送時，訊息會逾時，其狀態會從傳送記錄檔中的 **[!UICONTROL Sent]** 更新為 **[!UICONTROL Failed]**。

如需有效期的詳細資訊，請參閱 [本節](steps-sending-the-delivery.md#defining-validity-period).

### DKIM簽名

DKIM(DomainKeys Indified Mail)電子郵件驗證簽署是由Enhanced MTA完成。 在Enhanced MTA升級過程中，由原生Campaign MTA簽署的DKIM將在網域管理表格中關閉。
有關DKIM的詳細資訊，請參閱 [Adobe傳遞能力最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 傳送成功報表

在 **[!UICONTROL Summary]** 電子郵件傳送的檢視 [儀表板](delivery-dashboard.md), **[!UICONTROL Success]** 百分比從100%開始，然後在整個交付過程中逐漸下降 [有效期](steps-sending-the-delivery.md#defining-validity-period)，因為軟退信和硬退信會從Enhanced MTA回報到Campaign。

事實上，所有訊息都顯示為 **[!UICONTROL Sent]** 在 [傳送記錄](delivery-dashboard.md#delivery-logs-and-history) 從Campaign成功轉送至Enhanced MTA時。 除非或直到 [跳出](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 因此，訊息會從Enhanced MTA傳回至Campaign。

從Enhanced MTA回報硬跳出訊息時，其狀態會從 **[!UICONTROL Sent]** to **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比相應減少。

從Enhanced MTA回報軟彈跳訊息時，仍會顯示為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比尚未更新。 然後，軟彈跳消息 [重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在整個傳送有效期間：

* 如果在有效期結束前重試成功，則訊息狀態會維持為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比保持不變。

* 否則，狀態會變更為 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比相應減少。

因此，您應等到有效期結束才查看最終 **[!UICONTROL Success]** 百分比，以及最終的 **[!UICONTROL Sent]** 和 **[!UICONTROL Failed]** 訊息。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 電子郵件意見回饋服務（測試版） {#email-feedback-service}

利用電子郵件反饋服務(EFS)功能，可以準確報告每封電子郵件的狀態，因為反饋是直接從增強MTA（郵件傳輸代理）中捕獲的。

>[!IMPORTANT]
>
>電子郵件意見回饋服務目前提供測試版功能。
>
>如果您有興趣參加此測試版計畫，請填寫 [此表單](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) 我們會回到你身邊。

傳送開始後， **[!UICONTROL Success]** 成功從促銷活動中繼至增強MTA時的百分比。

<!--![](assets/efs-sending.png)-->

傳送記錄會顯示 **[!UICONTROL Taken into account by the service provider]** 每個目標地址的狀態。

<!--![](assets/efs-pending.png)-->

當訊息實際傳送至目標設定檔，且從Enhanced MTA即時回報此資訊後，傳送記錄會顯示 **[!UICONTROL Sent]** 成功接收消息的每個地址的狀態。 此 **[!UICONTROL Success]** 每次成功傳送時，百分比會隨之增加。

從Enhanced MTA回報硬跳出訊息時，其記錄狀態會從 **[!UICONTROL Taken into account by the service provider]** to **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

從Enhanced MTA回報軟跳出訊息時，其記錄狀態維持不變(**[!UICONTROL Taken into account by the service provider]**):只有 [錯誤原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 已更新<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. 此 **[!UICONTROL Success]** 百分比保持不變。 然後在傳送期間重試軟反彈消息 [有效期](steps-sending-the-delivery.md#defining-validity-period):

* 如果在有效期結束前重試成功，則訊息狀態會變更為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比隨之增加。

* 否則，狀態會變更為 **[!UICONTROL Failed]**. 此 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不變。

>[!NOTE]
>
>如需硬跳出和軟跳出的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>如需傳送暫時失敗後重試的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


下表顯示了EFS功能引入的KPI和發送日誌狀態的更改。

**使用電子郵件反饋服務**

| 傳送程式的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從促銷活動中繼至增強MTA | **[!UICONTROL Success]** 百分比未顯示（從0%開始） | 由服務提供者考慮 |
| 從Enhanced MTA返回硬跳報文 | 中無變更 **[!UICONTROL Success]** 百分比 | 失敗 |
| 從Enhanced MTA返回軟彈跳報文 | 中無變更 **[!UICONTROL Success]** 百分比 | 由服務提供者考慮 |
| 軟跳出消息重試成功 | **[!UICONTROL Success]** 百分比相應增加 | 已傳送 |
| 軟跳出訊息重試失敗 | 中無變更 **[!UICONTROL Success]** 百分比 | 失敗 |

**不提供電子郵件反饋服務**

| 傳送程式的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從促銷活動中繼至增強MTA | **[!UICONTROL Success]** 百分比從100%開始 | 已傳送 |
| 從Enhanced MTA返回硬跳報文 | **[!UICONTROL Success]** 百分比相應地減少 | 失敗 |
| 從Enhanced MTA返回軟彈跳報文 | 中無變更 **[!UICONTROL Success]** 百分比 | 已傳送 |
| 軟跳出消息重試成功 | 中無變更 **[!UICONTROL Success]** 百分比 | 已傳送 | **[!UICONTROL Success]** 百分比相應增加 | 已傳送 |
| 軟跳出訊息重試失敗 | **[!UICONTROL Success]** 百分比相應地減少 | 失敗 |
