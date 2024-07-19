---
product: campaign
title: 建立事件類型
description: 瞭解如何建立符合您要在Adobe Campaign Classic中傳送之交易式訊息的事件型別
feature: Transactional Messaging, Message Center
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 建立事件類型 {#creating-event-types}



為了確保每個事件都可以變更為個人化訊息，您必須先建立&#x200B;**事件型別**。

當[建立訊息範本](../../message-center/using/creating-the-message-template.md)時，您將選取符合您要傳送之訊息的事件型別。

>[!IMPORTANT]
>
>您必須先建立事件型別，才能在訊息範本中使用它們。

若要建立Adobe Campaign將處理的事件型別，請遵循下列步驟：

1. 登入&#x200B;**控制例項**。

1. 前往樹狀結構的&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;資料夾。

1. 從清單中選取&#x200B;**[!UICONTROL Event type]**。

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以建立分項清單。 這可以是訂單確認、密碼變更、訂單傳遞變更等。

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >每個事件型別都必須符合&#x200B;**[!UICONTROL Event type]**&#x200B;列舉中的一個值。

1. 建立分項清單值後，請先登出再登入執行個體，才能讓建立生效。

>[!NOTE]
>
>深入瞭解[列舉管理](../../platform/using/managing-enumerations.md)中的逐項清單。


