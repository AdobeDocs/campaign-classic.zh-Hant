---
product: campaign
title: 設定Campaign Explorer導覽樹狀結構
feature: Application Settings
description: 瞭解如何設定Campaign Explorer導覽樹狀結構
role: Data Engineer, Developer
badge-v7-only: label="v7" type="Informative" tooltip="僅適用於 Campaign Classic v7"
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 28638e76bf286f253bc7efd02db848b571ad88c4
workflow-type: tm+mt
source-wordcount: '1193'
ht-degree: 0%

---

# 設定Campaign Explorer導覽樹狀結構{#configuration}

身為資深使用者，您可以在瀏覽器樹狀結構中新增資料夾並加以自訂。

進一步瞭解Campaign檔案總管和導覽階層 [在本節中](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

導覽清單使用的資料夾型別在遵循語法的XML檔案中進行說明 **xtk：navtree** 綱要。

XML檔案的結構如下：

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

XML檔案包含 **`<navtree>`** 根元素具有 **名稱** 和 **名稱空間** 屬性以指定檔名稱和名稱空間。 檔案識別金鑰的名稱和名稱空間組成。

應用程式的全域指令是在檔案中宣告的，來自 **`<commands>`** 元素。

檔案型別的宣告在檔案中結構化，並包含以下元素： **`<model>`** 和 **`<nodemodel>`**.

## 全域命令 {#global-commands}

全域命令可讓您啟動動作。 此動作可以是輸入表單或SOAP呼叫。

全域命令可從主命令存取 **[!UICONTROL Tools]** 功能表。

指令組態結構如下：

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

全域指令的說明輸入於 **`<command>`** 元素具有以下屬性：

* **名稱**：命令的內部名稱：名稱必須輸入且唯一
* **標籤**：命令的標籤。
* **desc**：說明可從主畫面的狀態列顯示。
* **表單**：要啟動的表單：要輸入的值是輸入表單的識別鍵（例如「cus：recipient」）
* **權利**：允許存取此命令的已命名許可權清單（以逗號分隔）。 可用許可權清單可從 **[!UICONTROL Administration > Access management > Named rights]** 資料夾。
* **提示標籤**：在執行命令前顯示確認方塊。

A **`<command>`** 元素可包含 **`<command>`** 子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子選單。

指令的顯示順序與在XML檔案中宣告的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 識別方式為 **&#39;-&#39;** 包含在命令標籤中的值。

選用的存在 **`<soapcall>`** 標籤及其輸入引數會定義要執行的SOAP方法的呼叫。 如需有關SOAP API的詳細資訊，請參閱 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant).

在初始化時，表單內容可從以下位置更新： **`<enter>`** 標籤之間。 如需有關此標籤的詳細資訊，請參閱有關輸入表單的檔案。

**範例**：

