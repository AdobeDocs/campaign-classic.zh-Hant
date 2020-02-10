---
title: 模組和常見問題
seo-title: 模組和常見問題
description: 模組和常見問題
seo-description: null
page-status-flag: never-activated
uuid: d53324ce-b6e2-40d7-932d-36ce4a6f5cf8
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: troubleshooting
discoiquuid: a44f5e71-3f9b-4d02-8b7a-a9782bb6bdd8
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 20f835c357d016643ea1f3209ee4dfb6d3239f90

---


# 模組和常見問題{#modules-and-frequent-issues}

以下是受頻繁問題影響的模組清單：

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
   <td> 匯出 </td> 
   <td> 執行導出進程<br /> </td> 
   <td> 排程此匯出的運算子需要重新啟動它。 Delta或完全重新啟動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 導入 </td> 
   <td> 執行導入進程<br /> </td> 
   <td> 排程此匯出的運算子需要重新啟動它。 檢查資料庫是否有重複項。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 彈回郵箱的閱讀<br /> </td> 
   <td> 如果不再轉發彈回郵件，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 傳送電子郵件<br /> </td> 
   <td> 如果不再發送郵件，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> 維護MTA連接統計資訊<br /> </td> 
   <td> 如果不再發送郵件，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 日誌寫入<br /> </td> 
   <td> 如果日誌檔案中缺少某些日誌，請檢查以確保模組使用埠6666。 請參閱 <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">開啟埠清單</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤 </td> 
   <td> 合併和檢索跟蹤日誌<br /> </td> 
   <td> 如果追蹤記錄不再轉送，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 跟蹤日誌寫入和清除伺服器<br /> </td> 
   <td> 如果跟蹤日誌不再轉發，並且伺服器上的檔案中沒有日誌的跟蹤，請檢查此模組。 請參閱追 <a href="../../production/using/tracking-logs-issues.md" target="_blank">蹤記錄問題</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 監視 </td> 
   <td> 啟動和監視實例<br /> </td> 
   <td> 如果未啟動進程，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> 應用程式伺服器（HTTP和SOAP）<br /> </td> 
   <td> 如果控制台和Web連接無法工作，請檢查此模組並觸發 <strong>xtk:session</strong> type錯誤<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流實例的執行。<br /> </td> 
   <td> 如果遇到任何問題，請重新啟動此模組。 如有必要，請應用此過程來提高日誌精度，如「日誌精 <a href="../../production/using/log-precision.md" target="_blank">度</a> 」部分所述。<br /> </td> 
  </tr> 
 </tbody> 
</table>

