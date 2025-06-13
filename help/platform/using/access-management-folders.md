---
product: campaign
title: 管理對Campaign資料夾的存取
description: 瞭解如何授予Campaign資料夾的存取權並建立檢視
badge: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
hide: true
hidefromtoc: true
source-git-commit: b27b85b126e002c0ea8b5d71da1ed60e1e817980
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 2%

---

# 管理對資料夾的存取{#folder-access-management}



Explorer導覽樹狀結構的每個資料夾都附加讀取、寫入和刪除存取許可權。 若要存取檔案，運運算元或運運算元群組至少必須擁有該檔案的讀取存取權。

>[!NOTE]
>
>若要進一步瞭解檔案夾的許可權，請參閱[Campaign v8檔案](https://experienceleague.adobe.com/zh-hant/docs/campaign/campaign-v8/admin/permissions/folder-permissions){target=_blank}。


## 資料夾和檢視 {#folders-and-views}

### 什麼是資料夾 {#about-folders}

資料夾是Adobe Campaign樹狀結構中的節點。 透過&#x200B;**[!UICONTROL Add new folder]**&#x200B;功能表以滑鼠右鍵按一下樹狀結構來建立這些節點。 依預設，第一個選單可讓您新增與目前前後關聯對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

您可以自訂Explorer導覽樹狀結構。 在本節](adobe-campaign-workspace.md)中瞭解設定步驟和最佳實務[。

### 什麼是檢視 {#about-views}

此外，您可以建立檢視來限制對資料的存取，並組織樹狀結構的內容以符合您的需求。 然後，您就可以指派許可權給檢視。

檢視是顯示實際儲存在相同型別的一或多個其他資料夾中的記錄的資料夾。 例如，如果您建立檢視的Campaign資料夾，預設會顯示資料庫中存在的所有行銷活動，無論其來源為何。 然後可以篩選此資料。

將資料夾轉換為檢視時，與資料庫中存在的資料夾型別對應的所有資料都會顯示在檢視中，無論資料夾儲存於哪個資料夾。 然後，您可以篩選它以限制顯示的資料清單。

>[!IMPORTANT]
>
>檢視包含資料並提供存取權，但資料並未實際儲存在檢視資料夾中。 運運算元必須具有資料來源資料夾中所需動作的適當許可權（至少具有讀取存取權）。
>
>若要在不提供來源資料夾存取權的情況下提供檢視的存取權，只要不要提供來源資料夾上層節點的讀取存取權即可。

為了區分檢視和資料夾，每個檢視的名稱都會以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 新增資料夾並建立檢視 {#adding-folders-and-creating-views}

>[!IMPORTANT]
>
>開箱即用的資料夾不應標示為檢視。


在下列範例中，我們將建立新資料夾以顯示特定資料：

1. 建立新的&#x200B;**[!UICONTROL Deliveries]**&#x200B;型別資料夾，並將其命名為&#x200B;**Deliveries France**。
1. 以滑鼠右鍵按一下此資料夾並選取&#x200B;**[!UICONTROL Properties...]**。

   ![熒幕擷圖顯示以滑鼠右鍵進入屬性](assets/s_ncs_user_add_folder_exple.png)

1. 在&#x200B;**[!UICONTROL Restriction]**&#x200B;索引標籤中，選取&#x200B;**[!UICONTROL This folder is a view]**。 然後資料庫中的所有傳遞都會顯示。

   ![熒幕顯示正在勾選的檢視方塊](assets/s_ncs_user_add_folder_exple01.png)

1. 從視窗中間的查詢編輯器定義傳送篩選條件：接著會顯示與已定義篩選對應的行銷活動。

   >[!NOTE]
   >
   >查詢編輯器出現在[此區段](../../platform/using/about-queries-in-campaign.md)中。

   篩選條件：

![顯示不同篩選條件的熒幕擷圖](assets/s_ncs_user_add_folder_exple00.png)

檢視中將顯示下列傳送：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>管理[異動訊息](../../message-center/using/about-transactional-messaging.md)事件時，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;資料夾不得在執行例項上設定為檢視，因為這樣可能會導致存取許可權問題。 如需事件集合的詳細資訊，請參閱[本節](../../message-center/using/about-event-processing.md#event-collection)。

<!--
## Permissions on a folder

### Edit permissions on a folder {#edit-permissions-on-a-folder}

To edit permissions on a specific folder of the tree, follow the steps below:

1. Right-click on the folder and select **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. Click the **[!UICONTROL Security]** tab to view authorizations on this folder.

   ![](assets/s_ncs_user_folder_properties_security.png)

### Modify permissions {#modify-permissions}

To modify permissions, you can:

* **Replace a group or an operator**. To do this, click one of the groups (or operators) with rights to the folder, and select a new group (or a new operator) from the drop-down list:

  ![](assets/s_ncs_user_folder_properties_security02.png)

* **Authorize a group or an operator**. To do this, click the **[!UICONTROL Add]** button and select the group or operator to which you want to assign authorizations for this folder.
* **Forbid a group or an operator**. To do this, click **[!UICONTROL Delete]** and select the group or operator from which you want to remove authorization for this folder.
* **Select the rights assigned to a group or an operator**. To do this, click the group or operator concerned, then select the access rights you want to grant and deselect the others.

  ![](assets/s_ncs_user_folder_properties_security03.png)

### Propagate permissions {#propagate-permissions}

You can propagate authorizations and access rights. To do this, select the **[!UICONTROL Propagate]** option in the folder properties.

The authorizations defined in this window will then be applied to all the sub-folders of the current node. You can then overload these authorizations for each of the sub-folders.

>[!NOTE]
>
>Clearing this option for a folder does not automatically clear it for the sub-folders. You must clear it explicitly for each of the sub-folders.

### Grant access to all operators {#grant-access-to-all-operators}

In the **[!UICONTROL Security]** tab, if the **[!UICONTROL System folder]** option is selected, all operators will have access to this data, regardless of their rights. If this option is cleared, you must explicitly add the operator (or their group) to the list of authorizations in order for them to have access.

![](assets/s_ncs_user_folder_properties_security03b.png)
-->