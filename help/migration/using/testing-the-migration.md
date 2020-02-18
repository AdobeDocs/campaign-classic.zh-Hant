---
title: 測試遷移
seo-title: 測試遷移
description: 測試遷移
seo-description: null
page-status-flag: never-activated
uuid: 3ee6a10b-dea2-41c6-9aef-ee3ac922b459
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: migration-procedure
discoiquuid: 30e3082f-a367-4c3b-bff2-208ccf97acd4
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9f7cf3d530f141a661df5fcc8cbcf0bb4c8d3e89

---


# 測試遷移{#testing-the-migration}

## 一般程式 {#general-procedure}

根據您的設定，執行移轉測試有幾種方式。

您應該有測試／開發環境來執行遷移測試。 開發環境需遵守授權：檢查您的授權合約或聯絡Adobe Campaign的銷售服務。

1. 停止所有正在進行的開發，並將其轉移到生產環境中。
1. 備份開發環境資料庫。
1. 停止開發例項上的所有Adobe Campaign程式。
1. 對生產環境資料庫進行備份，並將其作為開發環境進行恢復。
1. 在啟動Adobe Campaign服務之前，請執行 **** freezeInstance.js燒灼指令碼，讓您清除啟動備份時執行之任何物件的資料庫。

   ```
   nlserver javascript nms:freezeInstance.js -instance:<instance> -arg:<run|dry>
   ```

   >[!NOTE]
   >
   >預設會在乾模式下啟 **動命令** ，並列出該命令執行的所有請求，而不啟動這些請求。 要執行燒灼請求，請 **在命令中** 「運行」。

1. 通過嘗試恢復備份，確保備份正確。 請確定您可以存取您的資料庫、表格、資料等。
1. 在開發環境中測試遷移過程。

   移轉至Adobe Campaign 7的必要條 [件一節中會詳述完整程式](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。

1. 如果開發環境的遷移成功，則可以遷移生產環境。

>[!IMPORTANT]
>
>由於對資料結構所做的變更，v5平台與v7平台之間無法匯入和匯出資料封裝。

>[!NOTE]
>
>Adobe Campaign update命令(postupgrade ****)可讓您同步資源，並更新結構描述和資料庫。 此操作只能在應用程式伺服器上執行一次。 同步資源後， **postupgrade** 命令可讓您檢測同步是否生成任何錯誤或警告。

## 移轉工具 {#migration-tools}

各種選項可讓您測量移轉的影響並找出潛在問題。 將執行下列選項：

* 在config命 **令中** :

   ```
   nlserver.exe config <option> -instance:<instanceName>
   ```

* 或是在手術室：

   ```
   nlserver.exe config -postupgrade <option> -instance:<instanceName>
   ```

>[!NOTE]
>
>**您必須使用`<instanceame>`**-instance:的雙曲餘切值。 我們不建議使用**-allinstances選項&#x200B;**。

### -showCustomEntities和-showDeletedEntities選項 {#showcustomentities-and--showdeletedentities-options}

* - **showCustomEntities** 選項顯示所有非標準對象的清單：

   ```
   nlserver.exe config -showCustomEntities -instance:<instanceName>
   ```

   已傳送訊息的範例：

   ```
   xtk_migration:opsecurity2 xtk:entity
   ```

* - **showDeletedEntities** 選項顯示資料庫或檔案系統中缺少的所有標準對象的清單。 對於每個缺少的對象，都指定路徑。

   ```
   nlserver.exe config -showDeletedEntities -instance:<instanceName>
   ```

   已傳送訊息的範例：

   ```
   Out of the box object 'nms:deliveryCustomizationMdl' belonging to the 'xtk:srcSchema' schema has not been found in the file system.
   ```

### 驗證程式 {#verification-process}

此程式與postupgrade命令中的標準整合，可讓您顯示可能導致遷移失敗的警告和錯誤。 **如果顯示錯誤，則未執行遷移。** 如果發生此情況，請更正所有錯誤，然後重新啟動postupgrade。

您可以使用以下命令自行啟動驗證進程（不進行遷移）:

```
nlserver.exe config -postupgrade -check -instance:<instanceName>
```

>[!NOTE]
>
>請忽略所有包含JST-310040代碼的警告和錯誤。

會搜尋下列運算式（區分大小寫）:

<table> 
 <thead> 
  <tr> 
   <th> 運算式<br /> </th> 
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
   <td> 傳送個人化不再支援此類語法。 請參閱 <a href="../../migration/using/general-configurations.md#javascript" target="_blank">JavaScript</a>。 否則，檢查值類型是否正確。<br /> </td> 
  </tr> 
  <tr> 
   <td> common.js<br /> </td> 
   <td> PU-0002<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 此程式庫不得使用。<br /> </td> 
  </tr> 
  <tr> 
   <td> logon（登錄）<br /> </td> 
   <td> PU-0003<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 此連接方法必須不再使用。 請參閱「已識 <a href="../../migration/using/general-configurations.md#identified-web-applications" target="_blank">別的Web應用程式」</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> new SoapMethodCall(<br /> </td> 
   <td> PU-0004<br /> </td> 
   <td> 警告<br /> </td> 
   <td> 只有當此函式用於從sessionTokenOnly模式的安全區域執行的JavaScript程式碼時，才 <strong>支援此函式</strong> 。<br /> </td> 
  </tr> 
  <tr> 
   <td> sql=<br /> </td> 
   <td> PU-0005<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> 這種錯誤會導致遷移失敗。 請參閱 <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。<br /> </td> 
  </tr> 
  <tr> 
   <td> SQLDATA<br /> </td> 
   <td> PU-0006<br /> </td> 
   <td> 錯誤<br /> </td> 
   <td> 這種錯誤會導致遷移失敗。 請參閱 <a href="../../migration/using/general-configurations.md#sqldata" target="_blank">SQLData</a>。 如果您取得概述類型的Web應用程式錯誤記錄（從v6.02移轉），請參閱 <a href="../../migration/using/specific-configurations-in-v6-02.md#web-applications" target="_blank">Web應用程式</a>。<br /> </td> 
  </tr> 
 </tbody> 
</table>

還進行了資料庫和模式一致性檢查。

### 還原選項 {#restoration-option}

此選項可讓您在物件已修改時，還原現成可用的物件。 對於每個已恢復的對象，更改的備份都儲存在選定資料夾中：

```
nlserver.exe config -postupgrade -restoreFactory:<backupfolder> -instance:<instanceName>
```

>[!NOTE]
>
>強烈建議使用絕對資料夾路徑並保留資料夾樹結構。 例如：backupFolder\nms\srcSchema\billing.xml。

### 繼續移轉 {#resuming-migration}

如果在遷移失敗後重新啟動postupgrade，它會從停止的同一位置恢復。
