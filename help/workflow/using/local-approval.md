---
solution: Campaign Classic
product: campaign
title: 本地核准
description: 本地核准
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---


# 本地核准{#local-approval}

當整合至定位工作流程時，**[!UICONTROL Local approval]**&#x200B;活動可讓您在傳送傳送之前設定收件者核准程式。

![](assets/local_validation_0.png)

>[!CAUTION]
>
>若要使用此活動，您必須購買Distributed Marketing模組，此為促銷活動選項。 請檢查您的授權合約。

有關&#x200B;**[!UICONTROL Local approval]**&#x200B;活動及分佈模板的示例，請參閱[使用本地批准活動](../../workflow/using/using-the-local-approval-activity.md)。

首先輸入活動的標籤和&#x200B;**[!UICONTROL Action to execute]**&#x200B;欄位：

![](assets/local_validation_1.png)

* 選擇&#x200B;**[!UICONTROL Target approval notification]**&#x200B;選項，在傳送前傳送通知電子郵件給本機主管，要求他們核准指派給他們的收件者。

   ![](assets/local_validation_intro_2.png)

* **增量查詢**:可讓您執行查詢並規劃其執行。請參閱[增量查詢](../../workflow/using/incremental-query.md)部分。

   ![](assets/local_validation_intro_3.png)

## 目標批准通知{#target-approval-notification}

在此情況下，**[!UICONTROL Local approval]**&#x200B;活動會置於上游定位和傳送之間：

![](assets/local_validation_2.png)

在通知目標審批時要輸入的欄位為：

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:如果您 **[!UICONTROL Specified in the transition]** 使用類型活動來限 **[!UICONTROL Split]** 制目標人口，請選取選項。在這種情況下，分配模板將輸入到分解活動中。 如果不限制目標人口，請在此處選擇&#x200B;**[!UICONTROL Explicit]**&#x200B;選項，然後在&#x200B;**[!UICONTROL Data distribution]**&#x200B;欄位中輸入分佈模板。

   有關建立資料分發模板的詳細資訊，請參閱[限制每個資料分發的子集記錄數](../../workflow/using/split.md#limiting-the-number-of-subset-records-per-data-distribution)。

* **[!UICONTROL Approval management]**

   * 選擇傳送範本和用於電子郵件通知的主題。 預設範本可供使用：**[!UICONTROL Local approval notification]**。 您也可以新增將出現在核准和回饋通知中收件者清單上方的說明。
   * 指定與核准截止日期（自核准開始起的日期或截止日期）對應的&#x200B;**[!UICONTROL Approval type]**。 在此日期，工作流程會再次啟動，而未核准的收件者不會納入定位。 傳送通知後，活動會排入佇列，讓本地主管可以核准其連絡人。

      >[!NOTE]
      >
      >依預設，當核准程式啟動時，活動會暫停3天。

      您也可以新增一或多個提醒，通知當地主管期限即將到來。 若要這麼做，請按一下&#x200B;**[!UICONTROL Add a reminder]**&#x200B;連結。

* **[!UICONTROL Complementary set]**:此選 **[!UICONTROL Generate complement]** 項可讓您產生第二組包含所有未核准目標的集合。

   >[!NOTE]
   >
   >此選項預設為停用。

## 傳送意見報告{#delivery-feedback-report}

在這種情況下，**[!UICONTROL Local approval]**&#x200B;活動會放在傳送後：

![](assets/local_validation_4.png)

如果是傳送意見報表，必須輸入下列欄位：

![](assets/local_validation_workflow_4.png)

* 如果傳送是在上一個活動期間輸入，請選取&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;選項。 選擇&#x200B;**[!UICONTROL Explicit]**&#x200B;以指定本機核准活動中的傳送。
* 選擇傳送範本和通知電子郵件的物件。 預設範本：**[!UICONTROL Local approval notification]**。

## 範例：批准工作流傳送{#example--approving-a-workflow-delivery}

此範例說明如何設定工作流程傳送的核准程式。 如需建立傳送工作流程的詳細資訊，請參閱[範例：傳送工作流程](../../workflow/using/delivery.md#example--delivery-workflow)區段。

營運商可透過下列兩種方式之一核准傳送：使用電子郵件訊息中連結的網頁，或透過主控台。

* 網頁核准

   傳送給管理員群組營運商的電子郵件可讓您核准傳送目標。 訊息會使用已定義的文字，而JavaScript運算式會由計算值取代（在本例中為&#39;574&#39;）

   若要核准傳送，請按一下相關連結並登入Adobe Campaign主控台。

   ![](assets/new-workflow-valid-webaccess.png)

   進行選擇，然後按一下&#x200B;**[!UICONTROL Submit]**&#x200B;按鈕。

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 透過主控台核准

   在樹結構中，**[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]**&#x200B;節點包含要由當前連接的操作員批准的任務清單。 清單應顯示一行。 連按兩下此行以回應。 將顯示以下窗口：

![](assets/new-workflow-7.png)

選擇&#x200B;**是** ，然後按一下&#x200B;**[!UICONTROL Approve]**。 訊息會通知您已記錄回覆。

返回工作流程螢幕：大約十秒後，圖顯示如下：

![](assets/new-workflow-8.png)

工作流已執行&#x200B;**[!UICONTROL Delivery control]**&#x200B;任務，在本例中，這表示開始先前建立的傳送。 工作流程已完成，但未出現錯誤。
