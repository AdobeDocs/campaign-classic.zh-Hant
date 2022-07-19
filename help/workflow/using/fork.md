---
product: campaign
title: 分支
description: 瞭解有關Fork工作流活動的詳細資訊
feature: Workflows
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 1%

---

# 分支{#fork}

![](../../assets/v7-only.svg)

您可以使用 **[!UICONTROL Fork]** 活動：建立多個出站過渡，並在同一工作流中獨立運行多個活動。

>[!IMPORTANT]
>
>您在 **[!UICONTROL Fork]** 活動不能同時運行。 此行為會影響工作流效能。 使用 **[!UICONTROL Fork]** 活動。 （可選）您可以在工作流的後續部分之前加入出站活動。

配置 **[!UICONTROL Fork]** 活動及其相關活動，請按照以下步驟執行：

1. 開啟 **[!UICONTROL Fork]** 活動，並定義出站轉換的名稱和標籤。

   ![](assets/s_user_segmentation_fork.png)

1. 開啟每個出站轉換並配置它。
1. （可選）要加入出站轉換，請添加AND-join活動。 [了解更多資訊](and-join.md)。

   工作流的後續部分僅在連接的出站過渡完成後運行。

## 示例：分割

在本示例中，不同的電子郵件會發送到不同的人口組。 A **[!UICONTROL Fork]** 在查詢後使用活動，並行執行兩個操作：

* 保存查詢結果
* 將結果分段以發送多個交貨

   ![分叉活動沿兩個查詢的交集進行，並位於清單更新活動和拆分活動之前。](assets/wkf_fork_example.png)

工作流包括以下活動：

1. **[!UICONTROL Query]** 活動

   選擇兩個人口組：女人和巴黎人。

1. **[!UICONTROL Intersection]** 活動

   選擇查詢結果的交集，即巴黎女性。

1. **[!UICONTROL Fork]** 活動

   計算的總量被保存，並且並行分成兩組：

   1. 18至40歲的巴黎婦女
   1. 40歲以上巴黎女性

1. **[!UICONTROL Delivery]** 活動

   會向每個人口組發送不同的電子郵件。

## 用例：發送生日電子郵件

在收件人的生日時，會向其清單發送一封定期電子郵件。 A **[!UICONTROL Fork]** 活動用於包括2月29日出生的閏年受贈者。 [瞭解更多資訊](sending-a-birthday-email.md) 關於這個用例。

![分叉活動跟在test活動之後，並位於兩個查詢活動之前。](assets/birthday-workflow_usecase_1.png)

## 用例：使用工作流自動化內容

內容塊的建立和傳遞是自動的。 A **[!UICONTROL Fork]** 活動用於計算目標，並且並行建立內容。 [瞭解更多資訊](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content) 關於這個用例。

![分叉活動跟在傳遞活動之後，位於查詢活動和內容管理活動之前，這兩個活動都通過與聯接活動聯接。](../../delivery/using/assets/d_ncs_content_workflow10.png)

然後，您可以配置每個出站過渡，然後使用 [與連接](and-join.md) 活動（如果需要）。 這樣，其餘工作流將僅執行一次 **[!UICONTROL Fork]** 活動的出站轉換已完成。

## 相關主題

* [AND-join活動](and-join.md)
* [用例：生日郵件](sending-a-birthday-email.md)
* [用例：內容建立和交付](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)