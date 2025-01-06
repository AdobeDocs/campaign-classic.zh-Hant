---
product: campaign
title: 維護類型
description: 維護類型
feature: Monitoring
badge-v7-prem: label="僅限內部部署/混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: database-maintenance
exl-id: 08e179aa-fd83-4c0a-879e-ab7aec168d92
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 2%

---

# 維護類型{#types-of-maintenance}



## 應用程式維護 {#application-maintenance}

Adobe Campaign提供內建的工作流程，可讓您排程某些資料庫維護工作： **資料庫清理工作流程**。 此工作流程會執行下列工作：

* 刪除過期的記錄，
* 刪除孤立的記錄以及重新初始化過期物件的狀態，
* 更新資料庫統計資料。

>[!IMPORTANT]
>
>請注意，清理任務主要處理應用程式層級的維護，而非RDBMS層級的維護（統計資料更新除外）。 不過，需要針對資料庫執行維護操作。 即使資料庫清理工作流程成功執行，這並不表示資料庫已最佳調整。

## 技術維護 {#technical-maintenance}

資料庫清理工作流程不包含任何資料庫維護工具：由您來組織維護。 若要這麼做，您可以：

* 與您的資料庫管理員合作，使用協力廠商工具設定資料庫維護，
* 使用Adobe Campaign工作流程引擎來排程及追蹤這些維護活動。

這些維護程式必須定期執行，並應包括以下內容：

* 重新索引經常更新的資料表，
* 壓縮/重建資料表以避免片段。

### 維護排程 {#maintenance-schedule}

您需要尋找適當的位置來執行這些維護活動。 它們可能會嚴重影響執行時的資料庫效能，甚至封鎖應用程式（由於鎖定）。

這些工作通常會在低活動期間每週執行一次，而不會與備份、資料重新載入或彙總計算發生衝突。 有些系統受到強烈要求，需要更頻繁的維護。

更深入的維護（例如完整表格重建）可每月執行一次，最好是讓應用程式完全停止，因為系統無論如何都無法使用。

### 重建表格 {#rebuilding-a-table}

有幾種策略可供使用：

<table> 
 <thead> 
  <tr> 
   <th> 作業 </th> 
   <th> 說明 </th> 
   <th> 好處 </th> 
   <th> 缺點 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 線上磁碟重組<br /> </td> 
   <td> 大部分的資料庫引擎都提供磁碟重組方法。<br /> </td> 
   <td> 只要使用資料庫磁碟重組方法即可。 這些方法通常會在磁碟重組期間鎖定資料，以解決完整性問題。<br /> </td> 
   <td> 視資料庫而定，這些磁碟重組方法可作為RDBMS選項(Oracle)提供，而且並非總是處理大型資料表的最有效率。<br /> </td> 
  </tr> 
  <tr> 
   <td> 傾印及還原<br /> </td> 
   <td> 將資料表傾印到檔案、刪除資料庫中的資料表，並從傾印還原。<br /> </td> 
   <td> 這是重組表格的最簡單方法。 也是資料庫幾乎已滿時的唯一解決方案。<br /> </td> 
   <td> 因為資料表已被刪除並重新建立，所以即使是在唯讀模式中，應用程式也無法保持連線（資料表在還原階段無法使用）。<br /> </td> 
  </tr> 
  <tr> 
   <td> 複製、重新命名及卸除<br /> </td> 
   <td> 這樣會建立表格及其索引的復本，然後捨棄現有的復本，並重新命名復本以取而代之。<br /> </td> 
   <td> 此方法比第一種方法更快，因為它產生的IO較少（沒有檔案復本，且不會從此檔案讀取）。<br /> </td> 
   <td> 需要兩倍的空間。<br />必須停止在處理期間寫入資料表的所有作用中處理序。 不過，讀取程式不會受到影響，因為表格在重建後的最後時刻會被交換。<br /> </td> 
  </tr> 
 </tbody> 
</table>
