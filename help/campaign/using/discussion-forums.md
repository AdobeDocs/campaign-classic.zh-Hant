---
title: 論壇
seo-title: 論壇
description: 論壇
seo-description: null
page-status-flag: never-activated
uuid: 6253bb32-c71d-45ac-bc03-027131ae95a5
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: 88eb17b6-5206-4064-9cd9-b4645a85c609
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d30de91002862b664249c5a704b7c0f521dd30f2

---


# 論壇{#discussion-forums}

Adobe Campaign營運商可使用論壇來分享資訊。 以下各元素各有其論壇：計畫、計畫、宣傳、資源、模擬、股票。 每家運營商還設有個人論壇。 所有討論都是公開的，甚至在個人論壇上。

營運商可訂閱論壇，在每次張貼訊息時收到通知電子郵件。

## 存取論壇 {#accessing-a-forum}

若要造訪促銷活動的論壇、營運商等，請移至其控制面板，然後按一下右上角 **[!UICONTROL Forum]** 的連結。 此連結也會提供論壇中訊息的總數。

![](assets/mrm_forum_access_link.png)

## 使用論壇 {#using-a-forum}

訊息及其回應會依時間順序顯示（從最新到最舊）。

若要顯示訊息的內容，請按一下其標題。

![](assets/mrm_forum_expand_msg.png)

**開始新討論**

要開始新討論，請按一下 **[!UICONTROL Add a discussion]** 右上角的按鈕。 包裝 **[!UICONTROL Discussion forum]** 盒隨即出現（請參閱下方）。

![](assets/mrm_forum_new_thread.png)

**將訊息張貼至現有討論**

若要將訊息張貼至現有討論，請開啟您要回覆的訊息，然後按一 **[!UICONTROL Reply]** 下左上角的連結。 包裝 **[!UICONTROL Discussion forum]** 盒隨即出現（請參閱下方）。

![](assets/mrm_forum_answer_msg.png)

當您回覆訊息時，張貼原始訊息的人員會收到通知。

**寫入訊息**

包裝盒 **[!UICONTROL Discussion forum]** 中：

1. 在欄位中輸入 **[!UICONTROL Message]** 文本，在欄位中輸入討論 **[!UICONTROL Subject]** 標題。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要，請：

   * 如果您希望某人參與未訂閱論壇的討論，請使用該字 **[!UICONTROL Operator to notify]** 段。 營運商將會收到此特定訊息的通知電子郵件（不會訂閱論壇）。 要通知多個運算子，請選擇一組運算子。
   * 要向郵件添加附件，請按一下 **[!UICONTROL Browse]**。 附件也會包含在通知電子郵件中。 附件只能單獨發送：若要傳送數個檔案，您需要壓縮檔案。

1. 按一 **[!UICONTROL Create the message]** 下將其張貼至論壇。

>[!NOTE]
>
>一旦訊息張貼至論壇後，便無法再變更或刪除。

## 張貼至營運商的個人論壇 {#posting-to-the-personal-forum-of-an-operator}

例如，如果您的訊息與特定促銷活動無關，但您仍想要追蹤Adobe Campaign中的對話，您可以將訊息張貼至營運商的論壇。 個人論壇是公開的，所有營運商都會看到您的訊息。 營運商在每次有人張貼至個人論壇時都會收到訊息。

要訪問操作員論壇：

* 如果您擁有存取檔案總管節點的必 **[!UICONTROL Administration > Access management > Operators]** 要權限，請開啟所要運算子的控制面板，然後按一下右上角 **[!UICONTROL Forum]** 的連結。
* 如果沒有，請在Adobe Campaign中尋找運算元的名稱（透過此運算元張貼至論壇的訊息，指派給他的工作），然後按一下該名稱以存取其控制面板。 您也可以要求管理員建立運算子資料夾的檢視。

## 訂閱論壇 {#subscribing-to-a-forum}

訂閱論壇可讓您關注討論。 每次將訊息張貼至論壇時，您都會收到電子郵件通知。 此電子郵件將包含郵件正文和任何附件。 若要回覆訊息，請按一下電子郵件內文，然後登入Adobe Campaign網頁介面。 當您訂閱論壇時，所有人都能看到此資訊。

* 若要訂閱論壇，請按一 **[!UICONTROL Follow discussions]** 下訊息清單上方右上方區段的按鈕。

   ![](assets/mrm_forum_subscribe.png)

   該節顯示為藍色，顯示您已訂閱論壇。

* 若要取消訂閱論壇，請按一下 **[!UICONTROL Unsubscribe]** 按鈕。

   ![](assets/mrm_forum_unsubscribe.png)

* 您的個人儀表板會列出您所訂閱的論壇。 按一下 **[!UICONTROL Subscription to discussion forums]** 連結以顯示清單，然後按一下您感興趣的項目以存取其論壇。

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   有關個人儀表板的詳細資訊，請參 [閱本節](../../platform/using/access-management.md#operators)。

* 要查看誰訂閱了論壇，請按一下消息 **[!UICONTROL List of subscribers to this discussion forum]** 清單上方的連結。

   ![](assets/mrm_forum_subscribers.png)

## 檢查通知傳送 {#checking-notification-delivery}

如果訂閱論壇的營運商未如預期般收到通知：

* 檢查是否在操作員的配置檔案中輸入了電子郵件地址。
* 轉到節 **[!UICONTROL Administration > Production > Technical workflows > Campaign processes]** 點並檢查工作 **[!UICONTROL Jobs in discussion forums]** 流是否已啟動且未出錯。
* 檢視傳送記錄檔：

   * 在Adobe Campaign首頁上，前往 **[!UICONTROL Campaigns > Navigation > Deliveries]**，然後開啟傳 **[!UICONTROL Discussion forum notification]** 送。
   * 在瀏覽器中，轉至 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**，然後按一下 **[!UICONTROL Discussion forum notifications]**。
   在方塊 **[!UICONTROL Discussion forum notifications]** 中，傳送記錄檔位於標籤 **[!UICONTROL Edit > Delivery]** 中。 您也可以檢視 **[!UICONTROL Tracking > Log]** 和標 **[!UICONTROL Exclusion causes]** 簽。

