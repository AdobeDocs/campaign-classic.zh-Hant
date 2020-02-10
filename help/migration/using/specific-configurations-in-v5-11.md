---
title: v5.11中的特定組態
seo-title: v5.11中的特定組態
description: v5.11中的特定組態
seo-description: null
page-status-flag: never-activated
uuid: d6920beb-a766-4aec-8a8e-d32e47b545a4
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: fc280640-528d-44de-87d8-52f443772abd
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 703fa6e5d5e6f1c8c512bd65ebadad724f02ded3

---


# v5.11中的特定組態{#specific-configurations-in-v5-11}

本節詳細說明從v5.11移轉時需要的其他設定。您還應配置「常規配置」部分中詳 [細的設定](../../migration/using/general-configurations.md) 。

## 網頁應用程式 {#web-applications}

在移轉期間會自動顯示下列警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web應用程式的某些元件（例如各種公式欄位）具有@id屬性。 這些程式碼會用於網頁應用程式的XML程式碼中，而不再以相同的方式產生。 它們在介面中不可見，您通常不能使用它們。 不過，在某些情況下，@id屬性可能被用來個人化Web應用程式的轉譯，例如透過樣式表或使用JavaScript程式碼。

在遷移期間，必 **須檢查** 警告中指定的日誌檔案路徑：

* **檔案不為空**:它包含警告，這些警告涉及遷移前記錄的不一致，且仍然存在。 這可以是Web應用程式中參照不存在的ID的JavaScript程式碼。 必須檢查並更正每個錯誤。
* **檔案為空**:這表示Adobe Campaign未偵測到任何問題。

無論檔案是否空白，您都必須檢查這些ID是否未用於其他位置的設定（若是如此，請調整設定）。

## 工作流程 {#workflows}

由於Adobe Campaign安裝目錄的名稱已變更，因此在移轉後，某些工作流程可能無法運作。 如果工作流在其活動中引用了nl5目錄，則會引發錯誤。 以build取代此參 **考**。 您可以運行SQL查詢來標識這些工作流（PostgreSQL示例）:

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## 方便使用 {#user-friendliness}

Adobe Campaign v5.11首頁已不再提供。

雖然不建議使用，但若您想要保留Adobe Campaign 5.11版中的特定介面，則有某些解決方案。如需詳細資訊，請聯絡我們。

## MySQL {#mysql}

>[!CAUTION]
>
>使用此引擎從6.02或5.11版遷移時，v7中僅支援MySQL作為主資料庫引擎。

預設情況下，MySQL不管理時區。 要啟用時區管理，請運行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>如需詳細資訊，請參閱http://dev.mysql.com/doc/refman/5.5/en/time-zone-support.html [頁面](http://dev.mysql.com/doc/refman/5.5/en/time-zone-support.html) 。

如果對資料庫結構進行了修改，在配置期間（例如建立特定索引、建立SQL視圖等），遷移時應採取某些預防措施。 事實上，某些修改可能是由與遷移過程不相容而產生。 例如，建立包含 **Timestamp欄位的SQL視圖與** usetimestamptz選項不兼 **容** 。 因此，我們建議您遵循下列建議：

