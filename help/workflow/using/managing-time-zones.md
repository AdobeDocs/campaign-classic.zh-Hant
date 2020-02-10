---
title: 管理時區
seo-title: 管理時區
description: 管理時區
seo-description: null
page-status-flag: never-activated
uuid: a253861a-fc15-406d-969d-33cfb4169839
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8bcbcd23-9251-412a-ae72-11f15db74112
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 管理時區{#managing-time-zones}

Adobe Campaign可讓您管理同一例項所涉及之不同國家／地區之間的時差。 應用的配置是在建立實例期間配置的。

如需在Adobe Campaign中設定時區的詳細資訊，請參閱此 [節](../../installation/using/time-zone-management.md)。

在工作流中，您可以調整活動執行計畫並將特定時區連結至活動或整個工作流。 在匯入檔案時，或在傳送排程的架構中，此設定可派上用場。

## 執行計畫 {#execution-scheduling}

您可以使用調度程式調度任務的執行(請參 [閱Scheduler](../../workflow/using/scheduler.md))。 您也可以使用活動中提供此功能的排程選項。 這些活動提供一個 **[!UICONTROL Schedule]** 頁籤： **[!UICONTROL File collector]**、 **[!UICONTROL File transfer]****[!UICONTROL Web download]**、 **[!UICONTROL Email reception]** 和 **[!UICONTROL SMS]**&#x200B;等。

對於所有計畫任務（即具有計畫選項的所有活動），您可以選擇要應用的時區。 時區是透過相關活動 **[!UICONTROL Advanced]** 的標籤選取：

![](assets/wf-timezone-in-a-box.png)

可能的值包括：

* 伺服器時區

   使用Adobe Campaign應用程式伺服器的時區。

* 用戶時區

   使用執行工作流程的Adobe Campaign運算子的時區。

* 資料庫時區

   使用所用資料庫伺服器的時區。

* 特定時區

   使用選定的時區。

如果選 **[!UICONTROL By default]** 擇了該值，則應用工作流的時區，或應用伺服器的時區。

## 將時區連結至活動 {#linking-a-time-zone-to-an-activity}

工作流 **[!UICONTROL Advanced]** 活動的頁籤允許您選擇其時區。 雖然大部分時間工作流程的時區已足夠，但是對於特定活動（例如資料匯入），您必須時不時地將其過載，以便將日期連結至正確的時區。
