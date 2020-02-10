---
title: 建立和管理任務
seo-title: 建立和管理任務
description: 建立和管理任務
seo-description: null
page-status-flag: never-activated
uuid: 1d219ae4-1ca9-42cb-a49e-2b647520bda0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: campaign
content-type: reference
topic-tags: tasks--resources-and-budgets
discoiquuid: d71e5ff7-1e81-4c49-9673-c6fae890029b
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 建立和管理任務{#creating-and-managing-tasks}

## 關於任務 {#about-tasks}

Adobe Campaign可讓您直接在應用程式中建立工作並管理其完整生命週期。 方案和促銷活動實作可細分為指派給Adobe Campaign營運商或外部服務供應商的工作。 此操作模式可讓您建立開放的協作環境，其中包括所有方案參與者和外部參與者。

可從工作清單或促銷活動控制面板建立、檢視和監控工作。 您也可以在行銷計畫、方案和促銷活動的排程中檢視和追蹤這些項目。

任務會附加至促銷活動，並且可以具有相依性，即相關任務。 每個任務都有狀態、優先順序、估計負載和相關成本。

所有工作都會分組在可透過「促銷活動」範圍存取的 **清單中** 。 For more on this, refer to [Accessing tasks](#accessing-tasks).

它們可以顯示在它們所屬的程式的計畫表中。

![](assets/d_ncs_user_tasks_in_planning.png)

## 訪問任務 {#accessing-tasks}

### 顯示任務 {#displaying-tasks}

任務將顯示在可通過宇宙訪問的任務列 **[!UICONTROL Campaigns]** 表中。

![](assets/s_ncs_user_task_edit_view.png)

您可以在此處查看連接的操作員的所有任務。

有關詳細資訊，請參 [閱任務的執行狀態](#execution-status-of-a-task)[和任務的進度狀態](#progress-status-of-a-task)。

### 篩選工作 {#filtering-tasks}

當您顯示此檢視時，會自動篩選該檢視，以便僅顯示 **[!UICONTROL operator tasks]**。 您也可以使用視窗上方區段的欄位來篩選工作。

![](assets/s_ncs_user_task_filter_from_view.png)

### 編輯工作 {#editing-tasks}

按一下工作即可加以編輯。

![](assets/s_ncs_user_task_edit_from_view.png)

## 建立新任務 {#creating-a-new-task}

若要建立工作，請按一下「促銷 **[!UICONTROL Tasks]** 活動」範圍中的連結，然後選取 **[!UICONTROL Create]**。

![](assets/s_ncs_user_task_create_new.png)

至少輸入任務的名稱，並選擇它所連結的促銷活動。 您也必須指定開始和結束日期。 這三條資訊是強制性的。

按一下 **[!UICONTROL Save]** 可建立任務。

![](assets/s_ncs_user_task_create_simple.png)

您也可以透過促銷活動的控制面板來建立工作：在這種情況下，它會自動連結至從中建立的促銷活動。

![](assets/s_ncs_user_task_create_new_from_op.png)

建立工作後，它會新增至促銷活動排程和工作清單。 要編輯任務，請從計畫中選擇該任務，或在任務概述中按一下其名稱，然後按一下該 **[!UICONTROL Open]** 連結。

![](assets/s_ncs_user_task_edit_simple.png)

若要設定，您必須指出：

* 經理和參與者：請參閱「 [經理」和「參與者」](#manager-and-participants)。
* 建立計畫：請參閱執 [行計畫](#execution-schedule)。
* 承諾成本：請參閱 [費用和收入](#expenses-and-revenues)。

廣告審核者(請參閱「審核者」 [)和參考檔案(請參閱「參考](#reviewers)的檔案」 [](#documents-referenced))也可以。

任務生命週期是在生命週期中 [表示的](#life-cycle)。

### 經理與參與者 {#manager-and-participants}

只有負責任務的操作員才有權關閉任務。

依預設，當Adobe Campaign運算子建立工作時，系統會自動指派工作給他們。 要選擇不同的運算子，請使用該 **[!UICONTROL Assigned to]** 欄位。

![](assets/s_ncs_user_task_edit_simple_general_tab.png)

>[!NOTE]
>
>操作員管理在本節 [中介紹](../../platform/using/access-management.md)。

您可以指定執行任務時涉及的運算子。 這些營運商無權關閉工作。 他們只能批准指派給他們的任務。

使用任務工具欄 **[!UICONTROL Resources]** 中的表徵圖來選擇它們。 按一下並 **[!UICONTROL Add]** 選擇相關的運算子。

![](assets/s_ncs_user_task_add_resources.png)

按一 **[!UICONTROL Ok]** 下並輸入使用率：這表示在任務執行期間分配給運算子的負載。 此比率僅為指示，以百分比表示。

例如，對於將執行計畫設定為10天的任務，在10天內，此任務的一半工作時間內將移動其使用率為50%的操作員。

對於每個操作員，您可以輸入計畫工作量和實際工作量。 這些期間也僅供參考。

您可以設定提醒，提醒會在任務結束日期前自動傳送給參與該任務的所有運算子。

您可以透過圖示來檢視Adobe Campaign營運商的設 **[!UICONTROL Edit link]** 定檔。

![](assets/s_ncs_user_task_edit_resource_profile.png)

運算子控制面板可讓您檢查其工作量（其他進行中的工作）。

![](assets/s_ncs_user_task_edit_resource_planning.png)

### 審核者 {#reviewers}

除了參與者外，您還可以定義操作員，操作員在任務由負責人關閉後將複查任務。 若要這麼做，請 **[!UICONTROL Enable task approval]** 按一下視窗左下方區段中的選 **[!UICONTROL Resources]** 項。 這可以是個別運算子、運算子群組或運算子清單。

![](assets/s_ncs_user_task_edit_resource_validation.png)

要指定運算子清單，請按一下 **[!UICONTROL Edit...]** 第一個審閱者右側的連結，然後根據需要添加任意數量的運算子，如下所示：

![](assets/s_ncs_user_task_edit_resource_operators.png)

您可以在審核者配置窗口的下部定義任務的批准計畫。 依預設，審核者自提交日期起有三天時間可核准工作。 您可以設定提醒，提醒會在核准截止日期之前自動傳送給相關的營運商。

![](assets/s_ncs_user_edit_op_valid_calendar.png)

即使已指派其他營運商來核准，負責該工作的人員仍可自行指派核准工作。 如果尚未定義審核者，則通知將發送給任務負責人。 所有其他具有權限的Adobe Campaign **[!UICONTROL Administrator]** 營運商也可以核准此工作。 不過，他們不會收到通知。

### 參考的檔案 {#documents-referenced}

您可以將檔案和行銷資源新增至工作(如需詳細資訊，請參閱管理行 [銷資源](../../campaign/using/managing-marketing-resources.md))。 要執行此操作，請開啟任務，然後按一下任 **[!UICONTROL Documents]** 務工具欄中的表徵圖。

單 **[!UICONTROL Add]** 擊並選擇要添加到任務中的文檔。 對行銷資源套用相同的程式。

![](assets/s_ncs_user_task_edit_documents.png)

參考的文檔將出現在發送給任務中涉及的操作員的通知中，以及任務控制面板中。

![](assets/s_ncs_user_task_notification_documents.png)

### 執行計畫 {#execution-schedule}

任務的有效期在和欄位中 **[!UICONTROL Start]** 指 **[!UICONTROL End]** 明。 調度的負載表示在該期間要執行的工作量。 以日或小時表示。

>[!NOTE]
>
>任務的生命週期在生命週期中 [顯示](#life-cycle)。

該字 **[!UICONTROL Workload performed]** 段也以天和小時表示，使您可以手動更新與計畫工作量相關的任務進度。

![](assets/s_ncs_user_task_percentage_done_enter.png)

根 **[!UICONTROL Progress status]** 據相關操作員執行的任務自動更新任務的百分比。 可手動輸入。

此資訊可在任務控制面板中檢視。

![](assets/s_ncs_user_task_percentage_done_from_dashboard.png)

它也會顯示在促銷活動標籤中。

![](assets/s_ncs_user_task_percentage_done_from_op.png)

如果任務執行計畫結束日期已到，但任務尚未完成，則任務將完成 **[!UICONTROL Late]**。 警告訊息也會顯示給警報運算子。

有關詳細資訊，請參 [閱任務進度狀態](#progress-status-of-a-task)。

### 支出與收入 {#expenses-and-revenues}

您可以定義每個任務的相關費用和預測收入。 這些值將計算，然後合併至任務所附加的促銷活動。

要指定此資訊，請按一下任 **[!UICONTROL Expenses and revenue]** 務工具欄中的表徵圖。

![](assets/s_ncs_user_task_edit_costs.png)

依預設，已支付的預算是附加任務之促銷活動的預算。 它顯示在任務詳細資訊中。

>[!NOTE]
>
>有關費用和預算的詳細資訊，請參 [閱成本承諾、計算和計費](../../campaign/using/controlling-costs.md#cost-commitment--calculation-and-charging)。

在此窗口中，您也可以定義要達到的目標。 目標以任務的預測收入表示。

### 服務供應商 {#service-providers}

外部服務提供商可以參與任務的管理。

要執行此操作，請編輯任務屬性並選擇相關的服務提供商。 與服務提供商關聯的成本類別會自動列在窗口的中央部分。

有關詳細資訊，請參 [閱建立服務提供商及其成本類別](../../campaign/using/providers--stocks-and-budgets.md#creating-a-service-provider-and-its-cost-categories)。

選擇與任務執行相關的成本類別。 要執行此操作，請選擇成本類型，並根據需要添加附加費金額。

![](assets/s_ncs_user_task_edit_simple_costs_tab.png)

>[!NOTE]
>
>管理預算及成本之方法於控製成本 [中呈列](../../campaign/using/controlling-costs.md)。

選擇服務提供者後，它將顯示在任務儀表板中：

![](assets/s_ncs_user_task_supplier_view.png)

### 延遲任務 {#late-tasks}

如果任務已到達其結束日期，但其狀態未更改為，則任務將延遲 **[!UICONTROL Finished]**。 根據預設，當任務延遲時，不會警告任何運算子。 您可以設定通知電子郵件的傳送方式：即使所有運算子不參與任務，也會收到通知。

移至方 **[!UICONTROL Resources]** 塊並將運算子新增至欄 **[!UICONTROL Assignation]** 位。 要通知多個人，請選擇一組操作員。

![](assets/mrm_task_alert_if_late.png)

### 初始通知 {#initial-notifications}

當您建立或修改未來有開始日期的工作時，Adobe Campaign會提供傳送電子郵件給負責工作的人員，讓他們知道工作何時開始。

![](assets/mrm_task_first_notif.png)

不過，如果您正在建立的任務遠未完成，則最好在任務開始之前安排要發送的通知。 例如，如果任務在一個月內開始，您可以在任務開始前一週通知負責人。

若要排程通知，請移至方 **[!UICONTROL Resources]** 塊並使用欄 **[!UICONTROL Initial notification]** 位。

![](assets/mrm_task_alert_before.png)

* 對於促銷活動中的任務，請選取特定的日期和時間。
* 對於促銷活動範本中的任務，通知時間表示為任務開始前的剩餘時間（例如，如果您在欄位中輸入2d，則在任務開始日期前2天傳送電子郵件）。 **[!UICONTROL Initial notification]**

如果您已排程通知，當您儲存工作時，Adobe Campaign會暫停提供，以立即傳送通知。 您可以決定傳送它，但不會取代排程的通知。

### 與程式連結的任務 {#task-linked-to-a-program}

您可以直接在方案中建立工作，以管理與其整體組織相關的動作，而非與特定促銷活動相關的動作（例如，討論方案中即將推出之促銷活動主題的會議）。 任務將出現在程式計畫中。

要建立直接連結至程式的任務，請執行以下操作：

1. 開啟程式計畫：在首頁上，轉到 **[!UICONTROL Campaigns > Browse > Other choices > Programs]**。 整個方案排程會在視窗的右側區段中開啟。
1. 在排程中，按一下所需的程式：窗戶上會顯示該程式。
1. 在此窗口中，按一下 **[!UICONTROL Open]**。 程式排程隨即開啟。
1. 按一下 **[!UICONTROL Add]** 右側排程上方的按鈕，然後按一下 **[!UICONTROL Add a task]**。

![](assets/mrm_task_create_from_prg.png)

### 營運商可用性 {#operator-availability}

在任務儀表板中，操作員名稱旁邊的表徵圖表示他們已在任務涵蓋的期間內處理另一個任務或事件。 (操作員負責或參與的任務：他將出現在 **[!UICONTROL Assigned to]** 欄位或任務框 **[!UICONTROL Resources]** 中)。

![](assets/mrm_task_alert_operator_busy.png)

### 工作流中的任務 {#task-in-a-workflow}

在促銷活 **[!UICONTROL Task]** 動工作流程中使用元素可讓您根據任務是否已核准來定義兩個藍本。

![](assets/mrm_task_in_workflow.png)

在促銷活動工作流程中， **[!UICONTROL Task]** 活動會在標籤中找 **[!UICONTROL Flow control]** 到。

## 任務類型 {#types-of-task}

當您透過促銷活動建立工作時，可以建立特定的工作。 任務類型在選定模板中定義。

![](assets/s_ncs_user_task_select_template.png)

可排程下列工作：

* **[!UICONTROL Control task]**，請參閱「控 [制任務](#control-tasks)」
* **[!UICONTROL Marketing resource creation task]**，請參閱 [分組任務](#grouping-task),
* **[!UICONTROL Grouping task]**，請參閱 [分組任務](#grouping-task),
* **[!UICONTROL Notification task]**，請參閱 [通知任務](#notification-task)。

>[!NOTE]
>
>**[!UICONTROL Control task]** 而且 **[!UICONTROL Grouping]** 只能透過促 **銷活動控** 制面板，來建立工作。\
>它們顯示在為其分配的操作員的任務映射中。 請參 [閱訪問任務](#accessing-tasks)。

### 控制工作 {#control-tasks}

A會 **[!UICONTROL Control task]** 連結至傳送核准：核准目標、內容、擷取檔案、預算或證明。

![](assets/s_ncs_user_task_new_control.png)

建立工作後，該工作即會新增至促銷活動控制面板。

![](assets/s_ncs_user_task_edit_from_board.png)

然後可以編輯它並指定其參數。

### 行銷資源建立工作 {#marketing-resource-creation-task}

行銷資源建立工作可用來管理行銷資源的建立和發佈。 如果您通過任務管理資源，而不是通過資源本身管理資源，則可以：

* 透過促銷活動控制資源建立程式。
* 在計畫中查看資源建立流程。
* 管理資源建立程式（提醒、通知）。
* 計算和控制與建立資源連結的成本。
* 通過任務批准和發佈資源（如果啟用了相關選項）。

#### 任務及其連結資源之間的交互 {#interaction-between-the-task-and-its-linked-resource}

行銷資源建立工作會與連結至其的資源互動。 這表示：

* 資源建立時間表及其連結的成本通過任務進行管理。
* 營運商可以像一般（下載或上傳、鎖定和解除鎖定）一樣處理資源：這不會影響任務。
* 資源審批和發佈可通過任務執行：如果啟 **[!UICONTROL Publish the marketing resource]** 用了該選項，則在任務完成後，資源將被自動批准和發佈。 如果未啟用此選項，則任務和資源不進行交互：對一個不會影響另一個。

   您可以使用一系列連結的工作來定義完整的核准週期。 僅選中 **[!UICONTROL Publish the marketing resource]** 最後一個任務的選項：所有任務都需要完成，才能發佈資源。 此外，建立子行銷資源任務時，將在子任務中自動選擇該資源。

   * **透過資源**:如果提交資源進行審批或審批，這些操作將不影響任務。
   * **通過任務**:如果 **[!UICONTROL Publish the marketing resource]** 在任務中選中了該選項，則在任務完成後，資源將被批准並自動發佈（請參閱上面）。 如果未勾選此選項，則任務和資源將不進行交互：對一個不會影響另一個。

#### 設定行銷資源建立工作 {#configuring-a-marketing-resource-creation-task}

審閱任務的人員不必是審閱資源中定義的內容的同一人。 但是，如果選 **[!UICONTROL Publish the marketing resource]** 項被選中（請參見下面），則任務審核者有權批准資源內容，任務完成後將自動批准該資源（如果未定義審核者，則授權任務管理員）。

![](assets/mrm_task_asset_creation.png)

在欄位 **[!UICONTROL Marketing resource]** 中，定義要通過此任務管理的資源。 您可以：

* 選擇現有資源：下拉式清單會提供狀態為的所有資源 **[!UICONTROL Being edited]**。
* 建立資源：按一下 **[!UICONTROL Select the link]** 圖示，然後按一下圖 **[!UICONTROL Create]** 示。

此選 **[!UICONTROL Publish the marketing resource]** 項可讓您自動化資源發佈：一旦任務完成 **[!UICONTROL Finished]**&#x200B;後，即使資源既未提交批准，也未獲批准，資源的狀態也會自動切換到 **[!UICONTROL Published]**，包括完成任務的審核者不是資源中定義的內容審核者。

此 **[!UICONTROL Publish the resource]** 按鈕可供使用，資源發佈審閱者會收到通知電子郵件，通知他已準備好發佈。 在頁籤 **[!UICONTROL Edit > Tracking]** 中，任務審閱者的審閱和發佈將變為可見。 如果已定義資源後處理工作流，則立即執行。

![](assets/mrm_resource_audit_tab.png)

### 分組任務 {#grouping-task}

類型 **[!UICONTROL Grouping task]** 任務可讓您對多個任務進行分組，並同步管理其進度和審批。

分組任務沒有連結的費用或資源。

所有分組到分組任務的任務都可以在其自己的儀表板上查看。 這可讓您篩選工作清單，只顯示您感興趣的工作。

分組任務有一個連結，可讓您輕鬆建立分組任務。

若要根據群組任務建立群組任務，請前往促銷活動控制面板，然後按一下群組任務的名稱以顯示其說明，然後按一下 **[!UICONTROL Add a task]**。

![](assets/mrm_task_grouped_create.png)

但是，如果已建立要連結到分組任務的任務，則可以通過框的欄位 **[!UICONTROL Linked to]** 執行該 **[!UICONTROL Properties]** 操作。

![](assets/s_ncs_user_task_group_with.png)

### 通知任務 {#notification-task}

通知任務可讓您排程電子郵件傳送（傳送給營運商、營運商群組、服務供應商等）。 這可讓您排程提醒，例如通知某人促銷活動即將結束，或在促銷活動開始前傳送檔案，讓營運商可以準備。 這表示您可以追蹤促銷活動或方案中的通訊內容，並更密切地關注所執行的動作。

#### 生命週期 {#life-cycle}

通知工作不需要核准。 這意味著它們的生命週期比標準任務更簡單：

![](assets/mrm_task_notif_lifecycle.png)

通知任務可以具有以下狀態：

* **[!UICONTROL Scheduled]** 直到電子郵件傳送
* **[!UICONTROL In progress]** 一旦傳送電子郵件，直到到達結束日期
* **[!UICONTROL Finished]** 到達結束日期後。

#### 配置 {#configuration}

![](assets/mrm_task_notif_dashboard.png)

在建立過程中，必須在任務中輸入以下元素：

* **[!UICONTROL Assigned to]** :接收電子郵件的營運商或營運商群組。 如果您在傳送電子郵件後重新指派工作，則不會將電子郵件傳送給新的運算元（若要這麼做，您必須重新初始化工作並變更其開始日期）。
* **任務開始日期**:通知電子郵件的傳送日期。 此日期必須在記錄任務時在將來發生。
* **任務結束日期**:任務狀態更改為的日期 **[!UICONTROL Finished]**。 根據預設，結束日期與開始日期相同。 不過，為任務指定持續時間可讓您象徵操作員在計畫中必須執行的時間長度（如果需要）。
* **[!UICONTROL Description]** :此處輸入的文本將出現在通知電子郵件的正文中。

   ![](assets/mrm_task_notif_dashboard_msg.png)

您可以將附件添加到任務和通知電子郵件中。 若要這麼做，請按 **[!UICONTROL Documents]** 一下右上角工具列中的圖示。

## 生命週期 {#life-cycle-1}

### 任務之間的連結 {#links-between-tasks}

每個 **[!UICONTROL Properties]** 任務中的按鈕可讓您定義促銷活動中各任務之間的連結。 您可以使用分組任務將任務拆分為子任務(請參 [閱連結任務](#linked-tasks))，或定義任務之間的相依性(請參 [閱分組任務](#grouping-tasks))。

#### 連結的工作 {#linked-tasks}

使用字 **[!UICONTROL Linked task]** 段將任務與分組任務關聯。 請參 [閱任務類型](#types-of-task)。

在下列範例中，定位的核准會細分為四個子任務。

![](assets/s_ncs_user_task_linked_tasks.png)

每個子任務都是連結到主任務的標準任務。

![](assets/s_ncs_user_task_depends_on.png)

#### 將任務分組 {#grouping-tasks}

使用 **[!UICONTROL Grouped to]** 該欄位可使任務的執行取決於另一個任務的執行。

![](assets/s_ncs_user_task_group_with.png)

任務之間的相依性由促銷活動控制面板中的箭頭表示。

![](assets/s_ncs_user_task_dependencies_from_board.png)

對於分組任務，Adobe Campaign會自動將父任務的結束日期指派給子任務作為開始日期。 例如，如果 **Create invitation** task於10月15日下午3:30結束， **Send invitation email** child task將於10月15日下午3:30開始。

此外，如果您推遲父項任務的結束，其某些子項任務可能會受到影響：這些是狀態為且開始日期早 **[!UICONTROL Scheduled]** 於父任務新結束日期的子任務。 任務的持續時間保持不變。 如果子任務的開始日期晚於父任務的新結束日期，則子任務不受影響。

**範例**

預定於10月9日下午5點結束的父任務有兩個子任務，任務A和任務B。任務A定於10月10日下午2點開始，任務B定於10月12日上午8點開始。

讓我們推遲父任務：現在10月11日下午1點結束。 只有任務A被推遲，將於10月11日下午1點開始。

![](assets/mrm_task_parent_postpones_child.png)

### 任務的執行狀態 {#execution-status-of-a-task}

任務狀態可以在任務圖中查看。 根據操作員操作自動更新任務的執行狀態。

任務可以是： **[!UICONTROL Scheduled]**、 **[!UICONTROL In progress]**、 **[!UICONTROL Finished]****[!UICONTROL Canceled]**&#x200B;或 **[!UICONTROL Pending approval]****[!UICONTROL Rejected]**。

* 建立任務時，其開始日期 **[!UICONTROL Scheduled]** 是否為將來。 它會保留此狀態，直到達到其開始日期為止。
* 啟動後，任務即為 **[!UICONTROL In progress]**。 當負責任務的人員關閉任務時，它將更改為 **[!UICONTROL Finished]**。
* 如果已定義了審核者，則任務將在負責 **[!UICONTROL Pending approval]** 該任務的人員關閉後，直到審核者批准該任務。 如果審核者拒絕，則任務將是 **[!UICONTROL Rejected]**。
* 負責任務的人員可通過儀表板或按一下按鈕來取消 **[!UICONTROL Task map]** 任 **[!UICONTROL Cancel]** 務。
* 要計畫任務，請輸入將來的開始日期。 然後，您可以傳送第一個通知給執行工作所涉及的Adobe Campaign營運商。 請參 [閱完成任務生命週期](#complete-task-life-cycle)。

>[!NOTE]
>
>* 任務狀態會自動更新。
>* 即使有效期已結束，未關閉的任務仍會顯示在進行中的任務清單中。 警告會通知運算子任務已延遲。
>



### 任務的進度狀態 {#progress-status-of-a-task}

除了執行狀態外，任務還可以與進度狀態關聯： **[!UICONTROL Late]**、 **[!UICONTROL To approve]****[!UICONTROL To do today]** 或 **[!UICONTROL To do this week]**。 系統會根據任務計畫自動輸入此資訊。

您可以按進程或進度狀態篩選任務清單。

For more on this, refer to [Accessing tasks](#accessing-tasks).

### 完成任務生命週期 {#complete-task-life-cycle}

以下是整個任務生命週期的階段，負責人已為其定義參與者和審閱者。

1. 負責人建立任務並輸入各個欄位。 有關詳細資訊，請參閱 [建立新任務](#creating-a-new-task)。

   在建立和編輯未 **來排程的任務** （只要未到達任務開始日期）時，可以向參與者和經理發送通知，讓他們知道已排程了新任務。

   ![](assets/s_ncs_user_task_planed_send_message.png)

   若要傳送此第一個通知，請按一下 **[!UICONTROL Yes]**。 此通知會告知他們下一項工作，並包含內容的詳細資訊以及截止日期前的剩餘天數。

   當建立任務並排程以後，其狀態為 **[!UICONTROL Scheduled]**。

1. 在任務開始日期，負責人和參與者會收到通知，通知他們任務已開始。 其狀態變更為 **[!UICONTROL In progress]**。
1. 完成分配給他們的部分後，參與者可以批准該任務：

   * 透過通知電子郵件傳送。
   * 透過主控台或Web介面，在工作控制面板中。

      ![](assets/s_ncs_user_task_start_rea.png)

1. 每次參與者批准作業時，任務的進度狀態都會更新。

   ![](assets/s_ncs_user_task_percentage_done_op.png)

1. 審核者會收到通知電子郵件，通知他營運商已完成指派給他們的區段。

   他們可以遵循任務控制面板上的進度。

   ![](assets/s_ncs_user_task_follow_from_dashboard.png)

1. 當負責任務的人員決定任務完成後，他們可以使用任務啟動時發送的通知電子郵件中的連結、控制台或介面來關閉該任務。

   ![](assets/s_ncs_user_task_console_ressource_validation.png)

   >[!NOTE]
   >
   >負責任務的人員可以隨時關閉該任務，即使缺少批准。 進度狀態會自動變更為100%。

1. 任務狀態將更 **[!UICONTROL To approve]**&#x200B;改為，並向審核者發送通知。

   他們會透過通知電子郵件、主控台或網頁介面核准工作。

   他們可透過促銷活動控制面板採取行動：

   ![](assets/s_ncs_user_task_console_validation.png)

   他們還可以使用任務批准按鈕：

   ![](assets/s_ncs_user_task__validation.png)

   >[!NOTE]
   >
   >只有在任務窗口中啟 **[!UICONTROL To approve]** 用了該選項後， **[!UICONTROL Enable task validation]** 任務 **[!UICONTROL Resources]** 狀態才會更改。\
   >如果審核者拒絕任務，其狀態將更改為 **[!UICONTROL Rejected]**，並且任務生命週期將自動重新啟動。

1. 任務狀態將更改為 **[!UICONTROL Finished]**。 系統會傳送通知給所有相關人員。

   >[!NOTE]
   >
   >任務完成後，其生命週期由負責人重新初始化。 若要這麼做，請開啟工作，然後按一 **[!UICONTROL Reset task to execute it again...]** 下控制面板底部的連結。

