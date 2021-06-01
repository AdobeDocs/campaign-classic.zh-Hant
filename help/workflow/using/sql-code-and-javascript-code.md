---
product: campaign
title: SQL 程式碼和 JavaScript 程式碼
description: 進一步了解SQL和JavaScript程式碼工作流程活動
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: 729a2010-c2d8-481b-8c9e-780b9e5f97ef
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 3%

---

# SQL 程式碼和 JavaScript 程式碼{#sql-code-and-javascript-code}

## SQL代碼{#sql-code}

**[!UICONTROL SQL code]**&#x200B;活動執行SQL指令碼。 指令碼是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   編輯器的中央區域包含要執行的指令碼。 此指令碼是JST範本，因此可根據工作流程內容進行配置。

* **[!UICONTROL Processing errors]**

   請參閱[處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

## JavaScript程式碼和進階JavaScript程式碼{#javascript-code}

**[!UICONTROL JavaScript code]** 和 **[!UICONTROL Advanced JavaScript code]** 活動會在工作流程的內容中執行JavaScript指令碼。有關指令碼的詳細資訊，請參閱[JavaScript指令碼和模板](../../workflow/using/javascript-scripts-and-templates.md)部分。

### 執行延遲{#exec-delay}

從20.2版開始，**[!UICONTROL JavaScript code]**&#x200B;和&#x200B;**[!UICONTROL Advanced JavaScript code]**&#x200B;活動已新增執行延遲。 預設情況下，執行階段不能超過1小時。 在此延遲後，程式會中止並顯示錯誤訊息，而活動執行會失敗。

您可以在這些活動中可用的&#x200B;**[!UICONTROL Stop execution after]**&#x200B;欄位中變更此延遲。

若要忽略此限制，您必須將值設為&#x200B;**0**。

### JavaScript程式碼{#js-code-desc}

![](assets/javascript_code.png)

* **[!UICONTROL Script]**:編輯器的中央區域包含要執行的指令碼。

* **[!UICONTROL Process errors]**:請參閱 [處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)。

### 進階JavaScript程式碼{#adv-js-code-desc}

![](assets/advanced_javascript_code.png)

* **[!UICONTROL First call]**:編輯器的第一個區域包含要在首次呼叫期間執行的指令碼。
* **[!UICONTROL Next calls]**:編輯器的第二個區域包含要在下次呼叫期間執行的指令碼。
* **[!UICONTROL Transitions]**:您可以定義數個活動輸出轉變。
* **[!UICONTROL Schedule]**:索引 **[!UICONTROL Schedule]** 標籤可讓您排程觸發活動的時間。

進階JavaScript是一項永久性任務，如果尚未標示為已完成，則會定期回調。 要終止任務並防止將來召回，必須使用&#x200B;**[!UICONTROL Next calls]**&#x200B;部分中的&#x200B;**task.setCompleted()**&#x200B;方法：

```
task.postEvent(task.transitionByName("ok")); // to transition to Ok branch
task.setCompleted();

return 0;
```
