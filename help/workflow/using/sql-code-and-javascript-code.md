---
product: campaign
title: SQL 程式碼和 JavaScript 程式碼
description: 進一步了解SQL和JavaScript程式碼工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: 8e6ebec9af0b7865616cf3904c8d400094567bdb
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 5%

---

# SQL 程式碼和 JavaScript 程式碼{#sql-code-and-javascript-code}

![](../../assets/common.svg)

## SQL代碼 {#sql-code}

安 **[!UICONTROL SQL code]** 活動執行SQL指令碼。 指令碼是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   編輯器的中央區域包含要執行的指令碼。 此指令碼是JST範本，因此可根據工作流程內容進行配置。

* **[!UICONTROL Processing errors]**

   請參閱 [處理錯誤](monitoring-workflow-execution.md#processing-errors).

## JavaScript程式碼和進階JavaScript程式碼 {#javascript-code}

**[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活動會在工作流程的內容中執行JavaScript指令碼。 有關指令碼的詳細資訊，請參閱以下部分：

* [JavaScript 指令碼和範本](javascript-scripts-and-templates.md)
* [工作流程中的JavaScript程式碼範例](javascript-in-workflows.md)

### 執行延遲 {#exec-delay}

自20.2版開始，已將執行延遲新增至 **[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活動。 預設情況下，執行階段不能超過1小時。 在此延遲後，程式會中止並顯示錯誤訊息，而活動執行會失敗。

您可以在 **[!UICONTROL Stop execution after]** 欄位。

若要忽略此限制，您必須將值設為 **0**.

### JavaScript程式碼 {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**:編輯器的中央區域包含要執行的指令碼。

* **[!UICONTROL Process errors]**:請參閱 [處理錯誤](monitoring-workflow-execution.md#processing-errors).

### 進階JavaScript程式碼 {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**:編輯器的第一個區域包含要在首次呼叫期間執行的指令碼。
* **[!UICONTROL Next calls]**:編輯器的第二個區域包含要在下次呼叫期間執行的指令碼。
* **[!UICONTROL Transitions]**:您可以定義數個活動輸出轉變。
* **[!UICONTROL Schedule]**:此 **[!UICONTROL Schedule]** 索引標籤可讓您排程觸發活動的時間。

進階JavaScript是一項永久性任務，如果尚未標示為已完成，則會定期回調。 要終止任務並防止將來的召回，您必須使用 **task.setCompleted()** 方法(在 **[!UICONTROL Next calls]** 小節：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
