---
title: SQL程式碼和JavaScript程式碼
seo-title: SQL程式碼和JavaScript程式碼
description: SQL程式碼和JavaScript程式碼
seo-description: null
page-status-flag: never-activated
uuid: 20a39bbf-c6b0-4697-97b4-c07609cfb048
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 1afa75c2-7377-4d03-9105-11bcc9e3206c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 16e35b62cdf42c04139cc17645095a3d1f6e0fa7

---


# SQL程式碼和JavaScript程式碼{#sql-code-and-javascript-code}

## SQL代碼 {#sql-code}

*活動&#x200B;*[!UICONTROL SQL code*]* ，執行SQL指令碼。 該指令碼是JST模板。

![](assets/sql_code.png)

* **[!UICONTROL Script]**

   編輯器的中心區域包含要執行的指令碼。 此指令碼是JST模板，因此可以根據工作流上下文進行配置。

* **[!UICONTROL Processing errors]**

   請參閱「 [處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)」。

## JavaScript程式碼與進階JavaScript程式碼 {#javascript-code}

**[!UICONTROL JavaScript code]** 和活 **[!UICONTROL Advanced JavaScript code]** 動在工作流的上下文中執行JavaScript指令碼。 如需指令碼的詳細資訊，請參閱 [JavaScript指令碼和範本一節](../../workflow/using/javascript-scripts-and-templates.md) 。

>[!NOTE]
>
>預設情況下，活動和活動的執 **[!UICONTROL JavaScript code]** 行階 **[!UICONTROL Advanced JavaScript code]** 段不能超過1小時。 在此延遲後，進程將中止，並顯示錯誤消息，活動執行將失敗。
>
>您可以在活動屬性中可 **[!UICONTROL Stop execution after]** 用的欄位中更改此延遲。

* **[!UICONTROL JavaScript code]**

   ![](assets/javascript_code.png)

   * **[!UICONTROL Script]**:編輯器的中心區域包含要執行的指令碼。
   * **[!UICONTROL Processing errors]**:請參閱「 [處理錯誤](../../workflow/using/monitoring-workflow-execution.md#processing-errors)」。

* **[!UICONTROL Advanced JavaScript code]**

   ![](assets/advanced_javascript_code.png)

   * **[!UICONTROL First call]**:編輯器的第一個區域包含要在第一次調用期間執行的指令碼。
   * **[!UICONTROL Next calls]**:編輯器的第二個區域包含在下次調用期間執行的指令碼。
   * **[!UICONTROL Transitions]**:您可以定義數個活動輸出轉場。
   * **[!UICONTROL Schedule]**:此標 **[!UICONTROL Schedule]** 簽可讓您排程何時觸發活動。
