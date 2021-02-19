---
solution: Campaign Classic
product: campaign
title: 使用本機核准活動
description: 瞭解如何使用本機核准活動
audience: workflow
content-type: reference
topic-tags: use-cases
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1272'
ht-degree: 2%

---


# 使用本機核准活動{#using-the-local-approval-activity}

**[!UICONTROL Local approval]**&#x200B;活動整合在定位工作流程中，可讓您在傳送傳送之前設定收件者核准程式。

>[!CAUTION]
>
>若要使用此函式，您必須購買Distributed Marketing模組，此為促銷活動選項。 請檢查您的授權合約。

若要設定此使用案例，我們建立了下列定位工作流程：

![](assets/local_validation_workflow.png)

本端核准程式的主要步驟為：

1. 由於使用資料分發模型的&#x200B;**[!UICONTROL Split]**&#x200B;類型活動，定位所產生的人口數目可能會受到限制。

   ![](assets/local_validation_intro_1.png)

1. 然後，**[!UICONTROL Local approval]**&#x200B;活動接管並向每個本地主管發送通知電子郵件。 活動將暫停，直到每個本地主管批准分配給它們的收件人。

   ![](assets/local_validation_intro_4.png)

1. 一旦到達核准截止日期，工作流程就會重新開始。 在此範例中，**[!UICONTROL Delivery]**&#x200B;活動會啟動，傳送內容會傳送至已核准的目標。

   >[!NOTE]
   >
   >到達期限後，尚未核准的收件者就會被排除在定位之外。

   ![](assets/local_validation_intro_6.png)

1. 幾天後，第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;類型活動會向每個本地主管發送通知電子郵件，其中包含其聯繫人（按一下、開啟等）執行的操作的摘要。

   ![](assets/local_validation_intro_5.png)

## 步驟1:建立資料分發模板{#step-1--creating-the-data-distribution-template-}

資料分發範本可讓您根據資料分組限制定位所產生的人口族群，同時讓您將每個值指派給本機主管。 在此示例中，我們將&#x200B;**[!UICONTROL Email address domain]**&#x200B;欄位定義為分佈欄位，並為每個本地主管分配了域

有關建立資料分發模板的詳細資訊，請參閱[限制每個資料分發的子集記錄數](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)。

1. 要建立資料分發模板，請轉至&#x200B;**[!UICONTROL Resources > Campaign management > Data distribution]**&#x200B;節點，然後按一下&#x200B;**[!UICONTROL New]**。

   ![](assets/local_validation_data_distribution_1.png)

1. 選取 **[!UICONTROL General]** 索引標籤。

   ![](assets/local_validation_data_distribution_2.png)

1. 輸入&#x200B;**[!UICONTROL Label]**&#x200B;和&#x200B;**[!UICONTROL Distribution context]**。 在此範例中，我們選取了&#x200B;**[!UICONTROL Recipient]**&#x200B;定位架構和&#x200B;**[!UICONTROL Email domain]**&#x200B;欄位作為分佈欄位。 收件者清單將依網域劃分。
1. 在&#x200B;**[!UICONTROL Distribution type]**&#x200B;欄位中，選取目標限制值在&#x200B;**[!UICONTROL Distribution]**&#x200B;標籤中的表示方式。 這裡，我們選擇了&#x200B;**[!UICONTROL Percentage]**。
1. 在&#x200B;**[!UICONTROL Approval storage]**&#x200B;欄位中，輸入與使用中的目標模式相符之核准的儲存模式。 下面我們將使用預設儲存模式：**[!UICONTROL Local approval of recipients]**。
1. 然後按一下&#x200B;**[!UICONTROL Advanced parameters]**&#x200B;連結。

   ![](assets/local_validation_data_distribution_3.png)

