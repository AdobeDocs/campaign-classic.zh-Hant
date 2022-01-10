---
product: campaign
title: 使用工作流程建立設定檔清單
description: 了解如何在工作流程中建立設定檔清單
audience: configuration
content-type: reference
topic-tags: use-a-custom-recipient-table
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: fb4b4c42b907e86813ea570f912312fccf893bfe
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 10%

---

# 使用工作流程建立設定檔清單{#creating-a-profile-list-with-a-workflow}

![](../../assets/common.svg)

建立 **[!UICONTROL List]** 根據新收件者表格輸入清單，您需要建立將產生清單的目標工作流程。

如需Campaign中清單的詳細資訊，請參閱 [本節](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

若要建立目標工作流程並在自訂收件者表格中更新收件者，請遵循下列步驟：

1. 前往 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 瀏覽器的節點。
1. 建立新的目標工作流程。
1. 放置 **查詢** 活動後面接著a **清單更新** 活動。

   ![](assets/mapping_create_list_workflow01.png)

1. 按兩下 **查詢** 活動，然後按一下 **[!UICONTROL Edit the query]** 若要根據新收件者表格的結構選擇目標維度(在範例中： **個人**)。 按一下 **[!UICONTROL Finish]** 確認。

   ![](assets/mapping_create_list_workflow03.png)

1. 按兩下 **清單更新** 活動，然後選取 **[!UICONTROL Create the list if necessary (Computed name)]** 選項按鈕。

   ![](assets/mapping_create_list_workflow02.png)

1. 為新清單選擇建立資料夾。
1. 執行工作流以建立清單。
1. 在樹的節點中查看結果，在 **[!UICONTROL List update]** 活動。

   控制面板指定清單所依據的架構，如下所示：

   ![](assets/mapping_list_view.png)
