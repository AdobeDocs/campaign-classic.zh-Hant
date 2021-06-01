---
product: campaign
title: 重複傳送
description: 深入了解循環傳送工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: efd2cdfb-2e5f-4672-8be8-a424481b11ed
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 11%

---

# 重複傳送{#recurring-delivery}

**[!UICONTROL Recurring delivery]**&#x200B;活動可讓您設定促銷活動專屬的傳送範本發生次數。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#recurring-delivery-video)

此活動僅可從促銷活動中找到的&#x200B;**[!UICONTROL Targeting and workflows]**&#x200B;標籤取得。

操作步驟：

1. 選取活動將根據的傳送範本。

   ![](assets/recurring_delivery_001.png)

1. 設定傳送範本。

此活動的設定程式與根據可用選項建立傳送範本的程式類似。 如需詳細資訊，請參閱本[區段](../../delivery/using/about-templates.md)。

如需所使用此活動的範例，請參閱此[區段](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 如何設定循環傳送

每次執行&#x200B;**循環傳送**&#x200B;時，都會建立新的傳送例項。 例如，如果排程每週執行一次工作流程，則在一年後會產生52個傳送。 這也表示廣泛的記錄檔和追蹤記錄檔將依每個傳送例項加以區隔。

![循環傳送](assets/delivery_recurring.jpg)

>[!NOTE]
>
>無法從&#x200B;**[!UICONTROL Recurring delivery]**&#x200B;類型活動傳送校樣。\
>若要直接透過促銷活動工作流程建立傳送，請使用預先設定的通道特定活動(例如&#x200B;**[!UICONTROL Email delivery]**)。

## 教學課程影片(#recurring-delivery-video)

此影片說明如何設定循環傳送和排程器活動。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

其他Campaign Classic操作說明影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
