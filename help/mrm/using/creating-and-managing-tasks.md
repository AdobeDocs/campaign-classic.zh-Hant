---
product: campaign
title: 建立及管理任務
description: 建立及管理任務
feature: Resource Management
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
exl-id: cc1200fa-f6d8-4f41-aed1-d1a7f229447a
source-git-commit: 668cee663890fafe27f86f2afd3752f7e2ab347a
workflow-type: tm+mt
source-wordcount: '3750'
ht-degree: 0%

---

# 建立及管理設定檔{#creating-and-managing-tasks}



Adobe Campaign可讓您直接在應用程式中建立任務並管理其完整的生命週期。 方案和行銷活動實作可以細分為指派給Adobe Campaign操作員或外部服務提供者的任務。 此作業模式可讓您建立包含所有方案參與者和外部參與者的開放式共同作業環境。

您可以從任務清單或行銷活動控制面板建立、檢視及監控任務。 您也可以在行銷計畫、方案和行銷活動的排程中檢視和追蹤這些活動。

任務會附加至行銷活動，且可以具有相依性，即相關任務。 每個任務都有狀態、優先順序、預估負載和相關成本。

所有任務都分組在清單中，可透過存取 **行銷活動** 標籤。 有關詳細資訊，請參閱 [存取任務](#accessing-tasks).

它們可以顯示在所屬方案的排程中。

![](assets/d_ncs_user_tasks_in_planning.png)

## 存取任務 {#accessing-tasks}

### 顯示任務 {#displaying-tasks}

任務會顯示在可透過存取的任務清單中 **[!UICONTROL Campaigns]** 標籤。

![](assets/s_ncs_user_task_edit_view.png)

您可以在此檢視連線運運算元的所有工作。

有關詳細資訊，請參閱 [任務的執行狀態](#execution-status-of-a-task) 和 [任務的進度狀態](#progress-status-of-a-task).

### 篩選任務 {#filtering-tasks}

當您顯示此檢視時，系統會自動篩選該檢視以僅顯示 **[!UICONTROL operator tasks]**. 您也可以使用視窗上半部分的欄位來篩選任務。

![](assets/s_ncs_user_task_filter_from_view.png)

### 編輯任務 {#editing-tasks}

按一下工作以進行編輯。

![](assets/s_ncs_user_task_edit_from_view.png)

## 建立新任務 {#creating-a-new-task}

若要建立任務，請按一下 **[!UICONTROL Tasks]** 中的連結 **[!UICONTROL Campaigns]** 標籤並選取 **[!UICONTROL Create]**.

![](assets/s_ncs_user_task_create_new.png)

至少輸入任務的名稱，並選取它連結到的行銷活動。 您也必須指定開始和結束日期。 這三則資訊屬於必要資訊。

按一下 **[!UICONTROL Save]** 以建立任務。

![](assets/s_ncs_user_task_create_simple.png)

您也可以透過行銷活動的控制面板建立任務：在這種情況下，會自動連結至建立該行銷活動的來源。

![](assets/s_ncs_user_task_create_new_from_op.png)

建立任務後，會將其新增至行銷活動排程和任務清單。 若要編輯任務，請從排程中選取該任務，或在任務概述中按一下其名稱，然後按一下 **[!UICONTROL Open]** 連結。

![](assets/s_ncs_user_task_edit_simple.png)

若要進行設定，您必須指出：

* 經理與參與者：請參閱 [經理與參與者](#manager-and-participants).
* 建立排程：請參閱 [執行排程](#execution-schedule).
* 確認成本：請參閱 [費用與收入](#expenses-and-revenues).

也可以新增稽核者(請參閱 [檢閱者](#reviewers))和參考的檔案(請參閱 [引用的檔案](#documents-referenced))。

任務生命週期顯示於 [生命週期](#life-cycle).

### 經理與參與者 {#manager-and-participants}

只有負責任務的操作員才有權關閉任務。

根據預設，當Adobe Campaign運運算元建立任務時，會自動指派給他們。 若要選取其他運運算元，請使用 **[!UICONTROL Assigned to]** 欄位。

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>運運算元管理在中呈現 [本節](../../platform/using/access-management.md).

您可以指定執行任務時涉及的操作者。 這些操作者無權關閉任務。 他們只能核准指派給他們的任務。

您可使用 **[!UICONTROL Resources]** 圖示進行編輯。 按一下 **[!UICONTROL Add]** 並選取相關運運算元。

![](assets/s_ncs_user_task_add_resources.png)

按一下 **[!UICONTROL Ok]** 然後輸入使用率：這代表作業執行期間指派給運運算元的負載。 此比率僅供參考，並以百分比表示。

例如，對於執行排程設定為10天的工作，使用率為50%的運運算元將會在此任務上動員10天一半的工作時間。

對於每個運運算元，您可以輸入排程工作負載與實際工作負載。 這些持續時間也僅供參考。

您可以設定提醒，提醒會在任務結束日期之前自動傳送給所有參與工作的操作者。

您可以透過以下方式檢視Adobe Campaign運運算元設定檔： **[!UICONTROL Edit link]** 圖示。

![](assets/s_ncs_user_task_edit_resource_profile.png)

操作員儀表板可讓您檢查其工作量（其他進行中的任務）。

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 檢閱者 {#reviewers}

除了參與者之外，您還可以定義作業執行者，當作業執行者關閉作業後，他們將會複查作業。 若要這麼做，請按一下 **[!UICONTROL Enable task approval]** 的左下角選項 **[!UICONTROL Resources]** 視窗。 這可以是個別運運算元、一組運運算元或運運算元清單。

![](assets/s_ncs_user_task_edit_resource_validation.png)

若要指定運運算元清單，請按一下 **[!UICONTROL Edit...]** 連結至第一個檢閱者的右側，並視需要新增運運算元，如下所示：

![](assets/s_ncs_user_task_edit_resource_operators.png)

您可以在檢閱者組態視窗的下半部定義任務的核准排程。 依預設，稽核者從提交日期起有三天可核准任務。 您可以設定提醒，提醒會在核准截止日期前自動傳送給相關操作者。

![](assets/s_ncs_user_edit_op_valid_calendar.png)

任務負責人可以指派自己核准任務，即使已指派其他操作員進行此工作。 如果尚未定義稽核者，則會將通知傳送給負責任務的人。 所有其他的Adobe Campaign運運算元，搭配 **[!UICONTROL Administrator]** 許可權也可以核准任務。 但他們不會收到通知。

### 引用的檔案 {#documents-referenced}

您可以將檔案和行銷資源新增到任務(如需詳細資訊，請參閱 [管理行銷資源](../../mrm/using/managing-marketing-resources.md))。 若要這麼做，請開啟工作並按一下 **[!UICONTROL Documents]** 圖示進行編輯。

按一下 **[!UICONTROL Add]** 並選取要新增至您工作的檔案。 對行銷資源套用相同程式。

![](assets/s_ncs_user_task_edit_documents.png)

參考的檔案會顯示在傳送給工作相關操作員的通知中，也會顯示在工作控制面板上。

![](assets/s_ncs_user_task_notification_documents.png)

### 執行排程 {#execution-schedule}

任務的有效期顯示在 **[!UICONTROL Start]** 和 **[!UICONTROL End]** 欄位。 排定的負載表示要在此期間執行的工作負載。 以天或小時表示。

>[!NOTE]
>
>任務的生命週期會顯示在中 [生命週期](#life-cycle).

此 **[!UICONTROL Workload performed]** 欄位也以天和小時表示，可讓您手動更新與排程工作負載相關的任務進度。

![](assets/s_ncs_user_task_percentage_done_enter.png)

此 **[!UICONTROL Progress status]** 會根據相關操作員執行的作業自動更新的（以百分比表示）。 可以手動輸入。

可在任務儀表板中檢視此資訊。

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

它也會顯示在行銷活動標籤中。

![](assets/s_ncs_user_task_percentage_done_from_op.png)

如果已達到任務執行排程結束日期，但任務尚未完成，則任務將會 **[!UICONTROL Late]**. 警告訊息也會顯示給警示操作者。

有關詳細資訊，請參閱 [任務的進度狀態](#progress-status-of-a-task).

### 費用與收入 {#expenses-and-revenues}

您可以定義每個作業的相關費用與預測收入。 系統會計算這些值，然後針對附加任務的行銷活動將其合併。

若要指定此資訊，請按一下 **[!UICONTROL Expenses and revenue]** 圖示進行編輯。

![](assets/s_ncs_user_task_edit_costs.png)

依預設，收取的預算是附加任務的行銷活動的預算。 它會顯示在任務詳細資訊中。

>[!NOTE]
>
>如需費用與預算的詳細資訊，請參閱 [成本承諾、計算及收費](../../mrm/using/controlling-costs.md#cost-commitment--calculation-and-charging).

在此視窗中，您也可以定義要達成的目標。 目標會以任務的預測收入表示。

### 服務提供者 {#service-providers}

外部服務提供者可參與工作的管理。

若要這麼做，請編輯工作屬性，並選取相關的服務提供者。 與服務提供者相關的成本類別會自動列在視窗的中央區段中。

有關詳細資訊，請參閱 [建立服務提供者及其成本類別](../../campaign/using/providers-stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories).

選取與作業執行相關的成本類別。 若要這麼做，請選取成本型態，並視需要新增附加費金額。

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>管理預算與成本的方法顯示於 [控制成本](../../mrm/using/controlling-costs.md).

選取服務提供者時，它會顯示在工作儀表板中：

![](assets/s_ncs_user_task_supplier_view.png)

### 延遲任務 {#late-tasks}

如果任務已達到其結束日期且其狀態未變更為，則該任務會延遲 **[!UICONTROL Finished]**. 依預設，當任務延遲時，不會警告任何運運算元。 您可以設定通知電子郵件的傳送：即使操作員未參與工作，也可以通知所有操作員。

前往 **[!UICONTROL Resources]** 方塊並將運運算元新增至 **[!UICONTROL Assignation]** 欄位。 若要通知幾個人，請選取一組操作員。

![](assets/mrm_task_alert_if_late.png)

### 初始通知 {#initial-notifications}

當您建立或修改具有未來開始日期的任務時，Adobe Campaign會提供傳送電子郵件給負責任務的人，讓他們知道何時開始。

![](assets/mrm_task_first_notif.png)

但是，如果您要建立的任務還很遙遠，最好在任務開始之前排程要傳送的通知。 例如，如果工作在一個月後開始，您可以通知負責人員，時間早於工作開始的一週。

若要排程通知，請前往 **[!UICONTROL Resources]** 方塊並使用 **[!UICONTROL Initial notification]** 欄位。

![](assets/mrm_task_alert_before.png)

* 針對行銷活動內的任務，選取特定的日期和時間。
* 對於行銷活動範本內的任務，通知時間以任務開始前的剩餘時間表示(例如，如果您在 **[!UICONTROL Initial notification]** 欄位，電子郵件將在任務開始日期前2天傳送)。

如果您已排程通知，當您儲存任務時，Adobe Campaign仍會提供立即傳送通知的功能。 您可以決定傳送，這不會取代排程通知。

### 連結至方案的任務 {#task-linked-to-a-program}

您可以直接在方案中建立任務，以管理與其整體組織相關的動作，而不是與特定行銷活動相關的動作（例如，討論方案中即將開展行銷活動主題的會議）。 任務會出現在方案排程中。

若要建立直接連結至方案的工作：

1. 開啟方案排程：在首頁上，移至 **[!UICONTROL Campaigns > Browse > Other choices > Programs]**. 整個方案排程會在視窗的右側區段中開啟。
1. 在排程中，按一下所需的方案：一個視窗會提供其中方案。
1. 在此視窗中，按一下 **[!UICONTROL Open]**. 方案排程隨即開啟。
1. 按一下 **[!UICONTROL Add]** 按鈕於排程上方，然後按一下 **[!UICONTROL Add a task]**.

![](assets/mrm_task_create_from_prg.png)

### 操作員可用性 {#operator-availability}

在任務儀表板中，操作員名稱旁邊的圖示表示他們已在任務所涵蓋的期間處理另一個任務或事件。 運運算元負責或參與的任務會顯示在 **[!UICONTROL Assigned to]** 欄位或任務中 **[!UICONTROL Resources]** 方塊。

![](assets/mrm_task_alert_operator_busy.png)

### 工作流程中的任務 {#task-in-a-workflow}

使用 **[!UICONTROL Task]** 行銷活動工作流程中的要素可讓您根據工作是否核准來定義兩個案例。

![](assets/mrm_task_in_workflow.png)

在行銷活動工作流程中， **[!UICONTROL Task]** 活動可在 **[!UICONTROL Flow control]** 標籤。

## 任務型別 {#types-of-task}

當您透過行銷活動建立任務時，可以建立特定任務。 任務型別在所選範本中定義。

![](assets/s_ncs_user_task_select_template.png)

可以排程下列工作：

* [控制任務](#control-tasks)，
* [分組任務](#grouping-task)，
* [分組任務](#grouping-task)，
* [通知任務](#notification-task).

>[!NOTE]
>
>**[!UICONTROL Control task]** 和 **[!UICONTROL Grouping]** 可以建立任務 **僅限** 透過campaign控制面板。\
>它們會顯示在指派給它們的運運算元的工作圖中。 另請參閱 [存取任務](#accessing-tasks).

### 控制任務 {#control-tasks}

A **[!UICONTROL Control task]** 連結至傳遞核准：核准目標、內容、擷取檔案、預算或證明。

![](assets/s_ncs_user_task_new_control.png)

任務建立後，即會新增至行銷活動控制面板。

![](assets/s_ncs_user_task_edit_from_board.png)

然後您可以編輯並指定其引數。

### 行銷資源建立任務 {#marketing-resource-creation-task}

行銷資源建立任務可用於管理行銷資源的建立和發佈。 如果您是透過任務而非透過資源本身管理資源，您可以：

* 透過行銷活動控制資源建立流程。
* 檢視排程中的資源建立程式。
* 管理資源建立程式（提醒、通知）。
* 計算並控制連結到資源建立的成本。
* 透過任務核准並發佈資源（如果已啟用相關選項）。

#### 任務與其連結的資源之間的互動 {#interaction-between-the-task-and-its-linked-resource}

行銷資源建立任務會與連結至它的資源互動。 這表示：

* 資源建立排程及連結至該排程的成本會透過任務來管理。
* 操作員可在資源上正常運作（下載或上傳、鎖定和解除鎖定）：這不會影響工作。
* 可透過任務執行資源核准和發佈：如果 **[!UICONTROL Publish the marketing resource]** 選項已啟用，資源會在任務完成後自動核准和發佈。 如果未啟用此選項，則任務和資源不會互動：對一個專案執行動作不會影響另一個專案。

  您可以使用一系列連結的工作來定義完整的核准週期。 檢查 **[!UICONTROL Publish the marketing resource]** 僅用於最後一個任務的選項：所有任務都需要完成才能發佈資源。 此外，當您建立子行銷資源任務時，將會自動在子任務中選取資源。

   * **透過資源**：如果您提交資源以供核准或核准，這些動作將不會影響任務。
   * **透過任務**：如果 **[!UICONTROL Publish the marketing resource]** 選項在任務中核取，資源會在任務完成後自動核准和發佈（請參閱上文）。 如果未核取選項，則任務與資源不會互動：對一個專案執行動作不會影響另一個專案。

#### 設定行銷資源建立任務 {#configuring-a-marketing-resource-creation-task}

檢閱任務的人不必是檢閱資源中定義內容的同一個人。 但是，如果 **[!UICONTROL Publish the marketing resource]** 核取選項（見下文），任務稽核者被授權核准資源內容，因為完成任務會自動核准資源（如果未定義稽核者，則為任務管理員）。

![](assets/mrm_task_asset_creation.png)

在 **[!UICONTROL Marketing resource]** 欄位，定義您要透過此任務管理的資源。 您可以：

* 選取現有資源：下拉式清單會提供具有狀態的所有資源 **[!UICONTROL Being edited]**.
* 建立資源：按一下 **[!UICONTROL Select the link]** 圖示，然後按一下 **[!UICONTROL Create]** 圖示。

此 **[!UICONTROL Publish the marketing resource]** 選項可讓您自動發佈資源：一旦任務完成 **[!UICONTROL Finished]**，資源的狀態會自動切換為 **[!UICONTROL Published]**，即使未提交核准或未核准，包括完成任務的稽核者不是資源中定義的內容稽核者。

此 **[!UICONTROL Publish the resource]** 按鈕可供使用，資源發佈稽核者會收到通知電子郵件，通知他們該按鈕已準備好發佈。 在 **[!UICONTROL Edit > Tracking]** 標籤，任務檢閱者的檢閱和發佈會變為可見。 如果已定義資源後處理工作流程，則會立即執行。

![](assets/mrm_resource_audit_tab.png)

### 群組任務 {#grouping-task}

此 **[!UICONTROL Grouping task]** 型別任務可讓您將數個任務組成群組，並同步管理其進度與核准。

群組任務沒有連結的費用或資源。

分組到分組任務的所有任務都可以在自己的儀表板上看到。 這可讓您篩選任務清單，以僅顯示您感興趣的任務。

分組任務具有一個連結，可讓您輕鬆建立分組任務。

若要根據分組任務建立分組任務，請移至行銷活動控制面板，按一下分組任務的名稱以顯示其說明，然後按一下 **[!UICONTROL Add a task]**.

![](assets/mrm_task_grouped_create.png)

不過，如果您已建立要連結至分組任務的任務，則可透過 **[!UICONTROL Linked to]** 欄位屬於 **[!UICONTROL Properties]** 方塊。

![](assets/s_ncs_user_task_group_with.png)

### 通知任務 {#notification-task}

通知工作可讓您排程電子郵件傳送（傳送給操作員、操作員群組、服務提供者等）。 這可讓您排程提醒，例如，通知某人行銷活動即將完成，或在行銷活動開始之前傳送檔案，以便操作員進行準備。 這表示您可以追蹤行銷活動或方案中的通訊，並更密切地關注已執行的動作。

#### 生命週期 {#life-cycle}

通知工作不需要核准。 這表示它們的生命週期比標準任務的生命週期更簡單：

![](assets/mrm_task_notif_lifecycle.png)

通知任務可以有下列狀態：

* **[!UICONTROL Scheduled]** 在傳送電子郵件之前
* **[!UICONTROL In progress]** 傳送電子郵件之後，並直到到達結束日期為止
* **[!UICONTROL Finished]** 一旦到達結束日期。

#### 設定 {#configuration}

![](assets/mrm_task_notif_dashboard.png)

建立期間，必須在任務中輸入下列元素：

* **[!UICONTROL Assigned to]** ：將收到電子郵件的操作員或操作員群組。 如果您在傳送電子郵件後重新指派任務，則不會將電子郵件傳送給新運運算元（若要這樣做，您需要重新初始化任務並變更其開始日期）。
* **任務開始日期**：傳送通知電子郵件的日期。 此日期必須在未來錄製任務時發生。
* **任務結束日期**：任務狀態變更的日期 **[!UICONTROL Finished]**. 依預設，結束日期與開始日期相同。 不過，為任務指派工期可讓您在必要時象徵運運算元必須在排程中執行的時間量。
* **[!UICONTROL Description]** ：此處輸入的文字會出現在通知電子郵件的內文中。

  ![](assets/mrm_task_notif_dashboard_msg.png)

您可以將附件新增至工作及通知電子郵件。 若要這麼做，請按一下 **[!UICONTROL Documents]** 圖示加以調整。

## 生命週期 {#life-cycle-1}

### 任務之間的連結 {#links-between-tasks}

此 **[!UICONTROL Properties]** 每個任務中的按鈕可讓您定義行銷活動中任務之間的連結。 您可以使用分組任務將任務分割為子任務(請參閱 [連結的任務](#linked-tasks))，或定義工作之間的相依性(請參閱 [分組任務](#grouping-tasks))。

#### 連結的任務 {#linked-tasks}

使用 **[!UICONTROL Linked task]** 要將任務與分組任務相關聯的欄位。 另請參閱 [任務型別](#types-of-task).

在下列範例中，目標定位的核准會分成四個子任務。

![](assets/s_ncs_user_task_linked_tasks.png)

每個子任務都是連結至主要任務的標準任務。

![](assets/s_ncs_user_task_depends_on.png)

#### 群組任務 {#grouping-tasks}

使用 **[!UICONTROL Grouped to]** 使任務的執行取決於另一個任務的執行的欄位。

![](assets/s_ncs_user_task_group_with.png)

任務之間的相依性以行銷活動控制面板中的箭頭表示。

![](assets/s_ncs_user_task_dependencies_from_board.png)

若為已分組的任務，Adobe Campaign會自動將父任務的結束日期指派給子任務，作為開始日期。 例如，如果 **建立邀請** 工作於10月15日下午3:30結束， **傳送邀請電子郵件** 子任務將於10月15日下午3:30開始。

此外，如果延遲父系任務的結束，其某些子系任務可能會受到影響：這些是狀態為 **[!UICONTROL Scheduled]** 且其開始日期早於父系任務的新結束日期。 任務的持續時間保持不變。 如果子任務的開始日期晚於父任務的新結束日期，則子任務不受影響。

**範例**

排定於10月9日下午5點結束的父系任務有兩個子系任務，即任務A和任務B。任務A排定於10月10日下午2點開始，任務B排定於10月12日上午8點開始。

讓我們延遲父系任務：現在於10月11日下午1點結束。 只有任務A會延遲，10月11日下午1點開始。

![](assets/mrm_task_parent_postpones_child.png)

### 任務的執行狀態 {#execution-status-of-a-task}

任務狀態可在任務地圖中檢視。 任務的執行狀態會根據運運算元動作自動更新。

任務可以是： **[!UICONTROL Scheduled]**， **[!UICONTROL In progress]**， **[!UICONTROL Finished]**， **[!UICONTROL Canceled]**， **[!UICONTROL Pending approval]** 或 **[!UICONTROL Rejected]**.

* 建立任務時，它 **[!UICONTROL Scheduled]** 若其開始日期為未來。 它會保持此狀態，直到到達開始日期為止。
* 一旦開始執行，任務就是 **[!UICONTROL In progress]**. 當任務負責人關閉時，任務會變更為 **[!UICONTROL Finished]**.
* 若已定義稽核者，則任務為 **[!UICONTROL Pending approval]** 一旦負責人關閉它，直到稽核者核准它為止。 如果稽核者拒絕，則任務將為 **[!UICONTROL Rejected]**.
* 任務可由負責人員透過控制面板或 **[!UICONTROL Task map]** 按一下 **[!UICONTROL Cancel]** 按鈕。
* 若要排程工作，請輸入未來的開始日期。 接著，您就可以傳送第一則通知給參與執行工作的Adobe Campaign運運算元。 另請參閱 [完成任務生命週期](#complete-task-life-cycle).

>[!NOTE]
>
>* 任務狀態會自動更新。
>* 即使有效期已完成，未關閉的任務仍會出現在進行中的任務清單中。 警告會通知操作員任務已延遲。
>

### 任務的進度狀態 {#progress-status-of-a-task}

除了其執行狀態之外，任務還可以與進度狀態相關聯： **[!UICONTROL Late]**， **[!UICONTROL To approve]**， **[!UICONTROL To do today]** 或 **[!UICONTROL To do this week]**. 此資訊會根據工作排程自動輸入。

您可以依流程或進度狀態來篩選工作清單。

有關詳細資訊，請參閱 [存取任務](#accessing-tasks).

### 完成任務生命週期 {#complete-task-life-cycle}

以下為負責人員已定義參與者和稽核者之完整任務生命週期的階段。

1. 負責人建立任務並輸入各個欄位。 有關詳細資訊，請參閱 [建立新任務](#creating-a-new-task).

   建立和編輯任務時 **排程於未來時間** （只要未到達任務開始日期），您就可以傳送通知給參與者和管理者，讓他們知道已排程新任務。

   ![](assets/s_ncs_user_task_planed_send_message.png)

   若要傳送第一個通知，請按一下 **[!UICONTROL Yes]**. 此通知會告知他們下一個任務的相關資訊，並包含內容的詳細資訊以及到截止日期前的剩餘天數。

   當任務建立並排程於未來時，其狀態為 **[!UICONTROL Scheduled]**.

1. 在任務開始日期時，負責人和參與者會收到通知，告知他們任務已開始。 其狀態變更為 **[!UICONTROL In progress]**.
1. 完成指派給他們的區段後，參與者可以核准任務：

   * 透過通知電子郵件。
   * 透過主控台或web介面，在任務控制面板中。

     ![](assets/s_ncs_user_task_start_rea.png)

1. 每次參與者核准工作時，任務的進度狀態都會更新。

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. 稽核者會收到通知電子郵件，告知操作員已完成指派給他們的區段。

   他們可以追蹤任務控制面板上的進度。

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. 一旦負責任務的人確定任務已完成，他們可以使用任務啟動時傳送的通知電子郵件中的連結、主控台或介面將其關閉。

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >任務負責人可以隨時關閉任務，即使缺少核准也是如此。 進度狀態會自動變更為100%。

1. 任務狀態變更為 **[!UICONTROL To approve]**，並會傳送通知給檢閱者。

   他們透過通知電子郵件、主控台或網頁介面核准任務。

   他們可以透過行銷活動儀表板採取行動：

   ![](assets/s_ncs_user_task_console_validation.png)

   他們也可以使用任務核准按鈕：

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >任務狀態將只會變更為 **[!UICONTROL To approve]** 如果您已啟用 **[!UICONTROL Enable task validation]** 中的選項 **[!UICONTROL Resources]** 工作的視窗。\
   >如果檢閱者拒絕任務，其狀態會變更為 **[!UICONTROL Rejected]**，則任務生命週期會再次自動開始。

1. 任務狀態變更為 **[!UICONTROL Finished]**. 會傳送通知給每個相關人員。

   >[!NOTE]
   >
   >一旦任務完成，其生命週期可由負責該任務的人重新初始化。 若要這麼做，請開啟工作並按一下 **[!UICONTROL Reset task to execute it again...]** 控制面板底部的連結。
