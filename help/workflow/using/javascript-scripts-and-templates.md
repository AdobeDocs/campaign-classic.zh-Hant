---
solution: Campaign Classic
product: campaign
title: JavaScript 指令碼和範本
description: JavaScript 指令碼和範本
audience: workflow
content-type: reference
topic-tags: advanced-management
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '1234'
ht-degree: 2%

---


# JavaScript 指令碼和範本{#javascript-scripts-and-templates}

指令碼使計算值、在進程中的不同任務之間交換資料以及使用SOAP調用執行特定操作成為可能。

指令碼在工作流程圖中隨處可見：

* 所有活動都有初始化指令碼。 初始化指令碼會在活動啟動時執行，並可用來初始化變數和修改屬性。
* 「JavaScript程式碼」活動僅用於執行指令碼。
* 「測試」活動會評估JavaScript運算式，以啟動適當的轉換。
* 大部分的文字欄位是JavaScript範本：JavaScript運算式可包含在&lt;%=和%>之間。 這些欄位提供一個按鈕，可開啟下拉式清單，以協助您輸入運算式。

   ![](assets/script-button.png)

## 公開的{#objects-exposed}對象

在工作流程的上下文中執行的JavaScripts會存取一系列額外的全域物件。

* **例項**:表示要執行的工作流。此對象的模式為&#x200B;**xtk:workflow**。
* **任務**:表示正在執行的任務。此對象的模式為&#x200B;**xtk:workflowTask**。
* **事件**:表示激活要執行的任務的事件。此物件的架構為&#x200B;**xtk:workflowEvent**。 此對象未初始化為&#x200B;**AND-join**&#x200B;類型活動，這些活動已從多個轉變中激活。
* **事件**:表示激活當前任務的事件清單。此物件的架構為&#x200B;**xtk:workflowEvent**。 此表通常包含一個元素，但可包含多個&#x200B;**AND-join**&#x200B;類型活動，這些活動已基於多個轉變而激活。
* **活動**:表示正在執行的任務的模型。此對象的模式取決於活動類型。 此對象可由初始化指令碼修改，在其它指令碼中，修改具有不可確定的效果。

按一下指令碼工具列右側的按鈕，即可在下拉式清單中檢視這些物件的可用屬性。

>[!CAUTION]
>
>這些對象的屬性是只讀的，vars屬性的子屬性除外。
>  
>這些屬性中的大部分只有在執行基本任務或實例被鈍化後才會更新。 讀取的值不一定與當前狀態匹配，而是與前一個狀態匹配。

**範例**

在此範例和下列範例中，建立包含&#x200B;**JavaScript程式碼**&#x200B;活動和&#x200B;**End**&#x200B;活動的工作流程，如下圖所示。

![](assets/script-1.png)

連按兩下&#x200B;**JavaScript程式碼**&#x200B;活動並插入下列指令碼：

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

**[!UICONTROL logInfo(message)]**&#x200B;函式將消息插入日誌中。

按一下&#x200B;**[!UICONTROL OK]**&#x200B;關閉建立嚮導，然後使用位於工作流清單右上方的操作按鈕啟動工作流。 執行結束時，請查閱記錄檔。 您應該會看到與指令碼對應的兩則訊息：一個顯示工作流的標籤，另一個顯示指令碼激活的日期。

## 變數{#variables}

變數是&#x200B;**[!UICONTROL instance]**、**[!UICONTROL task]**&#x200B;和&#x200B;**[!UICONTROL event]**&#x200B;對象的自由屬性。 授權這些變數的JavaScript類型有&#x200B;**[!UICONTROL string]**、**[!UICONTROL number]**&#x200B;和&#x200B;**[!UICONTROL Date]**。

### 例項變數{#instance-variables}

例項變數(**[!UICONTROL instance.vars.xxx]**)可與全域變數比較。 所有活動都會共用。

### 任務變數{#task-variables}

任務變數(**[!UICONTROL task.vars.xxx]**)與本地變數相當。 它們僅用於當前任務。 這些變數會由持續性活動使用，以保留資料，有時也會用來在相同活動的不同指令碼之間交換資料。

### 事件變數{#event-variables}

事件變數(**[!UICONTROL vars.xxx]**)可在工作流進程的基本任務之間交換資料。 這些變數由啟動進行中任務的任務傳遞。 可以修改它們並定義新的。 然後，會將它們傳遞至下列活動。

