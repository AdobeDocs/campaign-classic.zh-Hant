---
product: campaign
title: JavaScript 指令碼和範本
description: JavaScript 指令碼和範本
audience: workflow
content-type: reference
topic-tags: advanced-management
exl-id: 4a3647d1-cf8c-4867-871e-472287be7c6a
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '1234'
ht-degree: 2%

---

# JavaScript 指令碼和範本{#javascript-scripts-and-templates}

![](../../assets/common.svg)

指令碼使得可以計算值、在進程中的不同任務之間交換資料，以及使用SOAP調用執行特定操作。

指令碼在工作流圖中隨處可見：

* 所有活動都有初始化指令碼。 初始化指令碼會在活動啟動時執行，並且可用於初始化變數和修改屬性。
* 「JavaScript程式碼」活動僅用於執行指令碼。
* 「測試」活動會評估JavaScript運算式，以啟動適當的轉變。
* 大部分文字欄位是JavaScript範本：&lt;%=和%>之間可以包含JavaScript運算式。 這些欄位提供一個按鈕，可開啟下拉式清單以協助您輸入運算式。

   ![](assets/script-button.png)

## 公開的物件 {#objects-exposed}

在工作流程內容中執行的JavaScripts會存取一系列其他全域物件。

* **例項**:代表要執行的工作流程。此物件的架構為&#x200B;**xtk:workflow**。
* **任務**:表示要執行的任務。此對象的架構為&#x200B;**xtk:workflowTask**。
* **事件**:表示激活要執行的任務的事件。此物件的架構為&#x200B;**xtk:workflowEvent**。 尚未針對已從多個轉變啟動的&#x200B;**AND-join**&#x200B;類型活動初始化此對象。
* **事件**:表示激活當前任務的事件清單。此物件的架構為&#x200B;**xtk:workflowEvent**。 此表通常包含一個元素，但可能包含&#x200B;**AND-join**&#x200B;類型活動的數個，這些活動已根據多個轉變而激活。
* **活動**:表示正在執行的任務的模型。此物件的結構取決於活動類型。 此對象可由初始化指令碼修改，在其他指令碼中，修改具有不可確定的效果。

您可以按一下指令碼工具列右側的按鈕，在下拉式清單中查看這些對象的可用屬性。

>[!CAUTION]
>
>除了vars屬性的子屬性外，這些物件的屬性為唯讀。
>  
>這些屬性中的大多數僅在執行基本任務或實例被鈍化後才更新。 讀取的值不一定與目前狀態相符，而是與上一個狀態。

**範例**

在此範例和下列範例中，建立包含&#x200B;**JavaScript程式碼**&#x200B;活動和&#x200B;**End**&#x200B;活動的工作流程，如下圖所示。

![](assets/script-1.png)

連按兩下&#x200B;**JavaScript程式碼**&#x200B;活動並插入以下指令碼：

```
logInfo("Label: " + instance.label)
logInfo("Start date: " + task.creationDate)
```

**[!UICONTROL logInfo(message)]**&#x200B;函式將消息插入日誌中。

按一下&#x200B;**[!UICONTROL OK]**&#x200B;關閉建立精靈，然後使用位於工作流程清單右上角的動作按鈕啟動工作流程。 執行結束時，請查閱記錄檔。 您應該會看到與指令碼對應的兩則訊息：一個顯示工作流的標籤，另一個顯示指令碼的激活日期。

## 變數 {#variables}

變數是&#x200B;**[!UICONTROL instance]**、**[!UICONTROL task]**&#x200B;和&#x200B;**[!UICONTROL event]**&#x200B;對象的自由屬性。 為這些變數授權的JavaScript類型為&#x200B;**[!UICONTROL string]**、**[!UICONTROL number]**&#x200B;和&#x200B;**[!UICONTROL Date]**。

### 例項變數 {#instance-variables}

例項變數(**[!UICONTROL instance.vars.xxx]**)可與全域變數比較。 所有活動都會共用。

### 任務變數 {#task-variables}

任務變數(**[!UICONTROL task.vars.xxx]**)可與本地變數相比。 它們僅供當前任務使用。 這些變數供持續性活動用來保留資料，有時也用於在相同活動的不同指令碼之間交換資料。

### 事件變數 {#event-variables}

事件變數(**[!UICONTROL vars.xxx]**)允許在工作流進程的基本任務之間交換資料。 這些變數由激活正在進行的任務的任務傳遞。 可以修改它們並定義新的。 然後會將它們傳遞至下列活動。

