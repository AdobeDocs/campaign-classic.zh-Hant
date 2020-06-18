---
title: 一般配置
seo-title: 一般配置
description: 一般配置
seo-description: null
page-status-flag: never-activated
uuid: 317a145d-36b0-40fe-a272-ad5e35b0b190
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: migration
content-type: reference
topic-tags: configuration
discoiquuid: f4b1c108-7f71-4aa1-8394-a7f660834c9c
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: e7de74feb61cc8f4b386a6ff86fc58b9c9e9ca1d
workflow-type: tm+mt
source-wordcount: '2822'
ht-degree: 0%

---


# 一般配置{#general-configurations}

本節詳細說明如果您要從v5.11或v6.02移轉，在Adobe Campaign v7中執行的設定。

此外：

* 如果您從v5.11移轉，您也必須完成v5.11中「特定 [組態」一節中的設定](../../migration/using/specific-configurations-in-v5-11.md) 。
* 如果您從v6.02進行移轉，您也必須完成v6.02中「特定 [組態」一節中的設定](../../migration/using/specific-configurations-in-v6-02.md) 。

## 時區 {#time-zones}

### 多時區模式 {#multi-time-zone-mode}

在v6.02中，「多時區」模式僅適用於PostgreSQL資料庫引擎。 現在，不論使用何種類型的資料庫引擎，都可提供此功能。 我們強烈建議您將您的基本系統轉換為「多時區」基本系統。

要使用TIMESTAMP WITH TIMEZONE模式，還需要將 **-userTimestamptz:1** 選項添加到postupgrade命令行。

>[!IMPORTANT]
>
>如果 **-usetimestamptz:1** 參數與不相容的資料庫引擎一起使用，則資料庫將損壞，您必須恢復資料庫的備份並重新執行上述命令。

>[!NOTE]
>
>在通過控制台（節點）遷移後，可以更改&#x200B;**[!UICONTROL Administration > Platform > Options > WdbcTimeZone]** 時區。
>
>有關時區管理的詳細資訊，請參 [閱本節](../../installation/using/time-zone-management.md)。

### Oracle {#oracle}

如果在配置過程中出現 **ORA 01805** 錯誤，這表示應用程式伺服器與資料庫伺服器之間的Oracle時區檔案不同步。 若要重新同步這些檔案，請套用下列步驟：

1. 要標識所使用的時區檔案，請運行以下命令：

   ```
   select * from v$timezone_file
   ```

   時區檔案通常位於 **ORACLE_HOME/oracore/zoneinfo/資料夾中** 。

1. 請確定兩個伺服器上的時區檔案都相同。

