---
product: campaign
title: JavaScript 指令碼和範本
description: JavaScript 指令碼和範本
feature: Workflows
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1242'
ht-degree: 2%

---

# JavaScript 指令碼和範本{#javascript-scripts-and-templates}

![](../../assets/v7-only.svg)

指令碼使計算值、在進程中的不同任務之間交換資料以及使用SOAP調用執行特定操作成為可能。

指令碼在工作流圖中無處不在：

* 所有活動都具有初始化指令碼。 激活活動時執行初始化指令碼，可用於初始化變數和修改屬性。
* 「JavaScript代碼」活動僅用於執行指令碼。
* 「Test」活動會計算JavaScript表達式，以激活適當的轉換。
* 大多數文本欄位是JavaScript模板：JavaScript表達式可以包含在&lt;%=和%>之間。 這些欄位提供一個按鈕，用於開啟下拉清單以幫助您輸入表達式。

   ![](assets/script-button.png)

## 公開的對象 {#objects-exposed}

在工作流上下文中執行的JavaScript訪問一系列附加全局對象。

* **實例**:表示正在執行的工作流。 此對象的架構為 **xtk：工作流**。
* **任務**:表示正在執行的任務。 此對象的架構為 **xtk：工作流任務**。
* **事件**:表示激活正在執行的任務的事件。 此對象的架構為 **xtk:workflowEvent**。 此對象未初始化 **與連接** 鍵入已從多個轉變中激活的活動。
* **事件**:表示激活當前任務的事件清單。 此對象的架構為 **xtk:workflowEvent**。 此表通常包含一個元素，但可能包含多個 **與連接** 類型活動，這些活動已基於多個過渡激活。
* **活動**:表示正在執行的任務的模型。 此對象的架構取決於活動類型。 此對象可由初始化指令碼修改，在其他指令碼中，修改具有不可確定的效果。

通過按一下指令碼工具欄右側的按鈕，可以在下拉清單中查看這些對象的可用屬性。

>[!CAUTION]
>
>這些對象的屬性是只讀的，vars屬性的子屬性除外。
>  
>這些屬性中的大多數只有在執行基本任務或實例被鈍化後才能更新。 讀取的值不一定與當前狀態匹配，而是與上一個狀態匹配。

**範例**

在本示例中，以及在以下示例中，建立一個包含 **JavaScript代碼** 活動和 **結束** 如下圖所示。

![](assets/script-1.png)

按兩下 **JavaScript代碼** 並插入以下指令碼：

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

的 **[!UICONTROL logInfo(message)]** 函式將消息插入日誌。

按一下 **[!UICONTROL OK]** 要關閉建立嚮導，請使用位於工作流清單右上角的操作按鈕啟動工作流。 在執行結束時，請查閱日誌。 您應看到與指令碼對應的兩條消息：一個顯示工作流的標籤，另一個顯示指令碼激活的日期。

## 變數 {#variables}

變數是 **[!UICONTROL instance]**。 **[!UICONTROL task]** 和 **[!UICONTROL event]** 對象。 為這些變數授權的JavaScript類型為 **[!UICONTROL string]**。 **[!UICONTROL number]** 和 **[!UICONTROL Date]**。

### 實例變數 {#instance-variables}

實例變數(**[!UICONTROL instance.vars.xxx]**)可與全局變數相比。 所有活動都共用。

### 任務變數 {#task-variables}

任務變數(**[!UICONTROL task.vars.xxx]**)可與局部變數比較。 它們僅用於當前任務。 這些變數由持久性活動使用以保留資料，有時用於在同一活動的不同指令碼之間交換資料。

### 事件變數 {#event-variables}

事件變數(**[!UICONTROL vars.xxx]**)允許在工作流進程的基本任務之間交換資料。 這些變數由激活正在執行的任務的任務傳遞。 可以修改它們並定義新的。 然後將它們傳遞到以下活動。

>[!CAUTION]
>
>在 [與連接](and-join.md) 類型活動，這些變數將合併，但如果同一變數定義了兩次，則會發生衝突，並且值仍未確定。

事件是最常使用的變數，它們應優先用於實例變數。

