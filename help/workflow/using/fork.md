---
product: campaign
title: 分支
description: 進一步瞭解分支工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 3%

---

# 分支{#fork}



您可以使用 **[!UICONTROL Fork]** 活動，以建立多個出站轉變，並在相同工作流程中獨立執行數個活動。

>[!IMPORTANT]
>
>您在之後新增的出站轉變 **[!UICONTROL Fork]** 活動不會同時執行。 此行為可能會影響工作流程效能。 使用 **[!UICONTROL Fork]** 活動（如果您需要獨立執行數個活動）。 您可以選擇在工作流程的後續部分之前加入出站活動。

若要設定 **[!UICONTROL Fork]** 活動及其相關活動，請遵循下列步驟：

1. 開啟 **[!UICONTROL Fork]** 活動，並定義出站轉變的名稱和標籤。

   ![](assets/s_user_segmentation_fork.png)

1. 開啟並設定每個出站轉變。
1. 或者，若要聯結出站轉變，請新增AND — 聯結活動。 [了解更多](and-join.md)。

   工作流程的後續部分只會在聯結的對外轉變完成後執行。

## 範例：細分

在此範例中，會將不同的電子郵件傳送至不同的母體群組。 A **[!UICONTROL Fork]** 活動用於查詢之後，以平行執行兩個動作：

* 儲存查詢結果
* 將結果分段以傳送多個傳遞

  ![分叉活動位於兩個查詢的交集處，並在清單更新活動和分割活動之前。](assets/wkf_fork_example.png)

工作流程包含下列活動：

1. **[!UICONTROL Query]** 活動

   選取兩個人口群組：女性和巴黎人。

1. **[!UICONTROL Intersection]** 活動

   已選取查詢結果的交集，即巴黎女性。

1. **[!UICONTROL Fork]** 活動

   已計算的母體會儲存，並同時分成兩個群組：

   1. 18至40歲的巴黎女性
   1. 40歲以上的巴黎女性

1. **[!UICONTROL Delivery]** 活動

   會傳送不同的電子郵件給每個母體群組。

## 使用案例：傳送生日電子郵件

在收件者生日當天會傳送定期電子郵件給收件者清單。 A **[!UICONTROL Fork]** 活動用於包含閏年2月29日出生的收件者。 [瞭解更多](sending-a-birthday-email.md) 關於此使用案例。

![分叉活動會依循測試活動，並在兩個查詢活動之前進行。](assets/birthday-workflow_usecase_1.png)

## 使用案例：使用工作流程自動化內容

內容區塊的建立與傳送會自動完成。 A **[!UICONTROL Fork]** 活動可用來計算目標，並同時建立內容。 [瞭解更多](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 關於此使用案例。

![分支活動會依循傳遞活動，並在查詢活動和內容管理活動之前，兩者都是透過AND聯結活動聯結。](../../delivery/using/assets/d_ncs_content_workflow10.png)

您可以接著設定每個出站轉變，然後使用 [合併連結](and-join.md) 活動（如有需要）。 如此一來，工作流程的其餘部分只會在 **[!UICONTROL Fork]** 活動的出站轉變已完成。

## 相關主題

* [AND-join 活動](and-join.md)
* [使用案例：生日電子郵件](sending-a-birthday-email.md)
* [使用案例：內容建立和傳遞](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)