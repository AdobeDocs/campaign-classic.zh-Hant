---
product: campaign
title: 管理用戶檔案
description: 管理用戶檔案
feature: Profiles
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 26%

---

# 管理輪廓{#managing-profiles}



## 收件者樹狀結構清單 {#recipient-tree}

若要存取進階收件者管理功能，您需要編輯Adobe Campaign樹狀結構。 若要這麼做，請按一下工具列中的&#x200B;**[!UICONTROL Explorer]**&#x200B;按鈕。

依預設，收件者會儲存在Adobe Campaign樹狀結構的&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;節點中。 在相同的節點中，您可以建立一或多個資料夾和子資料夾來儲存收件者用戶檔案。

每個節點都會與一個資料夾重合。 必須將每個資料夾中的資料視為彼此分割。 也就是說，在多個收件者資料夾中管理重複項目將更加棘手。

>[!NOTE]
>
>若要顯示資料庫中所有收件者的清單，您必須建立檢視。 深入瞭解[資料夾和檢視](../../platform/using/access-management-folders.md)。

## 移動收件者 {#moving-recipients}

您可以選取一或多個收件者，從收件者清單中將其拖曳，然後放置到所需的資料夾中。 將顯示一條警告訊息，要求您確認此動作。

## 複製收件者 {#copying-a-recipient}

您可以用滑鼠右鍵按一下所要的收件者並選取&#x200B;**[!UICONTROL Copy]**，以複製相同資料夾中的收件者。

## 刪除收件者 {#deleting-recipients}

若要刪除收件者，請將他們移至特定資料夾，然後清除此資料夾的內容。 **強烈建議不要在此情況下使用** **[!UICONTROL Delete]**&#x200B;選項。

若要清除資料夾，請使用&#x200B;**[!UICONTROL Actions > Purge folder]**&#x200B;功能表，以滑鼠右鍵按一下所要的資料夾來存取。

![](assets/s_ncs_user_purge_folder.png)

按一下&#x200B;**[!UICONTROL Start]**&#x200B;以啟動作業。 視窗的中間區域會顯示處理進度狀態，如下所示：

![](assets/s_ncs_user_purge_folder_start.png)
