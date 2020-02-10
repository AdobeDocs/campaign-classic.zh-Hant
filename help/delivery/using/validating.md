---
title: 驗證
seo-title: 驗證
description: 驗證
seo-description: null
page-status-flag: never-activated
uuid: e3cd96ef-4f5d-4e17-9fec-5eaa4d835cb1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-direct-mail
discoiquuid: c363a7cf-81a5-4c02-a021-b822eeeadd03
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 70f51ba3937d0f20d9a488c61b52b7ec4396fa5e

---


# 驗證{#validating}

驗證傳送時的全域概念會呈現在本 [節中](../../delivery/using/steps-validating-the-delivery.md)。

在遞送分析期間生成直接郵件遞送的輸出檔案。 檔案的內容取決於所選的輸出列(請參 [閱抽取檔案](../../delivery/using/defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>分析階段在分析交 [付中詳述](../../delivery/using/steps-validating-the-delivery.md#analyzing-the-delivery)。

在分析階段期間，會產生檔案，但不會更新與收件者（即傳送記錄）相關的資訊。 因此，您可以取消此作業，而不會有任何風險。

在按一下前檢查分析結果和輸出檔案的內容 **[!UICONTROL Confirm delivery]**。 確認訊息可讓您啟動傳送。

傳送確認會啟動指定檔案中的資料擷取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然後，您可以關閉精靈並透過標籤檢視傳送記錄檔，而標籤 **[!UICONTROL Delivery]** 可透過傳送詳細資訊存取。

您可以從傳送屬性的標籤中設定 **[!UICONTROL Analysis]** 傳送記錄檔擷取模式。

有兩種模式：

* **[!UICONTROL Messages are considered sent after validation]** （預設模式）:在此函式模式中，當運算子確認傳送（其狀態從「待定傳送」傳遞至「已傳送」），且傳送自動設為時，會更新所有廣告 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式允許您通過服務提供商發送的外部檔案更新廣播。 在這種情況下，需要使用處理此資訊的工作流來更新廣播狀態。

   >[!NOTE]
   >
   >在此情況下，傳送狀態也需要在廣播更新後 **[!UICONTROL Finished]** 由使用者立即變更為。