某些事件變數由各種活動修改或讀取。 這些都是字串型變數。 例如，導出設定 **[!UICONTROL vars.filename]** 具有剛導出的檔案的全名的變數。 所有這些讀取或修改的變數都記錄在 [關於活動](about-activities.md)，在 **輸入參數** 和 **輸出參數** 活動。

### 使用案例 {#example}

>[!NOTE]
>
>在中提供了其他工作流使用案例 [此部分](about-workflow-use-cases.md)。

**示例1**

在本示例中，實例變數用於動態計算要應用於總體的拆分百分比。

1. 建立工作流並添加「啟動」活動。

1. 添加並配置JavaScript代碼活動以定義實例變數。

   例如： `instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. 根據需要添加查詢活動和目標收件人。

1. 添加拆分活動並將其配置為對傳入人口執行隨機採樣。 抽樣百分比可以是您選擇的任何選擇。 在本例中，它設定為50%。

   它是動態更新的百分比，這要歸功於先前定義的實例變數。

   ![](assets/js_ex2.png)

1. 在「拆分」活動的「高級」頁籤的「初始化指令碼」部分中，定義JS條件。 JS條件選擇從「拆分」活動中產生的第一個轉換的隨機採樣百分比，並將其更新為先前建立的實例變數設定的值。

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. 確保補碼是在「拆分」活動的單獨轉換中生成的，並在每次出站轉換後添加「結束」活動。

1. 保存並執行工作流。 根據實例變數進行動態採樣。

   ![](assets/js_ex4.png)

**示例2**

1. 從上例中取出工作流，並替換 **JavaScript代碼** 的活動：

   ```
   instance.vars.foo = "bar1"
   vars.foo = "bar2"
   task.vars.foo = "bar3"
   ```

1. 將以下指令碼添加到的初始化指令碼 **結束** 活動：

   ```
   logInfo("instance.vars.foo = " + instance.vars.foo)
   logInfo("vars.foo = " + vars.foo)
   logInfo("task.vars.foo = " + task.vars.foo)
   ```

1. 啟動工作流，然後查看日誌。

   ```
   Workflow finished
   task.vars.foo = undefined
   vars.foo = bar2
   instance.vars.foo = bar1
   Starting workflow (operator 'admin')
   ```

此示例顯示以下活動 **JavaScript代碼** 訪問實例變數和事件變數，但任務變數無法從外部訪問(「undefined」)。

### 調用查詢中的執行個體變數 {#calling-an-instance-variable-in-a-query}

在活動中指定實例變數後，可以在工作流查詢中重新使用它。

因此，要調用變數 **instance.vars.xxx = &quot;yyy&quot;** 中，輸入 **$（實例/vars/xxx）**。

例如：

1. 建立實例變數，通過 **[!UICONTROL JavaScript code]**: **instance.vars.deliveryIN = &quot;DM42&quot;**。

   ![](assets/wkf_js_activity_1.png)

1. 建立其目標維和篩選維是收件人的查詢。 在條件中，指定要查找所有已發送由變數指定的傳遞的收件人。

   作為提醒，此資訊儲存在傳遞日誌中。

   引用中的實例變數 **[!UICONTROL Value]** 列，輸入 **$(實例/vars/@deliveryIN)**。

   工作流將返回DM42傳遞的收件人。

   ![](assets/wkf_var_in_query.png)

## 進階函式 {#advanced-functions}

除了標準JavaScript函式外，還可以使用特殊函式來操作檔案、讀取或修改資料庫中的資料或向日誌中添加消息。

### 日記 {#journal}

**[!UICONTROL logInfo(message)]** 在上述示例中詳述。 此函式向日記帳添加資訊消息。

**[!UICONTROL logError(message)]** 向日誌中添加錯誤消息。 指令碼中斷其執行，工作流將更改為錯誤狀態（預設情況下，將暫停實例）。

## 初始化指令碼 {#initialization-script}

在某些條件下，您可以在執行時修改活動的屬性。

活動的大多數屬性都可以動態計算，或者使用JavaScript模板，或者因為工作流屬性明確允許由指令碼計算值。

但是，對於其他屬性，必須使用初始化指令碼。 執行任務之前將評估此指令碼。 的 **[!UICONTROL activity]** 變數引用與任務對應的活動。 可以修改此活動的屬性，並且僅影響此任務。

**相關主題**
[工作流中JavaScript代碼的示例](javascript-in-workflows.md)
