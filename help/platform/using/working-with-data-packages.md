---
product: campaign
title: 使用資料套件
description: 使用資料套件
feature: Data Management, Package Export/Import
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
audience: platform
content-type: reference
topic-tags: administration-basics
exl-id: d3369b63-a29b-43b7-b2ad-d36d4f46c82e
source-git-commit: c262c27e75869ae2e4bd45642f5a22adec4a5f1e
workflow-type: tm+mt
source-wordcount: '2474'
ht-degree: 2%

---

# 使用資料套件{#working-with-data-packages}



## 關於資料套件 {#about-data-packages}

使用 Adobe Campaign，您可以透過資料包系統匯出或匯入平台配置和資料。套件可以包含不同型別的設定、元素、已篩選或不篩選。

資料包可以 XML 格式檔案的形式顯示 Adobe Campaign 資料庫的實體。資料包中包含的每個實體都會以其所有資料表示。

**資料套件**&#x200B;的原理是匯出資料組態，並將其整合到另一個Adobe Campaign系統中。 瞭解如何在此[區段](#data-package-best-practices)中維持一組一致的資料封裝。

### 封裝型別 {#types-of-packages}

可匯出的套件型別有三種：使用者套件、平台套件和管理套件。

* **使用者套件**：它可讓您選取要匯出的實體清單。 這種型別的套件管理相依性並驗證錯誤。
* **平台套件**：它包含所有新增的技術資源（非標準）：結構描述、JavaScript程式碼等。

  ![](assets/ncs_datapackage_package_platform.png)

* **管理套件**：包含所有新增的範本與企業物件（非標準）：範本、物件庫等。

  ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>**平台**&#x200B;和&#x200B;**管理員**&#x200B;型別包含要匯出的預先定義實體清單。 每個實體都會連結至篩選條件，可讓您移除已建立封裝的現成資源。

## 資料結構 {#data-structure}

資料封裝的描述是符合&#x200B;**xrk：navtree**&#x200B;資料結構描述語法的結構化XML檔案。

資料封裝範例：

```
<package>
  <entities schema="nms:recipient">
    <recipient email="john.smith@adobe.com" lastName="Smith" firstName="John">      
      <folder _operation="none" name="nmsRootFolder"/>      
      <company _operation="none" name="Adobe"/>
    </recipient>
  </entities>
  <entities schema="sfa:company">
    <company name="Adobe">
      location city="London" zipCode="W11 2BQ"/>
    </company>
  </entities>
</package>
```

XML檔案必須以&#x200B;**`<package>`**&#x200B;專案開頭和結尾。 後續的任何&#x200B;**`<entities>`**&#x200B;元素會依檔案型別分配資料。

**`<entities>`**&#x200B;元素包含封裝的資料，其格式為在&#x200B;**結構描述**&#x200B;屬性中輸入的資料結構描述。

套件中的資料不得包含基底之間不相容的內部金鑰，例如自動產生的金鑰（**autopk**&#x200B;選項）。

在我們的範例中，「資料夾」和「公司」連結上的聯結已被目的地表格上所謂的「高階」索引鍵取代：

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

值為「none」的&#x200B;**`operation`**&#x200B;屬性會定義調解連結。

您可以從任何文字編輯器手動建構資料套件。 只要確保XML檔案的結構符合「xtk：navtree」資料結構描述即可。 Adobe Campaign主控台有資料包匯出和匯入模組。

## 匯出套件 {#exporting-packages}

### 關於封裝匯出 {#about-package-export}

套件可以三種不同的方式匯出：

* **[!UICONTROL Package Export Assistant]**&#x200B;可讓您匯出單一封裝中的一組物件。 如需詳細資訊，請參閱[匯出封裝中的一組物件](#exporting-a-set-of-objects-in-a-package)
* 您可以用滑鼠右鍵按一下單一物件&#x200B;**並選取&#x200B;**[!UICONTROL Actions > Export in a package]**，直接將其匯出到封裝中。**
* **封裝定義**&#x200B;可讓您建立封裝結構，在其中新增稍後將在封裝中匯出的物件。 如需詳細資訊，請參閱[管理封裝定義](#managing-package-definitions)

套件匯出後，您就可以將套件和所有新增的實體匯入另一個Campaign執行個體。

### 匯出封裝中的一組物件 {#exporting-a-set-of-objects-in-a-package}

