---
product: campaign
title: 模組和常見問題
description: 模組和常見問題
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
badge-v7-prem: label="on-premise & hybrid" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html" tooltip="Applies to on-premise and hybrid deployments only"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 4661688a22bd1a82eaf9c72a739b5a5ecee168b1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 6%

---

# 模組和常見問題{#modules-and-frequent-issues}



下面列出了受頻繁問題影響的模組：

<table> 
 <thead> 
  <tr> 
   <th> 模組 </th> 
   <th> 執行範圍 </th> 
   <th> 疑難排解 </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 出口 </td> 
   <td> 執行導出進程<br /> </td> 
   <td> 計畫此導出的操作員需要重新啟動它。 增量或完全重新啟動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 導入 </td> 
   <td> 執行導入進程<br /> </td> 
   <td> 計畫此導出的操作員需要重新啟動它。 檢查資料庫中是否有重複項。<br /> </td> 
  </tr> 
  <tr> 
   <td> 郵件 </td> 
   <td> 彈回郵箱的閱讀<br /> </td> 
   <td> 如果已轉發郵件，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 發送電子郵件<br /> </td> 
   <td> 如果郵件不再發送，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> 統計 </td> 
   <td> 維護MTA連接統計<br /> </td> 
   <td> 如果郵件不再發送，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslog </td> 
   <td> 日誌寫入<br /> </td> 
   <td> 如果日誌檔案中缺少某些日誌，請檢查以確保模組使用埠6666。 請參閱 <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">開啟埠清單</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤 </td> 
   <td> 整合和檢索跟蹤日誌<br /> </td> 
   <td> 如果跟蹤日誌不再轉發，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> 跟蹤日誌 </td> 
   <td> 跟蹤日誌寫入和清除伺服器<br /> </td> 
   <td> 如果跟蹤日誌不再轉發並且伺服器上的檔案中沒有日誌跟蹤，請檢查此模組。 請參閱 <a href="../../production/using/tracking-logs-issues.md" target="_blank">跟蹤日誌問題</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 監視 </td> 
   <td> 啟動和監視實例<br /> </td> 
   <td> 如果沒有進程啟動，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> 網 </td> 
   <td> 應用程式伺服器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web連接不工作並觸發 <strong>xtk：會話</strong> 類型錯誤<br /> </td> 
  </tr> 
  <tr> 
   <td> wf伺服器 </td> 
   <td> 控制工作流實例執行。<br /> </td> 
   <td> 如果遇到任何問題，請重新啟動此模組。 如有必要，請應用此過程以提高中詳細介紹的日誌的精確度 <a href="../../production/using/log-precision.md" target="_blank">對數精度</a> 的子菜單。<br /> </td> 
  </tr> 
 </tbody> 
</table>
