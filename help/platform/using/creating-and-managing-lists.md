---
product: campaign
title: 建立和管理清單
description: 瞭解如何建立和管理清單
feature: Profiles
role: User
level: Beginner
exl-id: 711b84cd-bac8-4f1a-9999-0124fbfc3a01
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 28%

---

# 建立及管理清單{#creating-and-managing-lists}



## 什麼是清單？ {#about-lists-in-adobe-campaign}

清單是一組靜態的設定檔，可在傳遞動作中定位，或在匯入作業或工作流程執行期間更新。 例如，透過查詢而從資料庫中摘取出的母體可形成一個清單。

清單是透過以下方式建立和管理的： **[!UICONTROL Lists]** 中的連結 **[!UICONTROL Profiles and targets]** 標籤。

![](assets/s_ncs_user_interface_group_link.png)

Adobe Campaign 提供兩種類型的清單：

* **[!UICONTROL Group]** 型別： **[!UICONTROL Group]** 型別清單屬於 **靜態** 根據特定條件選取的人員清單。 此清單就像一組設定檔的快照。 請注意，用戶檔案新增至資料庫中時，不會對群組清單進行自動更新。

  如需如何建立 **[!UICONTROL Group]** 型別清單，請參閱此 [頁面](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** 型別： **[!UICONTROL List]** 型別清單可讓您使用工作流程來建立和管理清單。 這些是從資料匯入產生的特定清單，可以透過專用更新 **[!UICONTROL List update]** 工作流程活動。

  不喜歡 **[!UICONTROL Group]** 型別清單，此型別清單可透過 **[!UICONTROL Scheduler]** 活動。 請注意，如需如何建立的範例， **[!UICONTROL List]** 型別清單，請參閱 [此頁面](../../workflow/using/list-update.md).

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#create-list-video)

## 從群組建立設定檔清單 {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** 輸入透過建立的清單 **[!UICONTROL Profiles and targets]** 連結必須根據預設的Adobe Campaign設定檔表格(nms：recipient)。

>[!NOTE]
>
>若要建立包含其他資料型別的清單，您必須執行工作流程。 例如，若您在訪客表格上使用查詢，然後更新清單，即可建立訪客清單。 如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

若要建立新的 **[!UICONTROL Group]** 輸入清單，套用下列步驟：

1. 按一下 **[!UICONTROL Create]** 按鈕並選取 **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. 在 **[!UICONTROL Edit]** 清單建立視窗的標籤。

   * 輸入清單名稱，在 **[!UICONTROL Label]** 欄位並在必要時變更內部名稱。
   * 新增此清單的描述。
   * 您可以指定到期日：達到此日期時，清單會被清除並自動刪除。

     ![](assets/list_expiration_date.png)

1. 在 **[!UICONTROL Content]** 標籤，按一下 **[!UICONTROL Add]** 以選取屬於清單的設定檔。

   ![](assets/s_ncs_user_add_group.png)

1. 按一下 **[!UICONTROL Save]** 以儲存清單。 然後，清單便會新增至清單概要中。

您可以按一下「 」，直接從「新增設定檔」視窗建立新設定檔 **[!UICONTROL Create]**. 該用戶檔案將新增至資料庫。

![](assets/s_ncs_user_new_recipient_from_group.png)

設定檔清單可以像其他清單一樣設定。 請參閱[本節](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

## 將資料連結至清單 {#linking-data-to-a-list}

>[!NOTE]
>
>只能使用將資料連結至清單 **[!UICONTROL Group]** 型別清單。

可以篩選一組設定檔的設定檔，並將其連結至清單。 然後可能會傳送傳遞動作至此清單，以定位設定檔。 若要創建用戶檔案群組：

1. 選取用戶檔案並按一下滑鼠右鍵。
1. 選取 **[!UICONTROL Actions > Associate selection with a list...]**。

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. 選取所要的清單，或使用 **[!UICONTROL Create]** 按鈕，然後按一下 **[!UICONTROL Next]**.

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

此 **[!UICONTROL Recreate the list]** 選項會從清單中刪除先前的內容。 此模式已經最優化，因為不需查詢確認用戶檔案是否已連結至清單。

如果您取消核取 **[!UICONTROL No trace of this job is saved in the database]** 選項，您可以選取（或建立）執行資料夾，其中會儲存連結至此流程的資訊。

視窗的上方區段可讓您監視執行。 此 **[!UICONTROL Stop]** 按鈕可讓您停止此程式。 已處理的連絡人將連結至清單。

您可以透過以下方式監視此流程： **[!UICONTROL Lists]** 索引標籤上的設定檔進行此作業：

![](assets/s_ncs_user_add_selection_to_group_4.png)

您也可以透過Adobe Campaign首頁編輯清單：按一下 **[!UICONTROL Profiles and Targets > Lists]** 功能表並選取相關清單。 此 **[!UICONTROL Content]** 索引標籤會顯示連結至此清單的設定檔。

![](assets/s_ncs_user_add_selection_to_group_5.png)

## 從清單中移除設定檔 {#removing-a-profile-from-a-list}

若要從清單中移除用戶檔案，您可以：

* 編輯清單，選取中的設定檔 **[!UICONTROL Content]** 標籤，然後按一下 **[!UICONTROL Delete]** 圖示。

  ![](assets/list_remove_a_recipient.png)

* 編輯設定檔，按一下 **[!UICONTROL List]** 標籤，然後按一下 **[!UICONTROL Delete]** 圖示。

  ![](assets/recipient_remove_a_list.png)

## 刪除設定檔清單 {#deleting-a-list-of-profiles}

您可以從Adobe Campaign樹狀結構的群組清單中刪除一或多個清單。 若要這麼做，請透過 **[!UICONTROL Advanced > Explorer]** Adobe Campaign首頁中的連結。 選取相關群組，然後按一下滑鼠右鍵。 選取 **[!UICONTROL Delete]**。此時將顯示警告訊息，要求您確認是否刪除。

>[!NOTE]
>
>刪除清單時，清單上的用戶檔案不受影響，但是將更新用戶檔案中的資料。

## 教學課程影片 {#create-list-video}

### 如何建立收件者清單

此清單 (list) 是一組靜態的收件者名單，在傳遞作業期間可用於提供目標，或在匯入作業或工作流程執行期間可對其進行更新。收件者清單也可以稱為受眾。

瞭解如何從檔案總管設定收件者清單，以建立對象。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### 如何使用工作流程建立收件者清單 {#create-list-in-a-wf-video}

瞭解如何在電子郵件目標中使用清單之前，建立工作流程以定位收件者，以及如何使其重複發生。

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
