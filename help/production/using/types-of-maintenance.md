---
product: campaign
title: 維護類型
description: 維護類型
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# 維護類型{#types-of-maintenance}



## 應用程式維護 {#application-maintenance}

Adobe Campaign提供了內置工作流，讓您可以安排某些資料庫維護任務：這樣 **資料庫清理工作流**。 此工作流執行以下任務：

* 刪除過期記錄，
* 刪除孤立記錄並重新初始化過期對象的狀態，
* 更新資料庫統計資訊。

>[!IMPORTANT]
>
>請注意，清理任務主要處理應用程式級別維護，而不是RDBMS級別維護（統計資訊更新除外）。 但是，需要對資料庫執行維護操作。 即使資料庫清理工作流成功運行，這並不意味著資料庫得到了最佳調整。

## 技術維護 {#technical-maintenance}

資料庫清理工作流不包含任何資料庫維護工具：維護由您負責。 為此，您可以：

* 與資料庫管理員協作，使用第三方工具設定資料庫維護，
* 使用Adobe Campaign工作流引擎來安排和跟蹤這些維護活動。

這些維護程式必須定期執行，並應包括：

* 重新索引頻繁更新的表，
* 壓縮/重建表以避免碎片。

### 維護計畫 {#maintenance-schedule}

您需要找到執行這些維護活動的適當插槽。 它們在運行或甚至阻止應用程式（由於鎖定）時會嚴重影響資料庫效能。

這些任務通常在活動不與備份、資料重裝或聚合計算相衝突的低活動期間每週運行一次。 一些系統的頻繁請求需要更頻繁的維護。

可以每月執行一次更深入的維護，例如全表重建，最好是在應用程式完全停止的情況下執行，因為系統無論如何都不可用。

### 重建表 {#rebuilding-a-table}

有幾種策略可供選擇：

<table> 
 <thead> 
  <tr> 
   <th> 操作 </th> 
   <th> 說明 </th> 
   <th> 好處 </th> 
   <th> 缺陷 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 聯機碎片整理<br /> </td> 
   <td> 大多數資料庫引擎都提供碎片整理方法。<br /> </td> 
   <td> 只需使用資料庫碎片整理方法即可。 這些方法通常通過在碎片整理期間鎖定資料來解決完整性問題。<br /> </td> 
   <td> 根據資料庫的不同，這些碎片整理方法可以作為RDBMS選項(Oracle)提供，並且並不總是處理較大表的最有效方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 轉儲和恢復<br /> </td> 
   <td> 將表轉儲到檔案，刪除資料庫中的表並從轉儲中恢復。<br /> </td> 
   <td> 這是對表進行碎片整理的最簡單方法。 也是資料庫幾乎滿時唯一的解決方案。<br /> </td> 
   <td> 由於刪除並重新建立了表，因此即使在只讀模式下，應用程式也無法保持聯機狀態（在恢復階段該表不可用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 複製、更名和刪除<br /> </td> 
   <td> 這將建立表及其索引的副本，然後刪除現有副本並更名副本以取代它。<br /> </td> 
   <td> 此方法比第一種方法快，因為它生成的IO少（沒有作為檔案的副本，也沒有從此檔案中讀取）。<br /> </td> 
   <td> 需要兩倍的空間。<br /> 必須停止在進程期間寫入表的所有活動進程。 但是，讀取進程不會受到影響，因為表在重建後的最後時刻被交換。 <br /> </td> 
  </tr> 
 </tbody> 
</table>
