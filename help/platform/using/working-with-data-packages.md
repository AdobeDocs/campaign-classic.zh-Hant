---
title: 使用資料包
seo-title: 使用資料包
description: 使用資料包
seo-description: null
page-status-flag: never-activated
uuid: 867b2702-dbc4-4b71-a385-a2c7fd09d25e
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: platform
content-type: reference
topic-tags: administration-basics
discoiquuid: 42867665-d0ca-486e-9110-91716c0d5c57
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 使用資料包{#working-with-data-packages}

## 關於資料包 {#about-data-packages}

使用 Adobe Campaign，您可以透過資料包系統匯出或匯入平台設定和資料。包可以包含不同類型的配置、元素、過濾或不過濾。

資料包可以 XML 格式檔案的形式顯示 Adobe Campaign 資料庫的實體。資料包中包含的每個實體都會以其所有資料表示。

The principle of **data packages** is to export a data configuration and integrate it into another Adobe Campaign system. 有關如何維護一組一致的資料包的詳細資訊，請參閱此 [技術](https://docs.campaign.adobe.com/doc/AC/en/technicalResources/Technotes/AdobeCampaign_How_to_maintain_a_consistent_set_of_data_packages.pdf)。

### 包類型 {#types-of-packages}

可導出包有三種類型：使用者套件、平台套件和管理套件。

* **用戶包**:它允許您選擇要導出的圖元清單。 此類軟體包可管理相依性並驗證錯誤。
* **平台套件**:它包含所有新增的技術資源（非標準）:結構描述、JavaScript程式碼等。

   ![](assets/ncs_datapackage_package_platform.png)

* **管理套件**:它包含所有新增的範本和商業物件（非標準）:範本、資料庫等。

   ![](assets/ncs_datapackage_package_admin.png)

>[!CAUTION]
>
>平 **台和管** 理類型包 **含要導出的** 、預定義的實體清單。 每個實體都會連結至篩選條件，讓您移除已建立套件的現成可用資源。

## 資料結構 {#data-structure}

資料包的描述是符合 **xrk:navtree資料架構的語法的結構化XML文** 檔。

資料套件範例：

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

XML檔案必須以元素開始和結 **`<package>`** 束。 隨後 **`<entities>`** 的任何元素會依檔案類型分發資料。

元 **`<entities>`** 素包含在模式屬性中輸入的資料模式格式的包 **資料** 。

套件中的資料不得包含不相容於基本之間的內部索引鍵，例如自動產生的索引鍵(**autopk** 選項)。

在我們的示例中，「資料夾」和「公司」連結上的連接已被目標表上的所謂「高級」鍵替換：

```
<recipient>
  <folder _operation="none" name="nmsRootFolder"/>
  <company _operation="none" name="Adobe"/>
</recipient>
```

具有 **`operation`** 值&quot;none&quot;的屬性定義協調連結。

可以從任何文本編輯器手動構建資料包。 只要確保XML檔案的結構符合「xtk:navtree」資料架構。 Adobe Campaign主控台有資料套件匯出與匯入模組。

## 導出包 {#exporting-packages}

### 關於套件匯出 {#about-package-export}

可以以三種不同的方式導出包：

* 可 **[!UICONTROL Package Export Wizard]** 以在單個包中導出一組對象。 有關詳細資訊，請參 [閱導出包中的一組對象](#exporting-a-set-of-objects-in-a-package)
* 單 **個對象** ，可通過按一下右鍵並選擇直接導出到包中 **[!UICONTROL Actions > Export in a package]**。
* **包定義** 可讓您建立包結構，在其中添加將在以後在包中導出的對象。 有關詳細資訊，請參閱管 [理包定義](#managing-package-definitions)

在匯出套件後，您就可以將它和所有新增的實體匯入另一個促銷活動例項。

### 導出包中的一組對象 {#exporting-a-set-of-objects-in-a-package}

套件匯出精靈可透過Adobe Campaign用戶 **[!UICONTROL Tools > Advanced > Export package...]** 端主控台的選單存取。

![](assets/ncs_datapackage_typepackage.png)

對於三種類型的包，嚮導提供了以下步驟：

1. 按文檔類型列出要導出的圖元：

   ![](assets/ncs_datapackage_export2.png)

   >[!CAUTION]
   >
   >如果您匯出 **[!UICONTROL Offer category]**、 **[!UICONTROL Offer environment]**&#x200B;或 **[!UICONTROL Program]** 類型資料夾，請勿選取 **[!UICONTROL Plan]** xtk:folder **** ，因為您可能會遺失一些資料。 選擇與資料夾對應的實體： **nms:offerCategory** for offer 、 **nms:offerEnv** for offer環境、 **nms:program** for programs和 **** nms:plan for plans

   清單管理可讓您新增或刪除要從設定匯出的實體。 按一下 **[!UICONTROL Add]** 以選擇新圖元。

   按鈕 **[!UICONTROL Detail]** 會編輯選取的設定。

   >[!NOTE]
   >
   >從屬機制控制實體導出序列。 For more on this, refer to [Managing dependencies](#managing-dependencies).

1. 實體配置螢幕定義要提取的文檔類型的過濾器查詢。

   必須為資料抽取配置過濾子句。

   ![](assets/ncs_datapackage_export4.png)

   >[!NOTE]
   >
   >此部分顯示查詢 [編輯器](../../platform/using/about-queries-in-campaign.md)。

1. 按一下 **[!UICONTROL Next]** 並選擇排序列，以在提取過程中對資料進行排序：

   ![](assets/ncs_datapackage_export5.png)

1. 在執行匯出之前，先預覽要擷取的資料。

   ![](assets/ncs_datapackage_export6.png)

1. 套件匯出精靈的最後一頁可讓您開始匯出。 資料將儲存在欄位中指示的檔 **[!UICONTROL File]** 案中。

   ![](assets/ncs_datapackage_export7.png)

### 管理相依性 {#managing-dependencies}

匯出機制可讓Adobe Campaign追蹤各種匯出元素之間的連結。

此機制由兩個規則定義：

* 連結到具有自 **己****或** owncopy類型完整性的連結的對象將導出到與導出對象相同的包中。
* 連結至具有中性或定 **義類型****** 完整性（定義的連結）的物件必須個別匯出。

>[!NOTE]
>
>連結到方案元素的完整性類型在本節 [中定義](../../configuration/using/database-mapping.md#links--relation-between-tables)。

#### 匯出促銷活動 {#exporting-a-campaign}

以下是如何匯出促銷活動的範例。 要匯出的行銷促銷活動包含一個工作(標籤：「MyTask」)和工作流程(標籤：「MyWorkflow」檔案夾(節點：管理／生產／技術工作流程／促銷活動流程/ myWorkflow)。

任務和工作流會匯出到與促銷活動相同的套件中，因為符合的結構描述是由具有「自有」類型完整性的連結所連結。

封裝內容：

```
<?xml version='1.0'?>
<package author="Administrator (admin)" buildNumber="7974" buildVersion="6.1" img=""
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

與包類型的隸屬關係在具有@pkgAdmin和@pkgPlatform屬性 **的架構中定義** 。 這兩個屬性都接收定義與軟體包關聯的條件的XTK表達式。

```
<element name="offerEnv" img="nms:offerEnv.png" 
template="xtk:folder" pkgAdmin="@id != 0">
```

最後， **@pkgStatus** 屬性使您能夠定義這些元素或屬性的導出規則。 根據屬性的值，元素或屬性將在導出的包中找到。 此屬性的三個可能值是：

* **永不**:不匯出欄位／連結
* **一律**:這個領域的出口
* **preCreate**:授權建立連結的實體

>[!NOTE]
>
>僅 **允許連結類型** 事件使用preCreate值。 它授權您建立或指向尚未載入匯出封裝中的實體。

## 管理包定義 {#managing-package-definitions}

### 關於包定義 {#about-package-definitions}

包定義允許您建立包結構，在其中添加將在以後在單個包中導出的實體。 然後，您就可以將此套件及所有新增的實體匯入另一個促銷活動實例。

**相關主題：**

* [建立包定義](#creating-a-package-definition)
* [向包定義添加實體](#adding-entities-to-a-package-definition)
* [配置包定義生成](#configuring-package-definitions-generation)
* [從包定義導出包](#exporting-packages-from-a-package-definition)

### 建立包定義 {#creating-a-package-definition}

可從菜單訪問包定 **[!UICONTROL Administration > Configuration > Package management > Package definitions]** 義。

要建立包定義，請按一下該按 **[!UICONTROL New]** 鈕，然後填寫包定義一般資訊。

![](assets/packagedefinition_create.png)

然後，可以將實體添加到包定義中，並將其導出到XML檔案包中。

**相關主題：**

* [向包定義添加實體](#adding-entities-to-a-package-definition)
* [配置包定義生成](#configuring-package-definitions-generation)
* [從包定義導出包](#exporting-packages-from-a-package-definition)

### 向包定義添加實體 {#adding-entities-to-a-package-definition}

在頁籤 **[!UICONTROL Content]** 中，按一下按 **[!UICONTROL Add]** 鈕以選擇要與包一起導出的實體。 在「導出包中的一組對象」( [Exporting a set of objects in a package](#exporting-a-set-of-objects-in-a-package) )部分中顯示了選擇圖元時的最佳做法。

![](assets/packagedefinition_addentities.png)

實體可直接從實體在實例中的位置添加到包定義中。 要執行此操作，請遵循下列步驟：

1. 以滑鼠右鍵按一下所要的實體，然後選取 **[!UICONTROL Actions > Export in a package]**。

   ![](assets/packagedefinition_singleentity.png)

1. 選 **[!UICONTROL Add to a package definition]**&#x200B;擇，然後選擇要向其添加實體的包定義。

   ![](assets/packagedefinition_packageselection.png)

1. 實體將添加到包定義中，它將與包一起導出(請參閱從包定 [義導出包](#exporting-packages-from-a-package-definition))。

   ![](assets/packagedefinition_entityadded.png)

### 配置包定義生成 {#configuring-package-definitions-generation}

可以從包定義頁籤配置包生 **[!UICONTROL Content]** 成。 若要這麼做，請按一下 **[!UICONTROL Generation parameters]** 連結。

![](assets/packagedefinition_generationparameters.png)

* **[!UICONTROL Include the definition]**:包括當前在包定義中使用的定義。
* **[!UICONTROL Include an installation script]**:可讓您新增javascript指令碼，以便在套件匯入時執行。 選取此選項時， **[!UICONTROL Script]** 會在套件定義畫面中新增標籤。
* **[!UICONTROL Include default values]**:向包中添加所有實體屬性的值。

   為避免冗長的匯出，預設不會選取此選項。 這表示具有預設值(「空字串」、「0」和「false」（如果未在模式中定義）的實體屬性不會添加到包中，因此不會導出。

   >[!CAUTION]
   >
   >取消選取此選項可導致合併本機和匯入的版本。
   >
   >如果導入包的實例包含與包的實體相同的實體（例如，具有相同的外部ID），則不會更新其屬性。 如果前實例的屬性具有預設值（因為這些值未包含在包中），則會發生這種情況。
   >
   >在這種情況下，選擇該選 **[!UICONTROL Include default values]** 項將防止版本合併，因為前實例的所有屬性都將與包一起導出。

### 從包定義導出包 {#exporting-packages-from-a-package-definition}

要從包定義導出包，請執行以下步驟：

1. 選擇要導出的包定義，然後按一下按 **[!UICONTROL Actions]** 鈕並選擇 **[!UICONTROL Export the package]**。
1. 預設情況下，將選擇與導出的包對應的XML檔案。 它根據包定義命名空間和名稱命名。
1. 定義包名和位置後，按一下按 **[!UICONTROL Start]** 鈕啟動導出。

   ![](assets/packagedefinition_packageexport.png)

## 導入包 {#importing-packages}

### 關於包導入 {#about-package-import}

套件匯入精靈可透過Adobe Campaign用戶端主控台 **[!UICONTROL Tools > Advanced > Package import...]** 的主功能表存取。

您可以從先前執行的匯出匯入套件，例如從其他Adobe Campaign實例或標準套件匯入套件，視授權條款而定。

![](assets/ncs_datapackage_import.png)

### 從檔案安裝軟體包 {#installing-a-package-from-a-file}

若要匯入現有的資料套件，請選取XML檔案，然後按一下 **[!UICONTROL Open]**。

![](assets/ncs_datapackage_import_1.png)

然後，要導入的包的內容將顯示在編輯器的中間部分。

按一 **[!UICONTROL Next]** 下並 **[!UICONTROL Start]** 啟動匯入。

![](assets/ncs_datapackage_import_2.png)

### 安裝標準軟體包 {#installing-a-standard-package}

設定Adobe Campaign時，會安裝標準套件。 視您的權限和部署模型而定，如果您取得新選項或附加元件，或升級至新選件，則可匯入新的標準套件。

請參閱您的授權合約以檢查您可以安裝哪些套件。

有關標準軟體包的詳細資訊，請參 [閱本頁](../../installation/using/installing-campaign-standard-packages.md)。
