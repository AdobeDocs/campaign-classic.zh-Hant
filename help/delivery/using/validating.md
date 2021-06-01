---
product: campaign
title: 驗證
description: 驗證
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 驗證{#validating}

驗證傳送時的全域概念會顯示在[此區段](../../delivery/using/steps-validating-the-delivery.md)中。

在傳遞分析期間生成直接郵件傳遞的輸出檔案。 檔案的內容取決於所選的輸出列（請參閱[提取檔案](../../delivery/using/defining-the-direct-mail-content.md#extraction-file)）。

>[!NOTE]
>
>分析階段在[分析傳送](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)中詳細說明。

在分析階段期間，會產生檔案，但不會更新與收件者（即傳送記錄檔）相關的資訊。 因此，您可以取消此作業，而不會有任何風險。

在按一下&#x200B;**[!UICONTROL Confirm delivery]**&#x200B;之前，檢查分析結果和輸出檔案的內容。 確認訊息可讓您啟動傳送。

傳送確認會開始指定檔案中的資料擷取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然後，您可以關閉精靈，並透過&#x200B;**[!UICONTROL Delivery]**&#x200B;標籤查看傳送記錄，可透過傳送詳細資料存取。

您可以從傳送屬性的&#x200B;**[!UICONTROL Analysis]**&#x200B;標籤設定傳送記錄擷取模式。

有兩種模式：

* **[!UICONTROL Messages are considered sent after validation]** （預設模式）:在此函式模式中，當運算子確認傳送時（其狀態會從「擱置中傳送」傳遞至「已傳送」），且傳送會自動設為 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式可讓您透過服務提供者傳送的外部檔案更新broadlogs。在此情況下，需要使用處理此資訊的工作流程來更新broadlog狀態。

   >[!NOTE]
   >
   >在此情況下，當更新廣播時，使用者也需要將傳送的狀態變更為&#x200B;**[!UICONTROL Finished]**。
