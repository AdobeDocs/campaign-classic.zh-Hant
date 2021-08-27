---
product: campaign
title: 模組和常見問題
description: 模組和常見問題
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 5%

---

# 模組和常見問題{#modules-and-frequent-issues}

![](../../assets/v7-only.svg)

以下是受常見問題影響的模組清單：

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
   <td> 排程此匯出作業的運算子需要重新啟動。 增量或完全重新啟動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 匯入 </td> 
   <td> 執行導入進程<br /> </td> 
   <td> 排程此匯出作業的運算子需要重新啟動。 檢查資料庫中是否有重複項。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 讀取退信盒<br /> </td> 
   <td> 如果退回郵件不再轉發，請檢查此模組。<br /> </td> 
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
   <td> 如果日誌檔案中缺少某些日誌，請檢查以確保模組使用埠6666。 請參閱<a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">開啟埠清單</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤 </td> 
   <td> 合併和檢索跟蹤日誌<br /> </td> 
   <td> 如果跟蹤日誌不再轉發，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 跟蹤日誌寫入和清除伺服器<br /> </td> 
   <td> 如果追蹤記錄檔不再轉送，且伺服器上的檔案中沒有記錄檔的追蹤，請檢查此模組。 請參閱<a href="../../production/using/tracking-logs-issues.md" target="_blank">追蹤記錄問題</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> 監視 </td> 
   <td> 啟動和監視實例<br /> </td> 
   <td> 如果沒有進程啟動，請檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> web </td> 
   <td> 應用程式伺服器（HTTP和SOAP）<br /> </td> 
   <td> 如果主控台和Web連線無法運作，請檢查此模組並觸發<strong>xtk:session</strong>類型錯誤<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流實例執行。<br /> </td> 
   <td> 如果遇到任何問題，請重新啟動此模組。 如有必要，請應用該過程以提高<a href="../../production/using/log-precision.md" target="_blank">日誌精度</a>部分中詳述的日誌的精度。<br /> </td> 
  </tr> 
 </tbody> 
</table>
