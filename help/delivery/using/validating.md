---
solution: Campaign Classic
product: campaign
title: 驗證
description: 驗證
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---


# 驗證{#validating}

驗證傳送時的全域概念會顯示在[本節](../../delivery/using/steps-validating-the-delivery.md)中。

在遞送分析期間生成直接郵件遞送的輸出檔案。 檔案的內容取決於所選的輸出列（請參閱[抽取檔案](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)）。

>[!NOTE]
>
>分析階段詳見[分析遞送](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在分析階段期間，會產生檔案，但不會更新與收件者（即傳送記錄）相關的資訊。 因此，您可以取消此作業，而不會有任何風險。

在按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;之前，檢查分析結果和輸出檔案的內容。 確認訊息可讓您啟動傳送。

傳送確認會啟動指定檔案中的資料擷取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然後，您可以關閉嚮導，並通過&#x200B;**[!UICONTROL Delivery]**&#x200B;頁籤查看交付日誌，該頁籤可通過交付詳細資訊訪問。

您可以從傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤中設定傳送記錄檔擷取模式。

有兩種模式：

* **[!UICONTROL Messages are considered sent after validation]** （預設模式）:在此函式模式中，當運算子確認傳送（其狀態從「待定傳送」傳遞至「已傳送」），且傳送自動設為時，會更新所有廣告 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式允許您通過服務提供商發送的外部檔案更新廣播。在這種情況下，需要使用處理此資訊的工作流來更新廣播狀態。

   >[!NOTE]
   >
   >在這種情況下，當廣播更新後，用戶還需要將傳送的狀態更改為&#x200B;**[!UICONTROL Finished]**。
