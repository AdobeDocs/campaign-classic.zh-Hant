---
solution: Campaign Classic
product: campaign
title: SQL 程式碼和 JavaScript 程式碼
description: 進一步瞭解SQL和JavaScript程式碼工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
translation-type: tm+mt
source-git-commit: add0efb4efd5a37129c649b942799622947f3143
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---


# SQL 程式碼和 JavaScript 程式碼{#sql-code-and-javascript-code}

## SQL代碼{#sql-code}

**[!UICONTROL SQL code]**&#x200B;活動執行SQL指令碼。 該指令碼是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   編輯器的中心區域包含要執行的指令碼。 此指令碼是JST模板，因此可以根據工作流上下文進行配置。

* **[!UICONTROL Processing errors]**

   請參閱[處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## JavaScript程式碼和進階JavaScript程式碼{#javascript-code}

**[!UICONTROL JavaScript code]** 和活 **[!UICONTROL Advanced JavaScript code]** 動在工作流的上下文中執行JavaScript指令碼。有關指令碼的詳細資訊，請參閱[JavaScript指令碼和模板](../../workflow/using/javascript-scripts-and-templates.md)部分。

### 執行延遲{#exec-delay}

從20.2版開始，**[!UICONTROL JavaScript code]**&#x200B;和&#x200B;**[!UICONTROL Advanced JavaScript code]**&#x200B;活動已添加執行延遲。 依預設，執行階段不能超過1小時。 在此延遲後，進程將中止，並顯示錯誤消息，活動執行將失敗。

您可以在這些活動中的&#x200B;**[!UICONTROL Stop execution after]**&#x200B;欄位中更改此延遲。

若要忽略此限制，您必須將值設為&#x200B;**0**。

### JavaScript程式碼{#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**:編輯器的中心區域包含要執行的指令碼。

* **[!UICONTROL Process errors]**:請參閱「 [處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)」。

### 進階JavaScript程式碼{#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**:編輯器的第一個區域包含要在第一次調用期間執行的指令碼。
* **[!UICONTROL Next calls]**:編輯器的第二個區域包含在下次調用期間執行的指令碼。
* **[!UICONTROL Transitions]**:您可以定義數個活動輸出轉場。
* **[!UICONTROL Schedule]**:此標 **[!UICONTROL Schedule]** 簽可讓您排程何時觸發活動。

進階JavaScript是一項永續性工作，如果尚未標示為完成，則會定期回調它。 要終止任務並防止將來召回，您必須使用&#x200B;**[!UICONTROL Next calls]**&#x200B;部分中的&#x200B;**task.setCompleted()**&#x200B;方法：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
