---
product: campaign
title: 持續傳遞
description: 持續傳遞
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 6%

---

# 持續傳遞{#continuous-delivery}

**連續傳送**&#x200B;類型動作可讓您將新收件者新增至現有傳送。 此傳送類型可避免您每次都需建立新傳送：此模式通常更有效率，尤其是對於需要時發送的低流量警報或通知。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#continuous-delivery-video)

在傳遞範本層級，您可以指定指令碼，以計算相關傳送的標籤（和促銷活動資料夾）。 如果指令碼會計算尚未存在的傳送，則會即時建立。

![](assets/edit_diffusion_fil.png)

**[!UICONTROL Process errors]**&#x200B;選項顯示特定轉變，當產生錯誤時，該轉變將被激活。 在這種情況下，工作流程不會進入錯誤模式並繼續執行。

考慮的錯誤是檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

此選項不會處理與活動配置相關的錯誤，即無效值。

## 輸入參數{#input-parameters}

* tableName
* 綱要

每個入站事件都必須指定由這些參數定義的目標。

僅當選取&#x200B;**[!UICONTROL Specified by the inbound event]**&#x200B;選項時。

## 輸出參數{#output-parameters}

* tableName
* 綱要
* recCount

這組三個值可識別即時傳送所產生的目標。 **[!UICONTROL tableName]** 是儲存目標標識符的表的名稱， **[!UICONTROL schema]** 是母體（通常為nms:recipient）的模式， **[!UICONTROL recCount]** 是表中的元素數。

與補體相關聯的轉變具有相同的參數。

## 如何設定連續傳送

本節說明如何設定持續傳送。

**連續傳送**&#x200B;可讓您將新收件者新增至現有傳送，並避免每次新增收件者時都必須建立新傳送。 您可以直接在促銷活動工作流程中更新創作內容，而且會更新傳遞範本「資源」資料夾中的範本。

持續傳送會建立SINGLE傳送和傳送記錄(broadLog)及追蹤記錄，以參考每次執行傳送時都會新增一個傳送。

![持續傳遞](assets/delivery_continuous.jpg)

## 教學課程影片{#continuous-delivery-video}

此影片說明如何使用增量查詢來設定連續傳送。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

其他Campaign Classic操作說明影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
