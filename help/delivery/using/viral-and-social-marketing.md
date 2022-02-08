---
product: campaign
title: 病毒式行銷及社交行銷
description: 病毒式行銷及社交行銷
exl-id: 10fd561f-1b07-490e-9f66-d67e44a0def5
source-git-commit: 1e11b7419388698f5de366cbeddf2be88ef12873
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 2%

---

# 病毒式行銷及社交行銷{#viral-and-social-marketing}

![](../../assets/common.svg)

Adobe Campaign讓你建立工具來鼓勵病毒式營銷。

這樣，遞送收件人或網站訪問者就可以與其網路共用資訊：從添加指向Facebook或Twitter檔案的連結，到向朋友發送資訊。

![](assets/s_ncs_user_viral_icons.png)

>[!CAUTION]
>
>為了使添加的連結正常運行，必須提供匹配的鏡像頁。 為此，請在傳遞中包括到鏡像頁的連結。

## 社交網路：共用連結 {#social-networks--sharing-a-link}

要使傳遞收件人能夠與其網路成員共用郵件內容，您需要包括匹配的個性化塊。

![](assets/s_ncs_user_viral_add_link.png)

>[!NOTE]
>
>預設情況下，塊清單中不提供此連結。 您可以通過按一下 **[!UICONTROL Other...]**，然後選擇 **[!UICONTROL Social network sharing links]** 框。

![](assets/s_ncs_user_viral_add_link_via_others.png)

呈現方式如下：

![](assets/s_ncs_user_viral_add_link_rendering.png)

當收件人按一下顯示的社交網路之一的表徵圖時，他們將自動重定向到其帳戶，並可以通過連結共用消息內容。 這樣，其網路成員就可以訪問通信。

>[!NOTE]
>
>此個性化塊包含所有連結（用於與所有社交網路發送和共用消息）。 可以根據需要進行更改。 但是，為高級用戶保留配置。 要編輯匹配的個性化設定塊，請轉到 **[!UICONTROL Resources > Campaign management > Personalization blocks]** Adobe Campaign樹的節點。

## 病毒式營銷：轉給朋友 {#viral-marketing--forward-to-a-friend}

病毒服務允許執行推薦類型的操作：這些操作使您能夠將消息轉發給朋友。 裁判者的檔案被臨時地儲存在資料庫中（在專用表中）。 轉發的資訊包括供裁判訂閱的連結：如果他們這樣做，他們將被添加到Adobe Campaign資料庫。

消息轉發與社交網路鏈路的原理相同。

應用以下階段：

1. 添加 **[!UICONTROL Social network sharing links]** 個性化塊到原始消息的正文中。
1. 郵件收件人可以按一下 **[!UICONTROL Email]** 表徵圖，將此消息發送給一個或多個好友。

   ![](assets/s_ncs_user_viral_email_link.png)

   通過推薦表單，您可以輸入裁判的電子郵件地址。

   ![](assets/s_ncs_user_viral_email_msg.png)

   當主收件人按一下 **[!UICONTROL Next]** 按鈕

   >[!NOTE]
   >
   >此郵件的內容可以個性化以滿足您的需要。 它是基於 **[!UICONTROL Transfer of original message]** 模板，儲存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 的下界。
   >
   >還可以更改可供引用者使用的消息轉發表單。要執行此操作，您需要更改 **病毒形式** 儲存在 **[!UICONTROL Resources > Online > Web applications]** 的下界。

1. 在轉發的資訊中，連結允許裁判將他們的檔案保存在資料庫中。 為此提供了一個入口表。

   ![](assets/s_ncs_user_viral_create_account_form.png)

   >[!NOTE]
   >
   >這種結構可以調整。 為此，需要修改 **收件人訂閱** 儲存在 **[!UICONTROL Resources > Online > Web applications]** 的下界。
   >
   >有關Web應用程式的詳細資訊，請參閱 [此部分](../../web/using/about-web-applications.md)。

   驗證後，會向他們發送一條確認消息：只有在激活確認消息中的連結後，才會永久註冊。 此消息是根據 **[!UICONTROL Registration confirmation]** 模板，儲存在 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 的下界。

   裁判被加到 **收件人** 資料夾，並（預設）訂閱到 **新聞稿** 資訊服務。

## 跟蹤社交網路共用 {#tracking-social-network-sharing}

跟蹤共用資訊的共用和訪問。 Adobe Campaign收集的這些資訊可在兩個地方查閱：

* 的 **[!UICONTROL Tracking]** （或每個收件人的單個）:

   ![](assets/s_ncs_user_network_del_tracking_tab.png)

* 在 **[!UICONTROL Sharing to social networks]** 報告：

   ![](assets/s_ncs_user_viral_report.png)
