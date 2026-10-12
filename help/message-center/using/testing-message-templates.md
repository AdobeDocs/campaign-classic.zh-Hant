---
product: campaign
title: 測試異動訊息範本
description: 瞭解如何管理異動訊息中的種子地址，以便在Adobe Campaign Classic中預覽和測試它們
feature: Transactional Messaging, Message Center, Templates
audience: message-center
content-type: reference
topic-tags: message-templates
exl-id: 417004c9-ed96-4b98-a518-a3aa6123ee7b
TQID: 'https://experienceleague.adobe.com/jcmXX4aMPaTBatt4m3s-IAaAeoXnjmPaEE4oqIDoIOI'
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: 6d358f27-4f3c-5ddf-9159-05192e672ba7
    internal-label: Message Center
  - id: baf8e746-117b-5e73-b179-0a83edc0295f
    internal-label: Templates
  - id: a4671286-a59f-47e3-b97b-90627a1977d5
    internal-label: Communication channels
subfeature_v2:
  - id: d3b34fea-a110-482f-adb2-aae8d686bac8
    internal-label: Transactional messaging
topic_v2:
  - id: e0eb8757-182f-49f3-94a4-1587d16f5094
    internal-label: Personalization
source-git-commit: 617db6f51887118c965b8938b2b9f14335293875
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%
---
# 測試異動訊息範本 {#testing-message-templates}

在您的[訊息範本](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template){target="_blank"} （Campaign v8檔案）準備就緒後，請依照下列步驟預覽及測試。

作為從Campaign v7轉變到v8的一部分，Campaign Classic檔案集已簡化並重新組織。 Campaign v8檔案集中現在提供常見功能。 若要瞭解如何新增種子地址、預覽交易式訊息及傳送校樣，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}。

[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#test-message-template){target=_blank}

## 個人化資料 {#personalization-data}

您可在訊息範本中使用資料，以測試異動訊息個人化。 此功能用於產生預覽或傳送校樣。 您也可以為不同的網際網路存取提供者顯示訊息的呈現。 如需詳細資訊，請參閱[收件匣轉譯](../../delivery/using/inbox-rendering.md)。

此資料的用途是在訊息最終傳送之前測試訊息。 這些訊息與要處理的實際資料不一致。 但是，XML結構必須與執行例項中儲存之事件的結構相同，如下所示：

![](assets/messagecenter_create_custo_006.png)

此資訊可讓您使用個人化標籤來個人化訊息內容(如需詳細資訊，請參閱[建立訊息內容](https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/send/real-time/transactional-template#create-message-content){target="_blank"} （Campaign v8檔案）。

1. 選取異動訊息範本。

1. 在範本中，按一下「**[!UICONTROL Seed addresses]**」標籤。

1. 在事件內容中，以XML格式輸入測試資訊。

   ![](assets/messagecenter_create_custo_001.png)

1. 按一下 **[!UICONTROL Save]**。
