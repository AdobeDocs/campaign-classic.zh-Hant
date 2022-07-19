---
product: campaign
title: 本地核准
description: 本地核准
feature: Workflows
exl-id: 2d9cbfc8-1f99-4b38-8460-77c7c986e9ca
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 1%

---

# 本地核准{#local-approval}

![](../../assets/v7-only.svg)

整合到目標工作流時， **[!UICONTROL Local approval]** 「活動」(Activity)，用於在發送交貨之前設定收件人審批流程。

![](assets/local_validation_0.png)

>[!CAUTION]
>
>要使用此活動，您需要購買「分佈式市場營銷」模組（即「市場活動」選項）。 請檢查您的授權合約。

例如 **[!UICONTROL Local approval]** 包含分發模板的活動，請參閱 [使用本地審批活動](using-the-local-approval-activity.md)。

首先輸入活動和 **[!UICONTROL Action to execute]** 欄位：

![](assets/local_validation_1.png)

* 選擇 **[!UICONTROL Target approval notification]** 選項，在傳遞之前向本地主管發送電子郵件通知，要求他們批准分配給他們的收件人。

   ![](assets/local_validation_intro_2.png)

* **增量查詢**:允許您執行查詢並計畫其執行。 請參閱 [增量查詢](incremental-query.md) 的子菜單。

   ![](assets/local_validation_intro_3.png)

## 目標審批通知 {#target-approval-notification}

在這個例子中， **[!UICONTROL Local approval]** 活動位於上游目標和交貨之間：

![](assets/local_validation_2.png)

在目標審批通知時要輸入的欄位為：

![](assets/local_validation_3.png)

* **[!UICONTROL Distribution context]**:選擇 **[!UICONTROL Specified in the transition]** 選項 **[!UICONTROL Split]** 類型活動以限制目標人口。 在這種情況下，分配模板將輸入到分解活動中。 如果不限制目標人口，請選擇 **[!UICONTROL Explicit]** 的子菜單。 **[!UICONTROL Data distribution]** 的子菜單。

   有關建立資料分發模板的詳細資訊，請參閱 [限制每個資料分佈的子集記錄數](split.md#limiting-the-number-of-subset-records-per-data-distribution)。

* **[!UICONTROL Approval management]**

   * 選擇用於電子郵件通知的傳遞模板和主題。 預設模板可用： **[!UICONTROL Local approval notification]**。 您還可以添加將在審批和反饋通知中的收件人清單上方顯示的說明。
   * 指定 **[!UICONTROL Approval type]** 與批准截止時間（從批准開始的日期或截止時間）相對應。 在此日期，工作流將再次啟動，目標中不會考慮尚未批准的收件人。 通知發送後，活動將排隊，以便本地主管可以批准其聯繫人。

      >[!NOTE]
      >
      >預設情況下，當啟動審批流程時，活動將暫停三天。

      您還可以添加一個或多個提醒以通知本地主管截止時間即將到來。 要執行此操作，請按一下 **[!UICONTROL Add a reminder]** 的子菜單。

* **[!UICONTROL Complementary set]**:這樣 **[!UICONTROL Generate complement]** 選項，您可以生成包含所有未批准目標的第二個集。

   >[!NOTE]
   >
   >預設情況下禁用此選項。

## 交貨反饋報告 {#delivery-feedback-report}

在這個例子中， **[!UICONTROL Local approval]** 活動在交貨後放置：

![](assets/local_validation_4.png)

如果是交貨反饋報告，則必須輸入以下欄位：

![](assets/local_validation_workflow_4.png)

* 選擇 **[!UICONTROL Specified in the transition]** 的子菜單。 選擇 **[!UICONTROL Explicit]** 指定本地審批活動中的交貨。
* 選擇傳遞模板和通知電子郵件的對象。 有一個預設模板： **[!UICONTROL Local approval notification]**。

## 示例：批准工作流交付 {#example--approving-a-workflow-delivery}

此示例說明如何設定工作流交付的審批流程。 有關建立交貨工作流的詳細資訊，請參閱 [示例：交付工作流](delivery.md#example--delivery-workflow) 的子菜單。

操作員可以通過以下兩種方式之一批准交貨：使用電子郵件中連結的網頁，或通過控制台。

* Web審批

   發送到管理員組的操作員的電子郵件允許您批准傳遞目標。 消息使用定義的文本，JavaScript表達式將替換為計算值（在本例中為「574」）

   要批准交付，請按一下相關連結並登錄到Adobe Campaign控制台。

   ![](assets/new-workflow-valid-webaccess.png)

   選擇並按一下 **[!UICONTROL Submit]** 按鈕

   ![](assets/new-workflow-valid-webaccess-confirm.png)

* 通過控制台批准

   在樹結構中， **[!UICONTROL Administration > Production > Objects created automatically > Approvals pending]** 節點包含當前連接的操作員要批准的任務清單。 清單應顯示一行。 按兩下此行以響應。 將顯示以下窗口：

![](assets/new-workflow-7.png)

選擇 **是**，然後按一下 **[!UICONTROL Approve]**。 一條消息將通知您已記錄響應。

返回至工作流螢幕：大約10秒後，圖顯示如下：

![](assets/new-workflow-8.png)

工作流已執行 **[!UICONTROL Delivery control]** 任務，在本例中，這意味著開始以前建立的傳遞。 工作流已完成，但無錯誤。
