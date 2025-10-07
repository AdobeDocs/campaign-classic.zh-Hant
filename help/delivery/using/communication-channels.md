---
product: campaign
title: 通訊管道
description: 建立傳遞，以在不同通道上傳送個人化訊息。
feature: Cross Channel Orchestration, Email, SMS, In App, Direct Mail, Push
role: User
exl-id: 92b5e013-b619-4f0b-b0b1-1fc2e653ceac
source-git-commit: 89e350c727fb9379d28916f79d9749f22fd4974f
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 14%

---

# 通訊管道{#communication-channels}

透過 Adobe Campaign，您可以傳送跨頻道行銷活動，包括電子郵件、簡訊、LINE 訊息、推播通知和直接郵件，並使用各種專屬報告來評估行銷成效。 這些訊息是透過傳遞進行設計和傳送，而且可針對每位收件者進行個人化。

核心功能包括目標定位、定義及個人化訊息、通訊執行及相關的營運報告。

做為Campaign v8促銷活動的一部分，Campaign Classic檔案已重新整理。 現在僅可在Campaign v8檔案集中使用常見功能。



>[!BEGINTABS]

>[!TAB 通訊通道檔案]

若要深入瞭解通訊管道，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=zh-Hant){target=_blank}。


[![影像](../../assets/do-not-localize/learn-more-button.svg)](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=zh-Hant){target=_blank}


>[!TAB 傳遞內容與對象]

在Campaign v8檔案中瞭解與傳送建立、內容和對象相關的重要步驟：

