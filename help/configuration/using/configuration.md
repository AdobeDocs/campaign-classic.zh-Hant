---
title: 配置
seo-title: 配置
description: 配置
seo-description: null
page-status-flag: never-activated
uuid: 0f2aadc3-5199-476c-9956-6e39b899a7d0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
discoiquuid: b781fd52-828c-4582-a546-a1fee7e5a26d
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 912507f25c5bc3c1ca7121b0df8182176900f4c0

---


# 配置{#configuration}

導覽清單所使用的資料夾類型在遵循 **xtk:navtree架構語法的XML檔案中描述** 。

XML文檔的結構如下：

```
<navtree name="name" namespace="name_space">
  <!-- Global commands -->
  <commands>
      ...
  </commands>
  
  <!-- Structured space for adding a folder -->
  <model name="<name>" label="<Label>">
    <!-- Folder type -->
    <nodeModel>
      ...
    </nodeModel>
<model name="<name>" label="<Sub model>">
      ...
    </model>
  </model> 
</navtree>
```

XML文檔包含具有 **`<navtree>`** 名稱和命名空 **間屬****** 性的根元素，以指定文檔名和命名空間。 名稱和名稱空間構成檔案識別索引鍵。

應用程式的全局命令在文檔中從元素聲明 **`<commands>`** 出來。

檔案類型的聲明在文檔中具有以下元素： **`<model>`** 和 **`<nodemodel>`**。

## 全局命令 {#global-commands}

全域命令可讓您啟動動作。 此動作可以是輸入表單或SOAP呼叫。

可從主菜單訪問全局 **[!UICONTROL Tools]** 命令。

命令配置結構如下：

```
<commands>
  <!-- Description of a command -->
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
  <!-- Separator -->
  <command label="-" name="<name>"/>
  <!-- Command structure -->
  <command name="<name>" label="<Label>">
    <command...
  </command>
</commands>
```

在元素中輸入全局命令的說明， **`<command>`** 其屬性如下：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一
* **標籤**:命令的標籤。
* **desc**:說明可從主螢幕的狀態欄中看到。
* **表格**:要啟動的表單：要輸入的值是輸入表單的識別鍵(例如，&quot;cus:recipient&quot;)
* **權限**:允許訪問此命令的命名權限清單（以逗號分隔）。 可從資料夾存取可用權限的 **[!UICONTROL Administration > Access management > Named rights]** 清單。
* **promptLabel**:在命令執行之前顯示確認框。

元 **`<command>`** 素可以包 **`<command>`** 含子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子功能表。

這些命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 它由命令標 **簽中包含的** &#39;-&#39;值標識。

