---
solution: Campaign Classic
product: campaign
title: 管理對促銷活動資料夾的存取權
description: 瞭解如何授與Campaign資料夾的存取權並建立檢視
feature: 應用程式設定
role: 業務從業人員、管理員
level: 初學者
translation-type: tm+mt
source-git-commit: b05b8daad449aeb1f5226fdd76744776c6553b63
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 0%

---


# 管理對資料夾的訪問{#folder-access-management}

瀏覽器導航樹的每個資料夾都有附加的讀取、寫入和刪除訪問權限。 若要存取檔案，運算元或運算元群組至少必須具有讀取存取權。

## 資料夾和視圖{#folders-and-views}

### 什麼是資料夾{#about-folders}

資料夾是Adobe Campaign樹中的節點。 通過按一下右鍵樹，通過&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜單建立這些節點。 依預設，第一個功能表可讓您新增與目前內容對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

您可以自訂Explorer導覽樹狀結構。 在本節](adobe-campaign-workspace.md)中瞭解配置步驟和最佳實踐[。

### 什麼是視圖{#about-views}

此外，您還可以建立檢視，以限制資料存取，並組織樹狀結構的內容以符合您的需求。 然後，您可以指派檢視的權限。

視圖是一個資料夾，它顯示物理儲存在一個或多個相同類型的其他資料夾中的記錄。 例如，如果您建立的「促銷活動」資料夾是檢視，則預設會顯示資料庫中顯示的所有促銷活動，無論其來源為何。 然後可以篩選此資料。

將資料夾轉換為視圖時，與資料庫中存在的資料夾類型相對應的所有資料都會顯示在視圖中，而與保存資料夾無關。 然後，您可以篩選它，以限制顯示的資料清單。

>[!IMPORTANT]
>
>這些視圖包含資料並提供對其的訪問，但資料不實際儲存在視圖資料夾中。 運算子必須擁有資料來源資料夾中所需動作的適當權限（至少是讀取存取）。
>
>要在不授予對其源資料夾訪問權限的情況下授予對視圖的訪問權限，只要不授予對源資料夾父節點的讀訪問權限即可。

要區分視圖和資料夾，每個視圖的名稱以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 添加資料夾並建立視圖{#adding-folders-and-creating-views}

在以下範例中，我們將建立新資料夾以顯示特定資料：

1. 建立新的&#x200B;**[!UICONTROL Deliveries]**&#x200B;類型資料夾，並將它命名為&#x200B;**Deliveries France**。
1. 按一下右鍵此資料夾並選擇&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在 **[!UICONTROL Restriction]** 索引標籤中，選取 **[!UICONTROL This folder is a view]**。然後會顯示資料庫中的所有傳送。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 從視窗中間區段的查詢編輯器定義傳送篩選條件：接著會顯示與已定義篩選器對應的促銷活動。

   >[!NOTE]
   >
   >查詢編輯器顯示在[此部分](../../platform/using/about-queries-in-campaign.md)中。

   使用下列篩選條件：

![](assets/s_ncs_user_add_folder_exple00.png)

檢視中將顯示下列傳送：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>在管理[事務性消息傳遞](../../message-center/using/about-transactional-messaging.md)事件時，**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;資料夾不能設定為執行實例的視圖，因為這可能導致訪問權限問題。 如需事件收集的詳細資訊，請參閱[本節](../../message-center/using/event-collection.md)。



## 資料夾的權限

### 編輯資料夾{#edit-permissions-on-a-folder}的權限

要編輯對樹的特定資料夾的權限，請執行以下步驟：

1. 按一下右鍵資料夾並選擇&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_folder_properties.png)

1. 按一下&#x200B;**[!UICONTROL Security]**&#x200B;頁籤查看此資料夾的授權。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改權限{#modify-permissions}

若要修改權限，您可以：

* **取代群組或運算子**。若要這麼做，請按一下其中一個具有資料夾權限的群組（或運算子），然後從下拉式清單中選取新群組（或新運算子）:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **授權群組或營運商**。要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後選擇要為此資料夾分配授權的組或運算子。
* **禁止群組或營運商**。若要這麼做，請按一下&#x200B;**[!UICONTROL Delete]**&#x200B;並選取您要移除此資料夾授權的群組或運算子。
* **選擇指派給群組或運算子的權限**。若要這麼做，請按一下相關的群組或運算子，然後選取您要授與的存取權，並取消選取其他的存取權。

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 傳播權限{#propagate-permissions}

您可以傳播授權和訪問權限。 要執行此操作，請在資料夾屬性中選擇&#x200B;**[!UICONTROL Propagate]**&#x200B;選項。

然後，在此窗口中定義的授權將應用於當前節點的所有子資料夾。 然後，您可以對每個子資料夾超載這些授權。

>[!NOTE]
>
>清除資料夾的此選項不會自動清除子資料夾的選項。 您必須明確清除每個子資料夾。

### 授予對所有運算子{#grant-access-to-all-operators}的訪問權限

在&#x200B;**[!UICONTROL Security]**&#x200B;標籤中，如果選取&#x200B;**[!UICONTROL System folder]**&#x200B;選項，所有運算子都可存取此資料，不論其權限為何。 如果清除此選項，您必須將運算子（或其群組）明確新增至授權清單，以便其擁有存取權。

![](assets/s_ncs_user_folder_properties_security03b.png)
