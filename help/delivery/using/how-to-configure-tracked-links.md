---
title: 如何設定追蹤的連結
seo-title: 如何設定追蹤的連結
description: 如何設定追蹤的連結
seo-description: null
page-status-flag: never-activated
uuid: 0fb41a43-8a84-4a61-bf93-97e1d448a5ec
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: tracking-messages
discoiquuid: 9cae3861-88eb-447a-aa23-9d1de0710eec
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 3522f4f50770dde220610cd5f1c4084292d8f1f5
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 8%

---


# 如何設定追蹤的連結{#how-to-configure-tracked-links}

對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被點擊。這樣，您可以在目標傳遞行動實施後，追蹤收件者的行為。

>[!NOTE]
>
>追蹤會套用至訊息，但網路追蹤可讓您監控收件者瀏覽網站（瀏覽的頁面、購買）的方式。
>
>本節將介紹Web跟蹤的 [配置](../../configuration/using/about-web-tracking.md)。

預設會啟用訊息追蹤。 若要個人化URL的追蹤方式，請遵循下列步驟：

1. 在傳送 **[!UICONTROL Display URLs]** 精靈下方的訊息內容下方選取選項。

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

1. 如有需要，請變更追蹤模式，在符合目標連結的欄 **[!UICONTROL Tracking]** 中選取新模式，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   對於每個個別URL，您可以將追蹤模式設定為下列其中一個值：

   * **[!UICONTROL Enabled]** : 在此URL上啟動追蹤。
   * **[!UICONTROL Not tracked]** : 停用此URL上的追蹤。
   * **[!UICONTROL Always enabled]** : 一律啟動此URL的追蹤。 此資訊會儲存，如此，如果下次URL再次出現在未來的訊息內容中，其追蹤就會自動啟動。
   * **[!UICONTROL Never tracked]** : 切勿啟動此URL的追蹤。 此資訊會儲存，如此，如果下次URL再次出現在未來的訊息中，其追蹤就會自動停用。
   * **[!UICONTROL Opt-out]** : 將此URL視為選擇退出或取消訂閱URL。
   * **[!UICONTROL Mirror page]** : 認為此URL是鏡像頁面URL。

1. 此外，您也可以在欄的下拉式清單中，為每個追蹤的URL選取類 **[!UICONTROL Category]** 別。 這些類別可顯示報表，例如 **[!UICONTROL URLs and click streams]** (請 [參閱本節](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams))。 類別在特定枚舉中定義： **[!UICONTROL urlCategory]** (請參 [閱管理枚舉](../../platform/using/managing-enumerations.md))。
