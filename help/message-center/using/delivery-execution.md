---
title: 傳送執行
seo-title: 傳送執行
description: 傳送執行
seo-description: null
page-status-flag: never-activated
uuid: d4f4cea7-783b-45d3-b004-297104f0a906
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: message-center
content-type: reference
topic-tags: event-processing
discoiquuid: afb375de-2de3-47ad-8b37-664cc04864e8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: bc227c2da2e8b1a78714748809ad40bbcefe0458

---


# 傳送執行{#delivery-execution}

>[!NOTE]
>
>MTA會優先處理交易訊息，而非其他傳送。

在執行例項上，一旦濃縮階段完成且傳送範本已連結至事件，傳送。 所有傳送都會分組在資料 **[!UICONTROL Administration > Production > Message Center > Default > Deliveries]** 夾中。

![](assets/messagecenter_deliveries_execinstances_001.png)

依預設，會依傳送月份將它們排序為子資料夾。

可以在消息模板屬性中更改此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>若是代管或混合式安裝，如果您已升級至「增強MTA」，所有交易訊息也可能會隨Adobe Campaign Enhanced MTA一起傳送，以改善傳遞能力、吞吐量和彈回處理。 所有影響與標準行銷訊息的影響相同，並在 [Adobe Campaign Enhanced MTA檔案中詳細說明](https://helpx.adobe.com/campaign/kb/campaign-enhanced-mta.html) 。