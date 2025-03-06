---
product: campaign
title: 使用本地核准活動
description: 瞭解如何使用本機核准活動
feature: Workflows
hide: true
hidefromtoc: true
exl-id: cc29eec9-9c97-4d1b-9567-2581154d7b3f
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1283'
ht-degree: 2%

---

# 使用本地核准活動{#using-the-local-approval-activity}



整合至目標工作流程的&#x200B;**[!UICONTROL Local approval]**&#x200B;活動可讓您在傳送傳遞前設定收件者核准流程。

>[!CAUTION]
>
>若要使用此函式，您必須購買分散式行銷模組，這是行銷活動選項。 請檢查您的授權合約。

為了設定此使用案例，我們已建立下列目標定位工作流程：

![](assets/local_validation_workflow.png)

本地核准流程的主要步驟為：

1. 由於使用資料分佈模型的&#x200B;**[!UICONTROL Split]**&#x200B;型別活動，因此定位所產生的母體可能會受到限制。

   ![](assets/local_validation_intro_1.png)

1. 然後&#x200B;**[!UICONTROL Local approval]**&#x200B;活動接手並傳送通知電子郵件給每個本機主管。 活動會擱置，直到每個本機主管核准指派給他們的收件者為止。

   ![](assets/local_validation_intro_4.png)

1. 一旦達到核准期限，工作流程就會重新開始。 在此範例中，**[!UICONTROL Delivery]**&#x200B;活動會開始，且傳遞會傳送至已核准的目標。

   >[!NOTE]
   >
   >一旦到達截止日期，未獲核准的收件者則會從目標定位中排除。

   ![](assets/local_validation_intro_6.png)

1. 幾天後，第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;型別活動會傳送通知電子郵件給每個本機主管，其中包含其聯絡人執行的動作（點選、開啟等）摘要。

   ![](assets/local_validation_intro_5.png)

## 步驟1：建立資料發佈範本 {#step-1--creating-the-data-distribution-template-}

資料發佈範本可讓您限制根據資料分組定位而導致的母體，同時讓您將每個值指派給本機主管。 在此範例中，我們已將&#x200B;**[!UICONTROL Email address domain]**&#x200B;欄位定義為發佈欄位，並將網域指派給每個本機監督員

如需建立資料發佈範本的詳細資訊，請參閱[限制每個資料發佈的子集記錄數目](split.md#limiting-the-number-of-subset-records-per-data-distribution)。

1. 若要建立資料發佈範本，請前往&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;節點並按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 選取 **[!UICONTROL General]** 索引標籤。

   ![](assets/local_validation_data_distribution_2.png)

1. 輸入&#x200B;**[!UICONTROL Label]**&#x200B;與&#x200B;**[!UICONTROL Distribution context]**。 在此範例中，我們已選取&#x200B;**[!UICONTROL Recipient]**&#x200B;目標結構描述和&#x200B;**[!UICONTROL Email domain]**&#x200B;欄位作為發佈欄位。 收件者清單將依網域劃分。
1. 在&#x200B;**[!UICONTROL Distribution type]**&#x200B;欄位中，選取目標限制值在&#x200B;**[!UICONTROL Distribution]**&#x200B;索引標籤中的表示方式。 我們已選擇&#x200B;**[!UICONTROL Percentage]**。
1. 在&#x200B;**[!UICONTROL Approval storage]**&#x200B;欄位中，輸入與使用中目標結構描述相符之核准的儲存結構描述。 我們在這裡將使用預設的儲存結構描述： **[!UICONTROL Local approval of recipients]**。
1. 然後按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結。

   ![](assets/local_validation_data_distribution_3.png)

1. 保留&#x200B;**[!UICONTROL Approve the targeted messages]**&#x200B;選項為已核取狀態，以便從要核准的收件者清單中預先選取所有收件者。
1. 在&#x200B;**[!UICONTROL Delivery label]**&#x200B;欄位中，我們已保留預設運算式（傳遞的計算字串）。 回饋意見通知將使用傳遞的標準標籤。
1. 在&#x200B;**[!UICONTROL Grouping field]**&#x200B;區段中，我們已選取&#x200B;**[!UICONTROL Gender]**&#x200B;欄位作為群組欄位，以在核准和回饋通知中顯示收件者。
1. 在&#x200B;**[!UICONTROL Edit targeted messages]**&#x200B;區段中，我們已選取&#x200B;**[!UICONTROL Edit recipients]**&#x200B;網頁應用程式和&#x200B;**[!UICONTROL recipientId]**&#x200B;引數。 在核准和回饋通知中，收件者將可點選，且會指向網頁應用程式的URL。 額外的URL引數將會是&#x200B;**[!UICONTROL recipientId]**。
1. 然後按一下「**[!UICONTROL Distribution]**」標籤。 針對每個網域，輸入下列欄位：

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**：輸入網域名稱的值。
   * **[!UICONTROL Percentage / Fixed]**：為每個網域輸入最大值。 您要傳送傳遞的收件者人數。 在此範例中，我們想將每個網域的傳送限製為10%。
   * **[!UICONTROL Label]**：輸入要顯示在核准和意見反應通知中的網域標籤。
   * **[!UICONTROL Group or operator]**：選取指派給網域的運運算元或運運算元群組。

     >[!CAUTION]
     >
     >請確定已指派適當的許可權給運運算元。

## 步驟2：建立目標定位工作流程 {#step-2--creating-the-targeting-workflow}

為了設定此使用案例，我們已建立下列目標定位工作流程：

![](assets/local_validation_workflow.png)

已新增下列活動：

* 兩個&#x200B;**[!UICONTROL Query]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Intersection]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Split]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Delivery]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Wait]**&#x200B;活動，
* 第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL End]**&#x200B;活動。

