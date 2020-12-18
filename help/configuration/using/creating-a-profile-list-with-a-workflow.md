---
solution: Campaign Classic
product: campaign
title: 使用工作流建立設定檔清單
description: 瞭解如何在工作流程中建立描述檔清單
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---


# 使用工作流建立設定檔清單{#creating-a-profile-list-with-a-workflow}

若要根據新的收件者表格建立&#x200B;**[!UICONTROL List]**&#x200B;類型清單，您必須建立將產生清單的定位工作流程。

如需促銷活動清單的詳細資訊，請參閱[本節](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign)。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

若要建立定位工作流程並在自訂收件者表格中更新收件者，請遵循下列步驟：

1. 轉至瀏覽器的&#x200B;**[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]**&#x200B;節點。
1. 建立新的定位工作流程。
1. 放置&#x200B;**Query**&#x200B;活動，後面接著&#x200B;**List update**&#x200B;活動。

   ![](assets/mapping_create_list_workflow01.png)

1. 連按兩下&#x200B;**Query**&#x200B;活動，然後按一下&#x200B;**[!UICONTROL Edit the query]**&#x200B;以根據新收件者表格的架構選擇定位維度(在我們的範例中：**個人**)。 按一下&#x200B;**[!UICONTROL Finish]**&#x200B;進行確認。

   ![](assets/mapping_create_list_workflow03.png)

1. 連按兩下「清單更新&#x200B;**」活動，然後選取「**[!UICONTROL Create the list if necessary (Computed name)]**」選項按鈕。**

   ![](assets/mapping_create_list_workflow02.png)

1. 選擇新清單的建立資料夾。
1. 執行工作流以建立清單。
1. 在&#x200B;**[!UICONTROL List update]**&#x200B;活動期間選擇的樹節點中查看結果。

   控制面板指定清單所基於的方案，如下所示：

   ![](assets/mapping_list_view.png)


