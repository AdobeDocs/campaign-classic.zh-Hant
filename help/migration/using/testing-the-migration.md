---
product: campaign
title: 測試移轉
description: 測試移轉
feature: Upgrade
audience: migration
content-type: reference
topic-tags: migration-procedure
hide: true
hidefromtoc: true
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# 移轉測試{#testing-the-migration}



## 一般程式 {#general-procedure}

根據您的設定，有數種方式可執行移轉測試。

您應該要有測試/開發環境來執行移轉測試。 Adobe Campaign環境受限於授權：請檢查您的授權合約或聯絡您的Adobe代表。

1. 停止所有進行中的開發，並將它們帶往生產環境。
1. 備份開發環境資料庫。
1. 停止開發執行個體上的所有Adobe Campaign程式。
1. 備份生產環境資料庫，並將其還原為開發環境。
1. 在啟動Adobe Campaign服務之前，請執行&#x200B;**freezeInstance.js**&#x200B;燒錄指令碼，讓您清除啟動備份時執行的任何物件資料庫。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >該命令預設會以&#x200B;**乾**&#x200B;模式啟動，並列出該命令執行的所有要求，而不啟動它們。 若要執行燒灼要求，請在命令中使用&#x200B;**run**。

1. 嘗試還原備份，以確定備份是否正確。 確定您可以存取資料庫、表格、資料等。
1. 在開發環境中測試移轉程式。
1. 如果成功移轉開發環境，您可以移轉生產環境。

>[!CAUTION]
>
>由於資料結構已變更，無法在v5平台和v7平台之間匯入和匯出資料套件。


## 移轉工具 {#migration-tools}

有多種選項可讓您測量移轉帶來的影響，並找出潛在問題。 這些選項將會執行：

* 在&#x200B;**config**&#x200B;命令中：

  ```
  nlserver.exe config <option> -instance:<instance-name>
  ```

* 或在升級後：

  ```
  nlserver.exe config -postupgrade <option> -instance:<instance-name>
  ```

>[!NOTE]
>
>* 您必須使用&#x200B;**-instance：`<instanceame>`**&#x200B;選項。 我們不建議使用&#x200B;**-allinstances**&#x200B;選項。
>* Adobe Campaign更新命令（**升級後**）可讓您同步資源，並更新結構描述和資料庫。 這項作業只能執行一次，而且只能在應用程式伺服器上執行。 同步資源之後，**postupgrade**&#x200B;命令可讓您偵測同步是否產生任何錯誤或警告。

### 非標準或遺失物件

* **-showCustomEntities**&#x200B;選項會顯示所有非標準物件的清單：

  ```
  nlserver.exe config -showCustomEntities -instance:<instance-name>
  ```

  已傳送訊息的範例：

  ```
  xtk_migration:opsecurity2 xtk:entity
  ```

* **-showDeletedEntities**&#x200B;選項會顯示資料庫或檔案系統中遺失的所有標準物件清單。 對於每個遺失的物件，都會指定路徑。

  ```
  nlserver.exe config -showDeletedEntities -instance:<instance-name>
  ```

  已傳送訊息的範例：

  ```
  Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
  ```

### 驗證程式 {#verification-process}

在升級後命令中整合為標準，此程式可讓您顯示可能導致移轉失敗的警告和錯誤。 **如果顯示錯誤，表示移轉尚未執行。**&#x200B;如果發生此情況，請更正所有錯誤，然後重新啟動升級後。

您可以使用下列命令自行啟動驗證程式（不進行移轉）：

```
nlserver.exe config -postupgrade -check -instance:<instance-name>
```

>[!NOTE]
>
>您可以使用JST-310040程式碼忽略所有警告和錯誤。

系統會搜尋下列運算式（區分大小寫）：

<table> 
 <thead> 
  <tr> 
   <th> 運算式<br /> </th> 
   <th> 錯誤碼<br /> </th> 
   <th> 記錄型別<br /> </th> 
   <th> 註解<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 傳遞個人化不再支援這類語法。<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 不得使用此資料庫。<br /> </td> 
  </tr> 
  <tr> 
   <td> 登入(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 此連線方法必須不再使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> 新SoapMethodCall(<br />) </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 只有在從<strong>sessionTokenOnly</strong>模式的安全性區域執行的JavaScript程式碼中使用這個函式時，才支援這個函式。<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> 這類錯誤會導致移轉失敗。<br /> </td> 
  </tr> 
  <tr> 
   <td> crmDeploymentType="onpremise"<br /> </td> 
   <td> PU-0007<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> 不再支援此型別的部署。 Office 365和內部部署Microsoft CRM聯結器部署型別現已棄用。 
   </br>如果您在外部帳戶中使用這些已棄用的部署型別之一，應刪除此外部帳戶，然後您應該執行<b>升級後</b>命令。 
   </br>若要變更網頁API部署，請參閱<a href="../../platform/using/crm-ms-dynamics.md#configure-acc-for-microsoft" target="_blank">網頁應用程式</a>。<br /> </td>
  </tr> 
  <tr> 
   <td> CRM v1(mscrmWorkflow/sfdcWorkflow)<br /> </td> 
   <td> PU-0008<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> Microsoft CRM、Salesforce、OracleCRM隨選動作活動已無法使用。 若要設定Adobe Campaign與CRM系統之間的資料同步，您必須使用<a href="../../workflow/using/crm-connector.md" target="_blank">CRM聯結器</a>目標定位活動。<br /> </td>
  </tr> 
 </tbody> 
</table>

也會執行資料庫和綱要一致性檢查。

### 還原選項 {#restoration-option}

此選項可讓您還原已修改的現成物件。 對於每個已還原的物件，變更的備份會儲存在選取的資料夾中：

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instance-name>
```

>[!NOTE]
>
>我們強烈建議使用絕對資料夾路徑並保留資料夾樹狀結構。 例如： backupFolder\nms\srcSchema\billing.xml。

### 繼續移轉 {#resuming-migration}

如果您在移轉失敗後重新啟動升級後，它會從停止的位置繼續。
