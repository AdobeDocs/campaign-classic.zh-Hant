---
product: campaign
title: 一般設定
description: 一般設定
audience: migration
content-type: reference
topic-tags: configuration
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 8610d29a3df1080f1622a2cb3685c0961fb40092
workflow-type: tm+mt
source-wordcount: '2625'
ht-degree: 0%

---

# 一般設定{#general-configurations}

![](../../assets/v7-only.svg)

本節詳細說明從v5.11或v6.02移轉時，在Adobe Campaign v7中要執行的設定。

此外：

* 如果您從v5.11移轉，您也必須完成以下章節所述的設定： [本節](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* 如果您從v6.02移轉，您也必須完成以下章節所述的設定： [本節](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## 時區 {#time-zones}

### 多時區模式 {#multi-time-zone-mode}

在v6.02中，「多時區」模式僅適用於PostgreSQL資料庫引擎。 現在，無論使用何種類型的資料庫引擎，都可提供此功能。 強烈建議您將基礎轉換為「多時區」基礎。

若要使用TIMESTAMP WITH TIMEZONE模式，您還需要新增 **-userTimestamptz:1** 選項。

>[!IMPORTANT]
>
>若 **-usetimestamptz:1** 參數與不相容的資料庫引擎一起使用時，資料庫將已損壞，您必須還原資料庫的備份並重新執行上述命令。

>[!NOTE]
>
>移轉後可透過主控台(**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** 節點)。
>
>有關時區管理的詳細資訊，請參閱 [本節](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

如果你得到 **ORA 01805** 升級後期出錯，這表示應用程式伺服器和資料庫伺服器之間的Oracle時區檔案不同步。 要重新同步它們，請應用以下步驟：

1. 要標識所使用的時區檔案，請運行以下命令：

   ```
   select * from v$timezone_file
   ```

   時區檔案通常位於 **ORACLE_HOME/oracore/zoneinfo/** 檔案夾。

1. 請確定兩個伺服器上的時區檔案相同。

如需詳細資訊，請造訪： [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

客戶端和伺服器之間的時區不對齊也可能造成一些滯後。 這就是為什麼我們建議在用戶端和伺服器端使用相同版本的Oracle程式庫，這兩個時區必須相同。

檢查兩側是否位於同一時區：

1. 運行以下命令，檢查客戶端上的時區檔案的版本：

   ```
   genezi -v
   ```

   genezi是二進位的，位於 **$ORACLE_HOME/bin** 存放庫。

1. 運行以下命令，檢查伺服器端的時區檔案版本：

   ```
   select * from v$timezone_file
   ```

1. 若要變更用戶端的時區檔案，請使用 **ORA_TZFILE** 環境變數。

## 安全性 {#security}

### 安全區域 {#security-zones}

>[!IMPORTANT]
>
>基於安全考量，預設不再存取Adobe Campaign平台：您必須配置安全區域，因此收集運算子IP地址。

Adobe Campaign v7包含 **安全區**. 每個用戶必須與某個區域關聯才能登錄實例，並且用戶的IP地址必須包含在安全區域中定義的地址或地址範圍中。 可在Adobe Campaign伺服器設定檔案中設定安全區域。 必須在主控台中定義與使用者相關聯的安全區域(**[!UICONTROL Administration > Access management > Operators]**)。

**移轉前**，請要求網路管理員幫助您定義要在遷移後激活的安全區域。

**升級後** （在伺服器重新啟動之前），您必須配置安全區域。

在中找到安全區域配置 [本節](../../installation/using/security-zones.md).

### 用戶密碼 {#user-passwords}

在v7中， **內部** 和 **管理員** 操作員連接必須用密碼保護。 強烈建議為這些帳戶和所有運算子帳戶分配密碼， **移轉前**. 如果您尚未為 **內部**，您將無法連線。 要將密碼分配給 **內部**，輸入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>此 **內部** 所有追蹤伺服器的密碼必須相同。 如需詳細資訊，請參閱 [本節](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [本節](../../platform/using/access-management.md).

### v7中的新功能 {#new-features-in-v7}

* 沒有權限的使用者無法再連線至Adobe Campaign。 其權限必須手動新增，例如，透過建立 **connect**.

   在升級後期間會識別並列出受此修改影響的使用者。

* 如果密碼為空，則追蹤不再有效。 如果是這種情況，錯誤訊息會通知您並請您重新設定它。
* 使用者密碼不再儲存在 **xtk:sessionInfo** 綱要。
* 現在需要管理權限才能使用 **xtk:builder:評估JavaScript** 和 **xtk:builder:評估JavaScriptTemplate** 函式。

某些現成可用的結構已修改，現在預設僅可透過具有的運算子的寫入存取存取權存取 **管理員** 權限：

* ncm:publishing
* nl：監視
* nms:calendar
* xtk:builder
* xtk：連接
* xtk:dbInit
* xtk:entityBackupNew
* xtk:entityBackupOriginal
* xtk:entityOriginal
* xtk:form
* xtk:funcList
* xtk:fusion
* xtk:image
* xtk:javascript
* xtk:jssp
* xtk:jst
* xtk:navtree
* xtk:operatorGroup
* xtk:package
* xtk:queryDef
* xtk:resourceMenu
* xtk:rights
* xtk:schema
* xtk:scriptContext
* xtk:specFile
* xtk:sql
* xtk:sqlSchema
* xtk:srcSchema
* xtk:strings
* xtk:xslt

### Sessiontoken參數 {#sessiontoken-parameter}

在v5中， **sessiontoken** 參數可在用戶端上運作（概述類型畫面清單、連結編輯器等） 和伺服器端（網頁應用程式、報表、jsp、jssp等）。 在v7中，它只能在伺服器端運作。 如果您想要恢復v5的完整功能，必須使用此參數修改連結，並透過連線頁面傳遞：

連結範例：

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

使用「連線」頁面的新連結：

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>如果您使用連結了受信任IP掩碼的運算子，請檢查該運算子是否具有最低權限，並檢查它是否位於 **sessionTokenOnly** 模式。

### SQL函式 {#sql-functions}

未知的SQL函式調用不再自然地發送到伺服器。 目前，必須將所有SQL函式添加到 **xtk:funcList** 結構(如需詳細資訊，請參閱 [本節](../../configuration/using/adding-additional-sql-functions.md))。 遷移時，在升級後期間會添加一個選項，允許您與舊的未聲明SQL函式保持相容。 如果您想繼續使用這些函式，請檢查 **XtkPassUnknownSQLFunctionsToRDBMS** 期權確定於 **[!UICONTROL Administration > Platform > Options]** 節點層級。

>[!IMPORTANT]
>
>由於此選項會帶來安全風險，我們強烈建議不要使用此選項。

### JSSP {#jssp}

如果您想要透過HTTP通訊協定（而非HTTPS）授權存取特定頁面，例如，在您的Web應用程式中，無論在安全區中執行哪些設定，您必須指定 **httpAllowed=&quot;true&quot;** 參數。

如果您使用匿名JSSP，則必須新增 **httpAllowed=&quot;true&quot;** JSSP的中繼規則中的參數(**[!UICONTROL serverConf.xml]** 檔案):

例如：

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## 語法 {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7整合了更新的JavaScript解釋器。 不過，此更新可能導致某些指令碼運作不正常。 由於上一個引擎比較寬容，因此某些語法會起作用，而新版引擎則不再適用。

此 **[!UICONTROL myObject.@attribute]** 語法現在僅對XML對象有效。 此語法可用於個人化傳遞和內容管理。 如果您在非XML物件上使用此類語法，則個人化功能將無法繼續運作。

對於所有其他物件類型，語法現在為 **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. 例如，使用下列語法的非XML對象： **[!UICONTROL employee.@sn]**，現在必須使用下列語法： **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* 舊版語法：

   ```
   employee.@sn
   ```

* 新語法：

   ```
   employee["sn"]
   ```

要更改XML對象中的值，現在需要先更新值，然後才添加XML節點：

* 舊版JavaScript程式碼：

   ```
   var cellStyle = node.style.copy();
   this.styles.appendChild(cellStyle);
   cellStyle.@width = column.@width;
   ```

* 新的JavaScript程式碼：

   ```
   var cellStyle = node.style.copy();
   cellStyle.@width = column.@width;
   this.styles.appendChild(cellStyle);
   ```

您不能再將XML屬性用作表鍵。

* 舊版語法：

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* 新語法：

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

為了加強執行個體安全性，Adobe Campaign v7已引入新語法，以取代以SQLData為基礎的語法。 如果您透過此語法使用這些程式碼元素，則必須加以修改。 主要因素包括：

* 依子查詢篩選：新語法以 `<subQuery>`  定義子查詢的元素
* 匯總：新語法為「aggregate function(collection)」
* 按聯接篩選：新語法為 `[schemaName:alias:xPath]`

已修改queryDef(xtk:queryDef)架構：

* 新 `<subQuery>`  元素可用於替換SQLData中包含的SELECT
* 為@setOperator屬性引入兩個新值：「IN」和「NOT IN」
* 新 `<where>`  元素，是 `<node>` 元素：這可以讓您在SELECT中進行「子選擇」

使用&quot;@expr&quot;屬性時，可能會存在SQLData。 可以搜尋下列詞語：&quot;SQLData&quot;、&quot;aliasSqlTable&quot;、&quot;sql&quot;。

Adobe Campaign v7執行個體預設為安全。 安全性取決於 **[!UICONTROL serverConf.xml]** 檔案：the **allowSQLInjents** 屬性管理SQL語法安全性。

如果在升級後執行期間發生SQLData錯誤，則必須修改此屬性以暫時允許使用基於SQLData的語法，從而允許重寫代碼。 若要這麼做，您必須在 **serverConf.xml** 檔案：

```
allowSQLInjection="true"
```

因此，請使用下列命令重新啟動升級後：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

您必須配置安全區域(請參閱 [安全性](#security))，然後變更選項以重新啟用安全性：

```
allowSQLInjection="false"
```

以下提供舊語法與新語法的比較範例。

**按子查詢篩選**

* 舊版語法：

   ```
   <condition expr="@id NOT IN ([SQLDATA[SELECT iOperatorId FROM XtkOperatorGroup WHERE iGroupId = $(../@owner-id)]])" enabledIf="$(/ignored/@ownerType)=1"/>
   ```

* 新語法：

   ```
   <condition setOperator="NOT IN" expr="@id" enabledIf="$(/ignored/@ownerType)=1">
     <subQuery schema="xtk:operatorGroup">
        <select>
          <node expr="[@operator-id]" />
        </select>
        <where>
          <condition expr="[@group-id]=$long(../@owner-id)"/>
        </where>
      </subQuery>
   </condition>
   ```

* 舊版語法：

   ```
   <queryFilter name="dupEmail" label="Emails duplicated in the folder" schema="nms:recipient">
       <where>
         <condition sql="sEmail in (select sEmail from nmsRecipient where iFolderId=$(folderId) group by sEmail having count(sEmail)>1)" internalId="1"/>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

* 新語法：

   ```
   <queryFilter name="dupEmail" label=" Emails duplicated in the folder " schema="nms:recipient">
       <where>
         <condition expr="@email" setOperator="IN" internalId="1">
           <subQuery schema="nms:recipient">
             <select><node expr="@email"/></select>
             <where><condition expr="[@folder-id]=$(folderId)"/></where>
             <groupBy><node expr="@email"/></groupBy>
             <having><condition expr="count(@email)>1"/></having>
           </subQuery>
         </condition>
       </where>
       <folder _operation="none" name="nmsSegment"/>
     </queryFilter>
   ```

**匯總**

匯總函式（集合）

* 舊版語法：

   ```
   <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
   ```

* 新語法：

   ```
   <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
   ```

   >[!NOTE]
   >
   >對集料函式自動進行接頭。 不再需要指定條件WHERE O0.iOperationId=iOperationId。
   >
   >無法再使用「count(*)」函式。 您必須使用&quot;countall()&quot;。

* 舊版語法：

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* 新語法：

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**按聯接進行篩選**

`[schemaName:alias:xPath]`

別名為可選

* 舊版語法：

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* 新語法：

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**提示與秘訣**

在 `<subQuery>` 元素，以參考主要欄位的「欄位」欄位 `<queryDef>`   元素，請使用下列語法： `[../@field]`

範例:

```
<queryDef operation="select" schema="xtk:jobLog" startPath="/" xtkschema="xtk:queryDef">
  <select>
    <node expr="[job/@pid]" alias="@pid"/>
    <node expr="@id" ordered="true"/>
    <node expr="@logType"/>
  </select>
  <where>
    <condition expr="[@job-id]=99"/>
    <condition expr="@logType" setOperator="IN">
      <subQuery schema="xtk:jobLog">
        <select><node expr="@logType"/></select>
        <where><condition expr="[@job-id]=[../job/@id]"/></where>
        <groupBy><node expr="@logType"/></groupBy>
        <having><condition expr="count(@logType)>1"/></having>
      </subQuery>
    </condition>
  </where>
</queryDef>
```

## 衝突 {#conflicts}

移轉是透過升級後執行，而報表、表單或網頁應用程式中可能會出現衝突。 這些衝突可從主控台解決。

資源同步後， **postugrade** 命令可讓您檢測同步是否生成錯誤或警告。

### 查看同步結果 {#view-the-synchronization-result}

可以用兩種方式查看同步結果：

* 在命令行介面中，錯誤由三個>形形成 **>>** 並自動停止同步。 雙形箭頭就會發出警告 **>>** 同步完成後，和必須解析。 在升級後的結尾處，命令提示符中將顯示一個摘要。 例如：

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及資源衝突，則需要操作員注意才能解決。

* 此 **postupgrade_`<server version number>`升級後時間(_T)`>`.log** 檔案包含同步結果。 預設可在下列目錄中使用： **安裝目錄/var/`<instance>`postugrade**. 錯誤和警告由 **錯誤** 和 **警告** 屬性。

### 解決衝突 {#resolve-a-conflict}

只有高級運算子和那些已獲得「管理員」權限的運算子才能解決衝突。

要解決衝突，請應用以下進程：

1. 在Adobe Campaign樹結構中，將游標放在 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. 在清單中選擇要解決的衝突。

解決衝突有三種可能的方法：

* **[!UICONTROL Declared as resolved]**:需要事先操作員干預。
* **[!UICONTROL Accept the new version]**:如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]**:表示已拒絕更新。

   >[!IMPORTANT]
   如果選擇此解析模式，則可能會丟失新版本中的修補程式。 因此，強烈建議不要僅對專家運算子使用或保留此選項。

如果選擇手動解決衝突，請按以下步驟繼續：

1. 在視窗的下方，搜尋 **`_conflict_ string`** 查找具有衝突的實體。 隨新版本安裝的實體包含 **new** 引數中，與上一版本匹配的實體包含 **cus** 引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想保留的版本。 刪除 **`_conflict_argument_ string`** 你所保留的實體。

   ![](assets/s_ncs_production_conflict003.png)

1. 去找你本該解決的衝突。 按一下 **[!UICONTROL Actions]** 圖示並選取 **[!UICONTROL Declare as resolved]**.
1. 儲存您的變更：衝突現在已經解決。

## Tomcat {#tomcat}

Adobe Campaign v7中整合的Tomcat伺服器已變更版本。 因此，其安裝資料夾(tomcat-6)也發生了更改(tomcat 7)。 升級後，請務必檢查路徑是否確實連結至更新的資料夾(位於 **[!UICONTROL serverConf.xml]** 檔案):

```
$(XTK_INSTALL_DIR)/tomcat-8/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-8/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-8/lib/el-api.jar
```

## 互動 {#interaction}

### 先決條件 {#prerequisites}

**升級後之前**，您必須從6.02中刪除v7中不再存在的所有結構參考。

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### 選件內容 {#offer-content}

在v7中，選件內容已移動。 在v6.02中，內容位於每個表示結構中(**nms:emailOfferView**)。 在v7中，內容現在位於選件結構中。 升級後，內容因此不會顯示在介面中。 升級後，您必須重新建立選件內容，或開發指令碼，以自動將內容從表示結構移至選件結構。

>[!IMPORTANT]
如果在移轉後要傳送某些使用已設定選件的傳送，您必須刪除，並在v7中重新建立這些傳送。 如果您無法這麼做，則會提供「相容性模式」。 不建議使用此模式，因為您不會從Interaction v7中的所有新功能中受益。 這是一種過渡模式，可讓您在實際6.1移轉前完成持續進行的促銷活動。 有關此模式的詳細資訊，請與我們聯繫。

移動指令碼的示例(**interactionTo610_full_XX.js**) **移轉** 資料夾(在Adobe Campaign v7資料夾中)。 此檔案顯示用戶端指令碼的範例，每個選件使用單一電子郵件表示法( **[!UICONTROL htmlSource]** 和 **[!UICONTROL textSource]** 欄位)。 內容 **NmsEmailOfferView** 表格已移至選件表格。

>[!NOTE]
使用此指令碼不允許您從「內容管理」和「呈現函式」選項中受益。 若要從這些函式中獲益，您必須重新思考目錄選件，尤其是選件內容和設定空間。

```
loadLibrary("/nl/core/shared/nl.js");

NL.require("/nl/core/shared/xtk.js");

// 1. Restore old emailOfferView schema
logInfo("Restoring old emailOfferView schema");
var oldOfferViewSchemas = <entities schema="xtk:srcSchema"/>;

oldOfferViewSchemas.appendChild(
  <srcSchema img="nms:offerView.png"
             label="Email offer representations"
             labelSingular="Email offer representation"
             name="emailOfferView" namespace="nlmig"
             genAccessors="false" implements="xtk:persist">
    <element name="emailOfferView" template="nms:offerView" sqltable="NmsEmailOfferView">
      <element name="offer" revLabel="Email representation" revIntegrity="owncopy"/>
      <element   name="htmlSource"      type="html" label="HTML content"  xml="true"/>
      <element   name="textSource"      type="CDATA" label="Text content" xml="true"/>
      <element   name="htmlSource_jst"  type="CDATA" label="HTML script"  desc="HTML content calculation script."  xml="true" advanced="true"/>
      <element   name="textSource_jst"  type="CDATA" label="Text script" desc="Text content calculation script." xml="true" advanced="true"/>
    </element>
  </srcSchema>);

var oldOfferViewsPkg = <builder><package buildNumber="*">{oldOfferViewSchemas}</package></builder>;
xtk.builder.InstallPackage(oldOfferViewsPkg);

// 2. Migrate data from old emailOfferView table to nms:offer
logInfo("Moving data from old EmailOfferView table to NmsOffer");
var OFFER_STATUS_VALIDATED = 3;

var queryDef = xtk.queryDef.create(
  <queryDef operation="select" schema="nlmig:emailOfferView">
    <select>
      <node expr="[@offer-id]"/>
      <node expr="[@space-id]"/>
      <node expr="htmlSource_jst"/>
      <node expr="textSource_jst"/>
    </select>
  </queryDef>);
var res = queryDef.ExecuteQuery();

var processedOffers = {};
for each( var emailOfferView in res.emailOfferView )
{
  if( processedOffers[String(emailOfferView.@["offer-id"])] != undefined )
  {
    logWarning("Found 2 or more eff fffffmail representations for offer " + String(emailOfferView.@["offer-id"]) + ". Only keep the first one here.");
    continue;
  }
  xtk.session.Write(
    <offer id={emailOfferView.@["offer-id"]} status={OFFER_STATUS_VALIDATED} xtkschema="nms:offer">
      <view>
        {emailOfferView.mdSource_jst}
        {emailOfferView.textSource_jst}
      </view>
    </offer>
  );
  processedOffers[String(emailOfferView.@["offer-id"])] = 1;
}

// 3. Get rid of emailOfferView schema now that data has been moved.
logInfo("Deleting EmailOfferView schema");
xtk.session.Write(<srcSchema xtkschema="xtk:srcSchema" name="emailOfferView" namespace="nlmig" _operation="delete"/>);

logInfo("Done");
```

### 測試和設定 {#tests-and-configuration}

如果您只有一個環境，移動選件內容後，以下是應遵循的程式。 在此案例中，以「ENV」為例。

1. 在所有「ENV」環境中提供空格，請更新所用欄位清單。 例如，對於只使用 **[!UICONTROL htmlSource]**，您必須新增 **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. 在 **[!UICONTROL Type of Environment]** 欄位 **[!UICONTROL General]** 索引標籤，選取 **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. 建立設計環境（例如「ENV_DESIGN」）並將其連接到ENV線上環境。

   ![](assets/migration_interaction_4.png)

1. 部署所有「ENV」環境提供空間(按一下右鍵> **[!UICONTROL Actions > Deploy]**)，然後選取「ENV_DESIGN」環境。

   ![](assets/migration_interaction_5.png)

1. 對所有「ENV」環境選件都執行相同操作。
1. 在相關通道上激活所有環境都提供「ENV_DESIGN」。
1. 測試讓優惠方案上線。 如果您未遇到任何問題，請對最新的工作流任務執行掛起的任務 **[!UICONTROL Offer notification]** (offerMgt)，讓所有選件都上線。

   ![](assets/migration_interaction_6.png)

1. 執行全面的測試。

   >[!NOTE]
   線上的類別和選件名稱會在上線後修改。 在傳入的通道上，更新對選件和類別的所有參考。

## 報告 {#reports}

### 標準報表 {#standard-reports}

所有標準報表目前都使用轉譯引擎v6.x。如果您已將JavaScript新增至這些報表，則某些元素可能無法再運作。 事實上，舊版JavaScript與v6.x演算引擎不相容。 因此，您必須檢查JavaScript程式碼，之後再加以調整。 您應測試每個報表，尤其是匯出函式。

### 個人化報表 {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
如果您想要受益於新的報表功能，則必須重新發佈報表。 在此情況下，請檢查所有指令碼，並視需要加以變更。 關於PDF匯出，如果您已新增Open Office的特定指令碼，則此指令碼將不再適用於新的PDF匯出引擎(PhantomJS)。

## 網站應用程式 {#web-applications}

有兩個Web應用程式系列：

* 確定的Web應用程式（一起查看，批准表，外聯網內部發展）,
* 匿名的網路應用程式（網路或調查表表單）。

### 已識別的Web應用程式 {#identified-web-applications}

與報表([了解更多](#reports))，如果您已新增JavaScript，則必須視需要檢查並調整。 如果您想從v7藍色橫幅（包含藍色標籤）中獲益，則必須重新發佈Web應用程式。

v7中的Web應用程式連接方法已更改。 如果您在已識別的Web應用程式中遇到任何連線問題，您必須暫時啟用 **allowUserPassword** 和 **sessionTokenOnly** 選項 **serverConf.xml** 檔案。 升級後，修改下列選項值：

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

因此，請使用下列命令重新啟動升級後：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

在發佈之前，請先在v6.x轉譯引擎中測試您的Web應用程式。 然後停用這兩個選項。

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### 匿名Web應用程式 {#anonymous-web-applications}

如果您遇到任何問題，請重新發佈Web應用程式。
