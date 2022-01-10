---
product: campaign
title: 論壇
description: 了解如何使用Campaign論壇
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: 222853c5-c754-4c0b-8ee4-a64b2f8677a4
source-git-commit: 98380c18b915cfebc980e68f9840f9d8919eaca4
workflow-type: tm+mt
source-wordcount: '728'
ht-degree: 0%

---

# 論壇{#discussion-forums}

![](../../assets/v7-only.svg)

Adobe Campaign運營商可使用論壇來共用資訊。 以下各元素有各自的論壇：計畫，計畫，行銷，資源，模擬，股票。 每家運營商還有個人論壇。 所有討論都是公開的，甚至在個人論壇上。

操作員可以訂閱論壇，以在每次發送郵件時接收通知電子郵件。

## 存取論壇 {#accessing-a-forum}

若要造訪促銷活動的論壇、運算子等，請前往其控制面板，然後按一下 **[!UICONTROL Forum]** 連結。 此連結也提供論壇中的訊息總數。

![](assets/mrm_forum_access_link.png)

## 使用論壇 {#using-a-forum}

訊息及其回應會依時間順序顯示（從最新到最舊）。

若要顯示訊息的內容，請按一下訊息的標題。

![](assets/mrm_forum_expand_msg.png)

**開始新的討論**

要啟動新討論，請按一下 **[!UICONTROL Add a discussion]** 按鈕。 此 **[!UICONTROL Discussion forum]** 框（請參閱下面）。

![](assets/mrm_forum_new_thread.png)

**向現有討論發佈消息**

要向現有討論發佈消息，請開啟要應答的消息，然後按一下 **[!UICONTROL Reply]** 左上角的連結。 此 **[!UICONTROL Discussion forum]** 框（請參閱下面）。

![](assets/mrm_forum_answer_msg.png)

當您回覆訊息時，張貼原始訊息的人員會收到通知。

**撰寫訊息**

在 **[!UICONTROL Discussion forum]** 框：

1. 在 **[!UICONTROL Message]** 欄位與討論標題 **[!UICONTROL Subject]** 欄位。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要：

   * 如果您希望未訂閱論壇的人參與討論，請使用 **[!UICONTROL Operator to notify]** 欄位。 運算子會收到此特定訊息的通知電子郵件（不會訂閱論壇）。 要通知多個運算子，請選擇一組運算子。
   * 若要將附件新增至訊息，請按一下 **[!UICONTROL Browse]**. 通知電子郵件也會包含附件。 附件只能單獨發送：若要傳送數個檔案，您需要壓縮這些檔案。

1. 按一下 **[!UICONTROL Create the message]** 發佈到論壇。

>[!NOTE]
>
>將訊息張貼至論壇後，就無法再變更或刪除訊息。

## 發佈至操作員的個人論壇 {#posting-to-the-personal-forum-of-an-operator}

例如，如果您的訊息與特定促銷活動無關，但您仍想要追蹤Adobe Campaign中的對話，您可以將訊息張貼至運算子的論壇。 個人論壇是公開的，所有操作者都會看到您的資訊。 每當有人貼文至其個人論壇時，操作員都會收到訊息。

要訪問操作員的論壇：

* 如果您有必要的存取權限 **[!UICONTROL Administration > Access management > Operators]** 瀏覽器的節點，開啟所需運算子的控制面板，然後按一下 **[!UICONTROL Forum]** 連結。
* 若否，請在Adobe Campaign中尋找運算子的名稱（透過此運算子張貼至論壇的訊息，指派給他們的任務），然後按一下該名稱以存取其控制面板。 您也可以要求管理員建立運算子資料夾的檢視。

## 訂閱論壇 {#subscribing-to-a-forum}

訂閱論壇可讓您關注討論。 每次將訊息張貼至論壇時，您都會收到電子郵件通知。 此電子郵件將包含郵件正文和任何附件。 若要回答訊息，請按一下電子郵件內文，然後登入Adobe Campaign網頁介面。 當您訂閱論壇時，所有人都能看到此資訊。

* 若要訂閱論壇，請按一下 **[!UICONTROL Follow discussions]** 按鈕（位於消息清單的右上角）。

   ![](assets/mrm_forum_subscribe.png)

   區段顯示為藍色，顯示您已訂閱論壇。

* 若要取消訂閱論壇，請按一下 **[!UICONTROL Unsubscribe]** 按鈕。

   ![](assets/mrm_forum_unsubscribe.png)

* 您的個人儀表板會列出您訂閱的論壇。 按一下 **[!UICONTROL Subscription to discussion forums]** 連結以顯示清單，然後按一下您感興趣的項目以存取其論壇。

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   有關個人儀表板的詳細資訊，請參閱 [本節](../../platform/using/access-management-operators.md).

* 若要查看訂閱論壇的人，請按一下 **[!UICONTROL List of subscribers to this discussion forum]** 郵件清單上方的連結。

   ![](assets/mrm_forum_subscribers.png)

## 檢查通知傳送 {#checking-notification-delivery}

如果訂閱論壇的運算子未如預期般收到通知：

* 檢查是否在運算子的設定檔中輸入電子郵件地址。
* 前往 **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** 並檢查 **[!UICONTROL Jobs in discussion forums]** 工作流程已啟動，且沒有錯誤。
* 檢視傳送記錄檔：

   * 在Adobe Campaign首頁上，前往 **[!UICONTROL Campaigns > Navigation > Deliveries]**，然後開啟 **[!UICONTROL Discussion forum notification]** 傳遞。
   * 在瀏覽器中，前往 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**，然後按一下 **[!UICONTROL Discussion forum notifications]**.
   在 **[!UICONTROL Discussion forum notifications]** 框中，則在 **[!UICONTROL Edit > Delivery]** 標籤。 您也可以檢視 **[!UICONTROL Tracking > Log]** 和 **[!UICONTROL Exclusion causes]** 標籤。
