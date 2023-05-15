---
product: campaign
title: 分支
description: 深入了解「分支工作流程」活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 分支{#fork}



您可以使用 **[!UICONTROL Fork]** 活動來建立多個出站轉變，以及在相同的工作流程內獨立執行多個活動。

>[!IMPORTANT]
>
>您在 **[!UICONTROL Fork]** 活動不會同時執行。 此行為可能會影響工作流程效能。 使用 **[!UICONTROL Fork]** 活動。 您可以視需要在工作流程的後續部分之前加入傳出活動。

若要設定 **[!UICONTROL Fork]** 活動及其相關活動，請遵循下列步驟：

1. 開啟 **[!UICONTROL Fork]** 活動，並定義出站轉變的名稱和標籤。

   ![](assets/s_user_segmentation_fork.png)

1. 開啟每個出站轉變並加以設定。
1. （可選）要加入出站轉變，請添加AND-join活動。 [了解更多](and-join.md)。

   工作流程的後續部分僅在已加入的出站轉變完成後才會執行。

## 範例：細分

在此範例中，會傳送不同的電子郵件給不同的母體群組。 A **[!UICONTROL Fork]** 活動用於查詢後，以同時執行兩個動作：

* 保存查詢結果
* 將結果分段以傳送多個傳送

   ![分支活動會遵循兩個查詢的交集，並在清單更新活動和分割活動之前。](assets/wkf_fork_example.png)

工作流程包含下列活動：

1. **[!UICONTROL Query]** 活動

   已選取兩個母體群組：女人和巴黎人。

1. **[!UICONTROL Intersection]** 活動

   選取查詢結果的交集，即巴黎女性。

1. **[!UICONTROL Fork]** 活動

   計算的母體會儲存，並且並行分割為兩個群組：

   1. 18至40歲的巴黎女性
   1. 40歲以上巴黎女性

1. **[!UICONTROL Delivery]** 活動

   會傳送不同的電子郵件給每個母體群組。

## 使用案例：傳送生日電子郵件

循環電子郵件會在收件者生日當天傳送至其清單。 A **[!UICONTROL Fork]** 活動用於包含閏年2月29日出生的收件者。 [深入了解](sending-a-birthday-email.md) 關於此使用案例。

![分支活動會遵循測試活動，並在兩個查詢活動之前。](assets/birthday-workflow_usecase_1.png)

## 使用案例：使用工作流程自動化內容

內容區塊的建立和傳送會自動進行。 A **[!UICONTROL Fork]** 活動可用來計算目標，並行建立內容。 [深入了解](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 關於此使用案例。

![分支活動會遵循傳送活動，並在查詢活動和內容管理活動之前，兩者皆透過AND-join活動連結。](../../delivery/using/assets/d_ncs_content_workflow10.png)

接著，您可以設定每個出站轉變，然後使用 [合併連結](and-join.md) 活動（如有需要）。 如此一來，其餘的工作流程只會在 **[!UICONTROL Fork]** 活動的出站轉變已完成。

## 相關主題

* [與加入活動](and-join.md)
* [使用案例：生日電子郵件](sending-a-birthday-email.md)
* [使用案例：內容建立與傳遞](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)