---
solution: Campaign Classic
product: campaign
title: 管理對Campaign資料夾的存取
description: 了解如何授與Campaign資料夾的存取權並建立檢視
feature: 應用程式設定
role: Business Practitioner, Administrator
level: Beginner
exl-id: 0ba8a3d0-36d7-42f3-b281-0255e49b5fa3
source-git-commit: b211948f1b6a64d0734d1d23f6df4951af88445a
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 1%

---

# 管理對資料夾的存取{#folder-access-management}

瀏覽器導航樹的每個資料夾都具有附加的讀取、寫入和刪除訪問權限。 若要存取檔案，運算子或運算子群組必須至少具有檔案的讀取存取權。

## 資料夾和視圖{#folders-and-views}

### 什麼是資料夾{#about-folders}

資料夾是Adobe Campaign樹中的節點。 通過&#x200B;**[!UICONTROL Add new folder]**&#x200B;菜單按一下右鍵樹可建立這些節點。 依預設，第一個功能表可讓您新增與目前內容對應的資料夾。

![](assets/s_ncs_user_add_folder_in_tree.png)

您可以自訂Explorer導覽樹。 在本小節](adobe-campaign-workspace.md)中了解配置步驟和最佳實踐[。

### 什麼是檢視{#about-views}

此外，您可以建立檢視，以限制對資料的存取，並組織樹狀結構的內容以符合您的需求。 然後，您可以指派檢視的權限。

視圖是一個資料夾，它顯示物理上儲存在同一類型的一個或多個其他資料夾中的記錄。 例如，如果您建立一個作為檢視的促銷活動資料夾，它會依預設顯示資料庫中存在的所有促銷活動，無論其來源為何。 然後可以篩選此資料。

將資料夾轉換為視圖時，與資料庫中存在的資料夾類型對應的所有資料都顯示在視圖中，而與保存資料夾的資料夾無關。 接著，您可以篩選它，以限制顯示的資料清單。

>[!IMPORTANT]
>
>檢視包含資料並提供存取權，但資料不會實際儲存在檢視資料夾中。 運算子必須擁有資料源資料夾中所需動作的適當權限（至少讀取存取權）。
>
>要在不授予其源資料夾訪問權限的情況下授予對視圖的訪問權限，只需不授予源資料夾的父節點的讀訪問權限。

為了區分視圖和資料夾，每個視圖的名稱以不同的顏色（深青色）顯示。

![](assets/s_ncs_user_view_name_color.png)

### 添加資料夾並建立視圖{#adding-folders-and-creating-views}

在以下範例中，我們將建立新資料夾以顯示特定資料：

1. 建立新的&#x200B;**[!UICONTROL Deliveries]**&#x200B;類型資料夾，並將其命名為&#x200B;**Deliveries France**。
1. 按一下右鍵此資料夾，然後選擇&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_add_folder_exple.png)

1. 在 **[!UICONTROL Restriction]** 索引標籤中，選取 **[!UICONTROL This folder is a view]**。之後，資料庫中的所有傳送都會顯示。

   ![](assets/s_ncs_user_add_folder_exple01.png)

1. 從視窗中間區段的查詢編輯器中定義傳送篩選條件：接著會顯示與已定義篩選相對應的促銷活動。

   >[!NOTE]
   >
   >查詢編輯器顯示在[此部分](../../platform/using/about-queries-in-campaign.md)中。

   具有下列篩選條件：

![](assets/s_ncs_user_add_folder_exple00.png)

檢視中將顯示下列傳送：

![](assets/s_ncs_user_add_folder_exple02.png)

>[!NOTE]
>
>管理[交易式訊息](../../message-center/using/about-transactional-messaging.md)事件時，不能將&#x200B;**[!UICONTROL Real time events]**&#x200B;或&#x200B;**[!UICONTROL Batch events]**&#x200B;資料夾設定為執行例項的檢視，因為這可能導致存取權限問題。 如需事件集合的詳細資訊，請參閱[此區段](../../message-center/using/about-event-processing.md#event-collection)。

## 資料夾的權限

### 編輯資料夾{#edit-permissions-on-a-folder}的權限

要編輯樹的特定資料夾的權限，請執行以下步驟：

1. 按一下右鍵資料夾，然後選擇&#x200B;**[!UICONTROL Properties...]**。

   ![](assets/s_ncs_user_folder_properties.png)

1. 按一下&#x200B;**[!UICONTROL Security]**&#x200B;頁簽查看此資料夾上的授權。

   ![](assets/s_ncs_user_folder_properties_security.png)

### 修改權限{#modify-permissions}

若要修改權限，您可以：

* **取代群組或運算子**。要執行此操作，請按一下其中一個具有資料夾權限的群組（或運算子），然後從下拉式清單中選取新群組（或新運算子）:

   ![](assets/s_ncs_user_folder_properties_security02.png)

* **授權群組或運算子**。要執行此操作，請按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕並選擇要為此資料夾分配授權的組或運算子。
* **禁止組或操作員**。要執行此操作，請按一下&#x200B;**[!UICONTROL Delete]**&#x200B;並選擇要從中刪除此資料夾授權的組或運算子。
* **選取指派給群組或運算子的權限**。要執行此操作，請按一下相關的組或運算子，然後選擇要授予的訪問權限並取消選擇其他訪問權限。

   ![](assets/s_ncs_user_folder_properties_security03.png)

### 傳播權限{#propagate-permissions}

您可以傳播授權和訪問權限。 要執行此操作，請在資料夾屬性中選取&#x200B;**[!UICONTROL Propagate]**&#x200B;選項。

然後，此窗口中定義的授權將應用於當前節點的所有子資料夾。 然後，您就可以為每個子資料夾過載這些授權。

>[!NOTE]
>
>清除資料夾的此選項不會自動清除子資料夾的選項。 您必須為每個子資料夾明確清除它。

### 授予所有運算子的訪問權限{#grant-access-to-all-operators}

在&#x200B;**[!UICONTROL Security]**&#x200B;標籤中，如果選取&#x200B;**[!UICONTROL System folder]**&#x200B;選項，則所有運算子都將有權存取此資料，無論其權限為何。 如果清除了此選項，則必須將運算子（或其組）顯式添加到授權清單中，以便它們具有訪問權限。

![](assets/s_ncs_user_folder_properties_security03b.png)
