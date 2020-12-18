---
solution: Campaign Classic
product: campaign
title: 建立登錄頁面
description: 建立登錄頁面
audience: web
content-type: reference
topic-tags: editing-html-content
translation-type: tm+mt
source-git-commit: 972885c3a38bcd3a260574bacbb3f507e11ae05b
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 3%

---


# 建立登錄頁面{#creating-a-landing-page}

## 關於建立著陸頁面{#about-landing-pages-creation}

此使用案例說明如何使用Digital Editor從Adobe Campaign主控台建立著陸頁面。

開始在Adobe Campaign中設定「著陸頁面」之前，請確定您有&#x200B;**一或多個範本**&#x200B;來代表HTML頁面。

此使用案例的主要目的是使用DCE中的函式，讓「著陸頁面」表單欄位與Adobe Campaign中的內部欄位對應。

## 建立著陸頁面{#creating-the-landing-page}

若要建立新的著陸頁面類型Web應用程式，請使用下列步驟：

1. 前往&#x200B;**[!UICONTROL Campaigns]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Web application]**&#x200B;連結，然後按一下&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。
1. 選擇&#x200B;**[!UICONTROL New landing page]**&#x200B;模板並輸入標籤，然後按一下&#x200B;**[!UICONTROL Save]**。

   ![](assets/dce_uc1_newlandingpage.png)

1. 按一下&#x200B;**[!UICONTROL Edit]**&#x200B;頁籤。
1. 刪除&#x200B;**End**&#x200B;活動。
1. 在&#x200B;**[!UICONTROL Storage]**&#x200B;活動後添加&#x200B;**[!UICONTROL Page]**&#x200B;活動。
1. 編輯&#x200B;**第2頁**&#x200B;活動，然後取消選中&#x200B;**[!UICONTROL Properties]**&#x200B;頁籤中的&#x200B;**[!UICONTROL Activate outbound transitions]**&#x200B;選項。

   ![](assets/dce_uc1_transition.png)

1. 儲存變更。

接著，您將取得下列順序：

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>有關建立Web應用程式的詳細資訊，請參閱[本節](../../web/using/creating-a-new-web-application.md)。

## 步驟1 —— 選擇並載入模板{#step-1---selecting-and-loading-templates}

在本節中，我們將介紹如何為Web應用程式的每個頁面導入&#x200B;**HTML內容**。

範本必須包含：

* an **HTML** file(mandatory)
* 一或多個&#x200B;**CSS**&#x200B;檔案（選用）
* 一個或多個&#x200B;**images**（可選）

若要在第一頁載入範本，請套用下列步驟：

1. 開啟Web應用程式的前一個&#x200B;**[!UICONTROL Page]**&#x200B;活動。
1. 選擇&#x200B;**[!UICONTROL From a file]**&#x200B;以擷取您的內容範本。

   ![](assets/dce_uc1_selectmodel.png)

1. 選取要使用的HTML檔案。
1. 按一下&#x200B;**開啟**&#x200B;啟動導入。

   載入期間，會顯示共用檔案的清單。 匯入系統會檢查連結至所選HTML的所有檔案（CSS、影像等）是否在此。

   匯入完成後，按一下&#x200B;**[!UICONTROL Close]**&#x200B;按鈕。

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >您必須等到收到下列訊息後，才能關閉：**[!UICONTROL The external resources have been successfully published]**。

1. 按一下&#x200B;**[!UICONTROL Properties]**&#x200B;頁籤。
1. 為每個頁輸入&#x200B;**label**(例如：第1頁=收集，第2頁=謝謝)。

   ![](assets/dce_uc1_pagelabel.png)

對插入Web應用程式中的每個頁面套用這些步驟。

>[!CAUTION]
>
>**DCE會為載入的HTML頁面執行JavaScript程式碼。** HTML範本中可能出現在Adobe Campaign介面中的JavaScript錯誤。這些錯誤與編輯器無關。 要檢查導入的檔案中是否沒有錯誤，建議在將檔案導入DCE之前，先在瀏覽器(Internet Explorer / Firefox / Chrome)中測試這些錯誤。

## 步驟2 —— 配置內容{#step-2---configuring-the-content}

在本節中，我們將調整導入的內容，並將資料庫的欄位連結到網頁的形式。 先前建立的Web應用程式為：

![](assets/dce_uc1_lp_enchainement.png)

### 修改內容{#modifying-content}

首先，我們來更改頁面的顏色。 操作步驟：

1. 開啟&#x200B;**[!UICONTROL Collection]**&#x200B;頁面。
1. 按一下背景。
1. 按一下右側的&#x200B;**背景顏色**。
1. 選擇新的背景顏色。
1. 按一下&#x200B;**確定**&#x200B;確認更改。

   ![](assets/dce_uc1_changecolor.png)

1. 套用這些相同的程式以變更按鈕的顏色

   ![](assets/dce_uc1_finalcolor.png)

### 連結表單域{#linking-form-fields}

為了保存提供的資訊，我們將將頁面中的欄位連結到資料庫中的欄位。

1. 選擇表單欄位。
1. 編輯編輯器右側的&#x200B;**[!UICONTROL Field]**&#x200B;部分。
1. 選擇要連結到選定欄位的資料庫欄位。

   ![](assets/dce_uc1_mapping.png)

1. 對頁面上的每個欄位重複此程式。

您可以將欄位設為必填：例如，按一下&#x200B;**[!UICONTROL Email]**&#x200B;欄位，然後啟用&#x200B;**Mandatory**&#x200B;選項。

![](assets/dce_uc1_fieldmandatory.png)

### 建立連至下一頁{#creating-a-link-to-the-next-page}的連結

此步驟是必要的，因為它將允許Web應用程式確定後續步驟的順序：將收集的資料儲存在資料庫中，然後顯示下一頁（**感謝**&#x200B;頁）。

1. 選擇&#x200B;**[!UICONTROL Collection]**&#x200B;頁面的&#x200B;**[!UICONTROL Send it!]**&#x200B;按鈕。
1. 按一下&#x200B;**[!UICONTROL Action]**&#x200B;下拉菜單。
1. 選擇&#x200B;**[!UICONTROL Next page]**&#x200B;操作。

   ![](assets/dce_uc1_actionbouton.png)

### 插入個人化欄位 {#inserting-a-personalization-field}

此步驟可讓您個人化「感謝」頁面。 操作步驟：

1. 開啟&#x200B;**[!UICONTROL Thank you]**&#x200B;頁面。
1. 將游標置於要插入收件人名字的文本區域。
1. 在工具欄的&#x200B;**[!UICONTROL Insert]**&#x200B;菜單中選擇&#x200B;**[!UICONTROL Personalization field]**。
1. 選擇名字。

   ![](assets/dce_uc1_persochamp.png)

個人化欄位在編輯器中有黃色背景。

![](assets/dce_uc1_edit_champperso.png)

## 步驟3 —— 發佈內容{#step-3---publishing-content}

內容會從Web應用程式儀表板發佈。 按一下&#x200B;**[!UICONTROL Publish]**&#x200B;按鈕以運行它。

![](assets/dce_uc1_pub_dashboard.png)

在發佈期間，將顯示日誌。 出版系統會分析Web應用程式中找到的所有內容

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>在發佈日誌中，警告和錯誤按活動排序。

現在可使用表格：其URL可在應用程式控制面板中存取，並可傳送給收件者。
