---
product: campaign
title: 資料庫清除工作流程
description: 瞭解過時資料如何自動清理
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: b472178316f97f08e9c87f8aebd707709f320e5f
workflow-type: tm+mt
source-wordcount: '2823'
ht-degree: 0%

---

# 資料庫清除工作流程{#database-cleanup-workflow}

![](../../assets/v7-only.svg)

## 簡介 {#introduction}

的 **[!UICONTROL Database cleanup]** 可通過 **[!UICONTROL Administration > Production > Technical workflows]** 節點，用於刪除過時的資料以避免資料庫的指數增長。 工作流自動觸發，無需用戶干預。

![cleanup](assets/ncs_cleanup_workflow.png)

## 設定 {#configuration}

資料庫清理配置在兩個級別：在工作流計畫程式和部署嚮導中。

### 工作流計畫程式 {#the-scheduler}

>[!NOTE]
>
>有關計畫程式的詳細資訊，請參閱 [此部分](../../workflow/using/scheduler.md)。

預設情況下， **[!UICONTROL Database cleanup]** 工作流配置為每天凌晨4點開始。 調度程式允許您更改工作流觸發頻率。 以下頻率可用：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![調度](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>為了 **[!UICONTROL Database cleanup]** 要在計畫程式中定義的日期和時間啟動的工作流，必須啟動工作流引擎(wfserver)。

### 部署嚮導 {#deployment-wizard}

的 **[!UICONTROL Deployment wizard]**，通過 **[!UICONTROL Tools > Advanced]** 的子菜單。 值以天表示。 如果這些值未更改，則工作流將使用預設值。

![](assets/ncs_cleanup_deployment-wizard.png)

的欄位 **[!UICONTROL Purge of data]** 窗口與以下選項一致。 這些任務由執行 **[!UICONTROL Database cleanup]** 工作流：

* 整合跟蹤： **NmsCleanup_TrackingStatPurgeDelay** (請參閱 [清理跟蹤日誌](#cleanup-of-tracking-logs))
* 交貨日誌： **NmsCleanup_BroadLogPurgeDelay** (請參閱 [清除傳遞日誌](#cleanup-of-delivery-logs))
* 跟蹤日誌： **NmsCleanup_TrackingLogPurgeDelay** (請參閱 [清理跟蹤日誌](#cleanup-of-tracking-logs))
* 已刪除的交貨： **NmsCleanup_RecyledDeliveryPurgeDelay** (請參閱 [清除要刪除或回收的交貨](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 導入拒絕： **NmsCleanup_RejectsPurgeDelay** (請參閱 [清除導入生成的廢品](#cleanup-of-rejects-generated-by-imports-))
* 訪問者配置檔案： **NmsCleanup_VisitorPurgeDelay** (請參閱 [清除訪問者](#cleanup-of-visitors))
* 提供建議： **NmsCleanup_PropositionPurgeDelay** (請參閱 [清理命題](#cleanup-of-propositions))

   >[!NOTE]
   >
   >的 **[!UICONTROL Offer propositions]** 欄位僅在 **交互** 已安裝模組。

* 事件： **NmsCleanup_EventPurgeDelay** (請參閱 [清除過期事件](#cleansing-expired-events))
* 存檔事件： **NmsCleanup_EventHistoPurgeDelay** (請參閱 [清除過期事件](#cleansing-expired-events))

   >[!NOTE]
   >
   >的 **[!UICONTROL Events]** 和 **[!UICONTROL Archived events]** 欄位僅在 **消息中心** 已安裝模組。

* 審核跟蹤： **XtkCleanup_AuditTrailPurgeDelay** (請參閱 [清理審核跟蹤](#cleanup-of-audit-trail))

執行的所有任務 **[!UICONTROL Database cleanup]** 工作流將在以下部分中介紹。

## 由資料庫清理工作流執行的任務 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流計畫程式中定義的日期和時間(請參閱 [調度程式](#the-scheduler))，工作流引擎啟動資料庫清理進程。 資料庫清理連接到資料庫，並按如下所示的順序執行任務。

>[!IMPORTANT]
>
>如果其中一個任務失敗，則不執行下一個任務。
>
>SQL查詢 **限制** 重複執行屬性，直到處理所有資訊。


### 要刪除清除的清單 {#lists-to-delete-cleanup}

執行的第一個任務 **[!UICONTROL Database cleanup]** 工作流刪除所有具有 **deleteStatus != 0** 屬性 **NMS組**。 連結到這些組並且存在於其他表中的記錄也會被刪除。

1. 將使用以下SQL查詢恢復要刪除的清單：

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每個清單都有多個指向其他表的連結。 使用以下查詢批量刪除所有這些連結：

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   何處 `$(relatedTable)` 是與 **NMS組** 和 `$(l)` 是清單標識符。

1. 當清單是「清單」類型清單時，將使用以下查詢刪除關聯的表：

   ```sql
   DROP TABLE grp$(l)
   ```

1. 每 **選擇** 通過以下查詢刪除操作恢復的類型清單：

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   何處 `$(l)` 是清單標識符

### 清除要刪除或回收的交貨 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任務清除要刪除或回收的所有交貨。

1. 的 **[!UICONTROL Database cleanup]** 工作流選擇所有交貨 **刪除狀態** 欄位的值 **[!UICONTROL Yes]** 或 **[!UICONTROL Recycled]** 且其刪除日期早於在 **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecyledDeliveryPurgeDelay**)欄位。 有關此內容的詳細資訊，請參閱 [部署嚮導](#deployment-wizard)。 此期間根據當前伺服器日期計算。
1. 對於每個中間採購伺服器，任務將選擇要刪除的交貨清單。
1. 的 **[!UICONTROL Database cleanup]** 工作流刪除交貨日誌、附件、鏡像頁資訊和所有其他相關資料。
1. 在刪除好的交貨之前，工作流會清除以下表中的連結資訊：

   * 在傳遞排除表中(**NmsDlv排除**)，使用以下查詢：

      ```sql
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      何處 **$(l)** 是交貨的標識符。

   * 在優惠券表中(**NmsGouponValue**)，使用以下查詢（含成批刪除）:

      ```sql
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      何處 `$(l)` 是交貨的標識符。

   * 在傳遞日誌表中(**NMSBroadlogXxx**)，批量刪除以20,000條記錄的批次執行。
   * 在產品建議表中(**NMS命題XXX**)，批量刪除以20,000條記錄的批次執行。
   * 在跟蹤日誌表中(**Nms跟蹤日誌Xxx**)，批量刪除以20,000條記錄的批次執行。
   * 在傳遞片段表中(**NmsDeliveryPart**)，批量刪除以500,000條記錄為批執行。 此表包含要傳遞的其餘消息的個性化資訊。
   * 在鏡像頁資料片段表中(**NmsMirrorPageInfo**)，批量刪除是按20,000條記錄對過期交貨部件和已完成或取消的部件執行的。 此表包含有關用於生成鏡像頁的所有消息的個性化資訊。
   * 在鏡像頁搜索表中(**NmsMirrorPageSearch**)，批量刪除以20,000條記錄的批次執行。 此表是搜索索引，它提供對儲存在 **NmsMirrorPageInfo** 的子菜單。
   * 在批處理日誌表中(**Xtk作業日誌**)，批量刪除以20,000條記錄的批次執行。 此表包含要刪除的交貨日誌。
   * 在傳遞URL跟蹤表中(**NmsTrackingUrl**)，使用以下查詢：

      ```sql
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      何處 `$(l)` 是交貨的標識符。

      此表包含在要刪除的遞送中找到的URL，以啟用其跟蹤。

1. 從交貨表中刪除交貨(**Nms交付**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   何處 `$(l)` 是交貨的標識符。

#### 使用中間來源補充的交貨 {#deliveries-using-mid-sourcing}

的 **[!UICONTROL Database cleanup]** 工作流還會刪除中間採購伺服器上的交貨。

1. 為此，工作流將檢查每個傳遞是否處於非活動狀態（基於其狀態）。 如果傳遞處於活動狀態，則在刪除之前將停止它。 檢查通過執行以下查詢執行：

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   何處 **$(l)** 是交貨的標識符。

1. 如果狀態值為 **[!UICONTROL Start pending]** 。 **[!UICONTROL In progress]** 。 **[!UICONTROL Recovery pending]** 。 **[!UICONTROL Recovery in progress]** 。 **[!UICONTROL Pause requested]** 。 **[!UICONTROL Pause in progress]** 或 **[!UICONTROL Paused]** （值51、55、61、62、71、72、75），停止傳遞，任務清除連結的資訊。

### 清除過期的交貨 {#cleanup-of-expired-deliveries}

此任務停止有效期已過的交貨。

1. 的 **[!UICONTROL Database cleanup]** 工作流建立已過期的交貨清單。 此清單包括狀態為「非」的所有過期交貨 **[!UICONTROL Finished]** ，以及最近停止的包含超過10,000條未處理消息的交付。 使用以下查詢：

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   何處 `delivery mode 1` 與 **[!UICONTROL Mass delivery]** 模式， `state 51` 與 **[!UICONTROL Start pending]** 州， `state 85` 與 **[!UICONTROL Stopped]** 狀態，並且傳遞伺服器上成批更新的傳遞日誌的最大數目等於10,000。

1. 然後，工作流將包括使用中間來源補充的最近過期交貨的清單。 不包括尚未通過中間採購伺服器恢復交貨日誌的交貨。

   使用以下查詢：

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查詢用於檢測外部帳戶是否仍處於活動狀態，以便按日期篩選交貨：

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在過期交貨的清單中，狀態為 **[!UICONTROL Pending]** ，切換到 **[!UICONTROL Delivery cancelled]** ，此清單中的所有交貨都切換到 **[!UICONTROL Finished]** 。

   使用以下查詢：

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   何處 `$(curdate)`是資料庫伺服器的當前日期， `$(bl)` 是傳遞日誌消息的標識符， `$(dl)` 是傳遞標識符， `delivery status 6` 與 **[!UICONTROL Pending]** 狀態和 `delivery status 7` 與 **[!UICONTROL Delivery cancelled]** 狀態。

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   何處 `delivery state 95` 與 **[!UICONTROL Finished]** 狀態和 `$(dl)` 是交貨的標識符。

1. 所有片段(**交付部件**)，並刪除所有正在執行的通知傳遞的過時片段。 成批刪除用於這兩個任務。

   使用以下查詢：

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   何處 `delivery state 95` 與 **[!UICONTROL Finished]** 狀態， `delivery state 85` 與 **[!UICONTROL Stopped]** 狀態和 `$(curDate)` 是當前伺服器日期。

### 清除鏡像頁 {#cleanup-of-mirror-pages}

此任務刪除交付所使用的Web資源（鏡像頁）。

1. 首先，使用以下查詢恢復要清除的交貨清單：

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   何處 `$(curDate)` 是當前伺服器日期。

1. 的 **NmsMirrorPageInfo** 然後，如果需要，使用先前恢復的交貨的標識符清除表。 成批刪除用於生成以下查詢：

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   何處 `$(dl)` 是交貨的標識符。

1. 然後，將一個條目添加到傳遞日誌。
1. 然後識別清除的交貨，以避免以後必須重新處理。 將執行以下查詢：

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   何處 `$(strIn)` 是傳遞標識符的清單。

### 清理工作表 {#cleanup-of-work-tables}

此任務從資料庫中刪除與狀態為 **[!UICONTROL Being edited]** 。 **[!UICONTROL Stopped]** 或 **[!UICONTROL Deleted]** 。

1. 名稱以開頭的表清單 **wkDlv_** 首先使用以下查詢(postgresql)恢復：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後，將排除正在進行的工作流使用的表。 為此，將使用以下查詢恢復正在進行的交貨清單：

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   何處 `0` 是與 **[!UICONTROL Being edited]** 交貨狀態， `85` 與 **[!UICONTROL Stopped]** 狀態和 `100` 與 **[!UICONTROL Deleted]** 狀態。

1. 不再使用的表將使用以下查詢刪除：

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 清除導入生成的廢品 {#cleanup-of-rejects-generated-by-imports-}

此步驟允許您刪除在導入期間未處理所有資料的記錄。

1. 對 **Xtk拒絕** 表格，其中包含以下查詢：

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   何處 `$(curDate)` 是當前伺服器日期，我們從中減去為 **NmsCleanup_RejectsPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard)) `$(l)` 是要成批刪除的最大記錄數。

1. 然後，使用以下查詢刪除所有孤立拒絕：

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流實例 {#cleanup-of-workflow-instances}

此任務使用其標識符清除每個工作流實例(**工作流ID**)和歷史記錄(**歷史**)。 它通過再次運行工作表清理任務來刪除非活動表。 清除還刪除已刪除工作流的所有孤立工作表（wkf%和wkfhisto%）。

>[!NOTE]
>
>為中的每個工作流指定歷史記錄的清除頻率 **日曆** 欄位（預設值30天）。 可以在 **執行** 頁籤。 如需詳細資訊，請參閱[本章節](../../workflow/using/workflow-properties.md#execution)。

1. 要恢復要刪除的工作流清單，請使用以下查詢：

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查詢將生成工作流清單，這些工作流將使用以下查詢來刪除所有連結的日誌、完成的任務和完成的事件：

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   何處 `$(lworkflow)` 是工作流的標識符 `$(lhistory)` 是歷史記錄的標識符。

1. 所有未使用的表都將被刪除。 為此目的，所有桌子都由於 **wkf%** 使用以下查詢鍵入掩碼(postgresql):

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後，將排除掛起工作流實例使用的所有表。 使用以下查詢恢復活動工作流清單：

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然後恢復每個工作流標識符，以查找正在進行的工作流使用的表的名稱。 這些名稱將從先前恢復的表清單中排除。
1. 「增量查詢」類型活動歷史記錄表使用以下查詢排除：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   何處 `$(strcondition)` 是與 **wfhisto%** 蒙版。

1. 剩餘的表將使用以下查詢刪除：

   ```sql
   DROP TABLE wkf15487_12;
   ```

### 清除工作流登錄 {#cleanup-of-workflow-logins}

此任務使用以下查詢刪除工作流登錄：

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立工作表 {#cleanup-of-orphan-work-tables}

此任務刪除連結到組的孤立工作表。 的 **NMS組** 表儲存要清除的組（類型與0不同）。 表名的前置詞是 **grp**。 要標識要清除的組，請使用以下查詢：

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清除訪問者 {#cleanup-of-visitors}

此任務使用成批刪除從訪問者表中刪除過時記錄。 過時記錄是指上次修改時間早於部署嚮導中定義的保存期的記錄(請參閱 [部署嚮導](#deployment-wizard))。 使用以下查詢：

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

何處 `$(tsDate)` 是當前伺服器日期，從中減去為 **NmsCleanup_VisitorPurgeDelay** 的雙曲餘切值。

### NPAI的清理 {#cleanup-of-npai}

此任務允許您從 **NMS地址** 的子菜單。 以下查詢用於執行成批刪除：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

何處 `status 2` 與 **[!UICONTROL Valid]** 狀態， `$(tsDate1)` 是當前伺服器日期， `$(tsDate2)` 與 **NmsCleanup_LastCleanup** 的雙曲餘切值。

### 清除訂閱 {#cleanup-of-subscriptions-}

此任務清除用戶從 **Nms訂閱** 表，使用成批刪除。 使用以下查詢：

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清理跟蹤日誌 {#cleanup-of-tracking-logs}

此任務從跟蹤日誌表和Web跟蹤日誌表中刪除過時記錄。 過時記錄是指早於部署嚮導中定義的保存期的記錄(請參閱 [部署嚮導](#deployment-wizard))。

1. 首先，使用以下查詢恢復跟蹤日誌表的清單：

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批刪除用於清除先前恢復的表清單中的所有表。 使用以下查詢：

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   何處 `$(tsDate)` 是當前伺服器日期，我們從中減去為 **NmsCleanup_TrackingLogPurgeDelay** 的雙曲餘切值。

1. 跟蹤統計表使用成批刪除來清除。 使用以下查詢：

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   何處 `$(tsDate)` 是當前伺服器日期，我們從中減去為 **NmsCleanup_TrackingStatPurgeDelay** 的雙曲餘切值。

### 清除傳遞日誌 {#cleanup-of-delivery-logs}

此任務允許您清除儲存在各種表中的傳遞日誌。

1. 為此，使用以下查詢恢復傳遞日誌架構清單：

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中間採購時， **NmsBroadLogMid** 在傳遞映射中未引用表。 的 **nms:broadLogMid** 將架構添加到由上一個查詢恢復的清單中。
1. 的 **資料庫清理** 然後，工作流會從以前恢復的表中清除過時資料。 使用以下查詢：

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   何處 `$(tableName)` 是架構清單中每個表的名稱， `$(option)` 是為 **NmsCleanup_BroadLogPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))。

1. 最後，工作流檢查 **NmsProviderMsgId** 表存在。 如果是，則使用以下查詢刪除所有過時資料：

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   何處 `$(option)` 與為 **NmsCleanup_BroadLogPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))。

### 清除NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任務清除 **NmsEmailErrorStat** 的子菜單。 主程式(**合併錯誤**)定義兩個日期：

* **開始日期**:與 **NmsLastErrorStatCoalesce** 的子菜單。
* **結束日期**:當前伺服器日期。

如果開始日期大於或等於結束日期，則不會進行任何進程。 在這個例子中， **合併更新** 的子菜單。

如果開始日期早於結束日期， **NmsEmailErrorStat** 已清除表。

中的錯誤總數 **NmsEmailErrorStat** 使用以下查詢恢復起始日期和終止日期之間的表：

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

何處 `$end` 和 `$start` 是先前定義的起始日期和終止日期。

如果總數大於0:

1. 執行以下查詢，以僅將錯誤保持在超過特定閾值（等於20）:

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. 的 **合併錯誤** 的子菜單。
1. 建立新連接以刪除在開始日期和結束日期之間發生的所有錯誤。 使用以下查詢：

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 每個錯誤都保存在 **NmsEmailErrorStat** 表格：

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   其中，每個變數與前一個查詢恢復的值匹配。

1. 的 **開始** 變數將用上一進程的值更新，以完成循環。

循環和任務停止。

在 **NmsEmailError** 和 **清理NmsMx域** 的下界。

### 清除NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用以下查詢：

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢將刪除中沒有連結記錄的所有行 **NmsEmailErrorStat** 從 **NmsEmailError** 的子菜單。

### 清除NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用以下查詢：

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢將刪除所有在中沒有連結記錄的行 **NmsEmailErrorStat** 表格 **NmsMx域** 的子菜單。

### 清理命題 {#cleanup-of-propositions}

如果 **交互** 已安裝模組，執行此任務以清除 **NMS命題XXX** 的下界。

使用以下查詢，可恢復命題表清單，並對每個命題表執行成批刪除：

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

何處 `$(option)` 是為 **NmsCleanup_PropositionPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))。

### 清理模擬表 {#cleanup-of-simulation-tables}

此任務清除孤立模擬表（不再連結到提供模擬或交付模擬）。

1. 要恢復需要清除的模擬清單，請使用以下查詢：

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要刪除的表的名稱由 **wkSimu_** 前置詞後跟模擬的標識符(例如： **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 清理審核跟蹤 {#cleanup-of-audit-trail}

使用以下查詢：

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

何處 **$（ts日期）** 是為 **XtkCleanup_AuditTrailPurgeDelay** 選項。

### 清除Nms地址 {#cleanup-of-nmsaddress}

使用以下查詢：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查詢刪除與iOS和Android相關的所有條目。

### 統計更新和儲存優化 {#statistics-update}

的 **XtkCleanup_NoStats** 選項，用於控制清除工作流的儲存優化步驟的行為。

如果 **XtkCleanup_NoStats** 選項不存在，或者如果其值為0，則將在PostgreSQL上以詳細模式(DAVOMUS VERBOSE ANALYZE)執行儲存優化，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 DAVOUM將輸出以下格式的行： `INFO: vacuuming "public.nmsactivecontact"` 並且ANALYZE將以以下格式輸出行： `INFO: analyzing "public.nmsactivecontact"`。

如果選項的值為1，則不對任何資料庫執行統計資訊更新。 以下日誌行將出現在工作流日誌中： `Option 'XtkCleanup_NoStats' is set to '1'`。

如果選項的值為2，則將在PostgreSQL上以詳細模式(ANALYZE VERBOSE)執行儲存分析，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 ANALYZE將以以下格式輸出行： `INFO: analyzing "public.nmsactivecontact"`。

### 訂閱清理(NMAC) {#subscription-cleanup--nmac-}

此任務刪除與已刪除服務或移動應用程式相關的任何訂閱。

要恢復廣播方案清單，請使用以下查詢：

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然後，該任務將恢復連結到 **appSubscription** 連結並刪除這些表。

此清除工作流還刪除自在中設定的時間以來未更新的idabled = 1的所有條目 **NmsCleanup_AppSubscriptionRcpPurgeDelay** 的雙曲餘切值。

### 清除會話資訊 {#cleansing-session-information}

此任務清除 **會話資訊** 表中，使用以下查詢：

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清除過期事件 {#cleansing-expired-events}

此任務清除在執行實例上接收和儲存的事件以及在控制實例上存檔的事件。

### 清洗反應 {#cleansing-reactions}

此任務清除反應（表） **NmsRemaMatchRcp**)，這些假設本身已被刪除。
