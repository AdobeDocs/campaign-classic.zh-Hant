---
product: campaign
title: 測試移轉
description: 測試移轉
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: 228ee9e4-46a0-4d82-b8ba-b019bc0e7cac
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '667'
ht-degree: 1%

---

# 測試移轉{#testing-the-migration}

## 一般程式{#general-procedure}

根據您的設定，有數種方式可執行移轉測試。

您應有測試/開發環境來執行移轉測試。 開發環境需依授權規範執行：檢查您的授權合約，或聯絡Adobe Campaign的銷售服務。

1. 停止所有正在進行的開發，並將其轉移到生產環境中。
1. 備份開發環境資料庫。
1. 停止開發執行個體上的所有Adobe Campaign程式。
1. 備份生產環境資料庫，並將其還原為開發環境。
1. 在啟動Adobe Campaign服務之前，請運行&#x200B;**freezeInstance.js**&#x200B;燒錄指令碼，該指令碼允許您清除啟動備份時運行的任何對象的資料庫。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >預設情況下，該命令將在&#x200B;**dry**&#x200B;模式中啟動，並列出該命令執行的所有請求，而不啟動這些請求。 要執行燒灼請求，請在命令中使用&#x200B;**run**。

1. 嘗試還原備份，以確保備份正確。 請務必訪問資料庫、表、資料等。
1. 在開發環境中測試移轉程式。

   [移轉至Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)的必要條件一節中會詳細說明完整程式。

1. 如果開發環境的移轉成功，您可以移轉生產環境。

>[!IMPORTANT]
>
>由於資料結構有所變更，v5平台和v7平台之間無法匯入和匯出資料套件。

>[!NOTE]
>
>Adobe Campaign update命令(**postupgrade**)可讓您同步資源，以及更新結構和資料庫。 此操作只能在應用程式伺服器上執行一次。 同步資源後， **postupgrade**&#x200B;命令允許您檢測同步是否生成任何錯誤或警告。

## 遷移工具{#migration-tools}

各種選項可讓您評估移轉的影響並找出潛在問題。 這些選項將執行：

* 在&#x200B;**config**&#x200B;命令中：

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 或在升級後：

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>您必須使用&#x200B;**-instance:`<instanceame>`**&#x200B;選項。 我們不建議使用&#x200B;**-allinstances**&#x200B;選項。

### -showCustomEntities和 — showDeletedEntities選項{#showcustomentities-and--showdeletedentities-options}

* **-showCustomEntities**&#x200B;選項顯示所有非標準對象的清單：

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   已傳送訊息的範例：

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* **-showDeletedEntities**&#x200B;選項顯示資料庫或檔案系統中缺少的所有標準對象的清單。 對於每個缺少的對象，指定路徑。

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   已傳送訊息的範例：

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### 驗證進程{#verification-process}

整合為後置升級命令中的標準，此程式可讓您顯示可能導致遷移失敗的警告和錯誤。 **如果顯示錯誤，則未執行移轉。** 如果發生此情況，請更正所有錯誤，然後重新啟動升級後。

您可以使用以下命令自行啟動驗證過程（無需遷移）:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>請忽略具有JST-310040代碼的所有警告和錯誤。

會搜尋下列運算式（區分大小寫）:

<table> 
 <thead> 
  <tr> 
   <th> 表達式<br /> </th> 
   <th> 錯誤代碼<br /> </th> 
   <th> 日誌類型<br /> </th> 
   <th> 注釋<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> .@<br /> </td> 
   <td> PU-0001<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 傳遞個人化不再支援此類語法。 請參閱<a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>。 否則，檢查值類型是否正確。<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 不得使用此庫。<br /> </td> 
  </tr> 
  <tr> 
   <td> 登錄(<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 此連接方法不得再使用。 請參閱<a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">已識別的Web應用程式</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 只有在從<strong>sessionTokenOnly</strong>模式的安全區域執行的JavaScript代碼中使用此函式時，才支援該函式。<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> 這種錯誤會導致遷移失敗。 請參閱<a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> 這種錯誤會導致遷移失敗。 請參閱<a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。 如果您收到概述類型的Web應用程式錯誤日誌（從v6.02遷移），請參閱<a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Web應用程式</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

還進行了資料庫和方案一致性檢查。

### 還原選項{#restoration-option}

此選項可讓您在對象已修改時還原現成可用的對象。 對於每個已還原的對象，更改的備份會儲存在所選資料夾中：

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>強烈建議使用絕對資料夾路徑並保留資料夾樹結構。 例如：backupFolder\nms\srcSchema\billing.xml。

### 繼續遷移{#resuming-migration}

如果您在移轉失敗後重新啟動升級後，會從停止的相同位置繼續。
