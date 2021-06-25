---
product: campaign
title: 如何設定追蹤的連結
description: 如何設定追蹤的連結
audience: delivery
content-type: reference
topic-tags: tracking-messages
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 98bbbb36c9f8156cc34e826a024ff6e6e3f3fee3
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# 如何設定追蹤的連結{#how-to-configure-tracked-links}

對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被啟用。這樣，您可以在目標傳遞操作實施後，追蹤收件者的行為。

追蹤會套用至訊息，但網頁追蹤可讓您監視收件者瀏覽網站的方式（瀏覽的頁面、購買）。 網站追蹤的設定在[本節](../../configuration/using/about-web-tracking.md)中說明。

>[!NOTE]
>
>包含個人化的電子郵件內容中的連結需要追蹤特定語法。 如需如何在可個人化的電子郵件中新增連結以及支援追蹤的詳細資訊，請參閱[此區段](tracking-personalized-links.md)。

強烈建議您在套用追蹤公式前，先在&#x200B;**[!UICONTROL Text content]**&#x200B;標籤的分隔字元中括住URL。 Adobe Campaign會使用此索引標籤中輸入的URL分隔字元來識別字元字串內的URL。 您可以使用下列分隔字元組：
* 括弧()
* 括弧[ ]
* 大括弧{ }

在此範例中，URL https://www.adobe.com後面會加上分號。 收件者電子郵件用戶端可將分號解讀為URL的一部分。 因此，連結可能會損毀。 若要避免此問題，您可以透過下列其中一種方式，將URL括在分隔字元中：
* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};

訊息追蹤預設為啟用。 若要個人化URL的追蹤方式，請遵循下列步驟：

1. 在傳遞精靈的下半部，在訊息內容下方選取&#x200B;**[!UICONTROL Display URLs]**&#x200B;選項。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   當您從追蹤的URL清單中選取URL時，傳送內容中會反白顯示該URL，但鏡像頁面中的連結和預設提供的取消訂閱連結除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 針對訊息的每個URL，選取是否要啟用追蹤。

   >[!IMPORTANT]
   >
   >將連結的URL用作標籤時，建議取消激活跟蹤以避免因網路釣魚而遭拒的風險。
   >
   >例如，如果將www.adobe.com URL插入訊息中並啟動追蹤，則超文字連結的內容將修改為https://nlt.adobe.net/r/?id=xxxxxx。 這表示收件者訊息用戶端可將其視為欺詐性。

1. 如有需要，請變更追蹤標籤，按兩下標籤並輸入新標籤。

   >[!NOTE]
   >
   >追蹤的URL標籤和標籤可以修改，以簡化追蹤傳送時的資訊閱讀。 計算點按計數時，會新增兩個或兩個同名的URL。

1. 如有需要，請變更追蹤模式，在&#x200B;**[!UICONTROL Tracking]**&#x200B;欄中選取符合目標連結的新模式，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   您可以針對每個個別URL，將追蹤模式設為下列其中一個值：

   * **[!UICONTROL Enabled]** :在此URL上啟用追蹤。
   * **[!UICONTROL Not tracked]** :停用對此URL的追蹤。
   * **[!UICONTROL Always enabled]** :一律會啟用此URL的追蹤。系統會儲存此資訊，以便下次（如果URL在未來的訊息內容中再次出現），其追蹤會自動啟動。
   * **[!UICONTROL Never tracked]** :切勿啟用此URL的追蹤。系統會儲存此資訊，以便下次（如果URL在未來的訊息中再次出現），其追蹤會自動停用。
   * **[!UICONTROL Opt-out]** :將此URL視為選擇退出或取消訂閱URL。
   * **[!UICONTROL Mirror page]** :將此URL視為鏡像頁面URL。

1. 此外，您還可以在&#x200B;**[!UICONTROL Category]**&#x200B;欄的下拉式清單中，為每個追蹤的URL選取類別。 這些類別可以顯示報告，例如&#x200B;**[!UICONTROL URLs and click streams]**&#x200B;中（請參閱[此部分](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)）。 在特定枚舉中定義類別：**[!UICONTROL urlCategory]**（請參閱[管理枚舉](../../platform/using/managing-enumerations.md)）。
