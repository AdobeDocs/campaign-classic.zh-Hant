---
product: campaign
title: 配置市場活動瀏覽器導航樹
description: 瞭解如何配置市場活動瀏覽器導航樹
exl-id: c7ae7240-0c12-4420-bbb3-4268c9ade3e7
source-git-commit: 40da5774c8a6a228992c4aa400e2d9924215611e
workflow-type: tm+mt
source-wordcount: '1196'
ht-degree: 1%

---

# 配置市場活動瀏覽器導航樹{#configuration}

![](../../assets/v7-only.svg)

作為專家用戶，您可以在瀏覽器樹中添加資料夾並對其進行自定義。

瞭解有關市場活動瀏覽器和導航層次結構的詳細資訊 [此部分](../../platform/using/adobe-campaign-explorer.md#about-navigation-hierarchy)。

導航清單使用的資料夾類型在遵循XML文檔的語法的XML文檔中描述 **xtk：導航樹** 架構。

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

XML文檔包含 **`<navtree>`** 根元素 **名稱** 和 **命名空間** 屬性，以指定文檔名稱和命名空間。 名稱和命名空間構成文檔標識鍵。

應用程式的全局命令在文檔中聲明自 **`<commands>`** 的子菜單。

檔案類型聲明在文檔中具有以下元素： **`<model>`** 和 **`<nodemodel>`**。

## 全局命令 {#global-commands}

全局命令允許您啟動操作。 此操作可以是輸入表單或SOAP調用。

全局命令可從主 **[!UICONTROL Tools]** 的子菜單。

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

全局命令的說明在 **`<command>`** 具有以下屬性的元素：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一
* **標籤**:的子菜單。
* **des**:說明可從主螢幕的狀態欄中看到。
* **表格**:格式：要輸入的值是輸入表單的標識鍵(例如，&quot;cus:recipient&quot;)
* **權利**:允許訪問此命令的命名權限清單（以逗號分隔）。 可以從 **[!UICONTROL Administration > Access management > Named rights]** 的子菜單。
* **提示標籤**:在執行命令之前顯示確認框。

A **`<command>`** 元素 **`<command>`** 子元素。 在這種情況下，父元素允許您顯示由這些子元素組成的子菜單。

命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符允許您在命令之間顯示分隔條。 由 **&#39;-&#39;** 命令標籤中包含的值。

可選存在 **`<soapcall>`** 帶有其輸入參數的標籤定義了要執行的SOAP方法的調用。 有關SOAP API的詳細資訊，請參閱 [市場活動JSAPI文檔](https://experienceleague.adobe.com/developer/campaign-api/api/index.html?lang=zh-Hant)。

可以在從 **`<enter>`** 標籤。 有關此標籤的詳細資訊，請參閱輸入表單的文檔。

**範例**:

* 聲明全局命令以啟動「xtk:import」表單：

   ```
   <command desc="Start the data import wizard" form="xtk:import" label="&amp;Data import..." name="import" rights="import,recipientImport"/>
   ```

   在「I」字元上聲明了鍵盤快捷鍵 **&amp;** 的子菜單。

* 帶分隔符的子菜單示例：

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

資料夾類型允許您訪問架構的資料。 與資料夾關聯的視圖由清單和輸入表單組成。

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

資料夾類型聲明必須在 **`<model>`** 的子菜單。 此元素允許您定義從 **[!UICONTROL Add new folder]** 的子菜單。 A **`<model>`** 元素必須包含 **`<nodemodel>`** 元素 **`<model>`** 元素。

的 **名稱** 和 **標籤** 屬性填充元素的內部名稱和 **[!UICONTROL Add new folder]** 的子菜單。

的 **`<nodemodel>`** 元素包含具有以下屬性的資料夾類型的說明：

* **名稱**:內部名稱
* **標籤**:標籤 **[!UICONTROL Add new folder]** 的子菜單。
* **img**:資料夾插入時的預設影像。
* **隱藏命令**:要屏蔽的命令清單（用逗號分隔）。 可能的值：&quot;adbnew&quot;、&quot;adbsave&quot;、&quot;adbcancel&quot;和&quot;adbdup&quot;。
* **新資料夾短切**:模型的快捷方式清單(**`<nodemodel>`** 以逗號分隔)。
* **插入右**。 **編輯右**。 **刪除右**:用於插入、編輯和刪除資料夾的權限。

的 **`<view>`** 元素 **`<nodemodel>`** 元素包含與視圖關聯的清單的配置。 清單的架構在 **架構** 屬性 **`<view>`** 的子菜單。

要編輯清單的記錄，將隱式使用與清單架構同名的輸入表單。 的 **類型** 屬性 **`<view>`** 元素會影響窗體的顯示。 可能的值為：

* **清單**:在清單底部顯示窗體。
* **清單**:單獨顯示清單。 通過按兩下或通過選擇清單時菜單中的「開啟」啟動窗體。
* **表格**:顯示只讀窗體。
* **編輯窗體**:在編輯模式下顯示窗體。

>[!NOTE]
>
>輸入表單的名稱可通過輸入 **表格** 屬性 **`<view>`** 的子菜單。

清單列的預設配置通過 **`<columns>`** 的子菜單。 列在 **`<node>`** 包含元素 **xpath** 屬性，其模式中要引用的欄位作為其值。

**示例**:「nms:recipient」架構上資料夾類型的聲明。

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

在載入清單時，可以應用篩選和排序：

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

快捷方式命令允許您在選擇清單時啟動操作。 操作可以是輸入表單或SOAP調用。

可從 **[!UICONTROL Action]** 按鈕。

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

命令的說明在 **`<command>`** 具有以下屬性的元素：

* **名稱**:命令的內部名稱：名稱必須輸入且唯一。
* **標籤**:的子菜單。
* **des**:說明可從主螢幕的狀態欄中看到。
* **表格**:格式：要輸入的值是輸入表單的標識鍵(例如，&quot;cus:recipient&quot;)。
* **權利**:允許訪問此命令的命名權限清單（以逗號分隔）。 可以從 **[!UICONTROL Administration > Access management > Named rights]** 的子菜單。
* **提示標籤**:在執行命令之前顯示確認框
* **單聲道選擇**:強制單選（預設為多選）。
* **刷新視圖**:在執行命令後強制重裝清單。
* **enabledIf**:根據輸入的表達式激活該命令。
* **img**:輸入允許從清單工具欄訪問命令的影像。

A **`<command>`** 元素 **`<command>`** 子元素。 在這種情況下，父元素允許您顯示由這些子元素組成的子菜單。

命令的顯示順序與在XML文檔中聲明的順序相同。

命令分隔符允許您在命令之間顯示分隔條。 由 **&#39;-&#39;** 命令標籤中包含的值。

可選存在 **`<soapcall>`** 帶有其輸入參數的標籤定義了要執行的SOAP方法的調用。 有關SOAP API的詳細資訊，請參閱 [市場活動JSAPI文檔](https://experienceleague.adobe.com/developer/campaign-api/api/index.html)。

在初始化時，可以通過 **`<enter>`** 標籤。 有關此標籤的詳細資訊，請參閱輸入表單文檔。

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

### 連結資料夾 {#linked-folder}

資料夾管理操作有兩種類型：

1. 資料夾是視圖：該清單顯示與方案關聯的所有記錄，並且在資料夾屬性中輸入了系統篩選的可能性。
1. 資料夾已連結：清單中的記錄在資料夾連結上隱式過濾。

對於連結的資料夾， **資料夾連結** 屬性 **`<nodemodel>`** 必須填充元素。 此屬性包含在資料架構中配置的資料夾中的連結的名稱。

資料方案中連結資料夾聲明示例：

```
<element default="DefaultFolder('nmsFolder', [@_folder-id])" label="Folder" name="folder" revDesc="Recipients in the folder" revIntegrity="define" revLabel="Recipients" target="xtk:folder" type="link"/>
```

配置 **`<nodemodel>`** 在名為&quot;folder&quot;的資料夾的連結上，如下所示：

```
<nodeModel deleteRight="folderDelete" editRight="folderEdit" folderLink="folder"
  img="nms:folder.png" insertRight="folderInsert" label="Recipients" name="nmsFolder">
...
</nodeModel>
```
