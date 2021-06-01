---
product: campaign
title: 清單更新
description: 清單更新
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: fcc51131-15d0-4d39-95cb-371d7044373b
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 2%

---

# 清單更新{#list-update}

**清單更新**&#x200B;活動將轉變中指定的母體儲存在收件者清單中。

![](assets/s_user_segmentation_update_group.png)

可從現有組清單中選擇該清單。

也可使用&#x200B;**[!UICONTROL Create the list if necessary (Computed name)]**&#x200B;和&#x200B;**[!UICONTROL Create the list if necessary (Computed Folder and Name)]**&#x200B;選項來建立。 這些選項可讓您選取所選的標籤，以建立清單，之後再建立要儲存清單的資料夾。 您也可以插入動態欄位或指令碼，自動產生標籤。 標籤右側的快顯功能表中提供不同的動態欄位。

![](assets/s_user_segmentation_update_list_calc.png)

如果清單已存在，則收件者將被添加到現有內容，除非您勾選&#x200B;**[!UICONTROL Purge the list if it exists (otherwise add to the list)]**&#x200B;選項。 在這種情況下，清單的內容會在更新前刪除。

如果希望建立或更新的清單使用收件者表格以外的表格，請核取&#x200B;**[!UICONTROL Create or use a list with its own table]**&#x200B;選項。

若要使用選項，您的Adobe Campaign例項中必須已設定相關的特定表格。

通常，將目標儲存在清單中會標籤工作流程的結尾。 因此，預設情況下，**[!UICONTROL List update]**&#x200B;活動沒有出站轉變。 勾選&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項以新增選項。

![](assets/do-not-localize/how-to-video.png) [了解如何從影片中的檔案總管建立收件者清單](#video)

## 範例：清單更新{#example--list-update}

在下列範例中，清單更新活動會依循查詢，鎖定居住在法國超過30歲的男性。 清單最初將從查詢結果中建立。 然後，每當從工作流程啟動時，就會更新它。 例如，它可定期用於促銷活動的目標促銷優惠。

1. 直接在查詢後新增&#x200B;**[!UICONTROL list update activity]**，然後開啟它以進行編輯。

   有關在工作流中建立查詢的詳細資訊，請參閱[Query](../../workflow/using/query.md)。

1. 您可以為活動選取標籤。
1. 選取&#x200B;**[!UICONTROL Create the list if necessary (Calculated name)]**&#x200B;選項，顯示第一個工作流程執行完畢後將建立清單，然後以下列執行更新。
1. 選擇要保存清單的資料夾。
1. 輸入清單的標籤。 您可以插入動態欄位，以自動從清單產生名稱。 在此範例中，清單與查詢同名，可輕鬆識別其內容。
1. 保留&#x200B;**[!UICONTROL Purge the list if it exists (otherwise add to the list)]**&#x200B;選項為已核取狀態，以刪除不符合目標准則的收件者，並將新收件者插入清單中。
1. 同時保留&#x200B;**[!UICONTROL Create or use a list with its own table]**&#x200B;選項為已核取狀態。
1. 保留&#x200B;**[!UICONTROL Generate an outbound transition]**&#x200B;選項未勾選。
1. 按一下&#x200B;**[!UICONTROL Ok]**，然後啟動工作流。

   ![](assets/s_user_segmentation_update_list_calc_example.png)

   然後會建立或更新相符的收件者清單。

## 輸入參數{#input-parameters}

* tableName
* 綱要

識別要儲存在群組中的母體。

## 輸出參數{#output-parameters}

* groupId:群組識別碼。

## 教學課程影片 {#video}

此影片說明如何從檔案總管建立收件者清單。

>[!VIDEO](https://video.tv.adobe.com/v/25602/quality=12)

其他Campaign Classic操作說明影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
