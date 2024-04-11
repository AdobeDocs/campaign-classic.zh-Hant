---
product: campaign
title: 翻譯網路表單
description: 翻譯網路表單
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Web Forms
exl-id: 72959141-ca18-4512-80c7-239efd31f711
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 1%

---

# 翻譯網路表單{#translating-a-web-form}



您可以將網頁應用程式當地化為數種語言。

您可以直接在Adobe Campaign主控台中執行翻譯(請參閱 [在編輯器中管理翻譯](#managing-translations-in-the-editor))，或匯出和匯入字串以外部化翻譯(請參閱 [外部化翻譯](#externalizing-translation))。

預設提供的翻譯語言清單詳見 [變更表單顯示語言](#changing-forms-display-language).

網頁應用程式是以編輯語言設計：這是用來輸入標籤和其他要翻譯內容的參考語言。

如果未將語言設定新增至其存取URL，預設語言為Web應用程式顯示的語言。

>[!NOTE]
>
>依預設，編輯語言和預設語言與主控台語言相同。

## 選擇語言 {#choosing-languages}

若要定義一或多個翻譯語言，請按一下 **[!UICONTROL Properties]** Web應用程式的按鈕，然後 **[!UICONTROL Localization]** 標籤。 按一下 **[!UICONTROL Add]** 按鈕以定義網頁應用程式的新翻譯語言。

>[!NOTE]
>
>此視窗也可讓您變更預設語言和編輯語言。

![](assets/s_ncs_admin_survey_add_lang.png)

當您新增網頁應用程式的翻譯語言時（或預設語言與編輯語言不同時）， **[!UICONTROL Translation]** 子索引標籤會新增至 **[!UICONTROL Edit]** 標籤以管理翻譯。

Adobe Campaign包含翻譯及管理多語言翻譯的工具。 此編輯器可讓您檢視要翻譯或核准的字串、直接在介面中輸入翻譯，或匯入/匯出字元字串以將翻譯外部化。

## 在編輯器中管理翻譯 {#managing-translations-in-the-editor}

### 收集字串 {#collecting-strings}

此 **[!UICONTROL Translations]** 索引標籤可讓您為構成Web應用程式的字元字串輸入翻譯。

第一次開啟此索引標籤時，不會包含任何資料。 按一下 **[!UICONTROL Collect the strings to translate]** 更新網頁應用程式中字串的連結。

Adobe Campaign會收集中定義的欄位和字串標籤 **[!UICONTROL Texts]** 所有靜態元素的索引標籤：HTML區塊、Javascript等。 靜態元素的詳細資訊，請參見 [網路表單中的靜態元素](static-elements-in-a-web-form.md).

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>視要處理的資料量而定，此程式可能需要幾分鐘的時間。
> 
>如果警告顯示系統字典中缺少某些翻譯，請參閱 [轉譯系統字串](#translating-the-system-strings).

每次翻譯字串時，其翻譯都會新增至翻譯字典。

當收集程式偵測到翻譯已存在時，此翻譯會顯示在 **[!UICONTROL Text]** 字串的欄。 字串的狀態已轉換為 **[!UICONTROL Translated]**.

對於從未翻譯過的字元字串， **[!UICONTROL Text]** 欄位為空白，狀態為 **[!UICONTROL To translate]**.

### 篩選字串 {#filtering-strings}

依預設，會顯示Web應用程式的每種翻譯語言。 預設篩選器有兩種：語言和狀態。 按一下 **[!UICONTROL Filters]** 按鈕，然後按一下 **[!UICONTROL By language or status]** 以顯示相符的下拉式方塊。 您也可以建立進階篩選。 如需詳細資訊，請參閱[此頁面](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

![](assets/s_ncs_admin_survey_trad_tab_en.png)

前往 **[!UICONTROL Language]** 下拉式方塊以選取翻譯語言。

若只要顯示未翻譯的字串，請選取 **[!UICONTROL To translate]** 在 **[!UICONTROL Status]** 下拉式方塊。 您也可以只顯示翻譯或核准的字串。

### 轉譯字串 {#translating-strings}

1. 若要翻譯單字，請在字串清單上連按兩下其行。

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   來源字串會顯示在視窗的上半部分。

1. 在下半部輸入其翻譯。 若要核准，請核取 **[!UICONTROL Translation approved]** 選項。

   >[!NOTE]
   >
   >翻譯核准為選用，不會阻礙此程式。

   未核准的翻譯會顯示為 **[!UICONTROL Translated]**. 已核准的翻譯會顯示為 **[!UICONTROL Approved]**.

## 外部化翻譯 {#externalizing-translation}

您可以使用Adobe Campaign以外的工具匯出和匯入字元字串以翻譯字元。

>[!CAUTION]
>
>匯出字串後，請勿使用整合工具執行任何翻譯。 當您重新匯入翻譯時，這會導致衝突，而且這些翻譯將會遺失。

### 匯出檔案 {#exporting-files}

1. 選取您要匯出其字串的Web應用程式，按一下滑鼠右鍵，然後選取 **[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. 選取 **[!UICONTROL Export strategy]** ：

   * **[!UICONTROL One file per language]**：匯出作業會針對每種翻譯語言產生一個檔案。 每個檔案對於所有選取的Web應用程式都是通用的。
   * **[!UICONTROL One file per Web application]**：匯出作業會針對每個選取的Web應用程式產生一個檔案。 每個檔案都會包含所有翻譯語言。

     >[!NOTE]
     >
     >此型別的匯出不適用於XLIFF匯出。

   * **[!UICONTROL One file per language and per Web application]**：匯出將會產生數個檔案。 每個檔案將包含每個網頁應用程式的一種翻譯語言。
   * **[!UICONTROL One file for all]**：匯出將會為所有Web應用程式產生單一多語言檔案。 它會包含所有選取之網頁應用程式的所有翻譯語言。

     >[!NOTE]
     >
     >此型別的匯出不適用於XLIFF匯出。

1. 然後選取 **[!UICONTROL Target folder]** 將記錄檔案的位置。
1. 選取檔案格式( **[!UICONTROL CSV]** 或 **[!UICONTROL XLIFF]** )並按一下 **[!UICONTROL Start]**.

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>匯出檔案的名稱會自動產生。 如果多次執行相同的匯出，則會以新的檔案取代現有的檔案。 如果您需要保留先前的檔案，請變更 **[!UICONTROL Target folder]** ，然後按一下 **[!UICONTROL Start]** 以再次執行匯出。

當您匯出檔案時 **CSV格式**，每種語言都會連結至狀態和核准狀態。 此 **核准？** 欄可讓您核准翻譯。 此欄可能包含值 **是** 或 **否**. 至於整合式編輯器(請參閱 [在編輯器中管理翻譯](#managing-translations-in-the-editor))，則核准翻譯為選用，不會阻礙此程式。

### 正在匯入檔案 {#importing-files}

外部翻譯完成後，您可以匯入已翻譯檔案。

1. 前往Web應用程式清單，按一下滑鼠右鍵，然後選取 **[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >不需要選取翻譯所關心的網頁應用程式。 將游標置於Web應用程式清單上的任何位置。

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. 選取要匯入的檔案，然後按一下 **[!UICONTROL Upload]**.

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>外部翻譯總是比內部翻譯優先。 如果發生衝突，內部翻譯將由外部翻譯覆寫。

## 變更表單顯示語言 {#changing-forms-display-language}

網路表單會以中指定的預設語言顯示 **[!UICONTROL Localization]** Web應用程式屬性的頁簽。 若要變更語言，您必須在URL結尾處新增下列字元(其中 **xx** 是語言的符號)：

```
?lang=xx
```

語言是URL的第一個或唯一引數。 例如： **https://myserver/webApp/APP34**

```
&lang=xx
```

如果URL中的語言之前有其他引數。 例如： **https://myserver/webApp/APP34?status=1&amp;lang=en**

以下列出預設可用的翻譯語言和字典。

**預設系統字典**：有些語言會包含預設字典，其中包含系統字串的翻譯。 有關詳細資訊，請參閱 [轉譯系統字串](#translating-the-system-strings).

**行事曆管理**：網頁應用程式的頁面可包含用於輸入日期的日曆。 依預設，此行事曆提供數種語言版本（日翻譯、日期格式）。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>語言（符號）</strong><br /> </td> 
   <td> <strong>預設系統字典</strong><br /> </td> 
   <td> <strong>行事曆管理</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 德文(de)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 英文(en)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 英文（美國） (en_US)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 英文（英國） (en_GB)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 阿拉伯文(ar)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 中文(zh)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 韓文(ko)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 丹麥文(da)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 西班牙文(es)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 愛沙尼亞文(et)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 芬蘭文(fi)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 法文(fr)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 法文（比利時） (fr_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 法文（法國） (fr_FR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 希臘文(el)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 希伯來文(he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 匈牙利文(hu)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 印尼文(id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 愛爾蘭文(ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 義大利文(it)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 義大利文（義大利） (it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 義大利文（瑞士） (it_CH)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 日文(ja)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 拉脫維亞文(lv)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 立陶宛文(lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 馬爾他文(mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭文(nl)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭文（比利時） (nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭文（荷蘭） (nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 挪威文（挪威） (no_NO)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 波蘭文(pl)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙文(pt)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙文（巴西） (pt_BR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙文（葡萄牙） (pt_PT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 俄文(ru)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 斯洛維尼亞文(sl)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 斯洛伐克文(sk)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典文(sv)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 瑞典文（芬蘭） (sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典文（瑞典） (sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 捷克文(cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 泰文(th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 越南文(vi)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瓦隆文(wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>若要新增預設語言以外的其他語言，請參閱 [新增翻譯語言](#adding-a-translation-language)

## 範例：以數種語言顯示網頁應用程式 {#example--displaying-a-web-application-in-several-languages}

下列網路表單提供四種語言版本：英文、法文、德文和西班牙文。 字元字串已透過 **[!UICONTROL Translation]** 網頁表單的索引標籤。 由於預設語言為英文，因此發佈調查表時，請使用標準URL以英文顯示。

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

新增 **？lang=fr** 在URL結尾以法文顯示：

>[!NOTE]
>
>每種語言的符號清單詳見 [變更表單顯示語言](#changing-forms-display-language).

![](assets/s_ncs_admin_survey_trad_sample_en.png)

您可以新增 **？lang=es** 或 **？lang=de** 以西班牙文或德文顯示。

>[!NOTE]
>
>如果此Web應用程式已經使用其他引數，請新增 **&amp;lang=**.\
>例如： **https://myserver/webApp/APP34?status=1&amp;lang=en**

## 進階翻譯設定 {#advanced-translation-configuration}

>[!CAUTION]
>
>本區段僅供專家使用者使用。

### 轉譯系統字串 {#translating-the-system-strings}

系統字串是所有Web應用程式所使用的現成可用的字元字串。 例如： **[!UICONTROL Next]** ， **[!UICONTROL Previous]**， **[!UICONTROL Approve]** 按鈕， **[!UICONTROL Loading]** 訊息等 依預設，某些語言會包含字典，其中包含這些字串的翻譯。 詳細語言清單位於 [變更表單顯示語言](#changing-forms-display-language).

如果您將Web應用程式翻譯成系統字典未翻譯的語言，則會出現警告訊息，通知您缺少部分翻譯。

![](assets/s_ncs_admin_survey_trad_error.png)

若要新增語言，請套用下列步驟：

1. 前往Adobe Campaign樹並按一下 **[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** .
1. 在視窗的上半部分，選取要翻譯的系統字串，然後按一下 **[!UICONTROL Add]** 位於下半部分。

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. 選取翻譯語言並輸入字串的翻譯。 您可以核取 **[!UICONTROL Translation approved]** 選項。

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >翻譯核准為選用，不會阻礙此程式。

>[!CAUTION]
>
>請勿刪除現成可用的系統字串。

### 新增翻譯語言 {#adding-a-translation-language}

若要將網頁應用程式翻譯成預設語言以外的其他語言(請參閱 [變更表單顯示語言](#changing-forms-display-language))，您將需要新增翻譯語言。

1. 按一下 **[!UICONTROL Administration > Platform > Enumerations]** Adobe Campaign樹狀結構的節點，並選取 **[!UICONTROL Languages available for translation]** 從清單中。 可用翻譯的清單會顯示在視窗的下方。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. 按一下 **[!UICONTROL Add]** 按鈕，然後輸入 **[!UICONTROL Internal name]**， **[!UICONTROL Label]** 和影像的識別碼（標幟）。 若要新增影像，請聯絡您的管理員。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)
