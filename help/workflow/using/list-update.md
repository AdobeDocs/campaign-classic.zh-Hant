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

可從現有組清單中選擇該清單。

您也可以使用 **[!UICONTROL Create the list if necessary (Computed name)]** 和 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 選項。 這些選項可讓您選取所選的標籤，以建立清單，之後再建立要儲存清單的資料夾。 您也可以插入動態欄位或指令碼，自動產生標籤。 標籤右側的快顯功能表中提供不同的動態欄位。

![](assets/s_user_segmentation_update_list_calc.png)

如果清單已存在，收件者將新增至現有內容，除非您勾選 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 選項。 在這種情況下，清單的內容會在更新前刪除。

如果希望建立或更新的清單使用收件者表格以外的表格，請核取 **[!UICONTROL Create or use a list with its own table]** 選項。

若要使用選項，您的Adobe Campaign例項中必須已設定相關的特定表格。

通常，將目標儲存在清單中會標籤工作流程的結尾。 依預設， **[!UICONTROL List update]** 活動因此沒有出站轉變。 檢查 **[!UICONTROL Generate an outbound transition]** 選項來新增。

![](assets/do-not-localize/how-to-video.png) [了解如何從影片中的檔案總管建立收件者清單](#video)

## 範例：清單更新 {#example--list-update}

在下列範例中，清單更新活動會依循查詢，鎖定居住在法國超過30歲的男性。 清單最初將從查詢結果中建立。 然後，每當從工作流程啟動時，就會更新它。 例如，它可定期用於促銷活動的目標促銷優惠。

1. 新增 **[!UICONTROL list update activity]** 直接在查詢後開啟，然後加以編輯。

   如需在工作流程中建立查詢的詳細資訊，請參閱 [查詢](query.md).

1. 您可以為活動選取標籤。
1. 選取 **[!UICONTROL Create the list if necessary (Calculated name)]** 選項，顯示執行第一個工作流程後將建立清單，然後以下列執行更新。
1. 選擇要保存清單的資料夾。
1. 輸入清單的標籤。 您可以插入動態欄位，以自動從清單產生名稱。 在此範例中，清單與查詢同名，可輕鬆識別其內容。
1. 保留 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 選項，刪除不符合定位條件的收件者，並將新收件者插入清單中。
1. 同時將 **[!UICONTROL Create or use a list with its own table]** 選項。
1. 保留 **[!UICONTROL Generate an outbound transition]** 選項。
1. 按一下 **[!UICONTROL Ok]** 然後啟動工作流程。

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   然後會建立或更新相符的收件者清單。

## 輸入參數 {#input-parameters}

* tableName
* 綱要

識別要儲存在群組中的母體。

## 輸出參數 {#output-parameters}

* groupId:群組識別碼。

## 教學課程影片 {#video}

此影片說明如何從檔案總管建立收件者清單。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

提供其他Campaign Classic作法影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
