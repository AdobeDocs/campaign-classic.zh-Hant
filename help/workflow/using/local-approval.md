---
product: campaign
title: 本地核准
description: 本地核准
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 本地核准{#local-approval}

![](../../assets/common.svg)

整合至目標工作流程時， **[!UICONTROL Local approval]** 活動可讓您在傳送傳遞前設定收件者核准程式。

![](assets/local_validation_0.png)

>[!CAUTION]
>
>若要使用此活動，您必須已購買「分散式行銷」模組（此為「促銷活動」選項）。 請檢查您的授權合約。

例如 **[!UICONTROL Local approval]** 具有發佈範本的活動，請參閱 [使用本機核准活動](using-the-local-approval-activity.md).

首先，輸入活動的標籤，然後 **[!UICONTROL Action to execute]** 欄位：

![](assets/local_validation_1.png)

* 選取 **[!UICONTROL Target approval notification]** 選項，在傳送前傳送通知電子郵件給本機主管，要求他們核准指派給他們的收件者。

   ![](assets/local_validation_intro_2.png)

* **增量查詢**:可讓您執行查詢並規劃其執行。 請參閱 [增量查詢](incremental-query.md) 區段。

   ![](assets/local_validation_intro_3.png)

## Target核准通知 {#target-approval-notification}

在此情況下， **[!UICONTROL Local approval]** 活動會置於上游鎖定目標和傳送之間：

![](assets/local_validation_2.png)

在進行目標批准通知時要輸入的欄位為：

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:選取 **[!UICONTROL Specified in the transition]** 選項 **[!UICONTROL Split]** 類型活動以限制目標母體。 在這種情況下，分配模板將輸入到拆分活動中。 如果您不限制目標母體，請選取 **[!UICONTROL Explicit]** ，並在 **[!UICONTROL Data distribution]** 欄位。

   如需建立資料分送範本的詳細資訊，請參閱 [限制每個資料分發的子集記錄數](split.md#limiting-the-number-of-subset-records-per-data-distribution).

* **[!UICONTROL Approval management]**

   * 選取用於電子郵件通知的傳送範本和主旨。 預設範本可供使用： **[!UICONTROL Local approval notification]**. 您也可以新增說明，該說明將出現在核准和意見通知的收件者清單上方。
   * 指定 **[!UICONTROL Approval type]** 與核准截止日期（自核准開始之日期或截止日期）相對應。 此日期時，工作流程會再次開始，且目標定位中不會考慮尚未核准的收件者。 傳送通知後，活動會排入佇列，讓本機主管可以核准其聯絡人。

      >[!NOTE]
      >
      >依預設，當核准程式啟動時，活動會暫停三天。

      您也可以新增一或多個提醒，通知當地主管截止日期即將到來。 若要這麼做，請按一下 **[!UICONTROL Add a reminder]** 連結。

* **[!UICONTROL Complementary set]**:the **[!UICONTROL Generate complement]** 選項可讓您產生第二組，其中包含所有未核准的目標。

   >[!NOTE]
   >
   >預設會停用此選項。

## 傳遞意見報告 {#delivery-feedback-report}

在此情況下， **[!UICONTROL Local approval]** 活動會放在傳送之後：

![](assets/local_validation_4.png)

若是傳送意見報表，必須輸入下列欄位：

![](assets/local_validation_workflow_4.png)

* 選取 **[!UICONTROL Specified in the transition]** 選項。 選擇 **[!UICONTROL Explicit]** 指定本機核准活動中的傳送。
* 選取傳送範本和通知電子郵件的物件。 預設範本如下： **[!UICONTROL Local approval notification]**.

## 範例：核准工作流程傳送 {#example--approving-a-workflow-delivery}

此範例說明如何設定工作流程傳送的核准程式。 如需建立傳送工作流程的詳細資訊，請參閱 [範例：傳遞工作流程](delivery.md#example--delivery-workflow) 區段。

運算子可透過下列兩種方式之一核准傳送：使用電子郵件中連結的網頁，或透過主控台。

* 網路核准

   傳送給管理員群組運算子的電子郵件可讓您核准傳送目標。 訊息會使用定義的文字，而JavaScript運算式會取代為計算值（在此例中為&#39;574&#39;）

   若要核准傳送，請按一下相關連結並登入Adobe Campaign主控台。

   ![](assets/new-workflow-valid-webaccess.png)

   進行選擇，然後按一下 **[!UICONTROL Submit]** 按鈕。

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 透過主控台核准

   在樹結構中， **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 節點包含當前連接的操作員要批准的任務清單。 清單應顯示一行。 按兩下此行以響應。 將顯示以下窗口：

![](assets/new-workflow-7.png)

選擇 **是**，然後按一下 **[!UICONTROL Approve]**. 系統會傳送訊息通知您回應已記錄。

返回工作流程畫面：大約10秒後，圖表顯示如下：

![](assets/new-workflow-8.png)

工作流程已執行 **[!UICONTROL Delivery control]** 任務，在此情況下，這表示開始先前建立的傳送。 工作流程已完成，未發生錯誤。
