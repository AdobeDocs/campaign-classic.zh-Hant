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

A **等待** 活動會在幾秒到幾個月之間的任何時間延遲後，啟動其轉變。 等待任務不會阻止其他任務的執行；當此任務處於掛起狀態時，工作流可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如下列範例所示：

![](assets/edit_wait.png)

在 **[!UICONTROL Duration]** 欄位中，值可以以您選擇的單位表示：（根據操作員的區域設定）:

* 如果未指定區域設定： **s** 幾秒， **m** 幾分鐘， **h** 數小時， **d** 幾天， **y** 多年了。 在核準時，值會自動轉換為最容易讀取的單位。

   預設單位為日(**d**)。

* 而舉例來說，如果地區設定設為「Français」： **s** 幾秒， **mn** 幾分鐘， **h** 數小時， **j** 幾天， **m** 幾個月來， **a** 多年了。 如上例所示，在核準時，值會自動轉換為最易讀的單位 **90年代** 轉換為 **1分30秒**.

   預設單位為日(**d**)。
