---
title: 持續傳送
seo-title: 持續傳送
description: 持續傳送
seo-description: null
page-status-flag: never-activated
uuid: af8b4582-299e-47f9-9819-987b35db94ab
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 9d80be19-8dde-4278-ab5f-23f364fe422e
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 持續傳送{#continuous-delivery}

「連 **續傳送類型** 」動作可讓您將新收件者新增至現有的傳送。 此傳送類型可避免您每次都必須建立新傳送：此模式通常更有效率，尤其是對於需要時發送的低容量警報或通知。 在傳送範本層級，您可以指定指令碼來計算相關傳送的標籤（和促銷活動資料夾）。 如果指令檔計算尚未存在的傳送，則會即時建立。

![](assets/edit_diffusion_fil.png)

選 **[!UICONTROL Process errors]** 項會顯示特定轉場，當產生錯誤時即會啟動。 在這種情況下，工作流不會進入錯誤模式並繼續執行。

考慮到的錯誤是檔案系統錯誤（無法移動檔案、無法訪問目錄等）。

此選項不處理與活動配置相關的錯誤，即無效值。

## 輸入參數 {#input-parameters}

* tableName
* 架構

每個傳入事件都必須指定由這些參數定義的目標。

僅當選取 **[!UICONTROL Specified by the inbound event]** 了選項時。

## 輸出參數 {#output-parameters}

* tableName
* 架構
* recCount

這組三個值可識別由即時傳送產生的目標。 **[!UICONTROL tableName]** 是儲存目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常是nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補體相關的過渡具有相同的參數。
