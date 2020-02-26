---
title: 傳送類型
seo-title: 傳送類型
description: 傳送類型
seo-description: null
page-status-flag: never-activated
uuid: a540efc7-105d-4c7f-a2ee-ade4d22b3445
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: about-deliveries-and-channels
discoiquuid: 0cbc4e92-482f-4dac-a1fb-b738e7127938
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 707352334144df86ae82aa51d595ae6bc751d1f2

---


# 傳送類型{#types-of-deliveries}

促銷活動中有三種類型的傳送物件：

## 單次傳送 {#single-delivery}

傳 **送** ，是執行一次的獨立傳送物件。 它可以複製、重新準備，但只要它處於最終狀態（已取消、停止、完成），就不能重複使用。

可從傳送清單或透過「傳送」活動在工作流程中建立 [傳送](../../workflow/using/delivery.md) 。

工作流程也會根據您要使用的管道類型，提供特定的傳送活動。 For more on these activities, refer to [this section](../../workflow/using/cross-channel-deliveries.md).

## 循環傳送 {#recurring-delivery}

循 **環傳送** ，可讓您在每次執行活動時建立新傳送。 如此可避免您必須針對循環工作建立新的傳送。

例如，如果您每月執行此類活動一次，一年後最終會有12個傳送。

循環傳送是透過循環傳送活動在工作流程 [中建立的](../../workflow/using/recurring-delivery.md)。 本節將介紹此活動的示例：在定 [位工作流程中建立循環傳送](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 持續傳送 {#continuous-delivery}

持續 **傳送** ，可讓您將新收件者新增至現有的傳送，如此就不必在每次執行時建立新的傳送。

如果傳送中的資訊變更（內容、名稱等），則會在傳送執行時建立新的傳送物件。 如果未變更任何資訊，則會重複使用相同的傳送物件，而傳送和追蹤記錄檔會新增至相同的物件。

例如，如果您每月執行此類活動一次，則一年後會有單次傳送（若您未變更傳送）。

在工作流程中，會透過「連續傳送」活動 [建立連續傳送](../../workflow/using/continuous-delivery.md)。
