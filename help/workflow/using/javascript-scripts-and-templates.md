---
title: JavaScript指令碼和範本
seo-title: JavaScript指令碼和範本
description: JavaScript指令碼和範本
seo-description: null
page-status-flag: never-activated
uuid: d341a892-dc71-4413-acb8-9cba372b38cf
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: advanced-management
discoiquuid: 8867d9c3-2ce4-4611-8c88-ce505c3a01d1
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 9d36192a768fd0162f2301a5fe0437074d0fda58

---


# JavaScript指令碼和範本{#javascript-scripts-and-templates}

指令碼使計算值、在進程中的不同任務之間交換資料以及使用SOAP調用執行特定操作成為可能。

指令碼在工作流程圖中隨處可見：

* 所有活動都有初始化指令碼。 初始化指令碼會在活動啟動時執行，並可用來初始化變數和修改屬性。
* 「JavaScript程式碼」活動僅用於執行指令碼。
* 「測試」活動會評估JavaScript運算式，以啟動適當的轉換。
* 大部分的文字欄位是JavaScript範本：JavaScript運算式可包含在&lt;%=和%>之間。 這些欄位提供一個按鈕，可開啟下拉式清單，以協助您輸入運算式。

   ![](assets/script-button.png)

## 公開的物件 {#objects-exposed}

在工作流程的上下文中執行的JavaScripts會存取一系列額外的全域物件。

* **例項**:表示要執行的工作流。 此對象的模式為 **xtk:workflow**。
* **任務**:表示正在執行的任務。 此對象的模式為 **xtk:workflowTask**。
* **事件**:表示激活要執行的任務的事件。 此物件的架構為 **xtk:workflowEvent**。 此對象未初始化為 **AND-join** type活動，這些活動已從多個轉變中激活。
* **事件**:表示激活當前任務的事件清單。 此物件的架構為 **xtk:workflowEvent**。 此表通常包含一個元素，但可能包含 **AND-join** type活動的數個元素，這些活動已基於多個轉變而激活。
* **活動**:表示正在執行的任務的模型。 此對象的模式取決於活動類型。 此對象可由初始化指令碼修改，在其它指令碼中，修改具有不可確定的效果。

按一下指令碼工具列右側的按鈕，即可在下拉式清單中檢視這些物件的可用屬性。

>[!CAUTION]
>
>這些對象的屬性是只讀的，vars屬性的子屬性除外。
>  
>這些屬性中的大部分只有在執行基本任務或實例被鈍化後才會更新。 讀取的值不一定與當前狀態匹配，而是與前一個狀態匹配。

**範例**

在此範例和下列範例中，建立包含 **JavaScript程式碼活動和** End **** 活動的工作流程，如下圖所示。

![](assets/script-1.png)

連按兩下 **JavaScript程式碼活動** ，並插入下列指令碼：

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

函式 **[!UICONTROL logInfo(message)]** 將消息插入日誌中。

按一 **[!UICONTROL OK]** 下以關閉建立精靈，然後使用位於工作流程清單右上方的動作按鈕來啟動工作流程。 執行結束時，請查閱記錄檔。 您應該會看到與指令碼對應的兩則訊息：一個顯示工作流的標籤，另一個顯示指令碼激活的日期。

## 變數 {#variables}

變數是對象和對象的 **[!UICONTROL instance]**&#x200B;自由 **[!UICONTROL task]** 屬 **[!UICONTROL event]** 性。 為這些變數授權的JavaScript類型 **[!UICONTROL string]**&#x200B;為 **[!UICONTROL number]** 和 **[!UICONTROL Date]**。

### 例項變數 {#instance-variables}

例項變數(**[!UICONTROL instance.vars.xxx]**)可與全域變數比較。 所有活動都會共用。

### 任務變數 {#task-variables}

任務變數(**[!UICONTROL task.vars.xxx]**)可與局部變數相比。 它們僅用於當前任務。 這些變數會由持續性活動使用，以保留資料，有時也會用來在相同活動的不同指令碼之間交換資料。

