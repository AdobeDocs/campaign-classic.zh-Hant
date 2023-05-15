---
product: campaign
title: 驗證
description: 驗證
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 驗證{#validating}



驗證傳遞時的全域概念，在 [本節](steps-validating-the-delivery.md).

在傳遞分析期間生成直接郵件傳遞的輸出檔案。 檔案的內容取決於選取的輸出欄(請參閱 [擷取檔案](defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>分析階段於 [分析傳送](steps-validating-the-delivery.md#analyzing-the-delivery).

在分析階段期間，會產生檔案，但不會更新與收件者（即傳送記錄檔）相關的資訊。 因此，您可以取消此作業，而不會有任何風險。

在按一下前，檢查分析結果和輸出檔案的內容 **[!UICONTROL Confirm delivery]**. 確認訊息可讓您啟動傳送。

傳送確認會開始指定檔案中的資料擷取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然後，您可以關閉精靈，並透過 **[!UICONTROL Delivery]** 標籤，可透過傳送詳細資料存取。

您可以從 **[!UICONTROL Analysis]** 標籤。

有兩種模式：

* **[!UICONTROL Messages are considered sent after validation]** （預設模式）:在此函式模式中，當運算子確認傳送時，會更新所有廣播（其狀態會從「擱置中傳送」傳遞至「已傳送」），且傳送會自動設為 **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式可讓您透過服務提供者傳送的外部檔案更新broadlogs。 在此情況下，需要使用處理此資訊的工作流程來更新broadlog狀態。

   >[!NOTE]
   >
   >在此情況下，傳送的狀態也需要變更為 **[!UICONTROL Finished]** 更新broadlog時由使用者指定。