1. 將&#x200B;**[!UICONTROL Approve the targeted messages]**&#x200B;選項保持為勾選狀態，以便所有收件者都已預先從要核准的收件者清單中選取。
1. 在&#x200B;**[!UICONTROL Delivery label]**&#x200B;欄位中，我們保留了預設運算式（傳送的計算字串）。 傳送的標準標籤將用於回饋通知。
1. 在&#x200B;**[!UICONTROL Grouping field]**&#x200B;區段中，我們選取&#x200B;**[!UICONTROL Gender]**&#x200B;欄位作為群組欄位，以在核准和意見通知中顯示收件者。
1. 在&#x200B;**[!UICONTROL Edit targeted messages]**&#x200B;區段中，我們選取了&#x200B;**[!UICONTROL Edit recipients]**&#x200B;網頁應用程式和&#x200B;**[!UICONTROL recipientId]**&#x200B;參數。 在核准和意見通知中，收件者可點按，並指向網頁應用程式的URL。 其他URL參數將是&#x200B;**[!UICONTROL recipientId]**。
1. 然後按一下&#x200B;**[!UICONTROL Distribution]**&#x200B;標籤。 針對每個網域，輸入下列欄位：

   ![](assets/local_validation_data_distribution_4.png)

   * **[!UICONTROL Value]**:輸入域名的值。
   * **[!UICONTROL Percentage / Fixed]**:對於每個域，輸入最大值。要傳送傳送給的收件者數。 在此範例中，我們希望將傳送限制為每個網域10%。
   * **[!UICONTROL Label]**:輸入要在批准和反饋通知中顯示的域標籤。
   * **[!UICONTROL Group or operator]**:選擇分配給域的運算子或運算子組。

      >[!CAUTION]
      >
      >請確定已為運算子指派適當的權限。

## 步驟2:建立定位工作流程{#step-2--creating-the-targeting-workflow}

若要設定此使用案例，我們建立了下列定位工作流程：

![](assets/local_validation_workflow.png)

新增下列活動：

* 兩個&#x200B;**[!UICONTROL Query]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Intersection]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Split]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Delivery]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL Wait]**&#x200B;活動，
* 第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動，
* 一個&#x200B;**[!UICONTROL End]**&#x200B;活動。

### 查詢、交叉和拆分{#queries--intersection-and-split}

上游定位由兩個查詢組成，一個交叉點和一個分割。 使用資料分發範本的&#x200B;**[!UICONTROL Split]**&#x200B;活動，可以限制由定位產生的人口。

有關配置拆分活動的詳細資訊，請參閱[Split](../../workflow/using/split.md)。 [限制每個資料分發的子集記錄數](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)中詳細介紹了資料分發模板的建立。

如果您不想限制查詢的人口，則不必使用&#x200B;**[!UICONTROL Query]**、**[!UICONTROL Intersection]**&#x200B;和&#x200B;**[!UICONTROL Split]**&#x200B;活動。 在此情況下，請完成第一個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動中的資料分發範本。

1. 在&#x200B;**[!UICONTROL Record count limitation]**&#x200B;部分，選擇&#x200B;**[!UICONTROL Limit the selected records]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Edit]**&#x200B;連結。

   ![](assets/local_validation_split_1.png)

1. 選擇&#x200B;**[!UICONTROL Keep only the first records after sorting]**&#x200B;選項，然後按一下&#x200B;**[!UICONTROL Next]**。

   ![](assets/local_validation_split_1bis.png)

1. 在&#x200B;**[!UICONTROL Sort columns]**&#x200B;節中，添加應用排序的欄位。 這裡，我們選擇了&#x200B;**[!UICONTROL Email]**&#x200B;欄位。 按一下 **[!UICONTROL Next]**。

   ![](assets/local_validation_split_2.png)

1. 選擇&#x200B;**[!UICONTROL By data distribution]**&#x200B;選項，選擇以前建立的分發模板(請參閱[步驟1:建立資料分發範本](#step-1--creating-the-data-distribution-template-))，然後按一下&#x200B;**[!UICONTROL Finish]**。

   ![](assets/local_validation_split_3.png)

在分配模板中，我們選擇將人口限制為每個分組值10%，這與工作流中顯示的值一致（340作為輸入，34作為輸出）。

![](assets/local_validation_intro_1.png)

### 批准通知{#approval-notification}

**[!UICONTROL Local approval]**&#x200B;活動可讓您傳送通知給每個本機主管。

有關配置&#x200B;**[!UICONTROL Local approval]**&#x200B;活動的詳細資訊，請參閱[本地批准](../../workflow/using/local-approval.md)。

![](assets/local_validation_workflow_2.png)

需要輸入下列欄位：

