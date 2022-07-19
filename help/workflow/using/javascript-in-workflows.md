---
product: campaign
title: 工作流程中的 JavaScript 程式碼範例
description: 這些示例說明如何在工作流中使用JavaScript代碼
feature: Workflows
exl-id: 7213ea64-3dec-4b16-9d93-4ae941ddfaa7
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 3%

---

# 工作流程中的 JavaScript 程式碼範例{#javascript-in-workflows}

![](../../assets/v7-only.svg)

以下示例說明如何在工作流中使用JavaScript代碼：

* [寫入資料庫](#write-example)
* [查詢資料庫](#read-example)
* [使用靜態SOAP方法觸發工作流](#trigger-example)
* [使用非靜態SOAP方法與資料庫交互](#interact-example)

[瞭解更多資訊](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html) 關於靜態和非靜態SOAP方法。

在這些示例中，使用ECMAScript for XML(E4X)擴展。 使用此副檔名，可以將JavaScript調用和XML基元組合在同一指令碼中。

要試用這些示例，請執行以下步驟：

1. 建立工作流，並將這些活動添加到工作流：
   1. 啟動活動
   1. JavaScript代碼活動
   1. 結束活動

   [瞭解更多資訊](building-a-workflow.md) 關於構建工作流。

1. 將JavaScript代碼添加到活動。 [了解更多資訊](advanced-parameters.md)。
1. 儲存工作流程。
1. Test示例：
   1. 開始工作流程. [了解更多資訊](starting-a-workflow.md)。
   1. 開啟日記帳。 [了解更多資訊](monitoring-workflow-execution.md#displaying-logs)。

## 示例1:寫入資料庫{#write-example}

要寫入資料庫，可以使用 `Write` 方法 `xtk:session` 架構：

1. 在XML中合成寫請求。

1. 寫下記錄：

   1. 呼叫 `Write` 方法 `xtk:session` 架構。

      >[!IMPORTANT]
      > 如果您使用Adobe Campaignv8，建議您將轉移機制與 **攝取** 和 **資料更新/刪除** API `Write` 的子菜單。 [閱讀更多內容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}。

   1. 將XML代碼作為寫請求的參數傳遞。

### 步驟1:編寫寫請求

您可以添加、更新和刪除記錄。

#### 插入記錄

因為 `insert` 操作是預設操作，無需指定。

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

使用 `_update` 的下界。 [了解更多資訊](../../configuration/using/data-oriented-apis.md)。

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

使用 `DeleteCollection` 的雙曲餘切值。 [了解更多資訊](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)。

指定以下資訊：

* 要修改的表的架構
* 的 `where` 用於標識要更新的記錄的子句，形式為XML元素

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

### 步驟2:寫下記錄

調用非靜態 `Write` 方法 `xtk:session` 架構：

```javascript
xtk.session.Write(myXML)
```

此方法不返回值。

將完整代碼添加到工作流中的JavaScript代碼活動：

```javascript
var myXML = <recipient xtkschema="nms:recipient"
    firstName="Isabel"
    lastName="Garcia"
    email="isabel.garcia@mycompany.com"/>

xtk.session.Write(myXML)
```

此視頻顯示如何寫入資料庫：
>[!VIDEO](https://video.tv.adobe.com/v/18472/?learn=on)

## 示例2:查詢資料庫{#read-example}

要查詢資料庫，可以使用非靜態 `xtk:queryDef` 實例方法：

1. 在XML中合成查詢。
1. 建立查詢對象。
1. 運行查詢。

### 步驟1:合成查詢

指定的XML代碼 `queryDef` 的雙曲餘切值。

語法:

```xml
<queryDef schema="nms:recipient" operation="">
    <!-- select, where, and orderBy clauses as XML elements -->
</queryDef>
```

指定以下資訊：

* 要讀取的表的架構
* 操作
* 要返回的列，在 `select` 子句
* 條件，在 `where` 子句
* 篩選條件，在 `orderBy` 子句

您可以使用以下操作：

| 操作 | 結果 |
| --- | --- |
| `select` | 零個或多個元素作為集合返回。 |
| `getIfExists` | 返回一個元素。 如果不存在匹配元素，則返回空元素。 |
| `get` | 返回一個元素。 如果不存在匹配元素，則返回錯誤。 |
| `count` | 以元素形式返回的匹配記錄數 `count` 屬性。 |

寫入 `select`。 `where`, `orderBy` 子句作為XML元素：

* `select` 子句

   指定要返回的列。 例如，要選擇人員的名和姓，請編寫以下代碼：

   ```xml
   <select>
       <node expr="@firstName"/>
       <node expr="@lastName"/>
   </select>
   ```

   使用 `nms:recipient` 架構，以此形式返回元素：

   ```xml
   <recipient firstName="Bo" lastName="Didley"/>
   ```

* `where` 子句

   要指定條件，請使用 `where` 。 例如，要選擇位於 **培訓** 資料夾，可以編寫此代碼：

   ```xml
   <where>
       <condition expr="[folder/@label]='Training'"/>
   </where>
   ```

   組合多個表達式時，請在第一個表達式中使用布爾運算子。 例如，要選擇所有名為Isabel Garcia的人員，您可以編寫以下代碼：

   ```xml
   <condition boolOperator="AND" expr="@firstName='Isabel'"/>
   <condition expr="@lastName='Garcia'"/>
   ```

* `orderBy` 子句

   要對結果集進行排序，請指定 `orderBy` 子句作為XML元素， `sortDesc` 屬性。 例如，要按升序對姓氏進行排序，可以編寫以下代碼：

   ```xml
   <orderBy>
       <node expr="@lastName> sortDesc="false"/>
   </orderBy>
   ```

### 步驟2:建立查詢對象

要從XML代碼建立實體，請使用 `create(`*`content`*`)` 方法：

```javascript
var query = xtk.queryDef.create(
    <queryDef schema="nms:recipient" operation="select">
    …
    </queryDef>)
```

前置詞 `create(`*`content`*`)` 方法。

的 *`content`* 參數是字串參數，是可選的。 此參數包含描述實體的XML代碼。

### 第3步：運行查詢

執行以下步驟：

1. 呼叫 `ExecuteQuery` 方法 `queryDef` 實體：

   ```javascript
   var res = query.ExecuteQuery()
   ```

1. 處理結果：
   1. 迭代到 `select` 操作，使用循環構造。
   1. Test結果，使用 `getIfExists` 的下界。
   1. 使用 `count` 的下界。

#### a的結果 `select` 操作

所有匹配項都作為集合返回：

```xml
<recipient-collection>
    <recipient email="jane.smith@mycompany.com">
    <recipient email="john.harris@mycompany.com">
</recipient-collection>
```

要迭代結果，請使用 `for each` 循環：

```javascript
for each (var rcp in res:recipient)
    logInfo(rcp.@email)
```

該循環包括本地接收者變數。 對於在收件人集合中返回的每個收件人，將打印該收件人的電子郵件。 [瞭解更多資訊](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html) 關於 `logInfo` 的子菜單。

#### a的結果 `getIfExists` 操作

每個匹配都作為元素返回：

```xml
<recipient id="52,378,079">
```

如果沒有匹配項，則返回空元素：

```xml
<recipient/>
```

可以引用主鍵節點，例如 `@id` 屬性：

```javascript
if (res.@id !=undefined)
    { // match was found
    …
    }
```

#### 結果 `get` 操作

一個匹配項作為元素返回：

```xml
<recipient id="52,378,079">
```

如果沒有匹配項，則返回錯誤。

>[!TIP]
>
>如果你知道有匹配項，請使用 `get` 的下界。 否則，使用 `getIfExists` 的下界。 如果使用此最佳做法，則錯誤會顯示意外問題。 如果使用 `get` 操作，不使用 `try…catch` 的雙曲餘切值。 該問題由工作流的錯誤處理進程處理。

#### 結果 `count` 操作

具有 `count` 屬性：

```xml
<recipient count="200">
```

要使用結果，請參閱 `@count` 屬性：

```javascript
if (res.@count > 0)
    { // matches were found
    …
    }
```

對於 `select` 操作，將此代碼添加到工作流中的JavaScript代碼活動：

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

因為 `select` 操作是預設操作，無需指定。

此視頻顯示如何從資料庫讀取：
>[!VIDEO](https://video.tv.adobe.com/v/18475/?learn=on)

## 觸發工作流 {#trigger-example}

您可以以寫程式方式觸發工作流，例如，在技術工作流中或處理用戶在Web應用程式頁上輸入的資訊。

工作流觸發通過事件的使用進行。 您可以將以下功能用於事件：

* 要發佈事件，可以使用 `PostEvent` 的雙曲餘切值。 [了解更多資訊](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)。
* 要接收事件，可以使用 **[!UICONTROL External signal]** 的子菜單。 [了解更多資訊](external-signal.md)。

可以以不同方式觸發工作流：

* 您可以在內聯觸發工作流，即從 **[!UICONTROL JavaScript code]** 的子菜單。
* 在完成另一個工作流時，可以觸發工作流：
   * 將初始化指令碼添加到 **[!UICONTROL End]** 活動。
   * 添加 **[!UICONTROL External signal]** 活動。

      在完成初始工作流後，將發佈事件。 激活傳出轉換並填充事件變數。 然後，由目標工作流接收該事件。

      >[!TIP]
      >
      >最佳做法是，將指令碼添加到活動時，將活動名稱用雙連字元括起來，例如， `-- end --`。 [瞭解更多資訊](workflow-best-practices.md) 工作流最佳實踐。

的語法 `PostEvent` 方法：

```javascript
PostEvent(
    String     //ID of the target workflow
    String     //Name of the target activity
    String     //Name of the transition to be activated in case of multiple transitions
    XML        //Event parameters, in the <variables/> element
    Boolean    //To trigger the target workflow only once, set this parameter to true.
)
```

在本示例中，在完成工作流後，將向 **信號** 的 **wkfExampleReceiver** 工作流：

```javascript
var strLabel = "Adobe Campaign, Marketing that delivers"
xtk.workflow.PostEvent(
    "wkfExampleReceiver",
    "signal",
    "",
    <variables strLine={strLabel}/>,
    false)
```

因為最後一個參數設定為 `false`，也請參見Wiki頁。 **wkfExampleReceiver** 每次完成初始工作流時都會觸發工作流。

觸發工作流時，請牢記以下原則：

* 的 `PostEvent` 命令非同步運行。 該命令被放置在伺服器隊列上。 該方法在發佈事件後返回。
* 必須啟動目標工作流。 否則，錯誤將寫入日誌檔案。
* 如果目標工作流已掛起，則 `PostEvent` 命令將排入隊列，直到工作流恢復。
* 觸發的活動不要求正在執行任務。

此視頻顯示如何使用靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18481/?learn=on)

此視頻顯示如何觸發工作流：
>[!VIDEO](https://video.tv.adobe.com/v/18485/?learn=on)

## 與資料庫交互 {#interact-example}

以下示例說明如何執行這些操作：

* 使用 `get` 和 `create` 方案上使用非靜態SOAP方法的方法
* 建立執行SQL查詢的方法
* 使用 `write` 插入、更新和刪除記錄的方法

執行以下步驟：

1. 定義查詢：

   * 使用 `create` 對應架構上的方法 — 例如 `xtk:workflow` 架構。 [了解更多資訊](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)。
   * 使用 `queryDef` 方法來發出SQL查詢。

1. 使用 `ExecuteQuery` 的雙曲餘切值。 [了解更多資訊](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)。

   使用 `for each` 循環以檢索結果。

### 的語法 `queryDef` 方法 `select` 子句

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

#### 示例1:選擇記錄並寫入日記帳

位於 **wf示例** 資料夾。 結果按內部名稱按升序排序，並寫入日記帳。

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

#### 示例2:刪除記錄

將選擇名稱為Chris Smith的所有收件人的名字、姓名、電子郵件和ID。 結果按電子郵件按升序排序，並寫入日記帳。 A `delete` 操作用於刪除選定的記錄。

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

#### 示例3:選擇記錄並寫入日記帳

在本示例中，使用非靜態方法。 其資訊儲存在 **1234** 資料夾，其電子郵件域名以「adobe」開頭。 結果按出生日期按降序排序。 收件人的電子郵件將寫入日記帳。

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

您可以插入、更新和刪除記錄。 您可以使用 `Write` 方法在Adobe Campaign。 由於此方法是靜態的，因此您不需要建立對象。 您可以使用以下操作：

* 的 `update` 操作
* 的 `insertOrUpdate` 操作，與 `_key` 用於標識要更新的記錄的參數

   如果未指定 **收件人** 資料夾，如果存在匹配項，則在任何子資料夾中更新記錄。 否則，將在根中建立記錄 **收件人** 的子菜單。

* 的 `delete` 操作

>[!IMPORTANT]
> 如果您使用Adobe Campaignv8，建議您將轉移機制與 **攝取** 和 **資料更新/刪除** API `Write` 的子菜單。 [閱讀更多內容](https://experienceleague.adobe.com/docs/campaign/campaign-v8/architecture/api/new-apis.html){target=&quot;_blank&quot;}。

#### 示例1:插入或更新記錄

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

#### 示例2:刪除記錄

此示例將靜態方法與非靜態方法相結合。

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

此視頻顯示如何使用非靜態API方法：
>[!VIDEO](https://video.tv.adobe.com/v/18477/?learn=on)

此視頻顯示了在工作流中使用非靜態API方法的示例：
>[!VIDEO](https://video.tv.adobe.com/v/18476/?learn=on)

## 相關主題

* [面向資料的API](../../configuration/using/data-oriented-apis.md)
* [JavaScript 指令碼和範本](javascript-scripts-and-templates.md)
* [JavaScript 中的 SOAP 方法](../../configuration/using/soap-methods-in-javascript.md)

### API文檔

* [SOAP調用示例](https://experienceleague.adobe.com/developer/campaign-api/api/p-14.html)
* 方法:
   * [建立](https://experienceleague.adobe.com/developer/campaign-api/api/f-create.html)
   * [刪除集合](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-DeleteCollection.html)
   * [執行查詢](https://experienceleague.adobe.com/developer/campaign-api/api/sm-queryDef-ExecuteQuery.html)
   * [後事件](https://experienceleague.adobe.com/developer/campaign-api/api/sm-workflow-PostEvent.html)
   * [寫入](https://experienceleague.adobe.com/developer/campaign-api/api/sm-session-Write.html)
* [logInfo函式](https://experienceleague.adobe.com/developer/campaign-api/api/f-logInfo.html)
