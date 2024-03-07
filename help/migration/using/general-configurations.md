---
product: campaign
title: 一般設定
description: 一般設定
feature: Upgrade
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
audience: migration
content-type: reference
topic-tags: configuration
hide: true
hidefromtoc: true
exl-id: 7aad0e49-8d9c-40c7-9d6a-42fee0ae5870
source-git-commit: 209ccbcac20052826dad0c55b35173be20b10114
workflow-type: tm+mt
source-wordcount: '2607'
ht-degree: 1%

---

# 一般設定{#general-configurations}



本節詳細說明從v5.11或v6.02遷移時，在Adobe Campaign v7中執行的設定。

此外：

* 如果您從v5.11移轉，您也必須完成中詳述的設定 [本節](../../migration/using/configuring-your-platform.md#specific-configurations-in-v5-11).
* 如果您從v6.02移轉，您也必須完成中詳述的設定 [本節](../../migration/using/configuring-your-platform.md#specific-configurations-in-v6-02).

## 時區 {#time-zones}

### 多時區模式 {#multi-time-zone-mode}

在v6.02中，「多時區」模式僅適用於PostgreSQL資料庫引擎。 現在不論使用何種資料庫引擎，都提供此功能。 我們強烈建議您轉換基準為「多時區」基準。

若要以時區模式使用TIMESTAMP，您還需要新增 **-userTimestamptz：1** 選項至升級後命令列。

>[!IMPORTANT]
>
>如果 **-usetimestamptz：1** 引數用於不相容的資料庫引擎，您的資料庫將損毀，您必須還原資料庫的備份，然後重新執行上述命令。

>[!NOTE]
>
>您可在移轉後透過主控台變更時區(**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** 節點)。
>
>如需時區管理的詳細資訊，請參閱 [本節](../../installation/using/time-zone-management.md).

### Oracle {#oracle}

如果您收到 **ORA 01805** 升級後發生錯誤，這表示應用程式伺服器和資料庫伺服器之間的Oracle時區檔案不同步。 若要重新同步這些檔案，請套用下列步驟：

1. 若要識別使用的時區檔案，請執行以下命令：

   ```
   select * from v$timezone_file
   ```

   時區檔案通常可在 **oracle_HOME/oracore/zoneinfo/** 資料夾。

1. 確定兩個伺服器上的時區檔案相同。

如需詳細資訊，請造訪： [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

使用者端與伺服器之間的時區不符也可能會造成一些延遲。 這就是為什麼我們建議在使用者端和伺服器端使用相同版本的Oracle庫，兩個時區必須相同。

若要檢查兩側是否位於相同的時區：

1. 執行下列命令，檢查使用者端的時區檔案版本：

   ```
   genezi -v
   ```

   genezi是二進位檔案，位於 **$ORACLE_HOME/bin** 存放庫。

1. 執行下列命令，檢查伺服器端的時區檔案版本：

   ```
   select * from v$timezone_file
   ```

1. 若要變更使用者端的時區檔案，請使用 **ORA_TZFILE** 環境變數。

## 安全性 {#security}

### 安全性區域 {#security-zones}

>[!IMPORTANT]
>
>基於安全性理由，Adobe Campaign平台在預設情況下無法再存取：您必須設定安全性區域，因此請收集操作員IP位址。

Adobe Campaign v7涉及以下概念 **安全性區域**. 每個使用者都必須與區域相關聯，才能登入執行個體，而且使用者的IP位址必須包含在安全性區域中定義的位址或位址範圍內。 您可以在Adobe Campaign伺服器設定檔案中設定安全性區域。 必須在主控台中定義使用者相關聯的安全區域(**[!UICONTROL Administration > Access management > Operators]**)。

**移轉前**，請要求您的網路管理員協助您定義要在移轉後啟用的安全性區域。

**升級後** （在伺服器重新啟動之前），您必須設定安全性區域。

安全性區域設定可在以下位置找到： [本節](../../installation/using/security-zones.md).

### 使用者密碼 {#user-passwords}

在v7中， **內部** 和 **管理員** 操作員連線必須使用密碼保護。 我們強烈建議為這些帳戶及所有操作員帳戶指定密碼， **移轉前**. 如果您尚未指定密碼 **內部**，您將無法連線。 若要指派密碼給 **內部**，輸入下列命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>此 **內部** 所有追蹤伺服器的密碼必須相同。 如需詳細資訊，請參閱 [本節](../../installation/using/configuring-campaign-server.md#internal-identifier) 和 [本節](../../platform/using/access-management.md).

### v7中的新功能 {#new-features-in-v7}

* 沒有許可權的使用者無法再連線至Adobe Campaign。 例如，您必須建立名為的許可權，以手動方式新增其許可權。 **connect**.

  在升級後期間，會識別並列出受此修改影響的使用者。

* 如果密碼為空，追蹤就不再有效。 如果是這種情況，錯誤訊息會通知您並要求您重新配置。
* 使用者密碼不再儲存在 **xtk：sessionInfo** 綱要。
* 現在必須使用管理許可權 **`xtk:builder:EvaluateJavaScript`** 和 **`xtk:builder:EvaluateJavaScriptTemplate`** 函式。

某些現成可用的結構描述已經過修改，現在預設只有具備寫入許可權的運運算元才能存取， **管理員** 許可權：

* ncm：publishing
* nl：monitoring
* nms：calendar
* xtk：builder
* xtk：連線
* xtk：dbInit
* xtk：entityBackupNew
* xtk：entityBackupOriginal
* xtk：entityOriginal
* xtk：form
* xtk：funcList
* xtk：fusion
* xtk：image
* xtk：javascript
* xtk：jssp
* xtk：jst
* xtk：navtree
* xtk：operatorGroup
* xtk：package
* xtk：queryDef
* xtk：resourceMenu
* xtk：rights
* xtk：schema
* xtk：scriptContext
* xtk：specFile
* xtk：sql
* xtk：sqlSchema
* xtk：srcSchema
* xtk：strings
* xtk：xslt

### Sessiontoken引數 {#sessiontoken-parameter}

在v5中， **sessiontoken** 引數適用於兩個使用者端（概觀型別熒幕、連結編輯器等清單） 和伺服器端（網頁應用程式、報表、jsp、jssp等）。 在v7中，它僅適用於伺服器端。 如果要恢復到v5上的完整功能，您必須使用此引數修改連結，並透過連線頁面傳遞：

連結範例：

```
/view/recipientOverview?__sessiontoken=<trusted login>
```

使用連線頁面的新連結：

```
/nl/jsp/logon.jsp?login=<trusted login>&action=submit&target=/view/recipientOverview
```

>[!IMPORTANT]
>
>如果您使用連結至信任IP遮罩的運運算元，請檢查該運運算元是否具有最低許可權，以及它是否位於中的安全區域 **sessionTokenOnly** 模式。

### SQL函式 {#sql-functions}

不明的SQL函式呼叫不再自然傳送到伺服器。 目前，所有SQL函式都必須新增至 **xtk：funcList** 結構描述(如需詳細資訊，請參閱 [本節](../../configuration/using/adding-additional-sql-functions.md))。 移轉時，會在升級後期間新增一個選項，可讓您維持與舊未宣告SQL函式的相容性。 如果要繼續使用這些功能，請檢查 **xtkpassunknowledsqlfunctionsToRDBMS** 選項的確定義於 **[!UICONTROL Administration > Platform > Options]** 節點層級。

>[!IMPORTANT]
>
>由於此選項會帶來安全性風險，因此強烈建議不要使用此選項。

### JSSP {#jssp}

如果您想要透過HTTP通訊協定（而非HTTPS）授權存取某些頁面，例如在您的Web應用程式中，無論在安全性區域中執行的設定為何，您都必須指定 **httpAllowed=&quot;true&quot;** 對應轉送規則中的引數。

如果您使用匿名JSSP，則必須新增 **httpAllowed=&quot;true&quot;** JSSP的轉送規則引數(**[!UICONTROL serverConf.xml]** 檔案)：

例如：

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blacklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## 語法 {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7整合了更新的JavaScript解譯器。 不過，此更新可能會導致某些指令碼無法正常運作。 由於之前的引擎比較寬鬆，某些語法將不再適用於新版本的引擎。

此 **[!UICONTROL myObject.@attribute]** 語法現在只對XML物件有效。 此語法可用於個人化傳送和內容管理。 如果您在非XML物件上使用此型別的語法，個人化功能將無法再運作。

對於所有其他物件型別，語法現在為 **[!UICONTROL myObject`[`&quot;attribute&quot;`]`]**. 例如，使用下列語法的非XML物件： **[!UICONTROL employee.@sn]**，現在必須使用下列語法： **[!UICONTROL employee`[`&quot;sn&quot;`]`]**.

* 先前的語法：

  ```
  employee.@sn
  ```

* 新語法：

  ```
  employee["sn"]
  ```

若要變更XML物件中的值，您現在需要在新增XML節點之前先更新值：

* 舊的JavaScript程式碼：

  ```
  var cellStyle = node.style.copy();
  this.styles.appendChild(cellStyle);
  cellStyle.@width = column.@width;
  ```

* 新JavaScript程式碼：

  ```
  var cellStyle = node.style.copy();
  cellStyle.@width = column.@width;
  this.styles.appendChild(cellStyle);
  ```

您無法再使用XML屬性做為資料表索引鍵。

* 先前的語法：

  ```
  if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
  ```

* 新語法：

  ```
  if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
  ```

### SQLData {#sqldata}

為了增強執行個體安全性，Adobe Campaign v7中引入了新語法，以取代基於SQLData的語法。 如果您將這些程式碼元素與此語法搭配使用，則必須加以修改。 相關的主要元素包括：

* 依子查詢篩選：新語法以 `<subQuery>`  要定義子查詢的元素
* 彙總：新語法為「彙總函式（集合）」
* 依加入篩選：新語法為 `[schemaName:alias:xPath]`

queryDef (xtk：queryDef)結構描述已修改：

* 新 `<subQuery>`  元素可用來取代SQLData中包含的SELECT
* @setOperator屬性引進了兩個新值「IN」和「NOT IN」
* 新 `<where>`  元素，其子系 `<node>` 元素：這可讓您在SELECT中進行「子選取」

使用「@expr」屬性時，可能會出現SQLData。 可以搜尋下列詞語：「SQLData」、「aliasSqlTable」、「sql」。

Adobe Campaign v7例項預設為安全狀態。 安全性係指中安全性區域的定義 **[!UICONTROL serverConf.xml]** 檔案： **allowSQLInjection** 屬性管理SQL語法安全性。

如果升級後執行期間發生SQLData錯誤，您必須修改此屬性以暫時允許使用以SQLData為基礎的語法，讓您重新寫入程式碼。 若要這麼做，必須在 **serverConf.xml** 檔案：

```
allowSQLInjection="true"
```

因此，請使用以下命令重新啟動升級後：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

您必須設定安全性區域(請參閱 [安全性](#security))，然後變更選項以重新啟用安全性：

```
allowSQLInjection="false"
```

下方提供新舊語法的比較範例。

**依子查詢篩選**

* 先前的語法：

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

* 先前的語法：

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

**彙總**

彙總函式（集合）

* 先前的語法：

  ```
  <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
  ```

* 新語法：

  ```
  <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
  ```

  >[!NOTE]
  >
  >系統會自動執行集合函式的接點。 不再需要指定條件WHERE O0.iOperationId=iOperationId。
  >
  >不能再使用「count(&#42;)」函式。 您必須使用「countall()」。

* 先前的語法：

  ```
  <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
  ```

* 新語法：

  ```
  <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                    <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
  ```

**依聯結篩選**

`[schemaName:alias:xPath]`

別名是選用的

* 先前的語法：

  ```
  <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                           aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
  ```

* 新語法：

  ```
  <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
  ```

**提示與秘訣**

在 `<subQuery>` 元素，以參照主要欄位的「欄位」 `<queryDef>`   元素，請使用下列語法： `[../@field]`

例如：

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

移轉會透過升級後執行，且衝突可能會出現在報表、表單或網頁應用程式中。 這些衝突可以從主控台解決。

資源同步之後， **升級後** 命令可讓您偵測同步是否產生錯誤或警告。

### 檢視同步化結果 {#view-the-synchronization-result}

可以用兩種方式檢視同步化結果：

* 在命令列介面中，錯誤會以三個>形箭號具體化 **>>>** 和同步會自動停止。 以雙>形箭號具體化警告 **>>** 同步完成後，必須解析和。 升級後結束時，命令提示字元中會顯示摘要。 例如：

  ```
  2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
  2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
  2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
  2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
  2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
  ```

  如果警告與資源衝突有關，操作員必須注意解決衝突。

* 此 **升級後_`<server version number>`升級後時間(_T)`>`.log** 檔案包含同步化結果。 預設可在下列目錄中使用： **安裝目錄/var/`<instance>`升級後**. 錯誤和警告會由 **錯誤** 和 **警告** 屬性。

### 解決衝突 {#resolve-a-conflict}

解決衝突必須僅由進階運運算元及已授予「管理員」許可權的操作者執行。

若要解決衝突，請套用下列程式：

1. 在Adobe Campaign樹狀結構中，將游標置於 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**.
1. 在清單中選取要解決的衝突。

解決衝突有三種可能方式：

* **[!UICONTROL Declared as resolved]**：需要運運算元預先介入。
* **[!UICONTROL Accept the new version]**：如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]**：表示更新遭拒。

  >[!IMPORTANT]
  >
  如果您選取此解決模式，新版本中的修補程式可能會遺失。 因此，強烈建議不要使用此選項，或僅保留給專家運運算元。

如果您選擇手動解決衝突，請按照以下步驟進行：

1. 在視窗的下半部分，搜尋 **`_conflict_ string`** 以找出有衝突的圖元。 與新版本一起安裝的實體包含 **新** 引數，符合先前版本的實體包含 **cus** 引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想要保留的版本。 刪除 **`_conflict_argument_ string`** 實體的URL名稱。

   ![](assets/s_ncs_production_conflict003.png)

1. 移至您原本要解決的衝突。 按一下 **[!UICONTROL Actions]** 圖示並選取 **[!UICONTROL Declare as resolved]**.
1. 儲存變更：衝突現已解決。

## Tomcat {#tomcat}

Adobe Campaign v7中的整合Tomcat伺服器已變更版本。 因此，它的安裝資料夾(tomcat-6)也改變了(tomcat 7)。 升級後，請確定路徑確實連結到更新後的資料夾(在 **[!UICONTROL serverConf.xml]** 檔案)：

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

**升級後之前**&#x200B;中，您必須刪除6.02版中所有在v7中不再存在的結構描述參考。

* nms：emailOfferView
* nms：webOfferView
* nms：callCenterOfferView
* nms：mobileOfferView
* nms：paperOfferView

### 選件內容 {#offer-content}

在v7中，已移動選件內容。 在v6.02中，內容位於每個代表結構描述(**nms：emailOfferView**)。 在v7中，內容現在位於選件結構描述中。 因此，升級後內容將不會顯示在介面中。 升級後，您必須重新建立優惠方案內容，或開發指令碼，自動將內容從代表結構描述移至優惠方案結構描述。

>[!IMPORTANT]
>
如果某些使用已設定選件的傳送會在移轉後傳送，您必須在v7中刪除並重新建立所有這些傳送。 如果您無法這麼做，系統會提供「相容性模式」。 不建議使用此模式，因為您將無法受益於Interaction v7中的所有新功能。 這是一種轉換模式，可讓您在實際6.1移轉之前完成進行中的行銷活動。 如需有關此模式的詳細資訊，請連絡我們。

移動指令碼的範例(**interactionTo610_full_XX.js**)中提供 **移轉** 在Adobe Campaign v7資料夾內建立資料夾。 此檔案為使用者端顯示指令碼範例，每個選件使用單一電子郵件呈現(選件 **[!UICONTROL htmlSource]** 和 **[!UICONTROL textSource]** 欄位)。 中的內容 **NmsEmailOfferView** 表格已移至選件表格。

>[!NOTE]
>
使用此指令碼無法讓您受益於「內容管理」和「演算函式」選項。 若要受益於這些功能，您必須重新思考目錄選件，尤其是選件內容和設定空間。

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

如果您只有一個環境，以下是移動優惠方案內容後要遵循的程式。 在此案例中，讓我們以「環境」為例。

1. 在所有「環境」環境選件空間中，更新使用的欄位清單。 例如，對於只使用 **[!UICONTROL htmlSource]**，您必須新增 **[!UICONTROL view/htmlSource]**.

   ![](assets/migration_interaction_2.png)

1. 在 **[!UICONTROL Type of Environment]** 欄位(在 **[!UICONTROL General]** 索引標籤，選取 **[!UICONTROL Live]**.

   ![](assets/migration_interaction_3.png)

1. 建立設計環境（例如「ENV_DESIGN」）並將其連線到環境線上環境。

   ![](assets/migration_interaction_4.png)

1. 部署所有「環境」環境選件空間(按一下右鍵> **[!UICONTROL Actions > Deploy]**)並選取「ENV_DESIGN」環境。

   ![](assets/migration_interaction_5.png)

1. 對所有「環境」環境選件執行相同操作。
1. 在相關管道上啟用所有環境選件「ENV_DESIGN」。
1. 測試讓選件上線。 如果您沒有遇到任何問題，請在最新的工作流程任務上執行暫緩任務 **[!UICONTROL Offer notification]** (offerMgt)讓所有優惠方案上線。

   ![](assets/migration_interaction_6.png)

1. 執行完整的測試。

   >[!NOTE]
   >
   線上類別和優惠方案的名稱會在上線後修改。 在傳入頻道上，更新優惠和類別的所有參考。

## 報告 {#reports}

### 標準報表 {#standard-reports}

目前所有標準報表都使用轉譯引擎v6.x。如果您已將JavaScript新增至這些報表，則某些元素可能無法再運作。 事實上，舊版JavaScript與v6.x轉譯引擎不相容。 因此，您必須檢查JavaScript程式碼，並在稍後加以調整。 您應該測試每個報表，特別是匯出函式。

### 個人化報表 {#personalized-reports}

<!--If you want to have the blue banner from v7 (allowing you access to the tabs), you must republish reports. If you encounter problems, you can force the v6.0 rendering engine. To do this, go to **[!UICONTROL Properties]** within the report, click **[!UICONTROL Rendering]** and choose the **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** rendering engine.

![](assets/migration_reports_1.png)
-->
如果您希望從新的報告功能中獲益，則必須重新發佈報告。 在此情況下，請檢查所有指令碼，並視需要加以變更。 關於PDF匯出，如果您已為Open Office新增特定指令碼，這將無法再與新的PDF匯出引擎(PhantomJS)搭配使用。

## 網頁應用程式 {#web-applications}

網頁應用程式系列有兩種：

* 已識別的網頁應用程式（一起檢視、核准表單、外部網路內部開發）、
* 匿名網路應用程式（網路或調查表）。

### 已識別的網頁應用程式 {#identified-web-applications}

就像報告一樣([瞭解更多](#reports))，如果您已新增JavaScript，則必須檢查並視需要調整。 如果您希望受益於v7藍色橫幅（包含藍色標籤），您必須重新發佈網頁應用程式。

v7中的Web應用程式連線方法已變更。 如果您在已識別的Web應用程式中遇到任何連線問題，您必須暫時啟動 **allowUserPassword** 和 **sessionTokenOnly** 中的選項 **serverConf.xml** 檔案。 升級後，請修改以下選項值：

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

因此，請使用以下命令重新啟動升級後：

```
nlserver config -postupgrade -instance:<instance_name> -force
```

請先在v6.x轉譯引擎中測試您的Web應用程式，然後再發佈。 然後停用這兩個選項。

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### 匿名網路應用程式 {#anonymous-web-applications}

如果您遇到任何問題，請重新發佈網頁應用程式。