1. 在 **[!UICONTROL Action to execute]** 區段中，選取 **[!UICONTROL Target approval notification]** 選項。
1. 在 **[!UICONTROL Distribution context]** 區段中，選取 **[!UICONTROL Specified in the transition]** 選項。

   如果不想限制目標人口，請在此處選擇&#x200B;**[!UICONTROL Explicit]**&#x200B;選項，然後在&#x200B;**[!UICONTROL Data distribution]**&#x200B;欄位中輸入先前建立的散發範本。

1. 在&#x200B;**[!UICONTROL Notification]**&#x200B;區段中，選取傳送範本和用於通知電子郵件的主題。 在此，我們選擇了預設模板：**[!UICONTROL Local approval notification]**。
1. 在&#x200B;**[!UICONTROL Approval schedule]**&#x200B;區段中，我們保留了預設的核准期限（3天）並新增提醒。 交貨將於批准開始後3天內結束。 在核准期限到達後，尚未核准的收件者就不會透過定位來考量。

**[!UICONTROL Local approval]**&#x200B;活動向本地主管發送的通知電子郵件如下：

![](assets/local_validation_intro_2.png)

### 等待 {#wait}

等待活動可讓您延遲第二個本機核准活動的開始，該活動將傳送傳送意見回應通知。 在&#x200B;**[!UICONTROL Duration]**&#x200B;欄位中，我們輸入了&#x200B;**[!UICONTROL 5d]**&#x200B;值（5天）。 收件者在傳送傳送後5天所執行的動作，會納入回饋通知中。

![](assets/local_validation_workflow_3.png)

### 反饋通知{#feedback-notification}

第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;活動可讓您傳送傳送意見通知給每個本機主管。

![](assets/local_validation_workflow_4.png)

需要輸入下列欄位。

1. 在&#x200B;**[!UICONTROL Action to execute]**&#x200B;部分，選擇&#x200B;**[!UICONTROL Delivery feedback report]**。
1. 在&#x200B;**[!UICONTROL Delivery]**&#x200B;部分，選擇&#x200B;**[!UICONTROL Specified in the transition]**。
1. 在&#x200B;**[!UICONTROL Notification]**&#x200B;區段中，選取傳送範本和用於通知電子郵件的主題。

在等待活動中配置的截止時間到達後，第二個&#x200B;**[!UICONTROL Local approval]**&#x200B;類型活動會向每個本地主管發送以下通知電子郵件：

![](assets/local_validation_intro_3.png)

### 管理員{#approval-tracking-by-the-administrator}的核准追蹤

每次啟動本地批准活動時，都會建立一個批准任務。 管理員可以控制這些核准工作。

前往促銷活動的定位工作流程，然後按一下&#x200B;**[!UICONTROL Local approval tasks]**&#x200B;標籤。

![](assets/local_validation_admin_1.png)

您也可以透過資料分發範本的&#x200B;**[!UICONTROL Approval tasks]**&#x200B;標籤來存取本機核准工作清單。

![](assets/local_validation_admin_2.png)

選擇要監視的任務，然後按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕。 本地批准任務的&#x200B;**[!UICONTROL General]**&#x200B;頁籤允許您查看有關該任務的資訊。 如有必要，您可以變更核准和提醒日期。

![](assets/local_validation_admin_3.png)

此頁籤顯示以下資訊：

* 任務的標籤及其ID
* 使用的散發範本
* 目標訊息數
* 連結的工作流程和促銷活動
* 任務計畫

任務的&#x200B;**[!UICONTROL Distribution]**&#x200B;標籤可讓您檢視核准記錄檔、其狀態、已定位的訊息數量、核准日期，以及核准傳送的運算子。

![](assets/local_validation_admin_4.png)

選擇批准日誌，然後按一下&#x200B;**[!UICONTROL Detail]**&#x200B;按鈕以顯示詳細資訊。 本機核准記錄的&#x200B;**[!UICONTROL General]**&#x200B;標籤可讓您檢視一般記錄資訊。 您也可以變更核准狀態。

![](assets/local_validation_admin_5.png)

此頁籤顯示以下資訊：

* 連結的核准工作
* 核准狀態（**[!UICONTROL Approved]**&#x200B;或&#x200B;**[!UICONTROL Pending]**）
* 使用的散發範本
* 批准和批准日期的當地主管
* 已定位和批准的消息數

核准記錄的&#x200B;**[!UICONTROL Targeted]**&#x200B;標籤會顯示目標收件者的清單及其核准狀態。 您可以視需要變更此狀態。

![](assets/local_validation_admin_6.png)

