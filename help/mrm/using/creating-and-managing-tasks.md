---
product: campaign
title: 建立及管理任務
description: 建立及管理任務
feature: Resource Management
audience: campaign
content-type: reference
hide: true
hidefromtoc: true
topic-tags: tasks--resources-and-budgets
exl-id: cc1200fa-f6d8-4f41-aed1-d1a7f229447a
source-git-commit: 942edcf028207eab2ea583949ebc99ab61539ea0
workflow-type: tm+mt
source-wordcount: '3743'
ht-degree: 0%

---

# 建立及管理設定檔{#creating-and-managing-tasks}



Adobe Campaign可讓您直接在應用程式中建立任務並管理其完整的生命週期。 方案和行銷活動實作可以細分為指派給Adobe Campaign操作員或外部服務提供者的任務。 此作業模式可讓您建立包含所有方案參與者和外部參與者的開放式共同作業環境。

您可以從任務清單或行銷活動控制面板建立、檢視及監控任務。 您也可以在行銷計畫、方案和行銷活動的排程中檢視和追蹤這些活動。

任務會附加至行銷活動，且可以具有相依性，即相關任務。 每個任務都有狀態、優先順序、預估負載和相關成本。

所有任務都分組在可透過&#x200B;**行銷活動**&#x200B;索引標籤存取的清單中。 如需詳細資訊，請參閱[存取工作](#accessing-tasks)。

它們可以顯示在所屬方案的排程中。

![](assets/d_ncs_user_tasks_in_planning.png)

## 存取任務 {#accessing-tasks}

### 顯示任務 {#displaying-tasks}

任務會顯示在可透過&#x200B;**[!UICONTROL Campaigns]**&#x200B;索引標籤存取的工作清單中。

![](assets/s_ncs_user_task_edit_view.png)

您可以在此檢視連線運運算元的所有工作。

