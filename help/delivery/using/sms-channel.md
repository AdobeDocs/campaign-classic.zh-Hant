---
product: campaign
title: 開始使用簡訊頻道
description: 開始使用簡訊頻道
feature: SMS
role: User
exl-id: 6fc2ab09-8ea7-4865-88ad-bd45eee68958
source-git-commit: d3d731c64cb5a430de6adac3aeb326f74134c436
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# 開始使用簡訊頻道{#sms-channel}

使用Adobe Campaign傳送簡訊給行動裝置上的客戶。 您可以從SMS編輯器以文字格式建立、個人化和預覽訊息。

SMS是直接且高效的管道，無論使用者身在何處，都可聯絡上他們。 SMS具有高開放率及幾乎即時的傳送方式，非常適合用於時效性高的警示、交易式更新及簡明的促銷訊息。 使用簡訊補充您的跨頻道策略，並提供有影響力的即時通訊。 在[Adobe Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hant){target=_blank}中瞭解如何有效設定和使用簡訊頻道。

做為Campaign v8促銷活動的一部分，Campaign Classic檔案已重新整理。 現在僅可在Campaign v8檔案集中使用常見功能。

>[!BEGINTABS]

>[!TAB 簡訊頻道檔案]

若要深入瞭解簡訊頻道，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hant){target=_blank}。


[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hant){target=_blank}


>[!TAB SMS傳遞建立]

在Campaign v8檔案中瞭解與建立簡訊傳遞相關的關鍵步驟：

* [簡訊通道概觀](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms.html?lang=zh-Hant){target="_blank"}：瞭解您如何透過行動裝置傳送簡訊給您的客戶。
* [建立SMS傳遞](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/create-sms.html?lang=zh-Hant){target="_blank"}：探索建立新SMS傳遞所需的不同步驟。
* [定義內容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-content.html?lang=zh-Hant){target="_blank"}：瞭解如何個人化SMS訊息的內容。
* [選取對象](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/create-sms/sms-audience.html?lang=zh-Hant){target="_blank"}：主要目標已從Adobe Campaign資料庫擷取，或也可以儲存在外部檔案中。
* [傳送SMS校樣](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-proofs.html?lang=zh-Hant)：必須設定傳遞驗證週期。 將內容傳送給對象之前，請確定內容已核准。
* [傳送給對象](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/validate-sms/sms-send.html?lang=zh-Hant)：當您的SMS通過驗證時，您現在可以傳送給其對象。
* [監視及追蹤SMS](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/sms/sms-monitor.html?lang=zh-Hant)：監視您的SMS傳遞，以確保您的行銷活動有效率。


>[!TAB 簡訊設定]

請參閱這些頁面以瞭解SMS設定：

* [獨立設定](sms-set-up.md)：瞭解如何在獨立執行個體上設定SMS頻道。
* [中間來源組態](sms-set-up-mid.md)：探索如何傳送至具有中間伺服器的行動電話。
* [SMS聯結器](sms-protocol.md)：瞭解SMS聯結器通訊協定與設定。
* [其他設定](sms-send.md)：瞭解進階引數和其他額外設定。
* [疑難排解](troubleshooting-sms.md)：我們已列出一系列潛在問題及其解決方案。

>[!ENDTABS]



<!--
Use Adobe Campaign to send personalized SMS messages.

Before starting sending SMS:

* Make sure recipient profiles contain at least a mobile phone in their profile.
* Learn more about the Adobe Campaign [Delivery best practices](delivery-best-practices.md).

The key steps to send a SMS are as follows:

* [Configure the SMS channel](sms-set-up.md)
* [Create a SMS delivery](sms-create.md)
* [Define the audience](sms-create.md#selecting-the-target-population)
* [Define the SMS content](sms-create.md#defining-the-sms-content)
* [Send, monitor and track SMS](sms-send.md)
* [Troubleshoot](troubleshooting-sms.md)

In addition, you need to be familiar with SMS protocol and settings. Walk through the connection set up between Adobe Campaign and a SMPP provider in [this document](sms-protocol.md)

For global information on how to create a delivery, refer to [this section](steps-about-delivery-creation-steps.md).

>[!NOTE]
>
>Adobe Campaign also lets you submit notifications on mobile terminals, via its **Adobe Campaign Mobile App Channel (NMAC)** option. 
> 
>For more on this, refer to the [Get started with mobile app channel](about-mobile-app-channel.md) section.
-->