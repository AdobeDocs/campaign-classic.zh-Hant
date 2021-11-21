---
product: campaign
title: 自訂表情符號清單
description: 了解使用Adobe Campaign Classic時如何自訂表情符號清單。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# 自訂表情符號清單 {#customize-emoticons}

![](../../assets/common.svg)

彈出式視窗中顯示的表情符號清單由列舉排定，可讓您在清單中顯示值，以限制使用者對指定欄位的選擇。
您可以自訂表情符號清單順序，也可以將其他表情符號新增至清單。
表情符號可用於電子郵件，並可依照以下項目推送更多資訊： [頁面](defining-the-email-content.md#inserting-emoticons).

## 新增表情符號 {#add-new-emoticon}

>[!CAUTION]
>
>表情符號清單不能顯示超過81個項目。

1. 從中選擇要添加的新表情符號 [頁面](https://unicode.org/emoji/charts/full-emoji-list.html). 請注意，它必須與不同的平台（例如瀏覽器和作業系統）相容。

1. 從 **[!UICONTROL Explorer]**，選取 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** 並按一下 **[!UICONTROL Emoticon list]** 現成可用的列舉。

   >[!NOTE]
   >
   >您的Adobe Campaign Classic主控台管理員只能管理現成可用的列舉。

   ![](assets/emoticon_1.png)

1. 按一下&#x200B;**[!UICONTROL Add]**。

1. 填寫欄位：

   * **[!UICONTROL U+]**:新表情符號的代碼。 您可以在此找到表情符號代碼清單 [頁面](https://unicode.org/emoji/charts/full-emoji-list.html).
為避免相容性問題，我們建議您選擇瀏覽器和每個作業系統都支援的表情符號。

   * **[!UICONTROL Label]**:新表情符號的標籤。

   ![](assets/emoticon_5.png)

1. 按一下 **[!UICONTROL Ok]** then **[!UICONTROL Save]** 完成設定時。
新的表情符號會自動放入商店。

1. 若要在 **[!UICONTROL Insert emoticon]** 在傳遞視窗中，按兩下新建立的表情符號以加以選取。

1. 在 **[!UICONTROL Display order]** 下拉式清單中顯示新表情符號的順序。 請注意，選取已指派的顯示順序後，現有表情符號會自動移至商店。

   <br>在此示例中，我們選擇了顯示訂單編號61，這意味著如果某個條目已經具有此訂單，則它將自動移到商店，而我們的新條目將在枚舉清單中取代。

   ![](assets/emoticon_2.png)

1. 您的新表情符號已新增至 **[!UICONTROL Insert emoticon list]** 現成可用的列舉。 您可以變更 **[!UICONTROL Display order]** 如果您不再需要，可隨時將其移至商店。

1. 若要將您的變更納入考量，請中斷連線，然後重新連線至Adobe Campaign Classic。 如果您的新表情符號仍未出現在 **[!UICONTROL Insert emoticon]** 快取時，您可能需要清除快取。 如需詳細資訊，請參閱本[區段](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。

1. 您現在可在 **[!UICONTROL Insert emoticon]** 在第61位的快顯視窗中，如先前步驟所設定。 如需如何在傳送中使用表情符號的詳細資訊，請參閱 [頁面](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. 如果您的 **[!UICONTROL Insert emoticon]** 快顯視窗，這表示未正確設定。 檢查 **[!UICONTROL U+]** 代碼或 **[!UICONTROL Display order]** 在 **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
