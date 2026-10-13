---
product: campaign
title: 設定並傳送傳遞
description: 瞭解如何設定並傳送傳遞
feature: Channel Configuration
role: User
hide: true
exl-id: 0411686e-4f13-401e-9333-e14b05ebe9cd
TQID: 'https://experienceleague.adobe.com/-Wh-pHFGE1kTId3t6g7wVJFfSvh2W5ERHi2K5-0Ohdw'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a075b2c1-7748-4328-b7f6-343aa314616a
    internal-label: Campaigns
  - id: b631758a-142d-425f-b9aa-f756d85cb979
    internal-label: Campaign Email Designer
  - id: c858a28b-ea19-49b0-8d48-828717fad89c
    internal-label: Prepare and test messages
  - id: c5474392-5419-4296-9e41-f6f4ce4f6e9b
    internal-label: Administration
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: e95a583b-fcfa-4524-8666-46a29c828119
    internal-label: Email messaging
  - id: c8da4fdd-eb94-4751-a43c-f82733fb2d6e
    internal-label: Email design
  - id: d5bbe3da-ba85-4242-817e-54f7c4b943e0
    internal-label: A/B testing
  - id: f4da0e76-df77-451e-ad61-21afb7bd8810
    internal-label: Manage deliverability
  - id: b4ecd69f-2adf-4219-bc47-c9cd9a53c118
    internal-label: Channel configuration
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
source-git-commit: d7e5f68c0d2e0b94fd5cfdf2981bed29f33d9f62
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 18%
---
# 設定並傳送傳遞 {#configuring-and-sending-the-delivery}

本頁面說明Campaign Classic v7內部部署和混合安裝專屬的傳送設定。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要進一步瞭解傳遞傳送設定，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/validate/configure-and-send){target=_blank}

## 傳遞其他引數 {#delivery-additiona-parameters}

在傳送傳遞之前，您可以透過&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤，在傳遞屬性中定義傳送引數。

* **[!UICONTROL Test SMTP delivery]**：使用此選項來測試透過SMTP的傳送。 處理傳遞直到連線到 SMTP 伺服器，但不傳送：對於傳遞的每個收件者，Campaign 會連線到 SMTP 提供者伺服器，執行 SMTP RCPT TO 命令，並在 SMTP DATA 命令之前關閉連線。

  >[!NOTE]
  >
  >* 此選項不得在中間來源中設定。
  >
  >* 在[本節](../../installation/using/configure-delivery-settings.md)中進一步瞭解SMTP伺服器組態。

## 設定重試 {#configuring-retries}

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign將不再使用傳送中的重試設定。 軟退信重試次數和兩次之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，傳送引數的&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤的中央區段會指出在傳送後一天應執行多少次重試，以及重試之間的最小延遲。

![](assets/s_ncs_user_wizard_retry_param.png)

根據預設，排程在傳送的第一天進行五次重試，最小間隔為一小時分佈在一天中的24小時。 之後及傳遞期限（在&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤中定義）之前，每天會設定一次重試。 請參閱[定義有效期間](#defining-validity-period)。

## 定義有效期間 {#defining-validity-period}

當傳送已啟動時，可傳送訊息（以及任何重試），直到傳送期限為止。 透過&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤在傳遞屬性中指出這點。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;欄位可讓您輸入全域傳遞重試的限制。 這表示 Adobe Campaign 會傳送從開始日期開始的訊息，然後，對於僅傳回錯誤的訊息，會執行一般、可設定的重試，直到達到效度限制為止。

  >[!IMPORTANT]
  >
  >針對託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，則只有在設為&#x200B;**3.5天或更短時間時，才會使用Campaign電子郵件傳遞中的&#x200B;**[!UICONTROL Delivery duration]**設定**。 如果您定義的值超過3.5天，則不會考慮該值。

* **資源效度限制**： **[!UICONTROL Validity limit]**&#x200B;欄位是用於上傳的資源，主要用於映象頁面和影像。 本頁上的資源在限定時間內有效（以節省磁碟空間）。

  此欄位中的值可以下列單位表示： **s**&#x200B;代表秒數，**m**&#x200B;代表分鐘，**h**&#x200B;代表小時，**d**&#x200B;代表天（預設），**y**&#x200B;代表年。
