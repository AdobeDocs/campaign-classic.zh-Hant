---
title: 使用工作流建立配置檔案清單
seo-title: 使用工作流建立配置檔案清單
description: 使用工作流建立配置檔案清單
seo-description: null
page-status-flag: never-activated
uuid: a30f7217-fe82-4290-b1e6-e7a126a316c1
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
discoiquuid: ba42c3cf-31fc-4fbc-b230-a2b3982328c5
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 681e6ec5fc9ed8c7e46af04f0ed62927b30e1b2e

---


# 使用工作流建立配置檔案清單{#creating-a-profile-list-with-a-workflow}

若要根據新 **[!UICONTROL List]** 的收件者表格建立類型清單，您必須建立定位工作流程，以產生清單。 如需促銷活動清單的詳細資訊，請參閱 [本節](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

1. 轉至瀏 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 覽器的節點。
1. 建立新的定位工作流程。
1. 放置查詢 **活動** ，後面接著 **清單更新活動** 。

   ![](assets/mapping_create_list_workflow01.png)

1. 連按兩下「 **查詢** 」活動，然後按一下 **[!UICONTROL Edit the query]** ，以根據新收件者表格的架構選擇定位維度(在我們的範例中：個 **人**)。 Click **[!UICONTROL Finish]** to confirm.

   ![](assets/mapping_create_list_workflow03.png)

1. 連按兩下「清 **單更新** 」活動，然後選取 **[!UICONTROL Create the list if necessary (Computed name)]** 選項按鈕。

   ![](assets/mapping_create_list_workflow02.png)

1. 選擇新清單的建立資料夾。
1. 執行工作流以建立清單。
1. 在活動期間選定的樹節點中查看結 **[!UICONTROL List update]** 果。

   控制面板指定清單所基於的方案，如下所示：

   ![](assets/mapping_list_view.png)

>[!NOTE]
>
>您也可以參閱「建立收 [件者清單」影片](https://docs.adobe.com/content/help/en/campaign-learn/campaign-classic-tutorials/getting-started/creating-a-list-of-recipients.html) 。

