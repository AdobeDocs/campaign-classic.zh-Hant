---
product: campaign
title: 設定階段
description: 設定階段
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 設定階段{#setup-stages}

![](../../assets/v7-only.svg)

基本原則是將網頁追蹤標籤插入網站的特定頁面。

標籤有兩種類型：

* **WEB**:此標籤會告訴您是否已造訪過頁面，
* **交易**:操作方式類似web標籤，但可能會新增產生的業務量資訊，例如（交易金額、購買的項目數等）。

套用下列步驟以設定這些標籤：

1. 識別您要追蹤的頁面，並判斷其類型（WEB或TRANSACTION）。
1. 決定您要收集哪些其他資訊，並擴充 **nms:webTrackingLog** 此資訊說明的架構。 預設情況下，此架構可以儲存每個交易的交易金額和項目數。
1. 建立網頁追蹤標籤。 執行此作業有兩種方式：

   * 在您的Adobe Campaign平台中插入與這些頁面對應的URL，然後產生並擷取相關的網頁追蹤標籤(從 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 客戶端控制台的節點)。
   * 自行在「即時建立」模式中建立網頁追蹤標籤：與這些頁面對應的URL會自動插入您的Adobe Campaign平台。

1. 在您要追蹤的頁面中以靜態或動態方式新增這些標籤。

   >[!NOTE]
   >
   >所有WEB類型標籤都可依原樣新增至您的網站頁面。 必須動態修改或添加交易標籤，以包含附加資訊（金額、項目等）。

**範例**:

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```
