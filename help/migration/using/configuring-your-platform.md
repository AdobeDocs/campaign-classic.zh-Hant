---
product: campaign
title: 調整配置
description: 了解如何在移轉至Campaign v7之前和之後調整您的配置
audience: migration
content-type: reference
topic-tags: migration-procedure
exl-id: ad71dead-c0ca-42d5-baa8-0f340979231a
source-git-commit: 327f220d6700242308ef3738a38cc95b970e3f46
workflow-type: tm+mt
source-wordcount: '1980'
ht-degree: 3%

---

# 調整配置{#configuring-your-platform}

![](../../assets/v7-only.svg)

Adobe Campaign v7中的某些重大變更需要特定設定。 移轉之前或之後，可能需要進行這些設定。

從Campaign v5或v6移轉時，要在Adobe Campaign v7中執行的詳細設定可在 [本頁](general-configurations.md).


在移轉期間， **NmsRecipient** 表格是從結構定義中重建。 在Adobe Campaign之外對此表的SQL結構所做的任何更改都將丟失。

要檢查的元素範例：

* 如果您已將欄（或索引）新增至 **NmsRecipient** 表格，但您尚未在架構中詳細說明，則系統不會儲存此表格。
* 此 **表空間** 屬性預設會回傳其值，亦即部署精靈中定義的值。
* 如果您已將參考檢視新增至 **NmsRecipient** 表格，您必須先將其刪除，才能移轉。


## 移轉前 {#before-the-migration}

移轉至Adobe Campaign v7時，必須設定下列元素。 在開始 **postugrade**.

