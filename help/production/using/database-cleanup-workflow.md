---
product: campaign
title: 資料庫清除工作流程
description: 瞭解如何自動清除過時的資料
feature: Monitoring, Workflows
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 6c85ca9d50dd970915b7c46939f88f4d7fdf07d8
workflow-type: tm+mt
source-wordcount: '2827'
ht-degree: 0%

---

# 資料庫清除工作流程{#database-cleanup-workflow}



## 簡介 {#introduction}

可透過&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點存取的&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程可讓您刪除過時的資料，以避免資料庫呈指數增長。 工作流程會自動觸發，使用者無需另行干預。

![清理](assets/ncs_cleanup_workflow.png)

## 設定 {#configuration}

資料庫清理是在兩個層級上設定：在工作流程排程器和部署精靈中。

### 工作流程排程器 {#the-scheduler}

>[!NOTE]
>
>如需排程器的詳細資訊，請參閱[本區段](../../workflow/using/scheduler.md)。

根據預設，**[!UICONTROL Database cleanup]**&#x200B;工作流程設定為每天凌晨4:00開始。 排程器可讓您變更工作流程觸發頻率。 可使用下列頻率：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![排程器](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>為了讓&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程在排程器中所定義的日期和時間啟動，工作流程引擎(wfserver)必須啟動。

### 部署精靈 {#deployment-assistant}

透過&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;功能表存取的&#x200B;**[!UICONTROL deployment wizard]**&#x200B;可讓您設定儲存資料的時間長度。 值以天為單位表示。 如果未變更這些值，工作流程將使用預設值。

![](assets/ncs_cleanup_deployment-wizard.png)

**[!UICONTROL Purge of data]**&#x200B;視窗的欄位與下列選項一致。 **[!UICONTROL Database cleanup]**&#x200B;工作流程所執行的一些工作會使用這些專案：

