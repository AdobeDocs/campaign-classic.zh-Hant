---
product: campaign
title: 自訂表情符號清單
description: 瞭解如何使用Adobe Campaign自訂表情符號清單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Email, Push
role: User, Data Engineer
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 287d1bf60b39e9e2b389701097995dbea962dec9
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 3%

---

# 自訂表情符號清單 {#customize-emoticons}

在快顯視窗中顯示的表情符號清單由列舉來排程，可讓您在清單中顯示值，以限制使用者在指定欄位中的選擇。
表情符號清單順序可以自訂，您也可以將其他表情符號新增到清單中。

請注意，表情符號僅可用於電子郵件和推播。 如需詳細資訊，請參閱此[頁面](defining-the-email-content.md#inserting-emoticons)。

## 新增表情符號 {#add-new-emoticon}

>[!CAUTION]
>
>表情符號清單不能顯示超過81個專案。

1. 從此[頁面](https://unicode.org/emoji/charts/full-emoji-list.html)選擇您的新表情符號。 請注意，它必須與不同的平台相容，例如瀏覽器和作業系統。

1. 從&#x200B;**[!UICONTROL Explorer]**&#x200B;中，選取&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]**，然後按一下&#x200B;**[!UICONTROL Emoticon list]**&#x200B;現成的列舉。

   >[!NOTE]
   >
   >現成可用的分項清單只能由Adobe Campaign Classic主控台的管理員管理。

   ![](assets/emoticon_1.png)

1. 按一下&#x200B;**[!UICONTROL Add]**。

1. 填寫欄位：

   * **[!UICONTROL U+]**：您新表情符號的代碼。 您可以在此[頁面](https://unicode.org/emoji/charts/full-emoji-list.html)中找到表情符號的程式碼清單。
為避免相容性問題，我們建議您選擇支援瀏覽器和每個作業系統的表情符號。

   * **[!UICONTROL Label]**：您新表情符號的標籤。

   ![](assets/emoticon_5.png)

1. 完成設定時，按一下&#x200B;**[!UICONTROL Ok]**，然後再按&#x200B;**[!UICONTROL Save]**。
您的新表情符號會自動放入商店中。

1. 若要在傳遞的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;視窗中顯示表情符號，請連按兩下以選取新建立的表情符號。

1. 在&#x200B;**[!UICONTROL Display order]**&#x200B;下拉式清單中選擇新表情符號的顯示順序。 請注意，選取已指派的顯示順序後，現有的表情符號就會自動移至存放區。

   <br>在此範例中，我們選擇顯示訂單編號61，這表示如果專案已有此訂單，則會自動移至商店，而我們的新專案會出現在分項清單中。

   ![](assets/emoticon_2.png)

1. 您的新表情符號現已新增至&#x200B;**[!UICONTROL Insert emoticon list]**&#x200B;現成的分項清單。 您可以隨時變更其&#x200B;**[!UICONTROL Display order]**，或將其移至市集（如果不再需要的話）。

1. 若要將您的變更列入考量，請中斷連線，然後從Adobe Campaign Classic重新連線。 如果您的新表情符號仍未出現在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中，您可能需要清除您的快取。 如需詳細資訊，請參閱本[區段](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。

1. 您的新表情符號現在可在傳送中找到了，位置位於先前步驟中設定的第61個位置的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中。 如需如何在傳遞中使用表情符號的詳細資訊，請參閱此[頁面](defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中出現下清單情符號，表示未正確設定。 檢查您的&#x200B;**[!UICONTROL U+]**&#x200B;程式碼或&#x200B;**[!UICONTROL Display order]**&#x200B;在&#x200B;**[!UICONTROL Emoticon list]**&#x200B;中是否正確。

   ![](assets/emoticon_6.png)
