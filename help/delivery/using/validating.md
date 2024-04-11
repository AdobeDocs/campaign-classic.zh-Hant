---
product: campaign
title: 驗證
description: 驗證
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 1%

---

# 驗證{#validating}



驗證傳遞時的全域概念如下所述： [本節](steps-validating-the-delivery.md).

直接郵件傳遞的輸出檔案會在傳遞分析期間產生。 檔案的內容取決於選取的輸出欄(請參閱 [擷取檔案](defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>有關分析階段的詳情，請參閱 [分析傳遞](steps-validating-the-delivery.md#analyzing-the-delivery).

在分析階段會產生檔案，但未更新收件者的相關資訊（即傳遞記錄）。 因此，您可以取消此工作而不執行任何風險。

按一下之前，請先檢查分析結果和輸出檔案的內容 **[!UICONTROL Confirm delivery]**. 確認訊息可讓您啟動傳送。

傳送確認會從指定的檔案中開始資料擷取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

接著，您可以關閉精靈，並透過檢視傳送記錄檔 **[!UICONTROL Delivery]** 索引標籤，可透過傳送詳細資料存取。

您可以從以下位置設定傳送記錄擷取模式： **[!UICONTROL Analysis]** 傳遞屬性的索引標籤。

有兩種模式：

* **[!UICONTROL Messages are considered sent after validation]** （預設模式）：在此函式模式中，當操作員確認傳送（其狀態從「擱置的傳送」傳遞至「已傳送」）且傳送自動設定為時，會更新所有broadlog **[!UICONTROL Finished]**.
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** ：此模式可讓您透過服務提供者傳送的外部檔案更新broadlog。 在這種情況下，需要使用處理此資訊的工作流程來更新broadlog狀態。

  >[!NOTE]
  >
  >在此情況下，傳遞的狀態也需要變更為 **[!UICONTROL Finished]** 一更新broadlog後立即由使用者執行。
