---
solution: Campaign Classic
product: campaign
title: 分支
description: 進一步瞭解Fork工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 3eecc16442a11849c12819cf83392f60c5b82a13
workflow-type: tm+mt
source-wordcount: '207'
ht-degree: 0%

---


# 分支{#fork}

**[!UICONTROL Fork]**&#x200B;活動允許您建立多個出站轉換，以便在同一工作流中獨立執行多個活動。

例如，您可在查詢後使用活動，以便並行執行兩個動作：

* 將查詢結果儲存至觀眾，
* 對結果執行分段，以傳送多個傳送。

您也可以在內容建立和傳送傳送自動化的環境中使用活動，以便同時啟動目標計算和內容建立。 [本節](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供專用的使用案例。

>[!WARNING]
>
>請記住，在Fork活動之後新增的去話切換效果不會同時執行。
>
>因此，不應使用活動來改進工作流的效能，而應獨立執行多個活動，並最終在執行其餘工作流之前將它們連接在一起。

若要設定活動，請將其開啟，然後定義所要之出站轉場的數目和標籤。

![](assets/s_user_segmentation_fork.png)

然後，您可以設定每個傳出轉場，然後視需要使用[AND-join](../../workflow/using/and-join.md)活動將它們結合在一起。 這樣，只有&#x200B;**[!UICONTROL Fork]**&#x200B;活動的出站轉換完成後，其餘的工作流才會執行。
