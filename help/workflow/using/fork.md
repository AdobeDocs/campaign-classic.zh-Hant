---
product: campaign
title: 分支
description: 深入了解「分支工作流程」活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 7a38653b-c15d-4ed8-85dc-f7214409f42b
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 1%

---

# 分支{#fork}

![](../../assets/common.svg)

**[!UICONTROL Fork]**&#x200B;活動可讓您建立多個出站轉變，以便在相同的工作流程中獨立執行多個活動。

例如，您可以在查詢後使用活動，以便同時執行兩個動作：

* 將查詢結果儲存至對象中，
* 對結果執行分段，以傳送多個傳送。

您也可以在內容建立和傳送自動化的內容中使用活動，以便同時啟動目標計算和內容建立。 [此部分](../../delivery/using/automating-via-workflows.md#creating-the-delivery-and-its-content)中提供專用的使用案例。

>[!IMPORTANT]
>
>在&#x200B;**[!UICONTROL Fork]**&#x200B;活動&#x200B;**後新增的出站轉變不會**&#x200B;同時執行。 此行為可能會影響工作流程的效能。 如果您需要獨立執行數個活動，並最終在執行其餘工作流程之前將其結合，請使用此活動。

若要設定&#x200B;**[!UICONTROL Fork]**&#x200B;活動，請開啟該活動，以定義出站轉變的數字和標籤。

![](assets/s_user_segmentation_fork.png)

接著，您可以設定每個出站轉變，然後視需要使用[AND-join](and-join.md)活動將它們連結在一起。 這樣，只有&#x200B;**[!UICONTROL Fork]**&#x200B;活動的出站轉變完成後，工作流程的其餘部分才會執行。
