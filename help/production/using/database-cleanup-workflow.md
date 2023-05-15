---
product: campaign
title: 資料庫清除工作流程
description: 了解過期資料如何自動清理
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '2823'
ht-degree: 0%

---

# 資料庫清除工作流程{#database-cleanup-workflow}



## 簡介 {#introduction}

此 **[!UICONTROL Database cleanup]** 可透過 **[!UICONTROL Administration > Production > Technical workflows]** 節點，可讓您刪除過時的資料，以避免資料庫呈指數增長。 工作流程會自動觸發，使用者不需干預。

![cleanup](assets/ncs_cleanup_workflow.png)

## 設定 {#configuration}

資料庫清理是在兩個級別上配置的：在工作流程排程器和部署精靈中。

### 工作流程排程器 {#the-scheduler}

>[!NOTE]
>
>有關調度程式的詳細資訊，請參閱 [本節](../../workflow/using/scheduler.md).

依預設， **[!UICONTROL Database cleanup]** 工作流程已設定為每天凌晨4:00開始。 排程器可讓您變更工作流程觸發頻率。 下列頻率可用：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![排程器](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>為了 **[!UICONTROL Database cleanup]** 要在調度程式中定義的日期和時間啟動工作流，必須啟動工作流引擎(wfserver)。

### 部署嚮導 {#deployment-wizard}

此 **[!UICONTROL Deployment wizard]**，可透過 **[!UICONTROL Tools > Advanced]** 功能表，可讓您設定資料的儲存時間。 值以天表示。 如果這些值未更改，工作流程將使用預設值。

![](assets/ncs_cleanup_deployment-wizard.png)

的欄位 **[!UICONTROL Purge of data]** 窗口與以下選項一致。 這些會由執行的部分任務使用 **[!UICONTROL Database cleanup]** 工作流程：

* 整合追蹤： **NmsCleanup_TrackingStatPurgeDelay** (請參閱 [清除追蹤記錄](#cleanup-of-tracking-logs))
* 傳送記錄檔： **NmsCleanup_BroadLogPurgeDelay** (請參閱 [清除傳送記錄檔](#cleanup-of-delivery-logs))
* 追蹤記錄： **NmsCleanup_TrackingLogPurgeDelay** (請參閱 [清除追蹤記錄](#cleanup-of-tracking-logs))
* 已刪除的傳送： **NmsCleanup_RecycledDeliveryPurgeDelay** (請參閱 [清除要刪除或回收的傳遞](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 導入拒絕： **NmsCleanup_RejectsPurgeDelay** (請參閱 [清除匯入產生的拒絕](#cleanup-of-rejects-generated-by-imports-))
* 訪客設定檔： **NmsCleanup_VisitorPurgeDelay** (請參閱 [訪客清除](#cleanup-of-visitors))
* 提案： **NmsCleanup_PostitionPurgeDelay** (請參閱 [清理命題](#cleanup-of-propositions))

   >[!NOTE]
   >
   >此 **[!UICONTROL Offer propositions]** 欄位僅在 **互動** 模組已安裝。

* 事件： **NmsCleanup_EventPurgeDelay** (請參閱 [清除過期事件](#cleansing-expired-events))
* 封存的事件： **NmsCleanup_EventHistoPurgeDelay** (請參閱 [清除過期事件](#cleansing-expired-events))

   >[!NOTE]
   >
   >此 **[!UICONTROL Events]** 和 **[!UICONTROL Archived events]** 欄位只有在 **訊息中心** 模組已安裝。

* 稽核軌跡： **XtkCleanup_AuditTrailPurgeDelay** (請參閱 [清理稽核軌跡](#cleanup-of-audit-trail))

由 **[!UICONTROL Database cleanup]** 以下章節會說明工作流程。

## 由資料庫清理工作流執行的任務 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流程排程器中定義的日期和時間(請參閱 [排程器](#the-scheduler))，工作流程引擎就會啟動資料庫清理程式。 資料庫清理會連接到資料庫，並按如下所示的順序執行任務。

>[!IMPORTANT]
>
>如果其中一個任務失敗，則不執行下一個任務。
>
>SQL查詢 **限制** 屬性會重複執行，直到處理所有資訊為止。


### 要刪除清理的清單 {#lists-to-delete-cleanup}

由 **[!UICONTROL Database cleanup]** 工作流程會刪除所有具有 **deleteStatus != 0** 屬性 **NmsGroup**. 也會刪除連結到這些組的記錄，以及存在於其他表中的記錄。

1. 要刪除的清單將使用以下SQL查詢進行恢復：

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每個清單都有多個其他表格的連結。 會使用下列查詢大量刪除這些連結：

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   where `$(relatedTable)` 是與 **NmsGroup** 和 `$(l)` 是清單識別碼。

1. 當該清單為「清單」類型清單時，將使用以下查詢刪除關聯表：

   ```sql
   DROP TABLE grp$(l)
   ```

1. 每個 **選擇** 使用以下查詢刪除操作恢復的類型清單：

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   where `$(l)` 是清單識別碼

### 清除要刪除或回收的傳遞 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任務將清除要刪除或回收的所有傳送。

1. 此 **[!UICONTROL Database cleanup]** 工作流程會選取所有傳送 **deleteStatus** 欄位有值 **[!UICONTROL Yes]** 或 **[!UICONTROL Recycled]** 且其刪除日期早於 **[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**)部署精靈的欄位。 有關詳細資訊，請參閱 [部署嚮導](#deployment-wizard). 此期間會與目前伺服器日期比較計算。
1. 對於每個中間來源伺服器，任務將選擇要刪除的傳送清單。
1. 此 **[!UICONTROL Database cleanup]** 工作流程會刪除傳送記錄檔、附件、鏡像頁面資訊和所有其他相關資料。
1. 在刪除正確的傳送之前，工作流程會從下表清除連結的資訊：

   * 在傳送排除表格中(**NmsDlvExclusion**)，則會使用下列查詢：

      ```sql
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      where **$(l)** 是傳送的識別碼。

   * 在抵用券表格中(**NmsCouponValue**)，則會使用下列查詢（含大量刪除）:

      ```sql
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      where `$(l)` 是傳送的識別碼。

   * 在傳送記錄表(**NmsBroadlogXxx**)，則會以20,000筆記錄的批次執行大量刪除。
   * 在優惠方案主張表格中(**NmsPostimationXxx**)，則會以20,000筆記錄的批次執行大量刪除。
   * 在追蹤記錄表(**NmsTrackinglogXxx**)，則會以20,000筆記錄的批次執行大量刪除。
   * 在傳送片段表格(**NmsDeliveryPart**)，則會以500,000筆記錄的批次執行大量刪除。 此表格包含要傳送之其餘訊息的個人化資訊。
   * 在鏡像頁資料片段表中(**NmsMirrorPageInfo**)，批量刪除將針對過期的傳送部件和已完成或已取消的部件執行20,000條記錄。 此表包含有關用於生成鏡像頁的所有消息的個人化資訊。
   * 在鏡像頁搜索表(**NmsMirrorPageSearch**)，則會以20,000筆記錄的批次執行大量刪除。 此表格是搜尋索引，可提供對儲存在 **NmsMirrorPageInfo** 表格。
   * 在批處理日誌表中(**XtkJobLog**)，則會以20,000筆記錄的批次執行大量刪除。 此表包含要刪除的傳送記錄。
   * 在傳送URL追蹤表格中(**NmsTrackingUrl**)，則會使用下列查詢：

      ```sql
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      where `$(l)` 是傳送的識別碼。

      此表格包含要刪除的傳送中找到的URL，以啟用其追蹤。

1. 傳送會從傳送表格(**NmsDelivery**):

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   where `$(l)` 是傳送的識別碼。

#### 使用中間來源的傳送 {#deliveries-using-mid-sourcing}

此 **[!UICONTROL Database cleanup]** 工作流程也會刪除中間來源伺服器上的傳送。

1. 為此，工作流程會檢查每個傳送是否為非作用中（根據其狀態）。 如果傳送處於作用中狀態，則會在刪除傳送前停止傳送。 檢查通過執行以下查詢來執行：

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   where **$(l)** 是傳送的識別碼。

1. 如果狀態的值為 **[!UICONTROL Start pending]** , **[!UICONTROL In progress]** , **[!UICONTROL Recovery pending]** , **[!UICONTROL Recovery in progress]** , **[!UICONTROL Pause requested]** , **[!UICONTROL Pause in progress]** ，或 **[!UICONTROL Paused]** （值51、55、61、62、71、72、75），則停止傳送並清除連結的資訊。

### 清除過期的傳送 {#cleanup-of-expired-deliveries}

此任務將停止有效期已過的傳送。

1. 此 **[!UICONTROL Database cleanup]** 工作流程會建立已過期的傳送清單。 此清單包含狀態為非 **[!UICONTROL Finished]** ，以及最近停止傳送超過10,000個未處理的訊息。 使用下列查詢：

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   where `delivery mode 1` 符合 **[!UICONTROL Mass delivery]** 模式， `state 51` 符合 **[!UICONTROL Start pending]** 州， `state 85` 符合 **[!UICONTROL Stopped]** 狀態，且傳送伺服器上大量更新的傳送記錄數最多等於10,000。

1. 然後，工作流程會包含使用中間來源的最近過期傳送清單。 尚未透過中間來源伺服器復原傳送記錄的傳送則會排除。

   使用下列查詢：

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 下列查詢可用來偵測外部帳戶是否仍為作用中狀態，以便依日期篩選傳送：

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在過期傳遞的清單中，狀態為 **[!UICONTROL Pending]** ，切換至 **[!UICONTROL Delivery cancelled]** ，此清單中的所有傳送會切換至 **[!UICONTROL Finished]** .

   使用下列查詢：

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   where `$(curdate)`是資料庫伺服器的當前日期， `$(bl)` 是傳送記錄檔訊息的識別碼， `$(dl)` 是傳遞識別碼， `delivery status 6` 符合 **[!UICONTROL Pending]** 狀態與 `delivery status 7` 符合 **[!UICONTROL Delivery cancelled]** 狀態。

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   where `delivery state 95` 符合 **[!UICONTROL Finished]** 狀態，和 `$(dl)` 是傳送的識別碼。

1. 所有片段(**deliveryParts**)，並刪除所有進行中通知傳送的過時片段。 這兩個任務都使用大量刪除。

   使用下列查詢：

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   where `delivery state 95` 符合 **[!UICONTROL Finished]** 狀態， `delivery state 85` 符合 **[!UICONTROL Stopped]** 狀態，和 `$(curDate)` 是目前的伺服器日期。

### 清除鏡像頁面 {#cleanup-of-mirror-pages}

此任務會刪除傳送使用的Web資源（鏡像頁面）。

1. 首先，系統會使用下列查詢來復原要清除的傳送清單：

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   where `$(curDate)` 是目前的伺服器日期。

1. 此 **NmsMirrorPageInfo** 然後，如有必要，會使用先前已復原傳送的識別碼來清除表格。 成批刪除用於生成以下查詢：

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   where `$(dl)` 是傳送的識別碼。

1. 然後，項目會新增至傳送記錄檔。
1. 之後會識別已清除的傳送，以避免稍後重新處理。 會執行下列查詢：

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   where `$(strIn)` 是傳遞識別碼的清單。

### 清除工作表 {#cleanup-of-work-tables}

此任務從資料庫中刪除，所有與狀態為的傳送匹配的工作表 **[!UICONTROL Being edited]** , **[!UICONTROL Stopped]** 或 **[!UICONTROL Deleted]** .

1. 名稱開頭為的表清單 **wkDlv_** 會先透過下列查詢(postgresql)復原：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 接著會排除進行中的工作流程所使用的表格。 要執行此操作，系統會使用下列查詢來復原進行中的傳送清單：

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   where `0` 是與 **[!UICONTROL Being edited]** 傳遞狀態， `85` 符合 **[!UICONTROL Stopped]** 狀態與 `100` 符合 **[!UICONTROL Deleted]** 狀態。

1. 不再使用的表將使用以下查詢刪除：

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 清除匯入產生的拒絕 {#cleanup-of-rejects-generated-by-imports-}

此步驟可讓您刪除匯入期間未處理所有資料的記錄。

1. 會對 **XtkReject** 表格，其中包含下列查詢：

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   where `$(curDate)` 是目前伺服器日期，我們會從中減去為 **NmsCleanup_RejectsPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))和 `$(l)` 是要成批刪除的最大記錄數。

1. 然後，會使用下列查詢刪除所有孤立拒絕：

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流程例項 {#cleanup-of-workflow-instances}

此任務使用其標識符清除每個工作流實例(**lWorkflowId**)和歷史記錄(**lHistory**)。 它通過再次運行工作表清理任務刪除非活動表。 清除也會刪除已刪除工作流程的所有孤立工作台（wkf%和wkfhisto%）。

>[!NOTE]
>
>系統會為 **以天為單位的歷史記錄** 欄位（預設值30天）。 您可以在 **執行** 頁簽。 如需詳細資訊，請參閱[本章節](../../workflow/using/workflow-properties.md#execution)。

1. 若要復原要刪除的工作流程清單，會使用下列查詢：

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查詢會使用下列查詢，產生用於刪除所有連結記錄、已完成任務和已完成事件的工作流程清單：

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   where `$(lworkflow)` 是工作流程的識別碼，且 `$(lhistory)` 是歷史記錄的識別碼。

1. 所有未使用的表都將被刪除。 為此，會透過 **wkf%** 使用下列查詢(postgresql)輸入掩碼：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後，將排除掛起工作流實例使用的所有表。 使用下列查詢可恢復活動工作流清單：

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然後，恢復每個工作流標識符，以查找正在進行的工作流所使用的表的名稱。 這些名稱將從先前恢復的表清單中排除。
1. 使用以下查詢排除「增量查詢」類型的活動歷史記錄表：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   where `$(strcondition)` 是與 **wkfhisto%** 遮罩。

1. 其餘表使用以下查詢刪除：

   ```sql
   DROP TABLE wkf15487_12;
   ```

### 清除工作流程登入 {#cleanup-of-workflow-logins}

此任務使用以下查詢刪除工作流登錄：

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立工作表 {#cleanup-of-orphan-work-tables}

此任務將刪除連結到組的孤立工作表。 此 **NmsGroup** 表儲存要清除的組（類型與0不同）。 表名的前置詞為 **grp**. 要標識要清除的組，將使用以下查詢：

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 訪客清除 {#cleanup-of-visitors}

此任務使用批量刪除從訪客表中刪除過時記錄。 過時記錄是指上次修改時間早於部署嚮導中定義的保護期的記錄(請參閱 [部署嚮導](#deployment-wizard))。 使用下列查詢：

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

where `$(tsDate)` 是目前的伺服器日期，我們會減去為 **NmsCleanup_VisitorPurgeDelay** 選項。

### 清除NPAI {#cleanup-of-npai}

此任務可讓您從 **NmsAddress** 表格。 以下查詢用於執行成批刪除：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

where `status 2` 符合 **[!UICONTROL Valid]** 狀態， `$(tsDate1)` 是目前的伺服器日期，和 `$(tsDate2)` 符合 **NmsCleanup_LastCleanup** 選項。

### 清除訂閱 {#cleanup-of-subscriptions-}

此任務會清除使用者從 **NmsSubscription** 表格，使用大量刪除。 使用下列查詢：

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清除追蹤記錄 {#cleanup-of-tracking-logs}

此任務從跟蹤日誌表和網路跟蹤日誌表中刪除過時記錄。 過時記錄是指早於部署嚮導中定義的保護期(請參閱 [部署嚮導](#deployment-wizard))。

1. 首先，使用下列查詢來復原追蹤記錄表清單：

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批刪除用於清除先前恢復的表清單中的所有表。 使用下列查詢：

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   where `$(tsDate)` 是目前伺服器日期，我們會從中減去為 **NmsCleanup_TrackingLogPurgeDelay** 選項。

1. 追蹤統計資料表格會使用大量刪除來清除。 使用下列查詢：

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   where `$(tsDate)` 是目前伺服器日期，我們會從中減去為 **NmsCleanup_TrackingStatPurgeDelay** 選項。

### 清除傳送記錄檔 {#cleanup-of-delivery-logs}

此任務可讓您清除儲存在各種表格中的傳送日誌。

1. 為此，會使用下列查詢來復原傳送記錄結構清單：

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中間來源時， **NmsBroadLogMid** 未在傳遞映射中引用表。 此 **nms:broadLogMid** 架構會新增至上一個查詢所復原的清單。
1. 此 **資料庫清理** 然後，工作流程會從先前復原的表格中清除過時資料。 使用下列查詢：

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   where `$(tableName)` 是結構清單中每個表的名稱，和 `$(option)` 是為 **NmsCleanup_BroadLogPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))。

1. 最後，工作流程會檢查 **NmsProviderMsgId** 表存在。 若存在，則會使用下列查詢來刪除所有過時資料：

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   where `$(option)` 符合為 **NmsCleanup_BroadLogPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))。

### 清理NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任務會清除 **NmsEmailErrorStat** 表格。 主程式(**coalesceErrors**)定義兩個日期：

* **開始日期**:與 **NmsLastErrorStatCoalesce** 選項或表格中的最近日期。
* **結束日期**:當前伺服器日期。

如果開始日期大於或等於結束日期，則不會進行任何程式。 在此情況下， **coalesceUpToDate** 訊息。

如果開始日期早於結束日期，則 **NmsEmailErrorStat** 已清理表格。

中的錯誤總數 **NmsEmailErrorStat** 表格在開始日期和結束日期之間使用以下查詢進行恢復：

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

where `$end` 和 `$start` 是先前定義的開始和結束日期。

如果總計大於0:

1. 執行下列查詢，僅將錯誤保持在超過特定臨界值（等於20）:

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. 此 **合併錯誤** 訊息。
1. 系統會建立新連線，以刪除開始日期與結束日期之間發生的所有錯誤。 使用下列查詢：

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 每個錯誤都會儲存在 **NmsEmailErrorStat** 表格（使用下列查詢）:

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   其中，每個變數都符合上一個查詢所復原的值。

1. 此 **開始** 變數會以上一個程式的值更新，以完成回圈。

循環和任務停止。

清除會在 **NmsEmailError** 和 **cleanupNmsMxDomain** 表格。

### 清理NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用下列查詢：

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢會刪除中沒有連結記錄的所有行 **NmsEmailErrorStat** 從 **NmsEmailError** 表格。

### 清理NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用下列查詢：

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢會刪除所有行，這些行中沒有連結的記錄 **NmsEmailErrorStat** 表格 **NmsMxDomain** 表格。

### 清理命題 {#cleanup-of-propositions}

若 **互動** 模組已安裝，則執行此任務以清除 **NmsPostimationXxx** 表格。

使用以下查詢恢復命題表清單，並對每個命題表執行批量刪除：

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

where `$(option)` 是為 **NmsCleanup_PostitionPurgeDelay** 選項(請參閱 [部署嚮導](#deployment-wizard))。

### 清理模擬表 {#cleanup-of-simulation-tables}

此任務會清除孤立模擬表（不再連結至選件模擬或傳送模擬）。

1. 若要復原需要清除的模擬清單，會使用下列查詢：

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要刪除的表的名稱由 **wkSimu_** 前置詞後跟模擬的標識符(例如： **wkSimu_456831_aggr**):

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 清理稽核軌跡 {#cleanup-of-audit-trail}

使用下列查詢：

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

where **$(tsDate)** 是目前伺服器日期，為 **XtkCleanup_AuditTrailPurgeDelay** 選項減去。

### 清除Nmsaddress {#cleanup-of-nmsaddress}

使用下列查詢：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查詢會刪除與iOS和Android相關的所有項目。

### 統計資訊更新和儲存優化 {#statistics-update}

此 **XtkCleanup_NoStats** 選項可讓您控制清理工作流程中儲存最佳化步驟的行為。

若 **XtkCleanup_NoStats** 選項不存在，或者如果其值為0，則將在PostgreSQL上以冗餘模式(VAMU VERBOSE ANALYZE)執行儲存優化，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 VAMU將輸出以下格式的行： `INFO: vacuuming "public.nmsactivecontact"` 和ANALYZE將輸出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

如果選項的值為1，則不會對任何資料庫執行統計資訊更新。 工作流程記錄檔中會顯示下列記錄行： `Option 'XtkCleanup_NoStats' is set to '1'`.

如果選項的值為2，則將在PostgreSQL上以詳細模式(ANALYZE VERBOSE)執行儲存分析，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 ANALYZE將輸出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`.

### 訂閱清除(NMAC) {#subscription-cleanup--nmac-}

此任務將刪除與已刪除服務或移動應用程式相關的任何訂閱。

若要復原broadlog結構清單，請使用下列查詢：

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然後，任務將恢復連結到的表的名稱 **appSubscription** 連結並刪除這些表格。

此清理工作流程也會刪除自 **NmsCleanup_AppSubscriptionRcpPurgeDelay** 選項。

### 清除會話資訊 {#cleansing-session-information}

此任務會清除 **sessionInfo** 表格中，會使用下列查詢：

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清除過期事件 {#cleansing-expired-events}

此任務會清除在執行實例上接收和儲存的事件以及在控制實例上存檔的事件。

### 清除反應 {#cleansing-reactions}

此任務將清除反應(表 **NmsRemaMatchRcp**)，這些假設本身已被刪除。
