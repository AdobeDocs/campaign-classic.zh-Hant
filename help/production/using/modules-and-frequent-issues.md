---
product: campaign
title: 模組和常見問題
description: 模組和常見問題
feature: Monitoring, Troubleshooting
badge-v7-prem: label="內部部署和混合" type="Caution" url="https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/architecture-and-hosting-models/hosting-models-lp/hosting-models.html?lang=zh-Hant" tooltip="僅適用於內部部署和混合部署"
audience: production
content-type: reference
topic-tags: troubleshooting
exl-id: dbd50178-0a16-46ed-bfad-47beb3c2a420
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 7%

---

# 模組和常見問題{#modules-and-frequent-issues}



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
   <td> 匯出程式的執行<br /> </td> 
   <td> 排程此匯出的操作員需要重新啟動它。 差異或完整重新啟動。<br /> </td> 
  </tr> 
  <tr> 
   <td> 匯入 </td> 
   <td> 匯入程式的執行<br /> </td> 
   <td> 排程此匯出的操作員需要重新啟動它。 檢查資料庫是否有重複專案。<br /> </td> 
  </tr> 
  <tr> 
   <td> inMail </td> 
   <td> 正在讀取退信箱<br /> </td> 
   <td> 如果退回郵件不再轉寄，則檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> mta </td> 
   <td> 傳送電子郵件<br /> </td> 
   <td> 如果郵件已不再傳送，則檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> stat </td> 
   <td> 維護MTA連線統計資料<br /> </td> 
   <td> 如果郵件已不再傳送，則檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> syslogd </td> 
   <td> 記錄檔寫入<br /> </td> 
   <td> 如果記錄檔中缺少某些記錄，請檢查以確定模組使用連線埠6666。 請參閱 <a href="../../production/using/general-architecture.md#list-of-open-ports" target="_blank">開啟的連線埠清單</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 追蹤 </td> 
   <td> 合併和擷取追蹤記錄<br /> </td> 
   <td> 如果追蹤記錄不再轉送，則檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> trackinglogd </td> 
   <td> 追蹤記錄檔寫入和清除伺服器<br /> </td> 
   <td> 如果不再轉送追蹤記錄且伺服器上的檔案中沒有記錄追蹤，則檢查此模組。 請參閱 <a href="../../production/using/tracking-logs-issues.md" target="_blank">追蹤記錄問題</a>.<br /> </td> 
  </tr> 
  <tr> 
   <td> 看門狗 </td> 
   <td> 啟動和監視執行個體<br /> </td> 
   <td> 如果未啟動任何程式，則檢查此模組。<br /> </td> 
  </tr> 
  <tr> 
   <td> 網頁 </td> 
   <td> 應用程式伺服器（HTTP和SOAP）<br /> </td> 
   <td> 如果主控台和Web連線無法運作並觸發 <strong>xtk：session</strong> 型別錯誤<br /> </td> 
  </tr> 
  <tr> 
   <td> wfserver </td> 
   <td> 控制工作流程執行個體的執行。<br /> </td> 
   <td> 如果您遇到任何問題，請重新啟動此模組。 如有必要，請套用程式來提高中詳述的記錄精確度 <a href="../../production/using/log-precision.md" target="_blank">記錄精確度</a> 區段。<br /> </td> 
  </tr> 
 </tbody> 
</table>
