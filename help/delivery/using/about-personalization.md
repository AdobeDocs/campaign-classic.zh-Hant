---
product: campaign
title: 開始使用個人化
description: 瞭解如何在Campaign中個人化訊息和使用條件式內容
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Personalization
role: User
exl-id: 555082a2-1b62-4aa4-b80c-77b1a1ef9491
source-git-commit: a1e9fec0e9c85bf25b79e24a7432dfb45bd1a0cb
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 14%

---

# 開始使用個人化{#about-personalization}

有幾種不同的方式可個人化由 Adobe Campaign 傳送的訊息，包含訊息的內容或外觀。尤其是根據收件者輪廓中的準則，可以將這些方法結合使用。對於電子郵件傳遞，您可以從郵件的&#x200B;**[!UICONTROL Source]**&#x200B;索引標籤直接在JavaScript中定義傳遞的元素和個人化條件。 一般而言，Adobe Campaign 允許您：

* 個人化訊息格式。檢視[訊息內容](defining-the-email-content.md#message-content)。
* 插入動態的個人化欄位。請參閱[個人化欄位](personalization-fields.md)。
* 插入預先定義的個人化區塊。 請參閱[個人化區塊](personalization-blocks.md)。
* 建立有條件的內容。請參閱[條件式內容](conditional-content.md)區段。

>[!CAUTION]
>
>下列變數是可用於個人化的內部變數，但不可修改： **傳遞**、**訊息**、**資料來源**、**targetData**、**提供者**、**抵用券**、**抵用券值**、**主張**。


使用Adobe Campaign，個人化您的傳遞，以傳送符合每個收件者設定檔和興趣的訊息。

Personalization可協助您讓訊息更具相關性和吸引力。 您可以使用收件者資料來調整內容、新增動態欄位，或根據條件顯示不同資訊。 在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=zh-Hant){target=_blank}中瞭解如何在傳遞中設定和使用個人化功能。

做為Campaign v8促銷活動的一部分，Campaign Classic檔案已重新整理。 現在僅可在Campaign v8檔案集中使用常見功能。

>[!BEGINTABS]

>[!TAB 內容個人化檔案]

若要深入瞭解內容個人化，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=zh-Hant){target=_blank}。


[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/personalize/personalize.html?lang=zh-Hant){target=_blank}


>[!TAB 電子郵件傳遞建立]

在Campaign v8檔案中瞭解與建立電子郵件傳遞相關的關鍵步驟：

* [建立電子郵件傳遞](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email.html?lang=zh-Hant){target="_blank"}：瞭解建立電子郵件傳遞所需的不同步驟。
* [定義電子郵件內容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-the-email-content.html?lang=zh-Hant){target="_blank"}：定義您的電子郵件將包含的內容：寄件者、主旨、內容、影像。
* [定義互動式內容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/defining-interactive-content.html?lang=zh-Hant){target="_blank"}：使用互動式AMP for Email格式來傳送動態電子郵件。
* [在日文行動裝置上傳送電子郵件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/sending-emails-on-japanese-mobiles.html?lang=zh-Hant){target="_blank"}：在行動裝置上使用三種特定日文格式之一。
* [將檔案附加至電子郵件](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/attaching-files.html?lang=zh-Hant){target="_blank"}：瞭解將一或多個檔案附加至電子郵件的不同方式。


>[!TAB 電子郵件參數]

請參閱這些頁面，以在Campaign v8檔案中瞭解電子郵件引數：

* [連結至映象頁面](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/mirror-page.html?lang=zh-Hant){target="_blank"}：設定映象頁面，以確保您的使用者端永遠都能獲得最佳轉譯體驗。
* [新增密件副本地址](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-bcc.html?lang=zh-Hant){target="_blank"}：設定Adobe Campaign以保留從您的平台傳送的電子郵件復本。
* [定義其他電子郵件引數](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/emails/email-parameters.html?lang=zh-Hant){target="_blank"}：進一步瞭解傳遞屬性中可用的選項和引數。

另請參閱此[頁面](sending-with-enhanced-mta.md)，瞭解增強型MTA。

>[!ENDTABS]





<!--
Adobe Campaign lets you mass deliver personalized electronic messages to a target population.

Before starting sending emails:

* Make sure recipient profiles contain at least an email address.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).
* Read out these sections to learn more about Deliverability: [Deliverability management in Campaign](about-deliverability.md) and [Deliverability best practices guide](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/introduction.html?lang=zh-Hant).

The key steps to send an email are as follows:

* [Create an email delivery](creating-an-email-delivery.md)
* [Define the target population](steps-defining-the-target-population.md)
* [Define the email content](defining-the-email-content.md)
* [Send the email](sending-messages.md)
* [Monitor the delivery](about-delivery-monitoring.md)

The sections below provide information that is specific to the email channel. For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).
-->