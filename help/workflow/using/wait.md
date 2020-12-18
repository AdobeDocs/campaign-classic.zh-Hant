---
solution: Campaign Classic
product: campaign
title: 等待
description: 進一步瞭解「等待」工作流活動
audience: workflow
content-type: reference
topic-tags: flow-control-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# 等待{#wait}

**Wait**&#x200B;活動在幾秒到幾個月之間的時間延遲之後激活其轉換。 等待任務不會阻止其他任務的執行；當此任務處於待處理狀態時，工作流可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如下例所示：

![](assets/edit_wait.png)

在&#x200B;**[!UICONTROL Duration]**&#x200B;欄位中，值可以以您選擇的單位表示：（根據營運商的地區設定）:

* 如果未指定區域設定：**s**&#x200B;秒、**m**&#x200B;分鐘、**h**&#x200B;小時、**d**&#x200B;天、**y**&#x200B;年。 在核準時，值會自動轉換為最可讀的單位。

   預設單位為日(**d**)。

* 但是，例如，若地區設定設為「Français」:**s**&#x200B;秒、**mn**&#x200B;分鐘、**h**&#x200B;小時、**j**&#x200B;天、**m**&#x200B;月、**a11/>年。**&#x200B;在批准時，該值被自動轉換為最易讀的單元，如上例中的&#x200B;**90s**&#x200B;被轉換為&#x200B;**1mn 30s**。

   預設單位為日(**d**)。