### 查詢、交集和分割 {#queries--intersection-and-split}

上游目標定位由兩個查詢、一個交集和一個分割組成。 使用資料分佈範本的&#x200B;**[!UICONTROL Split]**&#x200B;活動可限制目標定位產生的母體。

如需設定分割活動的詳細資訊，請參閱[分割](split.md)。 資料發佈範本的建立在[限制每個資料發佈的子集記錄數目](split.md#limiting-the-number-of-subset-records-per-data-distribution)中有詳細說明。

如果您不想限制來自查詢的母體，則不必使用&#x200B;**[!UICONTROL Query]**、**[!UICONTROL Intersection]**&#x200B;和&#x200B;**[!UICONTROL Split]**&#x200B;活動。 在此情況下，請先完成前&#x200B;**[!UICONTROL Local approval]**&#x200B;個活動中的資料發佈範本。

1. 在&#x200B;**[!UICONTROL Record count limitation]**&#x200B;區段中，選取&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;選項並按一下&#x200B;**[!UICONTROL Edit]**&#x200B;連結。

   ![](assets/local_validation_split_1.png)

1. 選取&#x200B;**[!UICONTROL Keep only the first records after sorting]**&#x200B;選項並按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/local_validation_split_1bis.png)

1. 在&#x200B;**[!UICONTROL Sort columns]**&#x200B;區段中，新增套用排序的欄位。 我們已選取&#x200B;**[!UICONTROL Email]**&#x200B;欄位。 按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/local_validation_split_2.png)

1. 選取&#x200B;**[!UICONTROL By data distribution]**&#x200B;選項，選取先前建立的發佈範本（請參閱[步驟1：建立資料發佈範本](#step-1--creating-the-data-distribution-template-)），然後按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/local_validation_split_3.png)

在分佈範本中，我們已選擇將母體限製為每個分組值10%，這符合工作流程中顯示的值（340作為輸入和34作為輸出）。

![](assets/local_validation_intro_1.png)

### 核准通知 {#approval-notification}

**[!UICONTROL Local approval]**&#x200B;活動可讓您傳送通知給每個本機主管。

如需設定&#x200B;**[!UICONTROL Local approval]**&#x200B;活動的詳細資訊，請參閱[本機核准](local-approval.md)。

![](assets/local_validation_workflow_2.png)

需要輸入下列欄位：

1. 在 **[!UICONTROL Action to execute]** 區段中，選取 **[!UICONTROL Target approval notification]** 選項。
1. 在 **[!UICONTROL Distribution context]** 區段中，選取 **[!UICONTROL Specified in the transition]** 選項。

   如果您不想限制目標母體，請在此處選取&#x200B;**[!UICONTROL Explicit]**&#x200B;選項，然後輸入先前在&#x200B;**[!UICONTROL Data distribution]**&#x200B;欄位中建立的散發範本。

1. 在&#x200B;**[!UICONTROL Notification]**&#x200B;區段中，選取要用於通知電子郵件的傳遞範本和主旨。 在此處，我們已選擇預設範本： **[!UICONTROL Local approval notification]**。
1. 在&#x200B;**[!UICONTROL Approval schedule]**&#x200B;區段中，我們保留預設核准期限（3天）並新增提醒。 傳遞將在核准開始後3天後離開。 一旦達到核准期限，未核准的收件者就不會在鎖定目標時列入考量。

**[!UICONTROL Local approval]**&#x200B;活動傳送給本機監督員的通知電子郵件如下：

![](assets/local_validation_intro_2.png)

### 等待 {#wait}

等待活動可讓您延遲將傳送傳送回饋通知的第二個本機核准活動的開始。 我們已在&#x200B;**[!UICONTROL Duration]**&#x200B;欄位中輸入&#x200B;**[!UICONTROL 5d]**&#x200B;值（5天）。 在傳送傳遞後5天內由收件者執行的動作將包含在回饋通知中。

![](assets/local_validation_workflow_3.png)

### 意見反應通知 {#feedback-notification}

第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動可讓您傳送傳遞回饋通知給每個本機主管。

![](assets/local_validation_workflow_4.png)

需要輸入下列欄位。

1. 在&#x200B;**[!UICONTROL Action to execute]**&#x200B;區段中，選擇&#x200B;**[!UICONTROL Delivery feedback report]**。
1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;區段中，選擇&#x200B;**[!UICONTROL Specified in the transition]**。
1. 在&#x200B;**[!UICONTROL Notification]**&#x200B;區段中，選取要用於通知電子郵件的傳遞範本和主旨。

一旦達到等待活動中設定的期限，第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;型別活動就會傳送下列通知電子郵件給每個本機主管：

![](assets/local_validation_intro_3.png)

### 管理員的核准追蹤 {#approval-tracking-by-the-administrator}

每次本機核准活動開始時，都會建立核准任務。 管理員可以控制這些核准任務。

前往行銷活動的目標定位工作流程，然後按一下「**[!UICONTROL Local approval tasks]**」標籤。

![](assets/local_validation_admin_1.png)

也可以透過資料發佈範本的&#x200B;**[!UICONTROL Approval tasks]**&#x200B;索引標籤存取本機核准任務清單。

![](assets/local_validation_admin_2.png)

選取您要監視的工作，然後按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕。 本機核准任務的&#x200B;**[!UICONTROL General]**&#x200B;標籤可讓您檢視有關任務的資訊。 如有需要，您可以變更核准和提醒日期。

![](assets/local_validation_admin_3.png)

此標籤會顯示下列資訊：

* 任務的標籤及其ID
* 使用的散發範本
* 目標訊息數
* 連結的工作流程與行銷活動
* 任務排程

任務的&#x200B;**[!UICONTROL Distribution]**&#x200B;索引標籤可讓您檢視核准記錄、其狀態、目標訊息數、核准日期，以及核准傳遞的操作員。

![](assets/local_validation_admin_4.png)

選取核准記錄並按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕以顯示更多資訊。 本機核准記錄檔的&#x200B;**[!UICONTROL General]**&#x200B;索引標籤可讓您檢視一般記錄檔資訊。 您也可以變更核准狀態。

![](assets/local_validation_admin_5.png)

此標籤會顯示下列資訊：

* 連結的核准任務
* 核准狀態（**[!UICONTROL Approved]**&#x200B;或&#x200B;**[!UICONTROL Pending]**）
* 使用的散發範本
* 核准的當地主管和核准日期
* 已鎖定目標和已核准的訊息數

核准記錄檔的&#x200B;**[!UICONTROL Targeted]**&#x200B;索引標籤會顯示目標收件者的清單及其核准狀態。 您可以視需要變更此狀態。

![](assets/local_validation_admin_6.png)
