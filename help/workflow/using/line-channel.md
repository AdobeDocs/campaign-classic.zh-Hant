---
solution: Campaign Classic
product: campaign
title: LINE 頻道
description: LINE 頻道
audience: workflow
content-type: reference
topic-tags: technical-workflows
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 11%

---


# LINE 頻道{#line-channel}

以下詳細說明的工作流程預設會隨 **LINE channel** 模組一起安裝。 For more on this module, refer to this [section](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2存取Token更新</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> 此工作流程會將存取Token重新整理為LINE V2。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除被阻止的LINE用戶</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 此工作流程可確保在LINE V2用戶封鎖180天的LINE正式帳戶後，刪除其資料。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID到LineUserID移轉</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> 此工作流將生成LINE V2用戶的ID，以便從LINE V1遷移到LINE V2。<br /> </td> 
  </tr> 
 </tbody> 
</table>

