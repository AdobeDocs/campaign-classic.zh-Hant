---
product: campaign
title: 設定Campaign Explorer導覽樹
description: 了解如何設定Campaign Explorer導覽樹
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 1%

---

# 設定Campaign Explorer導覽樹{#configuration}

作為專家用戶，您可以在資源管理器樹中添加資料夾並對其進行自定義。

進一步了解Campaign瀏覽器和導覽階層 [在本節](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy).

導航清單使用的資料夾類型在遵循以下文法的XML文檔中進行描述 **xtk:navtree** 綱要。

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

XML文檔包含 **`<navtree>`** 根元素與 **名稱** 和 **命名空間** 用於指定文檔名稱和命名空間的屬性。 名稱和命名空間構成文檔標識密鑰。

應用程式的全局命令在文檔中聲明，來自 **`<commands>`** 元素。

檔案類型的聲明在文檔中具有以下元素： **`<model>`** 和 **`<nodemodel>`**.

## 全局命令 {#global-commands}

全域命令可讓您啟動動作。 此動作可以是輸入表單或SOAP呼叫。

全局命令可從主 **[!UICONTROL Tools]** 功能表。

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

全局命令的說明在 **`<command>`** 元素，具有下列屬性：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一
* **標籤**:命令的標籤。
* **desc**:從主螢幕的狀態欄中可見的說明。
* **表單**:要啟動的表單：要輸入的值是輸入表單的標識鍵(例如&quot;cus:recipient&quot;)
* **權利**:允許訪問此命令的命名權限清單（以逗號分隔）。 可從 **[!UICONTROL Administration > Access management > Named rights]** 檔案夾。
* **promptLabel**:在執行命令之前顯示一個確認框。

A **`<command>`** 元素可包含 **`<command>`** 子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子菜單。

命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符允許您顯示命令之間的分隔條。 會由 **&#39;-&#39;** 命令標籤中包含的值。

可選的 **`<soapcall>`** 標籤及其輸入參數定義要執行的SOAP方法的呼叫。 有關SOAP API的詳細資訊，請參閱 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant).

從 **`<enter>`** 標籤。 如需此標籤的詳細資訊，請參閱輸入表單的相關檔案。

**範例**:

* 發起「xtk:import」表單的全域命令聲明：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在「I」字元上，出現 **&amp;** 在命令標籤中。

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

必須在 **`<model>`** 元素。 此元素可讓您定義可從 **[!UICONTROL Add new folder]** 功能表。 A **`<model>`** 元素必須包含 **`<nodemodel>`** 元素和其他 **`<model>`** 元素。

此 **名稱** 和 **標籤** 屬性會填入元素的內部名稱，以及 **[!UICONTROL Add new folder]** 功能表。

此 **`<nodemodel>`** 元素包含資料夾類型的說明，其屬性如下：

* **名稱**:內部名稱
* **標籤**:標籤 **[!UICONTROL Add new folder]** 功能表和預設標籤。
* **img**:插入資料夾時的預設影像。
* **hiddenCommands**:要遮罩的命令清單（以逗號分隔）。 可能的值：&quot;adbnew&quot;、&quot;adbsave&quot;、&quot;adbcancel&quot;和&quot;adbdup&quot;。
* **newFolderShortCuts**:模型快捷方式清單(**`<nodemodel>`** 以逗號分隔)。
* **insertRight**, **editRight**, **deleteRight**:插入、編輯和刪除資料夾的權限。

此 **`<view>`** 元素下方 **`<nodemodel>`** 元素包含與檢視相關聯的清單的設定。 清單的架構會在 **綱要** 屬性 **`<view>`** 元素。

要編輯清單的記錄，將隱式使用與清單架構同名的輸入表單。 此 **type** 屬性 **`<view>`** 元素會影響表單的顯示。 可能的值包括：

* **listdet**:在清單底部顯示表單。
* **清單**:單獨顯示清單。 表單會以連按兩下或透過選取清單功能表中的「開啟」來啟動。
* **表單**:顯示只讀表單。
* **editForm**:以編輯模式顯示表單。

>[!NOTE]
>
>輸入表單的名稱可以多載，方法是輸入 **表單** 屬性 **`<view>`** 元素。

清單欄的預設設定會透過 **`<columns>`** 元素。 欄會在 **`<node>`** 包含 **xpath** 屬性，其結構中要參考的欄位為其值。

**範例**:「nms:recipient」架構上資料夾類型的聲明。

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

### 快捷方式命令 {#shortcut-commands}

快速鍵命令可讓您在選取清單時啟動動作。 動作可以是輸入表單或SOAP呼叫。

可從 **[!UICONTROL Action]** 清單的菜單或相關菜單按鈕。

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

在 **`<command>`** 元素，具有下列屬性：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一。
* **標籤**:命令的標籤。
* **desc**:從主螢幕的狀態欄中可見的說明。
* **表單**:要啟動的表單：要輸入的值是輸入表單的標識鍵(例如&quot;cus:recipient&quot;)。
* **權利**:允許訪問此命令的命名權限清單（以逗號分隔）。 可從 **[!UICONTROL Administration > Access management > Named rights]** 檔案夾。
* **promptLabel**:在執行命令之前顯示確認框
* **monoSelection**:強制單選（預設為多個選取）。
* **refreshView**:執行命令後強制重新載入清單。
* **enabledIf**:根據輸入的表達式激活該命令。
* **img**:輸入允許從清單工具欄訪問命令的影像。

A **`<command>`** 元素可包含 **`<command>`** 子元素。 在這種情況下，父元素可讓您顯示由這些子元素組成的子菜單。

命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符允許您顯示命令之間的分隔條。 會由 **&#39;-&#39;** 命令標籤中包含的值。

可選的 **`<soapcall>`** 標籤及其輸入參數定義要執行的SOAP方法的呼叫。 有關SOAP API的詳細資訊，請參閱 [Campaign JSAPI檔案](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant).

可透過 **`<enter>`** 標籤。 如需此標籤的詳細資訊，請參閱輸入表單檔案。

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

1. 資料夾為檢視：該清單顯示與架構關聯的所有記錄，並且有可能在資料夾屬性中輸入系統篩選。
1. 資料夾已連結：清單中的記錄會以隱含方式篩選在資料夾連結上。

對於連結的資料夾， **folderLink** 屬性 **`<nodemodel>`** 元素。 此屬性包含資料架構中配置的資料夾上的連結名稱。

資料結構中連結資料夾的聲明範例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

的設定 **`<nodemodel>`** 在名為「folder」的資料夾的連結上，如下所示：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
