---
product: campaign
title: 隱私權資料保護規範工作流程
description: 進一步瞭解隱私權資料保護規則工作流程
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
feature: Workflows, Privacy
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 9%

---


# 隱私權資料保護規範{#general-data-protection-regulation-gdpr}



以下詳述的工作流程會隨 **隱私權資料保護規範** 模組（預設）。 如需此模組的詳細資訊，請參閱此 [文章](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">收集隱私權請求</span> <br /> </td> 
   <td> <span class="uicontrol">Collectprivacyrequests</span> <br /> </td> 
   <td> 此工作流程會產生儲存在Adobe Campaign的收件者資料，並讓該資料可在隱私權請求的畫面中下載。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除隱私權請求資料</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 此工作流程會刪除收件者儲存在Adobe Campaign中的資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">隱私權請求清除</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 此工作流程會清除90天以前的存取請求檔案。<br /> </td> 
  </tr> 
 </tbody> 
</table>

