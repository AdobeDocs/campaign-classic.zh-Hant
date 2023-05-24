---
product: campaign
title: Adobe Campaign Classic中的增強型MTA的簡訊
description: 瞭解使用Adobe Campaign Enhanced MTA傳送電子郵件的範圍和特性
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Email
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '1999'
ht-degree: 4%

---

# 使用增強的 MTA 傳送 {#sending-with-enhanced-mta}



此 **Adobe Campaign Enhanced MTA** （郵件傳輸代理程式）提供升級的傳送基礎架構，可改善傳遞能力、信譽、輸送量、報告、跳出處理、IP提升和連線設定管理。

實作它可改善擴充性、提高傳遞輸送量，並協助更快速地傳送更多電子郵件。 這是透過新的最適化傳送技術達成，該技術會根據網際網路服務提供者的意見即時變更電子郵件傳送設定。

>[!IMPORTANT]
>
>Adobe Campaign Enhanced MTA僅適用於Campaign Classic託管或混合客戶。 Campaign Classic內部部署安裝無法升級為使用增強型MTA。

如果您在2018年9月之後布建了Campaign Classic執行個體，則您會使用Enhanced MTA。 對於所有其他Campaign Classic客戶，請參閱 [常見問題](#enhanced-mta-faq) 下方的。

增強型MTA實作可能會影響部分現有的Campaign功能。 如需詳細資訊，請參閱 [增強的MTA規格](#enhanced-mta-impacts).

>[!NOTE]
>
>如果您是Adobe Campaign的一般使用者，且想瞭解您的執行個體是否已升級至Enhanced MTA，請聯絡您的內部Campaign管理員。

## 常見問題 {#enhanced-mta-faq}

### 使用狀況和優點

**什麼是Enhanced MTA？**

Adobe Campaign現在可以升級，使用新的MTA （郵件傳輸代理程式），執行SparkPost的商業電子郵件MTA，稱為 **動量**.

Momentum代表創新的高效能MTA技術，包括更聰明的彈回處理以及自動化傳遞能力最佳化功能，可協助寄件者達到並維持最佳收件匣傳遞率。 <!--More than 37% of the world's business email is sent using SparkPost's MTA technology.-->

**有哪些優點？**

* 使用Enhanced MTA的Adobe Campaign使用者端已發現 <!--300%-->大幅提升整體處理速度，以及 <!--90%+-->大幅減少軟跳出。
* Enhanced MTA使用最新的MTA技術，為您提供最佳的電子郵件傳送輸送速度。
* 透過即時且自動地適應其收到的意見回饋，它還可以確保使用即時傳遞資料來傳送更精確且更智慧的電子郵件。

**我可以同時使用原生Adobe Campaign MTA和Enhanced MTA嗎？**

沒有。執行個體升級後，只有增強型MTA可用於電子郵件傳遞。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we've implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you're not already using it, we'll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升級至增強型MTA

**升級至Enhanced MTA需要什麼？**

如果您在2018年9月之後布建了Campaign Classic執行個體，則不需要採取任何動作，因為您已使用Enhanced MTA。

對於所有其他託管或部分託管（混合）的客戶，Adobe Campaign團隊會聯絡以協調移轉日期，並提供移轉所需適當步驟的詳細資訊。

>[!IMPORTANT]
>
>Enhanced MTA不適用於內部部署。

**將我的執行個體升級至增強型MTA的程式為何？**

託管執行個體的整個程式需要幾分鐘的停機時間。 Adobe將在升級後最多24小時內監控電子郵件輸送量和傳遞能力，以評估對電子郵件傳遞的任何影響。

如果發現任何問題，Adobe可以快速將您的執行個體暫時恢復為原生Adobe Campaign MTA。

目前，Enhanced MTA只會影響電子郵件頻道。 您的推播通知和SMS傳送將繼續使用原生Campaign MTA，且不會受到升級任何影響。

**升級至Enhanced MTA後，是否需要再次進行IP預熱？**

沒有。升級不需要切換到新IP，因此您可以繼續使用現有的、溫暖的電子郵件IP。

**升級至Enhanced MTA是否會影響目前進行的任何行銷活動或傳遞？**

將執行個體升級為使用增強型MTA之前準備的所有傳送，都需要重新準備才能正確使用新的MTA。

對於使用Adobe Campaign交易式傳訊功能的客戶，在極短的升級停機期間，觸發電子郵件的任何API呼叫都將排入佇列，並在升級完成後嘗試。

## 增強的MTA規格 {#enhanced-mta-impacts}

### 增強的MTA標題

最新的Campaign Classic執行個體包含將必要的Enhanced MTA標頭新增到每封郵件的程式碼。 如果您使用的是Adobe Campaign 19.1 (build 9032)或更高版本，如果不是這種情況，則必須請求 [Adobe客戶服務](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 新增&quot;useMomentum=true&quot;引數至您的執行例項設定(在 [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 檔案)，可能是您的行銷執行個體， [中間來源執行個體](../../installation/using/mid-sourcing-server.md)，或 [異動訊息執行例項](../../message-center/using/configuring-instances.md#execution-instance)，視您的設定而定。

不過，如果您使用不含此程式碼的舊例項，則會新增一個名為的型別規則 **[!UICONTROL Typology Rule for Enhanced MTAs]** 必須新增至您的Campaign執行個體中的所有現有型別。
此規則新增者為 **[!UICONTROL Typology]** 此套件是在升級至增強型MTA時安裝的。

>[!IMPORTANT]
>
>如果您在型別中看到此型別規則，請勿以任何方式刪除或修改它。 否則，您的電子郵件傳送可能會受到不利的影響。

此 **[!UICONTROL Typology]** 套件必須安裝在Adobe Campaign行銷執行個體上。

如果您是混合式使用者端，Adobe Campaign團隊會為您提供如何安裝 **[!UICONTROL Typology]** 套件進行升級，以前往增強型MTA。 請聯絡您的帳戶高階主管以取得完整指示。

>[!IMPORTANT]
>
>Adobe Campaign團隊提供的安裝說明 **[!UICONTROL Typology]** 套件應謹慎使用。 否則，您可能會在使用傳送電子郵件的IP時遇到重大問題。

如需型別的詳細資訊，請參閱 [本節](../../campaign-opt/using/about-campaign-typologies.md).

### 新的MX規則

不再使用MX管理傳遞輸送量規則。 Enhanced MTA有自己的MX規則，可讓它根據您過去的電子郵件信譽，以及您傳送電子郵件之網域所提供的即時回饋，依網域來自訂您的輸送量。

如需MX設定的詳細資訊，請參閱 [本節](../../installation/using/email-deliverability.md#mx-configuration).

### 彈回資格

Campaign中的退信資格 **[!UICONTROL Delivery log qualification]** 表格不再用於 **同步** 傳遞失敗錯誤訊息。 Enhanced MTA會決定退信型別和資格，並將該資訊傳回至Campaign。

>[!NOTE]
>
>Enhanced MTA會符合SMTP跳出的資格，並以對應至Campaign跳出原因和資格的跳出代碼形式，將該資格傳送回Campaign。

如需跳出資格的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#bounce-mail-qualification).

### 傳遞總處理能力

Campaign傳送輸送量圖表將不再顯示傳送給電子郵件收件者的輸送量。 該圖表現在會顯示從Campaign轉送訊息至Enhanced MTA的輸送量速度。

如需傳送輸送量的詳細資訊，請參閱 [本節](../../reporting/using/global-reports.md#delivery-throughput).

>[!NOTE]
>
>使用 [電子郵件回饋服務](#email-feedback-service) (EFS)功能（目前為測試版），Campaign傳送輸送量圖表仍會顯示傳送給電子郵件收件者的輸送量。

### 重試次數

Campaign不再使用傳送中的重試設定。 軟退信重試次數以及重試之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

如需重試的詳細資訊，請參閱 [本節](steps-sending-the-delivery.md#configuring-retries).

### 有效期限

Campaign傳送中的有效期間設定僅會在設為「 」時使用Enhanced MTA **3.5天或更短**. 如果您在Campaign中定義的值超過3.5天，則不會考慮該值。

例如，如果有效期間在Campaign中設定為預設值5天，則軟退信將會進入Enhanced MTA重試佇列，並從該訊息達到Enhanced MTA時起最多重試3.5天。 在這種情況下，將不使用Campaign中設定的值。

當訊息在 Enhanced MTA 佇列中停留 3.5 天且無法傳送時，訊息會逾時，其狀態會從傳送記錄檔中的 **[!UICONTROL Sent]** 更新為 **[!UICONTROL Failed]**。

如需有效期的詳細資訊，請參閱 [本節](steps-sending-the-delivery.md#defining-validity-period).

### DKIM簽署

DKIM (DomainKeys Indified Mail)電子郵件驗證簽署是由Enhanced MTA完成。 原生Campaign MTA的DKIM簽署將在網域管理表格中關閉，作為Enhanced MTA升級的一部分。
如需DKIM的詳細資訊，請參閱 [Adobe傳遞性最佳實務指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication).

### 傳遞成功報告

在 **[!UICONTROL Summary]** 電子郵件傳遞的檢視 [儀表板](delivery-dashboard.md)，則 **[!UICONTROL Success]** 百分比從100%開始，然後在整個傳送過程中逐步下降 [有效期](steps-sending-the-delivery.md#defining-validity-period)，因為軟跳出和硬跳出會從Enhanced MTA回報回Campaign。

事實上，所有訊息都會顯示為 **[!UICONTROL Sent]** 在 [傳送記錄檔](delivery-dashboard.md#delivery-logs-and-history) 只要成功從Campaign轉送至Enhanced MTA即可。 除非或直至 [跳出](understanding-delivery-failures.md#delivery-failure-types-and-reasons) ，該訊息的訊息會從Enhanced MTA傳回Campaign。

當硬跳出訊息從Enhanced MTA回傳時，其狀態會從 **[!UICONTROL Sent]** 至 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比會據此減少。

當從Enhanced MTA回報軟退信時，仍會顯示為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比尚未更新。 然後，軟跳出訊息會 [已重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在整個傳遞有效期間：

* 如果在有效期結束前重試成功，則訊息狀態將保持為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比保持不變。

* 否則，狀態會變更為 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比會據此減少。

因此，您應等到有效期結束才看到最終結果 **[!UICONTROL Success]** 百分比，以及最終實際數量 **[!UICONTROL Sent]** 和 **[!UICONTROL Failed]** 訊息。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 電子郵件回饋服務（測試版） {#email-feedback-service}

使用電子郵件回饋服務(EFS)功能，可準確報告每封電子郵件的狀態，因為回饋會直接從Enhanced MTA （訊息傳輸代理程式）擷取。

>[!IMPORTANT]
>
>電子郵件回饋服務目前提供測試版功能。
>
>如果您有興趣參與此Beta版計畫，請填寫 [此表單](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) 我們會與您聯絡。

開始傳送後，此專案沒有變更 **[!UICONTROL Success]** 訊息成功從Campaign轉送至Enhanced MTA時的百分比。

<!--![](assets/efs-sending.png)-->

傳遞記錄顯示 **[!UICONTROL Taken into account by the service provider]** 每個目標地址的狀態。

<!--![](assets/efs-pending.png)-->

當訊息實際傳送至目標設定檔時，一旦從Enhanced MTA即時回報此資訊後，傳送記錄會顯示 **[!UICONTROL Sent]** 成功收到訊息的每個位址的狀態。 此 **[!UICONTROL Success]** 百分比會隨著每次成功傳遞而相應增加。

從Enhanced MTA回報硬跳出訊息時，其記錄狀態會從 **[!UICONTROL Taken into account by the service provider]** 至 **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->.

當從Enhanced MTA回報軟退信時，其記錄狀態維持不變(**[!UICONTROL Taken into account by the service provider]**)：僅限 [錯誤原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 已更新<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->. 此 **[!UICONTROL Success]** 百分比保持不變。 然後，軟跳出訊息會在整個傳遞期間重試 [有效期](steps-sending-the-delivery.md#defining-validity-period)：

* 如果在有效期結束前重試成功，則訊息狀態會變更為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比會相應增加。

* 否則，狀態會變更為 **[!UICONTROL Failed]**. 此 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不變。

>[!NOTE]
>
>如需硬跳出和軟跳出的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#delivery-failure-types-and-reasons).
>
>如需傳送暫時失敗後重試的詳細資訊，請參閱 [本節](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure).


下表顯示EFS功能所引進的KPI和傳送記錄檔狀態的變更。

**使用電子郵件回饋服務**

| 傳送程式中的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從Campaign轉送至Enhanced MTA | **[!UICONTROL Success]** 百分比未顯示（從0%開始） | 服務提供者已將其列入考量 |
| 系統會從Enhanced MTA回報硬跳出的訊息 | 無變更 **[!UICONTROL Success]** 百分比 | 失敗 |
| 系統會從Enhanced MTA回報軟退信訊息 | 無變更 **[!UICONTROL Success]** 百分比 | 服務提供者已將其列入考量 |
| 軟退信重試成功 | **[!UICONTROL Success]** 百分比會相應增加 | 已傳送 |
| 軟退信重試失敗 | 無變更 **[!UICONTROL Success]** 百分比 | 失敗 |

**無電子郵件回饋服務**

| 傳送程式中的步驟 | KPI摘要 | 傳送記錄檔狀態 |
|--- |--- |--- |
| 訊息已成功從Campaign轉送至Enhanced MTA | **[!UICONTROL Success]** 百分比從100%開始 | 已傳送 |
| 系統會從Enhanced MTA回報硬跳出的訊息 | **[!UICONTROL Success]** 百分比會據此減少 | 失敗 |
| 系統會從Enhanced MTA回報軟退信訊息 | 無變更 **[!UICONTROL Success]** 百分比 | 已傳送 |
| 軟退信重試成功 | 無變更 **[!UICONTROL Success]** 百分比 | 已傳送 | **[!UICONTROL Success]** 百分比會相應增加 | 已傳送 |
| 軟退信重試失敗 | **[!UICONTROL Success]** 百分比會據此減少 | 失敗 |
