---
product: campaign
title: 更新資料
description: 更新資料
feature: Data Management
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: platform
content-type: reference
topic-tags: profile-management
exl-id: f7dfbc22-4ac3-4b61-927f-34ecc4e35154
source-git-commit: 3a9b21d626b60754789c3f594ba798309f62a553
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 35%

---

# 更新資料{#updating-data}



可以手動或自動更新連結至收件者用戶檔案的資料。

## 設定自動更新 {#setting-up-an-automatic-update}

可透過工作流程設定自動更新。 如需詳細資訊，請參閱[本章節](../../workflow/using/update-data.md)。

## 執行大量更新 {#performing-a-mass-update}

若要執行手動更新，請在選取的收件者上按一下滑鼠右鍵，使用 **[!UICONTROL Actions]** 快捷選單，或使用 **[!UICONTROL Actions]** 圖示。

![](assets/s_ncs_user_action_icon.png)

有兩種型別的更新：大量更新一組收件者，以及兩個設定檔之間的資料合併。 針對每個動作，使用精靈可協助您設定更新。

### 大量更新 {#mass-update}

若要大量更新，請使用 **[!UICONTROL Action > Mass update of selected lines...]**. 此精靈可協助您設定並執行更新。

精靈的第一步驟是指定要更新的欄位。

精靈的左側區段會顯示可用欄位清單。 使用 **[!UICONTROL Find]** 欄位以搜尋這些欄位。 按下 **輸入** 鍵以瀏覽清單。 符合您輸入內容的欄位名稱會以粗體顯示，如下所示。

連按兩下要更新的欄位，以在精靈的右側區域顯示它們。

![](assets/s_ncs_user_update_wizard01_1.png)

發生錯誤時，請使用 **[!UICONTROL Delete]** 按鈕以從要更新的欄位清單中刪除欄位。

選取或輸入值以套用至要更新之用戶檔案。

![](assets/s_ncs_user_update_wizard01_12.png)

您可以按一下 **[!UICONTROL Distribution of values]** 顯示目前資料夾中存在的收件者（不僅僅是受更新影響的收件者）所選欄位值的分佈情況。

![](assets/s_ncs_user_update_wizard01_2.png)

您可以定義篩選器以顯示此視窗中的值分佈，或修改目前檔案夾以顯示另一個檔案夾中的值分佈。 這些操作是唯讀動作，不影義所定義的更新設定。

![](assets/s_ncs_user_update_wizard01_3.png)

關閉此視窗並按一下 **[!UICONTROL Next]** 以顯示第二個更新精靈步驟。 在此步驟中，您可以按一下來啟動更新 **[!UICONTROL Start]**.

![](assets/s_ncs_user_update_wizard01_4.png)

更新執行的相關資訊會顯示在精靈的上方區域中。

此 **[!UICONTROL Stop]** 可讓您取消更新，但某些記錄可能已更新，停止程式將不會取消這些更新。 進度列會顯示操作目前的進度。

### 合併資料 {#merge-data}

選取 **[!UICONTROL Merge selected lines...]** 以啟動兩個收件者設定檔的合併。 在選取選項之前，必須先選取要合併的設定檔。 使用精靈來設定和開始合併。

精靈會顯示要針對在一個或其他來源設定檔中完成的每個欄位擷取的值。 如果要合併的設定檔中一或多個欄位的值不同，則它們會顯示在 **[!UICONTROL List of conflicts]** 區段。 然後，您可以使用清單下方的選項按鈕來選取預設用戶檔案，如下列範例所示：

![](assets/s_ncs_user_merge_wizard01_1.png)

按一下 **[!UICONTROL Compute]** 以顯示您選擇的結果。

![](assets/s_ncs_user_merge_wizard01_2.png)

檢查 **[!UICONTROL Result]** 視窗兩個區段的欄，然後按一下 **[!UICONTROL Finish]** 以執行合併。

## 匯出資料 {#exporting-data}

清單的內容可以匯出。 若要設定並執行匯出：

1. 選取要匯出的記錄。
1. 按一下右鍵並選取 **[!UICONTROL Export...]**.

   ![](assets/s_ncs_user_export_list.png)

1. 然後選取要擷取的資料。 根據預設，所有顯示的欄會新增至輸出欄。

   ![](assets/s_ncs_user_export_list_start.png)

   有關如何設定匯出精靈的詳細資訊，請參閱 [本節](../../platform/using/executing-export-jobs.md).

## 訂閱服務 {#subscribing-to-a-service}

多數情況下，收件者會透過專用的登陸頁面訂閱電子報，如中所述 [本節](../../delivery/using/managing-subscriptions.md). 不過，篩選的收件者的設定檔可以手動訂閱服務（電子報或病毒式服務）。 操作步驟：

1. 選取您想要訂閱服務的收件者，然後按一下滑鼠右鍵。
1. 選取 **[!UICONTROL Actions > Subscribe selection to a service]**。

   ![](assets/s_ncs_user_selection_subscribe_service.png)

1. 選取所需的服務，然後按一下 **[!UICONTROL Next]**：

   ![](assets/s_ncs_user_selection_subscribe_service_2.png)

   >[!NOTE]
   >
   >此編輯器可讓您建立新服務：按一下 **[!UICONTROL Create]** 按鈕。

1. 您可以 **[!UICONTROL Send a confirmation message]** 收件者。 可在與所選服務相連結的訂閱場景中設定此訊息的內容。
1. 按一下 **[!UICONTROL Start]** 按鈕以執行訂閱程式。

   ![](assets/s_ncs_user_selection_subscribe_service_3.png)

視窗的上半段可讓您監視執行流程。 此 **[!UICONTROL Stop]** 按鈕可讓您停止此程式。 不過，已處理之收件者將訂閱服務。

如果您取消核取 **[!UICONTROL Do not keep a trace of this job in the database]** 選項，您可以選取（或建立）執行資料夾，此程式上的資訊將儲存於此資料夾。

若要檢查程式，請移至 **[!UICONTROL Subscriptions]** 索引標籤上的收件者設定檔，或 **[!UICONTROL Subscriptions]** 索引標籤是透過 **[!UICONTROL Profiles and Targets > Services and Subscriptions]** 節點。

![](assets/s_ncs_user_selection_subscribe_service_4.png)

>[!NOTE]
>
>如需建立和設定資訊服務的詳細資訊，請參閱[本頁面](../../delivery/using/managing-subscriptions.md)。
