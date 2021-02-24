---
solution: Campaign Classic
product: campaign
title: 如何配置追蹤的連結
description: 如何配置追蹤的連結
audience: delivery
content-type: reference
topic-tags: tracking-messages
translation-type: tm+mt
source-git-commit: 5e6a30cd70c6eb21398fda4ac0572fcefa780e0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 11%

---


# 如何配置追蹤的連結{#how-to-configure-tracked-links}

對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被啟用。這樣，您可以在目標傳遞操作實施後，追蹤收件者的行為。

追蹤會套用至訊息，但網路追蹤可讓您監控收件者瀏覽網站（瀏覽的頁面、購買）的方式。 網頁追蹤的設定顯示在[本節](../../configuration/using/about-web-tracking.md)中。

>[!NOTE]
>
>包含個人化的電子郵件內容中的連結需要追蹤特定的語法。 有關如何在電子郵件中新增可個人化且支援追蹤的連結，請參閱[本節](../../delivery/using/tracking-personalized-links.md)。




預設會啟用訊息追蹤。 若要個人化URL的追蹤方式，請遵循下列步驟：

1. 在傳送精靈下方的訊息內容下方，選取&#x200B;**[!UICONTROL Display URLs]**&#x200B;選項。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   當您從追蹤的URL清單中選取URL時，傳送內容會反白顯示該URL，但鏡像頁面中的連結和未訂閱的連結除外，預設會提供這些連結。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 針對訊息的每個URL，選取是否啟用追蹤。

   >[!IMPORTANT]
   >
   >當連結的URL被用作標籤時，建議停用追蹤以避免因網路釣魚而遭拒的風險。
   >
   >例如，如果將www.adobe.com URL插入訊息並啟動追蹤，超文字連結的內容會修改為https://nlt.adobe.net/r/?id=xxxxxx。 這表示收件者訊息用戶端可將其視為欺詐。

1. 如有需要，請變更追蹤標籤，按兩下標籤並輸入新標籤。

   >[!NOTE]
   >
   >追蹤的URL標籤和標籤可加以修改，以簡化追蹤傳送時的資訊讀取作業。 計算點按計數時，會新增兩個或兩個同名的URL。

1. 如有需要，請變更追蹤模式，在&#x200B;**[!UICONTROL Tracking]**&#x200B;欄中選取符合目標連結的新模式，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   對於每個個別URL，您可以將追蹤模式設定為下列其中一個值：

   * **[!UICONTROL Enabled]** :在此URL上啟動追蹤。
   * **[!UICONTROL Not tracked]** :停用此URL上的追蹤。
   * **[!UICONTROL Always enabled]** :一律啟動此URL的追蹤。此資訊會儲存，如此，如果下次URL再次出現在未來的訊息內容中，其追蹤就會自動啟動。
   * **[!UICONTROL Never tracked]** :切勿啟動此URL的追蹤。此資訊會儲存，如此，如果下次URL再次出現在未來的訊息中，其追蹤就會自動停用。
   * **[!UICONTROL Opt-out]** :將此URL視為選擇退出或取消訂閱URL。
   * **[!UICONTROL Mirror page]** :認為此URL是鏡像頁面URL。

1. 此外，您也可以在&#x200B;**[!UICONTROL Category]**&#x200B;欄的下拉式清單中，為每個追蹤的URL選取類別。 這些類別可顯示報告，例如&#x200B;**[!UICONTROL URLs and click streams]**（請參閱[本節](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams)）。 類別在特定枚舉中定義：**[!UICONTROL urlCategory]**（請參閱[管理枚舉](../../platform/using/managing-enumerations.md)）。
