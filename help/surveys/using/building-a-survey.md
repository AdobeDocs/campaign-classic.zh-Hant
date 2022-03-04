---
product: campaign
title: 設計調查
description: 瞭解設計調查的關鍵步驟
feature: Surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: 36e546a34d8c2345fefed5d459095a76c6224a38
workflow-type: tm+mt
source-wordcount: '782'
ht-degree: 2%

---

# 設計調查{#building-a-survey}

![](../../assets/v7-only.svg)

## 建立新調查 {#creating-a-new-survey}

本章詳細介紹了 **調查** 使用Adobe Campaign鍵入表單，以及可用的選項和配置。 Adobe Campaign允許您將此調查提供給用戶，並在資料庫中收集和存檔答案。

通過 **[!UICONTROL Resources > Online > Web applications]** 的子目標。 要建立調查，請按一下 **[!UICONTROL New]** 按鈕，或者按一下右鍵清單並選擇 **[!UICONTROL New]**。

選擇調查模板(**[!UICONTROL newSurvey]** )。

![](assets/s_ncs_admin_survey_select_template.png)

表單的頁面使用特殊編輯器建立，該編輯器允許您定義和配置（文本）輸入欄位、選擇欄位（清單、複選框等） 和靜態元素(影像、HTML內容等)。 可以裝在&quot;容器&quot;內，按要求排列。 [了解更多](#adding-questions)).

>[!NOTE]
>
>有關如何定義Web表單的內容和建立螢幕佈局的詳細資訊，請參閱 [此文檔](../../web/using/about-web-forms.md)。

## 新增欄位 {#adding-fields}

表單中的欄位使用戶能夠輸入資訊並選擇選項。 對於表單中的每個頁面，它們是通過工具欄中的第一個按鈕使用 **[!UICONTROL Add using the wizard]** 的子菜單。

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>也可以使用按一下右鍵並插入輸入區域。 預設情況下，區域將插入選定樹的末端。 使用工具欄中的箭頭移動它。

### 欄位類型 {#types-of-fields}

將欄位添加到調查時，需要選擇其類型。 可以使用以下選項：

1. **[!UICONTROL Answer a question]**:此選項允許您聲明一個新欄位（稱為「存檔欄位」）來儲存答案。 在這種情況下，即使參與者在表單中多次填充，也會保存收集的所有值。 此儲存模式僅在 **調查**。 [了解更多資訊](../../surveys/using/managing-answers.md#storing-collected-answers)。
1. **[!UICONTROL Edit a recipient]**:此選項允許您在資料庫中選擇欄位。 在這種情況下，用戶答案將儲存在此欄位中。 對於每個參與者，只保留最後保存的值，並將其添加到配置檔案資料中。
1. **[!UICONTROL Add a variable]**:此選項允許您建立設定，以便資訊不儲存在資料庫中。 局部變數可以在上游聲明。 也可以在建立欄位時直接添加它們。
1. **[!UICONTROL Import an existing question]**:此選項允許您導入在其他調查中建立的現有問題。

   >[!NOTE]
   >
   >儲存模式和欄位導入在 [此部分](../../surveys/using/managing-answers.md#storing-collected-answers)。

要添加的欄位的性質（下拉清單、文本欄位、複選框等） 調整到選定的儲存模式。 您可以使用 **[!UICONTROL Type]** 的 **[!UICONTROL General]** 頁籤，但確保與資料類型保持一致。

![](assets/s_ncs_admin_survey_change_type.png)

有關各種類型的可用欄位的詳細資訊，請參閱 [此部分](../../web/using/about-web-forms.md)。

## 調查特定要素 {#survey-specific-elements}

線上調查基於Web應用程式功能。 下面詳述了特定於調查的功能。

### 多選項 {#multiple-choice}

對於 **[!UICONTROL Multiple choice]** 鍵入控制項，可定義最小和最大選擇數。 例如，此選項使您能夠將所選內容強制至 **2** 最多 **4** 值：

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

如果選擇的數量太大或太小，則顯示相應的消息。

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>在這種情況下，選項將使用複選框進行選中。 如果只能使用一個選項，則使用單選按鈕。

相應的配置如下：

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

此外，此輸入欄位的儲存位置必須為 **[!UICONTROL Multiple values]** 類型 **存檔欄位**:

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* 此功能僅適用於 **調查** 的子菜單。
>* 此選項與隨機問題顯示不相容。 [了解更多資訊](#adding-questions)。


### 添加問題 {#adding-questions}

有兩種容器類型：標準和問題。 標準容器用於配置頁面佈局和頁面中的條件顯示。 [了解更多資訊](../../web/using/about-web-forms.md)。

使用 **問題** 容器以向頁面添加問題，並在層次結構中插入下面可能的答案。 用戶對此類型容器中放置的問題的回答可以在報告中進行分析。

>[!CAUTION]
>
>從不插入 **問題** 另一個 **問題** 層次中的容器。

![](assets/s_ncs_admin_question_label.png)

問題的標籤將在標籤欄位中輸入。 在這種情況下，將應用窗體樣式表中的樣式。 選擇 **[!UICONTROL Enter the title in HTML format]** 按鈕，將選定控制項在Tab鍵次序中下移一個位置。 這將允許您訪問HTML編輯器。

>[!NOTE]
>
>請參閱 [此文檔](../../web/using/about-web-forms.md) 的子菜單。

例如：

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

在上例中，渲染將如下所示：

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>每個問題都有 **問題** 類型容器。

您可以啟用Adobe Campaign的隨機抽題。 然後，可以在配置窗口底部的欄位中指定要在頁面中顯示的問題數。

![](assets/s_ncs_admin_survey_containers_qu_display.png)

渲染將如下所示：

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

刷新頁面時，顯示的問題不相同。

>[!CAUTION]
>
>隨機顯示問題時(**[!UICONTROL Display randomly]** 選項)，請小心不要使用一個或多個選擇是必需的多個選擇問題。
