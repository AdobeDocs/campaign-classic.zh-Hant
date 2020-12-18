---
solution: Campaign Classic
product: campaign
title: 持續傳遞
description: 持續傳遞
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 20dcdd91d71158bc373db68c3f61f6808b240bd2
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 6%

---


# 持續傳遞{#continuous-delivery}

**連續傳送**&#x200B;類型動作可讓您將新收件者新增至現有傳送。 此傳送類型可避免您每次都必須建立新傳送：此模式通常更有效率，尤其是對於需要時發送的低容量警報或通知。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#continuous-delivery-video)

在傳送範本層級，您可以指定指令碼來計算相關傳送的標籤（和促銷活動資料夾）。 如果指令檔計算尚未存在的傳送，則會即時建立。

![](assets/edit_diffusion_fil.png)

**[!UICONTROL Process errors]**&#x200B;選項顯示特定轉場，當產生錯誤時，該轉場將被啟動。 在這種情況下，工作流不會進入錯誤模式並繼續執行。

考慮到的錯誤是檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

此選項不處理與活動配置相關的錯誤，即無效值。

## 輸入參數{#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

僅當選取&#x200B;**[!UICONTROL Specified by the inbound event]**&#x200B;選項時。

## 輸出參數{#output-parameters}

* tableName
* 架構
* recCount

這組三個值可識別由即時傳送產生的目標。 **[!UICONTROL tableName]** 是儲存目標標識符的表的名稱，是 **[!UICONTROL schema]** 人口（通常是nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素數。

與補體相關的過渡具有相同的參數。

## 如何設定連續傳遞

本節說明如何設定連續傳送。

**連續傳送**&#x200B;可讓您將新收件者新增至現有傳送，並避免每次新增收件者時都必須建立新傳送。 您可以直接在促銷活動工作流程中更新創作內容，並會在傳送範本「資源」檔案夾中更新範本。

持續傳送將建立SINGLE傳送和傳送記錄檔(broadLog)和追蹤記錄檔，以參考每次執行時會新增一個傳送。

![持續傳送](assets/delivery_continuous.jpg)

## 教學課程影片{#continuous-delivery-video}

此視訊說明如何設定具有遞增查詢的連續傳送。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

其他Campaign Classic操作視訊可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。