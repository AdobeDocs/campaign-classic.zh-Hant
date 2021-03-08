---
solution: Campaign Classic
product: campaign
title: 論壇
description: 論壇
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
translation-type: tm+mt
source-git-commit: 693e38477b318ee44e0373a04d8524ddf128fe36
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---


# 論壇{#discussion-forums}

Adobe Campaign的營運商可以利用論壇來分享資訊。 以下各元素各有其論壇：計畫、計畫、宣傳、資源、模擬、股票。 每家運營商還設有個人論壇。 所有討論都是公開的，甚至在個人論壇上。

營運商可訂閱論壇，在每次張貼訊息時收到通知電子郵件。

## 訪問論壇{#accessing-a-forum}

若要造訪促銷活動、營運商等的論壇，請前往其控制面板，然後按一下右上角的&#x200B;**[!UICONTROL Forum]**&#x200B;連結。 此連結也會提供論壇中訊息的總數。

![](assets/mrm_forum_access_link.png)

## 使用論壇{#using-a-forum}

訊息及其回應會依時間順序顯示（從最新到最舊）。

若要顯示訊息的內容，請按一下其標題。

![](assets/mrm_forum_expand_msg.png)

**開始新討論**

要開始新討論，請按一下右上角的&#x200B;**[!UICONTROL Add a discussion]**&#x200B;按鈕。 **[!UICONTROL Discussion forum]**&#x200B;方塊出現（請參閱下方）。

![](assets/mrm_forum_new_thread.png)

**將訊息張貼至現有討論**

要向現有討論發佈消息，請開啟要回答的消息，然後按一下左上角的&#x200B;**[!UICONTROL Reply]**&#x200B;連結。 **[!UICONTROL Discussion forum]**&#x200B;方塊出現（請參閱下方）。

![](assets/mrm_forum_answer_msg.png)

當您回覆訊息時，張貼原始訊息的人員會收到通知。

**寫入訊息**

在&#x200B;**[!UICONTROL Discussion forum]**&#x200B;方塊中：

1. 在&#x200B;**[!UICONTROL Message]**&#x200B;欄位中輸入文本，在&#x200B;**[!UICONTROL Subject]**&#x200B;欄位中輸入討論標題。

   ![](assets/mrm_forum_edit_msg.png)

1. 如有必要，請：

   * 如果您希望有人參加未訂閱論壇的討論，請使用&#x200B;**[!UICONTROL Operator to notify]**&#x200B;欄位。 營運商將會收到此特定訊息的通知電子郵件（不會訂閱論壇）。 要通知多個運算子，請選擇一組運算子。
   * 要向郵件添加附件，請按一下&#x200B;**[!UICONTROL Browse]**。 附件也會包含在通知電子郵件中。 附件只能單獨發送：若要傳送數個檔案，您需要壓縮檔案。

1. 按一下&#x200B;**[!UICONTROL Create the message]**&#x200B;將它張貼至論壇。

>[!NOTE]
>
>一旦訊息張貼至論壇後，便無法再變更或刪除。

## 張貼至營運商的個人論壇{#posting-to-the-personal-forum-of-an-operator}

例如，如果您的訊息不涉及特定促銷活動，但您仍想追蹤Adobe Campaign的對話，您可以將訊息張貼至營運商的論壇。 個人論壇是公開的，所有營運商都會看到您的訊息。 營運商在每次有人張貼至個人論壇時都會收到訊息。

要訪問操作員論壇：

* 如果您具有訪問瀏覽器&#x200B;**[!UICONTROL Administration > Access management > Operators]**&#x200B;節點的必要權限，請開啟所需運算子的儀表板，然後按一下右上角的&#x200B;**[!UICONTROL Forum]**&#x200B;連結。
* 如果沒有，請尋找Adobe Campaign的營運商名稱（透過此營運商張貼至論壇的訊息，指派給他的工作），然後按一下它以存取其控制面板。 您也可以要求管理員建立運算子資料夾的檢視。

## 訂閱論壇{#subscribing-to-a-forum}

訂閱論壇可讓您關注討論。 每次將訊息張貼至論壇時，您都會收到電子郵件通知。 此電子郵件將包含郵件正文和任何附件。 若要回覆訊息，請按一下電子郵件內文，然後登入Adobe Campaign網頁介面。 當您訂閱論壇時，所有人都能看到此資訊。

* 若要訂閱論壇，請按一下訊息清單上方右上方區段的&#x200B;**[!UICONTROL Follow discussions]**&#x200B;按鈕。

   ![](assets/mrm_forum_subscribe.png)

   該節顯示為藍色，顯示您已訂閱論壇。

* 要取消訂閱論壇，請按一下&#x200B;**[!UICONTROL Unsubscribe]**&#x200B;按鈕。

   ![](assets/mrm_forum_unsubscribe.png)

* 您的個人儀表板會列出您所訂閱的論壇。 按一下&#x200B;**[!UICONTROL Subscription to discussion forums]**&#x200B;連結以顯示清單，然後按一下您感興趣的項目以存取其論壇。

   ![](assets/platform_dashboard_operator_subscr_forums.png)

   有關個人儀表板的詳細資訊，請參閱[本節](../../platform/using/access-management-operators.md)。

* 要查看誰訂閱了論壇，請按一下消息清單上方的&#x200B;**[!UICONTROL List of subscribers to this discussion forum]**&#x200B;連結。

   ![](assets/mrm_forum_subscribers.png)

## 正在檢查通知傳送{#checking-notification-delivery}

如果訂閱論壇的營運商未如預期般收到通知：

* 檢查是否在操作員的配置檔案中輸入了電子郵件地址。
* 轉至&#x200B;**[!UICONTROL Administration > Production > Technical workflows > Campaign processes]**&#x200B;節點，檢查&#x200B;**[!UICONTROL Jobs in discussion forums]**&#x200B;工作流是否已啟動且沒有錯誤。
* 檢視傳送記錄檔：

   * 在Adobe Campaign首頁上，轉至&#x200B;**[!UICONTROL Campaigns > Navigation > Deliveries]** ，然後開啟&#x200B;**[!UICONTROL Discussion forum notification]**&#x200B;傳送。
   * 在瀏覽器中，轉至&#x200B;**[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]**，然後按一下&#x200B;**[!UICONTROL Discussion forum notifications]**。

   在&#x200B;**[!UICONTROL Discussion forum notifications]**&#x200B;框中，在&#x200B;**[!UICONTROL Edit > Delivery]**&#x200B;頁籤中可找到交付日誌。 您也可以檢視&#x200B;**[!UICONTROL Tracking > Log]**&#x200B;和&#x200B;**[!UICONTROL Exclusion causes]**&#x200B;標籤。

