---
product: campaign
title: 使用工作流程建立設定檔清單
description: 瞭解如何在工作流程中建立設定檔清單
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Workflows
exl-id: 6b308299-4d07-4c9e-bd2f-a0860c41cf02
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 12%

---

# 使用工作流程建立設定檔清單{#creating-a-profile-list-with-a-workflow}



若要建立 **[!UICONTROL List]** 根據新的收件者表格型別清單，您需要建立將產生清單的目標工作流程。

如需Campaign中清單的詳細資訊，請參閱 [本節](../../platform/using/creating-and-managing-lists.md#about-lists-in-adobe-campaign).

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](../../platform/using/creating-and-managing-lists.md#create-list-in-a-wf-video)

若要在自訂收件者表格中建立目標工作流程並更新收件者，請遵循下列步驟：

1. 前往 **[!UICONTROL Profiles and Targets > Jobs > Targeting workflows]** 檔案總管的節點。
1. 建立新的目標定位工作流程。
1. 放置 **查詢** 活動後接 **清單更新** 活動。

   ![](assets/mapping_create_list_workflow01.png)

1. 連按兩下 **查詢** 活動，然後按一下 **[!UICONTROL Edit the query]** 根據新收件者表格的結構描述選擇目標維度(在我們的範例中： **個人**)。 按一下 **[!UICONTROL Finish]** 確認。

   ![](assets/mapping_create_list_workflow03.png)

1. 連按兩下 **清單更新** 活動，然後選取 **[!UICONTROL Create the list if necessary (Computed name)]** 選項按鈕。

   ![](assets/mapping_create_list_workflow02.png)

1. 選取新清單的建立資料夾。
1. 執行工作流程以建立清單。
1. 在樹狀結構中所選取的節點中檢視結果 **[!UICONTROL List update]** 活動。

   儀表板會指定清單所根據的結構描述，如下所示：

   ![](assets/mapping_list_view.png)
