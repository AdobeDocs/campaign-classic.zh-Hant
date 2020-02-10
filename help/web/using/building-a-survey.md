---
title: 建立調查
seo-title: 建立調查
description: 建立調查
seo-description: null
page-status-flag: never-activated
uuid: 50d501b9-2b4f-48d1-b394-f7f71c413990
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: online-surveys
discoiquuid: 6850851d-1dbe-44f0-bbff-18dbac2cad9a
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 建立調查{#building-a-survey}

## 建立新調查 {#creating-a-new-survey}

本章詳細說明如何使用Adobe Campaign **設計** 「調查」類型表單，以及可用的選項和設定。 Adobe Campaign可讓您將此調查提供給使用者，並在資料庫中收集和封存答案。

Web表單可通過樹 **[!UICONTROL Resources > Online > Web applications]** 的節點訪問。 若要建立調查，請按一 **[!UICONTROL New]** 下應用程式清單上方的按鈕，或以滑鼠右鍵按一下清單並選擇 **[!UICONTROL New]**。

選取調查範本(**[!UICONTROL newSurvey]** 依預設)。

![](assets/s_ncs_admin_survey_select_template.png)

表單的頁面是使用特殊編輯器建立的，可讓您定義和設定（文字）輸入欄位、選擇欄位（清單、核取方塊等）和靜態元素（影像、HTML內容等）。 您可以在「容器」中收集這些字元，並依需求進行排版(請參閱 [新增問題](#adding-questions))。

>[!NOTE]
>
>如需如何定義內容及建立網頁表單螢幕版面的詳細資訊，請參閱 [本節](../../web/using/about-web-forms.md)。

## 新增欄位 {#adding-fields}

表單中的欄位可讓使用者輸入資訊並選擇選項。 對於表單中的每個頁面，它們都是使用功能表透過工具列中的第一個按鈕來建立 **[!UICONTROL Add using the wizard]** 的。

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>您也可以使用滑鼠右鍵按一下並插入輸入區域。 預設情況下，區域將插入到選定樹的末端。 使用工具列中的箭頭來移動它。

### 欄位類型 {#types-of-fields}

將欄位新增至調查時，您需要選取其類型。 可以使用以下選項：

1. **[!UICONTROL Answer a question]**:此選項可讓您宣告新欄位（稱為「封存欄位」）以儲存答案。 在此情況下，即使參與者填入表單多次，所收集的所有值也會儲存。 此儲存模式僅適用於調查 **中**。 請參閱「 [儲存收集的答案」](../../web/using/managing-answers.md#storing-collected-answers)。
1. **[!UICONTROL Edit a recipient]**:此選項可讓您在資料庫中選取欄位。 在這種情況下，用戶答案將儲存在此欄位中。 對於每個參與者，僅保留最後保存的值，並將其添加到配置檔案資料中。
1. **[!UICONTROL Add a variable]**:此選項可讓您建立設定，讓資訊不儲存在資料庫中。 局部變數可宣告在上游。 您也可以在建立欄位時直接新增欄位。
1. **[!UICONTROL Import an existing question]**:此選項可讓您匯入在其他調查中建立的現有問題。

   >[!NOTE]
   >
   >儲存模式和欄位匯入在儲存收集的答 [案中有詳細說明](../../web/using/managing-answers.md#storing-collected-answers)。

要添加的欄位的性質（下拉清單、文本欄位、複選框等）適應選定的儲存模式。 您可以使用標籤的欄 **[!UICONTROL Type]** 位來變更它， **[!UICONTROL General]** 但請務必與資料類型保持一致。

![](assets/s_ncs_admin_survey_change_type.png)

本節將詳細說明各種可用欄 [位類型](../../web/using/about-web-forms.md)。

## 調查特定元素 {#survey-specific-elements}

線上調查使用Web應用程式功能。 連結至調查欄位的特定功能如下。

### 多重選擇 {#multiple-choice}

對於 **[!UICONTROL Multiple choice]** 文字控制項，您可以定義最小和最大選取數。 例如，此選項可讓您從可用選項強制選取至 **少** 2個值和最 **多** 4個值：

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

如果選取的數目過大或過小，則會顯示適當的訊息。

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>在這種情況下，會使用複選框來選擇選項。 只能使用一個選項時，會使用選項按鈕。

相應的配置如下：

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

此外，此輸入欄位的儲存位置必須是類 **[!UICONTROL Multiple values]** 型歸 **檔欄位**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* 此功能僅適用於「調查 **」類型** 表單。
>* 這個選項與隨機問題顯示不相容。 For more on this, refer to [Adding questions](#adding-questions).


### 新增問題 {#adding-questions}

容器有兩種類型：標準與問題。 標準容器可用來設定頁面版面配置和頁面中的條件式顯示。 本節將詳述 [這些內容](../../web/using/about-web-forms.md)。

使用「 **問題** 」容器，將問題新增至頁面，並在階層中插入下方可能的答案。 您可以在報表中分析使用者對此類型容器中所放置問題的回應。

>[!CAUTION]
>
>切勿將「問 **題** 」容器插入階 **層中的其** 他「問題」容器下方。

![](assets/s_ncs_admin_question_label.png)

在標籤欄位中輸入問題的標籤。 在這種情況下，將應用表單樣式表中的樣式。 選取個 **[!UICONTROL Enter the title in HTML format]** 人化選項。 這可讓您存取HTML編輯器。

>[!NOTE]
>
>有關使 [用HTML編輯器](../../web/using/about-web-forms.md) ，請參閱本節。

例如：

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

在上述範例中，演算方式如下：

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>每個問題都有「問 **題類** 型」容器。

您可以啟用Adobe Campaign隨機繪製問題。 然後，您就可以在設定視窗底部的欄位中，指定要在頁面中顯示的問題數。

![](assets/s_ncs_admin_survey_containers_qu_display.png)

轉換效果會如下所示：

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

重新整理頁面時，顯示的問題不相同。

>[!CAUTION]
>
>當您隨機顯示問題(**[!UICONTROL Display randomly]** 頁面上已勾選的選項)時，請務必避免使用多個選擇問題，其中必須有一個或多個選擇。

