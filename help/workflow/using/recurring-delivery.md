---
solution: Campaign Classic
product: campaign
title: 重複傳送
description: 進一步瞭解循環傳送工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 7%

---


# 重複傳送{#recurring-delivery}

活 **[!UICONTROL Recurring delivery]** 動可讓您設定促銷活動專屬的傳送範本事件。

此活動僅可從促銷活動中 **[!UICONTROL Targeting and workflows]** 找到的標籤中使用。

操作步驟：

1. 選擇活動將依據的傳送範本。

   ![](assets/recurring_delivery_001.png)

1. 設定傳送範本。

此活動的設定程式類似於根據可用選項建立傳送範本的程式。 如需詳細資訊，請參閱本[區段](../../delivery/using/about-templates.md)。

有關使用此活動的示例，請參閱此 [部分](../../workflow/using/sending-a-birthday-email.md#creating-a-recurring-delivery-in-a-targeting-workflow)。

## 如何設定循環傳送

循 **環傳送** ，每次執行時都會建立新的傳送例項。 例如，如果排程工作流程每週執行一次，則一年後會產生52次傳送。 這也表示廣泛的記錄檔和追蹤記錄檔將依每個傳送例項分開。

![循環傳送](assets/delivery_recurring.jpg)

此影片說明如何設定循環傳送和排程器活動。

>[!VIDEO](https://video.tv.adobe.com/v/25040?quality=12)

>[!NOTE]
>
>無法從文字活動傳送 **[!UICONTROL Recurring delivery]** 證明。\
>若要透過促銷活動工作流程直接建立傳送，請使用預先設定的渠道特定活動(例如 **[!UICONTROL Email delivery]**)。