* 時區

   從v5.11平台移轉期間，您必須指定在升級後期間要使用的時區。

   如果您想使用「多時區」模式，請參閱 [本節](../../migration/using/general-configurations.md#time-zones).

   如果將Oracle用作資料庫，請檢查應用程式伺服器和資料庫伺服器之間的Oracle時區檔案是否已正確同步。 [了解更多](../../migration/using/general-configurations.md#oracle)

* 安全區域

   基於安全考量，預設不再存取Adobe Campaign平台：您必須設定安全區域，這需要在移轉前收集使用者IP位址。 [了解更多](../../migration/using/general-configurations.md#security)

* 語法

   由於使用新的解釋程式，v7版本中可能不再接受某些Javascript程式碼。 [了解更多](../../migration/using/general-configurations.md#javascript)。

   同樣地，Adobe Campaign v7也導入了新語法，以取代SQLData型語法。 如果您使用此語法使用程式碼元素，則必須加以調整。 [了解更多](../../migration/using/general-configurations.md#sqldata)

* 密碼

   您必須設定 **管理** 和 **內部** 密碼。 [了解更多](../../migration/using/before-starting-migration.md#user-passwords)

* 樹結構

   如果從v5.11平台遷移，則必鬚根據Adobe Campaign v6規範重新組織樹結構資料夾。 [了解更多](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)。

* 互動

   如果您要從Campaign 6.02版移轉，並使用  **互動** 模組中，您必須刪除v7中已不存在的所有6.02架構參考。 [了解更多](../../migration/using/general-configurations.md#interaction)

## 移轉後 {#after-the-migration}

執行後 **postugrade**，檢查並設定下列元素：

* 鏡像頁面

   鏡像頁面個人化區塊已隨v6.x變更。這個新版本可改善存取這些頁面時的安全性。

   如果您在訊息中使用v5個人化區塊，鏡像頁面顯示將會失敗。 Adobe強烈建議在訊息中插入鏡像頁面時，使用新的個人化區塊。

   不過，作為暫時的因應措施（且鏡像頁面仍為即時頁面），您可以回到舊的個人化區塊，透過變更選項來避免此問題 **[!UICONTROL XtkAcceptOldPasswords]** 並將其設定為 **[!UICONTROL 1]**. 這不會影響新v6.x個人化區塊的使用。

* 語法

   如果您遇到任何與語法相關的錯誤，在升級後期間，您必須暫時啟用 **allowSQLInjents** 選項 **serverConf.xml** 檔案，因為這能讓您有時間重寫程式碼。 調整程式碼後，請務必重新啟用安全性。 [了解更多](../../migration/using/general-configurations.md#sqldata)

* 衝突

   移轉是透過升級後執行，而報表、表單或網頁應用程式中可能會出現衝突。 這些衝突可從主控台解決。 [了解更多](../../migration/using/general-configurations.md#conflicts)

* Tomcat

   如果您自訂了安裝資料夾，請務必確認移轉後資料夾已正確更新。 [了解更多](../../migration/using/general-configurations.md#tomcat)

* 報告

   現成可用的所有報表目前都使用v6.x轉譯引擎。 若您已將JavaScript程式碼新增至報表中，則某些元素可能會受到影響。 [了解更多](../../migration/using/general-configurations.md#reports)

* Web應用程式

   升級後，如果您在連接到已識別的Web應用程式時遇到任何問題，則必須激活 **allowUserPassword** 和 **sessionTokenOnly** 選項 **serverConf.xml** 檔案。 為避免出現任何安全問題，在問題解決後，必須重新激活這兩個選項。 [了解更多](../../migration/using/general-configurations.md#identified-web-applications)

   您必鬚根據Web應用程式的類型及其配置執行其他操作，以確保它們正常工作。 [了解更多](../../migration/using/general-configurations.md#web-applications)

   如果從v5.11平台移轉，則必須執行其他設定。 [了解更多](../../migration/using/general-configurations.md#specific-configurations-in-v5-11.md)

* 安全區域

   啟動伺服器之前，必須配置安全區域。 [深入了解](../../installation/using/security-zones.md) 和 [見這裡](../../migration/using/general-configurations.md#security)

* 工作流程

   如果從v5.11平台移轉，您必須檢查工作流程資料夾。 [了解更多](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 追蹤

   如果從v5.11平台移轉，您必須設定追蹤模式。 [了解更多](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11)

* 互動

   如果您使用 **互動**，您必須在移轉後調整任何參數。 [了解更多](../../migration/using/general-configurations.md#interaction)

* 控制面板

   如果出現用戶端錯誤，您必須使用新的Adobe Campaign v7程式碼更新控制面板，或手動將下列檔案從v6.02執行個體複製到v7執行個體：

   ```
   v6.02 files and spaces:
   /usr/local/neolane/nl6/datakit/xtk/eng/css/dropDownMenu.css
   /usr/local/neolane/nl6/datakit/xtk/eng/js/client/dropDownMenu.js
   v6.1 files and spaces:
   /usr/local/neolane/nl6/deprecated/xtk/css/dropDownMenu.css
   /usr/local/neolane/nl6/deprecated/xtk/js/client/dropDownMenu.js  
   ```


## 從v5.11到v7的特定配置{#specific-configurations-in-v5-11}

![](../../assets/v7-only.svg)

本節詳細說明從v5.11遷移時需要的其他配置。您也應配置 [一般配置](../../migration/using/general-configurations.md) 區段。

### 網站應用程式 {#web-applications-v5}

移轉期間會自動顯示下列警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side JavaScript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web應用程式的某些元件（例如各種公式欄位）具有@id屬性。 這些用於Web應用程式的XML代碼中，不再以相同方式生成。 它們不會顯示在介面中，而您通常不得使用它們。 但是，在某些情況下，可能@id用屬性來個性化Web應用程式的呈現，例如通過樣式表或使用JavaScript代碼。

在移轉期間，您 **必須** 檢查警告中指定的日誌檔案路徑：

* **檔案不為空**:其中包含的警告涉及遷移前記錄的不一致，且仍然存在。 這可以是參考不存在ID之Web應用程式中的JavaScript程式碼。 必須檢查並更正每個錯誤。
* **檔案為空**:這表示Adobe Campaign未偵測到任何問題。

無論檔案是否空白，您都必須檢查這些ID是否未用於其他位置的設定（若是如此，請調整設定）。

### 工作流程 {#workflows}

由於Adobe Campaign安裝目錄的名稱已變更，因此移轉後某些工作流程可能無法運作。 如果工作流程在其其中一個活動中參考nl5目錄，則會引發錯誤。 用替換此引用 **建置**. 您可以運行SQL查詢來標識這些工作流（PostgreSQL示例）:

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

### MySQL {#mysql}

>[!CAUTION]
>
>使用此引擎從6.02版或5.11版遷移時，v7僅支援MySQL作為主資料庫引擎。

MySQL預設不管理時區。 要啟用時區管理，請運行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>如需詳細資訊，請參閱 [https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html) 頁面。

如果對資料庫結構進行了修改，在配置期間（例如建立特定索引、建立SQL視圖等），則遷移時應採取某些預防措施。 事實上，某些修改可能會因與移轉程式不相容而產生。 例如，建立包含 **時間戳記** 欄位與不相容 **usetimestamtz** 選項。 因此，我們建議您遵循以下建議：

1. 開始遷移之前，請備份資料庫。
1. 刪除SQL更改。
1. 執行升級後
   >[!NOTE]
   >
   >您必須依照 [本節](../../migration/using/migrating-in-windows-for-adobe-campaign-7.md).
1. 重新整合SQL更改。

在此範例中， **NmcTrackingLogMessages** 已建立視圖，並且 **時間戳記** 欄位已命名 **tslog**. 在這種情況下，遷移過程會失敗，並出現以下錯誤消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

為確保升級後的工作正常，您必須在遷移前刪除視圖，並在遷移後重新建立視圖，同時將其調整為TIMESTAMP WITH TIMEZONE模式。

### 追蹤 {#tracking}

追蹤公式已修改。 移轉時，舊公式(v5)會取代為新公式(v7)。 如果您在Adobe Campaign v5中使用個人化公式，此設定必須在Adobe Campaign v7中調整(**NmsTracking_ClickFormula** 和 **NmsTracking_OpenFormula** 選項)。

網站追蹤管理也已修改。 執行v7移轉後，您必須啟動部署精靈以完成Web追蹤的設定。

![](assets/migration_web_tracking.png)

提供三種模式：

* **工作階段網路追蹤**:若 **[!UICONTROL Leads]** 尚未安裝軟體包，預設情況下會選擇此選項。 此選項是效能上最理想的選項，可讓您限制追蹤記錄檔的大小。
* **永久性網頁追蹤**
* **匿名網路追蹤**:若 **[!UICONTROL Leads]** 已安裝套件，預設會選取此選項。 這是最耗用資源的選項。 如上所述， **sSourceId** 欄必須已編列索引(在追蹤表格和 **CrmIncomingLead** 表格)。

>[!NOTE]
>
>有關這三種模式的詳細資訊，請參閱 [本節](../../configuration/using/about-web-tracking.md).

### Adobe Campaign v7樹結構 {#campaign-vseven-tree-structure}

在移轉期間，會根據v7標準自動重新組織樹狀結構。 新資料夾將被添加，過時資料夾將被刪除，其內容將放在「移動」資料夾中。 移轉後，必須檢查此資料夾中的所有項目，顧問必須決定保留或刪除每個項目。 然後，要保留的物品必須移至正確位置。

已新增選項，以停用導覽樹的自動移轉。 此操作現在為手動操作。 不會刪除過時的資料夾，也不會新增新資料夾。 只有在現成的v5導覽樹狀結構發生太多變更時，才應使用此選項。 在移轉前，將選項新增至主控台，位於 **[!UICONTROL Administration > Options]** 節點：

* 內部名稱：NlMigration_KeepFolderStructure
* 資料類型：整數
* 值（文本）:1

如果使用此選項，則遷移後必須刪除過時的資料夾，添加新資料夾並運行所有必要的檢查。

**新資料夾清單**:

移轉後需要新增下列資料夾：

| 內部名稱 | 標籤 | 條件 |
|---|---|---|
| nmsAutoObjects | 自動建立的對象 | - |
| nmsCampaignAdmin | 行銷活動管理 | - |
| nmsCampaignMgt | 行銷活動管理 | - |
| nmsCampaignRes | 行銷活動管理 | - |
| nmsModels | 範本 | - |
| nmsOnlineRes | 線上 | - |
| nmsProduction | 生產 | - |
| nmsProfilProcess | 程式 | - |
| xtkDashboard | 控制面板 | - |
| xtkPlatformAdmin | 平台 | - |
| nmsLocalOrgUnit | 組織單位 | - |
| nmsMRM | MRM | 已安裝MRM |
| nmsOperations | 行銷活動 | 已安裝Campaign |

**過時資料夾清單**:

遷移後要刪除的過時資料夾如下：

>[!NOTE]
>
>必須檢查過時資料夾的整個內容，並且顧問會針對每個項目決定是否保留或刪除它。 要保留的物品必須移至適當位置。

| 內部名稱 | 標籤 | 條件 |
|---|---|---|
| nmsAdministration | 管理 | - |
| nmsDeliveryMgt | 行銷活動執行 | - |
| ncmContent | 內容管理 | 已安裝內容管理器 |
| ncmForm | 輸入表單 | 已安裝內容管理器 |
| ncmImage | 影像 | 已安裝內容管理器 |
| ncmJavascript | JavaScript程式碼 | 已安裝內容管理器 |
| ncmJst | JavaScript範本 | 已安裝內容管理器 |
| ncmParameters | 設定 | 已安裝內容管理器 |
| ncmSrcSchema | 資料方案 | 已安裝內容管理器 |
| ncmStylesheet | XSL樣式檔案 | 已安裝內容管理器 |
| nmsAdminPlan | 管理 | 已安裝Campaign |
| nmsResourcePlan | 資源 | 已安裝Campaign |
| nmsResourcesModels | 範本 | 已安裝Campaign |
| nmsRootPlan | 行銷活動管理 | 已安裝Campaign |
| nmsOperator | 行銷運算子 | 已安裝MRM |


## 從v6.02到v7的特定配置{#specific-configurations-in-v6-02}

![](../../assets/v7-only.svg)

下節詳細說明從v6.02遷移時需要的其他配置。您也應配置中詳述的設定 [本頁](../../migration/using/general-configurations.md).

### 網站應用程式 {#web-applications-v6}

如果您要從v6.02移轉，可能會出現關於概述類型Web應用程式的錯誤記錄。 錯誤訊息範例：

```
[PU-0006] Entity of type : 'xtk:entityBackupNew' and Id 'nms:webApp|taskOverview', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'xtk:formDictionary' and Id 'nms:webApp|lastTasks', expression '[SQLDATA[' was found : '...)) or (@id IN ([SQLDATA[select 
[PU-0006] Entity of type : 'nms:webApp' and Id 'taskOverview', expression '[SQLDATA[' was found : '...@owner-id] IN ([SQLDATA[select iGroupid...'. (iRc=-1)
```

這些Web應用程式使用SQLData，並且由於安全性增強而與v7不相容。 這些錯誤將導致遷移失敗。

如果您未使用這些Web應用程式，請執行下列清除指令碼並重新執行升級後的程式：

```
Nlserver javascript -instance:[instance_name] -file [installation_path]/datakit/xtk/fra/js/removeOldWebApp.js
```

如果您已修改這些Web應用程式，並且想要在v7中繼續使用這些應用程式，則必須激活 **allowSQLInjents** 選項，然後重新啟動升級後版本。 請參閱 [SQLData](../../migration/using/general-configurations.md#sqldata) 一節以取得詳細資訊。

### 訊息中心 {#message-center}

在Message Center控制實例遷移後，必須重新發佈交易式消息模板，以便它們正常工作。

在v7中，執行例項上的交易式訊息範本的名稱已變更。 它們目前會加上前置詞運算子名稱，此名稱對應至建立它們的控制例項，例如 **control1_template1_rt** (其中 **control1** 是運算子的名稱)。 如果您有大量範本，建議您在控制執行個體上刪除舊範本。