如需詳細資訊，請造訪： [https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004](https://docs.oracle.com/cd/E11882_01/server.112/e10729/ch4datetime.htm#NLSPG004).

客戶端和伺服器之間的時區未對準也會導致一些滯後。 這就是為什麼建議在客戶端和伺服器端使用相同版本的Oracle庫，兩個時區必須相同。

要檢查兩側是否位於同一時區：

1. 通過運行以下命令檢查客戶端上的時區檔案版本：

   ```
   genezi -v
   ```

   genezi是位於 **$ORACLE_HOME/bin儲存庫中的二進位檔案** 。

1. 運行以下命令檢查伺服器端的時區檔案版本：

   ```
   select * from v$timezone_file
   ```

1. 要更改客戶端上的時區檔案，請使用 **ORA_TZFILE** 環境變數。

## 安全性 {#security}

### 安全區 {#security-zones}

>[!IMPORTANT]
>
>基於安全性原因，Adobe Campaign平台不再預設為可存取： 您必須設定安全區，因此必須收集營運商IP位址。

Adobe Campaign v7包含安全區 **的概念**。 每個用戶都必須與區域關聯才能登錄到實例，並且用戶的IP地址必須包含在安全區域中定義的地址或地址範圍中。 您可在Adobe Campaign伺服器設定檔案中設定安全區。 必須在控制台(**[!UICONTROL Administration > Access management > Operators]**)中定義用戶關聯到的安全區。

**在遷移之前**，請向網路管理員請求幫助定義在遷移後要激活的安全區。

**在配置升級後** （伺服器重新啟動之前），必須配置安全區。

此部分提供安全區 [配置](../../installation/using/configuring-campaign-server.md#defining-security-zones)。

### 使用者密碼 {#user-passwords}

在v7中，內 **部** 和管 **理員運** 算子連線必須以密碼保全。 我們強烈建議在移轉之前，先為這些帳戶和所有運算元帳戶指 **派密碼**。 如果您未為內部指定 **密碼**，將無法連接。 要為內部分配密 **碼**，請輸入以下命令：

```
nlserver config -internalpassword
```

>[!IMPORTANT]
>
>所有 **追蹤伺服器** 的內部密碼必須相同。 如需詳細資訊，請參 [閱本節](../../installation/using/campaign-server-configuration.md#internal-identifier)[和本節](../../platform/using/access-management.md#about-permissions)。

### v7的新功能 {#new-features-in-v7}

* 沒有權限的使用者無法再連線至Adobe Campaign。 必須手動添加其權限，例如，建立名為connect的權 **限**。

   受此修改影響的使用者會在設定檔中識別並列出。

* 如果密碼為空，追蹤不再有效。 如果是這樣，將會出現一條錯誤消息，要求您重新配置它。
* 使用者密碼不再儲存在 **xtk:sessionInfo** 架構中。
* 現在，使用 **xtk:builder:EvaluateJavaScript** 和 **** xtk:builder:EvaluateJavaScriptTemplate函式時，需要管理權限。

某些現成可用的結構已修改，現在預設只有具有管理員權限的運算子才能使用寫入存取 **權** :

* ncm：發佈
* nl：監控
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
* xtk：影像
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
* xtk：字串
* xtk:xslt

### Sessiontoken參數 {#sessiontoken-parameter}

在v5中， **sessiontoken** 參數適用於用戶端（概述類型畫面、連結編輯器等的清單） 和伺服器端（網路應用程式、報表、jsp、jssp等）。 在v7中，它只適用於伺服器端。 如果您想要回到v5的完整功能，您必須使用此參數修改連結，並透過連線頁面傳遞：

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
>如果您使用連結有受信任IP遮色片的運算子，請檢查其是否擁有最低權限，以及其是否位於 **sessionTokenOnly模式中的安全區** 。

### SQL函式 {#sql-functions}

未知的SQL函式調用不再自然地發送到伺服器。 目前，所有SQL函式都必須新增至 **xtk:funcList** (如需詳細資訊，請參 [閱本節](../../configuration/using/adding-additional-sql-functions.md))。 遷移時，在配置級別期間添加一個選項，允許您與舊的未聲明SQL函式保持相容。 如果要繼續使用這些函式，請檢查 **XtkPassUnknownSQLFunctionsToRDBMS** 選項是否確實在節點級 **[!UICONTROL Administration > Platform > Options]** 別定義。

>[!IMPORTANT]
>
>我們強烈建議不要使用此選項，因為它會帶來安全風險。

### JSSP {#jssp}

如果您想要授權透過HTTP通訊協定（非HTTPS）存取特定頁面，例如在您的Web應用程式中，無論在安全區中執行何種設定，您必須在對應的中繼規則中指定 **httpAllowed=&quot;true** &quot;參數。

如果您使用匿名JSSP，則必須在JSSP（檔案）的中繼規則中新增 **httpAllowed=&quot;true&quot;****[!UICONTROL serverConf.xml]** 參數：

例如：

```
<url IPMask="" deny="" hostMask="" httpAllowed="true" relayHost="true" relayPath="true"
           status="blocklist" targetUrl="https://localhost:8080" timeout="" urlPath="*/cus/myPublicPage.jssp"/>
```

## 語法 {#syntax}

### JavaScript {#javascript}

Adobe Campaign v7整合了更新的JavaScript解譯器。 但是，此更新可能會導致某些指令碼運行不正常。 由於舊版引擎的權限較大，因此某些語法將可以運作，而新版引擎則不再適用。

語 **[!UICONTROL myObject.@attribute]** 法現在只對XML物件有效。 此語法可用於個人化傳送和內容管理。 如果您在非XML物件上使用此類語法，個人化功能將不再有效。

對於所有其他對象類型，語法現在 **[!UICONTROL myObject`[`為「attribute」`]`]**。 例如，使用下列語法的非XML物件：**[!UICONTROL employee.@sn]**，現在必須使用下列語法：**[!UICONTROL employee`[`「sn」`]`]**。

* 前語法：

   ```
   employee.@sn
   ```

* 新語法：

   ```
   employee["sn"]
   ```

要更改XML對象中的值，現在需要先更新值，然後才添加XML節點：

* 舊JavaScript程式碼：

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

* 前語法：

   ```
   if(serverForm.activities[ctx.activityHistory.activity[0].@name].type !="end")
   ```

* 新語法：

   ```
   if(serverForm.activities[String(ctx.activityHistory.activity[0].@name)].type !="end"
   ```

### SQLData {#sqldata}

為了加強例項安全性，Adobe Campaign v7已引入新語法，以取代以SQLData為基礎的語法。 如果您將此語法與這些程式碼元素搭配使用，則必須加以修改。 主要內容是：

* 依子查詢篩選： 新語法是以元素為 `<subQuery>` 基礎，以定義子查詢
* 匯總： 新語法為&quot;aggregate function(collection)&quot;
* 依連結篩選： 新語法為 `[schemaName:alias:xPath]`

查詢定義(xtk:queryDef)架構已修改：

* 有新元 `<subQuery>` 素可用來替換SQLData中包含的SELECT
* 為@setOperator屬性引入兩個新值&quot;IN&quot;和&quot;NOT IN&quot;
* 新元 `<where>` 素，是元素的子 `<node>` 項： 這可讓您在SELECT中進行「子選擇」

使用&quot;@expr&quot;屬性時，可能存在SQLData。 可搜尋下列詞語： &quot;SQLData&quot;、&quot;aliasSqlTable&quot;、&quot;sql&quot;。

Adobe Campaign v7例項預設會受到保護。 安全性來自檔案中安全區的定 **[!UICONTROL serverConf.xml]** 義： allowSQLInjoffent **** 屬性管理SQL語法安全性。

如果在配置級執行期間發生SQLData錯誤，則必須修改此屬性以暫時允許使用基於SQLData的語法，從而允許重寫代碼。 為此，必須在serverConf.xml檔案中變更 **下列選項** :

```
allowSQLInjection="true"
```

因此，請使用下列命令重新啟動postupgrade:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

您必須設定安全區(請參 [閱Security](#security))，然後變更下列選項以重新啟用安全性：

```
allowSQLInjection="false"
```

以下是舊語法與新語法的比較範例。

**依子查詢篩選**

* 前語法：

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

* 前語法：

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

**集合**

集合函式（集合）

* 前語法：

   ```
   <node sql="(select count(*) from NmsNewsgroup WHERE O0.iOperationId=iOperationId)" alias="@nbMessages"/>
   ```

* 新語法：

   ```
   <node expr="count([newsgroup/@id])" alias="../@nbMessages"/>
   ```

   >[!NOTE]
   >
   >對集合函式自動執行節點。 不再需要指定條件WHERE O0.iOperationId=iOperationId。
   >
   >無法再使用&quot;count(*)&quot;函式。 您必須使用「countall()」。

* 前語法：

   ```
   <node sql="(select Sum(iToDeliver) from NmsDelivery WHERE O0.iOperationId=iOperationId AND iSandboxMode=0 AND iState>=45)" alias="@nbMessages"/>
   ```

* 新語法：

   ```
   <node expr="Sum([delivery-linkedDelivery/properties/@toDeliver])" alias= "../@sumToDeliver">
                     <where><condition expr="[validation/@sandboxMode]=0 AND @state>=45" /></where></node>
   ```

**依聯接篩選**

`[schemaName:alias:xPath]`

別名是可選的

* 前語法：

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [SQLDATA[W." + joinPart.source.SQLName + "]]"}
                                            aliasSqlTable={nodeSchemaRoot.SQLTable + " W"}/>
   ```

* 新語法：

   ```
   <condition expr={"[" + joinPart.destination.nodePath + "] = [" + nodeSchema.id + ":" + joinPart.source.nodePath + "]]"}/>
   ```

**秘訣與訣竅**

在元 `<subQuery>` 素中，若要參考主要元素的「欄位」欄 `<queryDef>` 位，請使用下列語法： `[../@field]`

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

移轉是透過程式檔執行，而衝突可能會出現在報表、表單或Web應用程式中。 這些衝突可以從控制台中解決。

在資源同步後， **postupgrade** 命令可讓您檢測同步是否生成錯誤或警告。

### 查看同步結果 {#view-the-synchronization-result}

同步結果可通過兩種方式查看：

* 在命令行介面中，錯誤由三重Chevron **>>>實** 現，並自動停止同步。 警告由雙雪佛龍 **>>實** 現，並且必須在同步完成後解決。 在postupgrade的末尾，將在命令提示符中顯示一個摘要。 例如：

   ```
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     =========Summary of the update==========
   2013-04-09 07:48:39.749Z        00002E7A          1     info    log     test instance, 6 warning(s) and 0 error(s) during the update.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'mobileAppDeliveryFeedback' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.749Z        00002E7A          1     warning log     The document with identifier 'opensByUserAgent' and type 'xtk:report' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     The document with identifier 'deliveryValidation' and type 'nms:webApp' is in conflict with the new version.
   2013-04-09 07:48:39.750Z        00002E7A          1     warning log     Document of identifier 'nms:includeView' and type 'xtk:srcSchema' updated in the database and found in the file system. You will have to merge the two versions manually.
   ```

   如果警告涉及資源衝突，則需要操作員注意才能解決。

* postupgrade **.log`<server version number>`檔案的postupgrade_`>`** _time包含同步結果。 預設情況下，它位於以下目錄： **安裝目錄/var/`<instance>`postupgrade**。 錯誤和警告由錯誤和警 **告屬** 性 **指示** 。

### 解決衝突 {#resolve-a-conflict}

解決衝突只能由高級運算子和那些已獲得「管理員」權限的運算子執行。

要解決衝突，請應用以下流程：

1. 在Adobe Campaign樹狀結構中，將游標置於上方 **[!UICONTROL Administration > Configuration > Package management > Edit conflicts]**。
1. 在清單中選擇要解決的衝突。

解決衝突有三種可能的方法：

* **[!UICONTROL Declared as resolved]**: 需要營運商事先介入。
* **[!UICONTROL Accept the new version]**: 如果使用者未變更隨Adobe Campaign提供的資源，則建議使用。
* **[!UICONTROL Keep the current version]**: 表示更新遭拒。

   >[!IMPORTANT]
   如果選擇此解析模式，則可能丟失新版本中的修補程式。 因此，強烈建議不要將此選項用於或僅保留給專家運算子。

如果您選擇手動解決衝突，請按如下步驟進行：

1. 在窗口的下半部分中，搜索以 **`_conflict_ string`** 查找衝突實體。 隨新版本安裝的實體包含 **new** 引數，與舊版相符的實體包含 **cus** 引數。

   ![](assets/s_ncs_production_conflict002.png)

1. 刪除您不想保留的版本。 刪除您 **`_conflict_argument_ string`** 所保留的實體。

   ![](assets/s_ncs_production_conflict003.png)

1. 前往您已解決的衝突。 按一下圖 **[!UICONTROL Actions]** 示並選取 **[!UICONTROL Declare as resolved]**。
1. 儲存變更： 衝突現已解決。

## Tomcat {#tomcat}

Adobe Campaign v7中整合的Tomcat伺服器已變更版本(Tomcat 7)。 因此，其安裝資料夾(tomcat-6)也發生了更改(tomcat 7)。 在配置升級後，請務必檢查路徑是否連結到更新的資料夾(在檔案 **[!UICONTROL serverConf.xml]** 中):

```
$(XTK_INSTALL_DIR)/tomcat-7/bin/bootstrap.jar 
$(XTK_INSTALL_DIR)/tomcat-7/bin/tomcat-juli.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-util.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/tomcat-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/servlet-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/jsp-api.jar
$(XTK_INSTALL_DIR)/tomcat-7/lib/el-api.jar
```

## 互動 {#interaction}

### 必要條件 {#prerequisites}

**在配置升級前**，您必須從6.02刪除v7中不再存在的所有架構參考。

* nms:emailOfferView
* nms:webOfferView
* nms:callCenterOfferView
* nms:mobileOfferView
* nms:paperOfferView

### 選件內容 {#offer-content}

在v7中，選件內容已移動。 在v6.02中，內容位於每個表示模式(**nms:emailOfferView**)中。 在v7中，內容現在位於選件架構中。 在設定升級後，內容就不會顯示在介面中。 在設定升級後，您必須重新建立選件內容，或開發指令碼，自動將內容從表示架構移至選件架構。

>[!IMPORTANT]
如果某些使用已設定選件的傳送要在移轉後傳送，您必須刪除並在v7中重新建立所有這些傳送。 如果您無法這麼做，則會提供「相容模式」。 不建議使用此模式，因為Interaction v7中的所有新功能都不會讓您受益。 這是一種過渡模式，可讓您在實際6.1移轉之前完成持續的促銷活動。 有關此模式的更多資訊，請與我們聯絡。

Adobe Campaign v7檔案夾中的&#x200B;**Migration**&#x200B;檔案夾提供移動指令碼(interactionTo610_full_XX.js **** )範例。 此檔案顯示客戶端指令碼的範例，每個選件（和欄位）使用單一電子 **[!UICONTROL htmlSource]** 郵件 **[!UICONTROL textSource]** 表示法。 NmsEmailOfferView表中 **** 的內容已移到選件表。

>[!NOTE]
使用此指令碼不允許您從「內容管理」和「轉換函式」選項中獲益。 為了從這些函式中獲益，您必須重新思考目錄選件，尤其是選件內容和設定空間。

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

### 測試與設定 {#tests-and-configuration}

如果您只有一個環境，請移動選件內容後，請遵循以下程式。 在此例中，我們以&quot;ENV&quot;為例。

1. 在所有&quot;ENV&quot;環境中提供空格，請更新所用欄位的清單。 例如，對於僅使用的選件空間， **[!UICONTROL htmlSource]**&#x200B;您必須新增 **[!UICONTROL view/htmlSource]**。

   ![](assets/migration_interaction_2.png)

1. 在頁籤 **[!UICONTROL Type of Environment]** 內的欄位中 **[!UICONTROL General]** ，選擇 **[!UICONTROL Live]**。

   ![](assets/migration_interaction_3.png)

1. 建立設計環境（例如「ENV_DESIGN」）並將其連接到ENV線上環境。

   ![](assets/migration_interaction_4.png)

1. 部署所有「ENV」環境提供空間(按一下右鍵> **[!UICONTROL Actions > Deploy]**)，然後選擇「ENV_DESIGN」環境。

   ![](assets/migration_interaction_5.png)

1. 對所有「ENV」環境選件都執行相同操作。
1. 激活相關通道上的所有環境都提供「ENV_DESIGN」。
1. 測試讓選件上線。 如果您未遇到任何問題，請在最新的工作流程工作( **[!UICONTROL Offer notification]** offerMgt)上執行擱置中的工作，讓所有選件都上線。

   ![](assets/migration_interaction_6.png)

1. 執行完整的測試。

   >[!NOTE]
   線上類別和選件的名稱會在上線後修改。 在傳入渠道上，更新選件和類別的所有參考。

## 報表 {#reports}

### 標準報表 {#standard-reports}

所有標準報表目前都使用轉換引擎v6.x。 如果您已將JavaScript新增至這些報表，某些元素可能不再有效。 事實上，舊版JavaScript與v6.x轉換引擎不相容。 因此，您必須檢查JavaScript程式碼，並稍後加以調整。 您應測試每個報表，尤其是匯出功能。

### 個人化報表 {#personalized-reports}

如果您想要v7的藍色橫幅（可讓您存取宇宙），您必須重新發佈報表。 如果您遇到問題，可以強制使用v6.0轉換引擎。 若要這麼做，請前往報 **[!UICONTROL Properties]** 表內，按一下並 **[!UICONTROL Rendering]** 選擇 **[!UICONTROL Version 6.0 (Flash & OpenOffice)]** 轉換引擎。

![](assets/migration_reports_1.png)

如果您想要從新的報表功能中獲益，則必須選取v.6.x轉換引擎。 在這種情況下，請檢查所有指令碼，並視需要進行更改。 至於PDF匯出，如果您已新增OpenOffice的特定指令碼，這將不再適用於新的PDF匯出引擎(PhantomJS)。

## 網頁應用程式 {#web-applications}

有兩個Web應用程式系列：

* 確定Web應用程式（一起看，核准表單，外部內部開發）,
* 匿名的Web應用程式（網路或問卷表格）。

### 已識別的Web應用程式 {#identified-web-applications}

如同報表(請參 [閱報表](#reports))，如果您已新增JavaScript，您必須視需要檢查並調整。 如果您想要從v7藍色橫幅（包含宇宙）獲益，則必須重新發佈Web應用程式。 如果您的JavaScript程式碼正在運作，您可以選取v6.x轉換引擎。 如果不是這樣，您可以在調整程式碼時使用v6.0轉譯引擎，然後使用v6.x轉譯引擎。

>[!NOTE]
選取轉換引擎的步驟與選取報表的步驟相同。 請參閱 [個人化報表](#personalized-reports)。

v7中的Web應用程式連線方法已變更。 如果您在已識別的Web應用程式中遇到任何連線問題，您必須暫時啟用 **serverConf.xml檔案中的** allowUserPassword **** 和sessionTokenOnly **** 選項。 在配置升級後，請修改下列選項值：

```
allowUserPassword="true"
```

```
sessionTokenOnly="true"
```

因此，請使用下列命令重新啟動postupgrade:

```
nlserver config -postupgrade -instance:<instance_name> -force
```

在發佈之前，請先在v6.x轉換引擎中測試您的網頁應用程式。 然後停用這兩個選項。

```
allowUserPassword="false"
```

```
sessionTokenOnly="false"
```

### 匿名Web應用程式 {#anonymous-web-applications}

如果您遇到任何問題，請重新發佈Web應用程式。 如果問題仍然存在，您可以選取v6.0轉換引擎。 如果您尚未新增JavaScript，則可以選取v6.x轉換引擎，並受益於其新功能。

>[!NOTE]
選取轉換引擎的步驟與選取報表的步驟相同。 請參閱 [個人化報表](#personalized-reports)。

## 紅帽 {#red-hat}

如果v6.02或v5.11中已刪除現成可用的結構描述，在配置升級後，您可能無法再編輯結構描述。 如果發生這種情況，請執行命令：

```
su - neolane
nlserver config -postupgrade -instance:<instance name> -force
```