### 事件變數 {#event-variables}

事件變數(**[!UICONTROL vars.xxx]**)可讓工作流程程式的基本任務之間交換資料。 這些變數由啟動進行中任務的任務傳遞。 可以修改它們並定義新的。 然後，會將它們傳遞至下列活動。

對於 **AND-join** type活動，會合併變數，但如果同一個變數定義了兩次，則會發生衝突，且值仍未確定。

這些是最常使用的變數，應優先使用於例項變數。

某些事件變數會由各種活動修改或讀取。 這些都是字串類型變數。 例如，匯出會以剛 **[!UICONTROL vars.filename]** 匯出的檔案的完整名稱來設定變數。 所有這些讀取或修改的變數都記錄在活 [動的](../../workflow/using/about-activities.md)About活動中， **活動的Input參數****** 和Output參數中。

### 範例 {#example}

**範例1**

在此範例中，例項變數可用來動態計算分割百分比以套用至人口族群。

1. 建立工作流程並新增「開始」活動。

1. 新增及設定JavaScript程式碼活動以定義例項變數。

   For example: `instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. 根據您的需求新增查詢活動和目標收件者。

1. 新增「分割」活動，並設定它以執行傳入人口的隨機取樣。 取樣百分比可以是您選擇的任何項目。 在本例中，它設為50%。

   這個百分比會動態更新，這要歸功於先前定義的例項變數。

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

1. 從上述範例中，將工作流程以下列指令碼取代 **JavaScript程式碼活動的指令碼** :

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. 將以下指令碼添加到 **End** 活動的初始化指令碼：

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

此範例顯示 **** JavaScript程式碼後的活動會存取例項變數和事件變數，但是無法從外部存取工作變數(&#39;undefined&#39;)。

### 呼叫查詢中的例項變數 {#calling-an-instance-variable-in-a-query}

在活動中指定例項變數後，您就可以在工作流程查詢中重新使用它。

因此，若要在篩選器中呼 **叫變數instance.vars.xxx = &quot;yyy&quot;** ，請輸 **入$(instance/vars/xxx)**。

例如：

1. 建立例項變數，透過下列網址定義傳送的內部名稱 **[!UICONTROL JavaScript code]**: **instance.vars.deliveryIN = &quot;DM42&quot;**。

   ![](assets/wkf_js_activity_1.png)

1. 建立其定位和篩選維度為收件者的查詢。 在條件中，指定您想要尋找所有傳送變數所指定之傳送的收件者。

   提醒時，此資訊會儲存在傳送記錄檔中。

   若要參考欄中的例 **[!UICONTROL Value]** 項變數，請 **輸入$(instance/vars/@deliveryIN)**。

   工作流將返回DM42交付的收件人。

   ![](assets/wkf_var_in_query.png)

## 進階函式 {#advanced-functions}

除了標準JavaScript函式外，還提供特殊函式，可用來控制檔案、讀取或修改資料庫中的資料，或將訊息新增至記錄檔。

### 日誌 {#journal}

**[!UICONTROL logInfo(message)]** 在上述範例中詳細說明。 此函式將資訊消息添加到日誌中。

**[!UICONTROL logError(message)]** 將錯誤消息添加到日誌中。 指令碼會中斷執行，而工作流程會變更為錯誤狀態（依預設會暫停執行個體）。

## 初始化指令碼 {#initialization-script}

在特定條件下，您可以在執行時修改活動的屬性。

活動的大部分屬性都可以動態計算，不論是使用JavaScript範本，還是因為工作流程屬性明確允許指令碼計算值。

但是，對於其他屬性，您必須使用初始化指令碼。 執行任務之前會評估此指令碼。 變 **[!UICONTROL activity]** 數會參照與任務對應的活動。 可修改此活動的屬性，並僅影響此任務。
