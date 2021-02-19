---
solution: Campaign Classic
product: campaign
title: 自訂表情符號清單
description: 瞭解如何使用Adobe Campaign Classic自訂表情符號清單。
audience: delivery
content-type: reference
topic-tags: sending-emails
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---


# 自訂表情符號清單 {#customize-emoticons}

彈出式選單中顯示的表情符號清單會由列舉來規定，可讓您在清單中顯示值，以限制使用者對指定欄位的選擇。
您可自訂表情符號清單順序，也可以將其他表情符號新增至清單。
電子郵件中提供表情符號，如需詳細資訊，請參閱此[頁面](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

## 新增{#add-new-emoticon}表情符號

>[!CAUTION]
>
>表情符號清單無法顯示超過81個項目。

1. 從此[頁面](https://unicode.org/emoji/charts/full-emoji-list.html)選擇要新增的表情符號。 請注意，它必須與瀏覽器和作業系統等不同平台相容。

1. 從&#x200B;**[!UICONTROL Explorer]**&#x200B;中，選擇&#x200B;**[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** ，然後按一下&#x200B;**[!UICONTROL Emoticon list]**&#x200B;現成枚舉。

   >[!NOTE]
   >
   >現成可用的列舉只能由Adobe Campaign Classic主控台的管理員管理。

   ![](assets/emoticon_1.png)

1. 按一下 **[!UICONTROL Add]**。

1. 填寫欄位：

   * **[!UICONTROL U+]**:新表情符號的程式碼。您可在此[頁面](https://unicode.org/emoji/charts/full-emoji-list.html)中找到表情符號清單。
為避免相容性問題，我們建議您選擇瀏覽器和每個作業系統都支援的表情。

   * **[!UICONTROL Label]**:新表情符號。

   ![](assets/emoticon_5.png)

1. 完成配置後，按一下&#x200B;**[!UICONTROL Ok]** ，然後按一下&#x200B;**[!UICONTROL Save]**。
您的新表情符號會自動放在商店中。

1. 若要在傳送的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;視窗中顯示它，請連按兩下您新建立的表情符號。

1. 在&#x200B;**[!UICONTROL Display order]**&#x200B;下拉式清單中選擇新表情符號的顯示順序。 請注意，選取已指派的顯示順序後，現有表情符號會自動移至商店。

   <br>在此範例中，我們選擇了顯示順序編號61，這表示如果某個項目已經有此順序，它將自動移至商店，而我們的新項目將取代它在列舉清單中。

   ![](assets/emoticon_2.png)

1. 您的新表情符號現在已新增至&#x200B;**[!UICONTROL Insert emoticon list]**&#x200B;現成可用的列舉。 您可以隨時變更其&#x200B;**[!UICONTROL Display order]**，或在您不需要時將其移至商店。

1. 若要考量您的變更，請中斷連線，然後重新連線至Adobe Campaign Classic。 如果您的新表情符號仍未出現在&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中，您可能需要清除快取。 如需詳細資訊，請參閱本[區段](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。

1. 如前述步驟所設定，新的表情符號現在可在61位置的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中，於您的傳送中找到。 如需如何在傳送中使用表情符號的詳細資訊，請參閱此[頁面](../../delivery/using/defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果您的&#x200B;**[!UICONTROL Insert emoticon]**&#x200B;快顯視窗中出現下清單情符號，表示它們未正確設定。 檢查&#x200B;**[!UICONTROL U+]**&#x200B;代碼或&#x200B;**[!UICONTROL Display order]**&#x200B;在&#x200B;**[!UICONTROL Emoticon list]**&#x200B;中是否正確。

   ![](assets/emoticon_6.png)
