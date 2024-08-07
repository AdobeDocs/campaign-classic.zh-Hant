---
product: campaign
title: 設定階段
description: 設定階段
feature: Configuration
role: Data Engineer, Developer
exl-id: a5ae0b61-3377-46d9-a327-6c897eeda770
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 2%

---

# 設定階段{#setup-stages}

基本原則是在網站的特定頁面中插入網頁追蹤標籤。

有兩種型別的標籤：

* **網頁**：此標籤會告訴您網頁是否已被瀏覽，
* **TRANSACTION**：運作方式類似網頁標籤，但可能會新增有關產生的業務量的資訊，例如（交易金額、購買的專案數量等）。

套用下列步驟以設定這些標籤：

1. 識別您要追蹤的頁面，並決定其型別（網頁或交易）。
1. 決定您要收集哪些其他資訊，並使用此資訊的說明來擴充&#x200B;**nms：webTrackingLog**&#x200B;結構描述。 依預設，此結構描述可以儲存每筆交易的交易金額和專案數。
1. 建立網頁追蹤標籤。 有兩種方法可以達成此目的：

   * 將與這些頁面相對應的URL插入您的Adobe Campaign平台，然後產生並擷取關聯的網頁追蹤標籤（從使用者端主控台的&#x200B;**[!UICONTROL Campaign execution>Resources>Web tracking tags]**&#x200B;節點）。
   * 在「即時建立」模式中自行建立網頁追蹤標籤：系統會自動將對應至這些頁面的URL插入您的Adobe Campaign平台。

1. 以靜態或動態方式在您要追蹤的頁面中新增這些標籤。

   >[!NOTE]
   >
   >所有WEB型別的標籤都可以新增至您網站的頁面。 TRANSACTION標籤必須動態修改或新增，才能包含其他資訊（金額、專案等）。

**範例**：

```
<script type="text/javascript">
var _f = "nmsWebTracking"
var _t = window.location.href.match(/.*://[^/]*(/[^?#&]*)/)[1] + "|w|" + _f
document.write("<img height='0' width='0' alt='' src='" +
window.location.protocol + "//tsupport/r/" +
Math.random().toString() + "?tagid=" + escape(_t) + "'/>")
</script>
```
