---
product: campaign
title: 設定登陸頁面
description: 設定登陸頁面
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Landing Pages
exl-id: 71c737c2-b0d6-4ae8-a5df-28a08dff82d7
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 3%

---

# 設定登陸頁面{#creating-a-landing-page}



## 關於建立登入頁面 {#about-landing-pages-creation}

此使用案例顯示如何使用數位編輯器從Adobe Campaign主控台建立登入頁面。

在Adobe Campaign中開始設定登入頁面之前，請確定您已 **一或多個範本** 表示HTML頁面。

此使用案例的主要目的是使用DCE中的函式，讓登入頁面表單欄位對應至Adobe Campaign中的內部欄位。

## 建立登入頁面 {#creating-the-landing-page}

若要建立新的登入頁面型別Web應用程式，請使用下列步驟：

1. 前往 **[!UICONTROL Campaigns]** 標籤並按一下 **[!UICONTROL Web application]** 連結，然後按一下 **[!UICONTROL Create]** 按鈕。
1. 選取 **[!UICONTROL New landing page]** 範本並輸入標籤，然後按一下 **[!UICONTROL Save]**.

   ![](assets/dce_uc1_newlandingpage.png)

1. 按一下 **[!UICONTROL Edit]** 標籤。
1. 刪除 **結束** 活動。
1. 新增 **[!UICONTROL Page]** 活動晚於 **[!UICONTROL Storage]** 活動。
1. 編輯 **第2頁** 活動，然後取消勾選 **[!UICONTROL Activate outbound transitions]** 中的選項 **[!UICONTROL Properties]** 標籤。

   ![](assets/dce_uc1_transition.png)

1. 儲存變更.

接著，您會取得下列排序：

![](assets/dce_uc1_edition_activity.png)

>[!NOTE]
>
>如需建立Web應用程式的詳細資訊，請參閱 [本節](creating-a-new-web-application.md).

## 步驟1 — 選取和載入範本 {#step-1---selecting-and-loading-templates}

在本節中，我們將瞭解如何 **匯入HTML內容** 網頁應用程式的每個頁面。

範本必須包含：

* 一個 **HTML** 檔案（必要）
* 一或多個 **CSS** 檔案（選擇性）
* 一或多個 **影像** （選擇性）

若要在第一頁載入範本，請套用下列步驟：

1. 開啟第一個 **[!UICONTROL Page]** 網頁應用程式的活動。
1. 選取 **[!UICONTROL From a file]** 以擷取您的內容範本。

   ![](assets/dce_uc1_selectmodel.png)

1. 選取要使用的HTML檔案。
1. 按一下 **開啟** 以開始匯入。

   在載入期間，會顯示共用檔案的清單。 匯入系統會檢查連結至所選HTML的所有檔案（CSS、影像等）是否存在。

   按一下 **[!UICONTROL Close]** 按鈕。

   ![](assets/dce_uc1_import.png)

   >[!CAUTION]
   >
   >您必須等到收到下列訊息後再關閉： **[!UICONTROL The external resources have been successfully published]** .

1. 按一下 **[!UICONTROL Properties]** 標籤。
1. 輸入 **標籤** （例如：頁面1=收集，頁面2=感謝）。

   ![](assets/dce_uc1_pagelabel.png)

請針對Web應用程式中插入的每個頁面套用這些步驟。

>[!CAUTION]
>
>**DCE會針對載入的HTML頁面執行JavaScript程式碼。** HTML範本中的JavaScript錯誤，可能會顯示在Adobe Campaign介面中。 這些錯誤與編輯器無關。 若要檢查匯入的檔案中是否有錯誤，建議您在匯入檔案到DCE之前，先在網頁瀏覽器中測試這些檔案。

## 步驟2 — 設定內容 {#step-2---configuring-the-content}

在本節中，我們將調整匯入的內容，並將資料庫的欄位連結至網頁的形式。 先前建立的Web應用程式為：

![](assets/dce_uc1_lp_enchainement.png)

### 修改內容 {#modifying-content}

讓我們從變更頁面的顏色開始。 操作步驟：

1. 開啟 **[!UICONTROL Collection]** 頁面。
1. 按一下背景。
1. 按一下 **背景顏色** 在右側。
1. 選取新的背景顏色。
1. 按一下 **確定** 以確認變更。

   ![](assets/dce_uc1_changecolor.png)

1. 套用這些相同的程式以變更按鈕的顏色

   ![](assets/dce_uc1_finalcolor.png)

### 連結表單欄位 {#linking-form-fields}

我們將連結頁面中的欄位與資料庫中的欄位，以儲存提供的資訊。

1. 選取表單欄位。
1. 編輯 **[!UICONTROL Field]** 編輯器右側的區段。
1. 選取您要連結至所選欄位的資料庫欄位。

   ![](assets/dce_uc1_mapping.png)

1. 對頁面上的每個欄位重複此程式。

您可以將欄位設為必要欄位：例如，按一下 **[!UICONTROL Email]** 欄位，然後啟用 **強制** 選項。

![](assets/dce_uc1_fieldmandatory.png)

### 建立下一頁的連結 {#creating-a-link-to-the-next-page}

此步驟為必要步驟，因為它可讓Web應用程式決定後續步驟的順序：將收集的資料儲存在資料庫中，然後顯示下一頁(**感謝您** 頁面)。

1. 選取 **[!UICONTROL Send it!]** 的按鈕 **[!UICONTROL Collection]** 頁面。
1. 按一下 **[!UICONTROL Action]** 下拉式功能表。
1. 選取 **[!UICONTROL Next page]** 動作。

   ![](assets/dce_uc1_actionbouton.png)

### 插入個人化欄位 {#inserting-a-personalization-field}

此步驟可讓您個人化「感謝您」頁面。 操作步驟：

1. 開啟 **[!UICONTROL Thank you]** 頁面。
1. 將游標放在您要插入收件者名字的文字區域中。
1. 選取 **[!UICONTROL Personalization field]** 在 **[!UICONTROL Insert]** 工具列功能表。
1. 選取名字。

   ![](assets/dce_uc1_persochamp.png)

個人化欄位在編輯器中具有黃色背景。

![](assets/dce_uc1_edit_champperso.png)

## 步驟3 — 發佈內容 {#step-3---publishing-content}

內容會從Web應用程式儀表板發佈。 按一下 **[!UICONTROL Publish]** 按鈕來執行它。

![](assets/dce_uc1_pub_dashboard.png)

發佈期間會顯示記錄。 發佈系統會分析在網頁應用程式中找到的所有內容

![](assets/dce_uc1_pub_dashboard_journal.png)

>[!NOTE]
>
>在發佈記錄檔中，警告和錯誤會依活動排序。

此表單現已可用：其URL可在應用程式控制面板中存取，並可傳送給收件者。