>[!CAUTION]
>
>若為[AND-join](and-join.md)類型活動，則會合併變數，但如果同一個變數定義兩次，則會發生衝突，值仍未確定。

事件是最常使用的變數，其使用方式應優先於例項變數。

各種活動會修改或讀取某些事件變數。 這些都是字串類型變數。 例如，匯出會以剛匯出的檔案的完整名稱設定&#x200B;**[!UICONTROL vars.filename]**&#x200B;變數。 所有這些讀取或修改的變數都記錄在活動的[About activities](about-activities.md)各節的&#x200B;**Input parameters**&#x200B;和&#x200B;**Output parameters**&#x200B;中。

### 使用案例 {#example}

>[!NOTE]
>
>[此部分](about-workflow-use-cases.md)提供了其他工作流使用案例。

**範例1**

在此範例中，例項變數可用來動態計算要套用至母體的分割百分比。

1. 建立工作流程並新增「開始」活動。

1. 新增並設定JavaScript程式碼活動以定義例項變數。

   例如：`instance.vars.segmentpercent = 10;`

   ![](assets/js_ex1.png)

1. 新增「查詢」活動，並根據您的需求鎖定收件者。

1. 新增分割活動並將其設定為對傳入母體執行隨機取樣。 取樣百分比可以是您選擇的任何項目。 在此範例中已設為50%。

   這是此百分比會因為先前定義的例項變數而動態更新。

   ![](assets/js_ex2.png)

1. 在分割活動之進階標籤的初始化指令碼區段內，定義JS條件。 JS條件會選取來自分割活動之第一個轉變的隨機取樣百分比，並將其更新為先前建立的例項變數所設定的值。

   ```
   activity.transitions.extractOutput[0].limiter.percent = instance.vars.segmentpercent;
   ```

   ![](assets/js_ex3.png)

1. 請確定補充項目是在分割活動的個別轉變中產生，並在每個出站轉變後新增結束活動。

1. 儲存並執行工作流程。 動態取樣會根據例項變數套用。

   ![](assets/js_ex4.png)

**範例2**

1. 從上述範例取代工作流程，並以下列指令碼取代&#x200B;**JavaScript代碼**&#x200B;活動的指令碼：

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

此示例說明&#x200B;**JavaScript代碼**&#x200B;之後的活動訪問了實例變數和事件變數，但無法從外部（「未定義」）訪問任務變數。

### 調用查詢中的執行個體變數 {#calling-an-instance-variable-in-a-query}

在活動中指定例項變數後，您就可以在工作流程查詢中重複使用該變數。

因此，要調用篩選器中的變數&#x200B;**instance.vars.xxx = &quot;yyy&quot;**，請輸入&#x200B;**$(instance/vars/xxx)**。

例如：

1. 建立例項變數，透過&#x200B;**[!UICONTROL JavaScript code]**&#x200B;定義傳送的內部名稱：**instance.vars.deliveryIN = &quot;DM42&quot;**。

   ![](assets/wkf_js_activity_1.png)

1. 建立以收件者為目標和篩選維度的查詢。 在條件中，指定您要尋找所有已傳送由變數指定之傳送的收件者。

   提醒您，此資訊會儲存在傳送記錄檔中。

   若要參考&#x200B;**[!UICONTROL Value]**&#x200B;欄中的例項變數，請輸入&#x200B;**$(instance/vars/@deliveryIN)**。

   工作流程會傳回DM42傳送的收件者。

   ![](assets/wkf_var_in_query.png)

## 進階函式 {#advanced-functions}

除了標準JavaScript函式外，還可使用特殊函式來處理檔案、讀取或修改資料庫中的資料，或將消息添加到日誌中。

### 日誌 {#journal}

**[!UICONTROL logInfo(message)]** 在上述範例中詳細說明。此函式將資訊消息添加到日誌中。

**[!UICONTROL logError(message)]** 將錯誤訊息新增至記錄檔。指令碼會中斷其執行，而工作流程會變更為錯誤狀態（依預設，執行個體會暫停）。

## 初始化指令碼 {#initialization-script}

在特定條件下，您可以在執行時修改活動的屬性。

活動的大部分屬性都可以動態計算，使用JavaScript範本或因為工作流程屬性明確允許指令碼計算值。

但是，對於其他屬性，必須使用初始化指令碼。 在執行任務之前會評估此指令碼。 **[!UICONTROL activity]**&#x200B;變數會參考與任務對應的活動。 可以修改此活動的屬性，並且只影響此任務。