* [建立傳遞](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant#create-the-delivery){target="_blank"}：瞭解如何建立單次傳遞。
* [定義內容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant#content-of-the-delivery){target="_blank"}：設定每個頻道專屬的傳遞內容。
* [指定對象](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant#target-population){target="_blank"}：定義幾種目標型別：主要對象、證明目標、種子地址和控制群組。
* [使用傳遞範本](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-templates.html?lang=zh-Hant){target="_blank"}：瞭解如何定義範本，以方便傳遞建立。





>[!TAB 傳遞驗證與傳送]

請參閱這些頁面，在Campaign v8檔案中瞭解傳遞驗證、傳送和最佳實務：

* [驗證傳遞](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant#validate-the-delivery){target="_blank"}：瞭解如何先驗證傳遞，再將其傳送至主要目標。
* [傳送傳遞](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant#configuring-and-sending-the-delivery){target="_blank"}：設定傳遞設定並定義傳送訊息的方式。
* [傳遞最佳實務](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/delivery-best-practices.html?lang=zh-Hant){target="_blank"}：請參閱與Campaign傳遞功能相關的最佳實務。

>[!ENDTABS]

以下設定專屬於Campaign Classic。 如需其他傳遞設定，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/gs-message.html?lang=zh-Hant){target="_blank"}。

+++ **傳遞分析**

**改善傳遞分析效能**

若要加速傳遞準備，您可以在啟動分析之前核取&#x200B;**[!UICONTROL Prepare the delivery parts in the database]**&#x200B;選項。

啟用此選項時，會直接在資料庫中執行傳遞準備，大幅加快分析。

目前，此選項只有在符合下列條件時才可用：

* 傳遞必須是電子郵件。 目前不支援其他管道。
* 您不得使用中間來源或外部路由，只能使用大量傳遞路由型別。 您可以檢查&#x200B;**[!UICONTROL General]**&#x200B;之&#x200B;**[!UICONTROL Delivery properties]**&#x200B;索引標籤中使用的路由。
* 您無法鎖定來自外部檔案的母體。 若為單一傳遞，請從&#x200B;**[!UICONTROL To]**&#x200B;按一下&#x200B;**[!UICONTROL Email parameters]**&#x200B;連結，並檢查是否已選取&#x200B;**[!UICONTROL Defined in the database]**&#x200B;選項。 針對工作流程中使用的傳遞，檢查收件者在&#x200B;**[!UICONTROL Specified by the inbound event(s)]**&#x200B;索引標籤中是否為&#x200B;**[!UICONTROL Delivery]**。
* 您必須使用PostgreSQL資料庫。

**設定分析優先順序**

當傳遞為行銷活動的一部分時，**[!UICONTROL Advanced]**&#x200B;索引標籤會提供其他選項。 這可讓您在相同行銷活動中組織傳送的處理順序。

傳送前，會分析每個傳遞。 分析持續時間取決於傳遞擷取檔案。 檔案大小愈大，分析所需的時間愈長，下列傳送作業就會等待一段時間。

**[!UICONTROL Message preparation by the scheduler]**&#x200B;的選項可讓您在行銷活動工作流程中排定傳遞分析的優先順序。

![](assets/delivery_analysis_priority.png)

如果傳送過大，最好將低優先順序指派給它，以避免減慢分析其他工作流程傳送的速度。

>[!NOTE]
>
>若要確保較大的傳遞分析不會減慢工作流程的進度，您可以按一下&#x200B;**[!UICONTROL Schedule execution for a time of low activity]**&#x200B;以排程其執行。

+++

+++ **傳遞傳送**

**設定重試**

因為&#x200B;**Soft**&#x200B;或&#x200B;**Ignored**&#x200B;錯誤而暫時未傳遞的郵件可能會自動重試。 傳送失敗型別和原因顯示於此[區段](understanding-delivery-failures.md#delivery-failure-types-and-reasons)。

>[!IMPORTANT]
>
>對於託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，Campaign將不再使用傳送中的重試設定。 軟退信重試次數和兩次之間的時間長度由Enhanced MTA根據從訊息的電子郵件網域傳回的退信回應的型別和嚴重性來決定。

對於使用舊版Campaign MTA的內部部署安裝和託管/混合安裝，傳送引數的&#x200B;**[!UICONTROL Delivery]**&#x200B;索引標籤的中央區段會指出在傳送後一天應執行多少次重試，以及重試之間的最小延遲。

![](assets/s_ncs_user_wizard_retry_param.png)

根據預設，排程在傳送的第一天進行五次重試，最小間隔為一小時分佈在一天中的24小時。 之後及傳遞期限（在&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤中定義）之前，每天會設定一次重試。 請參閱[定義有效期間](#defining-validity-period)。

**定義有效期間**

當傳送已啟動時，可傳送訊息（以及任何重試），直到傳送期限為止。 透過&#x200B;**[!UICONTROL Validity]**&#x200B;索引標籤在傳遞屬性中指出這點。

![](assets/s_ncs_user_email_del_valid_period.png)

* **[!UICONTROL Delivery duration]**&#x200B;欄位可讓您輸入全域傳遞重試的限制。 這表示 Adobe Campaign 會傳送從開始日期開始的訊息，然後，對於僅傳回錯誤的訊息，會執行一般、可設定的重試，直到達到效度限制為止。

  您也可以選擇指定日期。若要這麼做，請選取&#x200B;**[!UICONTROL Explicitly set validity dates]**。 在此情況下，傳遞和有效期限制日期也讓您指定時間。預設使用目前時間，但您可以直接在輸入欄位中修改。

  >[!IMPORTANT]
  >
  >針對託管或混合式安裝，如果您已升級至[Enhanced MTA](sending-with-enhanced-mta.md)，則只有在設為&#x200B;**[!UICONTROL Delivery duration]** 3.5天或更短時間時，才會使用Campaign電子郵件傳遞中的&#x200B;**設定**。 如果您定義的值超過3.5天，則不會考慮該值。

* **資源效度限制**： **[!UICONTROL Validity limit]**&#x200B;欄位是用於上傳的資源，主要用於映象頁面和影像。 本頁上的資源在限定時間內有效（以節省磁碟空間）。

  此欄位中的值可以以[此區段](../../platform/using/adobe-campaign-workspace.md#default-units)中列出的單位來表示。

+++

<!--

   Learn how to create a one-shot single delivery. You can create other types of deliveries to build your use cases. 

For more information about the different types of deliveries and how to create them, refer to the [Campaign v8 documentation](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/create-message.html?lang=zh-Hant){target="_blank"}. 

>[!NOTE]
>
>Adobe Campaign offers a set of tools to monitor your deliverability and optimize email sending. Learn more in [this section](about-deliverability.md).

Delivery sending can be automated by preparing a delivery and/or sending it in the process of a workflow. For more on delivery-type activities in workflows, refer to [this section](../../workflow/using/about-action-activities.md).

Adobe Campaign offers the following delivery channels:

1. **Email channel**: email deliveries let you send personalized emails to the target population. Refer to [About email channel](about-email-channel.md).
1. **Direct mail channel**: direct mail deliveries let you generate an extraction file which contains data on the target population. Refer to [About direct mail channel](about-direct-mail-channel.md).
1. **Mobile channel**: deliveries on mobile channels let you send personalized SMS or LINE messages to the target population. Refer to [SMS channel](sms-channel.md).
1. **Mobile application channel**: mobile app deliveries let you send notifications to iOS and Android systems. Refer to the [Mobile app channel](about-mobile-app-channel.md) chapter.

   Other channels are described on [this section](#other-channels).

   >[!NOTE]
   >
   >The number of available channels depends on your contract. Please check your license agreement.

Deliveries can be carried out **online** (via email, one of the mobile channels and push notifications), and **offline** (direct mail channel).

Depending on the channel, delivery modes can be:

* Direct mass delivery via Adobe Campaign (default mode for email channel).
* External delivery via a specialist operator who is given the output file generated by the delivery assistant (default mode for direct mail channel).

External accounts are configured via the **[!UICONTROL Administration > Platform > External accounts]** node. This configuration should be performed by expert users only.

## Email deliveries {#email-deliveries}

The [Email channel](about-email-channel.md) is one of the core channels in Adobe Campaign, allowing you to schedule and send personalized emails to specific targets.

You can send different types of emails:

* Single-send emails: emails that you can send once to a defined target. They are usually used to promote a specific content that would be prepared and sent only once (newsletter, promotional email, etc.).
* Recurring emails: in a campaign, send the same email regularly and aggregate each send and its reports on a periodic basis. The same email is sent, but usually to a different target, based on the eligible target for the day of the send. A common example is a birthday email. For more on this, refer to [Recurring deliveries](../../workflow/using/recurring-delivery.md).
* Transactional emails: unitary emails that are triggered based on your customers' behavior. Refer to [Transactional messaging](../../message-center/using/about-transactional-messaging.md).

To learn about delivery usage and recommendations, consult Campaign [Delivery best practices](delivery-best-practices.md).

For more on the different types of deliveries, refer to [this section](#types-of-deliveries).

## Mobile deliveries {#mobile-deliveries}

Adobe Campaign allows you to deliver [SMS](sms-channel.md) and [LINE](line-channel.md) messages on mobiles.

For SMS messages, you can create, modify, and personalize messages in text format only. You can also preview your SMS messages before they are sent.

For LINE messages, you can send text or images and links.

To deliver SMS or LINE messages to a mobile phone you need:

* An external account configured on the **[!UICONTROL Mobile (SMS)]** channel or on the **[!UICONTROL LINE]** channel. 
* An SMS or LINE delivery template that is correctly linked to this external account.

## Push notifications {#push-notifications}

Adobe Campaign allows you to send personalized and segmented [push notifications](about-mobile-app-channel.md) on iOS and Android mobile devices, through dedicated apps. Once configuration and integration steps have been performed, iOS and Android deliveries can be created and sent. You can also design rich notifications with images or videos.

## Direct mail {#direct-mail}

[Direct mail](about-direct-mail-channel.md) is an offline channel that allows you to personalize and generate the file required by direct mail providers. It gives you the possibility to mix online and offline channels in your customer journeys.

Online channels allow you to create your messages (email, SMS, mobile app delivery, etc.) and send them to your audience directly from Adobe Campaign. With offline channels, it is different. When you prepare a direct mail delivery, Adobe Campaign generates a file including all the targeted profiles and the chosen contact information (postal address for example). You will then be able to send this file to your direct mail provider who will take care of the actual sending.

## Other channels {#other-channels}

Adobe Campaign offers Telephone delivery template, which is used to create external deliveries. Using this channel implies you set up dedicated methodologies to process output files. Configuration steps are the same as for [Direct mail channel](about-direct-mail-channel.md).

>[!NOTE]
>
>The Telephone channel is not available out-of-the-box. Its implementation requires Adobe Consulting or an Adobe Partner to be engaged. Please reach out to your Adobe representative for more information.

In addition, 'Other' type deliveries use a specific technical template which does not execute a process: this lets them manage marketing actions executed outside of the Adobe Campaign platform.

This channel has no specific mechanism. It is a generic channel that has its own external account routing option, delivery template type and campaign workflow activity, just like any other communication channel available in Adobe Campaign.

This channel is designed for descriptive purposes only, for example to define deliveries for which you want to keep a trace of the target of a campaign performed in a tool other than Adobe Campaign.

## Types of deliveries{#types-of-deliveries}

There are three types of delivery objects in Campaign:

### Single delivery {#single-delivery}

A **delivery** is a standalone delivery object that is executed once. It can be duplicated, prepared again, but as long as it is in its final state (canceled, stopped, finished), it cannot be reused.

Deliveries can be created either from the list of deliveries, or within a workflow via a [Delivery](../../workflow/using/delivery.md) activity.

Workflows also provide specific delivery activities according to the type of channel you want to use. For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

### Recurring delivery {#recurring-delivery}

A **recurring delivery** lets you create a new delivery each time the activity is executed. This avoids you having to create a new delivery for recurring tasks.

As an example, if you run this type of activity once a month, you will end up with 12 deliveries after a year.

Recurring deliveries are created within workflows via the [Recurring delivery activity](../../workflow/using/recurring-delivery.md). An example of this activity being used is presented in this section: [Creating a recurring delivery in a targeting workflow](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

### Continuous delivery {#continuous-delivery}

A **continuous delivery** lets you add new recipients to an existing delivery, which avoids having to create a new delivery each time it is executed.

If an information in the delivery changes (content, name, etc.), a new delivery object is created at the delivery execution. If no information was changed, the same delivery object is reused and the delivery and tracking logs are added in the same object.

As an example, if you run this type of activity once a month, you will end up with a single delivery after a year (provided you did not make any change to the delivery).

Continuous deliveries are created within workflows via the [Continuous delivery activity](../../workflow/using/continuous-delivery.md).-->
