---
title: 設定階段
seo-title: 設定階段
description: 設定階段
seo-description: null
page-status-flag: never-activated
uuid: 4111a805-95ab-4e26-be51-2db1e5c20f57
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: setting-up-web-tracking
discoiquuid: 76174374-af73-4da0-b62b-6979bca0102b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 設定階段{#setup-stages}

基本原則是將網頁追蹤標籤插入網站的特定頁面。

標籤有兩種類型：

* **WEB**:此標籤會告訴您是否已瀏覽頁面，
* **交易**:運作方式類似Web標籤，但可能會新增有關所產生業務量的資訊，例如（交易金額、購買項目數等）。

套用下列步驟以設定這些標籤：

1. 識別您要追蹤的頁面，並判斷其類型（WEB或TRANSACTION）。
1. 確定您要收集的其他資訊，並使用此信 **息的說明擴展nms:webTrackingLog** 架構。 預設情況下，此方案可以儲存每個事務處理的事務處理金額和項目數。
1. 建立網頁追蹤標籤。 有兩種方法可以做到：

   * 在您的Adobe Campaign平台中插入與這些頁面對應的URL，然後產生並擷取相關的網頁追蹤標籤(從用戶端主控台 **[!UICONTROL Campaign execution>Resources>Web tracking tags]** 的節點)。
   * 在「即時建立」模式中自行建立網頁追蹤標籤：與這些頁面對應的URL會自動插入您的Adobe Campaign平台。

1. 在您要追蹤的頁面中以靜態或動態方式新增這些標籤。

   >[!NOTE]
   >
   >所有WEB類型標籤都可依原樣新增至您網站的頁面。 必須動態修改或添加TRANSACTION標籤，才能包含附加資訊（金額、項目等）。

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

