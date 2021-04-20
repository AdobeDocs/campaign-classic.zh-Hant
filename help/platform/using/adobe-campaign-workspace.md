---
solution: Campaign Classic
product: campaign
title: Adobe Campaign 工作區
description: 瞭解如何使用和自訂促銷活動工作區
feature: Overview
role: Data Engineer
level: Beginner
exl-id: 5f689679-7148-4abd-a9bf-185854c64b13
translation-type: tm+mt
source-git-commit: d7eabfbebf016d2632d95d34a5b36719ccc1d88a
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 79%

---

# Adobe Campaign 工作區{#adobe-campaign-workspace}

## 探索Adobe Campaign介面{#about-adobe-campaign-interface}

連線資料庫之後，您就可以存取 Adobe Campaign 首頁了，Adobe Campaign 首頁是一個儀表板，其中包含了可用於存取功能的連結和捷徑，顯示的連結和捷徑具體取決於安裝以及一般平台設定。

在首頁的中央，您可以透過連結存取 Campaign 線上文件入口網站、論壇及支援網站。

![](assets/d_ncs_user_interface_home.png)

![](assets/do-not-localize/how-to-video.png)[ 在影片中探索行銷活動工作區](#video)

>[!NOTE]
>
>您的實例上可用的 Adobe Campaign 功能取決於安裝的模組和附加元件。部分功能可能無法使用，具體取決於您的許可及特定設定。
>
>在安裝任何模組或附加元件之前，您需要檢查您的授權合約，或聯絡您的Adobe銷售代表。

### 主控台和網路存取 {#console-and-web-access}

Adobe Campaign 平台可透過主控台或網際網路瀏覽器進行存取。

網路存取介面與主控台的介面類似，但是功能有所減少。

例如，針對指定的操作者，在主控台中將顯示下列行銷活動選項：

![](assets/operation_from_console.png)

而網路存取介面上，主要啟用檢視選項：

![](assets/operation_from_web.png)

### 語言{#languages}

安裝Adobe Campaign Classic實例時，會選擇該語言。

![](assets/language.png)

您可以在5種不同的語言之間進行選擇：

* 英文（英國）
* 英文 (US)
* 法文
* 德文
* 日文

您為Adobe Campaign Classic實例選擇的語言可能會影響日期和時間格式。 如需詳細資訊，請參閱本[區段](../../platform/using/adobe-campaign-workspace.md#date-and-time)。

有關如何建立實例的詳細資訊，請參閱此[頁](../../installation/using/creating-an-instance-and-logging-on.md)。

>[!CAUTION]
>
>建立例項後，無法變更語言。

## 基本的導覽功能 {#navigation-basics}

### 瀏覽頁{#browsing-pages}

平台功能各式各樣，可歸類為幾大核心功能，您可使用介面上方的連結來存取這些功能。

![](assets/overview_home.png)

哪些核心功能可用取決於您所安裝的套件、附加元件以及您的存取權。

每項核心功能都包含一套基於任務相關需求及使用情境的功能。例如，使用 **[!UICONTROL Profiles and targets]** 連結，您可以找到收件者清單、訂閱服務、現有的目標工作流程，以及建立這些元素的捷徑。

這些清單可通過&#x200B;**[!UICONTROL Profiles and Targets]**&#x200B;介面左側部分的&#x200B;**[!UICONTROL Lists]**&#x200B;連結獲得。

![](assets/recipient_list_overview.png)

### 使用標籤{#using-tabs}

* 當您按一下核心功能或連結時，相關頁面會取代當前頁面。若要返回到上一頁，請按一下工具列上的 **[!UICONTROL Back]** 按鈕。若要返回到首頁，請按一下 **[!UICONTROL Home]** 按鈕。

   ![](assets/d_ncs_user_interface_back_home_buttons.png)

* 按一下顯示畫面 (例如網路應用程式、方案、傳遞、報告等) 的選單和捷徑時，將在另一個索引標籤中顯示相關頁面。這樣，您可使用索引標籤，從一個頁面切換到另一頁面。

   ![](assets/d_ncs_user_interface_tabs.png)

### 建立元素{#creating-an-element}

使用每個核心功能區段，您可以瀏覽可用的元素。若要瀏覽可用元素，請使用 **[!UICONTROL Browsing]** 區段中的捷徑。使用 **[!UICONTROL Other choices]** 連結，您可存取其他所有頁面，不受環境影響。

您可以建立新元素（傳送、Web應用程式、工作流程等） 使用畫面左側&#x200B;**[!UICONTROL Create]**&#x200B;區段中的捷徑。 使用清單上方的 **[!UICONTROL Create]** 按鈕，將新元素新增至清單中。

例如，在傳遞頁面上，使用 **[!UICONTROL Create]** 按鈕來建立新的傳遞。

![](assets/d_ncs_user_interface_tab_add_del.png)


## 格式和單位 {#formats-and-units}

### 日期和時間 {#date-and-time}

您的 Adobe Campaign Classic 實例的語言將會影響日期和時間格式。

您無法在之後變更安裝 Campaign 時選取的語言。您可以選取：英文 (US)、英文 (EN)、法文、德文或日文。有關詳細資訊，請參見[此頁面](../../installation/using/creating-an-instance-and-logging-on.md)。

英文 (US) 和英文 (EN) 的主要差異如下：

<table> 
 <thead> 
  <tr> 
   <th> 格式<br /> </th> 
   <th> 英文 (US)<br /> </th> 
   <th> 英文 (EN)<br /> </th> 
  </tr> 
 </thead> 
 <tbody> 
  <tr> 
   <td> 日期<br /> </td> 
   <td> 週開始於星期日<br /> </td> 
   <td> 週開始於星期一<br /> </td> 
  </tr> 
  <tr> 
   <td> 簡短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y</p><p><strong>範例：09/25/2018</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y</p><p><strong>範例：25/09/2018</strong></p> </td> 
  </tr> 
  <tr> 
   <td> 帶時間的簡短日期<br /> </td> 
   <td> <p>%2M/%2D/%4Y %I:%2N:%2S %P</p><p><strong>範例：09/25/2018 10:47:25 PM</strong></p> </td> 
   <td> <p>%2D/%2M/%4Y %2H:%2N:%2S</p><p><strong>範例：25/09/2018 22:47:25</strong></p> </td> 
  </tr> 
 </tbody> 
</table>

### 在列舉中新增值 {#add-values-in-an-enumeration}

使用下拉式清單中的輸入欄位，您可以輸入列舉值，可存儲該值，作為下拉式清單中的選項提供。例如，在收件者用戶檔案之 **[!UICONTROL City]** 索引標籤的 **[!UICONTROL General]** 欄位中，您可以輸入 London。當您按下 Enter 以確認此值時，將顯示一條訊息，詢問您是否要儲存此值以用於欄位相關的列舉。

![](assets/s_ncs_user_wizard_email_bat_substitute_email.png)

如果按一下 **[!UICONTROL Yes]**，就可以在相關欄位 (在此案例中為：**[!UICONTROL London]**) 的下拉式方塊中提供這個值。

>[!NOTE]
>
>管理員可透過 **[!UICONTROL Administration > Platform > Enumerations]** 區域管理列舉 (也稱為「分項清單」)。有關詳細資訊，請參閱[管理枚舉](../../platform/using/managing-enumerations.md)。

### 預設單位 {#default-units}

在表示時間期間 (例如，傳遞資源的有效期限、任務的核准期限等) 的欄位中，可以採用下列&#x200B;**單位** 列示值：

* **[!UICONTROL s]** 幾秒鐘內，
* **[!UICONTROL mn]** 幾分鐘內，
* **[!UICONTROL h]** 幾個小時，
* **[!UICONTROL d]** 幾天。

![](assets/enter_unit_sample.png)

## 教學課程影片{#video}

此影片顯示Campaign Classic工作區。

>[!VIDEO](https://video.tv.adobe.com/v/35130?quality=12)

其他Campaign Classichow-to影片可在[這裡](https://experienceleague.adobe.com/docs/campaign-classic-learn/tutorials/overview.html?lang=zh-Hant)取得。
