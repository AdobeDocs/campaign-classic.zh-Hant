---
product: campaign
title: 設定Campaign Explorer導覽樹狀結構
feature: Application Settings
description: 瞭解如何設定Campaign Explorer導覽樹狀結構
role: Data Engineer, Developer
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '1186'
ht-degree: 0%

---

# 設定Campaign Explorer導覽樹狀結構{#configuration}

身為資深使用者，您可以在瀏覽器樹狀結構中新增資料夾並加以自訂。

在本節](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)中進一步瞭解Campaign總管和導覽階層[。

導覽清單使用的資料夾型別在遵循&#x200B;**xtk：navtree**&#x200B;結構描述語法的XML檔案中描述。

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

XML檔案包含具有&#x200B;**名稱**&#x200B;和&#x200B;**名稱空間**&#x200B;屬性的&#x200B;**`<navtree>`**&#x200B;根專案，以指定檔名稱和名稱空間。 檔案識別金鑰的名稱和名稱空間組成。

應用程式的全域命令是從&#x200B;**`<commands>`**&#x200B;元素的檔案中宣告。

檔案型別的宣告在檔案中結構化，包含下列元素： **`<model>`**&#x200B;和&#x200B;**`<nodemodel>`**。

## 全域命令 {#global-commands}

全域命令可讓您啟動動作。 此動作可以是輸入表單或SOAP呼叫。

可從主&#x200B;**[!UICONTROL Tools]**&#x200B;功能表存取全域命令。

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

在&#x200B;**`<command>`**&#x200B;元素中輸入具有下列屬性的全域命令描述：

* **名稱**：命令的內部名稱：名稱必須輸入且是唯一的
* **label**：命令的標籤。
* **desc**：可從主畫面的狀態列看到描述。
* **表單**：要啟動的表單：要輸入的值是輸入表單的識別碼（例如「cus：recipient」）
* **rights**：允許存取此命令的已命名許可權清單（以逗號分隔）。 可從&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;資料夾存取可用許可權清單。
* **promptLabel**：在執行命令之前顯示確認方塊。

**`<command>`**&#x200B;專案可以包含&#x200B;**`<command>`**&#x200B;個子專案。 在這種情況下，父元素可讓您顯示由這些子元素組成的子選單。

指令的顯示順序與在XML檔案中宣告的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 它由包含在命令標籤中的&#x200B;**&#39;-&#39;**&#x200B;值識別。

**`<soapcall>`**&#x200B;標籤及其輸入引數的選擇性存在性定義要執行的SOAP方法呼叫。 如需SOAP API的詳細資訊，請參閱[Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。

從&#x200B;**`<enter>`**&#x200B;標籤初始化時可以更新表單內容。 如需有關此標籤的詳細資訊，請參閱有關輸入表單的檔案。

**範例**：

* 宣告全域命令以啟動「xtk：import」表單：

  ```
  <command desc="Start the data import assistant" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
  ```

  命令標籤中出現&#x200B;**&amp;**，因此在&#39;I&#39;字元上宣告鍵盤快速鍵。

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

資料夾型別宣告必須在&#x200B;**`<model>`**&#x200B;專案下輸入。 此元素可讓您定義可從&#x200B;**[!UICONTROL Add new folder]**&#x200B;功能表看到的階層式組織。 **`<model>`**&#x200B;元素必須包含&#x200B;**`<nodemodel>`**&#x200B;元素和其他&#x200B;**`<model>`**&#x200B;元素。

**name**&#x200B;和&#x200B;**label**&#x200B;屬性會填入元素的內部名稱和&#x200B;**[!UICONTROL Add new folder]**&#x200B;功能表中顯示的標籤。

**`<nodemodel>`**&#x200B;元素包含具有下列屬性的資料夾型別描述：

* **名稱**：內部名稱
* **label**： **[!UICONTROL Add new folder]**&#x200B;功能表中使用的標籤，並在插入資料夾時作為預設標籤。
* **img**：資料夾插入時的預設影像。
* **hiddenCommands**：要遮罩的命令清單（以逗號分隔）。 可能的值： 「adbnew」、「adbsave」、「adbcancel」和「adbdup」。
* **newFolderShortCuts**：建立資料夾時模型上的捷徑清單（**`<nodemodel>`**，以逗號分隔）。
* **insertRight**，**editRight**，**deleteRight**：插入、編輯和刪除資料夾的許可權。

**`<nodemodel>`**&#x200B;專案下的&#x200B;**`<view>`**&#x200B;專案包含與檢視相關聯的清單組態。 清單的結構描述是在&#x200B;**`<view>`**&#x200B;專案的&#x200B;**結構描述**&#x200B;屬性中輸入的。

若要編輯清單的記錄，會隱含使用與清單結構描述同名的輸入表單。 **`<view>`**&#x200B;專案上的&#x200B;**type**&#x200B;屬性會影響表單的顯示。 可能的值包括：

* **listdet**：在清單底部顯示表單。
* **清單**：單獨顯示清單。 透過按兩下或透過選取清單時選單中的「開啟」來啟動表單。
* **表單**：顯示唯讀表單。
* **editForm**：在編輯模式下顯示表單。

>[!NOTE]
>
>在&#x200B;**`<view>`**&#x200B;元素中輸入&#x200B;**form**&#x200B;屬性，可多載輸入表單的名稱。

清單欄的預設設定是透過&#x200B;**`<columns>`**&#x200B;專案輸入的。 在包含&#x200B;**xpath**&#x200B;屬性的&#x200B;**`<node>`**&#x200B;元素上宣告資料行，並在其結構描述中參考該欄位的值。

**範例**： &quot;nms：recipient&quot;結構描述上的資料夾型別宣告。

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

可從清單的&#x200B;**[!UICONTROL Action]**&#x200B;功能表或相關的功能表按鈕存取命令。

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

在具有下列屬性的&#x200B;**`<command>`**&#x200B;元素上輸入命令的描述：

* **name**：命令的內部名稱：名稱必須輸入且是唯一的。
* **label**：命令的標籤。
* **desc**：可從主畫面的狀態列看到描述。
* **表單**：要啟動的表單：要輸入的值是輸入表單的識別碼（例如「cus：recipient」）。
* **rights**：允許存取此命令的已命名許可權清單（以逗號分隔）。 可從&#x200B;**[!UICONTROL Administration > Access management > Named rights]**&#x200B;資料夾存取可用許可權清單。
* **promptLabel**：在執行命令之前顯示確認方塊
* **monoSelection**：強制單選（預設為多重選取）。
* **refreshView**：在執行命令後強制重新載入清單。
* **enabledIf**：根據輸入的運算式啟動命令。
* **img**：輸入允許從清單工具列存取命令的影像。

**`<command>`**&#x200B;專案可以包含&#x200B;**`<command>`**&#x200B;個子專案。 在這種情況下，父元素可讓您顯示由這些子元素組成的子選單。

指令的顯示順序與在XML檔案中宣告的順序相同。

命令分隔符號可讓您在命令之間顯示分隔列。 它由包含在命令標籤中的&#x200B;**&#39;-&#39;**&#x200B;值識別。

**`<soapcall>`**&#x200B;標籤及其輸入引數的選擇性存在性定義要執行的SOAP方法呼叫。 如需SOAP API的詳細資訊，請參閱[Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。

初始化時可透過&#x200B;**`<enter>`**&#x200B;標籤更新表單內容。 如需此標籤的詳細資訊，請參閱輸入表單檔案。

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

對於連結的資料夾，**`<nodemodel>`**&#x200B;專案上的&#x200B;**folderLink**&#x200B;屬性必須填入。 此屬性包含在資料架構中設定的資料夾上的連結名稱。

資料結構描述中連結資料夾的宣告範例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

名為「資料夾」的資料夾連結上&#x200B;**`<nodemodel>`**&#x200B;的設定如下：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
