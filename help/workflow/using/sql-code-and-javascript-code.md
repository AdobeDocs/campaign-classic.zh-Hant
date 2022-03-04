---
product: campaign
title: SQL 程式碼和 JavaScript 程式碼
description: 瞭解有關SQL和JavaScript代碼工作流活動的詳細資訊
feature: Workflows
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: b94c4bfd478b4a8fbcefe6341608dd6a14bb31d3
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 7%

---

# SQL 程式碼和 JavaScript 程式碼{#sql-code-and-javascript-code}

![](../../assets/common.svg)

## SQL代碼 {#sql-code}

安 **[!UICONTROL SQL code]** 活動執行SQL指令碼。 指令碼是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   編輯器的中心區域包含要執行的指令碼。 此指令碼是JST模板，因此可以根據工作流上下文進行配置。

* **[!UICONTROL Processing errors]**

   請參閱 [處理錯誤](monitoring-workflow-execution.md#processing-errors)。

## JavaScript代碼和高級JavaScript代碼 {#javascript-code}

**[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活動在工作流上下文中執行JavaScript指令碼。 有關指令碼的詳細資訊，請參閱以下各節：

* [JavaScript 指令碼和範本](javascript-scripts-and-templates.md)
* [工作流程中的 JavaScript 程式碼範例](javascript-in-workflows.md)

### 執行延遲 {#exec-delay}

從20.2版開始，向 **[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活動。 預設情況下，執行階段不能超過1小時。 在此延遲後，進程將中止，並顯示錯誤消息，活動執行將失敗。

您可以在 **[!UICONTROL Stop execution after]** 欄位。

要忽略此限制，需要將值設定為 **0**。

### JavaScript代碼 {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**:編輯器的中心區域包含要執行的指令碼。

* **[!UICONTROL Process errors]**:請參閱 [處理錯誤](monitoring-workflow-execution.md#processing-errors)。

### 高級JavaScript代碼 {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**:編輯器的第一個區域包含在第一次調用期間執行的指令碼。
* **[!UICONTROL Next calls]**:編輯器的第二個區域包含在下次調用期間執行的指令碼。
* **[!UICONTROL Transitions]**:可以定義多個活動輸出過渡。
* **[!UICONTROL Schedule]**:的 **[!UICONTROL Schedule]** 頁籤中，您可以計畫何時觸發活動。

高級JavaScript是一個持久性任務，如果尚未標籤為已完成，則會定期回調。 要終止任務並防止將來的召回，必須使用 **task.setCompleted()** 中 **[!UICONTROL Next calls]** 部分：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
