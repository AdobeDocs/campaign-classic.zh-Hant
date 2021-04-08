---
solution: Campaign Classic
product: campaign
title: 配置
description: 配置
audience: configuration
content-type: reference
topic-tags: navigation-hierarchy
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 1%

---

# 設定促銷活動檔案總管導覽樹{#configuration}

身為專家用戶，您可以在瀏覽器樹中添加資料夾並對其進行自定義。

在本節](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)中進一步瞭解促銷活動瀏覽器和導覽階層[。

導航清單使用的資料夾類型在遵循&#x200B;**xtk:navtree**&#x200B;模式的語法的XML文檔中進行了描述。

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

XML文檔包含&#x200B;**`<navtree>`**&#x200B;根元素，其中&#x200B;**name**&#x200B;和&#x200B;**namespace**&#x200B;屬性用於指定文檔名和namespace。 名稱和名稱空間構成檔案識別索引鍵。

應用程式的全局命令在文檔中從&#x200B;**`<commands>`**&#x200B;元素聲明。

檔案類型的聲明在文檔中具有以下元素：**`<model>`**&#x200B;和&#x200B;**`<nodemodel>`**。

## 全局命令{#global-commands}

全域命令可讓您啟動動作。 此動作可以是輸入表單或SOAP呼叫。

可從主&#x200B;**[!UICONTROL Tools]**&#x200B;菜單訪問全局命令。

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

在&#x200B;**`<command>`**&#x200B;元素中輸入全局命令的說明，其屬性如下：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一
* **標籤**:命令的標籤。
* **desc**:說明可從主螢幕的狀態欄中看到。
* **表格**:要啟動的表單：要輸入的值是輸入表單的識別鍵(例如，&quot;cus:recipient&quot;)
* **權限**:允許訪問此命令的命名權限清單（以逗號分隔）。可從&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;資料夾訪問可用權限清單。
* **promptLabel**:在命令執行之前顯示確認框。

**`<command>`**&#x200B;元素可包含&#x200B;**`<command>`**&#x200B;子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子功能表。

這些命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 它由命令標籤中包含的&#x200B;**&#39;-&#39;**&#x200B;值標識。

**`<soapcall>`**&#x200B;標籤及其輸入參數的可選存在定義了要執行的SOAP方法的調用。 有關SOAP API的詳細資訊，請參閱[促銷活動JSAPI檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

從&#x200B;**`<enter>`**&#x200B;標籤初始化時，可更新表單內容。 有關此標籤的詳細資訊，請參閱輸入表單的檔案。

**範例**:

* 聲明全域命令以啟動&quot;xtk:import&quot;表單：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   命令標籤中&#x200B;**&amp;**&#x200B;的存在會在「I」字元上宣告鍵盤快速鍵。

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

## 資料夾類型{#folder-type}

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

必須在&#x200B;**`<model>`**&#x200B;元素下輸入資料夾類型聲明。 此元素可讓您定義可從&#x200B;**[!UICONTROL Add new folder]**&#x200B;功能表看到的階層式組織。 **`<model>`**&#x200B;元素必須包含&#x200B;**`<nodemodel>`**&#x200B;元素和其他&#x200B;**`<model>`**&#x200B;元素。

**name**&#x200B;和&#x200B;**label**&#x200B;屬性填入元素的內部名稱和顯示在&#x200B;**[!UICONTROL Add new folder]**&#x200B;功能表中的標籤。

**`<nodemodel>`**&#x200B;元素包含資料夾類型的說明，其屬性如下：

* **名稱**:內部名稱
* **標籤**:標籤(用於菜 **[!UICONTROL Add new folder]** 單中)和作為插入資料夾時的預設標籤。
* **img**:檔案夾插入時的預設影像。
* **hiddenCommands**:要被遮色的命令清單（以逗號分隔）。可能的值：&quot;adbnew&quot;、&quot;adbsave&quot;、&quot;adbcancel&quot;和&quot;adbdup&quot;。
* **newFolderShortCuts**:建立檔案夾時模型&#x200B;**`<nodemodel>`** 的捷徑清單（以逗號分隔）。
* **insertRight**,  **editRight**,  **deleteRight**:用於插入、編輯和刪除資料夾的權限。

**`<nodemodel>`**&#x200B;元素下的&#x200B;**`<view>`**&#x200B;元素包含與視圖關聯的清單的配置。 清單的模式輸入在&#x200B;**`<view>`**&#x200B;元素的&#x200B;**schema**&#x200B;屬性中。

要編輯清單的記錄，將隱式使用與清單方案同名的輸入表單。 **`<view>`**&#x200B;元素上的&#x200B;**type**&#x200B;屬性會影響表單的顯示。 可能的值包括：

* **listdet**:在清單底部顯示表單。
* **清單**:單獨顯示清單。表單會以連按兩下或透過選取清單功能表中的「開啟」啟動。
* **表格**:顯示只讀表單。
* **editForm**:以編輯模式顯示表單。

>[!NOTE]
>
>通過在&#x200B;**`<view>`**&#x200B;元素中輸入&#x200B;**form**&#x200B;屬性，可以使輸入表單的名稱過載。

清單列的預設配置是通過&#x200B;**`<columns>`**&#x200B;元素輸入的。 在包含&#x200B;**xpath**&#x200B;屬性的&#x200B;**`<node>`**&#x200B;元素上聲明列，其中該欄位在其模式中作為其值引用。

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

### 快捷鍵命令{#shortcut-commands}

快捷方式命令可讓您在選擇清單時啟動操作。 動作可以是輸入表單或SOAP呼叫。

可從清單的&#x200B;**[!UICONTROL Action]**&#x200B;菜單或相關菜單按鈕訪問命令。

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

在&#x200B;**`<command>`**&#x200B;元素上輸入命令的說明，其屬性如下：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一。
* **標籤**:命令的標籤。
* **desc**:說明可從主螢幕的狀態欄中看到。
* **表格**:要啟動的表單：要輸入的值是輸入表單的識別鍵(例如，&quot;cus:recipient&quot;)。
* **權限**:允許訪問此命令的命名權限清單（以逗號分隔）。可從&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;資料夾訪問可用權限清單。
* **promptLabel**:在命令執行之前顯示確認框
* **monoSelection**:強制單選（預設為是多選）。
* **refreshView**:在命令執行後強制重新載入清單。
* **enabledIf**:根據輸入的表達式激活該命令。
* **img**:輸入允許從清單工具欄訪問命令的影像。

**`<command>`**&#x200B;元素可包含&#x200B;**`<command>`**&#x200B;子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子功能表。

這些命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 它由命令標籤中包含的&#x200B;**&#39;-&#39;**&#x200B;值標識。

**`<soapcall>`**&#x200B;標籤及其輸入參數的可選存在定義了要執行的SOAP方法的調用。 有關SOAP API的詳細資訊，請參閱[促銷活動JSAPI檔案](https://docs.adobe.com/content/help/en/campaign-classic/technicalresources/api/index.html)。

表單內容可透過&#x200B;**`<enter>`**&#x200B;標籤在初始化時更新。 有關此標籤的詳細資訊，請參閱輸入表單檔案。

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

### 連結資料夾{#linked-folder}

資料夾管理操作有兩種類型：

1. 資料夾是視圖：該清單顯示與方案關聯的所有記錄，並且可能在資料夾屬性中輸入系統篩選。
1. 資料夾已連結：清單中的記錄會在資料夾連結上隱式篩選。

對於連結的資料夾，必須填入&#x200B;**`<nodemodel>`**&#x200B;元素上的&#x200B;**folderLink**&#x200B;屬性。 此屬性包含資料架構中配置的資料夾上的連結的名稱。

資料方案中連結資料夾的聲明示例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

名為&quot;folder&quot;的資料夾連結上的&#x200B;**`<nodemodel>`**&#x200B;配置如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
