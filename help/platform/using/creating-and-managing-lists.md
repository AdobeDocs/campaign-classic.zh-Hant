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

清單是透過&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL Lists]**&#x200B;連結建立及管理的。

![](assets/s_ncs_user_interface_group_link.png)

Adobe Campaign 提供兩種類型的清單：

* **[!UICONTROL Group]**&#x200B;型別： **[!UICONTROL Group]**&#x200B;型別清單屬於根據特定條件選取的&#x200B;**靜態**&#x200B;人員清單。 此清單就像一組設定檔的快照。 請注意，用戶檔案新增至資料庫中時，不會對群組清單進行自動更新。

  如需如何建立&#x200B;**[!UICONTROL Group]**&#x200B;型別清單的詳細資訊，請參閱此[頁面](#creating-a-profile-list-from-a-group)。

* **[!UICONTROL List]**&#x200B;型別： **[!UICONTROL List]**&#x200B;型別清單可讓您使用工作流程來建立和管理清單。 這些是從資料匯入所產生的特定清單，可透過專用的&#x200B;**[!UICONTROL List update]**&#x200B;工作流程活動進行更新。

  不像&#x200B;**[!UICONTROL Group]**&#x200B;型別清單，此型別清單可以使用&#x200B;**[!UICONTROL Scheduler]**&#x200B;活動自動更新。 請注意，如需如何建立&#x200B;**[!UICONTROL List]**&#x200B;型別清單的範例，請參閱[此頁面](../../workflow/using/list-update.md)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#create-list-video)

## 從群組建立設定檔清單 {#creating-a-profile-list-from-a-group}

透過&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;連結建立的&#x200B;**[!UICONTROL Group]**&#x200B;型別清單必須根據預設的Adobe Campaign設定檔表格(nms：recipient)。

>[!NOTE]
>
>若要建立包含其他資料型別的清單，您必須執行工作流程。 例如，若您在訪客表格上使用查詢，然後更新清單，即可建立訪客清單。 如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

若要建立新的&#x200B;**[!UICONTROL Group]**&#x200B;型別清單，請套用下列步驟：

1. 按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕並選取&#x200B;**[!UICONTROL New list]**。

   ![](assets/s_ncs_user_new_group.png)

1. 在清單建立視窗的&#x200B;**[!UICONTROL Edit]**&#x200B;索引標籤中輸入資訊。

   * 在&#x200B;**[!UICONTROL Label]**&#x200B;欄位中輸入清單名稱，並視需要變更內部名稱。
   * 新增此清單的描述。
   * 您可以指定到期日：達到此日期時，清單會被清除並自動刪除。

     ![](assets/list_expiration_date.png)

1. 在&#x200B;**[!UICONTROL Content]**&#x200B;索引標籤中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選取屬於清單的設定檔。

   ![](assets/s_ncs_user_add_group.png)

1. 按一下&#x200B;**[!UICONTROL Save]**&#x200B;以儲存清單。 然後，清單便會新增至清單概要中。

您可以按一下&#x200B;**[!UICONTROL Create]**，直接從[新增設定檔]視窗建立新設定檔。 該用戶檔案將新增至資料庫。

![](assets/s_ncs_user_new_recipient_from_group.png)

設定檔清單可以像其他清單一樣設定。 請參閱[本節](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

## 將資料連結至清單 {#linking-data-to-a-list}

>[!NOTE]
>
>連結資料至清單只能使用&#x200B;**[!UICONTROL Group]**&#x200B;型別清單完成。

可以篩選一組設定檔的設定檔，並將其連結至清單。 然後可能會傳送傳遞動作至此清單，以定位設定檔。 若要創建用戶檔案群組：

1. 選取用戶檔案並按一下滑鼠右鍵。
1. 選取 **[!UICONTROL Actions > Associate selection with a list...]**。

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. 選取想要的清單或使用&#x200B;**[!UICONTROL Create]**&#x200B;按鈕建立新清單，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. 按一下 **[!UICONTROL Start]** 按鈕。

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

**[!UICONTROL Recreate the list]**&#x200B;選項會從清單中刪除較早的內容。 此模式已經最優化，因為不需查詢確認用戶檔案是否已連結至清單。

如果取消核取&#x200B;**[!UICONTROL No trace of this job is saved in the database]**&#x200B;選項，您可以選取（或建立）執行資料夾，其中會儲存連結至此程式的資訊。

視窗的上方區段可讓您監視執行。 **[!UICONTROL Stop]**&#x200B;按鈕可讓您停止程式。 已處理的連絡人將連結至清單。

您可以透過此作業相關設定檔上的&#x200B;**[!UICONTROL Lists]**&#x200B;索引標籤來監視程式：

![](assets/s_ncs_user_add_selection_to_group_4.png)

您也可以透過Adobe Campaign首頁編輯清單：按一下「**[!UICONTROL Profiles and Targets > Lists]**」功能表並選取相關清單。 **[!UICONTROL Content]**&#x200B;索引標籤會顯示連結至此清單的設定檔。

![](assets/s_ncs_user_add_selection_to_group_5.png)

## 從清單中移除設定檔 {#removing-a-profile-from-a-list}

若要從清單中移除用戶檔案，您可以：

* 編輯清單，在&#x200B;**[!UICONTROL Content]**&#x200B;索引標籤中選取設定檔，然後按一下&#x200B;**[!UICONTROL Delete]**&#x200B;圖示。

  ![](assets/list_remove_a_recipient.png)

* 編輯設定檔，按一下&#x200B;**[!UICONTROL List]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Delete]**&#x200B;圖示。

  ![](assets/recipient_remove_a_list.png)

## 刪除設定檔清單 {#deleting-a-list-of-profiles}

您可以從Adobe Campaign樹狀結構的群組清單中刪除一或多個清單。 若要這麼做，請透過Adobe Campaign首頁中的&#x200B;**[!UICONTROL Advanced > Explorer]**&#x200B;連結編輯樹狀結構。 選取相關群組，然後按一下滑鼠右鍵。 選取 **[!UICONTROL Delete]**。此時將顯示警告訊息，要求您確認是否刪除。

>[!NOTE]
>
>刪除清單時，清單上的用戶檔案不受影響，但是將更新用戶檔案中的資料。

## 教學課程影片 {#create-list-video}

### 如何建立收件者清單

此清單 (list) 是一組靜態的收件者名單，在傳遞作業期間可用於提供目標，或在匯入作業或工作流程執行期間可對其進行更新。收件者清單也稱為客群。

瞭解如何從檔案總管設定收件者清單，以建立對象。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

### 如何使用工作流程建立收件者清單 {#create-list-in-a-wf-video}

瞭解如何在電子郵件目標中使用清單之前，建立工作流程以定位收件者，以及如何使其重複發生。

>[!VIDEO](https://video.tv.adobe.com/v/25603?quality=12)

[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)提供其他Campaign Classic操作說明影片。
