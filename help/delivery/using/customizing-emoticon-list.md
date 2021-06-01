---
product: campaign
title: 自訂表情符號清單
description: 了解使用Adobe Campaign Classic時如何自訂表情符號清單。
audience: delivery
content-type: reference
topic-tags: sending-emails
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# 自訂表情符號清單 {#customize-emoticons}

彈出式視窗中顯示的表情符號清單由列舉排定，可讓您在清單中顯示值，以限制使用者對指定欄位的選擇。
您可以自訂表情符號清單順序，也可以將其他表情符號新增至清單。
表情符號可用於電子郵件，並可依此參閱此[page](../../delivery/using/defining-the-email-content.md#inserting-emoticons)以取得更多資訊。

## 新增表情符號{#add-new-emoticon}

>[!CAUTION]
>
>表情符號清單不能顯示超過81個項目。

1. 從此[page](https://unicode.org/emoji/charts/full-emoji-list.html)選擇要添加的新表情符號。 請注意，它必須與不同的平台（例如瀏覽器和作業系統）相容。

1. 從&#x200B;**[!UICONTROL Explorer]**&#x200B;中，選擇&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** ，然後按一下&#x200B;**[!UICONTROL Emoticon list]**&#x200B;現成可用的枚舉。

   >[!NOTE]
   >
   >您的Adobe Campaign Classic主控台管理員只能管理現成可用的列舉。

   ![](assets/emoticon_1.png)

1. 按一下 **[!UICONTROL Add]**。

1. 填寫欄位：

   * **[!UICONTROL U+]**:新表情符號的代碼。您可以在此[page](https://unicode.org/emoji/charts/full-emoji-list.html)中找到表情符號代碼清單。
為避免相容性問題，我們建議您選擇瀏覽器和每個作業系統均支援的表情符號。

   * **[!UICONTROL Label]**:新表情符號的標籤。

   ![](assets/emoticon_5.png)

1. 完成配置時，按一下&#x200B;**[!UICONTROL Ok]**，然後按一下&#x200B;**[!UICONTROL Save]**。
新的表情符號會自動放入商店。

1. 若要在傳送的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;視窗中顯示，請連按兩下新建立的表情符號，以選取它。

1. 在&#x200B;**[!UICONTROL Display order]**&#x200B;下拉式清單中選擇，新表情符號的顯示順序。 請注意，選取已指派的顯示順序後，現有表情符號會自動移至商店。

   <br>在此示例中，我們選擇了顯示訂單編號61，這意味著如果某個條目已經具有此訂單，則它將自動移到商店，而我們的新條目將在枚舉清單中取代。

   ![](assets/emoticon_2.png)

1. 您的新表情符號現已新增至&#x200B;**[!UICONTROL Insert emoticon list]**&#x200B;現成可用的列舉。 您可以隨時變更其&#x200B;**[!UICONTROL Display order]**，或在不需要的情況下將其移至商店。

1. 若要將您的變更納入考量，請中斷連線，然後重新連線至Adobe Campaign Classic。 如果新表情符號仍未出現在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中，則可能需要清除快取。 如需詳細資訊，請參閱本[區段](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。

1. 您現在可以在傳送中，依照先前步驟的設定，於第61位置的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗找到您的新表情符號。 如需如何在傳送中使用表情符號的詳細資訊，請參閱此[page](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果您的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中出現下清單情符號，表示它們未正確設定。 檢查&#x200B;**[!UICONTROL U+]**&#x200B;代碼或&#x200B;**[!UICONTROL Display order]**&#x200B;在&#x200B;**[!UICONTROL Emoticon list]**&#x200B;中是否正確。

   ![](assets/emoticon_6.png)
