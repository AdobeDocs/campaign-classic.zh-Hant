---
product: campaign
title: 驗證
description: 驗證
feature: Direct Mail
exl-id: 42bb395b-b3fe-4d48-8720-5a4cae191984
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '241'
ht-degree: 1%

---

# 驗證{#validating}

![](../../assets/common.svg)

驗證交付時的全局概念在中顯示 [此部分](steps-validating-the-delivery.md)。

在遞送分析期間生成直接郵件遞送的輸出檔案。 檔案的內容取決於所選輸出列(請參閱 [提取檔案](defining-the-direct-mail-content.md#extraction-file))。

>[!NOTE]
>
>分析階段詳見 [分析交貨](steps-validating-the-delivery.md#analyzing-the-delivery)。

在分析階段，生成檔案，但不更新有關接收者（即傳遞日誌）的資訊。 因此，您可以取消此作業，而不會帶來任何風險。

按一下前檢查分析結果和輸出檔案的內容 **[!UICONTROL Confirm delivery]**。 通過確認消息，您可以啟動傳遞。

發送確認將啟動指定檔案中的資料提取。

![](assets/s_ncs_user_postal_del_send_confirm_postal.png)

然後，您可以關閉嚮導，並通過 **[!UICONTROL Delivery]** 頁籤，可通過交貨詳細資訊訪問。

您可以從 **[!UICONTROL Analysis]** 的子菜單。

有兩種模式：

* **[!UICONTROL Messages are considered sent after validation]** （預設模式）:在此功能模式下，當操作員確認發送（其狀態從「待定傳遞」傳遞到「已發送」），並且傳遞自動設定為 **[!UICONTROL Finished]**。
* **[!UICONTROL A file of results determines the messages that are sent and those that have failed]** :此模式允許您通過服務提供商發送的外部檔案更新廣播。 在這種情況下，需要使用處理此資訊的工作流來更新廣播狀態。

   >[!NOTE]
   >
   >在這種情況下，交貨的狀態還需要更改為 **[!UICONTROL Finished]** 廣播更新後立即由用戶進行。
