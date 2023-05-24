---
product: campaign
title: 建立事件類型
description: 瞭解如何建立符合您要在Adobe Campaign Classic中傳送之交易式訊息的事件型別
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: message-center
content-type: reference
topic-tags: instance-configuration
exl-id: 98b7c827-f31d-46a6-a28d-40a78a4b4248
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 3%

---

# 建立事件類型 {#creating-event-types}



若要確保每個事件都可以變更為個人化訊息，您首先需要建立 **事件型別**.

時間 [建立訊息範本](../../message-center/using/creating-the-message-template.md)，則會選取符合您要傳送之訊息的事件型別。

>[!IMPORTANT]
>
>您必須先建立事件型別，才能在訊息範本中使用它們。

若要建立將由Adobe Campaign處理的事件型別，請遵循下列步驟：

1. 登入 **控制例項**.

1. 前往 **[!UICONTROL Administration > Platform > Enumerations]** 樹狀結構的資料夾。

1. 選取 **[!UICONTROL Event type]** 從清單中。

1. 按一下 **[!UICONTROL Add]** 以建立分項清單。 這可以是訂單確認、密碼變更、訂單傳遞變更等。

   ![](assets/messagecenter_eventtype_enum_001.png)

   >[!IMPORTANT]
   >
   >每個事件型別都必須符合 **[!UICONTROL Event type]** 分項清單。

1. 建立分項清單值後，請先登出再登入執行個體，才能使建立生效。

>[!NOTE]
>
>進一步瞭解中的分項清單 [分項清單管理](../../platform/using/managing-enumerations.md).


