---
product: campaign
title: 工作流程中的JavaScript程式碼範例
description: 這些範例說明如何在工作流程中使用JavaScript程式碼
audience: workflow
content-type: reference
topic-tags: advanced-management
source-git-commit: fa3a3e1801738928876734aa42342f0a5b49e320
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 2%

---

# 工作流程中的JavaScript程式碼範例{#javascript-in-workflows}

![](../../assets/common.svg)

以下範例說明如何在工作流程中使用JavaScript程式碼：

* [寫入資料庫](#write-example)
* [查詢資料庫](#read-example)
* [使用靜態SOAP方法觸發工作流](#trigger-example)
* [使用非靜態SOAP方法與資料庫交互](#interact-example)

[深入了解](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) 關於靜態和非靜態SOAP方法。

在這些範例中，會使用ECMAScript for XML(E4X)擴充功能。 透過此擴充功能，您可以將JavaScript呼叫和XML原語合併到相同的指令碼中。

若要試用這些範例，請遵循下列步驟：

1. 建立工作流程並將這些活動新增至工作流程：
   1. 啟動活動
   1. JavaScript程式碼活動
   1. 結束活動

   [深入了解](building-a-workflow.md) 關於建立工作流程。

1. 將JavaScript程式碼新增至活動。 [深入瞭解](advanced-parameters.md)。
1. 儲存工作流程。
1. 測試範例：
   1. 開始工作流程. [深入瞭解](starting-a-workflow.md)。
   1. 開啟日記帳。 [深入瞭解](monitoring-workflow-execution.md#displaying-logs)。

## 範例1:寫入資料庫{#write-example}

要寫入資料庫，可以使用靜態 `Write` 方法 `xtk:session` 方案：

1. 在XML中撰寫寫入請求。

1. 寫記錄：

   1. 呼叫 `Write` 方法 `xtk:session` 綱要。

      >[!IMPORTANT]
      > 如果您使用Adobe Campaign v8，建議您將預備機制與 **擷取** 和 **資料更新/刪除** 適用於 `Write` 方法。 [了解詳情](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}。

   1. 將XML代碼作為寫入請求的參數傳遞。

### 步驟1:撰寫請求

您可以新增、更新和刪除記錄。

#### 插入記錄

因為 `insert` 操作是預設操作，您不需要指定它。

將此資訊指定為XML屬性：

* 要修改的表的架構
* 要填充的表欄位

範例:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### 更新記錄

使用 `_update` 操作。 [深入瞭解](../../configuration/using/data-oriented-apis.md)。

將此資訊指定為XML屬性：

* 要修改的表的架構
* 要更新的表欄位
* 標識要更新的記錄所需的關鍵參數

範例:

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### 刪除記錄

使用 `DeleteCollection` 方法。 [深入瞭解](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)。

指定以下資訊：

* 要修改的表的架構
* 此 `where` 以XML元素形式標識要更新的記錄所需的子句

範例:

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### 步驟2:寫記錄

呼叫非靜態 `Write` 方法 `xtk:session` 方案：

```javascript
xtk.session.Write(myXML)
```

此方法不會傳回任何值。

將完整代碼新增至工作流程中的JavaScript代碼活動：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

此影片說明如何寫入資料庫：
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## 範例2:查詢資料庫{#read-example}

要查詢資料庫，可以使用非靜態 `xtk:queryDef` 例項方法：

1. 在XML中撰寫查詢。
1. 建立查詢物件。
1. 運行查詢。

### 步驟1:撰寫查詢

指定 `queryDef` 實體。

語法:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

指定以下資訊：

* 要讀取的表的架構
* 操作
* 要傳回的欄，以 `select` 子句
* 條件，在 `where` 子句
* 篩選條件，位於 `orderBy` 子句

您可以使用下列操作：

| 操作 | 結果 |
| --- | --- |
| `select` | 零個或多個元素會以集合的形式傳回。 |
| `getIfExists` | 會傳回一個元素。 如果不存在相符元素，則會傳回空白元素。 |
| `get` | 會傳回一個元素。 如果沒有相符元素存在，則會傳回錯誤。 |
| `count` | 以元素的形式傳回的相符記錄數，具有 `count` 屬性。 |

撰寫 `select`, `where`，和 `orderBy` 子句作為XML元素：

* `select` 子句

   指定要傳回的欄。 例如，若要選取人員的名字和姓氏，請撰寫以下程式碼：

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   使用 `nms:recipient` 架構中，會以此形式傳回元素：

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` 子句

   若要指定條件，請使用 `where` 條。 例如，若要選取位於 **培訓** 資料夾中，您可以編寫此代碼：

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   結合多個運算式時，請在第一個運算式中使用布林運算子。 例如，要選擇所有名為Isabel Garcia的人，可以編寫以下代碼：

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` 子句

   要對結果集進行排序，請指定 `orderBy` 子句作為XML元素，並帶有 `sortDesc` 屬性。 例如，若要以升序來排序姓氏，您可以撰寫此程式碼：

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### 步驟2:建立查詢物件

要從XML代碼建立實體，請使用 `create(`*`content`*`)` 方法：

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

前置詞為 `create(`*`content`*`)` 方法與要建立之實體的架構。

此 *`content`* 引數是字串引數，且為選用。 此引數包含描述實體的XML代碼。

### 步驟3:運行查詢

請依照下列步驟操作：

1. 呼叫 `ExecuteQuery` 方法 `queryDef` 實體：

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. 處理結果：
   1. 反覆查看 `select` 操作，使用循環結構。
   1. 使用 `getIfExists` 操作。
   1. 使用 `count` 操作。

#### a的結果 `select` 操作

所有相符項目都會以集合傳回：

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

若要反覆查看結果，請使用 `for each` 循環：

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

回圈包含本機收件者變數。 對於收件者集合中傳回的每個收件者，會列出收件者的電子郵件。 [深入了解](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) 關於 `logInfo` 函式。

#### a的結果 `getIfExists` 操作

每個符合都會以元素傳回：

```xml
<recipient id="52,378,079">
```

如果沒有相符項目，則會傳回空白元素：

```xml
<recipient/>
```

您可以參考主要索引鍵節點，例如 `@id` 屬性：

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### 結果 `get` 操作

會傳回一個相符項目作為元素：

```xml
<recipient id="52,378,079">
```

如果沒有相符項目，則會傳回錯誤。

>[!TIP]
>
>如果您知道有相符項目，請使用 `get` 操作。 否則，請使用 `getIfExists` 操作。 如果您使用此最佳實務，則錯誤會顯示非預期的問題。 如果您使用 `get` 操作，不使用 `try…catch` 語句。 問題由工作流的錯誤處理過程處理。

#### 結果 `count` 操作

具有 `count` 屬性傳回：

```xml
<recipient count="200">
```

若要使用結果，請參閱 `@count` 屬性：

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

若 `select` 操作，將此代碼新增至工作流程中的JavaScript代碼活動：

```javascript
var myXML =
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@firstName"/>
        <node expr="@lastName"/>
    </select>
</queryDef>

var query = xtk.queryDef.create(myXML)

var res = query.ExecuteQuery()

for each (var rcp in res.recipient)
    logInfo(rcp.@firstName + " " + rcp.@lastName)
```

因為 `select` 操作是預設操作，您不需要指定它。

此影片說明如何從資料庫讀取：
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## 觸發工作流程 {#trigger-example}

您可以以程式設計方式觸發工作流程，例如在技術工作流程中觸發工作流程，或處理使用者已在網頁應用程式頁面上輸入的資訊。

工作流程觸發可透過事件的使用運作。 您可以對事件使用下列功能：

* 若要張貼事件，您可以使用靜態 `PostEvent` 方法。 [深入瞭解](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)。
* 若要接收事件，您可以使用 **[!UICONTROL External signal]** 活動。 [深入瞭解](external-signal.md)。

您可以透過不同方式觸發工作流程：

* 您可以內嵌觸發工作流程，亦即從 **[!UICONTROL JavaScript code]** 活動。
* 您可以在完成其他工作流程時觸發工作流程：
   * 將初始化指令碼添加到 **[!UICONTROL End]** 活動。
   * 新增 **[!UICONTROL External signal]** 活動。

      完成初始工作流程後，會張貼一個事件。 即會啟動傳出轉變，並填入事件變數。 然後，目標工作流程接收事件。

      >[!TIP]
      >
      >最佳實務是，將指令碼新增至活動時，請將活動名稱括住雙連字型大小，例如 `-- end --`. [深入了解](workflow-best-practices.md) 關於工作流程最佳實務。

語法 `PostEvent` 方法：

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

在此範例中，完成工作流程後，會將簡短文字傳遞至 **信號** 活動 **wkfExampleReceiver** 工作流程：

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

因為最後一個參數設為 `false`, **wkfExampleReceiver** 每次完成初始工作流程時，就會觸發工作流程。

觸發工作流程時，請牢記以下原則：

* 此 `PostEvent` 命令以非同步方式運行。 命令被放置在伺服器隊列中。 方法會在事件張貼後傳回。
* 必須啟動目標工作流。 否則，將錯誤寫入日誌檔案。
* 如果目標工作流程已暫停，則 `PostEvent` 命令會排入佇列，直到工作流程繼續為止。
* 觸發的活動不需要進行任務。

此影片說明如何使用靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

此影片說明如何觸發工作流程：
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## 與資料庫互動 {#interact-example}

以下範例說明如何執行下列動作：

* 使用 `get` 和 `create` 結構使用非靜態SOAP方法的方法
* 建立執行SQL查詢的方法
* 使用 `write` 插入、更新和刪除記錄的方法

請依照下列步驟操作：

1. 定義查詢：

   * 使用 `create` 對應架構的方法，例如 `xtk:workflow` 綱要。 [深入瞭解](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)。
   * 使用 `queryDef` 方法來發出SQL查詢。

1. 使用 `ExecuteQuery` 方法。 [深入瞭解](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)。

   使用 `for each` 循環以檢索結果。

### 語法 `queryDef` 方法 `select` 子句

```xml
<queryDef schema="schema_key" operation="operation_type">
    <select>
        <node expr="expression1">
        <node sql="expression2">
    </select>
    <where> 
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </where>
    <orderBy>
        <node expr="expression1">
        <node sql="expression2">
    </orderBy>
    <groupBy>
        <node expr="expression1">
        <node sql="expression2">
    </groupBy>
    <having>
        <condition expr="expression1"/> 
        <condition sql="expression2"/>
    </having>
</queryDef>
```

### `Create` 方法

#### 範例1:選擇記錄並寫入日記帳

位於 **wfExamples** 檔案夾。 結果按內部名稱、升序排序，並寫入日記帳。

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="xtk:workflow" operation="select">
        <select>
            <node expr="@internalName"/>
        </select>
        <where>
            <condition expr="[folder/@name]='wfExamples'"/>
        </where>
        <orderBy>
            <node expr="@internalName" sortDesc="false"/>
        </orderBy>
    </queryDef>
    )

var res = query.ExecuteQuery()
for each (var w in res.workflow)
    logInfo(w.@internalName)
```

#### 範例2:刪除記錄

系統會選取名字、姓氏、電子郵件和所有收件者（名為Chris Smith）的ID。 結果按電子郵件、升序排序，並寫入日誌。 A `delete` 操作用於刪除所選記錄。

```javascript
// Build the query, create a query object and hold the object in a variable
var query = xtk.queryDef.create(
        <queryDef schema="nms:recipient" operation="select">
            <select>
                <node expr="@firstName"/>
                <node expr="@lastName"/>
                <node expr="@email"/>
                <node expr="@id"/>
            </select>
            <where>
                <condition expr="[folder/@label]='Recipients'"/>
                <condition expr="[@lastName]='Smith'"/>
                <condition expr="[@firstName]='Chris'"/>
            </where>
            <orderBy>
                <node expr="@email" sortDesc="false"/>
            </orderBy>
        </queryDef>
)

//Run the query using the ExecuteQuery method against the created object
var res = query.ExecuteQuery()

//Loop through the results, print out the person's name and email, then delete the records
for each (var rec in res.recipient)
    {
     logInfo("Delete record = Email: " + rec.@email + ', ' + rec.@firstName + ' ' + rec.@lastName)
     xtk.session.Write(<recipient xtkschema="nms:recipient" _operation="delete" id={rec.@id}/>)
    }
```

#### 範例3:選擇記錄並寫入日記帳

在此範例中，使用非靜態方法。 其資訊儲存在 **1234** 已選取其電子郵件網域名稱以「adobe」開頭的資料夾和。 結果按出生日期以降序排序。 收件者的電子郵件會寫入日誌。

```javascript
var query = xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@email"/>
        <node sql="sEmail"/>
        <node expr="Year(@birthDate)"/>
    </select>
    <where>
        <condition expr="[@folder-id] = 1234 and @domain like 'adobe%'"/>
        <condition sql="iFolderId = 1234 and sDomain like 'adobe%'"/>
    </where>
    <orderBy>
        <node expr="@birthDate" sortDesc="true"/>
    </orderBy>
</queryDef>
)

var res = query.ExecuteQuery()
for each (var w in res.recipient)
    logInfo(w.@email)
```

### `Write` 方法

您可以插入、更新和刪除記錄。 您可以使用 `Write` 方法。 因為此方法為靜態，您不需要建立物件。 您可以使用下列操作：

* 此 `update` 操作
* 此 `insertOrUpdate` 操作，使用 `_key` 用於標識要更新的記錄的參數

   如果您未指定 **收件者** ，則如果存在匹配項，則會在任何子資料夾中更新記錄。 否則，記錄會建立在根 **收件者** 檔案夾。

* 此 `delete` 操作

>[!IMPORTANT]
> 如果您使用Adobe Campaign v8，建議您將預備機制與 **擷取** 和 **資料更新/刪除** 適用於 `Write` 方法。 [了解詳情](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}。

#### 範例1:插入或更新記錄

```javascript
xtk.session.Write(
<recipient
    xtkschema="nms:recipient"
    _operation="insertOrUpdate" _key="@email"
    lastName="Lennon"
    firstName="John"
    email="johnlennon@thebeatles.com"
/>
)
```

#### 範例2:刪除記錄

此範例結合靜態方法與非靜態方法。

```javascript
var query=xtk.queryDef.create(
<queryDef schema="nms:recipient" operation="select">
    <select>
        <node expr="@Id"/>
    </select>
    <where>
        <condition expr="[@email]='johnlennon@thebeatles.com'"/>
    </where>
</queryDef>
);

var res = query.ExecuteQuery()
for each (var w in res.recipient) {
xtk.session.Write(
    <recipient xtkschema="nms:recipient" _operation="delete" id={w.@id}/>
);
}
```

此影片說明如何使用非靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

此影片示範如何在工作流程中使用非靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## 相關主題

* [資料導向API](../../configuration/using/data-oriented-apis.md)
* [JavaScript 指令碼和範本](javascript-scripts-and-templates.md)
* [JavaScript 中的 SOAP 方法](../../configuration/using/soap-methods-in-javascript.md)

### API檔案

* [SOAP呼叫範例](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* 方法:
   * [建立](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [寫入](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo函式](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)