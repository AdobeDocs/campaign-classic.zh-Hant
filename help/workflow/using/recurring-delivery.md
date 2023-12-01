---
product: campaign
title: 重複傳送
description: 深入瞭解循環傳送工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: cfc38df8184a8f59d49ce27eb7875783e8941611
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 12%

---

# 重複傳送{#recurring-delivery}

A **[!UICONTROL Recurring delivery]** 活動可讓您設定行銷活動特定的傳送範本發生次數。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#recurring-delivery-video)

此活動只能從 **[!UICONTROL Targeting and workflows]** 在行銷活動中找到的索引標籤。

操作步驟：

1. 選取活動將依據的傳遞範本。

   ![](assets/recurring_delivery_001.png)

1. 設定傳遞範本。

此活動的設定程式與根據可用選項建立傳遞範本的程式類似。 如需詳細資訊，請參閱本[區段](../../delivery/using/about-templates.md)。

>[!CAUTION]
>
>循環傳遞不支援預覽內容或傳送校樣，包括 [目標資料](../../workflow/using/data-life-cycle.md#target-data) 個人化元素。

如需此活動使用方式的範例，請參閱以下內容 [區段](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow).

## 如何設定循環傳遞 {#set-up-recurring-delivery}

A **循環傳遞** 每次執行時都會建立新的傳遞執行個體。 例如，如果排程每週執行一次工作流程，則在一年後會產生52項傳送。 這也表示廣泛的記錄檔和追蹤記錄檔會依每個傳送執行個體區隔。

![循環傳遞](assets/delivery_recurring.jpg)

如果您想要停止執行週期性傳送，您應該完全取消行銷活動或停止執行它的工作流程。 停止來自Campaign控制面板的傳送只會停止傳送專案：循環傳送的下一個例項將繼續在每個工作流程執行時建立。

>[!NOTE]
>
>無法從「 」傳送證明 **[!UICONTROL Recurring delivery]** 輸入活動。
> 
>若要透過行銷活動工作流程直接建立傳遞，請使用已預先設定的通道特定活動(例如 **[!UICONTROL Recurring delivery]**)。

## 教學課程影片 {#recurring-delivery-video}

此影片說明如何設定循環傳遞和排程器活動。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

提供其他Campaign Classic操作影片 [此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant).
