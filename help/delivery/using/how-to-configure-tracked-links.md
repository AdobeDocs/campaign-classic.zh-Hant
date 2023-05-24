---
product: campaign
title: 如何設定追蹤的連結
description: 如何設定追蹤的連結
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Monitoring
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# 如何設定追蹤的連結{#how-to-configure-tracked-links}



對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被啟用。這樣，您可以在目標傳遞操作實施後，追蹤收件者的行為。

追蹤適用於訊息，但網路追蹤可讓您監視收件者瀏覽網站的方式（瀏覽的頁面、購買）。 網站追蹤的設定在[本節](../../configuration/using/about-web-tracking.md)中說明。

>[!NOTE]
>
>包含個人化的電子郵件內容中的連結需要追蹤特定語法。 如需如何在電子郵件中新增可個人化且支援追蹤的連結的詳細資訊，請參閱 [本節](tracking-personalized-links.md).

我們強烈建議您將URL以分隔字元括在 **[!UICONTROL Text content]** 標籤中，然後再套用追蹤公式。 Adobe Campaign會使用您在此索引標籤中輸入的URL分隔符號，來識別字元字串內的URL。 您可以使用下列分隔符號組：
* 括弧( )
* 括弧 [ ]
* 大括弧{ }

在此範例中，URL https://www.adobe.com後面接著分號。 收件者電子郵件使用者端可能會將分號解譯為URL的一部分。 因此，連結可能會中斷。 若要避免此問題，您可以透過下列其中一種方式，以分隔符號括住URL：
* (https://www.adobe.com)；
* [https://www.adobe.com]；
* {https://www.adobe.com}；

訊息追蹤預設為啟用。 若要個人化追蹤URL的方式，請遵循下列步驟：

1. 選取 **[!UICONTROL Display URLs]** 選項位於傳送精靈下方的訊息內容下。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   當您從追蹤的URL清單中選取URL時，傳遞內容會醒目提示該URL — 映象頁面中的連結和預設提供的取消訂閱連結除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 針對訊息的每個URL，選取是否要啟用追蹤。

   >[!IMPORTANT]
   >
   >當連結的URL用作標籤時，建議停用追蹤，以避免因網路釣魚而被拒絕的風險。
   >
   >例如，如果將www.adobe.com URL插入訊息中並啟動追蹤，則超文字連結的內容將會修改為https://nlt.adobe.net/r/?id=xxxxxx。 這表示收件者訊息使用者端可能會將其視為詐騙郵件。

1. 如有需要，請變更追蹤標籤，連按兩下標籤並輸入新標籤。

   >[!NOTE]
   >
   >可修改追蹤的URL和標籤的標籤，以簡化追蹤傳遞時資訊的閱讀。 計算點選計數時，會將兩個具有相同名稱的URL或兩個標籤新增在一起。

1. 如有需要，請變更追蹤模式，然後在 **[!UICONTROL Tracking]** 符合目標連結的欄，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   對於每個個別URL，您可以將追蹤模式設定為下列其中一個值：

   * **[!UICONTROL Enabled]** ：啟用此URL上的追蹤。
   * **[!UICONTROL Not tracked]** ：停用此URL上的追蹤。
   * **[!UICONTROL Always enabled]** ：一律會啟用此URL的追蹤。 此資訊會儲存起來，以便下次如果URL再次出現在未來的訊息內容中，其追蹤會自動啟動。
   * **[!UICONTROL Never tracked]** ：絕對不要啟用此URL的追蹤。 系統會儲存此資訊，以便下次當該URL再次出現在未來的訊息中時，其追蹤會自動停用。
   * **[!UICONTROL Opt-out]** ：將此URL視為選擇退出或取消訂閱URL。
   * **[!UICONTROL Mirror page]** ：將此URL視為映象頁面URL。

1. 此外，您還可以在的下拉式清單中，為每個追蹤的URL選取類別 **[!UICONTROL Category]** 欄。 這些類別可顯示報表，例如 **[!UICONTROL URLs and click streams]** (請參閱 [本節](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams))。 類別是在特定分項清單中定義的： **[!UICONTROL urlCategory]** (請參閱 [管理分項清單](../../platform/using/managing-enumerations.md))。