* 整合的追蹤： **NmsCleanup_TrackingStatPurgeDelay** （請參閱[追蹤記錄的清除](#cleanup-of-tracking-logs)）
* 傳遞記錄： **NmsCleanup_BroadLogPurgeDelay** （請參閱[傳遞記錄的清理](#cleanup-of-delivery-logs)）
* 追蹤記錄： **NmsCleanup_TrackingLogPurgeDelay** （請參閱[追蹤記錄的清除](#cleanup-of-tracking-logs)）
* 已刪除的傳遞： **NmsCleanup_RecycledDeliveryPurgeDelay** （請參閱[清除要刪除或回收的傳遞](#cleanup-of-deliveries-to-be-deleted-or-recycled)）
* 匯入拒絕： **NmsCleanup_RejectsPurgeDelay** （請參閱清除匯入產生的拒絕](#cleanup-of-rejects-generated-by-imports-)）[
* 訪客設定檔： **NmsCleanup_VisitorPurgeDelay** （請參閱[訪客清理](#cleanup-of-visitors)）
* 優惠方案主張： **NmsCleanup_PropositionPurgeDelay** （請參閱[主張的清除](#cleanup-of-propositions)）

  >[!NOTE]
  >
  >**[!UICONTROL Offer propositions]**&#x200B;欄位只有在已安裝&#x200B;**互動**&#x200B;模組時才能使用。

* 事件： **NmsCleanup_EventPurgeDelay** （請參閱[清除過期的事件](#cleansing-expired-events)）
* 封存的事件： **NmsCleanup_EventHistoPurgeDelay** （請參閱[清除過期的事件](#cleansing-expired-events)）

  >[!NOTE]
  >
  >**[!UICONTROL Events]**&#x200B;和&#x200B;**[!UICONTROL Archived events]**&#x200B;欄位只有在已安裝&#x200B;**訊息中心**&#x200B;模組時才可用。

* 稽核軌跡： **XtkCleanup_AuditTrailPurgeDelay** （請參閱[稽核軌跡的清除](#cleanup-of-audit-trail)）

下節將說明&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程執行的所有工作。

## 由資料庫清理工作流程執行的任務 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流程排程器（請參閱[排程器](#the-scheduler)）中定義的日期和時間，工作流程引擎會啟動資料庫清理程式。 「資料庫清理」會連線到資料庫，並以下列順序執行工作。

>[!IMPORTANT]
>
>如果其中一個任務失敗，則不會執行下一個任務。
>
>具有&#x200B;**LIMIT**&#x200B;屬性的SQL查詢會重複執行，直到處理完所有資訊為止。


### 要刪除清除的清單 {#lists-to-delete-cleanup}

**[!UICONTROL Database cleanup]**&#x200B;工作流程執行的第一個任務會刪除所有具有&#x200B;**deleteStatus ！=來自** NmsGroup **的0**&#x200B;屬性。 連結至這些群組以及存在於其他表格中的記錄也會被刪除。

1. 使用下列SQL查詢復原要刪除的清單：

   ```sql
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每個清單都有數個連結至其他表格。 所有這些連結都會使用下列查詢大量刪除：

   ```sql
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   其中`$(relatedTable)`是與&#x200B;**NmsGroup**&#x200B;相關的資料表，`$(l)`是清單識別碼。

1. 當清單是「清單」型別清單時，會使用以下查詢刪除關聯的表格：

   ```sql
   DROP TABLE grp$(l)
   ```

1. 使用下列查詢刪除作業復原的每個&#x200B;**Select**&#x200B;型別清單：

   ```sql
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   其中`$(l)`是清單識別碼

### 清理要刪除或回收的傳遞 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任務會清除所有要刪除或回收的傳遞。

1. **[!UICONTROL Database cleanup]**&#x200B;工作流程會選取&#x200B;**deleteStatus**&#x200B;欄位值為&#x200B;**[!UICONTROL Yes]**&#x200B;或&#x200B;**[!UICONTROL Recycled]**&#x200B;且刪除日期早於部署精靈之&#x200B;**[!UICONTROL Deleted deliveries]** (**NmsCleanup_RecycledDeliveryPurgeDelay**)欄位中定義之期間的所有傳遞。 如需詳細資訊，請參閱[部署精靈](#deployment-assistant)。 此期間是根據目前的伺服器日期計算。
1. 對於每個中間來源伺服器，任務會選取要刪除的傳遞清單。
1. **[!UICONTROL Database cleanup]**&#x200B;工作流程會刪除傳遞記錄、附件、映象頁面資訊和所有其他相關資料。
1. 永久刪除傳送之前，工作流程會永久刪除下清單格中的連結資訊：

   * 在傳遞排除表格(**NmsDlvExclusion**)中，使用了下列查詢：

     ```sql
     DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
     ```

     其中&#x200B;**$(l)**&#x200B;是傳遞的識別碼。

   * 在抵用券資料表(**NmsCouponValue**)中，使用了下列查詢（含大量刪除）：

     ```sql
     DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
     ```

     其中`$(l)`是傳遞的識別碼。

   * 在傳遞記錄表格(**NmsBroadlogXxx**)中，大量刪除是以20,000筆記錄的批次執行。
   * 在優惠方案主張資料表(**NmsPropositionXxx**)中，大量刪除會以20,000筆記錄的批次執行。
   * 在追蹤記錄表(**NmsTrackinglogXxx**)中，大量刪除是以20,000筆記錄的批次執行。
   * 在傳遞片段資料表(**NmsDeliveryPart**)中，大量刪除是以500,000筆記錄的批次執行。 此表格包含其餘要傳送之訊息的個人化資訊。
   * 在映象頁面資料片段資料表(**NmsMirrorPageInfo**)中，針對已到期的傳遞部分以及已完成或已取消的傳遞部分，以20,000筆記錄的批次執行大量刪除。 此表格包含用於產生映象頁面之所有訊息的個人化資訊。
   * 在映象頁面搜尋表格(**NmsMirrorPageSearch**)中，大量刪除是以20,000筆記錄的批次執行。 此資料表是搜尋索引，可讓您存取儲存在&#x200B;**NmsMirrorPageInfo**&#x200B;資料表中的個人化資訊。
   * 在批次處理記錄表(**XtkJobLog**)中，大量刪除是以20,000筆記錄的批次執行。 此表格包含要刪除的傳遞記錄。
   * 在傳遞URL追蹤資料表(**NmsTrackingUrl**)中，使用了下列查詢：

     ```sql
     DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
     ```

     其中`$(l)`是傳遞的識別碼。

     此表格包含在要刪除以啟用其追蹤的傳遞中找到的URL。

1. 傳遞已從傳遞資料表(**NmsDelivery**)中刪除：

   ```sql
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   其中`$(l)`是傳遞的識別碼。

#### 使用中間來源的傳遞 {#deliveries-using-mid-sourcing}

**[!UICONTROL Database cleanup]**&#x200B;工作流程也會刪除中間來源伺服器上的傳遞。

1. 為此，工作流程會檢查每個傳送是否非作用中（根據其狀態）。 如果傳送處於作用中狀態，則會在刪除之前停止。 檢查會透過執行以下查詢來執行：

   ```sql
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   其中&#x200B;**$(l)**&#x200B;是傳遞的識別碼。

1. 如果狀態的值為&#x200B;**[!UICONTROL Start pending]**、**[!UICONTROL In progress]**、**[!UICONTROL Recovery pending]**、**[!UICONTROL Recovery in progress]**、**[!UICONTROL Pause requested]**、**[!UICONTROL Pause in progress]**&#x200B;或&#x200B;**[!UICONTROL Paused]** （值51、55、61、62、71、72、75），則傳遞會停止且工作會清除連結的資訊。

### 清除過期的傳遞 {#cleanup-of-expired-deliveries}

此任務會停止其有效期已過期的傳遞。

1. **[!UICONTROL Database cleanup]**&#x200B;工作流程會建立已過期的傳遞清單。 此清單包含狀態為&#x200B;**[!UICONTROL Finished]**&#x200B;以外的所有過期傳遞，以及最近停止的傳遞，其中包含超過10,000則未處理的訊息。 使用下列查詢：

   ```sql
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   其中`delivery mode 1`符合&#x200B;**[!UICONTROL Mass delivery]**&#x200B;模式，`state 51`符合&#x200B;**[!UICONTROL Start pending]**&#x200B;狀態，`state 85`符合&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態，而傳遞伺服器上大量更新的傳遞記錄最高數目等於10,000。

1. 然後，工作流程會包含使用中間來源的最近過期傳遞清單。 會排除尚未透過中間來源伺服器復原傳遞記錄的傳遞。

   使用下列查詢：

   ```sql
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 下列查詢可用來偵測外部帳戶是否仍在作用中，以依日期篩選傳遞：

   ```sql
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在過期的傳遞清單中，狀態為&#x200B;**[!UICONTROL Pending]**&#x200B;的傳遞記錄會切換至&#x200B;**[!UICONTROL Delivery cancelled]**，而此清單中的所有傳遞會切換至&#x200B;**[!UICONTROL Finished]**。

   使用下列查詢：

   ```sql
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   其中`$(curdate)`是資料庫伺服器的目前日期，`$(bl)`是傳遞記錄訊息的識別碼，`$(dl)`是傳遞識別碼，`delivery status 6`符合&#x200B;**[!UICONTROL Pending]**&#x200B;狀態，`delivery status 7`符合&#x200B;**[!UICONTROL Delivery cancelled]**&#x200B;狀態。

   ```sql
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   其中`delivery state 95`符合&#x200B;**[!UICONTROL Finished]**&#x200B;狀態，而`$(dl)`是傳遞的識別碼。

1. 已刪除過時傳遞的所有片段(**deliveryParts**)，並刪除進行中通知傳遞的所有過時片段。 這兩個任務都會使用大量刪除。

   使用下列查詢：

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```sql
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   其中`delivery state 95`符合&#x200B;**[!UICONTROL Finished]**&#x200B;狀態，`delivery state 85`符合&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態，且`$(curDate)`為目前的伺服器日期。

### 清理映象頁面 {#cleanup-of-mirror-pages}

此任務會刪除傳遞所使用的網站資源（映象頁面）。

1. 首先，使用以下查詢來復原要清除的傳遞清單：

   ```sql
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)
   ```

   其中`$(curDate)`為目前的伺服器日期。

1. 然後會清除&#x200B;**NmsMirrorPageInfo**&#x200B;表格（如有必要），使用先前復原的傳遞的識別碼。 大量刪除用於產生下列查詢：

   ```sql
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   ```sql
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000
   ```

   其中`$(dl)`是傳遞的識別碼。

1. 然後，專案會新增至傳遞記錄。
1. 接著會識別已清除的傳送，以避免稍後必須重新處理。 會執行以下查詢：

   ```sql
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   其中`$(strIn)`是傳遞識別碼的清單。

### 清理工作表 {#cleanup-of-work-tables}

此任務會從資料庫中刪除符合狀態為&#x200B;**[!UICONTROL Being edited]**、**[!UICONTROL Stopped]**&#x200B;或&#x200B;**[!UICONTROL Deleted]**&#x200B;之傳遞的所有工作表。

1. 名稱以&#x200B;**wkDlv_**&#x200B;開頭的資料表清單，會先透過下列查詢(postgresql)復原：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後會排除進行中工作流程使用的表格。 若要這麼做，請使用下列查詢復原進行中的傳遞清單：

   ```sql
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   其中`0`是符合&#x200B;**[!UICONTROL Being edited]**&#x200B;傳遞狀態的值，`85`符合&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態，`100`符合&#x200B;**[!UICONTROL Deleted]**&#x200B;狀態。

1. 不再使用的表格將透過下列查詢刪除：

   ```sql
   DROP TABLE wkDlv_15487_1;
   ```

### 清除匯入產生的拒絕 {#cleanup-of-rejects-generated-by-imports-}

此步驟可讓您刪除匯入期間未處理所有資料的記錄。

1. 使用下列查詢對&#x200B;**XtkReject**&#x200B;資料表執行大量刪除：

   ```sql
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l)
   ```

   其中`$(curDate)`是目前的伺服器日期，我們從其中減去為&#x200B;**NmsCleanup_RejectsPurgeDelay**&#x200B;選項（請參閱[部署精靈](#deployment-assistant)）定義的期間，而`$(l)`是大量刪除的記錄數上限。

1. 然後使用以下查詢刪除所有孤立拒絕：

   ```sql
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流程執行個體 {#cleanup-of-workflow-instances}

此工作會使用其識別碼(**lWorkflowId**)和歷程記錄(**lHistory**)清除每個工作流程執行個體。 它會透過再次執行工作表格清理任務來刪除非作用中的表格。 此清理也會刪除已刪除工作流程的所有孤立工作台（wkf%和wkfhisto%）。

>[!NOTE]
>
>已針對&#x200B;**以天為單位的歷程記錄**&#x200B;欄位中的每個工作流程指定歷程記錄的清除頻率（預設值為30天）。 此欄位可在工作流程屬性的&#x200B;**執行**&#x200B;索引標籤中找到。 如需詳細資訊，請參閱[本章節](../../workflow/using/workflow-properties.md#execution)。

1. 若要復原要刪除的工作流程清單，請使用以下查詢：

   ```sql
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查詢會產生工作流程清單，用於透過下列查詢刪除所有連結的記錄、完成的任務和完成的事件：

   ```sql
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```sql
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```sql
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   其中`$(lworkflow)`是工作流程的識別碼，`$(lhistory)`是歷程記錄的識別碼。

1. 刪除所有未使用的表格。 為此，使用下列查詢(postgresql)，使用&#x200B;**wkf%**&#x200B;型別遮罩來收集所有資料表：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後會排除擱置工作流程執行個體使用的所有表格。 使用下列查詢可復原使用中工作流程的清單：

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 接著，系統會復原每個工作流程識別碼，以尋找進行中工作流程所使用的表格名稱。 這些名稱會從先前復原的資料表清單中排除。
1. 使用下列查詢排除「增量查詢」型別活動歷史記錄表格：

   ```sql
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```sql
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   其中`$(strcondition)`是符合&#x200B;**wkfhisto%**&#x200B;遮罩的資料表清單。

1. 剩餘的表格會使用下列查詢刪除：

   ```sql
   DROP TABLE wkf15487_12;
   ```

### 清理工作流程登入 {#cleanup-of-workflow-logins}

此任務會使用以下查詢刪除工作流程登入：

```sql
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立的工作表 {#cleanup-of-orphan-work-tables}

此任務會刪除連結至群組的孤立工作表。 **NmsGroup**&#x200B;資料表儲存要清除的群組（使用非0的型別）。 資料表名稱的前置詞是&#x200B;**grp**。 若要識別要清除的群組，請使用下列查詢：

```sql
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 清理訪客 {#cleanup-of-visitors}

此任務會使用大量刪除，從訪客表格中刪除過時記錄。 過時記錄是指最後一次修改早於部署精靈中定義的儲存期間的記錄（請參閱[部署精靈](#deployment-assistant)）。 使用下列查詢：

```sql
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

其中`$(tsDate)`是目前的伺服器日期，我們從其中減去為&#x200B;**NmsCleanup_VisitorPurgeDelay**&#x200B;選項定義的期間。

### NPAI的清理 {#cleanup-of-npai}

此工作可讓您從&#x200B;**NmsAddress**&#x200B;資料表中刪除符合有效位址的記錄。 下列查詢可用來執行整批刪除：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

其中`status 2`符合&#x200B;**[!UICONTROL Valid]**&#x200B;狀態，`$(tsDate1)`為目前的伺服器日期，`$(tsDate2)`符合&#x200B;**NmsCleanup_LastCleanup**&#x200B;選項。

### 清理訂閱 {#cleanup-of-subscriptions-}

此工作會使用大量刪除，清除使用者從&#x200B;**NmsSubscription**&#x200B;資料表中刪除的所有訂閱。 使用下列查詢：

```sql
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清理追蹤記錄 {#cleanup-of-tracking-logs}

此工作會從追蹤和網站追蹤記錄表中刪除過時的記錄。 過時記錄是指早於部署精靈中定義的儲存期間的記錄（請參閱[部署精靈](#deployment-assistant)）。

1. 首先，使用下列查詢來復原追蹤記錄表清單：

   ```sql
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 整批刪除用於清除先前復原的表格清單中的所有表格。 使用下列查詢：

   ```sql
   DELETE FROM NmsTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM NmsTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   其中`$(tsDate)`是目前的伺服器日期，我們從中減去為&#x200B;**NmsCleanup_TrackingLogPurgeDelay**&#x200B;選項定義的期間。

1. 會使用大量刪除來清除追蹤統計資料表。 使用下列查詢：

   ```sql
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   其中`$(tsDate)`是目前的伺服器日期，我們從中減去為&#x200B;**NmsCleanup_TrackingStatPurgeDelay**&#x200B;選項定義的期間。

### 傳遞記錄的清理 {#cleanup-of-delivery-logs}

此任務可讓您清除儲存在各種表格中的傳送記錄。

1. 為此目的，會使用下列查詢復原傳遞記錄結構描述清單：

   ```sql
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中間來源時，傳遞對應中未參考&#x200B;**NmsBroadLogMid**&#x200B;表格。 **nms：broadLogMid**&#x200B;結構描述已新增到上一個查詢復原的清單中。
1. **資料庫清理**&#x200B;工作流程接著會從先前復原的資料表中清除過時的資料。 使用下列查詢：

   ```sql
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   其中`$(tableName)`是結構描述清單中每個資料表的名稱，`$(option)`是為&#x200B;**NmsCleanup_BroadLogPurgeDelay**&#x200B;選項定義的日期（請參閱[部署精靈](#deployment-assistant)）。

1. 最後，工作流程會檢查&#x200B;**NmsProviderMsgId**&#x200B;資料表是否存在。 若是如此，則會使用下列查詢刪除所有過時資料：

   ```sql
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   其中`$(option)`符合為&#x200B;**NmsCleanup_BroadLogPurgeDelay**&#x200B;選項定義的日期（請參閱[部署精靈](#deployment-assistant)）。

### 清理NmsEmailErrorStat表格 {#cleanup-of-the-nmsemailerrorstat-table-}

此工作會清除&#x200B;**NmsEmailErrorStat**&#x200B;資料表。 主要程式(**coalesceErrors**)定義了兩個日期：

* **開始日期**：下一個處理程式符合&#x200B;**NmsLastErrorStatCoalesce**&#x200B;選項或資料表中最近日期的日期。
* **結束日期**：目前的伺服器日期。

如果開始日期晚於或等於結束日期，則不會進行任何處理。 在這種情況下，**coalesceUpToDate**&#x200B;訊息會出現。

如果開始日期早於結束日期，則會清除&#x200B;**NmsEmailErrorStat**&#x200B;資料表。

使用下列查詢復原&#x200B;**NmsEmailErrorStat**&#x200B;資料表中介於開始和結束日期之間的錯誤總數：

```sql
SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)
```

其中`$end`與`$start`是先前定義的開始與結束日期。

如果總計大於0：

1. 執行以下查詢以僅保留超過特定臨界值（等於20）的錯誤：

   ```sql
   SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20
   ```

1. 顯示&#x200B;**coalescingErrors**&#x200B;訊息。
1. 建立新連線以刪除在開始和結束日期之間發生的所有錯誤。 使用下列查詢：

   ```sql
   DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)
   ```

1. 每個錯誤都使用下列查詢儲存在&#x200B;**NmsEmailErrorStat**&#x200B;資料表中：

   ```sql
   INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))
   ```

   其中每個變數都符合由先前查詢復原的值。

1. **start**&#x200B;變數已更新為前一個處理序的值，以完成回圈。

回圈和任務停止。

在&#x200B;**NmsEmailError**&#x200B;和&#x200B;**cleanupNmsMxDomain**&#x200B;資料表上執行清理。

### 清除NmsEmailError表格 {#cleanup-of-the-nmsemailerror-table-}

使用下列查詢：

```sql
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢會從&#x200B;**NmsEmailError**&#x200B;資料表刪除&#x200B;**NmsEmailErrorStat**&#x200B;中所有沒有連結記錄的行。

### 清除NmsMxDomain表格 {#cleanup-of-the-nmsmxdomain-table-}

使用下列查詢：

```sql
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢會從&#x200B;**NmsMxDomain**&#x200B;資料表刪除&#x200B;**NmsEmailErrorStat**&#x200B;資料表中所有沒有連結記錄的行。

### 主張的清除 {#cleanup-of-propositions}

如果已安裝&#x200B;**Interaction**&#x200B;模組，則會執行此工作以清除&#x200B;**NmsPropositionXxx**&#x200B;表格。

會復原主張表清單，並使用下列查詢對每個表執行大量刪除：

```sql
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

其中`$(option)`是為&#x200B;**NmsCleanup_PropositionPurgeDelay**&#x200B;選項定義的日期（請參閱[部署精靈](#deployment-assistant)）。

### 清理模擬表格 {#cleanup-of-simulation-tables}

此工作會清除孤立的模擬表格（不再連結至優惠方案模擬或傳遞模擬）。

1. 若要復原需要清理的模擬清單，請使用下列查詢：

   ```sql
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要刪除的資料表名稱包含&#x200B;**wkSimu_**&#x200B;首碼，後面接著模擬的識別碼(例如： **wkSimu_456831_aggr**)：

   ```sql
   DROP TABLE wkSimu_456831_aggr
   ```

### 清除稽核軌跡 {#cleanup-of-audit-trail}

使用下列查詢：

```sql
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

其中，**$(tsDate)**&#x200B;是減去&#x200B;**XtkCleanup_AuditTrailPurgeDelay**&#x200B;選項定義的期間之目前伺服器日期。

### 清除Nmsaddress {#cleanup-of-nmsaddress}

使用下列查詢：

```sql
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查詢會刪除與iOS和Android相關的所有專案。

### 統計資料更新和儲存最佳化 {#statistics-update}

**XtkCleanup_NoStats**&#x200B;選項可讓您控制清理工作流程之儲存最佳化步驟的行為。

如果&#x200B;**XtkCleanup_NoStats**&#x200B;選項不存在，或其值為0，則會在PostgreSQL上以詳細模式執行儲存最佳化(VACUUM VERBOSE ANALYZE)，並更新所有其他資料庫的統計資料。 若要確保執行此命令，請檢查PostgreSQL記錄。 VACUUM將輸出下列格式的行： `INFO: vacuuming "public.nmsactivecontact"`，而ANALYZE將輸出下列格式的行： `INFO: analyzing "public.nmsactivecontact"`。

如果選項的值為1，則統計資料更新不會在任何資料庫上執行。 工作流程記錄中將會顯示下列記錄行： `Option 'XtkCleanup_NoStats' is set to '1'`。

如果選項值為2，這會在PostgreSQL上以詳細資訊模式(ANALYZE VERBOSE)執行儲存體分析，並更新所有其他資料庫的統計資料。 若要確保執行此命令，請檢查PostgreSQL記錄。 ANALYZE會以下列格式輸出行： `INFO: analyzing "public.nmsactivecontact"`。

### 訂閱清理(NMAC) {#subscription-cleanup--nmac-}

此工作會刪除與已刪除的服務或行動應用程式相關的任何訂閱。

若要復原broadlog綱要清單，請使用以下查詢：

```sql
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然後，工作會復原連結至&#x200B;**appSubscription**&#x200B;連結的資料表名稱，並刪除這些資料表。

此清理工作流程也會刪除idisabled = 1且自&#x200B;**NmsCleanup_AppSubscriptionRcpPurgeDelay**&#x200B;選項中設定的時間以來尚未更新的所有專案。

### 清除工作階段資訊 {#cleansing-session-information}

此工作會清除&#x200B;**sessionInfo**&#x200B;資料表中的資訊，使用下列查詢：

```sql
DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清除過期的事件 {#cleansing-expired-events}

此工作會清除在執行例項上接收和儲存的事件，以及控制例項上封存的事件。

### 清除回應 {#cleansing-reactions}

此工作會清除其中已刪除假設的回應（資料表&#x200B;**NmsRemaMatchRcp**）。
