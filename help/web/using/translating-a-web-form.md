---
product: campaign
title: 翻譯網路表單
description: 翻譯網路表單
feature: Web Forms
exl-id: 72959141-ca18-4512-80c7-239efd31f711
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '1565'
ht-degree: 1%

---

# 翻譯網路表單{#translating-a-web-form}

![](../../assets/common.svg)

可以將Web應用程式本地化為多種語言。

您可以直接在Adobe Campaign控制台中執行翻譯(請參閱 [在編輯器中管理翻譯](#managing-translations-in-the-editor))，或導出和導入字串以將翻譯外部化(請參閱 [外部化翻譯](#externalizing-translation))。

預設情況下可用的翻譯語言清單詳見 [更改表單顯示語言](#changing-forms-display-language)。

Web應用程式是以編輯語言設計的：這是用於輸入要翻譯的標籤和其他內容的參考語言。

預設語言是Web應用程式在未將語言設定添加到其訪問URL時將顯示的語言。

>[!NOTE]
>
>預設情況下，編輯語言和預設語言與控制台語言相同。

## 選擇語言 {#choosing-languages}

要定義一個或多個翻譯語言，請按一下 **[!UICONTROL Properties]** 按鈕 **[!UICONTROL Localization]** 頁籤。 按一下 **[!UICONTROL Add]** 按鈕，將選定的控制項在Tab鍵次序中移動。

>[!NOTE]
>
>此窗口還允許您更改預設語言和編輯語言。

![](assets/s_ncs_admin_survey_add_lang.png)

為Web應用程式添加翻譯語言時（或當預設語言和編輯語言不同時）, **[!UICONTROL Translation]** 頁籤添加到 **[!UICONTROL Edit]** 的子菜單。

Adobe Campaign公司包括翻譯和管理多語言翻譯的工具。 此編輯器允許您查看要翻譯或批准的字串、直接在介面中輸入翻譯或導入/導出字串以將翻譯外部化。

## 在編輯器中管理翻譯 {#managing-translations-in-the-editor}

### 收集字串 {#collecting-strings}

的 **[!UICONTROL Translations]** 頁籤，用於輸入構成Web應用程式的字串的翻譯。

首次開啟此頁籤時，它將不包含任何資料。 按一下 **[!UICONTROL Collect the strings to translate]** 連結以更新Web應用程式中的字串。

Adobe Campaign收集在中定義的欄位和字串的標籤 **[!UICONTROL Texts]** 所有靜態元素的頁籤：HTML塊、Javascript等 靜態元素在 [Web窗體中的靜態元素](static-elements-in-a-web-form.md)。

![](assets/s_ncs_admin_survey_trad_tab.png)

>[!CAUTION]
>
>根據要處理的資料量，此過程可能需要幾分鐘時間。
> 
>如果系統字典中出現警告，說明缺少某些翻譯，請參閱 [轉換系統字串](#translating-the-system-strings)。

每次翻譯字串時，其翻譯都會添加到翻譯字典中。

當收集流程檢測到翻譯已存在時，此翻譯將顯示在 **[!UICONTROL Text]** 的下界。 字串的狀態已轉換為 **[!UICONTROL Translated]**。

對於從未翻譯過的字串， **[!UICONTROL Text]** 欄位為空，狀態為 **[!UICONTROL To translate]**。

### 篩選字串 {#filtering-strings}

預設情況下，將顯示Web應用程式的每種翻譯語言。 有兩個預設篩選器：語言和狀態。 按一下 **[!UICONTROL Filters]** 按鈕，然後按一下 **[!UICONTROL By language or status]** 按鈕。 也可以建立高級篩選器。 如需詳細資訊，請參閱[此頁面](../../platform/using/creating-filters.md#creating-an-advanced-filter)。

![](assets/s_ncs_admin_survey_trad_tab_en.png)

轉到 **[!UICONTROL Language]** 下拉框中選擇翻譯語言。

要僅顯示未翻譯的字串，請選擇 **[!UICONTROL To translate]** 的 **[!UICONTROL Status]** 下拉框。 您也只能顯示已轉換或批准的字串。

### 轉換字串 {#translating-strings}

1. 要翻譯單詞，請按兩下字串清單中的行。

   ![](assets/s_ncs_admin_survey_trad_tab_add_term.png)

   源字串顯示在窗口的上部。

1. 在下部輸入其翻譯。 要批准它，請檢查 **[!UICONTROL Translation approved]** 的雙曲餘切值。

   >[!NOTE]
   >
   >翻譯審批是可選的，不會阻止該流程。

   未批准的翻譯顯示為 **[!UICONTROL Translated]**。 批准的翻譯顯示為 **[!UICONTROL Approved]**。

## 外部化翻譯 {#externalizing-translation}

可以使用Adobe Campaign以外的工具導出和導入字串以翻譯字串。

>[!CAUTION]
>
>導出字串後，不要使用整合工具執行任何翻譯。 當您重新導入翻譯時，這將導致衝突，這些翻譯將丟失。

### 導出檔案 {#exporting-files}

1. 選擇要導出其字串的Web應用程式，按一下右鍵，然後選擇 **[!UICONTROL Actions > Export strings for translation...]**

   ![](assets/s_ncs_admin_survey_trad_export.png)

1. 選擇 **[!UICONTROL Export strategy]** :

   * **[!UICONTROL One file per language]**:導出將生成每個翻譯語言的一個檔案。 每個檔案對所有選定的Web應用程式都是公用的。
   * **[!UICONTROL One file per Web application]**:導出將為每個選定的Web應用程式生成一個檔案。 每個檔案都包含所有翻譯語言。

      >[!NOTE]
      >
      >此類型的導出不可用於XLIFF導出。

   * **[!UICONTROL One file per language and per Web application]**:導出將生成多個檔案。 每個檔案將包含每個Web應用程式的一種翻譯語言。
   * **[!UICONTROL One file for all]**:導出將為所有Web應用程式生成單個多語言檔案。 它將包含所有選定Web應用程式的所有翻譯語言。

      >[!NOTE]
      >
      >此類型的導出不可用於XLIFF導出。

1. 然後選擇 **[!UICONTROL Target folder]** 記錄檔案。
1. 選擇檔案格式( **[!UICONTROL CSV]** 或 **[!UICONTROL XLIFF]** ) **[!UICONTROL Start]**。

![](assets/s_ncs_admin_survey_trad_export_start.png)

>[!NOTE]
>
>導出檔案的名稱將自動生成。 如果多次執行相同的導出操作，將用新檔案替換現有檔案。 如果需要保留以前的檔案，請更改 **[!UICONTROL Target folder]** ，然後按一下 **[!UICONTROL Start]** 的子菜單。

在中導出檔案時 **CSV格式**，每種語言都連結到狀態和批准狀態。 的 **批准？** 欄，您可以批准轉換。 此列可能包含 **是** 或 **否**。 有關整合編輯器(請參閱 [在編輯器中管理翻譯](#managing-translations-in-the-editor))，批准翻譯是可選的，不會阻止該過程。

### 導入檔案 {#importing-files}

完成外部翻譯後，可以導入已翻譯的檔案。

1. 轉到Web應用程式清單，按一下右鍵，然後選擇 **[!UICONTROL Actions > Import translated strings...]**

   >[!NOTE]
   >
   >無需選擇與翻譯相關的Web應用程式。 將游標放在Web應用程式清單的任意位置。

   ![](assets/s_ncs_admin_survey_trad_import.png)

1. 選擇要導入的檔案，然後按一下 **[!UICONTROL Upload]**。

   ![](assets/s_ncs_admin_survey_trad_import_start.png)

>[!NOTE]
>
>外部翻譯始終優先於內部翻譯。 在發生衝突時，內部翻譯將被外部翻譯覆蓋。

## 更改表單顯示語言 {#changing-forms-display-language}

Web表單以在 **[!UICONTROL Localization]** 頁籤。 要更改語言，必須將以下字元添加到URL的末尾(其中 **xx** 是語言的符號):

```
?lang=xx
```

如果語言是URL的第一個或唯一參數。 例如： **https://myserver/webApp/APP34?lang=en**

```
&lang=xx
```

的子菜單。 例如： **https://myserver/webApp/APP34?status=1&amp;lang=en**

下面列出了預設情況下可用的翻譯語言和詞典。

**預設系統字典**:某些語言包括包含系統字串翻譯的預設字典。 有關此內容的詳細資訊，請參閱 [轉換系統字串](#translating-the-system-strings)。

**日曆管理**:Web應用程式的頁面可以包括輸入日期的日曆。 預設情況下，此日曆可以使用多種語言（日翻譯、日期格式）。

<table> 
 <tbody> 
  <tr> 
   <td> <strong>語言（符號）</strong><br /> </td> 
   <td> <strong>預設系統字典</strong><br /> </td> 
   <td> <strong>日曆管理</strong><br /> </td> 
  </tr> 
  <tr> 
   <td> 德語(de)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 英語(en)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
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
   <td> 阿拉伯語(ar)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 中文(zh)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 韓語(ko)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 丹麥語(da)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 西班牙語(e)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 愛沙尼亞語（等）<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 芬蘭語(fi)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 法語(fr)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
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
   <td> 希臘語(el)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 希伯來語(he)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 匈牙利語(hu)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 印度尼西亞語(id)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 愛爾蘭語(ga)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 義大利語(it)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 義大利語（義大利）(it_IT)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 義大利語（瑞士）(it_CH)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 日語(ja)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 拉脫維亞語(lv)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 立陶宛語(lt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 馬爾他語(mt)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭語(nl)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭語（比利時）(nl_BE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 荷蘭語（荷蘭）(nl_NL)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 挪威語（挪威）(no_NO)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 波蘭語(pl)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 葡萄牙語(pt)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
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
   <td> 俄語(ru)<br /> </td> 
   <td> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 斯洛維尼亞語(sl)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 斯洛伐克語(sk)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典語(sv)<br /> </td> 
   <td> 是<br /> </td> 
   <td> 是<br /> </td> 
  </tr> 
  <tr> 
   <td> 瑞典語（芬蘭）(sv_FI)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瑞典語（瑞典）(sv_SE)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 捷克語(cs)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 泰語(th)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 越南語（六）<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
  <tr> 
   <td> 瓦隆(wa)<br /> </td> 
   <td> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>要添加預設提供的語言以外的其他語言，請參閱 [添加翻譯語言](#adding-a-translation-language)

## 示例：以多種語言顯示Web應用程式 {#example--displaying-a-web-application-in-several-languages}

以下Web表單有四種語言：英語、法語、德語和西班牙語。 所有字串都已通過 **[!UICONTROL Translation]** 的子菜單。 由於預設語言是英語，因此在發佈調查時，請使用標準URL以英語顯示。

![](assets/s_ncs_admin_survey_trad_sample_fr.png)

添加 **?lang=fr** 到URL的末尾，以法文顯示：

>[!NOTE]
>
>每種語言的符號清單詳見 [更改表單顯示語言](#changing-forms-display-language)。

![](assets/s_ncs_admin_survey_trad_sample_en.png)

可以添加 **?lang=es** 或 **?lang=de** 用西班牙語或德語顯示。

>[!NOTE]
>
>如果此Web應用程式已使用其他參數，請添加 **&amp;lang=**。\
>例如： **https://myserver/webApp/APP34?status=1&amp;lang=en**

## 高級翻譯配置 {#advanced-translation-configuration}

>[!CAUTION]
>
>此部分僅用於專家用戶。

### 轉換系統字串 {#translating-the-system-strings}

系統字串是所有Web應用程式使用的現成字串。 例如： **[!UICONTROL Next]** 。 **[!UICONTROL Previous]**。 **[!UICONTROL Approve]** 按鈕， **[!UICONTROL Loading]** 消息等。 預設情況下，某些語言包含帶有這些字串翻譯的字典。 語言清單詳見 [更改表單顯示語言](#changing-forms-display-language)。

如果您將Web應用程式翻譯成系統詞典未翻譯的語言，則會出現一條警告消息，讓您知道缺少某些翻譯。

![](assets/s_ncs_admin_survey_trad_error.png)

要添加語言，請應用以下步驟：

1. 轉到Adobe Campaign樹並按一下 **[!UICONTROL Administration > Configuration > Global dictionary > System dictionary]** 。
1. 在窗口的上半部分，選擇要轉換的系統字串，然後按一下 **[!UICONTROL Add]** 的下界。

   ![](assets/s_ncs_admin_survey_trad_system_translation.png)

1. 選擇翻譯語言並輸入字串的翻譯。 您可以通過檢查 **[!UICONTROL Translation approved]** 的雙曲餘切值。

   ![](assets/s_ncs_admin_survey_trad_system_translation2.png)

   >[!NOTE]
   >
   >翻譯審批是可選的，不會阻止該流程。

>[!CAUTION]
>
>不要刪除現成系統字串。

### 添加翻譯語言 {#adding-a-translation-language}

將Web應用程式翻譯成預設應用程式以外的語言(請參閱 [更改表單顯示語言](#changing-forms-display-language))，您需要添加新的翻譯語言。

1. 按一下 **[!UICONTROL Administration > Platform > Enumerations]** 的子目錄。 **[!UICONTROL Languages available for translation]** 清單中。 可用翻譯的清單顯示在窗口的下部。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_1.png)

1. 按一下 **[!UICONTROL Add]** ，然後輸入 **[!UICONTROL Internal name]**。 **[!UICONTROL Label]** 影像（標誌）的標識符。 要添加新映像，請與管理員聯繫。

   ![](assets/s_ncs_admin_survey_trad_new_itemized_list_2.png)
