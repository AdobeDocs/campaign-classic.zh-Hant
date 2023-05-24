---
product: campaign
title: 管理設定檔
description: 管理設定檔
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: e1d0556a-6f30-4863-9025-eb9c1b8b53d3
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 94%

---

# 管理設定檔{#managing-profiles}



## 收件者樹狀結構清單 {#recipient-tree}

若要存取進階的收件者管理功能，您必須編輯 Adobe Campaign 樹狀結構清單。若要執行這項操作，請按一下工具列中的 **[!UICONTROL Explorer]** 按鈕。

根據預設，收件者會儲存在 Adobe Campaign 樹狀結構清單的 **[!UICONTROL Profiles and targets]** 節點中。在相同的節點中，您可以建立一或多個資料夾和子資料夾來儲存收件者用戶檔案。

每個節點都與一個資料夾重合。每個資料夾的資料都必須被視為彼此分區。也就是說，在多個收件者資料夾中管理重複項目將更加棘手。

>[!NOTE]
>
>若要顯示資料庫中所有收件者的清單，您必須建立一個檢視畫面。進一步瞭解 [資料夾和檢視](../../platform/using/access-management-folders.md).

## 移動收件者 {#moving-recipients}

您可以選取一位或多位收件者，從收件者清單拖曳收件者，並將它們放在想要的資料夾中。將顯示一條警告訊息，要求您確認此動作。

## 複製收件者 {#copying-a-recipient}

您可以複製同一資料夾中的收件者，方法是在所需的收件者上按一下滑鼠右鍵，然後選取 **[!UICONTROL Copy]**。

## 刪除收件者 {#deleting-recipients}

若要刪除收件者，請將它們移至特定資料夾，然後清除此資料夾的內容。**強烈建議您不要使用** 此處的 **[!UICONTROL Delete]** 選項。

若要清除資料夾，請在需要清除的資料夾上按一下滑鼠右鍵，以使用 **[!UICONTROL Actions > Purge folder]** 選單。

![](assets/s_ncs_user_purge_folder.png)

按一下 **[!UICONTROL Start]** 以執行操作。視窗的中間區域會顯示處理進度狀態，如下所示：

![](assets/s_ncs_user_purge_folder_start.png)
