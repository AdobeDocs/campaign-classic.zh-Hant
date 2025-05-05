---
product: campaign
title: 工作流程中的 JavaScript 程式碼範例
description: 這些範例說明如何在工作流程中使用JavaScript程式碼
feature: Workflows
hide: true
hidefromtoc: true
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 776c664a99721063dce5fa003cf40c81d94f8c78
workflow-type: tm+mt
source-wordcount: '1695'
ht-degree: 3%

---

# 工作流程中的 JavaScript 程式碼範例{#javascript-in-workflows}



這些範例說明如何在工作流程中使用JavaScript程式碼：

* [寫入資料庫](#write-example)
* [查詢資料庫](#read-example)
* [使用靜態SOAP方法觸發工作流程](#trigger-example)
* [使用非靜態SOAP方法與資料庫互動](#interact-example)

[進一步瞭解](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=zh-Hant)靜態和非靜態SOAP方法。

在這些範例中，會使用ECMAScript for XML (E4X)擴充功能。 透過此擴充功能，您可以在相同指令碼中合併JavaScript呼叫和XML原始專案。

若要嘗試這些範例，請依照下列步驟進行：

1. 建立工作流程並將這些活動新增至工作流程：
   1. 開始活動
   1. JavaScript程式碼活動
   1. 結束活動

   [進一步瞭解](building-a-workflow.md)建置工作流程。

1. 將JavaScript程式碼新增至活動。 [了解更多](advanced-parameters.md)。
1. 儲存工作流程。
1. 測試範例：
   1. 啟動工作流程。 [了解更多](starting-a-workflow.md)。
   1. 開啟日誌。 [了解更多](monitoring-workflow-execution.md#displaying-logs)。

## 範例1：寫入資料庫{#write-example}

若要寫入資料庫，您可以在`xtk:session`結構描述上使用靜態`Write`方法：

1. 以XML撰寫寫入要求。

1. 寫入記錄：

   1. 呼叫`xtk:session`結構描述上的`Write`方法。

      >[!IMPORTANT]
      > 如果您使用Adobe Campaign v8，建議您針對Snowflake表格中的`Write`方法，搭配&#x200B;**擷取**&#x200B;和&#x200B;**資料更新/刪除** API使用預備機制。 [深入了解](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=zh-Hant){target="_blank"}。

   1. 傳遞XML程式碼作為寫入要求的引數。

### 步驟1：撰寫寫入要求

您可以新增、更新和刪除記錄。

#### 插入記錄

由於`insert`作業是預設作業，因此您不需要指定它。

將此資訊指定為XML屬性：

* 要修改之資料表的綱要
* 要填入的表格欄位

例如：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>
```

#### 更新記錄

使用`_update`作業。 [了解更多](../../configuration/using/data-oriented-apis.md)。

將此資訊指定為XML屬性：

* 要修改之資料表的綱要
* 要更新的表格欄位
* 識別要更新的記錄所需的索引鍵引數

例如：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    status="Client"
    email="isabel.garcia@mycompany.com"
    operation="_update"
    _key="@email"/>
```

#### 刪除記錄

使用`DeleteCollection`方法。 [了解更多](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=zh-Hant)。

指定此資訊：

* 要修改之資料表的綱要
* 以XML元素的形式識別要更新的記錄所需的`where`子句

例如：

```javascript
xtk.session.DeleteCollection(
    "nms:recipient",
    <where>
        <condition expr="[@email] = 'isabel.garcia@mycompany.com'"/>
    </where>,
    false
    )
```

### 步驟2：寫入記錄

呼叫`xtk:session`結構描述上的非靜態`Write`方法：

```javascript
xtk.session.Write(myXML)
```

此方法不會傳回任何值。

將完整程式碼新增至工作流程中的JavaScript程式碼活動：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

此影片說明如何寫入資料庫：
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## 範例2：查詢資料庫{#read-example}

若要查詢資料庫，您可以使用非靜態`xtk:queryDef`執行個體方法：

1. 以XML撰寫查詢。
1. 建立查詢物件。
1. 執行查詢。

### 步驟1：撰寫查詢

指定`queryDef`實體的XML程式碼。

語法：

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

指定此資訊：

* 要讀取之資料表的綱要
* 作業
* 在`select`子句中要傳回的資料行
* `where`子句中的條件
* `orderBy`子句中的篩選准則

您可以使用下列操作：

| 作業 | 結果 |
| --- | --- |
| `select` | 零個或多個元素會傳回為集合。 |
| `getIfExists` | 傳回一個元素。 如果不存在相符元素，則會傳回空白元素。 |
| `get` | 傳回一個元素。 如果不存在相符元素，則會傳回錯誤。 |
| `count` | 以具有`count`屬性的元素形式傳回的相符記錄數目。 |

將`select`、`where`和`orderBy`子句寫入為XML專案：

* `select`子句

  指定要傳回的欄。 例如，若要選取人員的名字和姓氏，請撰寫此程式碼：

  ```xml
  <select>
      <node expr="@firstName"/>
      <node expr="@lastName"/>
  </select>
  ```

  使用`nms:recipient`結構描述時，元素會以下列形式傳回：

  ```xml
  <recipient firstName="Bo" lastName="Didley"/>
  ```

* `where`子句

  若要指定條件，請使用`where`子句。 例如，若要選取位於&#x200B;**Training**&#x200B;資料夾中的記錄，您可以撰寫此程式碼：

  ```xml
  <where>
      <condition expr="[folder/@label]='Training'"/>
  </where>
  ```

  合併多個運算式時，請在第一個運算式中使用布林運運算元。 例如，若要選取所有名為Isabel Garcia的人，您可以撰寫此程式碼：

  ```xml
  <condition boolOperator="AND" expr="@firstName='Isabel'"/>
  <condition expr="@lastName='Garcia'"/>
  ```

* `orderBy`子句

  若要排序結果集，請將`orderBy`子句指定為具有`sortDesc`屬性的XML專案。 例如，若要以遞增順序排序姓氏，您可以編寫此程式碼：

  ```xml
  <orderBy>
      <node expr="@lastName> sortDesc="false"/>
  </orderBy>
  ```

### 步驟2：建立查詢物件

若要從XML程式碼建立實體，請使用`create(`*`content`*`)`方法：

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

為`create(`*`content`*`)`方法加上要建立之實體的結構描述。

*`content`*&#x200B;引數為字串引數，是選用專案。 此引數包含描述實體的XML程式碼。

### 步驟3：執行查詢

請依照下列步驟操作：

1. 呼叫`queryDef`實體上的`ExecuteQuery`方法：

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. 處理結果：
   1. 使用回圈建構反複處理`select`作業的結果。
   1. 使用`getIfExists`作業測試結果。
   1. 使用`count`作業計算結果。

#### `select`作業的結果

所有相符專案都會傳回為集合：

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

若要反複檢查結果，請使用`for each`回圈：

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

回圈包含本機收件者變數。 對於收件者集合中傳回的每個收件者，都會列印出收件者的電子郵件。 [深入瞭解](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=zh-Hant)有關`logInfo`函式的資訊。

#### `getIfExists`作業的結果

每個相符專案都會傳回為元素：

```xml
<recipient id="52,378,079">
```

如果沒有相符專案，則會傳回空白元素：

```xml
<recipient/>
```

您可以參照主索引鍵節點，例如`@id`屬性：

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### `get`作業的結果

會傳回一個相符專案作為元素：

```xml
<recipient id="52,378,079">
```

如果沒有相符專案，則會傳回錯誤。

>[!TIP]
>
>如果您知道有相符專案，請使用`get`作業。 否則，請使用`getIfExists`作業。 如果您使用此最佳實務，則錯誤會顯示非預期的問題。 如果您使用`get`作業，請勿使用`try…catch`陳述式。 問題由工作流程的錯誤處理程式處理。

#### `count`作業的結果

傳回具有`count`屬性的專案：

```xml
<recipient count="200">
```

若要使用結果，請參考`@count`屬性：

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

針對`select`作業，將此程式碼新增至工作流程中的JavaScript程式碼活動：

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

由於`select`作業是預設作業，因此您不需要指定它。

此影片說明如何從資料庫讀取：
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## 觸發工作流程 {#trigger-example}

您可以程式設計方式觸發工作流程，例如，在技術工作流程中或處理使用者在網頁應用程式頁面上輸入的資訊。

工作流程觸發可透過使用事件來運作。 您可以對事件使用這些功能：

* 若要張貼事件，您可以使用靜態`PostEvent`方法。 [了解更多](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=zh-Hant)。
* 若要接收事件，您可以使用&#x200B;**[!UICONTROL External signal]**&#x200B;活動。 [了解更多](external-signal.md)。

您可以透過不同方式觸發工作流程：

* 您可以內嵌觸發工作流程，亦即從&#x200B;**[!UICONTROL JavaScript code]**&#x200B;活動的主要指令碼觸發。
* 另一個工作流程完成後，您可以觸發此工作流程：
   * 新增初始化指令碼至初始工作流程的&#x200B;**[!UICONTROL End]**&#x200B;活動。
   * 在目標工作流程的開頭新增&#x200B;**[!UICONTROL External signal]**&#x200B;活動。

     完成初始工作流程後，事件就會發佈。 會啟動傳出轉變並填入事件變數。 然後，目標工作流程會接收事件。

     >[!TIP]
     >
     >最佳實務是，當您新增指令碼至活動時，請以雙連字型大小將活動名稱括住，例如`-- end --`。 [進一步瞭解](workflow-best-practices.md)工作流程最佳實務。

`PostEvent`方法的語法：

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

在此範例中，工作流程完成後，會將簡短文字傳遞至&#x200B;**wkfExampleReceiver**&#x200B;工作流程的&#x200B;**訊號**&#x200B;活動：

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

因為最後一個引數設定為`false`，所以每次完成初始工作流程時，都會觸發&#x200B;**wkfExampleReceiver**&#x200B;工作流程。

觸發工作流程時，請牢記以下原則：

* `PostEvent`命令以非同步方式執行。 命令會放置在伺服器佇列中。 方法會在事件發佈後傳回。
* 必須啟動目標工作流程。 否則，錯誤會寫入記錄檔。
* 如果目標工作流程已暫停，則會將`PostEvent`命令排入佇列，直到工作流程恢復為止。
* 觸發的活動不需要進行中的任務。

本影片說明如何使用靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

本影片說明如何觸發工作流程：
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## 與資料庫互動 {#interact-example}

這些範例顯示如何執行下列動作：

* 在結構描述上使用`get`和`create`方法，以使用非靜態SOAP方法
* 建立執行SQL查詢的方法
* 使用`write`方法插入、更新和刪除記錄

請依照下列步驟操作：

1. 定義查詢：

   * 使用對應結構描述上的`create`方法擷取實體，例如`xtk:workflow`結構描述。 [了解更多](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=zh-Hant)。
   * 使用`queryDef`方法發出SQL查詢。

1. 使用`ExecuteQuery`方法執行查詢。 [了解更多](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=zh-Hant)。

   使用`for each`回圈來擷取結果。

### 具有`select`子句的`queryDef`方法語法

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

### `Create`方法

#### 範例1：選取記錄並寫入分錄

已選取位於&#x200B;**wfExamples**&#x200B;資料夾的工作流程的內部名稱。 結果會依內部名稱以遞增順序排序，並寫入日誌。

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

#### 範例2：刪除記錄

系統會選取名為Chris Smith之所有收件者的名字、姓氏、電子郵件及ID。 結果會依電子郵件遞增順序排序，並寫入日誌。 使用`delete`作業來刪除選取的記錄。

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

#### 範例3：選取記錄並寫入分錄

在此範例中，使用非靜態方法。 已選取其資訊儲存在&#x200B;**1234**&#x200B;資料夾且其電子郵件網域名稱以「adobe」開頭的所有收件者的電子郵件和出生年份。 結果會依出生日期遞減排序。 收件者的電子郵件會寫入日誌。

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

### `Write`方法

您可以插入、更新和刪除記錄。 您可以在Adobe Campaign中的任何結構描述上使用`Write`方法。 由於此方法為靜態方法，因此您不需要建立物件。 您可以使用下列操作：

* `update`作業
* `insertOrUpdate`作業，具有`_key`引數以識別要更新的記錄

  若您未指定&#x200B;**收件者**&#x200B;資料夾，則如果有相符專案，該記錄會更新到任何子資料夾中。 否則，會在根&#x200B;**收件者**&#x200B;資料夾中建立記錄。

* `delete`作業

>[!IMPORTANT]
> 如果您使用Adobe Campaign v8，建議您針對Snowflake表格中的`Write`方法，搭配&#x200B;**擷取**&#x200B;和&#x200B;**資料更新/刪除** API使用預備機制。 [深入了解](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html?lang=zh-Hant){target="_blank"}。

#### 範例1：插入或更新記錄

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

#### 範例2：刪除記錄

此範例結合了靜態方法和非靜態方法。

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

本影片說明如何使用非靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

本影片說明在工作流程中使用非靜態API方法的範例：
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## 相關主題

* [資料導向API](../../configuration/using/data-oriented-apis.md)
* [JavaScript 指令碼和範本](javascript-scripts-and-templates.md)
* [JavaScript 中的 SOAP 方法](../../configuration/using/soap-methods-in-javascript.md)

### API檔案

* [SOAP呼叫範例](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html?lang=zh-Hant)
* 方法：
   * [建立](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html?lang=zh-Hant)
   * [DeleteCollection](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html?lang=zh-Hant)
   * [ExecuteQuery](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html?lang=zh-Hant)
   * [PostEvent](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html?lang=zh-Hant)
   * [寫入](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html?lang=zh-Hant)
* [logInfo函式](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html?lang=zh-Hant)
