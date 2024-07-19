---
product: campaign
title: 病毒式行銷及社交行銷
description: 病毒式行銷及社交行銷
feature: Social Marketing
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 2%

---

# 病毒式行銷及社交行銷{#viral-and-social-marketing}

Adobe Campaign可讓您設定鼓勵病毒式行銷的工具。

這可讓傳遞收件者或網站訪客與其網路共用資訊：從新增連結至其Facebook或X (先前稱為Twitter)設定檔，到傳送訊息給朋友。

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>為了使新增的連結正常運作，必須提供相符的映象頁面。 若要這麼做，請在傳送中包含指向映象頁面的連結。

## 社交網路：共用連結 {#social-networks--sharing-a-link}

若要讓傳遞收件者與其網路成員共用訊息內容，您必須包含相符的個人化區塊。

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>依預設，封鎖清單中不提供此連結。 您可以按一下&#x200B;**[!UICONTROL Other...]**&#x200B;並選取&#x200B;**[!UICONTROL Social network sharing links]**&#x200B;區塊來存取它。

![](assets/s_ncs_user_viral_add_link_via_others.png)

演算方式如下：

![](assets/s_ncs_user_viral_add_link_rendering.png)

當收件者按一下顯示的其中一個社交網路圖示時，系統會自動將他們重新導向至其帳戶，並可透過連結共用訊息內容。 如此可讓網路成員存取通訊。

>[!NOTE]
>
>此個人化區塊包含所有連結（用於傳送訊息並與所有社交網路分享）。 您可以根據自己的需求加以變更。 但是，設定會保留給進階使用者。 若要編輯相符的個人化區塊，請前往Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Resources > Campaign management > Personalization blocks]**&#x200B;節點。

## 病毒式行銷：轉寄給朋友 {#viral-marketing--forward-to-a-friend}

病毒式服務可讓您執行轉介型別的動作：這些動作可讓您將訊息轉寄給朋友。 被裁判的設定檔會暫時儲存在資料庫中（在專用表格中）。 轉送的訊息包含供被推薦者訂閱的連結：如果提供，會新增至Adobe Campaign資料庫。

訊息轉寄與社交網路連結的原理相同。

套用下列階段：

1. 將&#x200B;**[!UICONTROL Social network sharing links]**&#x200B;個人化區塊新增至原始郵件的內文。
1. 郵件收件者可以按一下&#x200B;**[!UICONTROL Email]**&#x200B;圖示，將此郵件傳送給一或多個朋友。

   ![](assets/s_ncs_user_viral_email_link.png)

   推薦表單可讓您輸入推薦人的電子郵件地址。

   ![](assets/s_ncs_user_viral_email_msg.png)

   當主要收件者按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕時，會將訊息傳送給他們。

   >[!NOTE]
   >
   >此訊息的內容可以根據您的需求進行個人化。 它是根據儲存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;節點中的&#x200B;**[!UICONTROL Transfer of original message]**&#x200B;範本建立的。
   >
   >您也可以變更轉寄給反向連結的訊息表單。若要這麼做，您必須變更儲存在&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;節點中的&#x200B;**病毒表單**&#x200B;網頁應用程式。

1. 在轉送的訊息中，連結可讓裁判將其設定檔儲存在資料庫中。 為此提供輸入表單。

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >可調整此設定。 若要這麼做，您必須修改儲存在&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;節點中的&#x200B;**收件者訂閱**&#x200B;網頁應用程式。
   >
   >如需網頁應用程式的詳細資訊，請參閱[本節](../../web/using/about-web-applications.md)。

   驗證後，系統會將確認訊息傳送給他們：只有當他們在確認訊息中啟用連結時，他們才會永久註冊。 此訊息是根據&#x200B;**[!UICONTROL Registration confirmation]**&#x200B;範本建立的，該範本儲存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;節點中。

   被推薦者已新增至資料庫的&#x200B;**收件者**&#x200B;資料夾，並已訂閱（依預設）至&#x200B;**Newsletter**&#x200B;資訊服務。

## 追蹤社交網路分享 {#tracking-social-network-sharing}

會追蹤共用資訊的共用與存取權。 Adobe Campaign收集的這項資訊可在兩個地方存取：

* 在傳遞的&#x200B;**[!UICONTROL Tracking]**&#x200B;索引標籤中（或個別針對每個收件者）：

  ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 在專用的&#x200B;**[!UICONTROL Sharing to social networks]**&#x200B;報告中：

  ![](assets/s_ncs_user_viral_report.png)
