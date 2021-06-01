---
product: campaign
title: v5.11 中的特定設定
description: v5.11 中的特定設定
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 978e1249-f79b-4f5f-9a94-3bb2510785de
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 3%

---

# v5.11 中的特定設定{#specific-configurations-in-v5-11}

本節詳細說明從v5.11遷移時需要的其他配置。您也應配置[常規配置](../../migration/using/general-configurations.md)部分中詳述的設定。

## 網站應用程式{#web-applications}

移轉期間會自動顯示下列警告：

```
The webApp ids have been modified during the migration process. Please make sure to check your scripts/css for broken compatibility (any client side javascript or css dealing directly with another element through its id is impacted). See file 'c:\svn\602\nl\build\ncs\var\upgrade/postupgrade/webAppsMigration_*************.txt' for details about the references that were automatically updated, if any.
```

Web應用程式的某些元件（例如各種公式欄位）具有@id屬性。 這些用於Web應用程式的XML代碼中，不再以相同方式生成。 它們不會顯示在介面中，而您通常不得使用它們。 但是，在某些情況下，可能@id用屬性來個性化Web應用程式的呈現，例如通過樣式表或使用JavaScript代碼。

在遷移期間，您必須&#x200B;**檢查警告中指定的日誌檔案路徑：**

* **檔案不為空**:其中包含的警告涉及遷移前記錄的不一致，且仍然存在。這可以是參考不存在ID之Web應用程式中的JavaScript程式碼。 必須檢查並更正每個錯誤。
* **檔案為空**:這表示Adobe Campaign未偵測到任何問題。

無論檔案是否空白，您都必須檢查這些ID是否未用於其他位置的設定（若是如此，請調整設定）。

## 工作流程 {#workflows}

由於Adobe Campaign安裝目錄的名稱已變更，因此移轉後某些工作流程可能無法運作。 如果工作流程在其其中一個活動中參考nl5目錄，則會引發錯誤。 將此參考替換為&#x200B;**build**。 您可以運行SQL查詢來標識這些工作流（PostgreSQL示例）:

```
SELECT   iWorkflowId, sInternalName, sLabel 
FROM XtkWorkflow 
WHERE mData LIKE '%nl5%';
```

## 用戶友好性{#user-friendliness}

不再提供Adobe Campaign v5.11首頁。

雖然不建議使用，但如果您希望保留Adobe Campaign v5.11中的特定介面，則有某些解決方案。有關詳細資訊，請與我們聯繫。

## MySQL {#mysql}

>[!IMPORTANT]
>
>使用此引擎從6.02版或5.11版遷移時，v7僅支援MySQL作為主資料庫引擎。

MySQL預設不管理時區。 要啟用時區管理，請運行以下命令：

```
mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
```

>[!NOTE]
>
>如需詳細資訊，請參閱[https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html](https://dev.mysql.com/doc/refman/8.0/en/time-zone-support.html)頁面。

如果對資料庫結構進行了修改，在配置期間（例如建立特定索引、建立SQL視圖等），則遷移時應採取某些預防措施。 事實上，某些修改可能會因與移轉程式不相容而產生。 例如，建立包含&#x200B;**Timestamp**&#x200B;欄位的SQL視圖與&#x200B;**usetimestamptz**&#x200B;選項不相容。 因此，我們建議您遵循以下建議：

1. 開始遷移之前，請備份資料庫。
1. 刪除SQL更改。
1. 根據[移轉至Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)的必要條件一節中詳述的程式執行升級後。
   >[!NOTE]
   >
   >請務必遵循[移轉至Adobe Campaign 7](../../migration/using/prerequisites-for-migration-to-adobe-campaign-7.md)的必要條件一節中提供的移轉步驟。
1. 重新整合SQL更改。

在此範例中，已建立&#x200B;**NmcTrackingLogMessages**&#x200B;檢視，且此檢視具有&#x200B;**Timestamp**&#x200B;欄位，名為&#x200B;**tslog**。 在這種情況下，遷移過程會失敗，並出現以下錯誤消息：

```
2011-10-04 11:57:51.804Z B67B28C0 1 info log Updating table 'NmcTrackingLogMessages'
2011-10-04 11:57:51.804Z B67B28C0 1 error log PostgreSQL error: ERROR: cannot alter type of a column used by a view or rule\nDETAIL: rule _RETURN on view nmctrackinglogmessagesview depends on column "tslog"\n (iRc=-2006)
2011-10-04 11:57:51.804Z B67B28C0 1 error log SQL order 'ALTER TABLE NmcTrackingLogMessages ALTER COLUMN tsLog TYPE TIMESTAMPTZ' was not executed. (iRc=-2006)
```

為確保升級後的工作正常，您必須在遷移前刪除視圖，並在遷移後重新建立視圖，同時將其調整為TIMESTAMP WITH TIMEZONE模式。

## 追蹤 {#tracking}

追蹤公式已修改。 移轉時，舊公式(v5)會取代為新公式(v7)。 如果您在Adobe Campaign v5中使用個人化公式，則必須在Adobe Campaign v7中調整此設定（**NmsTracking_ClickFormula**&#x200B;和&#x200B;**NmsTracking_OpenFormula**&#x200B;選項）。

網站追蹤管理也已修改。 執行v7移轉後，您必須啟動部署精靈以完成Web追蹤的設定。

![](assets/migration_web_tracking.png)

提供三種模式：

* **工作階段網頁追蹤**:如果尚 **[!UICONTROL Leads]** 未安裝軟體包，則預設會選取此選項。此選項是效能上最理想的選項，可讓您限制追蹤記錄檔的大小。
* **永久性網頁追蹤**
* **匿名網路追蹤**:如果安 **[!UICONTROL Leads]** 裝了軟體包，預設會選取此選項。這是最耗用資源的選項。 如上所述，必須對&#x200B;**sSourceId**&#x200B;欄建立索引（在追蹤表格和&#x200B;**CrmIncomingLead**&#x200B;表格中）。

>[!NOTE]
>
>有關這三種模式的詳細資訊，請參閱[此部分](../../configuration/using/about-web-tracking.md)。

## Adobe Campaign v7樹結構{#campaign-vseven-tree-structure}

在移轉期間，會根據v7標準自動重新組織樹狀結構。 新資料夾將被添加，過時資料夾將被刪除，其內容將放在「移動」資料夾中。 移轉後，必須檢查此資料夾中的所有項目，顧問必須決定保留或刪除每個項目。 然後，要保留的物品必須移至正確位置。

已新增選項，以停用導覽樹的自動移轉。 此操作現在為手動操作。 不會刪除過時的資料夾，也不會新增新資料夾。 只有在現成的v5導覽樹狀結構發生太多變更時，才應使用此選項。 在移轉前，在&#x200B;**[!UICONTROL Administration > Options]**&#x200B;節點中將選項新增至主控台：

* 內部名稱：NlMigration_KeepFolderStructure
* 資料類型：整數
* 值（文本）:3

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
