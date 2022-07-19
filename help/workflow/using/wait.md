---
product: campaign
title: 等待
description: 瞭解有關等待工作流活動的詳細資訊
feature: Workflows
exl-id: 4872f756-14d7-4e37-a9cf-b929c77e34ca
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---

# 等待{#wait}

![](../../assets/v7-only.svg)

A **等待** 活動在幾秒到幾個月之間的時間延遲後激活其轉換。 等待任務不會阻止其他任務的執行；此任務處於掛起狀態時，工作流可以並行執行任務。

可以使用編輯器輸入標籤和等待時間，如下例所示：

![](assets/edit_wait.png)

在 **[!UICONTROL Duration]** 欄位中，值可以以您選擇的單位表示：（根據操作員的區域設定）:

* 如果未指定區域設定： **s** 幾秒鐘， **米** 幾分鐘， **h** 幾個小時， **d** 幾天來， **y** 多年了。 在批准時，值將自動轉換為最可讀單元。

   預設單位為日(**d**)。

* 而如果區域設定設定為「Français」： **s** 幾秒鐘， **錳** 幾分鐘， **h** 幾個小時， **j** 幾天來， **米** 幾個月來， **a** 多年了。 在批准時，值將自動轉換為最可讀單元，如上例所示 **90年代** 已轉換為 **1mn 30s**。

   預設單位為日(**d**)。
