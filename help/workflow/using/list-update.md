---
title: 清單更新
seo-title: 清單更新
description: 清單更新
seo-description: null
page-status-flag: never-activated
uuid: 1446f115-3f64-4b95-8e04-6426ab1b8dab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: targeting-activities
discoiquuid: ca2cd5bf-78a2-4e43-955d-206f4474d1e0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: b1a961822224ab0a9551f51942a5f94cf201c8ee
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# 清單更新{#list-update}

清單 **更新** (List update)活動會將轉場中指定的人口儲存在收件者清單中。

![](assets/s_user_segmentation_update_group.png)

可從現有組清單中選擇該清單。

您也可以使用和選項來 **[!UICONTROL Create the list if necessary (Computed name)]** 建立 **[!UICONTROL Create the list if necessary (Computed Folder and Name)]** 它。 這些選項允許您選擇所選的標籤以建立清單，以及以後將保存清單的資料夾。 您也可以插入動態欄位或指令碼，自動產生標籤。 標籤右側的彈出式選單中提供不同的動態欄位。

![](assets/s_user_segmentation_update_list_calc.png)

如果清單已存在，收件者將會新增至現有內容，除非您勾選此選 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 項。 在這種情況下，清單的內容會在更新前刪除。

如果希望建立或更新的清單使用收件人表以外的表，則選中該 **[!UICONTROL Create or use a list with its own table]** 選項。

若要使用此選項，您必須在Adobe Campaign例項中設定相關的特定表格。

通常，將目標儲存在清單中會標示工作流程的結束。 因此，預設情況下， **[!UICONTROL List update]** 活動不具有出站轉換。 勾選 **[!UICONTROL Generate an outbound transition]** 新增選項。

## 範例： 清單更新 {#example--list-update}

在以下範例中，清單更新活動會遵循查詢，以法國30歲以上的男性為目標。 清單最初會從查詢結果建立。 然後，每當從工作流程啟動時，就會更新它。 例如，它可定期用於促銷活動的定位促銷優惠。

1. 直接在查 **[!UICONTROL list update activity]** 詢之後新增，然後將其開啟以進行編輯。

   有關在工作流中建立查詢的詳細資訊，請參閱 [查詢](../../workflow/using/query.md)。

1. 您可以為活動選擇標籤。
1. 選取 **[!UICONTROL Create the list if necessary (Calculated name)]** 選項，以顯示清單將在第一個工作流程執行後建立，然後以下列執行更新。
1. 選擇要保存清單的資料夾。
1. 輸入清單的標籤。 您可以插入動態欄位，自動從清單中產生名稱。 在此範例中，清單與查詢的名稱相同，可輕鬆識別其內容。
1. 將選 **[!UICONTROL Purge the list if it exists (otherwise add to the list)]** 取的選項保留為刪除不符合定位標準的收件者，並將新收件者插入清單。
1. 同時，將選 **[!UICONTROL Create or use a list with its own table]** 項保留為選中。
1. 保留選 **[!UICONTROL Generate an outbound transition]** 項未選中。
1. 按一 **[!UICONTROL Ok]** 下，然後啟動工作流程。

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   然後會建立或更新相符的收件者清單。

如需詳細資訊，請參閱「建立收 [件者清單」影片](https://docs.campaign.adobe.com/doc/AC/en/Videos/Videos.html) 。

## 輸入參數 {#input-parameters}

* tableName
* 架構

標識要保存在組中的人口。

## 輸出參數 {#output-parameters}

* groupId: 群組識別碼。
