---
title: 等待
description: 進一步瞭解「等待」工作流活動
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
translation-type: tm+mt
source-git-commit: 6be6c353c3464839a74ba857d8d93d0f68bc8865
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 1%

---


# 等待{#wait}

等 **待** (Wait)活動會在幾秒到幾個月之間的時間延遲後啟動其轉換。 等待任務不會阻止其他任務的執行；當此任務處於待處理狀態時，工作流可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如下例所示：

![](assets/edit_wait.png)

在欄位 **[!UICONTROL Duration]** 中，值可以用您選擇的單位表示：（根據營運商的地區設定）:

* 如果未指定區域設定： **s** , **m** ，分鐘， **h** ，小時， **d,** d **** ,y,d,y。 在核準時，值會自動轉換為最可讀的單位。

   預設單位為日(**d**)。

* 但是，例如，若地區設定設為「Français」: **s** , **mn** , **min,** h，數小時 **,** j，數月 ******** , m, m，數年。 在核準時，值會自動轉換為最易讀的單位，如上 **90s** 已轉換 **為1mn 30s**。

   預設單位為日(**d**)。

