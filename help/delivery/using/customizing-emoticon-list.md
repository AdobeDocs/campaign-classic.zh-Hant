---
product: campaign
title: 自訂表情符號清單
description: 瞭解如何使用Adobe Campaign自訂表情符號清單
badge-v7: label="v7" type="Informative" tooltip="套用至Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email, Push
role: User, Data Engineer
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 4%

---

# 自訂表情符號清單 {#customize-emoticons}

在快顯視窗中顯示的表情符號清單由列舉來排程，可讓您在清單中顯示值，以限制使用者在指定欄位中的選擇。
表情符號清單順序可以自訂，您也可以將其他表情符號新增到清單中。
表情符號可用於電子郵件和推播，如需更多相關資訊，請參閱此處 [頁面](defining-the-email-content.md#inserting-emoticons).

## 新增表情符號 {#add-new-emoticon}

>[!CAUTION]
>
>表情符號清單不能顯示超過81個專案。

1. 選擇您的新表情符號以從此新增 [頁面](https://unicode.org/emoji/charts/full-emoji-list.html). 請注意，它必須與不同的平台相容，例如瀏覽器和作業系統。

1. 從 **[!UICONTROL Explorer]**，選取 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** 並按一下 **[!UICONTROL Emoticon list]** 現成可用的分項清單。

   >[!NOTE]
   >
   >現成可用的分項清單只能由Adobe Campaign Classic主控台的管理員管理。

   ![](assets/emoticon_1.png)

1. 按一下&#x200B;**[!UICONTROL Add]**。

1. 填寫欄位：

   * **[!UICONTROL U+]**：您新表情符號的程式碼。 您可在此找到表情符號的程式碼清單 [頁面](https://unicode.org/emoji/charts/full-emoji-list.html).
為避免相容性問題，我們建議您選擇支援瀏覽器和每個作業系統的表情符號。

   * **[!UICONTROL Label]**：新表情符號的標籤。

   ![](assets/emoticon_5.png)

1. 按一下 **[!UICONTROL Ok]** 則 **[!UICONTROL Save]** 完成設定時。
您的新表情符號會自動放入商店中。

1. 若要在下列專案中顯示它： **[!UICONTROL Insert emoticon]** 在傳遞的視窗中，按兩下新建立的表情符號，以選取它。

1. 選擇中的 **[!UICONTROL Display order]** 您的新表情符號顯示順序的下拉式清單。 請注意，選取已指派的顯示順序後，現有的表情符號就會自動移至存放區。

   <br>在此範例中，我們選取顯示訂單編號61，這表示如果專案已有此訂單，則會自動移至商店，而我們的新專案會出現在分項清單中。

   ![](assets/emoticon_2.png)

1. 您的新表情符號現已新增至 **[!UICONTROL Insert emoticon list]** 現成可用的分項清單。 您可以變更其 **[!UICONTROL Display order]** 您可以隨時使用，如果不再需要的話，可將它移至市集。

1. 若要將您的變更列入考量，請中斷連線，然後從Adobe Campaign Classic重新連線。 如果您的新表情符號仍未出現在 **[!UICONTROL Insert emoticon]** 快顯視窗，您可能需要清除快取。 如需詳細資訊，請參閱本[區段](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。

1. 您的新表情符號現在可以在以下連結的傳遞中找到： **[!UICONTROL Insert emoticon]** 快顯視窗（位於前述步驟中所設定的第61個位置）。 如需如何在傳遞中使用表情符號的詳細資訊，請參閱本 [頁面](defining-the-email-content.md#inserting-emoticons).

   ![](assets/emoticon_4.png)

1. 如果下清單情符號出現在您的 **[!UICONTROL Insert emoticon]** 快顯視窗，這表示未正確設定這些視窗。 檢查您的 **[!UICONTROL U+]** 程式碼或 **[!UICONTROL Display order]** 是正確的 **[!UICONTROL Emoticon list]**.

   ![](assets/emoticon_6.png)
