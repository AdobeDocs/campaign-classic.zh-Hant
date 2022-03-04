---
product: campaign
title: 自訂表情符號清單
description: 瞭解如何在使用Adobe Campaign Classic時自定義表情清單
feature: Email, Push
exl-id: b8642df3-1960-4f2c-8273-c3988a3e85f0
source-git-commit: 9839dbacda475c2a586811e3c4f686b1b1baab05
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 3%

---

# 自訂表情符號清單 {#customize-emoticons}

![](../../assets/common.svg)

彈出窗口中顯示的表情清單由枚舉所規定，該枚舉允許您在清單中顯示值以限制用戶對給定欄位的選擇。
可以自定義表情符清單順序，也可以將其他表情符添加到清單。
有關此方面的詳細資訊，請參閱此 [頁](defining-the-email-content.md#inserting-emoticons)。

## 添加新表情 {#add-new-emoticon}

>[!CAUTION]
>
>表情清單不能顯示81個以上的條目。

1. 選擇要從此添加的新表情 [頁](https://unicode.org/emoji/charts/full-emoji-list.html)。 請注意，它必須與瀏覽器和作業系統等不同的平台相容。

1. 從 **[!UICONTROL Explorer]**&#x200B;選中 **[!UICONTROL Administration]** > **[!UICONTROL Platform]** > **[!UICONTROL Enumerations]** 並按一下 **[!UICONTROL Emoticon list]** 現成枚舉。

   >[!NOTE]
   >
   >現成枚舉只能由Adobe Campaign Classic控制台的管理員管理。

   ![](assets/emoticon_1.png)

1. 按一下&#x200B;**[!UICONTROL Add]**。

1. 填寫欄位：

   * **[!UICONTROL U+]**:新表情代碼。 您可以在此中查找表情符號代碼清單 [頁](https://unicode.org/emoji/charts/full-emoji-list.html)。
為避免相容性問題，我們建議您選擇瀏覽器和每個作業系統都支援的表情符號。

   * **[!UICONTROL Label]**:新表情符的標籤。

   ![](assets/emoticon_5.png)

1. 按一下 **[!UICONTROL Ok]** 然後 **[!UICONTROL Save]** 完成配置。
你的新表情符號將自動放在商店中。

1. 在 **[!UICONTROL Insert emoticon]** 的子菜單。

1. 在 **[!UICONTROL Display order]** 下拉框，其中將顯示新的表情。 請注意，通過選擇已分配的顯示順序，現有表情將自動移動到商店。

   <br>在本示例中，我們選擇了顯示訂單號61，這意味著如果某個條目已經擁有此訂單，則它將自動移動到商店，而我們的新條目將在枚舉清單中取而代之。

   ![](assets/emoticon_2.png)

1. 您的新表情已添加到 **[!UICONTROL Insert emoticon list]** 現成枚舉。 可以更改 **[!UICONTROL Display order]** 如果你不再需要，可以隨時將它移到商店。

1. 要考慮您所做的更改，請斷開連接，然後重新連接Adobe Campaign Classic。 如果新的表情符號仍未出現在 **[!UICONTROL Insert emoticon]** 彈出窗口，您可能需要清除快取。 如需詳細資訊，請參閱本[區段](../../platform/using/faq-campaign-config.md#perform-soft-cache-clear)。

1. 您的新表情符現在可以在 **[!UICONTROL Insert emoticon]** 按前面步驟配置的第61位的彈出窗口。 有關如何在交貨中使用表情符號的詳細資訊，請參閱此 [頁](defining-the-email-content.md#inserting-emoticons)。

   ![](assets/emoticon_4.png)

1. 如果您的 **[!UICONTROL Insert emoticon]** 彈出窗口，這意味著它們未正確配置。 檢查 **[!UICONTROL U+]** 代碼 **[!UICONTROL Display order]** 在 **[!UICONTROL Emoticon list]**。

   ![](assets/emoticon_6.png)