標籤及其輸入參 **`<soapcall>`** 數的可選存在定義了要執行的SOAP方法的調用。 如需SOAP API的詳細資訊，請參閱 [Campaign JSAPI檔案](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。

從標籤初始化時，可更新表單內 **`<enter>`** 容。 有關此標籤的詳細資訊，請參閱輸入表單的檔案。

**範例**:

* 聲明全域命令以啟動&quot;xtk:import&quot;表單：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在命令標籤中存在鍵盤快捷鍵，在「I」字元上 **聲明(** &amp;I)。

* 具有分隔符的子菜單示例：

   ![](assets/d_ncs_integration_navigation_exemple1.png)

   ```
   <command label="Administration" name="admin">
     <command name="cmd1" label="Example 1" form="cus:example1"/>
     <command name="sep" label="-"/>
     <command name="cmd1" label="Example 2" form="cus:example2">
       <enter>
         <set xpath="@type" expr="1"/>
       </enter>
     </command>
   </command>
   ```

* 執行SOAP方法：

   ```
   <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
     <soapCall name="Execute" service="xtk:sql"/>
   </command>
   ```

## 資料夾類型 {#folder-type}

資料夾類型可讓您存取結構的資料。 與資料夾關聯的視圖由清單和輸入表單組成。

資料夾類型配置結構如下：

```
<!-- Structured location to add the folder -->
<model name="name" label="Labelled">
  <!-- Type of folder -->
  <nodeModel name="<name>" label="<Labelled>" img="<image>">
    <view name="<name>" schema="<schema>" type="<listdet|list|form|editForm>">
      <columns>
        <node xpath="<field1>"/>
        ...
    </columns>
    </view> 
  </nodeModel>
  <model name="<name>" label="<Sous modèle>">
    ...
  </model>
</model>
```

必須在元素下輸入資料夾類型 **`<model>`** 聲明。 此元素可讓您定義可從功能表檢視的階層 **[!UICONTROL Add new folder]** 組織。 元素 **`<model>`** 必須包含元 **`<nodemodel>`** 素和其他 **`<model>`** 元素。

名 **稱****和標籤屬性會填入元素的內部名稱，以及功能表中顯示的****[!UICONTROL Add new folder]** 標籤。

元素 **`<nodemodel>`** 包含資料夾類型的說明，其屬性如下：

* **名稱**:內部名稱
* **標籤**:標籤(用於功 **[!UICONTROL Add new folder]** 能表中)和作為插入資料夾時的預設標籤。
* **img**:檔案夾插入時的預設影像。
* **hiddenCommands**:要被遮色的命令清單（以逗號分隔）。 可能的值：「insert」、「delete」、「update」和「duplicate」。
* **newFolderShortCuts**:資料夾建立中模型&#x200B;**`<nodemodel>`** 的捷徑清單（以逗號分隔）。
* **insertRight**, **editRight**, **deleteRight**:用於插入、編輯和刪除資料夾的權限。

元素 **`<view>`** 下的元素 **`<nodemodel>`** 包含與視圖關聯的清單的配置。 清單的模式在元素的模式屬 **性中****`<view>`** 輸入。

要編輯清單的記錄，將隱式使用與清單方案同名的輸入表單。 元 **素上的** type屬 **`<view>`** 性會影響表單的顯示。 可能的值包括：

* **listdet**:在清單底部顯示表單。
* **清單**:單獨顯示清單。 表單會以連按兩下或透過選取清單功能表中的「開啟」啟動。
* **表格**:顯示只讀表單。
* **editForm**:以編輯模式顯示表單。

>[!NOTE]
>
>通過在元素中輸入form屬性，可以過載輸 **入表** 單的 **`<view>`** 名稱。

清單列的預設配置是通過元素輸 **`<columns>`** 入的。 在包含 **`<node>`** xpath屬性的元素上宣 **** 告一列，其模式中要引用的欄位為其值。

**範例**:&quot;nms:recipient&quot;架構上的資料夾類型聲明。

```
<model label="Profiles and targets" name="nmsProfiles">
  <nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
             img="nms:folder.png" insertRight="folderInsert" label="Recipients"
             name="nmsFolder">
    <view name="listdet" schema="nms:recipient" type="listdet">
      <columns>
        <node xpath="@firstName"/>
        <node xpath="@lastName"/>
        <node xpath="@email"/>
        <node xpath="@account"/>
      </columns>
    </view>
  </nodeModel>
  <nodeModel name="nmsGroup" label="Groups"...
</model>
```

相應的資料夾插入菜單：

![](assets/d_ncs_integration_navigation_exemple2.png)

載入清單時，可套用篩選和排序：

```
<view name="listdet" schema="nms:recipient" type="listdet">
  <columns>
    ...
  </columns>

  <orderBy>
    <node expr="@lastName" desc="true"/>
</orderBy>
  <sysFilter>
    <condition expr="@type = 1"/>
  </sysFilter>
</view>  
```

### 快速鍵命令 {#shortcut-commands}

快捷方式命令可讓您在選擇清單時啟動操作。 動作可以是輸入表單或SOAP呼叫。

可從清單菜單或相 **[!UICONTROL Action]** 關菜單按鈕訪問命令。

命令配置結構如下：

```
<nodeModel...
  ...
  <command name="<name>" label="<label>" desc="<Description>" form="<form>" rights="<rights>">
    <soapCall name="<name>" service="<schema>">
      <param type="<type>" exprIn="<xpath>"/>  
        ...
    </soapCall>
    <enter>
      ...
    </enter>
  </command>
</nodeModel>
```

在元素上輸入命令的說明， **`<command>`** 其屬性如下：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一。
* **標籤**:命令的標籤。
* **desc**:說明可從主螢幕的狀態欄中看到。
* **表格**:要啟動的表單：要輸入的值是輸入表單的識別鍵(例如，&quot;cus:recipient&quot;)。
* **權限**:允許訪問此命令的命名權限清單（以逗號分隔）。 可從資料夾存取可用權限的 **[!UICONTROL Administration > Access management > Named rights]** 清單。
* **promptLabel**:在命令執行之前顯示確認框
* **monoSelection**:強制單選（預設為是多選）。
* **refreshView**:在命令執行後強制重新載入清單。
* **enabledIf**:根據輸入的表達式激活該命令。
* **img**:輸入允許從清單工具欄訪問命令的影像。

元 **`<command>`** 素可以包 **`<command>`** 含子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子功能表。

這些命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 它由命令標 **簽中包含的** &#39;-&#39;值標識。

標籤及其輸入參 **`<soapcall>`** 數的可選存在定義了要執行的SOAP方法的調用。 如需SOAP API的詳細資訊，請參閱 [Campaign JSAPI檔案](http://docs.campaign.adobe.com/doc/AC/en/jsapi/index.html)。

表單內容可透過標籤在初始化時更 **`<enter>`** 新。 有關此標籤的詳細資訊，請參閱輸入表單檔案。

**範例**:

```
<command desc="Cancel execution of the job" enabledIf="EV(@status, 'running')"
         img="nms:difstop.bmp" label="Cancel..." name="cancelJob" 
         promptLabel="Do you really want to cancel this job?" refreshView="true">
  <soapCall name="Cancel" service="xtk:jobInterface"/>
</command>
<command label="-" name="sep1"/>
<command desc="Execute selected template" form="cus:form" lmonoSelection="true" name="executeModel"
         rights="import,export,aggregate">
  <enter>
    <set expr="0" xpath="@status"/>
  </enter>
</command>
```

### 連結的資料夾 {#linked-folder}

資料夾管理操作有兩種類型：

1. 資料夾是視圖：該清單顯示與方案關聯的所有記錄，並且可能在資料夾屬性中輸入系統篩選。
1. 資料夾已連結：清單中的記錄會在資料夾連結上隱式篩選。

對於連結的資料夾，必 **須填入元素上的****`<nodemodel>`** folderLink屬性。 此屬性包含資料架構中配置的資料夾上的連結的名稱。

資料方案中連結資料夾的聲明示例：

```
<element default="DefaultFolder('nmsFolder')" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="own" revLabel="Recipients" target="xtk:folder" type="link"/>
```

名為「 **`<nodemodel>`** folder」的資料夾連結上的配置如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```

