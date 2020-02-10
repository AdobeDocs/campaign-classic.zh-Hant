---
title: 執行工作流程
seo-title: 執行工作流程
description: 執行工作流程
seo-description: null
page-status-flag: never-activated
uuid: 7668f1a2-fcd0-41f8-b8f6-71d77bc47486
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: -general-operation
discoiquuid: 9ac4c60a-b0f6-42fb-a081-74b57820cb16
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 4b4ec97e52a494dd88b2516650ae514294f00934

---


# 執行工作流程{#executing-a-workflow}

本節提供與工作流程執行相關的疑難排解 [指引](../../production/using/workflow-execution.md)。

## 啟動工作流 {#starting-a-workflow}

工作流程一律以手動方式啟動。 但是，啟動時，它可以根據通過調度程式指定的資訊(請參見 [Scheduler](../../workflow/using/scheduler.md))或活動調度來保持非活動狀態。

與定位工作流程執行（啟動、停止、暫停等）相關的動作是非 **同步進程** :訂單會記錄下來，當伺服器可供套用時，訂單就會生效。

工具列可讓您啟動並追蹤工作流程的執行。

功能表和右鍵功能表 **[!UICONTROL Actions]** 中可用選項的清單在下方詳述。

### 動作工具列 {#actions-toolbar}

