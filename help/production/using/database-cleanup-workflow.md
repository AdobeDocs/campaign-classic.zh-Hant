---
product: campaign
title: 資料庫清除工作流程
description: 了解過期資料如何自動清理
audience: production
content-type: reference
topic-tags: data-processing
exl-id: 75d3a0af-9a14-4083-b1da-2c1b22f57cbe
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '2910'
ht-degree: 0%

---

# 資料庫清除工作流程{#database-cleanup-workflow}

![](../../assets/v7-only.svg)

## 簡介 {#introduction}

可透過&#x200B;**[!UICONTROL Administration > Production > Technical workflows]**&#x200B;節點存取的&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程可讓您刪除過時的資料，以避免資料庫呈指數增長。 工作流程會自動觸發，使用者不需干預。

![](assets/ncs_cleanup_workflow.png)

## 設定 {#configuration}

資料庫清理是在兩個級別上配置的：在工作流程排程器和部署精靈中。

### 工作流程排程器 {#the-scheduler}

>[!NOTE]
>
>有關調度程式的詳細資訊，請參閱[此部分](../../workflow/using/scheduler.md)。

預設情況下， **[!UICONTROL Database cleanup]**&#x200B;工作流程設定為每天凌晨4:00開始。 排程器可讓您變更工作流程觸發頻率。 下列頻率可用：

* **[!UICONTROL Several times a day]**
* **[!UICONTROL Daily]**
* **[!UICONTROL Weekly]**
* **[!UICONTROL Once]**

![](assets/ncs_cleanup_scheduler.png)

>[!IMPORTANT]
>
>為了使&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流從調度程式中定義的日期和時間開始，必須啟動工作流引擎(wfserver)。 如果情況並非如此，則直到下次啟動工作流引擎時才會進行資料庫清理。

### 部署嚮導 {#deployment-wizard}

透過&#x200B;**[!UICONTROL Tools > Advanced]**&#x200B;功能表存取的&#x200B;**[!UICONTROL Deployment wizard]**&#x200B;可讓您設定資料的儲存時間。 值以天表示。 如果這些值未更改，工作流程將使用預設值。

![](assets/ncs_cleanup_deployment-wizard.png)

**[!UICONTROL Purge of data]**&#x200B;窗口的欄位與以下選項一致。 以下是由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流程執行的某些任務所使用：

