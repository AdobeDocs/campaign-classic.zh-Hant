---
product: campaign
title: 建立事件類型
description: 了解如何建立符合您要在Adobe Campaign Classic中傳送的交易式訊息的事件類型。
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 建立事件類型 {#creating-event-types}

![](../../assets/v7-only.svg)

若要確保每個事件都可變更為個人化訊息，您必須先建立 **事件類型**.

當 [建立訊息範本](../../message-center/using/creating-the-message-template.md)，您將選取符合您要傳送之訊息的事件類型。

>[!IMPORTANT]
>
>您必須先建立事件類型，才能在訊息範本中使用它們。

若要建立Adobe Campaign將處理的事件類型，請遵循下列步驟：

1. 登入 **控制實例**.

1. 前往 **[!UICONTROL Administration > Platform > Enumerations]** 樹的資料夾。

1. 選擇 **[!UICONTROL Event type]** 從清單中。

1. 按一下 **[!UICONTROL Add]** 來建立分項清單。 這可以是訂單確認、密碼變更、訂單傳送變更等。

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >每個事件類型都必須符合 **[!UICONTROL Event type]** 枚舉。

1. 建立分項清單值後，請登出再重新登入您的例項，讓建立生效。

>[!NOTE]
>
>進一步了解 [枚舉管理](../../platform/using/managing-enumerations.md).