>[!CAUTION]
>
>對於[AND-join](../../workflow/using/and-join.md)類型活動，會合併變數，但如果同一個變數定義了兩次，則會發生衝突，且值仍未確定。

事件是最常使用的變數，應優先使用它們來取代例項變數。

某些事件變數會由各種活動修改或讀取。 這些都是字串類型變數。 例如，匯出會設定&#x200B;**[!UICONTROL vars.filename]**&#x200B;變數，其名稱為剛匯出的檔案。 所有這些讀取或修改的變數都記錄在[關於活動](../../workflow/using/about-activities.md)中，位於活動的&#x200B;**輸入參數**&#x200B;和&#x200B;**輸出參數**&#x200B;節中。

### 使用案例 {#example}

>[!NOTE]
>
>[本節](../../workflow/using/about-workflow-use-cases.md)中提供了其他工作流使用案例。

**範例1**

在此範例中，例項變數可用來動態計算分割百分比以套用至人口族群。

1. 建立工作流程並新增「開始」活動。

1. 新增及設定JavaScript程式碼活動以定義例項變數。

   例如：`instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. 根據您的需求新增查詢活動和目標收件者。

1. 新增「分割」活動，並設定它以執行傳入人口的隨機取樣。 取樣百分比可以是您選擇的任何項目。 在本例中，它設為50%。

   這個百分比會因先前定義的例項變數而動態更新。

   ![](assets/js_ex2.png)

1. 在「分割」活動「進階」標籤的「初始化指令碼」區段內，定義JS條件。 JS條件會選取來自「分割」活動之第一個轉場的隨機取樣百分比，並將其更新為先前建立之例項變數所設定的值。

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. 請確定補碼是在分割活動的個別轉場中產生，並在每次出站轉場後新增結束活動。

1. 儲存並執行工作流程。 動態採樣根據實例變數被應用。

   ![](assets/js_ex4.png)

**範例2**

1. 從上例中的工作流程，將&#x200B;**JavaScript代碼**&#x200B;活動的指令碼替換為以下指令碼：

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. 將以下指令碼添加到&#x200B;**End**&#x200B;活動的初始化指令碼中：

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. 啟動工作流程，然後查看記錄檔。

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

此範例顯示&#x200B;**JavaScript程式碼**&#x200B;後續的活動會存取例項變數和事件變數，但無法從外部存取工作變數(&#39;undefined&#39;)。

### 調用查詢中的執行個體變數 {#calling-an-instance-variable-in-a-query}

在活動中指定例項變數後，您就可以在工作流程查詢中重新使用它。

因此，要在過濾器中調用變數&#x200B;**instance.vars.xxx = &quot;yyy&quot;**，請輸入&#x200B;**$(instance/vars/xxx)**。

例如：

1. 建立例項變數，透過&#x200B;**[!UICONTROL JavaScript code]**&#x200B;定義傳送的內部名稱：**instance.vars.deliveryIN = &quot;DM42&quot;**。

   ![](assets/wkf_js_activity_1.png)

1. 建立其定位和篩選維度為收件者的查詢。 在條件中，指定您想要尋找所有傳送變數所指定之傳送的收件者。

   提醒時，此資訊會儲存在傳送記錄檔中。

   若要參考&#x200B;**[!UICONTROL Value]**&#x200B;欄中的例項變數，請輸入&#x200B;**$(instance/vars/@deliveryIN)**。

   工作流將返回DM42交付的收件人。

   ![](assets/wkf_var_in_query.png)

## 進階函式 {#advanced-functions}

除了標準JavaScript函式外，還提供特殊函式，可用來控制檔案、讀取或修改資料庫中的資料，或將訊息新增至記錄檔。

### 日誌{#journal}

**[!UICONTROL logInfo(message)]** 在上述範例中詳細說明。此函式將資訊消息添加到日誌中。

**[!UICONTROL logError(message)]** 將錯誤消息添加到日誌中。指令碼會中斷執行，而工作流程會變更為錯誤狀態（依預設會暫停執行個體）。

## 初始化指令碼{#initialization-script}

在特定條件下，您可以在執行時修改活動的屬性。

活動的大部分屬性都可以動態計算，不論是使用JavaScript範本，還是因為工作流程屬性明確允許指令碼計算值。

但是，對於其他屬性，您必須使用初始化指令碼。 執行任務之前會評估此指令碼。 **[!UICONTROL activity]**&#x200B;變數會參照與任務對應的活動。 可修改此活動的屬性，並僅影響此任務。
