---
product: campaign
title: SQL 程式碼和 JavaScript 程式碼
description: 深入瞭解SQL和JavaScript程式碼工作流程活動
feature: Workflows
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: b666535f7f82d1b8c2da4fbce1bc25cf8d39d187
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 13%

---

# SQL 程式碼和 JavaScript 程式碼{#sql-code-and-javascript-code}



## SQL 程式碼 {#sql-code}

**[!UICONTROL SQL code]**&#x200B;活動會執行SQL指令碼。 指令碼是JST範本。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

  編輯器的中央區域包含要執行的指令碼。 此指令碼是JST範本，因此可根據工作流程內容進行設定。

* **[!UICONTROL Processing errors]**

  請參閱[處理錯誤](monitoring-workflow-execution.md#processing-errors)。

## JavaScript程式碼和進階JavaScript程式碼 {#javascript-code}

**[!UICONTROL JavaScript code]**&#x200B;和&#x200B;**[!UICONTROL Advanced JavaScript code]**&#x200B;活動會在工作流程的內容中執行JavaScript指令碼。 如需指令碼的詳細資訊，請參閱下列章節：

* [JavaScript 指令碼和範本](javascript-scripts-and-templates.md)
* [工作流程中的 JavaScript 程式碼範例](javascript-in-workflows.md)

### 執行延遲 {#exec-delay}

自20.2發行版本開始，**[!UICONTROL JavaScript code]**&#x200B;和&#x200B;**[!UICONTROL Advanced JavaScript code]**&#x200B;活動已新增執行延遲。 依預設，執行階段不能超過 1 小時。在此延遲後，流程將中止並顯示錯誤訊息，活動執行將失敗。

您可以在下列活動中可用的&#x200B;**[!UICONTROL Stop execution after]**&#x200B;欄位中變更此延遲。

若要忽略此限制，您必須將值設定為&#x200B;**0**。

### JavaScript 程式碼 {#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**：編輯器的中央區域包含要執行的指令碼。

* **[!UICONTROL Process errors]**：請參考[處理錯誤](monitoring-workflow-execution.md#processing-errors)。

### 進階 JavaScript 程式碼 {#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**：編輯器的第一個區域包含要在第一次呼叫期間執行的指令碼。
* **[!UICONTROL Next calls]**：編輯器的第二個區域包含下次呼叫時要執行的指令碼。
* **[!UICONTROL Transitions]**：您可以定義數個活動輸出轉變。
* **[!UICONTROL Schedule]**： **[!UICONTROL Schedule]**&#x200B;索引標籤可讓您排程何時觸發活動。

進階JavaScript是一項持續性的工作，如果未標示為已完成，則會定期召回。 若要終止工作並防止將來重新呼叫，您必須使用&#x200B;**[!UICONTROL Next calls]**&#x200B;區段中的&#x200B;**task.setCompleted()**&#x200B;方法：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
