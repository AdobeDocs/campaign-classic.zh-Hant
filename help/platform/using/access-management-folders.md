---
product: campaign
title: 管理對Campaign資料夾的存取
description: 瞭解如何授與對Campaign資料夾的存取權並建立檢視
badge: label="v7" type="資訊性" tooltip="僅適用於Campaign Classicv7"
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 1%

---

# 管理對資料夾的存取{#folder-access-management}



Explorer導覽樹狀結構的每個資料夾都附加了讀取、寫入和刪除存取許可權。 若要存取檔案，運運算元或運運算元群組至少必須擁有該檔案的讀取存取權。

## 資料夾和檢視 {#folders-and-views}

### 什麼是資料夾 {#about-folders}

資料夾是Adobe Campaign樹狀結構中的節點。 建立這些節點的方法為透過以下方式以滑鼠右鍵按一下樹狀結構： **[!UICONTROL Add new folder]** 功能表。 依預設，第一個選單可讓您新增與目前前後關聯對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

您可以自訂瀏覽器導覽樹狀結構。 瞭解設定步驟和最佳實務 [在本節中](adobe-campaign-workspace.md).

### 什麼是檢視 {#about-views}

此外，您可以建立檢視來限制對資料的存取，並組織樹狀結構的內容以符合您的需求。 然後您可以指派許可權給檢視。

檢視是顯示實際儲存在相同型別的一或多個其他資料夾中的記錄的資料夾。 例如，如果您建立檢視的Campaign資料夾，預設會顯示資料庫中存在的所有行銷活動，無論其來源為何。 然後可以篩選此資料。

將資料夾轉換為檢視時，與資料庫中存在的資料夾型別對應的所有資料都會顯示在檢視中，無論資料夾儲存於哪個資料夾。 然後，您可以篩選該區段，以限制顯示的資料清單。

>[!IMPORTANT]
>
>檢視包含資料並提供存取權，但資料並未實際儲存在檢視資料夾中。 運運算元必須在資料來源資料夾中擁有所需動作的適當許可權（至少具有讀取存取權）。
>
>若要在不提供來源資料夾存取權的情況下提供檢視存取權，只要不提供來源資料夾上層節點的讀取存取權即可。

為了區分檢視和資料夾，每個檢視的名稱都會以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 新增資料夾並建立檢視 {#adding-folders-and-creating-views}

在下列範例中，我們將建立新資料夾以顯示特定資料：

1. 建立新的 **[!UICONTROL Deliveries]** 輸入資料夾並為其命名 **傳遞法國**.
1. 以滑鼠右鍵按一下此資料夾並選取 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在 **[!UICONTROL Restriction]** 索引標籤中，選取 **[!UICONTROL This folder is a view]**。然後會顯示資料庫中的所有傳送。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 從視窗中間的查詢編輯器定義傳遞篩選條件：接著會顯示與已定義篩選對應的行銷活動。

   >[!NOTE]
   >
   >查詢編輯器顯示於 [本節](../../platform/using/about-queries-in-campaign.md).

   篩選條件為：

![](assets/s_ncs_user_add_folder_exple00.png)

檢視中將顯示下列傳送：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>管理時 [異動訊息傳送](../../message-center/using/about-transactional-messaging.md) 事件， **[!UICONTROL Real time events]** 或 **[!UICONTROL Batch events]** 資料夾不得被設定為執行個體的檢視，因為這可能會導致存取許可權問題。 如需事件集合的詳細資訊，請參閱 [本節](../../message-center/using/about-event-processing.md#event-collection).

## 檔案夾的許可權

### 編輯檔案夾的許可權 {#edit-permissions-on-a-folder}

若要編輯樹狀結構之特定資料夾的許可權，請遵循下列步驟：

1. 以滑鼠右鍵按一下資料夾並選取 **[!UICONTROL Properties...]**.

   ![](assets/s_ncs_user_folder_properties.png)

1. 按一下 **[!UICONTROL Security]** 標籤以檢視此資料夾的授權。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改許可權 {#modify-permissions}

若要修改許可權，您可以：

* **取代群組或運運算元**. 若要這麼做，請按一下其中一個具有資料夾許可權的群組（或運運算元），然後從下拉式清單中選取新群組（或新運運算元）：

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **授權群組或操作員**. 若要這麼做，請按一下 **[!UICONTROL Add]** 按鈕並選取您要為此資料夾指派授權的群組或運運算元。
* **禁止群組或操作員**. 若要這麼做，請按一下 **[!UICONTROL Delete]** 並選取您要從中移除此資料夾授權的群組或運運算元。
* **選取指派給群組或操作員的許可權**. 若要這麼做，請按一下相關的群組或運運算元，然後選取您要授與的存取許可權，並取消選取其他許可權。

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 傳播許可權 {#propagate-permissions}

您可以傳播授權和存取許可權。 若要這麼做，請選取 **[!UICONTROL Propagate]** 資料夾屬性中的選項。

然後此視窗中定義的授權將套用至目前節點的所有子資料夾。 然後，您就可以為每個子資料夾多載這些授權。

>[!NOTE]
>
>為資料夾清除此選項並不會自動為子資料夾清除它。 您必須為每個子資料夾明確清除它。

### 授與存取權給所有運運算元 {#grant-access-to-all-operators}

在 **[!UICONTROL Security]** 標籤，如果 **[!UICONTROL System folder]** 選項時，無論操作員的許可權為何，所有操作員都將可存取此資料。 如果清除此選項，您必須明確將運運算元（或其群組）新增至授權清單，才能讓運運算元擁有存取權。

![](assets/s_ncs_user_folder_properties_security03b.png)
