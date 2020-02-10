---
title: 建立和管理清單
seo-title: 建立和管理清單
description: 建立和管理清單
seo-description: null
page-status-flag: never-activated
uuid: 17d1a7d0-a728-490e-a820-19f469fddbcd
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: profile-management
discoiquuid: 9fc243b2-7b7b-4083-83f6-04c12336492d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 建立和管理清單{#creating-and-managing-lists}

## 關於 Adobe Campaign 中的清單 {#about-lists-in-adobe-campaign}

清單 (list) 是一組靜態的用戶檔案，在傳遞作業期間可用於提供目標，或在匯入作業或工作流程執行期間可對其進行更新。例如，透過查詢而從資料庫中摘取出的母體可形成一個清單。

然後，可以遵守許可式行銷的職業道德，設定針對這些清單的傳遞 (透過電子郵件、SMS 或其他通路)。

Lists are created and managed via the **[!UICONTROL Lists]** link in the **[!UICONTROL Profiles and targets]** tab.

![](assets/s_ncs_user_interface_group_link.png)

Adobe Campaign 提供兩種類型的清單：

* **[!UICONTROL Group]** 類型：類 **[!UICONTROL Group]** 型清單屬於根據特 **定條件選擇** 的靜態人員清單。 此清單就像是一組用戶檔案的快照。請注意，用戶檔案新增至資料庫中時，不會對群組清單進行自動更新。

   For more information on how to create a **[!UICONTROL Group]** type list, refer to this [page](#creating-a-profile-list-from-a-group).

* **[!UICONTROL List]** 類型：類型 **[!UICONTROL List]** 清單可讓您使用工作流程來建立和管理清單。 These will be specific lists resulting from data imports, that can be updated via the dedicated **[!UICONTROL List update]** workflow activity.

   Unlike the **[!UICONTROL Group]** type list, this type list can be automatically updated with a **[!UICONTROL Scheduler]** activity. Note that For an example on how to create **[!UICONTROL List]** type lists, refer to [this page](../../workflow/using/list-update.md).

## 從群組建立用戶檔案清單 {#creating-a-profile-list-from-a-group}

**[!UICONTROL Group]** 透過連結建立的類 **[!UICONTROL Profiles and targets]** 型清單必須以預設的Adobe Campaign描述檔表格(nms:recipient)為基礎。

>[!NOTE]
>
>若要建立包含其他資料類型的清單，您必須執行工作流程。例如，透過在訪客資料表上查詢並更新清單，您可以建立訪客清單。如需此工作流程的詳細資訊，請參閱[本小節](../../workflow/using/about-workflows.md)。

To create a new **[!UICONTROL Group]** type list, apply the following steps:

1. Click the **[!UICONTROL Create]** button and select **[!UICONTROL New list]**.

   ![](assets/s_ncs_user_new_group.png)

1. 在清單建立視窗的 **[!UICONTROL Edit]** 索引標籤中輸入資訊。

   * 在 **[!UICONTROL Label]** 欄位中輸入清單名稱，並視需要變更內部名稱。
   * 新增此清單的描述。
   * 您可以指定到期日：達到此日期時，清單會被清除並自動刪除。

      ![](assets/list_expiration_date.png)

1. 在 **[!UICONTROL Content]** 索引標籤中，按一下 **[!UICONTROL Add]** 以選取屬於清單的用戶檔案。

   ![](assets/s_ncs_user_add_group.png)

1. 按一下 **[!UICONTROL Save]** 儲存清單。然後，清單便會新增至清單概要中。

您可以按一下 **[!UICONTROL Create]** 直接從「Add profiles」視窗建立新用戶檔案。該用戶檔案將新增至資料庫。

![](assets/s_ncs_user_new_recipient_from_group.png)

如同其他清單，您也可以調整用戶檔案清單的設定。請參 [閱設定清單](../../platform/using/adobe-campaign-workspace.md#configuring-lists)。

## 將資料連結至清單 {#linking-data-to-a-list}

>[!NOTE]
>
>Linking data to a list can only been done with a **[!UICONTROL Group]** type list.

可以將一組用戶檔案的用戶檔案篩選並連結至清單。然後傳遞作業便可傳送到此清單，以鎖定用戶檔案。若要創建用戶檔案群組：

1. 選取用戶檔案並按一下滑鼠右鍵。
1. Select **[!UICONTROL Actions > Associate selection with a list...]**.

   ![](assets/s_ncs_user_add_selection_to_group.png)

1. 選取想要的清單，或使用 **[!UICONTROL Create]** 按鈕建立新的清單，然後按 **[!UICONTROL Next]**。

   ![](assets/s_ncs_user_add_selection_to_group_2.png)

1. Click the **[!UICONTROL Start]** button.

   ![](assets/s_ncs_user_add_selection_to_group_3.png)

The **[!UICONTROL Recreate the list]** option deletes the earlier content from the list. 此模式已經最優化，因為不需查詢確認用戶檔案是否已連結至清單。

If you uncheck the **[!UICONTROL No trace of this job is saved in the database]** option, you can select (or create) the execution folder where the information linked to this process will be stored.

使用視窗的上方區域可監視執行情況。使用 **[!UICONTROL Stop]** 按鈕可停止程序。已處理的連絡人將連結至清單。

您可以透過此操作相關的用戶檔案上的 **[!UICONTROL Lists]** 索引標籤來監視流程：

![](assets/s_ncs_user_add_selection_to_group_4.png)

您也可以經由 Adobe Campaign 首頁來編輯清單：按一下 **[!UICONTROL Profiles and Targets > Lists]** 功能表，然後選取相關的清單。**[!UICONTROL Content]** 索引標籤顯示了連結至此清單的用戶檔案。

![](assets/s_ncs_user_add_selection_to_group_5.png)

## 從清單中移除用戶檔案 {#removing-a-profile-from-a-list}

若要從清單中移除用戶檔案，您可以：

* 編輯清單，在 **[!UICONTROL Content]** 索引標籤中選取用戶檔案，然後按一下 **[!UICONTROL Delete]** 圖示。

   ![](assets/list_remove_a_recipient.png)

* 編輯用戶檔案，按一下 **[!UICONTROL List]** 索引標籤，然後按一下 **[!UICONTROL Delete]** 圖示。

   ![](assets/recipient_remove_a_list.png)

## 刪除用戶檔案清單 {#deleting-a-list-of-profiles}

您可以刪除 Adobe Campaign 樹狀結構清單的群組清單中的一或多個清單。若要執行此操作，請透過 Adobe Campaign 首頁中的 **[!UICONTROL Advanced > Explorer]** 連結編輯樹狀結構清單。選取相關的群組，然後按一下滑鼠右鍵。Select **[!UICONTROL Delete]**. 此時將顯示警告訊息，要求您確認是否刪除。

>[!NOTE]
>
>刪除清單時，清單上的用戶檔案不受影響，但是將更新用戶檔案中的資料。

