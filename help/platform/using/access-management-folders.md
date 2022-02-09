---
product: campaign
title: 管理對市場活動資料夾的訪問
description: 瞭解如何授予對市場活動資料夾的訪問權限並建立視圖
feature: Application Settings, Permissions
role: User, Admin
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: f05eefc9945c4ead89eb448b6e28c3523559e055
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 1%

---

# 管理對資料夾的存取{#folder-access-management}

![](../../assets/common.svg)

瀏覽器導航樹的每個資料夾都附加了讀、寫和刪除訪問權限。 要訪問檔案，運算子或運算子組至少必須具有對該檔案的讀訪問權限。

## 資料夾和視圖 {#folders-and-views}

### 什麼是資料夾 {#about-folders}

資料夾是Adobe Campaign樹中的節點。 這些節點是通過以下方式建立的： **[!UICONTROL Add new folder]** 的子菜單。 預設情況下，第一個菜單允許您添加與當前上下文對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

可以自定義瀏覽器導航樹。 瞭解配置步驟和最佳做法 [此部分](adobe-campaign-workspace.md)。

### 什麼是視圖 {#about-views}

此外，您還可以建立視圖，以限制對資料的訪問，並組織樹的內容以滿足您的要求。 然後，可以為視圖分配權限。

視圖是一個資料夾，它顯示物理儲存在一個或多個相同類型的其他資料夾中的記錄。 例如，如果您建立的「市場活動」資料夾是視圖，則預設情況下，它將顯示資料庫中存在的所有市場活動，無論其來源如何。 然後可以過濾此資料。

將資料夾轉換為視圖時，與資料庫中存在的資料夾類型對應的所有資料都會顯示在視圖中，而與保存資料夾的資料夾無關。 然後，可以篩選它以限制顯示的資料清單。

>[!IMPORTANT]
>
>視圖包含資料並提供對其的訪問，但資料不實際儲存在視圖資料夾中。 操作員必須對資料源資料夾中的所需操作具有適當的權限（至少讀訪問權）。
>
>要授予對視圖的訪問權，而不授予對其源資料夾的訪問權限，只需不授予對源資料夾父節點的讀訪問權限即可。

要區分視圖和資料夾，每個視圖的名稱以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 添加資料夾並建立視圖 {#adding-folders-and-creating-views}

在下面的示例中，我們將建立新資料夾以顯示特定資料：

1. 新建 **[!UICONTROL Deliveries]** 類型資料夾，並命名它 **法國**。
1. 按一下右鍵此資料夾並選擇 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在 **[!UICONTROL Restriction]** 索引標籤中，選取 **[!UICONTROL This folder is a view]**。然後將顯示資料庫中的所有交貨。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 從窗口中間部分的查詢編輯器中定義傳遞篩選條件：隨後將顯示與定義的篩選器對應的市場活動。

   >[!NOTE]
   >
   >查詢編輯器在中顯示 [此部分](../../platform/using/about-queries-in-campaign.md)。

   具有以下篩選器條件：

![](assets/s_ncs_user_add_folder_exple00.png)

視圖中將顯示以下交貨：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>管理時 [事務消息](../../message-center/using/about-transactional-messaging.md) 事件、 **[!UICONTROL Real time events]** 或 **[!UICONTROL Batch events]** 不能將資料夾設定為執行實例的視圖，因為這可能導致訪問正確的問題。 有關事件集合的詳細資訊，請參閱 [此部分](../../message-center/using/about-event-processing.md#event-collection)。

## 資料夾權限

### 編輯資料夾的權限 {#edit-permissions-on-a-folder}

要編輯對樹的特定資料夾的權限，請執行以下步驟：

1. 按一下右鍵資料夾並選擇 **[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_folder_properties.png)

1. 按一下 **[!UICONTROL Security]** 頁籤，查看此資料夾的授權。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改權限 {#modify-permissions}

要修改權限，您可以：

* **替換組或運算子**。 要執行此操作，請按一下具有資料夾權限的組（或運算子）之一，然後從下拉清單中選擇新組（或新運算子）:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **授權組或操作員**。 要執行此操作，請按一下 **[!UICONTROL Add]** 按鈕，然後選擇要為此資料夾分配授權的組或運算子。
* **禁止組或運算子**。 要執行此操作，請按一下 **[!UICONTROL Delete]** 並選擇要從中刪除此資料夾授權的組或運算子。
* **選擇分配給組或運算子的權限**。 要執行此操作，請按一下相關組或運算子，然後選擇要授予的訪問權限並取消選擇其他訪問權限。

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 傳播權限 {#propagate-permissions}

您可以傳播授權和訪問權限。 要執行此操作，請選擇 **[!UICONTROL Propagate]** 的子菜單。

然後，此窗口中定義的授權將應用於當前節點的所有子資料夾。 然後，您可以為每個子資料夾重載這些授權。

>[!NOTE]
>
>清除資料夾的此選項不會自動清除子資料夾的選項。 必須為每個子資料夾明確清除它。

### 授予對所有運算子的訪問權限 {#grant-access-to-all-operators}

在 **[!UICONTROL Security]** 的 **[!UICONTROL System folder]** 選項，所有運算子都將有權訪問此資料，而不管其權限如何。 如果清除此選項，則必須將運算子（或其組）顯式添加到授權清單中，以使其具有訪問權限。

![](assets/s_ncs_user_folder_properties_security03b.png)
