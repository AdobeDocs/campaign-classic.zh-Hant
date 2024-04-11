---
product: campaign
title: 使用工作流程建立設定檔清單
description: 瞭解如何在工作流程中建立設定檔清單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Workflows, Profiles
role: User
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 11%

---

# 使用工作流程建立設定檔清單{#creating-a-profile-list-with-a-workflow}


若要建立 **[!UICONTROL List]** 根據新的收件者表格輸入清單，您需要建立將產生清單的目標工作流程。

如需Campaign中清單的詳細資訊，請參閱 [本節](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

若要在自訂收件者表格中建立目標工作流程及更新收件者，請遵循下列步驟：

1. 前往 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 瀏覽器節點。
1. 建立新的目標定位工作流程。
1. 放置 **查詢** 活動後接 **清單更新** 活動。

   ![](assets/mapping_create_list_workflow01.png)

1. 按兩下 **查詢** 活動，然後按一下 **[!UICONTROL Edit the query]** 根據新收件者表格的結構描述選擇目標維度(在我們的範例中： **個人**)。 按一下 **[!UICONTROL Finish]** 確認。

   ![](assets/mapping_create_list_workflow03.png)

1. 按兩下 **清單更新** 活動，然後選取 **[!UICONTROL Create the list if necessary (Computed name)]** 選項按鈕。

   ![](assets/mapping_create_list_workflow02.png)

1. 選取新清單的建立資料夾。
1. 執行工作流程以建立清單。
1. 在樹狀結構中檢視您於期間選取的節點結果 **[!UICONTROL List update]** 活動。

   控制面板會指定清單所根據的結構描述，如下所示：

   ![](assets/mapping_list_view.png)
