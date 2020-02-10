---
title: 資料庫清除工作流程
seo-title: 資料庫清除工作流程
description: 資料庫清除工作流程
seo-description: null
page-status-flag: never-activated
uuid: a7478641-cdf6-4bd4-9dd7-0c84416c9de6
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: production
content-type: reference
topic-tags: data-processing
discoiquuid: 6b188d78-abb4-4f03-80b9-051ce960f43c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: d5813af76e3cad16d9094a19509dcb855e36c01f

---


# 資料庫清除工作流程{#database-cleanup-workflow}

## 簡介 {#introduction}

可通 **[!UICONTROL Database cleanup]** 過節點訪問的工 **[!UICONTROL Administration > Production > Technical workflows]** 作流可讓您刪除過時的資料，以避免資料庫的指數級增長。 工作流程會自動觸發，使用者不需干預。

![](assets/ncs_cleanup_workflow.png)

## 配置 {#configuration}

資料庫清理配置在兩個級別上：在工作流調度程式和部署嚮導中。

### 排程器 {#the-scheduler}

>[!NOTE]
>
>For more on the scheduler, refer to [this section](../../workflow/using/scheduler.md).

依預設，工 **[!UICONTROL Database cleanup]** 作流程設定為每日4AM開始。 排程器可讓您變更工作流程觸發頻率。 以下是可用頻率：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!CAUTION]
>
>要使工作流 **[!UICONTROL Database cleanup]** 在調度器中定義的日期和時間啟動，必須啟動工作流引擎(wfserver)。 如果不是這樣，則資料庫清理要等到下次啟動工作流引擎時才進行。

### 部署精靈 {#deployment-wizard}

透過 **[!UICONTROL Deployment wizard]** 功能表存取的 **[!UICONTROL Tools > Advanced]** 資料，可讓您設定資料儲存的時間長度。 值以天數表示。 如果這些值未變更，工作流程會使用預設值。

![](assets/ncs_cleanup_deployment-wizard.png)

窗口的字 **[!UICONTROL Purge of data]** 段與以下選項一致。 工作流執行的某些任務將使用這些 **[!UICONTROL Database cleanup]** 任務：

