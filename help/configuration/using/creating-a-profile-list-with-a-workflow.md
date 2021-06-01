---
product: campaign
title: 使用工作流程建立設定檔清單
description: 了解如何在工作流程中建立設定檔清單
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# 使用工作流程建立設定檔清單{#creating-a-profile-list-with-a-workflow}

若要根據新的收件者表格建立&#x200B;**[!UICONTROL List]**&#x200B;類型清單，您需要建立將產生清單的目標工作流程。

如需Campaign中清單的詳細資訊，請參閱[此區段](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

若要建立目標工作流程並在自訂收件者表格中更新收件者，請遵循下列步驟：

1. 轉到瀏覽器的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]**&#x200B;節點。
1. 建立新的目標工作流程。
1. 放置&#x200B;**Query**&#x200B;活動，後面接著&#x200B;**List update**&#x200B;活動。

   ![](assets/mapping_create_list_workflow01.png)

1. 連按兩下&#x200B;**Query**&#x200B;活動，然後按一下&#x200B;**[!UICONTROL Edit the query]**&#x200B;以根據新收件者表格的結構選擇目標維度(在範例中：**個別**)。 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;以確認。

   ![](assets/mapping_create_list_workflow03.png)

1. 按兩下&#x200B;**List update**&#x200B;活動，然後選擇&#x200B;**[!UICONTROL Create the list if necessary (Computed name)]**&#x200B;單選按鈕。

   ![](assets/mapping_create_list_workflow02.png)

1. 為新清單選擇建立資料夾。
1. 執行工作流以建立清單。
1. 在&#x200B;**[!UICONTROL List update]**&#x200B;活動期間所選樹的節點中查看結果。

   控制面板指定清單所依據的架構，如下所示：

   ![](assets/mapping_list_view.png)