封裝匯出助理可以透過Adobe Campaign使用者端主控台的&#x200B;**[!UICONTROL Tools > Advanced > Export package...]**&#x200B;功能表存取。

![](assets/ncs_datapackage_typepackage.png)

對於三種型別的套裝程式，助理提供下列步驟：

1. 按檔案型別列出要匯出的實體：

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >如果您匯出&#x200B;**[!UICONTROL Offer category]**、**[!UICONTROL Offer environment]**、**[!UICONTROL Program]**&#x200B;或&#x200B;**[!UICONTROL Plan]**&#x200B;型別資料夾，請勿選取&#x200B;**xtk：folder**，因為您可能會遺失部分資料。 選取與資料夾對應的實體： **nms：offerCategory** （選件類別）、**nms：offerEnv** （選件環境）、**nms：program** （方案）和&#x200B;**nms：plan** （計畫）。

   清單管理可讓您新增或刪除要從設定匯出的實體。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;以選取新實體。

   **[!UICONTROL Detail]**&#x200B;按鈕會編輯選取的設定。

   >[!NOTE]
   >
   >相依性機制會控制實體匯出順序。 如需詳細資訊，請參閱[管理相依性](#managing-dependencies)。

1. 實體設定畫面會針對要擷取的檔案型別定義篩選查詢。

   您必須設定資料擷取的篩選子句。

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >查詢編輯器出現在[此區段](../../platform/using/about-queries-in-campaign.md)中。

1. 按一下&#x200B;**[!UICONTROL Next]**&#x200B;並選取排序資料行，以便在擷取期間排序資料：

   ![](assets/ncs_datapackage_export5.png)

1. 在執行匯出之前，先預覽要擷取的資料。

   ![](assets/ncs_datapackage_export6.png)

1. 封裝匯出助理的最後一頁可讓您開始匯出。 資料將會儲存在&#x200B;**[!UICONTROL File]**&#x200B;欄位中指定的檔案中。

   ![](assets/ncs_datapackage_export7.png)

### 管理相依性 {#managing-dependencies}

匯出機制可讓Adobe Campaign追蹤各種匯出元素之間的連結。

此機制由兩個規則定義：

* 連結到具有&#x200B;**擁有**&#x200B;或&#x200B;**owncopy**&#x200B;型別完整性的連結的物件，會匯出到與匯出物件相同的封裝。
* 連結至連結具有&#x200B;**neutral**&#x200B;或&#x200B;**define**&#x200B;型別完整性（定義的連結）的物件必須個別匯出。

>[!NOTE]
>
>連結到結構描述元素的完整性型別定義於[此區段](../../configuration/using/database-mapping.md#links--relation-between-tables)。

#### 匯出行銷活動 {#exporting-a-campaign}

以下是如何匯出行銷活動的範例。 要匯出的行銷活動包含「MyWorkflow」資料夾（節點：管理/生產/技術工作流程/行銷活動流程/MyWorkflow）中的任務（標籤：「MyTask」）和工作流程（標籤：「CampaignWorkflow」）。

任務和工作流程會匯出到與行銷活動相同的套件中，因為相符的結構描述是由具有「自己的」型別完整性的連結所連結。

封裝內容：

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="7.1" img=""
label="" name="" namespace="" vendor="">
 <desc></desc>
 <version buildDate="2013-01-09 10:30:18.954Z"/>
 <entities schema="nms:operation">
  <operation duration="432000" end="2013-01-14" internalName="OP1" label="MyCampaign"
  modelName="opEmpty" start="2013-01-09">
   <controlGroup>
    <where filteringSchema=""/>
   </controlGroup>
   <seedList>
    <where filteringSchema="nms:seedMember"></where>
    <seedMember internalName="SDM1"></seedMember>
   </seedList>
   <parameter useAsset="1" useBudget="1" useControlGroup="1" useDeliveryOutline="1"
   useDocument="1" useFCPValidation="0" useSeedMember="1" useTask="1"
   useValidation="1" useWorkflow="1"></parameter>
   <fcpSeed>
    <where filteringSchema="nms:seedMember"></where>
   </fcpSeed>
   <owner _operation="none" name="admin" type="0"/>
   <program _operation="none" name="nmsOperations"/>
   <task end="2013-01-17 10:07:51.000Z" label="MyTask" name="TSK2" start="2013-01-16 10:07:51.000Z"
   status="1">
    <owner _operation="none" name="admin" type="0"/>
    <operation _operation="none" internalName="OP1"/>
    <folder _operation="none" name="nmsTask"/>
   </task>
   <workflow internalName="WKF12" label="CampaignWorkflow" modelName="newOpEmpty"
   order="8982" scenario-cs="Notification of the workflow supervisor (notifySupervisor)"
   schema="nms:recipient">
    <scenario internalName="notifySupervisor"/>
    <desc></desc>
    <folder _operation="none" name="Folder4"/>
    <operation _operation="none" internalName="OP1"/>
   </workflow>
  </operation>
 </entities>
</package>   
```

在具有&#x200B;**@pkgAdmin和**&#x200B;屬性的結構描述中定義套裝型別@pkgPlatform附屬關係。 這兩個屬性都會接收定義套裝軟體附屬關係條件的XTK運算式。

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

最後，**@pkgStatus**&#x200B;屬性可讓您定義這些元素或屬性的匯出規則。 根據屬性的值，可在匯出的封裝中找到元素或屬性。 此屬性的三個可能值包括：

* **從不**：不匯出欄位/連結
* **一律**：強制匯出此欄位
* **preCreate**：授權建立連結的實體

>[!NOTE]
>
>**preCreate**&#x200B;值僅允許用於連結型別事件。 它授權您建立或指向尚未載入到匯出封裝中的實體。

## 管理封裝定義 {#managing-package-definitions}

封裝定義可讓您建立封裝結構，在其中新增稍後將在單一封裝中匯出的實體。 然後，您就可以將此套件和所有新增的實體匯入另一個Campaign執行個體。

**相關主題：**

* [建立套件定義](#creating-a-package-definition)
* [將實體新增至封裝定義](#adding-entities-to-a-package-definition)
* [設定封裝定義產生](#configuring-package-definitions-generation)
* [從封裝定義匯出封裝](#exporting-packages-from-a-package-definition)

### 建立套件定義 {#creating-a-package-definition}

可從&#x200B;**[!UICONTROL Administration > Configuration > Package management > Package definitions]**&#x200B;功能表存取封裝定義。

若要建立封裝定義，請按一下&#x200B;**[!UICONTROL New]**&#x200B;按鈕，然後填寫封裝定義的一般資訊。

![](assets/packagedefinition_create.png)

然後，您可以將實體加入封裝定義中，並將其匯出至XML檔案封裝。

**相關主題：**

* [將實體新增至封裝定義](#adding-entities-to-a-package-definition)
* [設定封裝定義產生](#configuring-package-definitions-generation)
* [從封裝定義匯出封裝](#exporting-packages-from-a-package-definition)

### 將實體新增至封裝定義 {#adding-entities-to-a-package-definition}

在&#x200B;**[!UICONTROL Content]**&#x200B;索引標籤中，按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以選取要與封裝一起匯出的實體。 選取實體時的最佳實務會顯示在[此區段](#exporting-a-set-of-objects-in-a-package)區段中。

![](assets/packagedefinition_addentities.png)

實體可以直接從其在執行個體中的位置新增到套件定義中。 要執行此操作，請遵循下列步驟：

1. 用滑鼠右鍵按一下所需的實體，然後選取&#x200B;**[!UICONTROL Actions > Export in a package]**。

   ![](assets/packagedefinition_singleentity.png)

1. 選取&#x200B;**[!UICONTROL Add to a package definition]**，然後選取要新增實體的封裝定義。

   ![](assets/packagedefinition_packageselection.png)

1. 實體已新增至封裝定義，將與封裝一起匯出（請參閱[此區段](#exporting-packages-from-a-package-definition)）。

   ![](assets/packagedefinition_entityadded.png)

### 設定封裝定義產生 {#configuring-package-definitions-generation}

封裝產生可從封裝定義&#x200B;**[!UICONTROL Content]**&#x200B;標籤進行設定。 若要這麼做，請按一下&#x200B;**[!UICONTROL Generation parameters]**&#x200B;連結。

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**：包含封裝定義中目前使用的定義。
* **[!UICONTROL Include an installation script]**：可讓您新增javascript指令碼，以在套件匯入時執行。 選取後，**[!UICONTROL Script]**&#x200B;索引標籤會新增到封裝定義畫面中。
* **[!UICONTROL Include default values]**：將所有實體屬性的值新增至封裝。

  為了避免冗長的匯出作業，預設不會選取此選項。 這表示具有預設值（「空字串」、「0」和「false」，如果未在結構描述中另外定義）的實體屬性將不會新增到封裝中，因此將不會匯出。

  >[!CAUTION]
  >
  >取消選取此選項會導致本機版本與匯入版本的合併。
  >
  >如果匯入封裝的執行個體包含與封裝相同的實體（例如具有相同的外部ID），則其屬性不會更新。 如果前一個執行處理的屬性具有預設值，則可能會發生這種情況，因為它們未包含在封裝中。
  >
  >在這種情況下，選取&#x200B;**[!UICONTROL Include default values]**&#x200B;選項會防止版本合併，因為先前執行個體中的所有屬性都會隨套件匯出。

### 從封裝定義匯出封裝 {#exporting-packages-from-a-package-definition}

若要從封裝定義匯出封裝，請遵循下列步驟：

1. 選取要匯出的封裝定義，然後按一下&#x200B;**[!UICONTROL Actions]**&#x200B;按鈕並選取&#x200B;**[!UICONTROL Export the package]**。
1. 依預設，會選取與匯出封裝相對應的XML檔案。 它會根據套件定義名稱空間和名稱來命名。
1. 定義封裝名稱和位置後，按一下&#x200B;**[!UICONTROL Start]**&#x200B;按鈕以啟動匯出。

   ![](assets/packagedefinition_packageexport.png)

## 匯入套件 {#importing-packages}

套件匯入助理可以透過Adobe Campaign使用者端主控台的主功能表&#x200B;**[!UICONTROL Tools > Advanced > Import package]**&#x200B;存取。

您可以根據授權條款，從先前執行的匯出匯入套件，例如從其他Adobe Campaign執行個體或[內建套件](../../installation/using/installing-campaign-standard-packages.md)。

![](assets/ncs_datapackage_import.png)

### 從檔案安裝套件 {#installing-a-package-from-a-file}

若要匯入現有的資料套件，請選取XML檔案並按一下&#x200B;**[!UICONTROL Open]**。

![](assets/ncs_datapackage_import_1.png)

然後，要匯入的封裝內容會顯示在編輯器的中間區段中。

按一下&#x200B;**[!UICONTROL Next]**&#x200B;和&#x200B;**[!UICONTROL Start]**&#x200B;以啟動匯入。

![](assets/ncs_datapackage_import_2.png)

### 安裝內建套件 {#installing-a-standard-package}

標準套件是內建套件，在設定Adobe Campaign時安裝。 如果您取得新選項或附加元件，或升級至新選件，則根據您的許可權和部署模式，可以匯入新的標準套件。

請參閱您的授權合約，以檢查您可以安裝哪些套件。

如需內建套件的詳細資訊，請參閱[此頁面](../../installation/using/installing-campaign-standard-packages.md)。

## 資料套件最佳實務 {#data-package-best-practices}

本節說明如何在專案的整個生命週期中，以一致的方式組織資料套件。

套件可以包含不同型別的設定和元素，無論是否經過篩選。 如果您遺漏了某些元素或未以正確順序匯入元素/套件，平台設定可能會中斷。

此外，如果同一個平台上有多名人員同時使用許多不同的功能，封裝規格資料夾可能會很快變得複雜。

雖然並非強制性，本節提供的解決方案可協助組織及使用Adobe Campaign中的套件以用於大型專案。

主要限制如下：
* 組織套件並追蹤變更內容及變更時間
* 如果更新設定，將破壞未直接連結到更新的專案的風險降至最低

>[!NOTE]
>
>如需設定工作流程以自動匯出套件的詳細資訊，請參閱[此頁面](https://helpx.adobe.com/campaign/kb/export-packages-automatically.html)。

### 建議 {#data-package-recommendations}

一律匯入相同版本的平台。 您必須檢查是否要在具有相同組建的兩個執行個體之間部署套件。 切勿強制匯入，並一律先更新平台（如果組建不同）。

>[!IMPORTANT]
>
>Adobe不支援在不同版本之間匯入。
<!--This is not allowed. Importing from 6.02 to 6.1, for example, is prohibited. If you do so, R&D won’t be able to help you resolve any issues you encounter.-->

請留意結構描述和資料庫結構。 匯入含有結構描述的封裝後，必須產生結構描述。

### 解決方案 {#data-package-solution}

#### 封裝型別 {#package-types}

從定義不同型別的封裝開始。 系統只會使用四種型別：

**個實體**
* Adobe Campaign中的所有「xtk」和「nms」特定元素，例如結構描述、表單、資料夾、傳遞範本等，
* 您可以將實體同時視為「管理員」和「平台」元素。
* 在Campaign執行個體上傳時，封裝中不應包含多個實體。

<!--Nothing “works” alone. An entity package does not have a specific role or objective.-->

如果您需要在新執行個體上部署設定，可以匯入所有實體套件。

**功能**

此型別的封裝：
* 回答使用者端需求/規格。
* 包含一或多個功能。
* 應該包含所有相依性，才能在不使用任何其他封裝的情況下執行功能。

**行銷活動**

此封裝不是強制性的。 有時候，為所有行銷活動建立特定型別會很有用，即使行銷活動可視為一項功能。

**更新**

設定之後，功能就可以匯出至另一個環境。 例如，套件可從開發環境匯出至測試環境。 在此測試中，會顯示缺陷。 首先，它需要在開發環境中修正。 接著，應該將修補程式套用至測試平台。

第一個解決方案是再次匯出整個特徵。 但是，為避免任何風險（更新不需要的元素），僅包含更正的套件比較安全。

這就是我們建議建立「更新」封裝的原因，它只包含特徵的一個圖元型別。

更新不僅可以是修正，也可以是實體/功能/行銷活動封裝的新元素。 若要避免部署整個套件，您可以匯出更新套件。

### 命名慣例 {#data-package-naming}

現在已定義型別，我們應該指定命名慣例。 Adobe Campaign不允許根據套件規格建立子資料夾，這表示數字是保持井然有序的最佳解決方案。 數字前置碼封裝名稱。 您可以使用以下慣例：

* 實體：從1到99
* 功能：從100到199
* 促銷活動：從200到299
* 更新：從5000到5999

### 套件 {#data-packages}

>[!NOTE]
>
>最好設定規則以定義正確數量的套件。

#### 實體套件順序 {#entity-packages-order}

為協助匯入，實體套件應依匯入時的順序排序。 例如：
* 001 — 結構描述
* 002 — 表單
* 003 — 影像
* 等等。

>[!NOTE]
>
>Forms只應在結構描述更新後匯入。

#### 封裝200 {#package-200}

套件編號「200」不應用於特定行銷活動：此編號將用於更新與所有行銷活動有關的專案。

#### 更新封裝 {#update-package}

最後一點與更新封裝編號有關。 它是以「5」為前置詞的套件編號（實體、功能或促銷活動）。 例如：
* 5001以更新一個結構描述
* 5200可更新所有行銷活動
* 5101以更新101功能

更新套件應僅包含一個特定實體，以便可輕鬆重複使用。 若要進行分割，請新增數字（從1開始）。 這些套件沒有特定的排序規則。 若想進一步瞭解，假設我們有101功能、社交應用程式：
* 它包含webApp和外部帳戶。
   * 套件標籤為： 101 — 社交應用程式(socialApplication)。
* webApp上存在缺陷。
   * wepapp已更正。
   * 需要建立修正套件，其名稱如下： 5101 - 1 — 社交應用程式webApp (socialApplication_webApp)。
* 需要為社交功能新增新的外部帳戶。
   * 已建立外部帳戶。
   * 新封裝為： 5101 - 2 — 社交應用程式外部帳戶(socialApplication_extAccount)。
   * 同時更新101套件以新增至外部帳戶，但未部署。
     ![](assets/ncs_datapackage_best-practices-1.png)

#### 套件檔案 {#package-documentation}

更新套件時，您應該一律在說明欄位中加上註解，以詳細說明任何修改和原因（例如「新增結構」或「修正缺陷」）。

![](assets/ncs_datapackage_best-practices-2.png)

您也應該指定註解的日期。 請一律將您對更新套件的評論報告給「父級」（不含5首碼的套件）。

>[!IMPORTANT]
>
>說明欄位最多只能包含2.000個字元。
