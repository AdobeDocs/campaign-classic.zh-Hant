---
product: campaign
title: 與增強的MTA一起發送，在Adobe Campaign Classic
description: 瞭解與Adobe Campaign增強型MTA發送電子郵件的範圍和特點
exl-id: 58cc23f4-9ab0-45c7-9aa2-b08487ec7e91
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '1921'
ht-degree: 3%

---

# 使用增強的 MTA 傳送 {#sending-with-enhanced-mta}

![](../../assets/common.svg)

的 **Adobe Campaign增強MTA** （郵件傳輸代理）提供了升級的發送基礎結構，可改善傳送能力、信譽、吞吐量、報告、跳轉處理、IP升級和連接設定管理。

它的實施旨在提高可擴充性、提高交付吞吐量並幫助更快地發送更多電子郵件。 這是通過新的自適應傳遞技術實現的，這種技術基於來自網際網路服務提供商的反饋即時地改變電子郵件發送設定。

>[!IMPORTANT]
>
>Adobe Campaign增強型MTA僅適用於Campaign Classic托管或混合客戶。 Campaign Classic內部安裝無法升級以使用增強的MTA。

如果您在2018年9月之後配置了Campaign Classic實例，則您正在使用增強的MTA。 對於所有其他Campaign Classic客戶，請參閱 [常見問題](#enhanced-mta-faq) 下。

增強的MTA實施可能會影響一些現有的市場活動功能。 有關此內容的詳細資訊，請參閱 [增強的MTA特異性](#enhanced-mta-impacts)。

>[!NOTE]
>
>如果您是Adobe Campaign的最終用戶，並且想知道您的實例是否已升級到增強型MTA，請與您的內部市場活動管理員聯繫。

## 常見問題 {#enhanced-mta-faq}

### 使用和優勢

**什麼是增強的MTA?**

Adobe Campaign現在可以升級為使用新的MTA（郵件轉移代理），該MTA運行SparkPost的商業電子郵件MTA，稱為 **動量**。

Momentum代表了創新的高效能MTA技術，其中包括更智慧的彈跳處理和自動化的可傳送性優化功能，幫助發送者實現和保持最佳收件箱傳送率。 <!--More than 37% of the world’s business email is sent using SparkPost’s MTA technology.-->

**有什麼好處？**

* Adobe Campaign客戶使用增強型MTA時 <!--300%-->整體吞吐量速度的大幅提升， <!--90%+-->軟介面顯著減少。
* 增強型MTA使用最新的MTA技術，為您的電子郵件傳輸提供最佳吞吐量速度。
* 通過立即自動適應它收到的反饋，它還確保了通過即時傳遞資料提供更準確和智慧的電子郵件。

**我可以同時使用本地的Adobe CampaignMTA和增強MTA嗎？**

沒有。在實例升級後，只有增強的MTA可用於您的電子郵件傳遞。

<!--
**Is there a fee associated with upgrading my instance to and subsequent use of the Enhanced MTA?**
No, there is no extra fee associated with the upgrade process to enable the use of the Enhanced MTA.

**When will the Enhanced MTA be available to me?**

* If you are new to Adobe Campaign Classic, you are already using the Enhanced MTA.

* For Adobe Campaign Classic existing customers, we’ve implemented a phased rollout that covers all hosted or partially hosted (hybrid) instances. If you’re not already using it, we’ll be contacting you in the near future with the dates and details for upgrading your Adobe Campaign Classic instances to the Enhanced MTA.
-->

### 升級到增強的MTA

**升級到增強型MTA需要什麼？**

如果您在2018年9月之後預配了Campaign Classic實例，則無需執行任何操作，因為您已在使用增強型MTA。

對於所有其他托管或部分托管（混合）客戶，Adobe Campaign團隊將聯繫起來協調遷移日期，並將提供遷移所需適當步驟的詳細資訊。

>[!IMPORTANT]
>
>增強型MTA不可用於內部安裝。

**將實例升級到增強型MTA的過程是什麼？**

托管實例的整個過程需要幾分鐘的停機時間。 Adobe將在升級後24小時內監控電子郵件吞吐量和可傳送性，以評估對您的電子郵件傳送的任何影響。

如果發現任何問題，Adobe可以快速並臨時將實例還原回本機Adobe CampaignMTA。

目前，增強型MTA僅影響電子郵件通道。 您的推送通知和SMS交付將繼續使用本機市場活動MTA，並且不會受升級的任何影響。

**升級到增強MTA後，是否需要再次經歷IP升溫？**

沒有。升級不需要切換到新IP，因此您可以繼續使用現有的熱電子郵件IP。

**升級到增強型MTA是否會影響當前正在進行的任何活動或交付？**

在升級實例以使用增強型MTA之前準備的任何交貨都需要重新準備，以便正確使用新的MTA。

對於使用Adobe Campaign事務性消息傳遞功能的客戶，任何觸發電子郵件的API調用都將在非常短的升級停機時間內排隊，並將在升級完成時嘗試。

## 增強的MTA特異性 {#enhanced-mta-impacts}

### 增強的MTA標頭

最新的Campaign Classic實例包括將所需的增強MTA標頭添加到每條消息的代碼。 如果您使用的是Adobe Campaign19.1(build 9032)或更高版本，如果不是，則必須請求 [Adobe客戶關懷](https://helpx.adobe.com/tw/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) 將&quot;useMomentum=true&quot;參數添加到執行實例配置(在 [serverConf.xml](../../installation/using/the-server-configuration-file.md#mta) 檔案)，可能是您的營銷實例， [中間採購實例](../../installation/using/mid-sourcing-server.md)或 [事務消息執行實例](../../message-center/using/configuring-instances.md#execution-instance)，具體取決於您的配置。

但是，如果您使用的舊實例不包括此代碼，則會使用名為 **[!UICONTROL Typology Rule for Enhanced MTAs]** 必須添加到您的市場活動實例中的所有現有類型。
此規則由 **[!UICONTROL Typology]** 包已安裝，作為升級到增強型MTA的一部分。

>[!IMPORTANT]
>
>如果您在類型中看到此類型規則，請勿以任何方式刪除或修改它。 否則，您的電子郵件遞送可能會受到負面影響。

此 **[!UICONTROL Typology]** 需要在Adobe Campaign市場推廣實例上安裝軟體包。

如果您是混合客戶機，Adobe Campaign團隊將向您提供有關如何安裝 **[!UICONTROL Typology]** 作為升級到增強型MTA的一部分，在您的市場營銷實例上打包。 請聯繫您的客戶經理以獲取完整說明。

>[!IMPORTANT]
>
>Adobe Campaign小組提供的有關如何安裝 **[!UICONTROL Typology]** 應當仔細地遵守包裹。 否則，您可能會遇到用於發送電子郵件的IP的主要問題。

有關類型的詳細資訊，請參見 [此部分](../../campaign-opt/using/about-campaign-typologies.md)。

### 新MX規則

不再使用MX管理傳遞吞吐量規則。 增強型MTA有其自己的MX規則，它可根據您的歷史電子郵件信譽以及您發送電子郵件的域的即時反饋，按域定制吞吐量。

有關MX配置的詳細資訊，請參見 [此部分](../../installation/using/email-deliverability.md#mx-configuration)。

### 彈跳資格

市場活動中的彈出資格 **[!UICONTROL Delivery log qualification]** 表不再用於 **同步** 傳遞失敗錯誤消息。 「增強的MTA」確定退貨類型和資格，並將該資訊發回市場活動。

>[!NOTE]
>
>「增強的MTA」確認了SMTP退貨資格，並將該資格以彈出代碼的形式發回市場活動，該代碼映射到市場活動退貨原因和資格。

有關彈跳資格的詳細資訊，請參閱 [此部分](understanding-delivery-failures.md#bounce-mail-qualification)。

### 傳遞總處理能力

「市場活動交付」吞吐量圖將不再顯示您的電子郵件收件人的吞吐量。 該圖現在將顯示從市場活動到增強型MTA的消息的中繼吞吐量速度。

有關交付吞吐量的詳細資訊，請參見 [此部分](../../reporting/using/global-reports.md#delivery-throughput)。

### 有效期

僅當設定為時，增強型MTA才會使用「市場活動交付」中的有效期設定 **3.5天或以下**。 如果在「市場活動」中定義的值超過3.5天，則不會將其考慮在內。

例如，如果有效期在市場活動中設定為預設值5天，則軟跳轉消息將進入增強MTA重試隊列，並從消息到達增強MTA後重試最多3.5天。 在這種情況下，將不使用「市場活動」中設定的值。

當訊息在 Enhanced MTA 佇列中停留 3.5 天且無法傳送時，訊息會逾時，其狀態會從傳送記錄檔中的 **[!UICONTROL Sent]** 更新為 **[!UICONTROL Failed]**。

有關有效期的詳細資訊，請參閱 [此部分](steps-sending-the-delivery.md#defining-validity-period)。

### DKIM簽名

DKIM(DomainKeys Indifed Mail)電子郵件身份驗證簽名由增強的MTA完成。 本機Campaign MTA的DKIM簽名將在域管理表中關閉，作為增強MTA升級的一部分。
有關DKIM的詳細資訊，請參閱 [Adobe交付能力最佳實踐指南](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/transition-process/infrastructure.html#authentication)。

### 交付成功報告

在 **[!UICONTROL Summary]** 電子郵件傳遞視圖 [儀表板](delivery-dashboard.md)，也請參見Wiki頁。 **[!UICONTROL Success]** 百分比從100%開始，然後在整個交貨期間逐漸下降 [有效期](steps-sending-the-delivery.md#defining-validity-period)從「增強型MTA」到「活動」，軟硬邊界被報回。

事實上，所有消息都顯示為 **[!UICONTROL Sent]** 的 [發送日誌](delivery-dashboard.md#delivery-logs-and-history) 一旦成功地從Mavigment轉送到Enhanced MTA。 除非或直到 [彈](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 從增強型MTA到「活動」傳遞該消息。

當硬跳消息從增強MTA返回報告時，其狀態將從 **[!UICONTROL Sent]** 至 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比相應減少。

從增強MTA返回軟跳跳消息時，它們仍顯示為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比尚未更新。 然後軟跳跳消息 [重試](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure) 在整個交貨有效期內：

* 如果在有效期結束前重試成功，則消息狀態將保持為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比保持不變。

* 否則，狀態將更改為 **[!UICONTROL Failed]** 和 **[!UICONTROL Success]** 百分比相應減少。

因此，您應等到有效期結束後才能查看最終版本 **[!UICONTROL Success]** 百分比，以及實際的 **[!UICONTROL Sent]** 和 **[!UICONTROL Failed]** 消息。

<!--The fact that the Success percentage will go to 100% very quickly indicates that your instance has been upgraded to the Enhanced MTA.-->

### 電子郵件反饋服務（測試版） {#email-feedback-service}

借助電子郵件反饋服務(EFS)功能，可以準確報告每封電子郵件的狀態，因為反饋會直接從增強的MTA（郵件傳輸代理）中捕獲。

>[!IMPORTANT]
>
>電子郵件反饋服務目前可作為測試版功能使用。
>
>如果您有興趣參加此測試版計畫，請填寫 [此表格](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4Rol2vQGupxItW9_BerXV6VUQTJPN1Q5WUI4OFNTWkYzQjg3WllUSDAxWi4u) 我們會回你電話。

一旦開始交貨， **[!UICONTROL Success]** 成功將消息從「市場活動」中繼到「增強的MTA」時的百分比。

<!--![](assets/efs-sending.png)-->

交貨日誌顯示 **[!UICONTROL Taken into account by the service provider]** 每個目標地址的狀態。

<!--![](assets/efs-pending.png)-->

當郵件實際被傳送到目標配置檔案，並且一旦從增強型MTA即時報告此資訊，傳遞日誌將顯示 **[!UICONTROL Sent]** 成功接收消息的每個地址的狀態。 的 **[!UICONTROL Success]** 每次成功交付時，百分比都相應增加。

當硬跳消息從增強MTA返回報告時，其日誌狀態將從 **[!UICONTROL Taken into account by the service provider]** 至 **[!UICONTROL Failed]**<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->。

從增強MTA返回軟跳跳消息時，其日誌狀態保持不變(**[!UICONTROL Taken into account by the service provider]**):只有 [錯誤原因](understanding-delivery-failures.md#delivery-failure-types-and-reasons) 已更新<!-- and the **[!UICONTROL Bounces + errors]** percentage is increased accordingly-->。 的 **[!UICONTROL Success]** 百分比保持不變。 然後在整個傳送過程中重試軟彈跳消息 [有效期](steps-sending-the-delivery.md#defining-validity-period):

* 如果在有效期結束前重試成功，則消息狀態將更改為 **[!UICONTROL Sent]** 和 **[!UICONTROL Success]** 百分比相應增加。

* 否則，狀態將更改為 **[!UICONTROL Failed]**。 的 **[!UICONTROL Success]** <!--and **[!UICONTROL Bounces + errors]** -->百分比保持不變。

>[!NOTE]
>
>有關硬邊界和軟邊界的詳細資訊，請參閱 [此部分](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。
>
>有關傳遞臨時失敗後重試的更多資訊，請參見 [此部分](understanding-delivery-failures.md#retries-after-a-delivery-temporary-failure)。


下表顯示了EFS功能引入的KPI和發送日誌狀態的更改。

**使用電子郵件反饋服務**

| 發送過程中的步驟 | KPI摘要 | 正在發送日誌狀態 |
|--- |--- |--- |
| 已成功將消息從市場活動中轉到增強的MTA | **[!UICONTROL Success]** 百分比未顯示（以0%開始） | 服務提供商考慮的因素 |
| 從增強的MTA返回硬跳消息 | 未更改 **[!UICONTROL Success]** 百分比 | 失敗 |
| 從增強的MTA返回軟彈跳消息 | 未更改 **[!UICONTROL Success]** 百分比 | 服務提供商考慮的因素 |
| 軟彈跳消息重試成功 | **[!UICONTROL Success]** 百分比相應增加 | 已發送 |
| 軟跳轉消息重試失敗 | 未更改 **[!UICONTROL Success]** 百分比 | 失敗 |

**沒有電子郵件反饋服務**

| 發送過程中的步驟 | KPI摘要 | 正在發送日誌狀態 |
|--- |--- |--- |
| 已成功將消息從市場活動中轉到增強的MTA | **[!UICONTROL Success]** 百分比從100%開始 | 已發送 |
| 從增強的MTA返回硬跳消息 | **[!UICONTROL Success]** 百分比相應減少 | 失敗 |
| 從增強的MTA返回軟彈跳消息 | 未更改 **[!UICONTROL Success]** 百分比 | 已發送 |
| 軟彈跳消息重試成功 | 未更改 **[!UICONTROL Success]** 百分比 | 已發送 | **[!UICONTROL Success]** 百分比相應增加 | 已發送 |
| 軟跳轉消息重試失敗 | **[!UICONTROL Success]** 百分比相應減少 | 失敗 |
