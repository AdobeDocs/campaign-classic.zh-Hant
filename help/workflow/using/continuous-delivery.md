---
product: campaign
title: 持續傳遞
description: 持續傳遞
feature: Workflows, Channels Activity
exl-id: 9c228cdb-331e-476e-a24c-3c7e23add3bf
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 10%

---

# 持續傳遞{#continuous-delivery}

![](../../assets/common.svg)

A **連續交付** 「類型」(type)操作允許您將新收件人添加到現有交貨中。 此交貨類型避免您每次都必須建立新交貨：此模式通常更有效，特別是對於在需要時發送的低容量警報或通知。

![](assets/do-not-localize/how-to-video.png) [在影片中探索此功能](#continuous-delivery-video)

在交貨模板層，您可以指定一個指令碼來計算關聯交貨的標籤（和市場活動資料夾）。 如果指令碼計算尚不存在的傳遞，則會即時建立它。

![](assets/edit_diffusion_fil.png)

的 **[!UICONTROL Process errors]** 選項顯示在生成錯誤時將激活的特定過渡。 在這種情況下，工作流不會進入錯誤模式並執行。

考慮的錯誤包括檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

此選項不處理與活動配置相關的錯誤，即無效值。

## 輸入參數 {#input-parameters}

* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

僅當 **[!UICONTROL Specified by the inbound event]** 的雙曲餘切值。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識了由即時交貨產生的目標。 **[!UICONTROL tableName]** 是保存目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補碼相關聯的過渡具有相同的參數。

## 如何設定連續傳送

本節介紹如何設定連續交貨。

的 **連續交付** 允許您將新收件人添加到現有遞送中，並避免每次添加新收件人時必須建立新遞送。 您可以直接在市場活動工作流中更新創意內容，並將更新交貨模板「資源」資料夾中的模板。

連續傳遞將建立SINGLE傳遞和傳遞日誌(broadLog)和跟蹤日誌，這些日誌引用每次執行一個傳遞時都添加一個。

![持續傳遞](assets/delivery_continuous.jpg)

## 教程視頻 {#continuous-delivery-video}

此影片說明如何使用增量查詢來設定持續傳送。

>[!VIDEO](https://video.tv.adobe.com/v/25039?quality=12)

可提供其他Campaign Classic操作視頻 [這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)。
