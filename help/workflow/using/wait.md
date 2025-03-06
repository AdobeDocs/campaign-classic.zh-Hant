---
product: campaign
title: 等待
description: 進一步瞭解等待工作流程活動
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 等待{#wait}



**等待**&#x200B;活動會在延遲數秒到幾個月之間的任何時間後啟動其轉變。 等待任務不會阻礙其他任務的執行；當此任務擱置時，工作流程可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如以下範例所示：

![](assets/edit_wait.png)

在&#x200B;**[!UICONTROL Duration]**&#x200B;欄位中，值可以您選擇的單位表示： （根據運運算元的地區設定）：

* 如果未指定地區設定： **s**&#x200B;代表秒數，**m**&#x200B;代表分鐘，**h**&#x200B;代表小時，**d**&#x200B;代表天，**y**&#x200B;代表年。 核準時，值會自動轉換為最易讀的單位。

  預設單位是日(**d**)。

* 舉例來說，若地區設定設為&#39;Français&#39;： **s**&#x200B;代表秒數，**mn**&#x200B;代表分鐘，**h**&#x200B;代表小時，**j**&#x200B;代表天，**m**&#x200B;代表月，**a**&#x200B;代表年。 在核準時，值會自動轉換為最易讀的單位，如上述範例中的&#x200B;**90s**&#x200B;已轉換為&#x200B;**1mn 30s**。

  預設單位是日(**d**)。
