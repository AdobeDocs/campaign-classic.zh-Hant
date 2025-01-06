---
product: campaign
title: Adobe Campaign 工作區
description: 瞭解如何使用及自訂Campaign工作區
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
source-git-commit: 0ed70b3c57714ad6c3926181334f57ed3b409d98
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 31%

---

# Adobe Campaign 工作區{#adobe-campaign-workspace}



## 探索Adobe Campaign介面 {#about-adobe-campaign-interface}

連線資料庫之後，您就可以存取 Adobe Campaign 首頁了，Adobe Campaign 首頁是一個儀表板，其中包含了可用於存取功能的連結和捷徑，顯示的連結和捷徑具體取決於安裝以及一般平台設定。

在首頁的中央，您可以透過連結存取 Campaign 線上文件入口網站、論壇及支援網站。

![](assets/d_ncs_user_interface_home.png)

在[影片](#video)中探索![](assets/do-not-localize/how-to-video.png)行銷活動工作區

>[!NOTE]
>
>您執行個體上可用的Adobe Campaign功能取決於安裝的模組和附加元件。 部分功能可能無法使用，具體取決於您的許可及特定設定。
>
>在安裝任何模組或附加元件之前，您需要檢查您的授權合約或聯絡您的Adobe客戶主管。

### 主控台和網路存取 {#console-and-web-access}

可透過主控台或網際網路瀏覽器存取Adobe Campaign平台。 檢視[相容性矩陣](../../rn/using/compatibility-matrix.md#Browsers)中的相容瀏覽器。

網頁存取介面與主控台介面類似。 在瀏覽器中，您可以使用與主控台相同的導覽和顯示功能，但您只能在行銷活動上執行一組精簡的動作。 例如，您可以檢視和取消行銷活動，但無法修改行銷活動。 對於指定的運運算元，行銷活動將在主控台中顯示以下選項：

![操作員可以從行銷活動的儀表板檢視和取消行銷活動，也可以修改行銷活動，以及新增傳遞、檔案和任務。](assets/operation_from_console.png)

而使用Web存取時，選項主要是可讓您檢視：

![在瀏覽器中，相同的運運算元只能檢視和取消行銷活動。](assets/operation_from_web.png)

進一步瞭解[使用網頁介面](../../campaign/using/accessing-marketing-campaigns.md#using-the-web-interface-)。

### 語言 {#languages}

安裝Adobe Campaign Classic執行個體時，會選取語言。

![](assets/language.png)

您可以在五種不同的語言之間進行選擇：

* 英文 (英國)
* 英文 (美國)
* 法文
* 德文
* 日文

您為Adobe Campaign Classic執行個體選擇的語言可能會影響日期和時間格式。 如需詳細資訊，請參閱本[區段](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

有關如何建立執行個體的詳細資訊，請參閱此[頁面](../../installation/using/creating-an-instance-and-logging-on.md)。

>[!CAUTION]
>
>建立執行個體後無法變更語言。

## 基本的導覽功能 {#navigation-basics}

### 瀏覽頁面 {#browsing-pages}

平台功能各式各樣，可歸類為幾大核心功能，您可使用介面上方的連結來存取這些功能。

![](assets/overview_home.png)

哪些核心功能可用取決於您所安裝的套件、附加元件以及您的存取權。

每個功能根據任務相關需求和使用上下文包含一組功能。 例如，**[!UICONTROL Profiles and targets]**&#x200B;連結可讓您存取收件者清單、訂閱服務、現有的鎖定目標工作流程，以及建立這些元素的捷徑。

清單可透過&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;介面左側區段中的&#x200B;**[!UICONTROL Lists]**&#x200B;連結取得。

![](assets/recipient_list_overview.png)

### 使用索引標籤 {#using-tabs}

* 當您按一下核心功能或連結時，相關頁面會取代目前頁面。 若要返回上一頁，請按一下工具列上的&#x200B;**[!UICONTROL Back]**&#x200B;按鈕。 若要返回首頁，請按一下&#x200B;**[!UICONTROL Home]**&#x200B;按鈕。

  ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 若是功能表或顯示畫面的捷徑（例如網頁應用程式、方案、傳送、報告等），則相符的頁面會顯示在另一個索引標籤中。 這樣，您可使用索引標籤，從一個頁面切換到另一頁面。

  ![](assets/d_ncs_user_interface_tabs.png)

### 建立元素 {#creating-an-element}

每個核心功能區段都可讓您瀏覽可用的元素。 若要這麼做，請使用&#x200B;**[!UICONTROL Browsing]**&#x200B;區段中的捷徑。 **[!UICONTROL Other choices]**&#x200B;連結可讓您存取所有其他頁面，無論環境為何。

您可以使用畫面左側&#x200B;**[!UICONTROL Create]**&#x200B;區段中的捷徑來建立新元素（傳遞、Web應用程式、工作流程等）。 使用清單上方的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕，將新元素新增至清單。

例如，在傳遞頁面上，使用&#x200B;**[!UICONTROL Create]**&#x200B;按鈕來建立新傳遞。

![](assets/d_ncs_user_interface_tab_add_del.png)


## 格式和單位 {#formats-and-units}

### 日期和時間 {#date-and-time}

您的 Adobe Campaign Classic 實例的語言將會影響日期和時間格式。

安裝Campaign時會選取語言，且之後無法變更。 您可以選取：英文（美國）、英文（英文）、法文、德文或日文。 如需詳細資訊，請參閱[此頁面](../../installation/using/creating-an-instance-and-logging-on.md)。

英文 (US) 和英文 (EN) 的主要差異如下：

<table> 
 <thead> 
  <tr> 
   <th> 格式<br /> </th> 
   <th> 英文（美國）<br /> </th> 
   <th> 英文(EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 星期從星期日開始<br /> </td> 
   <td> 星期從星期一<br />開始 </td> 
  </tr> 
  <tr> 
   <td> 簡短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>範例：09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>範例：25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> 具有時間<br />的簡短日期 </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>例如： 2018年9月25日10:47:25下午</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>例如： 2018年9月25日22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 在列舉中新增值 {#add-values-in-an-enumeration}

使用下拉式清單的輸入欄位，您可以輸入列舉值，該值可以儲存起來，然後作為下拉式清單中的選項提供。 例如，在收件者設定檔之&#x200B;**[!UICONTROL General]**&#x200B;索引標籤的&#x200B;**[!UICONTROL City]**&#x200B;欄位中，您可以輸入London。 當您按下Enter以確認此值時，訊息會詢問您是否要為與該欄位關聯的列舉儲存此值。

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

如果按一下&#x200B;**[!UICONTROL Yes]**，則相關欄位的下拉式方塊中會提供此值（在此案例中為： **[!UICONTROL London]**）。

>[!NOTE]
>
>分項清單（也稱為「分項清單」）由管理員透過&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;區段來管理。 如需詳細資訊，請參閱[管理分項清單](../../platform/using/managing-enumerations.md)。

### 預設單位 {#default-units}

在表示時間期間 (例如，傳遞資源的有效期限、任務的核准期限等) 的欄位中，可以採用下列&#x200B;**單位** 列示值：

* **[!UICONTROL s]**&#x200B;代表秒數，
* **[!UICONTROL mn]**&#x200B;分鐘，
* **[!UICONTROL h]**&#x200B;代表小時，
* **[!UICONTROL d]**&#x200B;天。

![](assets/enter_unit_sample.png)

## 教學課程影片 {#video}

本影片說明Campaign Classic工作區。

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

其他 Campaign Classic 作法影片可在[此處](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
