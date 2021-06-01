---
product: campaign
title: 建立事件類型
description: 了解如何建立符合您要在Adobe Campaign Classic中傳送的交易式訊息的事件類型。
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 建立事件類型 {#creating-event-types}

若要確保每個事件都可變更為個人化訊息，您必須先建立&#x200B;**事件類型**。

當[建立訊息範本](../../message-center/using/creating-the-message-template.md)時，您將選取符合您要傳送之訊息的事件類型。

>[!IMPORTANT]
>
>您必須先建立事件類型，才能在訊息範本中使用它們。

若要建立由Adobe Campaign處理的事件類型，請遵循下列步驟：

1. 登錄到&#x200B;**控制實例**。

1. 轉至樹的&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;資料夾。

1. 從清單中選擇&#x200B;**[!UICONTROL Event type]**。

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立分項清單。 這可以是訂單確認、密碼變更、訂單傳送變更等。

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >每個事件類型都必須符合&#x200B;**[!UICONTROL Event type]**&#x200B;分項清單中的值。

1. 建立分項清單值後，請登出再重新登入您的例項，讓建立生效。

>[!NOTE]
>
>進一步了解[枚舉管理](../../platform/using/managing-enumerations.md)中的分項清單。


