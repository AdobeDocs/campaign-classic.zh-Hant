---
product: campaign
title: 週期性傳遞
description: 深入瞭解循環傳送工作流程活動
feature: Workflows
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 8%

---

# 週期性傳遞{#recurring-delivery}

**[!UICONTROL Recurring delivery]**&#x200B;活動可讓您設定行銷活動特定的傳遞範本發生次數。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#recurring-delivery-video)

此活動只能從行銷活動中找到的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;索引標籤中使用。

操作步驟：

1. 選取活動將依據的傳遞範本。

   ![](assets/recurring_delivery_001.png)

1. 設定傳遞範本。

此活動的設定程式與根據可用選項建立傳遞範本的程式類似。 如需詳細資訊，請參閱本[區段](../../delivery/using/about-templates.md)。

>[!CAUTION]
>
>循環傳遞不支援預覽內容或傳送包含[目標資料](../../workflow/using/data-life-cycle.md#target-data)個人化元素的校樣。

如需此活動使用中的範例，請參閱此[區段](sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 如何設定循環傳遞 {#set-up-recurring-delivery}

**循環傳遞**&#x200B;每次執行時都會建立新的傳遞執行個體。 例如，如果排程每週執行一次工作流程，則在一年後會產生52項傳送。 這也表示廣泛的記錄檔和追蹤記錄檔會依每個傳送執行個體區隔。

![循環傳遞](assets/delivery_recurring.jpg)

如果您想要停止執行週期性傳送，您應該完全取消行銷活動或停止執行它的工作流程。 停止來自Campaign控制面板的傳送只會停止傳送專案：循環傳送的下一個例項將繼續在每個工作流程執行時建立。

>[!NOTE]
>
>無法從&#x200B;**[!UICONTROL Recurring delivery]**&#x200B;型別活動傳送校樣。
> 
>若要透過行銷活動工作流程直接建立傳遞，請使用預先設定的通道特定活動（例如&#x200B;**[!UICONTROL Recurring delivery]**）。

## 教學課程影片 {#recurring-delivery-video}

此影片說明如何設定循環傳遞和排程器活動。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)提供其他Campaign Classic操作說明影片。