如需詳細資訊，請參閱[任務的執行狀態](#execution-status-of-a-task)和[任務的進度狀態](#progress-status-of-a-task)。

### 篩選任務 {#filtering-tasks}

當您顯示此檢視時，系統會自動篩選檢視以僅顯示&#x200B;**[!UICONTROL operator tasks]**。 您也可以使用視窗上半部分的欄位來篩選任務。

![](assets/s_ncs_user_task_filter_from_view.png)

### 編輯任務 {#editing-tasks}

按一下工作以進行編輯。

![](assets/s_ncs_user_task_edit_from_view.png)

## 建立新任務 {#creating-a-new-task}

若要建立任務，請按一下&#x200B;**[!UICONTROL Campaigns]**&#x200B;索引標籤中的&#x200B;**[!UICONTROL Tasks]**&#x200B;連結，然後選取&#x200B;**[!UICONTROL Create]**。

![](assets/s_ncs_user_task_create_new.png)

至少輸入任務的名稱，並選取它連結到的行銷活動。 您也必須指定開始和結束日期。 這三則資訊屬於必要資訊。

按一下&#x200B;**[!UICONTROL Save]**&#x200B;以建立工作。

![](assets/s_ncs_user_task_create_simple.png)

您也可以透過行銷活動的控制面板建立任務：在這種情況下，會自動連結至建立該行銷活動的來源。

![](assets/s_ncs_user_task_create_new_from_op.png)

建立任務後，會將其新增至行銷活動排程和任務清單。 若要編輯任務，請從排程中選取該任務，或在任務概述中按一下其名稱，然後按一下&#x200B;**[!UICONTROL Open]**&#x200B;連結。

![](assets/s_ncs_user_task_edit_simple.png)

若要進行設定，您必須指出：

* 管理員與參與者：請參閱[管理員與參與者](#manager-and-participants)。
* 建立排程：請參閱[執行排程](#execution-schedule)。
* 已確認成本：請參考[費用與收入](#expenses-and-revenues)。

也可以新增稽核者（請參閱[稽核者](#reviewers)）和參考的檔案（請參閱[參考的檔案](#documents-referenced)）。

在[生命週期](#life-cycle)中顯示任務生命週期。

### 經理與參與者 {#manager-and-participants}

只有負責任務的操作員才有權關閉任務。

根據預設，當Adobe Campaign運運算元建立任務時，會自動指派給他們。 若要選取其他運運算元，請使用&#x200B;**[!UICONTROL Assigned to]**&#x200B;欄位。

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>運運算元管理顯示在[此區段](../../platform/using/access-management.md)中。

您可以指定執行任務時涉及的操作者。 這些操作者無權關閉任務。 他們只能核准指派給他們的任務。

使用任務工具列中的&#x200B;**[!UICONTROL Resources]**&#x200B;圖示來選取它們。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取相關運運算元。

![](assets/s_ncs_user_task_add_resources.png)

按一下&#x200B;**[!UICONTROL Ok]**，然後輸入使用率：這代表工作執行期間指派給運運算元的負載。 此比率僅供參考，並以百分比表示。

例如，對於執行排程設定為10天的工作，使用率為50%的運運算元將會在此任務上動員10天一半的工作時間。

對於每個運運算元，您可以輸入排程工作負載與實際工作負載。 這些持續時間也僅供參考。

您可以設定提醒，提醒會在任務結束日期之前自動傳送給所有參與工作的操作者。

您可以透過&#x200B;**[!UICONTROL Edit link]**&#x200B;圖示檢視Adobe Campaign運運算元設定檔。

![](assets/s_ncs_user_task_edit_resource_profile.png)

操作員儀表板可讓您檢查其工作量（其他進行中的任務）。

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 檢閱者 {#reviewers}

除了參與者之外，您還可以定義作業執行者，當作業執行者關閉作業後，他們將會複查作業。 若要這麼做，請按一下&#x200B;**[!UICONTROL Resources]**&#x200B;視窗左下角的&#x200B;**[!UICONTROL Enable task approval]**&#x200B;選項。 這可以是個別運運算元、一組運運算元或運運算元清單。

![](assets/s_ncs_user_task_edit_resource_validation.png)

若要指定運運算元清單，請按一下第一個檢閱者右側的&#x200B;**[!UICONTROL Edit...]**&#x200B;連結，並視需要新增運運算元，如下所示：

![](assets/s_ncs_user_task_edit_resource_operators.png)

您可以在檢閱者組態視窗的下半部定義任務的核准排程。 依預設，稽核者從提交日期起有三天可核准任務。 您可以設定提醒，提醒會在核准截止日期前自動傳送給相關操作者。

![](assets/s_ncs_user_edit_op_valid_calendar.png)

任務負責人可以指派自己核准任務，即使已指派其他操作員進行此工作。 如果尚未定義稽核者，則會將通知傳送給負責任務的人。 其他所有具有&#x200B;**[!UICONTROL Administrator]**&#x200B;許可權的Adobe Campaign運運算元也可以核准任務。 但他們不會收到通知。

### 引用的檔案 {#documents-referenced}

您可以將檔案和行銷資源新增至任務（如需詳細資訊，請參閱[管理行銷資源](../../mrm/using/managing-marketing-resources.md)）。 若要這麼做，請開啟工作並按一下工作工具列中的&#x200B;**[!UICONTROL Documents]**&#x200B;圖示。

按一下&#x200B;**[!UICONTROL Add]**&#x200B;並選取要新增至您工作的檔案。 對行銷資源套用相同程式。

![](assets/s_ncs_user_task_edit_documents.png)

參考的檔案會顯示在傳送給工作相關操作員的通知中，也會顯示在工作控制面板上。

![](assets/s_ncs_user_task_notification_documents.png)

### 執行排程 {#execution-schedule}

任務的有效期顯示在&#x200B;**[!UICONTROL Start]**&#x200B;和&#x200B;**[!UICONTROL End]**&#x200B;欄位中。 排定的負載表示要在此期間執行的工作負載。 以天或小時表示。

>[!NOTE]
>
>任務的生命週期會顯示在[生命週期](#life-cycle)中。

**[!UICONTROL Workload performed]**&#x200B;欄位也以天和小時表示，可讓您手動更新與排程工作負載相關的任務進度。

![](assets/s_ncs_user_task_percentage_done_enter.png)

工作&#x200B;**[!UICONTROL Progress status]** （以百分比表示）會根據相關操作員所執行的工作自動更新。 可以手動輸入。

可在任務儀表板中檢視此資訊。

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

它也會顯示在行銷活動標籤中。

![](assets/s_ncs_user_task_percentage_done_from_op.png)

如果已達到任務執行排程結束日期，但任務尚未完成，則任務將是&#x200B;**[!UICONTROL Late]**。 警告訊息也會顯示給警示操作者。

有關詳細資訊，請參閱[任務的進度狀態](#progress-status-of-a-task)。

### 費用與收入 {#expenses-and-revenues}

您可以定義每個作業的相關費用與預測收入。 系統會計算這些值，然後針對附加任務的行銷活動將其合併。

若要指定此資訊，請按一下工作工具列中的&#x200B;**[!UICONTROL Expenses and revenue]**&#x200B;圖示。

![](assets/s_ncs_user_task_edit_costs.png)

依預設，收取的預算是附加任務的行銷活動的預算。 它會顯示在任務詳細資訊中。

>[!NOTE]
>
>如需費用與預算的詳細資訊，請參閱[成本承諾、計算與費用](../../mrm/using/controlling-costs.md#cost-commitment--calculation-and-charging)。

在此視窗中，您也可以定義要達成的目標。 目標會以任務的預測收入表示。

### 服務提供者 {#service-providers}

外部服務提供者可參與工作的管理。

若要這麼做，請編輯工作屬性，並選取相關的服務提供者。 與服務提供者相關的成本類別會自動列在視窗的中央區段中。

如需詳細資訊，請參閱[建立服務提供者及其成本類別](../../campaign/using/providers-stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

選取與作業執行相關的成本類別。 若要這麼做，請選取成本型態，並視需要新增附加費金額。

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>管理預算與成本的方法在[控制成本](../../mrm/using/controlling-costs.md)中顯示。

選取服務提供者時，它會顯示在工作儀表板中：

![](assets/s_ncs_user_task_supplier_view.png)

### 延遲任務 {#late-tasks}

如果任務已達到其結束日期且其狀態未變更為&#x200B;**[!UICONTROL Finished]**，則任務會延遲。 依預設，當任務延遲時，不會警告任何運運算元。 您可以設定通知電子郵件的傳送：即使操作員未參與工作，也可以通知所有操作員。

移至&#x200B;**[!UICONTROL Resources]**&#x200B;方塊並將運運算元新增至&#x200B;**[!UICONTROL Assignation]**&#x200B;欄位。 若要通知幾個人，請選取一組操作員。

![](assets/mrm_task_alert_if_late.png)

### 初始通知 {#initial-notifications}

當您建立或修改具有未來開始日期的任務時，Adobe Campaign會提供傳送電子郵件給負責任務的人，讓他們知道何時開始。

![](assets/mrm_task_first_notif.png)

但是，如果您要建立的任務還很遙遠，最好在任務開始之前排程要傳送的通知。 例如，如果工作在一個月後開始，您可以通知負責人員，時間早於工作開始的一週。

若要排程通知，請移至&#x200B;**[!UICONTROL Resources]**&#x200B;方塊並使用&#x200B;**[!UICONTROL Initial notification]**&#x200B;欄位。

![](assets/mrm_task_alert_before.png)

* 針對行銷活動內的任務，選取特定的日期和時間。
* 對於行銷活動範本內的任務，通知時間以任務開始前的剩餘時間表示（例如，如果您在「**[!UICONTROL Initial notification]**」欄位中輸入2d，則會在任務開始日期前2天傳送電子郵件）。

如果您已排程通知，當您儲存任務時，Adobe Campaign仍會提供立即傳送通知的功能。 您可以決定傳送，這不會取代排程通知。

### 連結至方案的任務 {#task-linked-to-a-program}

您可以直接在方案中建立任務，以管理與其整體組織相關的動作，而不是與特定行銷活動相關的動作（例如，討論方案中即將開展行銷活動主題的會議）。 任務會出現在方案排程中。

若要建立直接連結至方案的工作：

1. 開啟方案排程：在首頁上，移至&#x200B;**[!UICONTROL Campaigns > Browse > Other choices > Programs]**。 整個方案排程會在視窗的右側區段中開啟。
1. 在排程中，按一下所需的方案：一個視窗會提供其中方案。
1. 在此視窗中，按一下&#x200B;**[!UICONTROL Open]**。 方案排程隨即開啟。
1. 按一下右側排程上方的&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後按一下&#x200B;**[!UICONTROL Add a task]**。

![](assets/mrm_task_create_from_prg.png)

### 操作員可用性 {#operator-availability}

在任務儀表板中，操作員名稱旁邊的圖示表示他們已在任務所涵蓋的期間處理另一個任務或事件。 運運算元負責或參與的任務會出現在&#x200B;**[!UICONTROL Assigned to]**&#x200B;欄位或任務&#x200B;**[!UICONTROL Resources]**&#x200B;方塊中。

![](assets/mrm_task_alert_operator_busy.png)

### 工作流程中的任務 {#task-in-a-workflow}

在行銷活動工作流程中使用&#x200B;**[!UICONTROL Task]**&#x200B;元素可讓您根據任務是否核准來定義兩個案例。

![](assets/mrm_task_in_workflow.png)

在行銷活動工作流程中，**[!UICONTROL Task]**&#x200B;活動可在&#x200B;**[!UICONTROL Flow control]**&#x200B;索引標籤中找到。

## 任務型別 {#types-of-task}

當您透過行銷活動建立任務時，可以建立特定任務。 任務型別在所選範本中定義。

![](assets/s_ncs_user_task_select_template.png)

可以排程下列工作：

* [控制任務](#control-tasks)，
* [分組任務](#grouping-task)，
* [分組任務](#grouping-task)，
* [通知工作](#notification-task)。

>[!NOTE]
>
>**[!UICONTROL Control task]**&#x200B;和&#x200B;**[!UICONTROL Grouping]**&#x200B;任務只能&#x200B;**透過行銷活動儀表板建立**。\
>它們會顯示在指派給它們的運運算元的工作圖中。 檢視[存取工作](#accessing-tasks)。

### 控制任務 {#control-tasks}

**[!UICONTROL Control task]**&#x200B;連結至傳遞核准：核准目標、內容、擷取檔案、預算或證明。

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
* 資源核准與發佈可透過工作執行：如果啟用&#x200B;**[!UICONTROL Publish the marketing resource]**&#x200B;選項，則資源會在工作完成後自動核准與發佈。 如果未啟用此選項，則任務和資源不會互動：對一個專案執行動作不會影響另一個專案。

  您可以使用一系列連結的工作來定義完整的核准週期。 僅針對最後一個任務核取&#x200B;**[!UICONTROL Publish the marketing resource]**&#x200B;選項：所有任務都需要完成才能發佈資源。 此外，當您建立子行銷資源任務時，將會自動在子任務中選取資源。

   * **透過資源**：如果您提交資源以供核准或核准，這些動作將不會影響工作。
   * **透過工作**：如果工作中的&#x200B;**[!UICONTROL Publish the marketing resource]**&#x200B;選項已核取，則資源會在工作完成後自動核准和發佈（請參閱上文）。 如果未核取選項，則任務與資源不會互動：對一個專案執行動作不會影響另一個專案。

#### 設定行銷資源建立任務 {#configuring-a-marketing-resource-creation-task}

檢閱任務的人不必是檢閱資源中定義內容的同一個人。 但是，如果核取&#x200B;**[!UICONTROL Publish the marketing resource]**&#x200B;選項（請參閱下文），則授權任務稽核者核准資源內容，因為完成任務會自動核准資源（如果未定義稽核者，則授權任務管理員）。

![](assets/mrm_task_asset_creation.png)

在&#x200B;**[!UICONTROL Marketing resource]**&#x200B;欄位中，定義您要透過此任務管理的資源。 您可以：

* 選取現有資源：下拉式清單會提供狀態為&#x200B;**[!UICONTROL Being edited]**&#x200B;的所有資源。
* 建立資源：按一下&#x200B;**[!UICONTROL Select the link]**&#x200B;圖示，然後按一下&#x200B;**[!UICONTROL Create]**&#x200B;圖示。

**[!UICONTROL Publish the marketing resource]**&#x200B;選項可讓您自動發佈資源：一旦任務為&#x200B;**[!UICONTROL Finished]**，資源的狀態會自動切換為&#x200B;**[!UICONTROL Published]**，即使它既未提交核准也未核准，包括完成任務的稽核者不是資源中定義的內容稽核者時。

**[!UICONTROL Publish the resource]**&#x200B;按鈕可供使用，資源發佈稽核者會收到通知電子郵件，通知他們該按鈕已準備好發佈。 在&#x200B;**[!UICONTROL Edit > Tracking]**&#x200B;索引標籤中，工作稽核者的稽核和發佈會變為可見。 如果已定義資源後處理工作流程，則會立即執行。

![](assets/mrm_resource_audit_tab.png)

### 群組任務 {#grouping-task}

**[!UICONTROL Grouping task]**&#x200B;型別任務可讓您將數個任務組成群組，並同步管理其進度與核准。

群組任務沒有連結的費用或資源。

分組到分組任務的所有任務都可以在自己的儀表板上看到。 這可讓您篩選任務清單，以僅顯示您感興趣的任務。

分組任務具有一個連結，可讓您輕鬆建立分組任務。

若要根據分組任務建立分組任務，請移至行銷活動控制面板，按一下分組任務的名稱以顯示其說明，然後按一下&#x200B;**[!UICONTROL Add a task]**。

![](assets/mrm_task_grouped_create.png)

不過，如果您已建立要連結至分組任務的任務，則可透過&#x200B;**[!UICONTROL Properties]**&#x200B;方塊的&#x200B;**[!UICONTROL Linked to]**&#x200B;欄位進行連結。

![](assets/s_ncs_user_task_group_with.png)

### 通知任務 {#notification-task}

通知工作可讓您排程電子郵件傳送（傳送給操作員、操作員群組、服務提供者等）。 這可讓您排程提醒，例如，通知某人行銷活動即將完成，或在行銷活動開始之前傳送檔案，以便操作員進行準備。 這表示您可以追蹤行銷活動或方案中的通訊，並更密切地關注已執行的動作。

#### 生命週期 {#life-cycle}

通知工作不需要核准。 這表示它們的生命週期比標準任務的生命週期更簡單：

![](assets/mrm_task_notif_lifecycle.png)

通知任務可以有下列狀態：

* 在傳送電子郵件之前&#x200B;**[!UICONTROL Scheduled]**
* 在傳送電子郵件後&#x200B;**[!UICONTROL In progress]**&#x200B;並到達結束日期之前
* 一旦到達結束日期&#x200B;**[!UICONTROL Finished]**。

#### 設定 {#configuration}

![](assets/mrm_task_notif_dashboard.png)

建立期間，必須在任務中輸入下列元素：

* **[!UICONTROL Assigned to]** ：將收到電子郵件的操作員或操作員群組。 如果您在傳送電子郵件後重新指派任務，則不會將電子郵件傳送給新運運算元（若要這樣做，您需要重新初始化任務並變更其開始日期）。
* **任務開始日期**：傳送通知電子郵件的日期。 此日期必須在未來錄製任務時發生。
* **任務結束日期**：任務狀態變更為&#x200B;**[!UICONTROL Finished]**&#x200B;的日期。 依預設，結束日期與開始日期相同。 不過，為任務指派工期可讓您在必要時象徵運運算元必須在排程中執行的時間量。
* **[!UICONTROL Description]** ：此處輸入的文字會出現在通知電子郵件的內文中。

  ![](assets/mrm_task_notif_dashboard_msg.png)

您可以將附件新增至工作及通知電子郵件。 若要這麼做，請按一下右上角工具列中的&#x200B;**[!UICONTROL Documents]**&#x200B;圖示。

## 生命週期 {#life-cycle-1}

### 任務之間的連結 {#links-between-tasks}

每個任務中的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕可讓您定義行銷活動中任務之間的連結。 您可以使用分組任務將任務分割為子任務（請參閱[連結的任務](#linked-tasks)），或定義任務之間的相依性（請參閱[分組任務](#grouping-tasks)）。

#### 連結的任務 {#linked-tasks}

使用&#x200B;**[!UICONTROL Linked task]**&#x200B;欄位將任務與分組任務相關聯。 檢視[工作型別](#types-of-task)。

在下列範例中，目標定位的核准會分成四個子任務。

![](assets/s_ncs_user_task_linked_tasks.png)

每個子任務都是連結至主要任務的標準任務。

![](assets/s_ncs_user_task_depends_on.png)

#### 群組任務 {#grouping-tasks}

使用&#x200B;**[!UICONTROL Grouped to]**&#x200B;欄位讓任務的執行取決於另一個任務的執行。

![](assets/s_ncs_user_task_group_with.png)

任務之間的相依性以行銷活動控制面板中的箭頭表示。

![](assets/s_ncs_user_task_dependencies_from_board.png)

若為已分組的任務，Adobe Campaign會自動將父任務的結束日期指派給子任務，作為開始日期。 舉例來說，如果&#x200B;**建立邀請**&#x200B;工作於10月15日下午3:30結束，**傳送邀請電子郵件**&#x200B;子工作將於10月15日下午3:30開始。

此外，如果您延遲父系任務的結束，其部分子系任務可能會受到影響：這些是狀態為&#x200B;**[!UICONTROL Scheduled]**&#x200B;且開始日期早於父系任務新結束日期的子系任務。 任務的持續時間保持不變。 如果子任務的開始日期晚於父任務的新結束日期，則子任務不受影響。

**範例**

排定於10月9日下午5點結束的父系任務有兩個子系任務，即任務A和任務B。任務A排定於10月10日下午2點開始，任務B排定於10月12日上午8點開始。

讓我們延遲父系任務：現在於10月11日下午1點結束。 只有任務A會延遲，10月11日下午1點開始。

![](assets/mrm_task_parent_postpones_child.png)

### 任務的執行狀態 {#execution-status-of-a-task}

任務狀態可在任務地圖中檢視。 任務的執行狀態會根據運運算元動作自動更新。

任務可以是： **[!UICONTROL Scheduled]**、**[!UICONTROL In progress]**、**[!UICONTROL Finished]**、**[!UICONTROL Canceled]**、**[!UICONTROL Pending approval]**&#x200B;或&#x200B;**[!UICONTROL Rejected]**。

* 建立任務時，如果開始日期在未來，則為&#x200B;**[!UICONTROL Scheduled]**。 它會保持此狀態，直到到達開始日期為止。
* 啟動之後，工作就會是&#x200B;**[!UICONTROL In progress]**。 當任務負責人關閉時，它會變更為&#x200B;**[!UICONTROL Finished]**。
* 如果已定義稽核者，則當負責該任務的人關閉它並直到稽核者核准它之前，該任務將為&#x200B;**[!UICONTROL Pending approval]**。 如果檢閱者拒絕，則任務為&#x200B;**[!UICONTROL Rejected]**。
* 任務負責人可透過儀表板或&#x200B;**[!UICONTROL Task map]**&#x200B;按一下&#x200B;**[!UICONTROL Cancel]**&#x200B;按鈕來取消任務。
* 若要排程工作，請輸入未來的開始日期。 接著，您就可以傳送第一則通知給參與執行工作的Adobe Campaign運運算元。 請參閱[完成任務生命週期](#complete-task-life-cycle)。

>[!NOTE]
>
>* 任務狀態會自動更新。
>* 即使有效期已完成，未關閉的任務仍會出現在進行中的任務清單中。 警告會通知操作員任務已延遲。
>

### 任務的進度狀態 {#progress-status-of-a-task}

除了其執行狀態之外，工作還可以與進度狀態相關聯： **[!UICONTROL Late]**、**[!UICONTROL To approve]**、**[!UICONTROL To do today]**&#x200B;或&#x200B;**[!UICONTROL To do this week]**。 此資訊會根據工作排程自動輸入。

您可以依流程或進度狀態來篩選工作清單。

如需詳細資訊，請參閱[存取工作](#accessing-tasks)。

### 完成任務生命週期 {#complete-task-life-cycle}

以下為負責人員已定義參與者和稽核者之完整任務生命週期的階段。

1. 負責人建立任務並輸入各個欄位。 如需詳細資訊，請參閱[建立新工作](#creating-a-new-task)。

   當在未來&#x200B;**建立及編輯工作**&#x200B;排程時（只要未到達工作開始日期），可以傳送通知給參與者和管理員，讓他們知道已排程新工作。

   ![](assets/s_ncs_user_task_planed_send_message.png)

   若要傳送第一個通知，請按一下&#x200B;**[!UICONTROL Yes]**。 此通知會告知他們下一個任務的相關資訊，並包含內容的詳細資訊以及到截止日期前的剩餘天數。

   當任務建立並排程於未來時，其狀態為&#x200B;**[!UICONTROL Scheduled]**。

1. 在任務開始日期時，負責人和參與者會收到通知，告知他們任務已開始。 其狀態變更為&#x200B;**[!UICONTROL In progress]**。
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

1. 工作狀態變更為&#x200B;**[!UICONTROL To approve]**，並傳送通知給檢閱者。

   他們透過通知電子郵件、主控台或網頁介面核准任務。

   他們可以透過行銷活動儀表板採取行動：

   ![](assets/s_ncs_user_task_console_validation.png)

   他們也可以使用任務核准按鈕：

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >只有在您已在任務的&#x200B;**[!UICONTROL Resources]**&#x200B;視窗中啟用&#x200B;**[!UICONTROL Enable task validation]**&#x200B;選項時，任務狀態才會變更為&#x200B;**[!UICONTROL To approve]**。\
   >如果檢閱者拒絕任務，其狀態會變更為&#x200B;**[!UICONTROL Rejected]**，且任務生命週期會自動重新開始。

1. 任務狀態變更為&#x200B;**[!UICONTROL Finished]**。 會傳送通知給每個相關人員。

   >[!NOTE]
   >
   >一旦任務完成，其生命週期可由負責該任務的人重新初始化。 若要這麼做，請開啟工作並按一下控制面板底部的&#x200B;**[!UICONTROL Reset task to execute it again...]**&#x200B;連結。
