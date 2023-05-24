---
product: campaign
title: 清單更新
description: 清單更新
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 2%

---

# 清單更新{#list-update}



A **清單更新** 活動會將轉變中指定的母體儲存在收件者清單中。

![](assets/s_user_segmentation_update_group.png)

可以從現有群組的清單中選取清單。

您也可以使用建立 **[!UICONTROL Create the list if necessary (Computed name)]** 和 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 選項。 這些選項可讓您選取您選擇的標籤來建立清單，以及稍後選取要儲存清單的資料夾。 也可以透過插入動態欄位或指令碼來自動產生標籤。 標籤右側的躍現式選單中有不同的動態欄位。

![](assets/s_user_segmentation_update_list_calc.png)

如果清單已存在，收件者將會新增至現有內容，除非您核取 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 選項。 在此情況下，清單的內容會在更新前刪除。

如果您希望建立或更新後的清單使用收件者表格以外的表格，請核取 **[!UICONTROL Create or use a list with its own table]** 選項。

若要使用選項，必須在您的Adobe Campaign執行個體中設定相關的特定表格。

一般而言，將目標儲存在清單中會標籤工作流程的結尾。 根據預設， **[!UICONTROL List update]** 因此，活動沒有出站轉變。 檢查 **[!UICONTROL Generate an outbound transition]** 選項以新增一個。

![](assets/do-not-localize/how-to-video.png) [在影片中探索如何從檔案總管建立收件者清單](#video)

## 範例：清單更新 {#example--list-update}

在以下範例中，清單更新活動會依循查詢，目標是居住在法國的超過30歲的男性。 清單最初將從查詢結果中建立。 然後，每次從工作流程啟動時都會更新。 例如，它可能會定期用於行銷活動的目標促銷優惠方案。

1. 新增 **[!UICONTROL list update activity]** 在查詢後直接開啟，然後進行編輯。

   有關在工作流程中建立查詢的詳細資訊，請參閱 [查詢](query.md).

1. 您可以為活動選取標籤。
1. 選取 **[!UICONTROL Create the list if necessary (Calculated name)]** 選項來顯示清單將在第一個工作流程執行後建立，然後使用以下執行進行更新。
1. 選取您要儲存清單的資料夾。
1. 輸入清單的標籤。 您可以插入動態欄位，以從清單中自動產生名稱。 在此範例中，清單的名稱與查詢相同，以便輕鬆識別其內容。
1. 離開 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 選項已核取，以刪除不符合目標定位條件的收件者，並將新收件者插入清單中。
1. 另外請將 **[!UICONTROL Create or use a list with its own table]** 選項已核取。
1. 離開 **[!UICONTROL Generate an outbound transition]** 選項未勾選。
1. 按一下 **[!UICONTROL Ok]** 然後開始工作流程。

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   然後會建立或更新相符的收件者清單。

## 輸入引數 {#input-parameters}

* tableName
* 綱要

識別要儲存在群組中的母體。

## 輸出引數 {#output-parameters}

* groupId：群組識別碼。

## 教學課程影片 {#video}

本影片說明如何從檔案總管建立收件者清單。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
