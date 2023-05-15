---
product: campaign
title: 管理時區
description: 管理時區
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 4%

---

# 管理時區{#managing-time-zones}



Adobe Campaign可讓您管理同一例項所涉及之不同國家/地區之間的時差。 套用的設定是在建立執行個體期間設定。

如需在Adobe Campaign中設定時區的詳細資訊，請參閱 [Campaign Classicv7安裝指南](../../installation/using/time-zone-management.md).

在工作流程中，您可以調整活動執行排程，並將特定時區連結至活動或整個工作流程。 此設定在匯入檔案時或在傳送排程的架構內時相當實用。

## 執行排程 {#execution-scheduling}

您可以使用排程器來排程任務的執行(請參閱 [排程器](scheduler.md))。 您也可以使用提供此功能之活動中可用的排程選項。 這些活動提供 **[!UICONTROL Schedule]** 標籤： **[!UICONTROL File collector]**, **[!UICONTROL File transfer]**, **[!UICONTROL Web download]**, **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**、等

對於所有計畫任務，即所有具有計畫選項的活動，您可以選擇要應用的時區。 時區是透過 **[!UICONTROL Advanced]** 頁簽中顯示的內容：

![](assets/wf-timezone-in-a-box.png)

可能的值包括：

* 伺服器時區

   使用Adobe Campaign應用程式伺服器的時區。

* 用戶時區

   使用執行工作流程的Adobe Campaign運算子的時區。

* 資料庫時區

   使用所使用資料庫伺服器的時區。

* 特定時區

   使用所選時區。

若 **[!UICONTROL By default]** 值，則應用工作流的時區，或應用程式伺服器的時區。

## 將時區連結至活動 {#linking-a-time-zone-to-an-activity}

此 **[!UICONTROL Advanced]** 工作流程活動的索引標籤可讓您選取其時區。 雖然大部分時間，工作流程的時區已足夠，但您可能需要時不時地對特定活動（例如資料匯入）超載，以將日期連結至其正確時區。
