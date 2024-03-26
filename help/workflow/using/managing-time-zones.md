---
product: campaign
title: 管理時區
description: 管理時區
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 5%

---

# 管理時區{#managing-time-zones}



Adobe Campaign可讓您管理同一個執行個體所關注的不同國家/地區之間的時間延遲。 套用的組態會在建立執行個體期間進行設定。

如需在Adobe Campaign中設定時區的詳細資訊，請參閱 [Campaign Classic v7安裝指南](../../installation/using/time-zone-management.md).

在工作流程中，您可以調整活動執行排程，並將特定時區連結至活動或整個工作流程。 此設定在匯入檔案時或是在傳送排程的架構中相當實用。

## 執行排程 {#execution-scheduling}

您可以使用排程器排程工作的執行(請參閱 [排程器](scheduler.md))。 您也可以使用提供此功能的活動中的可用排程選項。 這些活動提供 **[!UICONTROL Schedule]** 標籤： **[!UICONTROL File collector]**， **[!UICONTROL File transfer]**， **[!UICONTROL Web download]**， **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**&#x200B;等

對於所有已排程的工作（即具有排程選項的所有活動），您可以選取要套用的時區。 時區是透過 **[!UICONTROL Advanced]** 相關活動的索引標籤：

![](assets/wf-timezone-in-a-box.png)

可能的值包括：

* 伺服器時區

  使用Adobe Campaign應用程式伺服器的時區。

* 使用者時區

  使用執行工作流程的Adobe Campaign運運算元的時區。

* 資料庫時區

  使用所使用資料庫伺服器的時區。

* 特定時區

  使用選取的時區。

如果 **[!UICONTROL By default]** 選取、套用工作流程的時區，或應用程式伺服器的時區。

## 將時區連結至活動 {#linking-a-time-zone-to-an-activity}

此 **[!UICONTROL Advanced]** 工作流程活動的索引標籤可讓您選取其時區。 雖然在大部分時間中，工作流程的時區已經足夠，但是可能需要針對特定活動（例如資料匯入）一次又一次地讓時區超載，才能將日期連結到其正確的時區。