1. 開始遷移之前，請備份資料庫。
1. 刪除SQL更改。
1. 依照移轉至Adobe Campaign 7的先決條件一節中 [詳述的程式執行配置](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。
   >[!NOTE]
   >
   >您必須依照移轉至Adobe Campaign 7的必要條 [件一節中顯示的移轉步驟](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md) 。
1. 重新整合SQL更改。

在此範例中，已建 **立NmcTrackingLogMessages** 檢視，且此檢視具有名為tslog的 **Timestamp** 欄 **位**。 在這種情況下，遷移過程將失敗，並出現以下錯誤消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

為確保配置工作正常，您必須在遷移前刪除視圖，並在遷移後重新建立視圖，同時將其調整為TIMESTAMP WITH TIMEZONE模式。

## 追蹤 {#tracking}

追蹤公式已修改。 移轉時，舊公式(v5)會由新公式(v7)取代。 如果您在Adobe Campaign v5中使用個人化公式，則此設定必須在Adobe Campaign v7(**NmsTracking_ClickFormula** 和 **NmsTracking_OpenFormul** 選項)中調整。

網頁追蹤管理也已修改。 移轉至v7後，您必須啟動部署精靈以完成Web追蹤設定。

![](assets/migration_web_tracking.png)

提供三種模式：

* **作業網路追蹤**:如果尚 **[!UICONTROL Leads]** 未安裝軟體包，則預設選擇此選項。 這個選項在效能方面最理想，可讓您限制追蹤記錄檔的大小。
* **永久網頁追蹤**
* **匿名網頁追蹤**:如果安 **[!UICONTROL Leads]** 裝了軟體包，則預設選擇此選項。 這是最耗資的選項。 如上所述， **sSourceId** 欄必須建立索引(在追蹤表和 **** CrmIncomingLead表中)。

>[!NOTE]
>
>有關這三種模式的詳細資訊，請參 [閱本節](../../configuration/using/about-web-tracking.md)。

## Adobe Campaign v7樹狀結構 {#campaign-vseven-tree-structure}

在移轉期間，會根據v7標準自動重新整理樹狀結構。 新增資料夾、刪除過時的資料夾，其內容會放在「移動」資料夾中。 在移轉後，必須勾選此資料夾中的所有項目，顧問必須決定保留或刪除每個項目。 待保存的物品則必須移到正確的位置。

已新增選項，可停用導覽樹的自動移轉。 此操作現在為手動操作。 不會刪除過時的資料夾，也不會添加新資料夾。 只有在現成可用的v5導覽樹狀結構已經過太多變更時，才應使用此選項。 在移轉前，在節點中將選項添加到控制 **[!UICONTROL Administration > Options]** 台：

* 內部名稱：NlMigration_KeepFolderStructure
* 資料類型：整數
* 值（文本）:1

如果您使用此選項，在移轉後，您必須刪除過時的資料夾，新增資料夾並執行所有必要的檢查。

**新資料夾清單**:

移轉後需要新增下列資料夾：

| 內部名稱 | 標籤 | 條件 |
|---|---|---|
| nmsAutoObjects | 自動建立的物件 | - |
| nmsCampaignAdmin | 促銷活動管理 | - |
| nmsCampaignMgt | 促銷活動管理 | - |
| nmsCampaignRes | 促銷活動管理 | - |
| nmsModels | 範本 | - |
| nmsOnlineRes | 線上 | - |
| nmsProduction | 製作 | - |
| nmsProfilProcess | 流程 | - |
| xtkDashboard | 控制面板 | - |
| xtkPlatformAdmin | 平台 | - |
| nmsLocalOrgUnit | 組織單位 | - |
| nmsMRM | MRM | 已安裝MRM |
| nmsOperations | 促銷活動 | 已安裝促銷活動 |

**過時資料夾清單**:

遷移後要刪除的過時資料夾如下：

>[!NOTE]
>
>必須檢查過時資料夾的整個內容，並且顧問會決定是否保留或刪除每個項目。 必須將要保存的項目移至適當位置。

| 內部名稱 | 標籤 | 條件 |
|---|---|---|
| nmsAdministration | 管理 | - |
| nmsDeliveryMgt | 促銷活動執行 | - |
| ncmContent | 內容管理 | 已安裝Content Manager |
| ncmForm | 輸入表單 | 已安裝Content Manager |
| ncmImage | 影像 | 已安裝Content Manager |
| ncmJavascript | JavaScript程式碼 | 已安裝Content Manager |
| ncmJst | JavaScript範本 | 已安裝Content Manager |
| ncmParameters | 配置 | 已安裝Content Manager |
| ncmSrcSchema | 資料結構 | 已安裝Content Manager |
| ncmStylesheet | XSL樣式檔 | 已安裝Content Manager |
| nmsAdminPlan | 管理 | 已安裝促銷活動 |
| nmsResourcePlan | 資源 | 已安裝促銷活動 |
| nmsResourcesModels | 範本 | 已安裝促銷活動 |
| nmsRootPlan | 促銷活動管理 | 已安裝促銷活動 |
| nmsOperator | 行銷營運商 | 已安裝MRM |