* 宣告全域命令以啟動「xtk：import」表單：

  ```
  <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  鍵盤快速鍵是在&#39;I&#39;字元上宣告的，因為 **&amp;** 在指令標籤中。

* 具有分隔符號的子功能表範例：

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

* SOAP方法的執行：

  ```
  <command name="cmd3" label="Example 3" promptLabel="Do you really want to execute the command?">
    <soapCall name="Execute" service="xtk:sql"/>
  </command>
  ```

## 資料夾類型 {#folder-type}

資料夾型別可讓您授予結構描述資料的存取權。 與資料夾關聯的檢視由清單和輸入表單組成。

資料夾型別組態結構如下：

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

資料夾型別宣告必須輸入在 **`<model>`** 元素。 此要素可讓您定義階層式組織，其顯示方式為 **[!UICONTROL Add new folder]** 功能表。 A **`<model>`** 元素必須包含 **`<nodemodel>`** 元素和其他 **`<model>`** 元素。

此 **名稱** 和 **標籤** 屬性會填入元素的內部名稱，以及 **[!UICONTROL Add new folder]** 功能表。

此 **`<nodemodel>`** 元素包含資料夾型別的說明，其屬性如下：

* **名稱**：內部名稱
* **標籤**：中使用的標籤 **[!UICONTROL Add new folder]** 功能表，並做為插入資料夾時的預設標籤。
* **img**：資料夾插入時的預設影像。
* **hiddenCommand**：要遮罩的命令清單（以逗號分隔）。 可能的值： 「adbnew」、「adbsave」、「adbcancel」和「adbdup」。
* **newFolderShortCuts**：模型上的捷徑清單(**`<nodemodel>`** （以逗號分隔）。
* **插入右側**， **editRight**， **deleteRight**：插入、編輯和刪除資料夾的權利。

此 **`<view>`** 元素之下 **`<nodemodel>`** 元素包含與檢視相關聯的清單組態。 清單的結構描述輸入於 **綱要** 的屬性 **`<view>`** 元素。

若要編輯清單的記錄，會隱含使用與清單結構描述同名的輸入表單。 此 **type** 上的屬性 **`<view>`** 元素會影響表單的顯示。 可能的值包括：

* **listdet**：在清單底部顯示表單。
* **清單**：單獨顯示清單。 透過按兩下或透過選取清單時選單中的「開啟」來啟動表單。
* **表單**：顯示唯讀表單。
* **editForm**：在編輯模式下顯示表單。

>[!NOTE]
>
>輸入輸入表單的名稱可透過輸入 **表單** 中的屬性 **`<view>`** 元素。

清單欄的預設設定是透過 **`<columns>`** 元素。 資料行是在上宣告 **`<node>`** 元素包含 **xpath** 屬性，其結構描述中會參照的欄位作為其值。

**範例**：在「nms：recipient」結構描述上的資料夾型別宣告。

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

對應的資料夾插入功能表：

![](assets/d_ncs_integration_navigation_exemple2.png)

載入清單時可套用篩選和排序：

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

### 捷徑指令 {#shortcut-commands}

捷徑指令可讓您在選取清單時啟動動作。 動作可以是輸入表單或SOAP呼叫。

命令可從以下位置存取： **[!UICONTROL Action]** 清單功能表或相關功能表按鈕的功能表。

指令組態結構如下：

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

命令說明輸入於 **`<command>`** 元素具有以下屬性：

* **名稱**：命令的內部名稱：名稱必須輸入且唯一。
* **標籤**：命令的標籤。
* **desc**：說明可從主畫面的狀態列顯示。
* **表單**：要啟動的表單：要輸入的值是輸入表單的識別鍵（例如「cus：recipient」）。
* **權利**：允許存取此命令的已命名許可權清單（以逗號分隔）。 可用許可權清單可從 **[!UICONTROL Administration > Access management > Named rights]** 資料夾。
* **提示標籤**：在執行命令之前顯示確認方塊
* **單選**：強制單選（預設為多選）。
* **refreshView**：在執行命令後強制重新載入清單。
* **enabledIf**：根據輸入的運算式啟動命令。
* **img**：輸入允許從清單工具列存取命令的影像。

A **`<command>`** 元素可包含 **`<command>`** 子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子選單。

指令的顯示順序與在XML檔案中宣告的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 識別方式為 **&#39;-&#39;** 包含在命令標籤中的值。

選用的存在 **`<soapcall>`** 標籤及其輸入引數會定義要執行的SOAP方法的呼叫。 如需SOAP API的詳細資訊，請參閱 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant).

初始化時，可透過以下方式更新表單內容： **`<enter>`** 標籤之間。 如需此標籤的詳細資訊，請參閱輸入表單檔案。

**範例**：

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

有兩種型別的資料夾管理作業：

1. 資料夾是一個檢視：清單會顯示與結構描述相關的所有記錄，並可能在資料夾屬性中輸入系統篩選。
1. 資料夾已連結：清單中的記錄會在資料夾連結上以隱含的方式篩選。

對於連結的資料夾， **folderLink** 上的屬性 **`<nodemodel>`** 元素必須填入。 此屬性包含在資料架構中設定的資料夾上的連結名稱。

資料結構描述中連結資料夾的宣告範例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

的設定 **`<nodemodel>`** 位於名為「資料夾」的資料夾連結上，如下所示：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
