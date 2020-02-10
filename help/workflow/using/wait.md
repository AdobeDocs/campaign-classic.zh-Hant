---
title: 等待
seo-title: 等待
description: 等待
seo-description: null
page-status-flag: never-activated
uuid: 55e4f15d-8d69-45b1-b842-5ccdfdedf550
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: flow-control-activities
discoiquuid: 41bcfe67-b5d6-4ee6-9f8a-6a7a208e2036
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 等待{#wait}

等 **待** (Wait)活動會在幾秒到幾個月之間的時間延遲後啟動其轉換。 等待任務不會阻止其他任務的執行；當此任務處於待處理狀態時，工作流可以並行執行任務。

您可以使用編輯器輸入標籤和等待時間，如下例所示：

![](assets/edit_wait.png)

在欄位 **[!UICONTROL Duration]** 中，值可以用您選擇的單位表示：（根據營運商的地區設定）:

* 如果未指定區域設定： **s** , **m，分** 鐘， **** h **,** d,y, **** d,y,y。 在核準時，值會自動轉換為最可讀的單位。

   預設單位為日(**d**)。

* 但是，例如，若地區設定設為「Français」: **秒** , **mn** 分鐘， **** 小時 **,********** mj,數月，為數年。 在核準時，值會自動轉換為最易讀的單位，如上 **90s** 已轉換 **為1mn 30s**。

   預設單位為日(**d**)。

