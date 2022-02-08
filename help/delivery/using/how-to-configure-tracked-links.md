---
product: campaign
title: 如何設定追蹤的連結
description: 如何設定追蹤的連結
exl-id: ed88e1d6-c0d5-4a85-9f3e-be670f4bcc10
source-git-commit: 56459b188ee966cdb578c415fcdfa485dcbed355
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 10%

---

# 如何設定追蹤的連結{#how-to-configure-tracked-links}

![](../../assets/common.svg)

對於每次傳遞，您都可以追蹤訊息是否收到，以及郵件內容中的連結是否被啟用。這樣，您可以在目標傳遞操作實施後，追蹤收件者的行為。

跟蹤適用於郵件，但Web跟蹤允許您監視收件人瀏覽網站的方式（訪問的頁面、購買）。 網站追蹤的設定在[本節](../../configuration/using/about-web-tracking.md)中說明。

>[!NOTE]
>
>電子郵件內容中包含個性化的連結需要跟蹤特定語法。 有關如何在電子郵件中添加可個性化且支援跟蹤的連結的詳細資訊，請參閱 [此部分](tracking-personalized-links.md)。

強烈建議您將URL括在 **[!UICONTROL Text content]** 頁籤。 您在此頁籤中輸入的URL分隔符由Adobe Campaign用於標識字串中的URL。 可以使用以下分隔符對：
* 括弧()
* 括弧 [ ]
* 大括弧{ }

在本示例中，URL https://www.adobe.com後跟分號。 收件人電子郵件客戶端可將分號解釋為URL的一部分。 因此，連結可能被斷開。 為避免此問題，可以使用以下方法之一將URL括在分隔符中：
* (https://www.adobe.com);
* [https://www.adobe.com];
* {https://www.adobe.com};

預設情況下啟用消息跟蹤。 要個性化跟蹤URL的方式，請執行以下步驟：

1. 選擇 **[!UICONTROL Display URLs]** 的子菜單。

   ![](assets/s_ncs_user_email_del_display_urls.png)

   從跟蹤的URL清單中選擇URL時，它會在傳遞內容中突出顯示 — 預設情況下提供的鏡像頁中的連結和取消訂閱連結除外。

   ![](assets/s_ncs_user_email_del_show_urls.png)

1. 對於消息的每個URL，選擇是否激活跟蹤。

   >[!IMPORTANT]
   >
   >當連結的URL用作標籤時，建議取消激活跟蹤以避免因網路釣魚而遭拒的風險。
   >
   >例如，如果將www.adobe.com URL插入消息並激活其跟蹤，則超文本連結的內容將修改為https://nlt.adobe.net/r/?id=xxxxxx。 這意味著收件人消息客戶端可以認為它具有欺詐性。

1. 如果需要，請更改跟蹤標籤，按兩下標籤並輸入新標籤。

   >[!NOTE]
   >
   >可以修改被跟蹤的URL的標籤和標籤，以簡化跟蹤遞送時的資訊讀取。 計算按一下計數時，將添加兩個或兩個同名的URL。

1. 如果需要，請更改跟蹤模式，在 **[!UICONTROL Tracking]** 匹配目標連結的列，如下所示：

   ![](assets/s_ncs_user_select_tracking_mode.png)

   對於每個URL，可將跟蹤模式設定為以下值之一：

   * **[!UICONTROL Enabled]** :在此URL上激活跟蹤。
   * **[!UICONTROL Not tracked]** :停用此URL上的跟蹤。
   * **[!UICONTROL Always enabled]** :始終激活此URL的跟蹤。 保存此資訊，以便下次，如果URL再次出現在將來的消息內容中，則自動激活其跟蹤。
   * **[!UICONTROL Never tracked]** :從不激活此URL的跟蹤。 保存此資訊，以便下次，如果URL在將來的消息中再次出現，則自動停用其跟蹤。
   * **[!UICONTROL Opt-out]** :將此URL視為選擇退出或取消訂閱URL。
   * **[!UICONTROL Mirror page]** :認為此URL是鏡像頁URL。

1. 此外，您還可以在的 **[!UICONTROL Category]** 的雙曲餘切值。 這些類別可以顯示報告，例如 **[!UICONTROL URLs and click streams]** （請參見） [此部分](../../reporting/using/reports-on-deliveries.md#urls-and-click-streams))。 類別在特定枚舉中定義： **[!UICONTROL urlCategory]** （請參見） [管理枚舉](../../platform/using/managing-enumerations.md))。
