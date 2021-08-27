---
product: campaign
title: 等待
description: 深入了解「等待」工作流程活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 等待{#wait}

![](../../assets/common.svg)

**Wait**&#x200B;活動會在幾秒到幾個月之間的時間延遲後啟動其轉變。 等待任務不會阻止其他任務的執行；當此任務處於掛起狀態時，工作流可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如下列範例所示：

![](assets/edit_wait.png)

在&#x200B;**[!UICONTROL Duration]**&#x200B;欄位中，值可以以您選擇的單位表示：（根據操作員的區域設定）:

* 如果未指定區域設定：**s**&#x200B;秒，**m**&#x200B;分鐘，**h**&#x200B;小時，**d**&#x200B;天，**y**&#x200B;年。 在核準時，值會自動轉換為最容易讀取的單位。

   預設單位為日(**d**)。

* 而舉例來說，如果地區設定設為「Français」：**s**&#x200B;秒，**mn**&#x200B;分鐘，**h**&#x200B;小時，**j**&#x200B;天，**m**&#x200B;月，**a**&#x200B;年。 在批准時，值自動轉換為最可讀單元，如上例&#x200B;**90s**&#x200B;轉換為&#x200B;**1mn 30s**。

   預設單位為日(**d**)。