* 整合追蹤：**NmsCleanup_TrackingStatPurgeDelay**（請參閱[追蹤記錄清理](#cleanup-of-tracking-logs)）
* 傳送記錄檔：**NmsCleanup_BroadLogPurgeDelay**（請參閱[清除傳送記錄](#cleanup-of-delivery-logs)）
* 追蹤記錄：**NmsCleanup_TrackingLogPurgeDelay**（請參閱[追蹤記錄清理](#cleanup-of-tracking-logs)）
* 已刪除的傳送：**NmsCleanup_RecylendDeliveryPurgeDelay**（請參閱[要刪除或回收的傳送的清除](#cleanup-of-deliveries-to-be-deleted-or-recycled)）
* 導入拒絕：**NmsCleanup_RejectsPurgeDelay**（請參閱[Cleanup of rejects by imports](#cleanup-of-rejects-generated-by-imports-)）
* 訪客設定檔：**NmsCleanup_VisitorPurgeDelay**（請參閱[訪客清除](#cleanup-of-visitors)）
* 提案：**NmsCleanup_PostitionPurgeDelay**（請參閱[Cleanup of propositions](#cleanup-of-propositions)）

   >[!NOTE]
   >
   >**[!UICONTROL Offer propositions]**&#x200B;欄位僅在安裝&#x200B;**Interaction**&#x200B;模組時可用。

* 事件：**NmsCleanup_EventPurgeDelay**（請參閱[清除過期事件](#cleansing-expired-events)）
* 封存的事件：**NmsCleanup_EventHistoPurgeDelay**（請參閱[清除過期事件](#cleansing-expired-events)）

   >[!NOTE]
   >
   >**[!UICONTROL Events]**&#x200B;和&#x200B;**[!UICONTROL Archived events]**&#x200B;欄位僅在安裝了&#x200B;**Message Center**&#x200B;模組時可用。

* 稽核軌跡：**XtkCleanup_AuditTrailPurgeDelay**（請參閱[清理稽核軌跡](#cleanup-of-audit-trail)）

以下章節將介紹由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流執行的所有任務。

## 由資料庫清理工作流執行的任務 {#tasks-carried-out-by-the-database-cleanup-workflow}

在工作流調度程式中定義的日期和時間（請參閱[調度程式](#the-scheduler)），工作流引擎將啟動資料庫清理進程。 資料庫清理會連接到資料庫，並按如下所示的順序執行任務。

>[!IMPORTANT]
>
>如果其中一項任務失敗，則不會執行下列任務。\
>具有&#x200B;**LIMIT**&#x200B;屬性的SQL查詢將重複執行，直到處理所有資訊為止。

>[!NOTE]
>
>以下說明由資料庫清理工作流執行的任務的部分保留給資料庫管理員或熟悉SQL語言的用戶。

### 要刪除清理的清單 {#lists-to-delete-cleanup}

由&#x200B;**[!UICONTROL Database cleanup]**&#x200B;工作流執行的第一個任務將刪除具有&#x200B;**deleteStatus ！的所有組=** NmsGroup **中的0**&#x200B;屬性。 也會刪除連結到這些組的記錄，以及存在於其他表中的記錄。

1. 要刪除的清單將使用以下SQL查詢進行恢復：

   ```
   SELECT iGroupId, sLabel, iType FROM NmsGroup WHERE iDeleteStatus <> 0 OR tsExpirationDate <= GetDate() 
   ```

1. 每個清單都有多個其他表格的連結。 會使用下列查詢大量刪除這些連結：

   ```
   DELETE FROM $(relatedTable) WHERE iGroupId=$(l) IN (SELECT iGroupId FROM $(relatedTable) WHERE iGroupId=$(l) LIMIT 5000) 
   ```

   其中&#x200B;**$(relatedTable)**&#x200B;是與&#x200B;**NmsGroup**&#x200B;相關的表，而&#x200B;**$(l)**&#x200B;是清單標識符。

1. 當該清單為「清單」類型清單時，將使用以下查詢刪除關聯表：

   ```
   DROP TABLE grp$(l)
   ```

1. 使用以下查詢刪除由操作恢復的每個&#x200B;**選擇**&#x200B;類型清單：

   ```
   DELETE FROM NmsGroup WHERE iGroupId=$(l) 
   ```

   其中&#x200B;**$(l)**&#x200B;是清單標識符

### 清除要刪除或回收的傳遞 {#cleanup-of-deliveries-to-be-deleted-or-recycled}

此任務將清除要刪除或回收的所有傳送。

1. **[!UICONTROL Database cleanup]**&#x200B;工作流選擇&#x200B;**deleteStatus**&#x200B;欄位具有值&#x200B;**[!UICONTROL Yes]**&#x200B;或&#x200B;**[!UICONTROL Recycled]**&#x200B;且其刪除日期早於部署嚮導的&#x200B;**[!UICONTROL Deleted deliveries]**(**NmsCleanup_RecylenedDeliveryPurgeDelay**)欄位中定義的期間的所有傳送。 有關詳細資訊，請參閱[部署嚮導](#deployment-wizard)。 此期間會與目前伺服器日期比較計算。
1. 對於每個中間來源伺服器，任務將選擇要刪除的傳送清單。
1. **[!UICONTROL Database cleanup]**&#x200B;工作流程會刪除傳送記錄檔、附件、鏡像頁面資訊和所有其他相關資料。
1. 在刪除正確的傳送之前，工作流程會從下表清除連結的資訊：

   * 在傳送排除表(**NmsDlvExclusion**)中，使用下列查詢：

      ```
      DELETE FROM NmsDlvExclusion WHERE iDeliveryId=$(l)
      ```

      其中&#x200B;**$(l)**&#x200B;是傳送的識別碼。

   * 在抵用券表格(**NmsCouponValue**)中，使用下列查詢（含大量刪除）:

      ```
      DELETE FROM NmsCouponValue WHERE iMessageId IN (SELECT iMessageId FROM NmsCouponValue WHERE EXISTS (SELECT B.iBroadLogId FROM $(BroadLogTableName) B WHERE B.iDeliveryId = $(l) AND B.iBroadLogId = iMessageId ) LIMIT 5000)
      ```

      其中&#x200B;**$(l)**&#x200B;是傳送的識別碼。

   * 在傳送記錄表(**NmsBroadlogXxx**)中，批量刪除以20,000條記錄的批量執行。
   * 在優惠方案主張表(**NmsPostimationXxx**)中，批量刪除按20,000條記錄的批次執行。
   * 在追蹤記錄表(**NmsTrackinglogXxx**)中，大量刪除是以20,000條記錄的批次執行。
   * 在傳送片段表(**NmsDeliveryPart**)中，成批刪除以500,000條記錄的批次執行。 此表格包含要傳送之其餘訊息的個人化資訊。
   * 在鏡像頁資料片段表(**NmsMirrorPageInfo**)中，批量刪除按20,000條記錄的批次執行，以處理過期的傳送部件和已完成或已取消的傳送部件。 此表包含有關用於生成鏡像頁的所有消息的個人化資訊。
   * 在鏡像頁搜索表(**NmsMirrorPageSearch**)中，批量刪除按20,000條記錄的批次執行。 此表是搜索索引，它提供對儲存在&#x200B;**NmsMirrorPageInfo**&#x200B;表中的個人化資訊的訪問。
   * 在批處理日誌表(**XtkJobLog**)中，成批刪除以20,000條記錄的批次執行。 此表包含要刪除的傳送記錄。
   * 在傳送URL追蹤表格(**NmsTrackingUrl**)中，使用下列查詢：

      ```
      DELETE FROM NmsTrackingUrl WHERE iDeliveryId=$(l)
      ```

      其中&#x200B;**$(l)**&#x200B;是傳送的識別碼。

      此表格包含要刪除的傳送中找到的URL，以啟用其追蹤。

1. 從傳送表(**NmsDelivery**)中刪除傳送：

   ```
   DELETE FROM NmsDelivery WHERE iDeliveryId = $(l)
   ```

   其中&#x200B;**$(l)**&#x200B;是傳送的識別碼。

#### 使用中間來源的傳送 {#deliveries-using-mid-sourcing}

**[!UICONTROL Database cleanup]**&#x200B;工作流程也會刪除中間來源伺服器上的傳送。

1. 為此，工作流程會檢查每個傳送是否為非作用中（根據其狀態）。 如果傳送處於作用中狀態，則會在刪除傳送前停止傳送。 檢查通過執行以下查詢來執行：

   ```
   SELECT iState FROM NmsDelivery WHERE iDeliveryId = $(l) AND iState <> 100;
   ```

   其中&#x200B;**$(l)**&#x200B;是傳送的識別碼。

1. 如果狀態的值為&#x200B;**[!UICONTROL Start pending]** 、 **[!UICONTROL In progress]** 、 **[!UICONTROL Recovery pending]** 、 **[!UICONTROL Recovery in progress]** 、 **[!UICONTROL Pause requested]** 、 **[!UICONTROL Pause in progress]**&#x200B;或&#x200B;**[!UICONTROL Paused]**（值51、55、61、62、71、72、75），則停止傳送並任務清除連結的資訊。

### 清除過期的傳送 {#cleanup-of-expired-deliveries}

此任務將停止有效期已過的傳送。

1. **[!UICONTROL Database cleanup]**&#x200B;工作流程會建立已過期的傳送清單。 此清單包含狀態為&#x200B;**[!UICONTROL Finished]**&#x200B;以外的所有過期傳送，以及最近停止的包含超過10,000個未處理訊息的傳送。 使用下列查詢：

   ```
   SELECT iDeliveryId, iState FROM NmsDelivery WHERE iDeleteStatus=0 AND iIsModel=0 AND iDeliveryMode=1 AND ( (iState >= 51 AND iState < 85 AND tsValidity IS NOT NULL AND tsValidity < $(currentDate) ) OR (iState = 85 AND DateMinusDays(15) < tsLastModified AND iToDeliver - iProcessed >= 10000 ))
   ```

   其中，**傳送模式1**&#x200B;與&#x200B;**[!UICONTROL Mass delivery]**&#x200B;模式匹配，**狀態51**&#x200B;與&#x200B;**[!UICONTROL Start pending]**&#x200B;狀態匹配，**狀態85**&#x200B;與&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態匹配，且傳送伺服器上大量更新的傳送日誌的最大數量等於10,000。

1. 然後，工作流程會包含使用中間來源的最近過期傳送清單。 尚未透過中間來源伺服器復原傳送記錄的傳送則會排除。

   使用下列查詢：

   ```
   SELECT iDeliveryId, tsValidity, iMidRemoteId, mData FROM NmsDelivery WHERE (iDeliveryMode = 4 AND (iState = 85 OR iState = 95) AND tsValidity IS NOT NULL AND (tsValidity < SubDays(GetDate() , 15) OR tsValidity < $(DateOfLastLogPullUp)) AND tsLastModified > SubDays(GetDate() , 15))
   ```

1. 下列查詢可用來偵測外部帳戶是否仍為作用中狀態，以便依日期篩選傳送：

   ```
   SELECT iExtAccountId FROM NmsExtAccount WHERE iActive<>0 AND sName=$(providerName)
   ```

1. 在過期傳送的清單中，狀態為&#x200B;**[!UICONTROL Pending]**&#x200B;的傳送記錄檔會切換至&#x200B;**[!UICONTROL Delivery cancelled]** ，此清單中的所有傳送會切換至&#x200B;**[!UICONTROL Finished]** 。

   使用下列查詢：

   ```
   UPDATE $(BroadLogTableName) SET tsLastModified=$(curdate), iStatus=7, iMsgId=$(bl) WHERE iDeliveryId=$(dl) AND iStatus=6
   ```

   其中&#x200B;**$(curdate)**&#x200B;是資料庫伺服器的當前日期，**$(bl)**&#x200B;是傳遞日誌消息的標識符，**$(dl)**&#x200B;是傳遞標識符，**傳遞狀態6**&#x200B;匹配&#x200B;**[!UICONTROL Pending]**&#x200B;狀態，**傳遞狀態7**&#x200B;匹配&#x200B;**[!UICONTROL Delivery cancelled]**&#x200B;狀態。

   ```
   UPDATE NmsDelivery SET iState = 95, tsLastModified = $(curdate), tsBroadEnd = tsValidity WHERE iDeliveryId = $(dl)
   ```

   其中&#x200B;**傳送狀態95**&#x200B;符合&#x200B;**[!UICONTROL Finished]**&#x200B;狀態，而&#x200B;**$(dl)**&#x200B;是傳送的識別碼。

1. 已淘汰傳送的所有片段(**deliveryParts**)都會遭刪除，且所有正在進行的通知傳送的已淘汰片段都會遭到刪除。 這兩個任務都使用大量刪除。

   使用下列查詢：

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE iDeliveryId IN (SELECT iDeliveryId FROM NmsDelivery WHERE iState=95 OR iState=85) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsDeliveryPart WHERE iDeliveryPartId IN (SELECT iDeliveryPartId FROM NmsDeliveryPart WHERE tsValidity < $(curDate) LIMIT 500000)
   ```

   其中，**傳送狀態95**&#x200B;符合&#x200B;**[!UICONTROL Finished]**&#x200B;狀態，**傳送狀態85**&#x200B;符合&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態，而&#x200B;**$(curDate)**&#x200B;為目前伺服器日期。

### 清除鏡像頁面 {#cleanup-of-mirror-pages}

此任務會刪除傳送使用的Web資源（鏡像頁面）。

1. 首先，系統會使用下列查詢來復原要清除的傳送清單：

   ```
   SELECT iDeliveryId, iNeedMirrorPage FROM NmsDelivery WHERE iWebResPurged = 0 AND tsWebValidity IS NOT NULL AND tsWebValidity < $(curdate)"
   ```

   其中&#x200B;**$(curDate)**&#x200B;是目前的伺服器日期。

1. 然後，如果需要，使用先前恢復的傳送的標識符清除&#x200B;**NmsMirrorPageInfo**&#x200B;表。 成批刪除用於生成以下查詢：

   ```
   DELETE FROM NmsMirrorPageInfo WHERE iMirrorPageInfoId IN (SELECT iMirrorPageInfoId FROM NmsMirrorPageInfo WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   ```
   DELETE FROM NmsMirrorPageSearch WHERE iMessageId IN (SELECT iMessageId FROM NmsMirrorPageSearch WHERE iDeliveryId = $(dl)) LIMIT 5000)
   ```

   其中&#x200B;**$(dl)**&#x200B;是傳遞的標識符。

1. 然後，項目會新增至傳送記錄檔。
1. 之後會識別已清除的傳送，以避免稍後重新處理。 會執行下列查詢：

   ```
   UPDATE NmsDelivery SET iWebResPurged = 1 WHERE iDeliveryId IN ($(strIn))
   ```

   其中&#x200B;**$(strIn)**&#x200B;是傳遞標識符的清單。

### 清除工作表 {#cleanup-of-work-tables}

此任務從資料庫中刪除，即所有與狀態為&#x200B;**[!UICONTROL Being edited]** 、 **[!UICONTROL Stopped]**&#x200B;或&#x200B;**[!UICONTROL Deleted]**&#x200B;的傳送相符的工作表。

1. 名稱以&#x200B;**wkDlv_**&#x200B;開頭的表清單首先通過以下查詢(postgresql)恢復：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkDlv_') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 接著會排除進行中的工作流程所使用的表格。 要執行此操作，系統會使用下列查詢來復原進行中的傳送清單：

   ```
   SELECT iDeliveryId FROM NmsDelivery WHERE iDeliveryId<>0 AND iDeleteStatus=0 AND iState NOT IN (0,85,100);
   ```

   其中0是與&#x200B;**[!UICONTROL Being edited]**&#x200B;傳送狀態相符的值， 85符合&#x200B;**[!UICONTROL Stopped]**&#x200B;狀態， 100符合&#x200B;**[!UICONTROL Deleted]**&#x200B;狀態。

1. 不再使用的表將使用以下查詢刪除：

   ```
   DROP TABLE wkDlv_15487_1;
   ```

### 清除匯入產生的拒絕 {#cleanup-of-rejects-generated-by-imports-}

此步驟可讓您刪除匯入期間未處理所有資料的記錄。

1. 對&#x200B;**XtkReject**&#x200B;表執行成批刪除，其查詢如下：

   ```
   DELETE FROM XtkReject WHERE iRejectId IN (SELECT iRejectId FROM XtkReject WHERE tsLog < $(curDate)) LIMIT $(l))
   ```

   其中&#x200B;**$(curDate)**&#x200B;是當前伺服器日期，從中減去為&#x200B;**NmsCleanup_RejectsPurgeDelay**&#x200B;選項（請參閱[部署嚮導](#deployment-wizard)）定義的期間，而&#x200B;**$(l)**&#x200B;是要大量刪除的最大記錄數。

1. 然後，會使用下列查詢刪除所有孤立拒絕：

   ```
   DELETE FROM XtkReject WHERE iJobId NOT IN (SELECT iJobId FROM XtkJob)
   ```

### 清除工作流程例項 {#cleanup-of-workflow-instances}

此任務使用其標識符(**lWorkflowId**)和歷史記錄(**lHistory**)清除每個工作流實例。 它通過再次運行工作表清理任務刪除非活動表。 清除也會刪除已刪除工作流程的所有孤立工作台（wkf%和wkfhisto%）。

>[!NOTE]
>
>在&#x200B;**History in days**&#x200B;欄位（預設值30天）中為每個工作流指定歷史記錄的清除頻率。 可在工作流屬性的&#x200B;**Execution**&#x200B;頁簽中找到此欄位。 如需詳細資訊，請參閱[本章節](../../workflow/using/workflow-properties.md#execution)。

1. 若要復原要刪除的工作流程清單，會使用下列查詢：

   ```
   SELECT iWorkflowId, iHistory FROM XtkWorkflow WHERE iWorkflowId<>0
   ```

1. 此查詢會使用下列查詢，產生用於刪除所有連結記錄、已完成任務和已完成事件的工作流程清單：

   ```
   DELETE FROM XtkWorkflowLog WHERE iWorkflowId=$(lworkflow) AND tsLog < DateMinusDays($(lhistory))
   ```

   ```
   DELETE FROM XtkWorkflowTask WHERE iWorkflowId=$(lworkflow) AND iStatus<>0 AND tsCompletion < DateMinusDays($(lhistory)) 
   ```

   ```
   DELETE FROM XtkWorkflowEvent WHERE iWorkflowId=$(l) AND iStatus>2 AND tsProcessing < DateMinusDays($(lHistory))
   ```

   其中&#x200B;**$(lworkflow)**&#x200B;是工作流的標識符，而&#x200B;**$(lhistory)**&#x200B;是歷史記錄的標識符。

1. 所有未使用的表都將被刪除。 為此，所有表都由於&#x200B;**wkf%**&#x200B;類型掩碼（使用以下查詢）而收集：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkf%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

1. 然後，將排除掛起工作流實例使用的所有表。 使用下列查詢可恢復活動工作流清單：

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId<>0 AND iState<>20
   ```

1. 然後，恢復每個工作流標識符，以查找正在進行的工作流所使用的表的名稱。 這些名稱將從先前恢復的表清單中排除。
1. 使用以下查詢排除「增量查詢」類型的活動歷史記錄表：

   ```
   SELECT relname FROM pg_class WHERE relname LIKE Lower('wkfhisto%') ESCAPE E'\\' AND relkind IN ('r','v') AND pg_get_userbyid(relowner)<>'postgres'
   ```

   ```
   SELECT iWorkflowId FROM XtkWorkflow WHERE iWorkflowId IN ($(strCondition))
   ```

   其中&#x200B;**$(strcondition)**&#x200B;是與&#x200B;**wkfhisto%**&#x200B;掩碼匹配的表清單。

1. 其餘表使用以下查詢刪除：

   ```
   DROP TABLE wkf15487_12;
   ```

### 清除工作流程登入 {#cleanup-of-workflow-logins}

此任務使用以下查詢刪除工作流登錄：

```
DELETE FROM XtkWorkflowLogin WHERE iWorkflowId NOT IN (SELECT iWorkflowId FROM XtkWorkflow)
```

### 清除孤立工作表 {#cleanup-of-orphan-work-tables}

此任務將刪除連結到組的孤立工作表。 **NmsGroup**&#x200B;表儲存要清除的組（類型與0不同）。 表名的前置詞為&#x200B;**grp**。 要標識要清除的組，將使用以下查詢：

```
SELECT iGroupId FROM NmsGroup WHERE iType>0"
```

### 訪客清除 {#cleanup-of-visitors}

此任務使用批量刪除從訪客表中刪除過時記錄。 過時記錄是指上次修改時間早於部署嚮導中定義的保存期間（請參閱[部署嚮導](#deployment-wizard)）的記錄。 使用下列查詢：

```
DELETE FROM NmsVisitor WHERE iVisitorId IN (SELECT iVisitorId FROM NmsVisitor WHERE iRecipientId = 0 AND tsLastModified < AddDays(GetDate(), -30) AND iOrigin = 0 LIMIT 20000)
```

其中&#x200B;**$(tsDate)**&#x200B;是當前伺服器日期，從中減去為&#x200B;**NmsCleanup_VisitorPurgeDelay**&#x200B;選項定義的期間。

### 清除NPAI {#cleanup-of-npai}

此任務允許您從&#x200B;**NmsAddress**&#x200B;表中刪除與有效地址匹配的記錄。 以下查詢用於執行成批刪除：

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=2 AND tsLastModified < $(tsDate1) AND tsLastModified >= $(tsDate2) LIMIT 5000)
```

其中&#x200B;**status 2**&#x200B;與&#x200B;**[!UICONTROL Valid]**&#x200B;狀態匹配，**$(tsDate1)**&#x200B;為當前伺服器日期，而&#x200B;**$(tsDate2)**&#x200B;與&#x200B;**NmsCleanup_LastCleanup**&#x200B;選項匹配。

### 清除訂閱 {#cleanup-of-subscriptions-}

此任務使用成批刪除來清除用戶從&#x200B;**NmsSubscription**&#x200B;表中刪除的所有訂閱。 使用下列查詢：

```
DELETE FROM NmsSubscription WHERE iDeleteStatus <>0
```

### 清除追蹤記錄 {#cleanup-of-tracking-logs}

此任務從跟蹤日誌表和網路跟蹤日誌表中刪除過時記錄。 過時記錄是指早於部署嚮導中定義的保護期（請參閱[部署嚮導](#deployment-wizard)）的記錄。

1. 首先，使用下列查詢來復原追蹤記錄表清單：

   ```
   SELECT distinct(sTrackingLogSchema) FROM NmsDeliveryMapping WHERE sTrackingLogSchema IS NOT NULL;
   ```

1. 成批刪除用於清除先前恢復的表清單中的所有表。 使用下列查詢：

   ```
   DELETE FROM XtkTrackingLogRcp WHERE iTrackingLogId IN (SELECT iTrackingLogId FROM XtkTrackingLogRcp WHERE tsLog < $(tsDate) LIMIT 5000) 
   ```

   其中&#x200B;**$(tsDate)**&#x200B;是當前伺服器日期，從中減去為&#x200B;**NmsCleanup_TrackingLogPurgeDelay**&#x200B;選項定義的期間。

1. 追蹤統計資料表格會使用大量刪除來清除。 使用下列查詢：

   ```
   DELETE FROM NmsTrackingStats WHERE iTrackingStatsId IN (SELECT iTrackingStatsId FROM NmsTrackingStats WHERE tsStart < $(tsDate) LIMIT 5000) 
   ```

   其中&#x200B;**$(tsDate)**&#x200B;是當前伺服器日期，從中減去為&#x200B;**NmsCleanup_TrackingStatPurgeDelay**&#x200B;選項定義的期間。

### 清除傳送記錄檔 {#cleanup-of-delivery-logs}

此任務可讓您清除儲存在各種表格中的傳送日誌。

1. 為此，會使用下列查詢來復原傳送記錄結構清單：

   ```
   SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL UNION SELECT distinct(sBroadLogExclSchema) FROM NmsDeliveryMapping WHERE sBroadLogExclSchema IS NOT NULL
   ```

1. 使用中間來源時，傳送對應中未參考&#x200B;**NmsBroadLogMid**&#x200B;表格。 將&#x200B;**nms:broadLogMid**&#x200B;方案添加到由前一個查詢恢復的清單中。
1. 然後， **資料庫清理**&#x200B;工作流將清除先前恢復的表中的過時資料。 使用下列查詢：

   ```
   DELETE FROM $(tableName) WHERE iBroadLogId IN (SELECT iBroadLogId FROM $(tableName) WHERE tsLastModified < $(option) LIMIT 5000) 
   ```

   其中&#x200B;**$(tableName)**&#x200B;是方案清單中每個表的名稱，而&#x200B;**$(option)**&#x200B;是為&#x200B;**NmsCleanup_BroadLogPurgeDelay**&#x200B;選項（請參閱[部署精靈](#deployment-wizard)）定義的日期。

1. 最後，工作流檢查&#x200B;**NmsProviderMsgId**&#x200B;表是否存在。 若存在，則會使用下列查詢來刪除所有過時資料：

   ```
   DELETE FROM NmsProviderMsgId WHERE iBroadLogId IN (SELECT iBroadLogId FROM NmsProviderMsgId WHERE tsCreated < $(option) LIMIT 5000)
   ```

   其中&#x200B;**$（選項）**&#x200B;與為&#x200B;**NmsCleanup_BroadLogPurgeDelay**&#x200B;選項定義的日期相符（請參閱[部署精靈](#deployment-wizard)）。

### 清理NmsEmailErrorStat表 {#cleanup-of-the-nmsemailerrorstat-table-}

此任務將清除&#x200B;**NmsEmailErrorStat**&#x200B;表。 主程式(**coalesceErrors**)定義了兩個日期：

* **開始日期**:與NmsLastErrorStatCoalesce選項或表中 **** 的最近日期匹配的下一個進程的日期。
* **結束日期**:當前伺服器日期。

如果開始日期大於或等於結束日期，則不會進行任何程式。 在這種情況下，會顯示&#x200B;**coalesceUpToDate**&#x200B;消息。

如果開始日期早於結束日期，則會清除&#x200B;**NmsEmailErrorStat**&#x200B;表。

**NmsEmailErrorStat**&#x200B;表中在開始日期和結束日期之間的錯誤總數使用以下查詢進行恢復：

```
"SELECT COUNT(*) FROM NmsEmailErrorStat WHERE tsDate>= $(start) AND tsDate< $(end)"
```

其中&#x200B;**$end**&#x200B;和&#x200B;**$start**&#x200B;是先前定義的開始和結束日期。

如果總計大於0:

1. 執行下列查詢，僅將錯誤保持在超過特定臨界值（等於20）:

   ```
   "SELECT iMXIP, iPublicId, SUM(iTotalConnections), SUM(iTotalErrors), SUM(iMessageErrors), SUM(iAbortedConnections), SUM(iFailedConnections), SUM(iRefusedConnections), SUM(iTimeoutConnections) FROM NmsEmailErrorStat WHERE tsDate>=$(start ) AND tsDate<$(end ) GROUP BY iMXIP, iPublicId HAVING SUM(iTotalErrors) >= 20"
   ```

1. 此時將顯示&#x200B;**coalescingErrors**&#x200B;消息。
1. 系統會建立新連線，以刪除開始日期與結束日期之間發生的所有錯誤。 使用下列查詢：

   ```
   "DELETE FROM NmsEmailErrorStat WHERE tsDate>=$(start) AND tsDate<$(end)"
   ```

1. 每個錯誤都使用以下查詢保存在&#x200B;**NmsEmailErrorStat**&#x200B;表中：

   ```
   "INSERT INTO NmsEmailErrorStat(iMXIP, iPublicId, tsDate, iTotalConnections, iTotalErrors, iTimeoutConnections, iRefusedConnections, iAbortedConnections, iFailedConnections, iMessageErrors) VALUES($(lmxip ), $(lpublicId ), $(tsstart ), $(lconnections ), $(lconnectionErrors ),$(ltimeoutConnections ), $(lrefusedConnections ), $(labortedConnections ), $(lfailedConnections ), $(lmessageErrors))"
   ```

   其中，每個變數都符合上一個查詢所復原的值。

1. **start**&#x200B;變數會以前一個進程的值更新，以完成循環。

循環和任務停止。

清除會在&#x200B;**NmsEmailError**&#x200B;和&#x200B;**cleanupNmsMxDomain**&#x200B;表上執行。

### 清理NmsEmailError表 {#cleanup-of-the-nmsemailerror-table-}

使用下列查詢：

```
DELETE FROM NmsEmailError WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢從&#x200B;**NmsEmailError**&#x200B;表中刪除&#x200B;**NmsEmailError**&#x200B;中沒有連結記錄的所有行。

### 清理NmsMxDomain表 {#cleanup-of-the-nmsmxdomain-table-}

使用下列查詢：

```
DELETE FROM NmsMxDomain WHERE iMXIP NOT IN (SELECT DISTINCT iMXIP FROM NmsEmailErrorStat)
```

此查詢從&#x200B;**NmsMxDomain**&#x200B;表刪除&#x200B;**NmsEmailErrorStat**&#x200B;表中沒有連結記錄的所有行。

### 清理命題 {#cleanup-of-propositions}

如果安裝了&#x200B;**Interaction**&#x200B;模組，則執行此任務以清除&#x200B;**NmsPostitionXxx**&#x200B;表。

使用以下查詢恢復命題表清單，並對每個命題表執行批量刪除：

```
DELETE FROM NmsPropositionXxx WHERE iPropositionId IN (SELECT iPropositionId FROM NmsPropositionXxx WHERE tsLastModified < $(option) LIMIT 5000) 
```

其中&#x200B;**$（選項）**&#x200B;是為&#x200B;**NmsCleanup_PostitionPurgeDelay**&#x200B;選項（請參閱[部署嚮導](#deployment-wizard)）定義的日期。

### 清理模擬表 {#cleanup-of-simulation-tables}

此任務會清除孤立模擬表（不再連結至選件模擬或傳送模擬）。

1. 若要復原需要清除的模擬清單，會使用下列查詢：

   ```
   SELECT iSimulationId FROM NmsSimulation WHERE iSimulationId<>0
   ```

1. 要刪除的表的名稱由&#x200B;**wkSimu_**&#x200B;前置片語成，後跟模擬的標識符(例如：**wkSimu_456831_aggr**):

   ```
   DROP TABLE wkSimu_456831_aggr
   ```

### 清理稽核軌跡 {#cleanup-of-audit-trail}

使用下列查詢：

```
DELETE FROM XtkAudit WHERE tsChanged < $(tsDate)
```

其中&#x200B;**$(tsDate)**&#x200B;是為&#x200B;**XtkCleanup_AuditTrailPurgeDelay**&#x200B;選項定義的期間從哪個當前伺服器日期訂閱。

### 清除Nmsaddress {#cleanup-of-nmsaddress}

使用下列查詢：

```
DELETE FROM NmsAddress WHERE iAddressId IN (SELECT iAddressId FROM NmsAddress WHERE iStatus=STATUS_QUARANTINE AND tsLastModified < $(NmsCleanup_AppSubscriptionRcpPurgeDelay + 5d) AND iType IN (MESSAGETYPE_IOS, MESSAGETYPE_ANDROID ) LIMIT 5000)
```

此查詢會刪除與iOS和Android相關的所有項目。

### 統計資訊更新和儲存優化 {#statistics-update}

**XtkCleanup_NoStats**&#x200B;選項可讓您控制清除工作流程中儲存最佳化步驟的行為。

如果&#x200B;**XtkCleanup_NoStats**&#x200B;選項不存在，或如果其值為0，則將在PostgreSQL上以冗餘模式(VAMU VERBOSE ANALYZE)執行儲存優化，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 VAMU將輸出以下格式的行：`INFO: vacuuming "public.nmsactivecontact"`和ANALYZE將輸出以下格式的行：`INFO: analyzing "public.nmsactivecontact"`。

如果選項的值為1，則不會對任何資料庫執行統計資訊更新。 工作流程記錄檔中會顯示下列記錄行：`Option 'XtkCleanup_NoStats' is set to '1'`。

如果選項的值為2，則將在PostgreSQL上以詳細模式(ANALYZE VERBOSE)執行儲存分析，並更新所有其他資料庫的統計資訊。 要確保執行此命令，請檢查PostgreSQL日誌。 ANALYZE將輸出以下格式的行：`INFO: analyzing "public.nmsactivecontact"`。

### 訂閱清除(NMAC) {#subscription-cleanup--nmac-}

此任務將刪除與已刪除服務或移動應用程式相關的任何訂閱。

若要復原broadlog結構清單，請使用下列查詢：

```
SELECT distinct(sBroadLogSchema) FROM NmsDeliveryMapping WHERE sBroadLogSchema IS NOT NULL
```

然後，任務將恢復連結到&#x200B;**appSubscription**&#x200B;連結的表的名稱，並刪除這些表。

此清理工作流還刪除自&#x200B;**NmsCleanup_AppSubscriptionRcpPurgeDelay**&#x200B;選項中設定的時間以來未更新的idisabled = 1的所有條目。

### 清除會話資訊 {#cleansing-session-information}

此任務會清除&#x200B;**sessionInfo**&#x200B;表中的資訊，並使用以下查詢：

```
 DELETE FROM XtkSessionInfo WHERE tsexpiration < $(curdate) 
```

### 清除過期事件 {#cleansing-expired-events}

此任務會清除在執行實例上接收和儲存的事件以及在控制實例上存檔的事件。

### 清除反應 {#cleansing-reactions}

此任務清除了已刪除假設的反應（表&#x200B;**NmsRemaMatchRcp**）。
