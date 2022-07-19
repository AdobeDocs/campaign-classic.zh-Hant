---
product: campaign
title: 管理時區
description: 管理時區
feature: Workflows
exl-id: c2f6033c-30cd-4eb4-adf1-ab2de7510220
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 3%

---

# 管理時區{#managing-time-zones}

![](../../assets/v7-only.svg)

Adobe Campaign讓您管理同一實例所涉及的各國之間的時間差。 應用的配置是在實例建立過程中配置的。

有關在Adobe Campaign配置時區的詳細資訊，請參閱 [Campaign Classicv7安裝指南](../../installation/using/time-zone-management.md)。

在工作流中，您可以調整活動執行計畫並將特定時區連結到活動或整個工作流。 此配置在導入檔案時或在交貨計畫框架內非常有用。

## 執行計畫 {#execution-scheduling}

您可以使用調度程式調度任務的執行(請參閱 [調度程式](scheduler.md))。 您還可以使用提供此功能的活動中可用的計畫選項。 這些活動提供 **[!UICONTROL Schedule]** 頁籤： **[!UICONTROL File collector]**。 **[!UICONTROL File transfer]**。 **[!UICONTROL Web download]**。 **[!UICONTROL Email reception]** &amp; **[!UICONTROL SMS]**&#x200B;的子菜單。

對於所有計畫任務，即具有計畫選項的所有活動，您可以選擇要應用的時區。 通過 **[!UICONTROL Advanced]** 頁籤。

![](assets/wf-timezone-in-a-box.png)

可能的值為：

* 伺服器時區

   使用Adobe Campaign應用程式伺服器的時區。

* 用戶時區

   使用執行工作流的Adobe Campaign操作員的時區。

* 資料庫時區

   使用所用資料庫伺服器的時區。

* 特定時區

   使用選定的時區。

如果 **[!UICONTROL By default]** 值被選中，工作流的時區被應用，或者應用伺服器的時區被應用。

## 將時區連結到活動 {#linking-a-time-zone-to-an-activity}

的 **[!UICONTROL Advanced]** 的子菜單。 雖然大多數時間，工作流的時區已足夠，但是對於特定活動（如資料導入），可能需要時不時地使其超載，以便將日期連結到其正確的時區。
