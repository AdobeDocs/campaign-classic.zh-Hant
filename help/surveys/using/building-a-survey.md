---
product: campaign
title: 設計調查
description: 瞭解設計調查的關鍵步驟
badge-v8: label="也適用於v8" type="Positive" tooltip="亦適用於Campaign v8"
feature: Surveys
exl-id: 8d83dfd5-70ec-4656-965b-f6b5e6f9eec1
source-git-commit: e34718caefdf5db4ddd61db601420274be77054e
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 2%

---

# 設計調查{#building-a-survey}



## 建立新的調查 {#creating-a-new-survey}

本章詳細說明如何使用Adobe Campaign設計&#x200B;**調查**&#x200B;型別表單，以及可用的選項和設定。 Adobe Campaign可讓您將此調查提供給使用者，並在資料庫中收集和封存答案。

網路表單可透過樹狀結構的&#x200B;**[!UICONTROL Resources > Online > Web applications]**&#x200B;節點存取。 若要建立意見調查，請按一下應用程式清單上方的&#x200B;**[!UICONTROL New]**&#x200B;按鈕，或用滑鼠右鍵按一下清單，然後選擇&#x200B;**[!UICONTROL New]**。

選取問卷範本（預設為&#x200B;**[!UICONTROL newSurvey]**）。

![](assets/s_ncs_admin_survey_select_template.png)

表單頁面是使用特殊編輯器建立的，可讓您定義和設定（文字）輸入欄位、選擇欄位（清單、核取方塊等） 和靜態元素(影像、HTML內容等)。 可在「容器」中收集資料，並根據需求進行編排。 [深入瞭解](#adding-questions))。

>[!NOTE]
>
>如需如何定義網頁表單的內容及建立熒幕版面配置的詳細資訊，請參閱[此檔案](../../web/using/about-web-forms.md)。

## 新增欄位 {#adding-fields}

表單中的欄位可讓使用者輸入資訊並選取選項。 對於表單中的每個頁面，它們都是使用&#x200B;**[!UICONTROL Add using the wizard]**&#x200B;功能表透過工具列中的第一個按鈕建立的。

![](assets/s_ncs_admin_survey_add_field_menu.png)

>[!NOTE]
>
>您也可以使用滑鼠右鍵並插入輸入區域。 依照預設，區域會插入在所選樹狀結構的末端。 使用工具列中的箭頭來移動它。

### 欄位型別 {#types-of-fields}

將欄位新增至調查時，您需要選取其型別。 可以使用以下選項：

1. **[!UICONTROL Answer a question]**：此選項可讓您宣告新欄位（稱為「已封存的欄位」）以儲存答案。 在此情況下，會儲存所有收集的值，即使參與者多次填寫表單亦然。 此儲存模式僅適用於&#x200B;**調查**。 [了解更多](../../surveys/using/managing-answers.md#storing-collected-answers)。
1. **[!UICONTROL Edit a recipient]**：此選項可讓您選取資料庫中的欄位。 在這種情況下，使用者答案將儲存在此欄位中。 對於每個參與者，僅會保留最後儲存的值，並將其新增至設定檔資料。
1. **[!UICONTROL Add a variable]**：此選項可讓您建立安裝程式，讓資訊不會儲存在資料庫中。 區域變數可以宣告到上游。 您也可以在建立欄位時直接新增它們。
1. **[!UICONTROL Import an existing question]**：此選項可讓您匯入在其他調查中建立的現有問題。

   >[!NOTE]
   >
   >儲存模式與欄位匯入在[此區段](../../surveys/using/managing-answers.md#storing-collected-answers)中有詳細說明。

要新增的欄位性質（下拉式清單、文字欄位、核取方塊等） 會調整成選取的儲存模式。 您可以使用&#x200B;**[!UICONTROL General]**&#x200B;索引標籤的&#x200B;**[!UICONTROL Type]**&#x200B;欄位來變更它，但請確保與資料型別保持一致。

![](assets/s_ncs_admin_survey_change_type.png)

[此區段](../../web/using/about-web-forms.md)中詳細說明了各種型別的可用欄位。

## 調查特定元素 {#survey-specific-elements}

線上調查是以Web應用程式功能為基礎。 下文將詳細說明調查特定功能。

### 多選 {#multiple-choice}

對於&#x200B;**[!UICONTROL Multiple choice]**&#x200B;型別控制項，您可以定義最小和最大選擇數目。 例如，此選項可讓您強制從可用選項中選取至少&#x200B;**2**&#x200B;個值和最多&#x200B;**4**&#x200B;個值：

![](assets/s_ncs_admin_survey_multichoice_ex1.png)

如果選取範圍的數目太大或太小，則會顯示適當的訊息。

![](assets/s_ncs_admin_survey_multichoice_ex2.png)

>[!NOTE]
>
>在此情況下，會使用核取方塊來選取選項。 如果只有一個選項，則會使用選項按鈕。

對應的設定如下：

![](assets/s_ncs_admin_survey_multichoice_ex3.png)

此外，此輸入欄位的儲存位置必須是&#x200B;**[!UICONTROL Multiple values]**&#x200B;型別&#x200B;**封存欄位**：

![](assets/s_ncs_admin_survey_multiple_values_field.png)

>[!CAUTION]
>
>* 此功能僅適用於&#x200B;**調查**&#x200B;型別表單。
>* 此選項與隨機問題顯示不相容。 [了解更多](#adding-questions)。

### 新增問題 {#adding-questions}

有兩種型別的容器：標準容器和問題容器。 標準容器可用來設定頁面版面以及在頁面中的條件式顯示。 [了解更多](../../web/using/about-web-forms.md)。

使用&#x200B;**問題**&#x200B;容器將問題新增至頁面，並在階層中插入下列可能的答案。 使用者對於這類容器中所提問題的回應，可以在報表中分析。

>[!CAUTION]
>
>請勿在階層中的另一個&#x200B;**問題**&#x200B;容器下方插入&#x200B;**問題**&#x200B;容器。

![](assets/s_ncs_admin_question_label.png)

在標籤欄位中輸入問題的標籤。 在這種情況下，將會套用表單樣式表中的樣式。 選取&#x200B;**[!UICONTROL Enter the title in HTML format]**&#x200B;選項加以個人化。 這將為您提供HTML編輯器的存取權。

>[!NOTE]
>
>如需使用HTML編輯器的詳細資訊，請參閱[此檔案](../../web/using/about-web-forms.md)。

例如：

![](assets/s_ncs_admin_survey_containers_qu_arbo.png)

在上述範例中，演算將如下所示：

![](assets/s_ncs_admin_survey_containers_qu_ex.png)

>[!NOTE]
>
>每個問題都有一個&#x200B;**問題**&#x200B;型別容器。

您可以透過Adobe Campaign啟用隨機抽取問題。 然後，可以在位於設定視窗底部的欄位中，指定要在頁面中顯示的問題數。

![](assets/s_ncs_admin_survey_containers_qu_display.png)

轉譯看起來會像這樣：

![](assets/s_ncs_admin_survey_containers_qu_display_rendering.png)

重新整理頁面時，顯示的問題不同。

>[!CAUTION]
>
>當您隨機顯示問題（頁面上勾選&#x200B;**[!UICONTROL Display randomly]**&#x200B;選項）時，請注意不要使用一或多個必須選取的多重選取問題。
