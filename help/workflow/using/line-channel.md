---
product: campaign
title: LINE頻道
description: LINE頻道
feature: Workflows
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 2%

---


# LINE頻道{#line-channel}



以下詳述的工作流程會隨 **LINE頻道** 模組（預設）。 如需此模組的詳細資訊，請參閱此 [區段](../../delivery/using/line-channel.md).

<table> 
 <tbody> 
  <tr> 
   <td> <strong>標籤</strong><br /> </td> 
   <td> <strong>內部名稱</strong><br /> </td> 
   <td> <strong>說明</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">LINE V2存取權杖更新</span> <br /> </td> 
   <td> <span class="uicontrol">updateLineV2AccessToken</span> <br /> </td> 
   <td> 此工作流程會將存取Token重新整理至LINE V2。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">刪除封鎖的LINE使用者</span> <br /> </td> 
   <td> <span class="uicontrol">deleteBlockedLineUsersV2</span> <br /> </td> 
   <td> 此工作流程確保LINE V2使用者的資料在封鎖LINE正式帳戶180天後會被刪除。<br /> </td> 
  </tr> 
  <tr> 
   <td> <span class="uicontrol">MID到LineUserID移轉</span> <br /> </td> 
   <td> <span class="uicontrol">MIDToUserIDMigration</span> <br /> </td> 
   <td> 此工作流程會產生LINE V2使用者ID，以便從LINE V1移轉至LINE V2。<br /> </td> 
  </tr> 
 </tbody> 
</table>

