---
title: 自訂表情符號清單
description: 瞭解如何使用Adobe Campaign Classic自訂表情符號清單。
page-status-flag: never-activated
uuid: ddcc2e3b-e251-4a7a-a22a-28701522839f
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-emails
discoiquuid: 2ea2747f-957f-41a9-a03f-20c03fa99116
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3beb62d0264cfcb03486c291ce79cc7ff582e9c7
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# 自訂表情符號清單 {#customize-emoticons}

彈出式選單中顯示的表情符號清單會由列舉來規定，可讓您在清單中顯示值，以限制使用者對指定欄位的選擇。
您可自訂表情符號清單順序，也可以將其他表情符號新增至清單。
此頁面提供電子郵件表情和推播，以取得更多相關資 [訊](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

## 新增表情符號 {#add-new-emoticon}

>[!CAUTION]
>
>表情符號清單無法顯示超過81個項目。

1. 選擇要從此頁面新增的新表 [情符號](https://unicode.org/emoji/charts/full-emoji-list.html)。 請注意，它必須與瀏覽器和作業系統等不同平台相容。

1. 從中 **[!UICONTROL Explorer]**&#x200B;選擇 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** ，然後按一下現成 **[!UICONTROL Emoticon list]** 的枚舉。

   >[!NOTE]
   >
   >現成可用的列舉只能由Adobe Campaign Classic主控台的管理員管理。

   ![](assets/emoticon_1.png)

1. 按一下「**[!UICONTROL Add]**」。

1. 填寫欄位：

   * **[!UICONTROL U+]**: 新表情符號的程式碼。 您可在此頁面中找到表情符號的清 [單](https://unicode.org/emoji/charts/full-emoji-list.html)。
為避免相容性問題，我們建議您選擇瀏覽器和每個作業系統都支援的表情。

   * **[!UICONTROL Label]**: 新表情符號。
   ![](assets/emoticon_5.png)

1. 完成 **[!UICONTROL Ok]** 配 **[!UICONTROL Save]** 置後，按一下。
您的新表情符號會自動放在商店中。

1. 若要在傳送的視 **[!UICONTROL Insert emoticon]** 窗中顯示它，請連按兩下新建立的表情符號，以選取它。

1. 在下拉式 **[!UICONTROL Display order]** 清單中選擇顯示新表情符號的順序。 請注意，選取已指派的顯示順序後，現有表情符號會自動移至商店。

   <br>在此範例中，我們選擇了顯示順序編號61，這表示如果某個項目已經有此順序，它將自動移至商店，而我們的新項目將取代它在列舉清單中。

   ![](assets/emoticon_2.png)

1. 您的新表情符號現在已新 **[!UICONTROL Insert emoticon list]** 增至現成可用的列舉。 您可隨時變 **[!UICONTROL Display order]** 更它，或將它移至商店（如果您不需要）。

1. 若要考量您的變更，請中斷連線，然後重新連線至Adobe Campaign Classic。 如果您的新表情符號仍未顯示在快顯 **[!UICONTROL Insert emoticon]** 視窗中，您可能需要清除快取。 For more on this, refer to this [section](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear).

1. 您的新表情符號現在可在您的遞送中，如先前 **[!UICONTROL Insert emoticon]** 步驟所設定，位於第61位的快顯視窗中。 如需如何在傳送中使用表情符號的詳細資訊，請參閱本 [頁](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果您的快顯視窗中出 **[!UICONTROL Insert emoticon]** 現下清單情符號，表示它們未正確設定。 檢查您的 **[!UICONTROL U+]** 代碼 **[!UICONTROL Display order]** 或中的正確 **[!UICONTROL Emoticon list]**。

   ![](assets/emoticon_6.png)
