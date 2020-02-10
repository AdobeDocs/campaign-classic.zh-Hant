---
title: 維護類型
seo-title: 維護類型
description: 維護類型
seo-description: null
page-status-flag: never-activated
uuid: 44faee3d-0549-4f63-8fdc-b24e6de47bc4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: database-maintenance
discoiquuid: 4a436ccf-097c-43e6-9eda-492bada5512a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 579329d9194115065dff2c192deb0376c75e67bd

---


# 維護類型{#types-of-maintenance}

## 應用程式維護 {#application-maintenance}

Adobe Campaign提供內建的工作流程，可讓您排程特定資料庫維護工作：資料庫 **清理工作流**。 此工作流程會執行下列工作：

* 刪除過期記錄，
* 刪除失效對象的孤立記錄並重新初始化狀態，
* 更新資料庫統計資訊。

>[!CAUTION]
>
>請注意，清除任務主要涉及應用程式級別維護，而不是RDBMS級別維護（統計資料更新除外）。 但是，資料庫上需要維護操作。 即使資料庫清理工作流運行成功，但這並不意味著資料庫已得到優化。

## 技術維護 {#technical-maintenance}

資料庫清理工作流不包含任何資料庫維護工具：維護由您負責。 若要這麼做，您可以：

* 與資料庫管理員協作，使用第三方工具設定資料庫維護，
* 使用Adobe Campaign工作流程引擎來排程及追蹤這些維護活動。

這些維護程式必須定期執行，並應包括：

* 重新索引頻繁更新的表，
* 精簡／重建表以避免碎片化。

### 維護計畫 {#maintenance-schedule}

您需要找到執行這些維護活動的適當插槽。 它們在運行或甚至阻止應用程式（由於鎖定）時會嚴重影響資料庫效能。

這些任務通常在低活動期間每週運行一次，這些活動不會與備份、資料重新載入或聚合計算相衝突。 一些高度公開的系統需要更頻繁的維護。

更深入的維護，例如完整表格重建，每月可執行一次，最好是在應用程式完全停止時執行，因為系統無論如何都無法使用。

### 重建表 {#rebuilding-a-table}

有幾種策略可供使用：

<table> 
 <thead> 
  <tr> 
   <th> 操作 </th> 
   <th> 說明 </th> 
   <th> 優點 </th> 
   <th> 缺點 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 聯機碎片整理<br /> </td> 
   <td> 大多數資料庫引擎都提供了碎片整理方法。<br /> </td> 
   <td> 只需使用資料庫碎片整理方法。 這些方法通常通過在碎片整理期間鎖定資料來處理完整性問題。<br /> </td> 
   <td> 根據資料庫，這些碎片整理方法可以作為RDBMS選項(Oracle)提供，並不總是處理較大表時最有效的方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 轉儲和恢復<br /> </td> 
   <td> 將表轉儲到檔案，刪除資料庫中的表並從轉儲中恢復。<br /> </td> 
   <td> 這是對表進行碎片整理的最簡單方法。 也是資料庫幾乎已滿時的唯一解決方案。<br /> </td> 
   <td> 由於刪除並重新建立表，因此即使在只讀模式下，應用程式也無法保持聯機狀態（表在恢復階段不可用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 複製、重新命名和刪除<br /> </td> 
   <td> 這樣會建立表及其索引的副本，然後刪除現有的表並更名該副本以替代它。<br /> </td> 
   <td> 此方法比第一種方法更快，因為它生成的IO更少（沒有作為檔案的拷貝並從此檔案讀取）。<br /> </td> 
   <td> 需要兩倍的空間量。<br /> 必須停止在進程期間寫入表的所有活動進程。 但是，讀取過程不會受到影響，因為表在重建後的最後時刻被交換。 <br /> </td> 
  </tr> 
 </tbody> 
</table>