* 整合追蹤： **NmsCleanup_TrackingStatPurgeDelay** (請參 [閱追蹤記錄清理](#cleanup-of-tracking-logs))
* 傳送記錄檔： **NmsCleanup_BroadLogPurgeDelay** (請參 [閱Cleanup of delivery logs](#cleanup-of-delivery-logs))
* 追蹤記錄檔： **NmsCleanup_TrackingLogPurgeDelay** (請參 [閱追蹤記錄清理](#cleanup-of-tracking-logs))
* 已刪除傳送： **NmsCleanup_RecycledDeliveryPurgeDelay** (請參 [閱要刪除或回收的交貨的清理](#cleanup-of-deliveries-to-be-deleted-or-recycled))
* 匯入拒絕： **NmsCleanup_RejectsPurgeDelay** (請參 [閱Cleanup of rejects by imports](#cleanup-of-rejects-generated-by-imports-))
* 訪客資料： **NmsCleanup_VisitorPurgeDelay** (請參 [閱Cleanup of visitors](#cleanup-of-visitors))
* 提供的建議： **NmsCleanup_CompositionPurgeDelay** (請參 [閱Cleanup of propositions](#cleanup-of-propositions))

   >[!NOTE]
   >
   >該 **[!UICONTROL Offer propositions]** 欄位僅在安裝 **Interaction** 模組時可用。

* 事件： **NmsCleanup_EventPurgeDelay** (請參 [閱清除過期事件](#cleansing-expired-events))
* 已封存事件： **NmsCleanup_EventHistoPurgeDelay** (請參閱 [清除過期事件](#cleansing-expired-events))

   >[!NOTE]
   >
   >只有在 **[!UICONTROL Events]** 安裝了 **[!UICONTROL Archived events]** Message Center模組時，才可 **** 以使用和欄位。

* 稽核記錄： **XtkCleanup_AuditTrailPurgeDelay** (請參 [閱Cleanup of Audit Trail](#cleanup-of-audit-trail))

工作流執行的所有任 **[!UICONTROL Database cleanup]** 務將在以下部分中進行說明。

## 資料庫清理工作流執行的任務 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流調度程式中定義的日期和時間(請參 [閱調度程式](#the-scheduler))，工作流引擎將啟動資料庫清理進程。 資料庫清理將連接到資料庫，並按如下所示的順序執行任務。

>[!CAUTION]
>
>如果其中一個任務失敗，將不執行以下任務。\
>具有 **LIMIT** 屬性的SQL查詢將重複執行，直到處理所有資訊為止。

>[!NOTE]
>
>以下介紹資料庫清理工作流執行的任務的部分保留給資料庫管理員或熟悉SQL語言的用戶。

### 要刪除清理的清單 {#lists-to-delete-cleanup}

工作流執行的第一個任 **[!UICONTROL Database cleanup]** 務將刪除所有具有deleteStatus ! **的組=** NmsGroup的0屬性 ****。 也會刪除連結到這些組且存在於其他表中的記錄。

1. 要刪除的清單將使用以下SQL查詢進行恢復：

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每個清單都有多個指向其他表的連結。 所有這些連結都會使用下列查詢大量刪除：

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   其 **中$(relatedTable)** 是與 **NmsGroup相關的表** , **** $(l)是清單標識符。

1. 當清單為「清單」類型清單時，將使用以下查詢刪除關聯表：

   ```
   DROP TABLE grp$(l)
   ```

1. 操作 **恢復的每個Select** 類型清單都將使用以下查詢刪除：

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   其中 **$(l)** 是清單識別碼

### 清除要刪除或回收的交貨 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任務將清除要刪除或回收的所有交貨。

1. 工作 **[!UICONTROL Database cleanup]** 流選擇所有 **deleteStatus欄位具有值或刪除日期早於部署嚮導(****[!UICONTROL Yes]****[!UICONTROL Recycled]****[!UICONTROL Deleted deliveries]****** NmsCleanup_RecycleandDeliveryPurgeDelayDelayDelayDelayDelay)欄位中定義的期間的交貨。 For more on this, refer to [Deployment wizard](#deployment-wizard). 此期間會與目前伺服器日期相關計算。
1. 對於每個中間採購伺服器，任務將選擇要刪除的交貨清單。
1. 工作流 **[!UICONTROL Database cleanup]** 程會刪除傳送記錄檔、附件、鏡像頁面資訊和所有其他相關資料。
1. 在為了永久而刪除傳送之前，工作流會清除下清單格中的連結資訊：

   * 在傳送排除表(**NmsDlvExclusion**)中，使用下列查詢：

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      其中 **$(l)** 是傳送的識別碼。

   * 在抵用券表(**NmsCouponValue**)中，使用下列查詢（含大量刪除）:

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      其中 **$(l)** 是傳送的識別碼。

   * 在傳送日誌表(**NmsBroadlogXxx**)中，以10,000條記錄的批次執行大量刪除。
   * 在選件命題表(**NmsPostitionXxx**)中，以10,000條記錄批次執行批量刪除。
   * 在跟蹤日誌表(**NmsTrackinglogXxx**)中，以5,000條記錄的批次執行大量刪除。
   * 在傳送片段表(**NmsDeliveryPart**)中，以5,000條記錄的批次執行大量刪除。 此表包含要傳送之其餘訊息的個人化資訊。
   * 在鏡像頁資料片段表(**NmsMirrorPageInfo**)中，以5,000條記錄的批次執行大量刪除。 此表包含有關用於生成鏡像頁的所有消息的個性化資訊。
   * 在鏡像頁搜索表(**NmsMirrorPageSearch**)中，以5,000條記錄的批次執行大量刪除。 此表是搜索索引，它提供對儲存在 **NmsMirrorPageInfo表中的個人化資訊的訪** 問。
   * 在批處理日誌表(**XtkJobLog**)中，以5,000條記錄的批次執行成批刪除。 此表包含要刪除的交貨日誌。
   * 在傳送URL追蹤表(**NmsTrackingUrl**)中，會使用下列查詢：

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      其中 **$(l)** 是傳送的識別碼。

      此表格包含要刪除的傳送中找到的URL，以啟用其追蹤。

1. 從傳送表中刪除傳送(**NmsDelivery**):

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   其中 **$(l)** 是傳送的識別碼。

#### 使用中部來源補充的交貨 {#deliveries-using-mid-sourcing}

工 **[!UICONTROL Database cleanup]** 作流程也會刪除中間採購伺服器上的傳送。

1. 為此，工作流程會檢查每個傳送是否為非作用中（根據其狀態）。 如果傳送處於活動狀態，則會在刪除之前停止傳送。 通過執行以下查詢來執行檢查：

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   其中 **$(l)** 是傳送的識別碼。

1. 如果狀態的值是 **[!UICONTROL Start pending]** 、 **[!UICONTROL In progress]** 、、 **[!UICONTROL Recovery pending]** 、、、 **[!UICONTROL Recovery in progress]** 、 **[!UICONTROL Pause requested]** 、或 **[!UICONTROL Pause in progress]****[!UICONTROL Paused]** （值51、55、61、62、71、72、75），則會停止傳送，任務會清除連結的資訊。

### 清除過期的遞送 {#cleanup-of-expired-deliveries}

此任務將停止有效期已過期的交貨。

1. 工作 **[!UICONTROL Database cleanup]** 流程會建立已到期的傳送清單。 此清單包含狀態為非的所有過期傳送， **[!UICONTROL Finished]** 以及最近停止的傳送，超過10,000則未處理訊息。 使用下列查詢：

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   如 **果傳送模式** 1與 **[!UICONTROL Mass delivery]** 模式相符 **，則狀態51** 與狀態相符，狀態 **[!UICONTROL Start pending]********[!UICONTROL Stopped]** 5與狀態8相符，狀態8的最高數量的傳送日誌在傳送伺服器上大量更新為10,000。

1. 然後，工作流將包括使用中間來源補充的最近過期交貨的清單。 不包含尚未透過中部來源補充伺服器復原傳送記錄的傳送。

   使用下列查詢：

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 以下查詢用於檢測外部帳戶是否仍處於活動狀態，以便按日期篩選交貨：

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在過期傳送的清單中，狀態為、切換至 **[!UICONTROL Pending]** 、且此清單中 **[!UICONTROL Delivery cancelled]** 所有傳送都切換至的傳送記錄 **[!UICONTROL Finished]** 。

   使用下列查詢：

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   其中 **$(curdate)** 是資料庫伺服器的當前日期， **$(bl)** 是交付日誌的標識符， **$(dl)是交付日誌的標識符，** $（dl是交付狀態）與交付狀態6相符， ******[!UICONTROL Pending]********[!UICONTROL Delivery cancelled]** 700000000000000000000000000000。

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   其 **中傳送狀態** 95與狀態 **[!UICONTROL Finished]** 相符，而 **$(dl)** 是傳送的識別碼。

1. 會刪除過&#x200B;**時傳送的所有片段(deliveryParts**)，並刪除進行中通知傳送的所有過時片段。 成批刪除用於這兩個任務。

   使用下列查詢：

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   其中 **傳送狀態** 95與狀態相符， **[!UICONTROL Finished]** 傳送狀態85 **,** 且 **[!UICONTROL Stopped]****** $(curDate)與目前伺服器日期相符。

### 清除鏡像頁 {#cleanup-of-mirror-pages}

此工作會刪除傳送所使用的網頁資源（鏡像頁面）。

1. 首先，系統將使用以下查詢恢復要清除的交貨清單：

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   其中 **$(curDate)** 是目前的伺服器日期。

1. 然後， **如有必要，使用先前恢復的傳送的標識符來清除NmsMirrorPageInfo** 表。 大量刪除用於生成以下查詢：

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   其中 **$(dl)** 是傳送的識別碼。

1. 然後，會將項目新增至傳送記錄。
1. 然後會識別已清除的傳送，以避免日後必須重新處理。 會執行下列查詢：

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   其中 **$(strIn)** 是傳送識別碼的清單。

### 清理工作表 {#cleanup-of-work-tables}

此任務從資料庫中刪除，即所有與狀態為、或的傳送匹配 **[!UICONTROL Being edited]** 的工 **[!UICONTROL Stopped]** 作表 **[!UICONTROL Deleted]** 。

1. 名稱以 **wkDlv_** 開頭的表清單首先使用以下查詢(postgresql)恢復：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後會排除進行中的工作流程所使用的表格。 為此，系統會使用以下查詢恢復進行中的交貨清單：

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   其中0是與傳送狀態相符 **[!UICONTROL Being edited]** 的值，85與狀態 **[!UICONTROL Stopped]** 相符，100與狀態相 **[!UICONTROL Deleted]** 符。

1. 不再使用的表將使用以下查詢刪除：

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### 清除匯入產生的廢品 {#cleanup-of-rejects-generated-by-imports-}

此步驟可讓您刪除匯入期間未處理所有資料的記錄。

1. 對 **XtkReject表執行成批刪除** ，查詢如下：

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   其中 **$(curDate)** 是當前伺服器日期，從中減去為 **NmsCleanup_RejectsPurgeDelay** 選項(請參閱 [Deployment wizard](#deployment-wizard)**** )定義的期間，而$(l)是要刪除的最大記錄數。

1. 然後，所有孤立拒絕都將使用以下查詢刪除：

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流程例項 {#cleanup-of-workflow-instances}

此任務使用其標識符(**lWorkflowId**)和歷史記錄(**lHistory**)清除每個工作流實例。 它通過再次運行工作台清理任務刪除非活動表。

>[!NOTE]
>
>歷史記錄的清除頻率是在「歷史記錄中的天數」( **History in days** )欄位中為每個工作流指定的（預設值為30天）。 您可以在工作流屬性的「執 **行** 」頁籤中找到此欄位。 如需詳細資訊，請參閱[本小節](../../workflow/using/workflow-properties.md#execution)。

1. 要恢復要刪除的工作流清單，請使用以下查詢：

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查詢將生成工作流清單，該工作流清單將使用下列查詢來刪除所有連結的日誌、完成的任務和完成的事件：

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   其中 **$(lworkflow)** 是工作流程的識別碼， **$(lhistory)** 是歷史記錄的識別碼。

1. 所有未使用的表都將被刪除。 為此，所有表格都會因為使用下列查詢(postgresql)的 **wkf%** 類型遮色片而收集：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後，將排除待審工作流實例使用的所有表。 使用以下查詢可恢復活動工作流清單：

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然後，將恢復每個工作流標識符，以查找正在處理的工作流所使用的表的名稱。 這些名稱將從先前恢復的表清單中排除。
1. 「增量查詢」類型活動歷史記錄表使用以下查詢被排除：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   其 **中$(strcondition)** 是符合wkfhisto%遮色片 **的表格清單** 。

1. 其餘的表將使用以下查詢刪除：

   ```
   DROP TABLE wkf15487_12;
   ```

### 清除工作流程登入 {#cleanup-of-workflow-logins}

此任務使用以下查詢刪除工作流登錄：

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立工作表 {#cleanup-of-orphan-work-tables}

此任務將刪除連結到組的孤立工作表。 Nms **Group** 表儲存要清除的組（類型不同於0）。 表名的前置詞為 **grp**。 要標識要清除的組，請使用以下查詢：

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清除訪客 {#cleanup-of-visitors}

此任務使用成批刪除從訪客表中刪除過時記錄。 過時記錄是指上次修改時間早於部署嚮導中定義的保存期的記錄(請參 [閱部署嚮導](#deployment-wizard))。 使用下列查詢：

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < $(tsDate) LIMIT 5000)
```

其 **中$(tsDate)** 是目前的伺服器日期，我們會從中減去為 **NmsCleanup_VisitorPurgeDelay選項定義的期間** 。

### NPAI的清理 {#cleanup-of-npai}

此任務允許您從 **NmsAddress表中刪除與有效地址匹配的記** 錄。 以下查詢用於執行成批刪除：

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

其中 ******[!UICONTROL Valid]** status 2與 **status匹配，** $(tsDate1) **是當前伺服器日期，而** $(tsDate2) **** 與NmsCleanup_LastCleanup選項匹配。

### 清除訂閱 {#cleanup-of-subscriptions-}

此任務使用成批刪除，從 **NmsSubscription表清除用戶刪除的所有訂閱** 。 使用下列查詢：

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清除追蹤記錄 {#cleanup-of-tracking-logs}

此任務會從追蹤和網路追蹤記錄表中刪除過時的記錄。 過時記錄是指早於部署嚮導中定義的保存期的記錄(請參 [閱部署嚮導](#deployment-wizard))。

1. 首先，使用下列查詢來恢復跟蹤日誌表的清單：

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批刪除用於清除以前恢復的表清單中的所有表。 使用下列查詢：

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   其 **中$(tsDate)** 是當前伺服器日期，我們從中減去為 **NmsCleanup_TrackingLogPurgeDelay選項定義的期間** 。

1. 追蹤統計資料表格會使用大量刪除來清除。 使用下列查詢：

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   其 **中$(tsDate)** 是當前伺服器日期，我們從中減去為 **NmsCleanup_TrackingStatPurgeDelay選項定義的期間** 。

### 清除傳送記錄檔 {#cleanup-of-delivery-logs}

此任務可讓您清除儲存在各種表格中的傳送記錄檔。

1. 為此，將使用以下查詢恢復交付日誌方案清單：

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中間源時， **NmsBroadLogMid** 表不在傳送映射中引用。 將 **nms:broadLogMid** schema添加到由前一個查詢恢復的清單中。
1. 然後， **資料庫清理** 工作流將清除以前恢復的表中的過時資料。 使用下列查詢：

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   其 **中$(Name)** ($(Name) **)是方案清單中每個表的名稱，** $(option) **($(option)是為** NmsBroadLogPurgeDelay [選項(請參閱](#deployment-wizard)Deployment WizardCleaming)定義的日期。

1. 最後，工作流檢查 **NmsProviderMsgId表是否存在** 。 如果是，則會使用下列查詢刪除所有過時的資料：

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   其中 **$（選項）** ，與為 **NmsCleanup_BroadLogPurgeDelay選項定義的日期相符** (請參閱部 [署嚮導](#deployment-wizard))。

### 清除NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任務會清除 **NmsEmailErrorStat** 表。 主程式(coalesceErrors ****)定義兩個日期：

* **開始日期**:與 **NmsLastErrorStatCoalesce選項匹配的下一個進程的日期** ，或表中的最新日期。
* **結束日期**:目前伺服器日期。

如果開始日期大於或等於結束日期，則不會進行任何程式。 在這種情況下，會出 **現coalesceUpToDate** 消息。

如果開始日期早於結束日期，則會清 **除NmsEmailErrorStat** 表。

NmsEmailErrorStat **** 表中，在開始日期和結束日期之間的錯誤總數使用以下查詢來恢復：

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

其 **中$end** 和 **** $start是先前定義的開始和結束日期。

如果總數大於0:

1. 執行下列查詢時，僅會將錯誤保持在特定臨界值以外（等於20）:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. 此時將顯示 **coalescingErrors** （合併錯誤）消息。
1. 會建立新連線，以刪除在開始和結束日期之間發生的所有錯誤。 使用下列查詢：

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. 每個錯誤都使用以 **下查詢保存在NmsEmailErrorStat** 表中：

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   其中，每個變數都符合先前查詢所復原的值。

1. 開 **始變數** 會更新為先前程式的值，以完成循環。

循環和任務停止。

cleanups在 **NmsEmailError** 和 **cleanupNmsMxDomain表上執行** 。

### 清除NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用下列查詢：

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢從 **NmsEmailError表中刪除** NmsEmailErrorStat **中沒有連結記錄的** 所有行。

### 清除NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用下列查詢：

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢從 **NmsMxDomain表中刪除** NmsEmailErrorStat **表中沒有連結記錄的所有** 行。

### 清理主張 {#cleanup-of-propositions}

如果安 **裝了Interaction** 模組，則執行此任務以清除 **NmsCompositionXxx** 表。

使用以下查詢，可恢復命題表清單並對每個命題表執行批量刪除：

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

其中 **$（選項）** 是為 **NmsCleanup_CompostitionPurgeDelay選項定義的日期(請參** 閱部署嚮導 [](#deployment-wizard))。

### 清理模擬表 {#cleanup-of-simulation-tables}

此任務會清除孤立的模擬表（不再連結至選件模擬或傳送模擬）。

1. 若要恢復需要清除的模擬清單，請使用下列查詢：

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要刪除的表名由 **wkSimu_** prefix和模擬的標識符組成(例如： **wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### 統計資料更新和儲存空間最佳化 {#statistics-update}

XtkCleanup_NoStats **** 選項允許您控制清除工作流的儲存優化步驟的行為。

如果 **XtkCleanup_NoStats** 選項不存在或其值為0，則將在PostgreSQL上以冗餘模式（真空VERBOSE ANALYZE）執行儲存優化，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 DAVMANUM將輸出以下格式的行： `INFO: vacuuming "public.nmsactivecontact"` ANALYZE將輸出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`。

如果選項的值為1，則不會在任何資料庫上執行統計資訊更新。 工作流日誌中將顯示以下日誌行： `Option 'XtkCleanup_NoStats' is set to '1'`。

如果選項的值為2，則它將在PostgreSQL上以詳細模式(ANALYZE VERBOSE)執行儲存分析，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 ANALYZE將輸出以下格式的行： `INFO: analyzing "public.nmsactivecontact"`。

### 訂閱清除(NMAC) {#subscription-cleanup--nmac-}

此任務會刪除與已刪除服務或行動應用程式相關的訂閱。

1. 要恢復廣播方案清單，請使用以下查詢：

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
   ```

1. 然後，任務將恢復連結到appSubscription連結的表 **的名稱** ，並刪除這些表。

### 清理會話資訊 {#cleansing-session-information}

此任務會清除 **sessionInfo** 表中的資訊，並使用以下查詢：

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清除過期事件 {#cleansing-expired-events}

此任務將清除在執行實例上接收和儲存的事件以及在控制實例上存檔的事件。

### 清潔反應 {#cleansing-reactions}

該任務清除了已刪除假 **設的反應(表NmsRemaMatchRcp**)。

### 清理審計線索 {#cleanup-of-audit-trail}

使用下列查詢：

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

其中 **$(tsDate)** ，是為 **** XtkCleanup_AuditTrailPurgeDelay選項定義的期間所在的當前伺服器日期。
