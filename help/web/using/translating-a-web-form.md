---
product: campaign
title: 轉譯網路表單
description: 轉譯網路表單
audience: web
content-type: reference
topic-tags: web-forms
exl-id: 72959141-ca18-4512-80c7-239efd31f711
source-git-commit: bd9f035db1cbad883e1f27fe901e34dfbc9c1229
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---

# 轉譯網路表單{#translating-a-web-form}

![](../../assets/common.svg)

將Web應用程式本地化為多種語言是可能的。

您可以直接在Adobe Campaign主控台中執行翻譯（請參閱[在編輯器](#managing-translations-in-the-editor)中管理翻譯），或匯出和匯入字串以將翻譯外部化（請參閱[將翻譯外部化](#externalizing-translation)）。

預設可用的翻譯語言清單在[更改表單顯示語言](#changing-forms-display-language)中詳細說明。

Web應用程式是以編輯語言設計的：這是用於輸入要翻譯的標籤和其他內容的參考語言。

預設語言是Web應用程式在未將語言設定添加到其訪問URL時將顯示的語言。

>[!NOTE]
>
>依預設，編輯語言和預設語言與主控台語言相同。

## 選擇語言 {#choosing-languages}

要定義一個或多個翻譯語言，請按一下Web應用程式的&#x200B;**[!UICONTROL Properties]**&#x200B;按鈕，然後按一下&#x200B;**[!UICONTROL Localization]**&#x200B;頁簽。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以定義Web應用程式的新翻譯語言。

>[!NOTE]
>
>此視窗也可讓您變更預設語言和編輯語言。

![](assets/s_ncs_admin_survey_add_lang.png)

為Web應用程式添加翻譯語言時（或當預設語言和編輯語言不同時）,**[!UICONTROL Translation]**&#x200B;子頁簽將添加到&#x200B;**[!UICONTROL Edit]**&#x200B;頁簽中以管理翻譯。

Adobe Campaign包含翻譯和管理多語言翻譯的工具。 此編輯器可讓您檢視要翻譯或核准的字串、直接將翻譯輸入介面，或匯入/匯出字元字串以將翻譯外部化。

## 在編輯器中管理翻譯 {#managing-translations-in-the-editor}

### 收集字串 {#collecting-strings}

**[!UICONTROL Translations]**&#x200B;索引標籤可讓您輸入組成Web應用程式的字元字串的翻譯。

您第一次開啟此標籤時，該標籤不會包含任何資料。 按一下&#x200B;**[!UICONTROL Collect the strings to translate]**&#x200B;連結以更新Web應用程式中的字串。

Adobe Campaign會收集所有靜態元素之&#x200B;**[!UICONTROL Texts]**&#x200B;索引標籤中定義之欄位和字串的標籤：HTML區塊、Javascript等 靜態元素在[Web表單](static-elements-in-a-web-form.md)的靜態元素中詳細說明。

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>根據要處理的資料量，此程式可能需要數分鐘。
> 
>如果出現警告，指出系統字典中缺少某些翻譯，請參閱[轉譯系統字串](#translating-the-system-strings)。

每次翻譯字串時，其翻譯都會新增至翻譯字典。

當收集程式檢測到已存在翻譯時，此翻譯會顯示在字串的&#x200B;**[!UICONTROL Text]**&#x200B;欄中。 字串的狀態將轉換為&#x200B;**[!UICONTROL Translated]**。

對於從未翻譯的字元字串，**[!UICONTROL Text]**&#x200B;欄位為空，狀態為&#x200B;**[!UICONTROL To translate]**。

### 篩選字串 {#filtering-strings}

預設情況下，將顯示Web應用程式的每種翻譯語言。 有兩個預設篩選器：語言和狀態。 按一下&#x200B;**[!UICONTROL Filters]**&#x200B;按鈕，然後按一下&#x200B;**[!UICONTROL By language or status]**&#x200B;以顯示相符的下拉式方塊。 您也可以建立進階篩選。 如需詳細資訊，請參閱[此頁面](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

![](assets/s_ncs_admin_survey_trad_tab_en.png)

前往&#x200B;**[!UICONTROL Language]**&#x200B;下拉式方塊，選取翻譯語言。

若只要顯示未翻譯的字串，請在&#x200B;**[!UICONTROL Status]**&#x200B;下拉式方塊中選取&#x200B;**[!UICONTROL To translate]**。 您也可以只顯示已翻譯或已核准的字串。

### 轉譯字串 {#translating-strings}

1. 若要翻譯單字，請連按兩下字串清單上的行。

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   源字串顯示在窗口的上部。

1. 在下部輸入其翻譯。 若要核准，請核取&#x200B;**[!UICONTROL Translation approved]**&#x200B;選項。

   >[!NOTE]
   >
   >翻譯核准是選用項目，不會封鎖程式。

   未批准的翻譯顯示為&#x200B;**[!UICONTROL Translated]**。 批准的翻譯顯示為&#x200B;**[!UICONTROL Approved]**。

## 外部化翻譯 {#externalizing-translation}

您可以匯出和匯入字元字串，使用Adobe Campaign以外的工具進行翻譯。

>[!CAUTION]
>
>匯出字串後，請勿使用整合工具執行任何翻譯。 這會在重新導入翻譯時導致衝突，並且這些翻譯將丟失。

### 匯出檔案 {#exporting-files}

1. 選擇要導出其字串的Web應用程式，按一下右鍵，然後選擇&#x200B;**[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. 選取&#x200B;**[!UICONTROL Export strategy]** :

   * **[!UICONTROL One file per language]**:導出將生成每個翻譯語言的一個檔案。每個檔案都是所有選定Web應用程式的共用檔案。
   * **[!UICONTROL One file per Web application]**:導出將為每個選定的Web應用程式生成一個檔案。每個檔案都包含所有翻譯語言。

      >[!NOTE]
      >
      >此類導出不適用於XLIFF導出。

   * **[!UICONTROL One file per language and per Web application]**:匯出將產生數個檔案。每個檔案將包含每個Web應用程式的一種翻譯語言。
   * **[!UICONTROL One file for all]**:導出將為所有Web應用程式生成單個多語言檔案。它將包含所有選定Web應用程式的所有翻譯語言。

      >[!NOTE]
      >
      >此類導出不適用於XLIFF導出。

1. 然後選擇要記錄檔案的&#x200B;**[!UICONTROL Target folder]**。
1. 選擇檔案格式（**[!UICONTROL CSV]**&#x200B;或&#x200B;**[!UICONTROL XLIFF]**），然後按一下&#x200B;**[!UICONTROL Start]**。

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>導出檔案的名稱將自動生成。 如果執行相同的導出多次，將用新檔案替換現有檔案。 如果需要保留先前的檔案，請更改&#x200B;**[!UICONTROL Target folder]** ，然後再次按一下&#x200B;**[!UICONTROL Start]**&#x200B;以運行導出。

當您匯出&#x200B;**CSV格式**&#x200B;的檔案時，每種語言都會連結至狀態和核准狀態。 **批准？** 欄可讓您核准翻譯。此列可包含值&#x200B;**Yes**&#x200B;或&#x200B;**No**。 至於整合編輯器（請參閱編輯器](#managing-translations-in-the-editor)中的[管理翻譯），核准翻譯是選用項目，不會阻礙程式。

### 匯入檔案 {#importing-files}

完成外部翻譯後，您可以匯入翻譯的檔案。

1. 轉到Web應用程式清單，按一下右鍵，然後選擇&#x200B;**[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >不需要選擇翻譯涉及的Web應用程式。 將游標放在Web應用程式清單上的任意位置。

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. 選擇要導入的檔案，然後按一下&#x200B;**[!UICONTROL Upload]**。

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>外部翻譯優先於內部翻譯。 如果發生衝突，內部翻譯將被外部翻譯覆蓋。

## 變更表單顯示語言 {#changing-forms-display-language}

Web表單以Web應用程式屬性的&#x200B;**[!UICONTROL Localization]**&#x200B;頁簽中指定的預設語言顯示。 若要變更語言，您必須在URL的結尾處新增下列字元（其中&#x200B;**xx**&#x200B;是語言的符號）:

```
?lang=xx
```

如果語言是URL的第一個或唯一參數。 例如：**https://myserver/webApp/APP34?lang=en**

```
&lang=xx
```

如果URL中語言之前有其他參數。 例如：**https://myserver/webApp/APP34?status=1&amp;lang=en**

預設可用的翻譯語言和字典列於下方。

**預設系統字典**:有些語言包括包含系統字串翻譯的預設字典。有關詳細資訊，請參閱[轉譯系統字串](#translating-the-system-strings)。

**日曆管理**:Web應用程式的頁面可以包含輸入日期的日曆。依預設，此日曆提供多種語言（日翻譯、日期格式）。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>語言（符號）</strong><br /> </td> 
   <td> <strong>預設系統字典</strong><br /> </td> 
   <td> <strong>日曆管理</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 德文(de)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 英語(en)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 英語（美國）(en_US)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 英語（英國）(en_GB)<br /> </td> 
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
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 西班牙文(es)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 愛沙尼亞文(et)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 芬蘭文(fi)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 法語(fr)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 法語（比利時）(fr_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 法語（法國）(fr_FR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 希臘文(el)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 希伯來語(he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 匈牙利文(hu)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 印度尼西亞文(id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 愛爾蘭語(ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 義大利文(it)<br /> </td> 
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 義大利文（義大利）(it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 義大利文（瑞士）(it_CH)<br /> </td> 
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
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 立陶宛文(lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 馬爾他語(mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭文(nl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭文（比利時）(nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭語（荷蘭）(nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 挪威文（挪威）(no_NO)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 波蘭文(pl)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙文(pt)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙語（巴西）(pt_BR)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙語（葡萄牙）(pt_PT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 俄文(ru)<br /> </td> 
   <td> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 斯洛維尼亞語(sl)<br /> </td> 
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
   <td> yes<br /> </td> 
   <td> yes<br /> </td> 
  </tr> 
  <tr> 
   <td> 瑞典文（芬蘭）(sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典文（瑞典）(sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 捷克文(cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 泰語(th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 越南文(vi)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 華侖(wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>要添加預設提供的語言以外的其他語言，請參閱[添加翻譯語言](#adding-a-translation-language)

## 範例：以多種語言顯示Web應用程式 {#example--displaying-a-web-application-in-several-languages}

下列網路表單提供四種語言：英語、法語、德語和西班牙語。 字元字串已通過Web表單的&#x200B;**[!UICONTROL Translation]**&#x200B;頁簽進行翻譯。 由於預設語言為英文，因此在發佈調查時，請使用標準URL以英文顯示。

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

將&#x200B;**?lang=fr**&#x200B;添加到URL的末尾，以法文顯示：

>[!NOTE]
>
>[更改表單顯示語言](#changing-forms-display-language)中詳細列出了每種語言的符號。

![](assets/s_ncs_admin_survey_trad_sample_en.png)

您可以新增&#x200B;**?lang=es**&#x200B;或&#x200B;**?lang=de**&#x200B;以西班牙文或德文顯示。

>[!NOTE]
>
>如果已為此Web應用程式使用了其他參數，請添加&#x200B;**&amp;lang=**。\
>例如：**https://myserver/webApp/APP34?status=1&amp;lang=en**

## 高級翻譯配置 {#advanced-translation-configuration}

>[!CAUTION]
>
>本節僅適用於專家使用者。

### 轉換系統字串 {#translating-the-system-strings}

系統字串是所有Web應用程式使用的現成可用字串。 例如：**[!UICONTROL Next]** 、 **[!UICONTROL Previous]** 、 **[!UICONTROL Approve]**&#x200B;按鈕、 **[!UICONTROL Loading]**&#x200B;消息等。 根據預設，某些語言包含包含這些字串翻譯的字典。 語言清單在[更改表單顯示語言](#changing-forms-display-language)中詳細說明。

如果您將Web應用程式翻譯成未翻譯系統字典的語言，則會出現警告訊息，通知您缺少某些翻譯。

![](assets/s_ncs_admin_survey_trad_error.png)

若要新增語言，請套用下列步驟：

1. 前往Adobe Campaign樹狀結構，然後按一下&#x200B;**[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** 。
1. 在窗口的上部，選擇要轉換的系統字串，然後按一下下部的&#x200B;**[!UICONTROL Add]**。

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. 選擇翻譯語言並輸入字串的翻譯。 您可以核取&#x200B;**[!UICONTROL Translation approved]**&#x200B;選項，以核准翻譯。

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >翻譯核准是選用項目，不會封鎖程式。

>[!CAUTION]
>
>請勿刪除現成可用的系統字串。

### 新增翻譯語言 {#adding-a-translation-language}

要將Web應用程式翻譯成預設語言以外的語言（請參閱[更改表單顯示語言](#changing-forms-display-language)），您需要添加新的翻譯語言。

1. 按一下Adobe Campaign樹的&#x200B;**[!UICONTROL Administration > Platform > Enumerations]**&#x200B;節點，然後從清單中選擇&#x200B;**[!UICONTROL Languages available for translation]**。 可用翻譯的清單顯示在窗口的下部。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕，然後輸入&#x200B;**[!UICONTROL Internal name]**、**[!UICONTROL Label]**&#x200B;和影像的標識符（標誌）。 要添加新映像，請與管理員聯繫。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)
