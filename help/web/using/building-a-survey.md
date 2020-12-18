---
solution: Campaign Classic
product: campaign
title: 設計意見調查
description: 設計意見調查
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '796'
ht-degree: 2%

---


# 設計意見調查{#building-a-survey}

## 建立新調查{#creating-a-new-survey}

本章詳細說明使用Adobe Campaign設計&#x200B;**Survey**&#x200B;類型表單，以及可用的選項和設定。 Adobe Campaign可讓您將此調查提供給使用者，並在資料庫中收集和封存答案。

通過樹的&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;節點訪問Web表單。 若要建立調查，請按一下應用程式清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，或以滑鼠右鍵按一下清單並選擇&#x200B;**[!UICONTROL New]**。

選取調查範本（預設為&#x200B;**[!UICONTROL newSurvey]**）。

![](assets/s_ncs_admin_survey_select_template.png)

表單的頁面是使用特殊編輯器建立的，可讓您定義和設定（文字）輸入欄位、選擇欄位（清單、核取方塊等） 和靜態元素（影像、HTML內容等）。 您可在「容器」中收集這些字元，並依需求進行排版（請參閱「新增問題」[）。](#adding-questions)

>[!NOTE]
>
>如需如何定義內容並建立網頁表單螢幕版面的詳細資訊，請參閱[本節](../../web/using/about-web-forms.md)。

## 添加欄位{#adding-fields}

表單中的欄位可讓使用者輸入資訊並選擇選項。 對於表單中的每個頁面，都是使用&#x200B;**[!UICONTROL Add using the wizard]**&#x200B;功能表，透過工具列的第一個按鈕來建立。

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>您也可以使用滑鼠右鍵按一下並插入輸入區域。 預設情況下，區域將插入到選定樹的末端。 使用工具列中的箭頭來移動它。

### 欄位類型{#types-of-fields}

將欄位新增至調查時，您需要選取其類型。 可以使用以下選項：

1. **[!UICONTROL Answer a question]**:此選項可讓您宣告新欄位（稱為「封存欄位」）以儲存答案。在此情況下，即使參與者填入表單多次，所收集的所有值也會儲存。 此儲存模式僅適用於&#x200B;**調查**。 請參閱[儲存收集的答案](../../web/using/managing-answers.md#storing-collected-answers)。
1. **[!UICONTROL Edit a recipient]**:此選項可讓您在資料庫中選取欄位。在這種情況下，用戶答案將儲存在此欄位中。 對於每個參與者，僅保留最後保存的值，並將其添加到配置檔案資料中。
1. **[!UICONTROL Add a variable]**:此選項可讓您建立設定，讓資訊不儲存在資料庫中。局部變數可宣告在上游。 您也可以在建立欄位時直接新增欄位。
1. **[!UICONTROL Import an existing question]**:此選項可讓您匯入在其他調查中建立的現有問題。

   >[!NOTE]
   >
   >儲存模式和欄位導入在[儲存收集的答案](../../web/using/managing-answers.md#storing-collected-answers)中有詳細說明。

要添加的欄位的性質（下拉清單、文本欄位、複選框等） 適應選定的儲存模式。 您可以使用&#x200B;**[!UICONTROL General]**&#x200B;標籤的&#x200B;**[!UICONTROL Type]**&#x200B;欄位來變更它，但請務必與資料類型保持一致。

![](assets/s_ncs_admin_survey_change_type.png)

[本節](../../web/using/about-web-forms.md)中詳細介紹了各種可用欄位類型。

## 調查特定元素{#survey-specific-elements}

線上調查使用Web應用程式功能。 連結至調查欄位的特定功能如下。

### 多選項{#multiple-choice}

對於&#x200B;**[!UICONTROL Multiple choice]**&#x200B;類型控制項，您可以定義最小和最大選擇數。 例如，此選項可讓您從可用選項強制選擇至少&#x200B;**2**&#x200B;值和最多&#x200B;**4**&#x200B;值：

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

如果選取的數目過大或過小，則會顯示適當的訊息。

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>在這種情況下，會使用複選框來選擇選項。 只能使用一個選項時，會使用選項按鈕。

相應的配置如下：

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

此外，此輸入欄位的儲存位置必須為&#x200B;**[!UICONTROL Multiple values]**&#x200B;類型&#x200B;**歸檔欄位**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* 此功能僅適用於&#x200B;**Survey**&#x200B;類型表單。
>* 這個選項與隨機問題顯示不相容。 有關詳細資訊，請參閱[添加問題](#adding-questions)。


### 添加問題{#adding-questions}

容器有兩種類型：標準與問題。 標準容器可用來設定頁面版面配置和頁面中的條件式顯示。 [本節](../../web/using/about-web-forms.md)將詳細說明。

使用&#x200B;**Question**&#x200B;容器，將問題新增至頁面，並在階層中插入下方的可能答案。 您可以在報表中分析使用者對此類型容器中所放置問題的回應。

>[!CAUTION]
>
>切勿將&#x200B;**Question**&#x200B;容器插入階層中其他&#x200B;**Question**&#x200B;容器下方。

![](assets/s_ncs_admin_question_label.png)

在標籤欄位中輸入問題的標籤。 在這種情況下，將應用表單樣式表中的樣式。 選擇&#x200B;**[!UICONTROL Enter the title in HTML format]**&#x200B;選項以個人化它。 這可讓您存取HTML編輯器。

>[!NOTE]
>
>有關使用HTML編輯器的詳細資訊，請參閱[本節](../../web/using/about-web-forms.md)。

例如：

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

在上述範例中，演算方式如下：

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>每個問題都有一個&#x200B;**問題**&#x200B;類型容器。

您可以啟用Adobe Campaign隨機繪製問題。 然後，您就可以在設定視窗底部的欄位中，指定要在頁面中顯示的問題數。

![](assets/s_ncs_admin_survey_containers_qu_display.png)

轉換效果會如下所示：

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

重新整理頁面時，顯示的問題不相同。

>[!CAUTION]
>
>當您隨機顯示問題（在頁面上勾選了&#x200B;**[!UICONTROL Display randomly]**&#x200B;選項）時，請小心不要使用多個選擇問題，其中必須有一個或多個選擇。

