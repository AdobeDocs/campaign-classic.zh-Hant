---
product: campaign
title: 病毒式行銷及社交行銷
description: 病毒式行銷及社交行銷
audience: delivery
content-type: reference
topic-tags: subscriptions-and-referrals
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 2%

---

# 病毒式行銷及社交行銷{#viral-and-social-marketing}

![](../../assets/common.svg)

## 關於病毒式行銷 {#about-viral-marketing}

Adobe Campaign可讓您設定工具來鼓勵病毒式行銷。

這可讓傳遞收件者或網站訪客與其網路共用資訊：從新增連結至其Facebook或Twitter設定檔，到傳送訊息給朋友。

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>為了新增連結才能正常運作，必須有相符的鏡像頁面可用。 若要這麼做，請在傳送中納入鏡像頁面的連結。

## 社交網路：共用連結 {#social-networks--sharing-a-link}

若要讓傳遞收件者與其網路成員共用訊息內容，您必須包含相符的個人化區塊。

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>依預設，區塊清單中不提供此連結。 您可以按一下&#x200B;**[!UICONTROL Other...]**&#x200B;並選取&#x200B;**[!UICONTROL Social network sharing links]**&#x200B;區塊來存取它。

![](assets/s_ncs_user_viral_add_link_via_others.png)

呈現方式如下：

![](assets/s_ncs_user_viral_add_link_rendering.png)

當收件者按一下其中一個社交網路的圖示時，就會自動將他們重新導向至其帳戶，並可透過連結共用訊息內容。 這可讓其網路成員存取通訊。

>[!NOTE]
>
>此個人化區塊包含所有連結（用於訊息傳送以及與所有社交網路共用）。 可依您的需求加以變更。 不過，設定會保留給進階使用者。 若要編輯相符的個人化區塊，請前往Adobe Campaign樹狀結構清單的&#x200B;**[!UICONTROL Resources > Campaign management > Personalization blocks]**&#x200B;節點。

## 病毒式行銷：轉告朋友 {#viral-marketing--forward-to-a-friend}

病毒式服務可執行反向連結類型動作：這些動作可讓您將訊息轉送給朋友。 被推薦者的簡檔被暫時儲存在資料庫中（在專用表中）。 轉發的消息包括推薦者訂閱的連結：若有，則會將其新增至Adobe Campaign資料庫。

訊息轉送以與社交網路連結相同的原則為基礎。

應用以下階段：

1. 將&#x200B;**[!UICONTROL Social network sharing links]**&#x200B;個人化區塊新增至原始訊息的內文中。
1. 郵件收件人可以按一下&#x200B;**[!UICONTROL Email]**&#x200B;表徵圖將此郵件發送給一個或多個朋友。

   ![](assets/s_ncs_user_viral_email_link.png)

   推薦表可讓您輸入裁判的電子郵件地址。

   ![](assets/s_ncs_user_viral_email_msg.png)

   當主要收件者按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕時，訊息會傳送給他們。

   >[!NOTE]
   >
   >您可依需求個人化此訊息的內容。 它根據儲存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;節點中的&#x200B;**[!UICONTROL Transfer of original message]**&#x200B;模板建立。
   >
   >您也可以變更可供反向連結使用的訊息轉送表單。若要這麼做，您需要變更儲存在&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;節點中的&#x200B;**病毒式表單** Web應用程式。

1. 在轉送的訊息中，連結可讓裁判將其設定檔儲存在資料庫中。 為此提供了入門表。

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >此結構可調整。 要執行此操作，您需要修改儲存在&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;節點中的&#x200B;**收件人訂閱** Web應用程式。
   >
   >有關Web應用程式的詳細資訊，請參閱[此部分](../../web/using/about-web-applications.md)。

   驗證後，會傳送確認訊息給他們：只有在他們啟用確認訊息中的連結後，他們才會永久註冊。 此消息基於&#x200B;**[!UICONTROL Registration confirmation]**&#x200B;模板建立，該模板儲存在&#x200B;**[!UICONTROL Administration > Campaign management > Technical delivery templates]**&#x200B;節點中。

   推薦者被添加到資料庫的&#x200B;**Recipients**&#x200B;資料夾中，並（預設）訂閱&#x200B;**Newsletter**&#x200B;資訊服務。

## 追蹤社交網路分享 {#tracking-social-network-sharing}

會追蹤共用資訊的共用和存取。 Adobe Campaign收集的這些資訊可在兩處存取：

* 在傳送的&#x200B;**[!UICONTROL Tracking]**&#x200B;標籤中（或針對每個收件者個別顯示）:

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 在專用的&#x200B;**[!UICONTROL Sharing to social networks]**&#x200B;報告中：

   ![](assets/s_ncs_user_viral_report.png)
