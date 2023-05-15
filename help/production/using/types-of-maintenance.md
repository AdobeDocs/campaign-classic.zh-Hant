---
product: campaign
title: 維護類型
description: 維護類型
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=en" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: a5762cd21a1a6d5a5f3a10f53a5d1f43542d99d4
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 2%

---

# 維護類型{#types-of-maintenance}



## 應用程式維護 {#application-maintenance}

Adobe Campaign提供內建的工作流程，可讓您排程特定資料庫維護任務：the **資料庫清理工作流程**. 此工作流程會執行下列工作：

* 刪除過期記錄，
* 刪除失效對象的孤立記錄和狀態重新初始化，
* 更新資料庫統計資訊。

>[!IMPORTANT]
>
>請注意，清理任務主要涉及應用程式級維護，而非RDBMS級維護（統計資訊更新除外）。 但是，資料庫上需要維護操作。 即使資料庫清理工作流成功運行，這並不意味著資料庫已得到最佳調整。

## 技術維護 {#technical-maintenance}

資料庫清理工作流不包含任何資料庫維護工具：由您負責組織維護。 若要這麼做，您可以：

* 與資料庫管理員合作，使用第三方工具設定資料庫維護，
* 使用Adobe Campaign工作流程引擎來排程及追蹤這些維護活動。

這些維護程式必須定期執行，並應包括：

* 重新索引頻繁更新的表，
* 精簡/重建表以避免碎片。

### 維護計畫 {#maintenance-schedule}

您需要找到執行這些維護活動的適當位置。 它們在運行時可能會嚴重影響資料庫效能，甚至會阻止應用程式（由於鎖定）。

這些任務通常在低活動期間每週運行一次，這些活動不與備份、資料重新載入或聚合計算相衝突。 一些高度請求的系統需要更頻繁的維護。

更深入的維護（如完整表重建）可以每月執行一次，最好在應用程式完全停止的情況下執行，因為系統無論如何都不可用。

### 重建表 {#rebuilding-a-table}

有數種策略可供使用：

<table> 
 <thead> 
  <tr> 
   <th> 操作 </th> 
   <th> 說明 </th> 
   <th> 好處 </th> 
   <th> 缺點 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 聯機碎片整理<br /> </td> 
   <td> 大多數資料庫引擎都提供碎片整理方法。<br /> </td> 
   <td> 只需使用資料庫碎片整理方法即可。 這些方法通常會在碎片整理期間鎖定資料，以處理完整性問題。<br /> </td> 
   <td> 根據資料庫，這些碎片整理方法可以作為RDBMS選項(Oracle)提供，並且並不總是處理較大表的最有效方法。<br /> </td> 
  </tr> 
  <tr> 
   <td> 轉儲和還原<br /> </td> 
   <td> 將表轉儲到檔案，刪除資料庫中的表，然後從轉儲中還原。<br /> </td> 
   <td> 這是對表進行碎片整理的最簡單方法。 也是資料庫幾乎已滿時的唯一解決方案。<br /> </td> 
   <td> 由於表被刪除並重新建立，因此即使處於只讀模式，應用程式也無法保持聯機狀態（該表在恢復階段不可用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 複製、更名和刪除<br /> </td> 
   <td> 這會建立表及其索引的副本，然後刪除現有的副本，並重新命名副本以取代該副本。<br /> </td> 
   <td> 此方法比第一種方法快，因為它生成的IO較少（沒有作為檔案的拷貝並從此檔案讀取）。<br /> </td> 
   <td> 需要兩倍的空間。<br /> 必須停止進程期間寫入表的所有活動進程。 但是，讀取過程不會受影響，因為表在重建後的最後時刻被交換。 <br /> </td> 
  </tr> 
 </tbody> 
</table>