本節將詳細介紹工具欄 [按鈕](../../campaign/using/marketing-campaign-deliveries.md#building-the-main-target-in-a-workflow)。 此按 **[!UICONTROL Actions]** 鈕可讓您存取其他執行選項，以便在選取的工作流程上執行。 您也可以使用功 **[!UICONTROL File > Actions]** 能表，或以滑鼠右鍵按一下工作流程並選取 **[!UICONTROL Actions]**。

![](assets/purge_historique.png)

* **[!UICONTROL Start]**

   此動作可讓您開始執行工作流程：已完成、正在編 **輯**&#x200B;或暫 **停的工作流將狀** 態更改為 ********&#x200B;已啟動 然後，工作流引擎將處理此工作流的執行。 如果暫停了工作流，則會繼續，否則工作流會從頭開始，並激活初始活動。

   啟動是非同步程式：請求會儲存，並由工作流程伺服器盡快處理。

* **[!UICONTROL Pause]**

   此動作會將工作流程的狀態設為「暫 **停」**。 在工作流恢復之前，不會激活任何活動；但不會暫停進行中的操作。

* **[!UICONTROL Stop]**

   此動作會停止目前執行的工作流程。 實例的狀態設定為「已 **完成」**。 如果可能，將停止正在進行的操作。 導入和SQL查詢會立即取消。

   停止是非同步進程。 該請求被註冊，然後工作流伺服器或伺服器取消正在進行的操作。 因此，停止工作流實例可能需要時間，尤其是當工作流在多個伺服器上運行時，每個伺服器都必須控制其中的一個，以取消正在進行的任務。

* **[!UICONTROL Restart]**

   此動作會停止，然後重新啟動工作流程。 在大多數情況下，它可以更快地重新啟動。 當停止需要一定時間時，自動重新啟動也很有用：這是因為當工作流停止時，「停止」命令不可用。

   這些 **[!UICONTROL Start / Pause / Stop / Restart]** 動作也可透過工具列中的執行圖示使用。 For more on this, refer to this [section](../../campaign/using/marketing-campaign-deliveries.md#creating-a-targeting-workflow).

* **[!UICONTROL Purge history]**

   此動作可讓您清除工作流程歷史記錄。 有關詳細資訊，請參閱 [清除日誌](../../workflow/using/monitoring-workflow-execution.md#purging-the-logs)。

* **[!UICONTROL Start in simulation mode]**

   此選項可讓您在模擬模式中啟動工作流程，而非實際模式。 這表示啟用此模式時，僅執行不影響資料庫或檔案系統的活動(如 **[!UICONTROL Query]**、 **[!UICONTROL Union]****[!UICONTROL Intersection]**&#x200B;等)。 具有影響的活動(例如 **[!UICONTROL Export]**、 **[!UICONTROL Import]**&#x200B;等等)以及之後（位於相同分支）的執行。

* **[!UICONTROL Execute pending tasks now]**

   此動作可讓您盡快開始所有待審工作。 要啟動特定任務，請按一下右鍵其活動並選擇 **[!UICONTROL Execute pending task(s) now]**。

* **[!UICONTROL Unconditional stop]**

   此選項會將工作流狀態更改為 **[!UICONTROL Finished]**。 只有在正常停止進程在幾分鐘後失敗時，才應將此操作用作最後選擇。 只有在確定沒有實際工作流作業正在進行時，才使用無條件停止。

   >[!CAUTION]
   >
   >此選項保留給專家用戶。

* **[!UICONTROL Save as template]**

   此動作會根據選取的工作流程建立新的工作流程範本。 您需要指定要儲存檔案夾的資料夾(在欄位 **[!UICONTROL Folder]** 中)。

   這些 **[!UICONTROL Mass update of selected lines]** 和 **[!UICONTROL Merge selected lines]** 選項是所有功能表中可用的通用平台 **[!UICONTROL Actions]** 選項。 For more on this, refer to this [section](../../platform/using/updating-data.md).

### 右鍵功能表 {#right-click-menu}

在選取一或多個工作流程活動時，您可以按一下滑鼠右鍵，對您的選取動作。

![](assets/contextual_menu.png)

右鍵功能表提供下列選項：

**[!UICONTROL Open]**:此選項可讓您存取活動屬性。

**[!UICONTROL Display logs:]** 此選項可讓您查看所選活動的任務執行日誌。 請參閱顯 [示日誌](../../workflow/using/monitoring-workflow-execution.md#displaying-logs)。

**[!UICONTROL Execute pending task(s) now:]** 此動作可讓您盡快開始待審工作。

**[!UICONTROL Workflow restart from a task:]** 此選項可讓您使用先前儲存的此活動結果，重新啟動工作流程。

**[!UICONTROL Cut/Copy/Paste/Delete:]** 這些選項可讓您剪下、複製、貼上和刪除活動。

**[!UICONTROL Copy as bitmap:]** 此選項可讓您擷取所有活動的螢幕擷取。

**[!UICONTROL Normal execution / Enable but do not execute / Do not enable:]** 這些選項也可在活動屬 **[!UICONTROL Advanced]** 性的頁籤中使用。 這些內容在「執行」 [中詳述](../../workflow/using/advanced-parameters.md#execution)。

**[!UICONTROL Save / Cancel:]** 可讓您儲存或取消對工作流程所做的變更。

>[!NOTE]
>
>您可以選取一組活動，並將其中一個命令套用至活動。

本節中也詳述了右鍵功 [能表](../../campaign/using/marketing-campaign-deliveries.md#executing-a-workflow)。

## 工作流程生命週期 {#workflow-life-cycle}

工作流程週期有三個主要步驟。

* **正在編輯**

   這是初始設計階段：建立新工作流程時，其狀態為「正在編輯」。 伺服器尚未處理工作流程，因此可以無風險地修改工作流程。

* **已開始**

   在初始設計階段完成後，就可以開始工作流程。 在此階段中，由伺服器處理實例，並執行各個任務。 工作流仍然可以用某些預防措施進行修改。

* **已完成**

   當不再進行任何工作或操作員明確停止實例時，工作流將為「完成」。

例如，開始和 **交付** (Start **)活動和交付(Delivery** )活動在下面 **** 的工作區閃爍。

![](assets/new-workflow-6.png)

這表示前兩項活動已成功執行，且正在進行核准，即已建立但尚未完成。

在 **Delivery** （傳送）活動後，轉場上方顯示的字元為574 -Ok **** ，表示傳送準備已鎖定574位收件者，且作業已順利完成。 執行轉場時會新增此資訊至轉場，由處理資料的活動計算。

工作流已啟動，正在等待屬於「批准」活動中指定的組的運 **算** 符做出決策。 會通知屬於該群組的營運商以及擁有電子郵件地址或行動電話號碼的營運商。

操作員管理在本節中有詳 [細說明](../../platform/using/access-management.md)。

如需如何監控工作流程的詳細資訊，請參閱 [本節](../../workflow/using/monitoring-workflow-execution.md)。

## 資料生命週期 {#data-life-cycle}

### 工作表 {#work-table}

在工作流中，從一個活動傳輸到另一個活動的資料儲存在臨時工作表中。

以滑鼠右鍵按一下適當的轉場，即可顯示和分析此資料。

![](assets/wf-right-click-analyze.png)

若要這麼做，請選取相關功能表：

* 顯示目標

   此菜單顯示目標人口的可用資料以及工作表（頁籤）**[!UICONTROL Schema]** 的結構。

   ![](assets/wf-right-click-display.png)

   有關詳細資訊，請參閱工作 [表和工作流模式](../../workflow/using/monitoring-workflow-execution.md#worktables-and-workflow-schema)。

* 分析目標

   此功能表可讓您存取描述性分析精靈，讓您產生轉場資料的統計資料和報表。

   For more on this, refer to this [section](../../reporting/using/using-the-descriptive-analysis-wizard.md).

當執行工作流時，會清除目標資料。 只有最後一個工作表可以訪問。 您可以配置工作流，以便所有工作表保持可訪問性：選中工 **[!UICONTROL Keep the result of interim populations between two executions]** 作流屬性中的選項。

不過，我們建議您避免在大量資料時啟用此選項。

![](assets/wf-purge-data-option.png)

### 目標資料 {#target-data}

儲存在工作流工作表中的資料可以在個性化欄位中訪問。

這可讓您使用透過清單收集或根據傳送中調查的答案收集的資料。 若要這麼做，請使用下列語法：

```
%= targetData.FIELD %
```

**[!UICONTROL Target extension]** (targetData)類型的個人化元素無法用於定位工作流程。 傳送目標必須在工作流程中建立，並在傳送的傳入轉換中指定。

如果您想要建立傳送校樣，則需要根據模式建立校樣目 **[!UICONTROL Address substitution]** 標，以便輸入個人化資料。 For more on this, refer to this [section](../../delivery/using/steps-defining-the-target-population.md#using-address-substitution-in-proof).

在下例中，我們將收集客戶相關資訊的清單，以便用於個人化電子郵件。

應用以下步驟：

1. 建立工作流程以收集資訊、將其與資料庫中已有的資料協調，然後開始傳送。

   ![](assets/wf-targetdata-sample-1.png)

   在我們的範例中，檔案內容如下：

   ```
   Music,First name,Last name,Account,CD/DVD,Card
   Pop,David,BLAIR,4323,CD,0
   Rock,Daniel,ARCARI,3222,DVD,1
   Disco,Uma,ALTON,0488,DVD,0
   Jazz,Paul,BOLES,6475,CD,1
   Jazz,David,BOUKHARI,0841,DVD,1
   [...]
   ```

   若要載入檔案，請套用下列步驟：

   ![](assets/wf-targetdata-sample-2.png)

1. 設定類 **[!UICONTROL Enrichment]** 型活動，以協調已收集的資料與Adobe Campaign資料庫中已有的資料。

   在這裡，協調密鑰是帳戶號碼：

   ![](assets/wf-targetdata-sample-3.png)

1. 然後設定 **[!UICONTROL Delivery]**:它是根據模板建立的，而收件者則由入站轉換指定。

   ![](assets/wf-targetdata-sample-4.png)

   >[!CAUTION]
   >
   >只有轉換中包含的資料才能用於個人化傳送。 **targetData** type personalization欄位僅適用於活動的傳入 **[!UICONTROL Delivery]** 人口。

1. 在傳送範本中，使用在工作流程中收集的欄位。

   若要這麼做，請插入 **[!UICONTROL Target extension]** 文字個人化欄位。

   ![](assets/wf-targetdata-sample-5.png)

   在此，我們要插入客戶最愛的音樂類型和媒體類型（CD或DVD），如工作流程收集的檔案中所述。

   另外，我們將為忠誠卡持有者（即「卡」值等於1的收件者）新增抵用券。

   ![](assets/wf-targetdata-sample-6.png)

   **[!UICONTROL Target extension]** (targetData)類型資料會使用與所有個人化欄位相同的特性，插入傳送。 它們也可用於主題、連結標籤或連結本身。

   傳送給收集之收件者的訊息將包含下列資料：

   ![](assets/wf-targetdata-sample-7.png)

## 定義審批 {#defining-approvals}

運算子可使用核准來決定工作流程，或確認其持續執行。

系統會傳送訊息給一組運算子，而工作流程會等待回應再繼續。 工作流不會停止，並且可以執行其他操作。 例如，可能有多個同時核准擱置中。

一個核准可以包含多個選項，讓運算子可以選擇。 但是，可以將選擇的數目限制為一個，以便將要執行的任務提交給操作員（如執行定位）。 然後，操作員可以在執行任務後做出響應（然後繼續處理）。 以下示例說明了這些類型的批准：

![](assets/validation-1.png)

在營運中，所有需要核准的階段都以相同的原則為基礎。

![](assets/validation-1-in-op.png)

您可在本節中找到核准 [範例](../../campaign/using/marketing-campaign-approval.md#checking-and-approving-deliveries)。

運算子可以以兩種方式回應：驗證是否使用電子郵件訊息中連結的網頁，或透過主控台。

>[!NOTE]
>
>儲存回應後，就無法加以修改。

### 傳送電子郵件 {#sending-emails}

可以接收包含到可回應的網頁的連結的批准消息。 要讓目標營運商收到核准電子郵件，營運商的電子郵件地址必須完整。 如果不是這樣，運算子必須使用主控台來回應

操作員管理在本節中有詳 [細說明](../../platform/using/access-management.md)。

核准電子郵件會持續傳送。 預設的傳送範本為 **[!UICONTROL notifyAssignee]**:它會儲存在資料 **[!UICONTROL Administration > Campaign management > Technical delivery templates]** 夾中。 您可自訂此藍本，也建議您製作復本並變更每個活動的範本。

透過此範本建立的傳送會儲存在資料 **[!UICONTROL Administration > Production > Objects created automatically > Technical deliveries > Workflow notifications]** 夾中。

### 透過主控台核准 {#approval-via-the-console}

在操作中，要核准的元素會顯示在促銷活動控制面板上。

對於技術工作流，用戶可以從資料夾的樹結構訪問用戶可以批准的 **[!UICONTROL Administration > Production > Objects created automatically > Pending approvals]** 任務。

![](assets/validation-node.png)

### 群組 {#groups}

核准會指派給透過篩選條件選取的運算子群組、單一運算子或運算子集。

1. 對於最簡單的核准形式，只要營運商回應，任務就會立即完成。 任何其他嘗試回應的營運商都會收到有人已做過的通知。
1. 如需多項核准，請參閱多 [項核准](#multiple-approval)。

審批的運算元群組應指定為角色或函式，而非指定個人。 例如，「促銷活動預算」群組比「Harry&#39;s group」更好。 我們建議在一個群組中至少要有兩個人可以核准工作。 這樣，如果缺一個，另一個就可以回應。

### 到期日 {#expirations}

過期是用於不同活動類型（尤其是在批准中）的特定轉場。 過期可用來在沒有回應的指定時間段後觸發動作，或追蹤工作流程（例如，將核准指派給不同群組）。

活動核准屬性中的第二個標籤可讓您定義一或多個到期日。 事實上，您可以定義多種過期類型。

![](assets/expiration.png)

若要新增過期時間，請按一下 **[!UICONTROL Add]**。 轉換會新增至所建立的每個到期日。 您可以：

* 通過按一下清單中的單元格（或按F2）直接修改典型參數，
* 或者，按一下按鈕編輯運算 **[!UICONTROL Detail...]** 式。

>[!NOTE]
>
>在按時間順序處理到期日時，不需要指定其順序。

當延 **[!UICONTROL Do not terminate the task]** 遲超出時，此選項會使批准保持活動狀態。 此模式可讓您在啟用核準時管理提醒：營運商仍可回應。 此選項預設為停用，這表示任務在到期時即視為完成，而運算子可能不再回應。

您可以建立四種到期類型：

* **任務開始後延遲**:有效期的計算方式是將指定的時間長度新增至核准啟動的日期。
* **在指定日期後延遲**:到期日的計算方式是將時間長度新增至您指定的日期。
* **在指定日期之前延遲**:有效期的計算方式是從您指定的日期減去時間長度。
* **按指令碼計算的過期時間**:有效期是使用JavaScript計算。

   下列範例會計算傳送開始之日24小時前的到期日(由 **vars.deliveryId識別**):

   ```
   var delivery = nms.delivery.get(vars.deliveryId)
   var expiration = delivery.scheduling.contactDate
   var oneDay = 1000*60*60*24
   expiration.setTime(expiration.getTime() - oneDay)
   return expiration
   ```

### 多重核准 {#multiple-approval}

多重核准是一種機制，可讓所有核准營運商回應。 會針對每個回應啟動轉場。

多重核准對投票或調查機制有用。 您可以計算答案，並在指定的時段後，透過新增期限來處理結果。

### 必要權限 {#required-rights}

群組中的營運商至少必須擁有下列權利，才能回應核准請求：

* 工作流程的寫入權限。
* 包含要批准任務的資料夾的讀寫權限。

「工作流執行」組具有這些權限。 新增至此群組的運算子有權回應核准請求。

## 建築 {#architecture}

工作流由特定模組處理。 此模組可在多台伺服器上啟動，以共用處理負載。

![](assets/architecture.png)

* 「工作流實例運行者」(runwf)進程執行給定工作流實例的所有任務。 當目前沒有任務需要執行時，它會變成「被動」，即它將狀態保存在資料庫中，然後停止。
* 「Workflow Server」(wfserver)模組會監控目前的工作流程例項。 當有要執行的任務時，此模組將建立一個過程以激活（或重新激活）相應實例。

當操作員對工作流執行動作（啟動、停止、暫停等）時，「nlserver」模組不會直接執行動作，而是將動作置於佇列中，以便由工作流模組處理。
