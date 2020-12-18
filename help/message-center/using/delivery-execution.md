---
solution: Campaign Classic
product: campaign
title: 傳遞執行
description: 傳遞執行
audience: message-center
content-type: reference
topic-tags: event-processing
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 8%

---


# 傳遞執行{#delivery-execution}

>[!NOTE]
>
>MTA會優先處理交易訊息，而非其他傳送。

在執行例項上，一旦濃縮階段完成且傳送範本已連結至事件，傳送。 所有傳送都會分組在&#x200B;**[!UICONTROL Administration > Production > Message Center > Default > Deliveries]**&#x200B;資料夾中。

![](assets/messagecenter_deliveries_execinstances_001.png)

依預設，會依傳送月份將它們排序為子資料夾。

可以在消息模板屬性中更改此排序，如下所示。

![](assets/messagecenter_deliveries_properties_001.png)

>[!NOTE]
>
>若是代管或混合式安裝，如果您已升級至「增強MTA」，所有交易訊息也可能會隨Adobe Campaign Enhanced MTA一起傳送，以改善傳遞能力、吞吐量和彈回處理。 所有影響與標準行銷訊息的影響相同，並詳見[Adobe Campaign Enhanced MTA](https://helpx.adobe.com/tw/campaign/kb/acc-campaign-enhanced-mta.html)檔案。