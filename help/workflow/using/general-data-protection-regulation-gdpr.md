---
product: campaign
title: 隱私權資料保護規範工作流程
description: 進一步瞭解隱私權資料保護規則工作流程
hide: true
feature: Workflows, Privacy
product_v2:
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
    internal-label: Campaign
  - id: fd6e6e36-54e4-4f1a-96fc-1a750e400d50
    internal-label: Campaign Classic v7
feature_v2:
  - id: a658c786-869b-4194-a780-2594d663adda
    internal-label: Data management
  - id: a7760dfc-5c44-4d77-bb68-c50b1e265c93
    internal-label: Security and privacy
subfeature_v2:
  - id: fcb46c0f-76e1-48bc-9dd0-fcf9d97526cf
    internal-label: Workflows
  - id: ac9c0a9c-8a76-4419-bd64-9c34c5782666
    internal-label: Privacy
source-git-commit: a43e591a565a18d79f583d975e3e812c5435b0c0
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 7%
---

# 隱私權資料保護規範{#general-data-protection-regulation-gdpr}



依預設，以下詳細描述的工作流程會與&#x200B;**隱私權資料保護規範**&#x200B;模組一併安裝。 如需此模組的詳細資訊，請參閱此[文章](https://helpx.adobe.com/tw/campaign/kb/acc-privacy.html)。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">收集隱私權要求</span> <br /> </td> 
   <td> <span class="uicontrol">collectPrivacyRequests</span> <br /> </td> 
   <td> 此工作流程會產生儲存在Adobe Campaign的收件者資料，並讓該資料可在隱私權請求的畫面中下載。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除隱私權要求資料</span> <br /> </td> 
   <td> <span class="uicontrol">deletePrivacyRequestsData</span> <br /> </td> 
   <td> 此工作流程會刪除收件者儲存在Adobe Campaign中的資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">隱私權要求清理</span> <br /> </td> 
   <td> <span class="uicontrol">cleanupPrivacyRequests</span> <br /> </td> 
   <td> 此工作流程會清除90天以前的存取要求檔案。<br /> </td> 
  </tr> 
 </tbody> 
</table>

