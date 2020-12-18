---
solution: Campaign Classic
product: campaign
title: 建立調查的關鍵步驟
description: 使用Campaign建立您的第一個調查
audience: web
content-type: reference
topic-tags: online-surveys
translation-type: tm+mt
source-git-commit: e76eb171aac1f7088ff8647f99c928ec349b24fc
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 1%

---


# 建立調查的關鍵步驟{#getting-started-with-surveys}

以下是使用下列範本，快速概述建立簡單調查的主要步驟：

![](assets/s_ncs_admin_survey_result.png)

這些步驟包括：

1. [步驟1 —— 建立調查](#step-1---creating-a-survey),
1. [步驟2 —— 選擇範本](#step-2---selecting-the-template),
1. [步驟3 —— 建立調查](#step-3---building-the-survey),
1. [步驟4 —— 建立頁面內容](#step-4---creating-the-page-content),
1. [步驟5 —— 儲存調查資料](#step-5---storing-the-survey-data-),
1. [步驟6 —— 發佈頁面](#step-6---publishing-the-pages),
1. [步驟7 —— 分享您的線上調查](#step-7---sharing-your-online-survey)。

## 步驟1 —— 建立調查{#step-1---creating-a-survey}

若要建立新調查，請前往&#x200B;**[!UICONTROL Campaigns]**&#x200B;或&#x200B;**[!UICONTROL Profiles and targets]**&#x200B;標籤，然後按一下&#x200B;**[!UICONTROL Web Applications]**&#x200B;功能表。 按一下表單清單上方的&#x200B;**[!UICONTROL Create]**&#x200B;按鈕。

![](assets/s_ncs_admin_survey_create.png)

## 步驟2 —— 選擇模板{#step-2---selecting-the-template}

選取調查範本，然後為調查指定名稱。 使用者不會看到此名稱，但可讓調查在Adobe Campaign中識別。 按一下&#x200B;**[!UICONTROL Save]**，將調查新增至Web應用程式清單。

![](assets/s_ncs_admin_survey_wz_00.png)

## 步驟3 —— 建立調查{#step-3---building-the-survey}

調查是以下元素所在的圖形建立：建立內容的頁面、資料預載和儲存步驟，以及測試階段。 指令碼和查詢也可以插入。

若要建立圖表，請按一下調查的&#x200B;**[!UICONTROL Edit]**&#x200B;表單。

調查必須包含&#x200B;**至少**&#x200B;下列三個元件：頁面、儲存方塊和結束頁面。

* 若要建立頁面，請在編輯器的左側區段中選取&#x200B;**[!UICONTROL Page]**&#x200B;物件，並將它放入中間區段，如下所示：

   ![](assets/s_ncs_admin_survey_new_page.png)

* 接著，選取&#x200B;**[!UICONTROL Storage]**&#x200B;物件，並將它置於頁面的輸出轉場中。
* 最後，選擇&#x200B;**[!UICONTROL End]**&#x200B;對象並將其放置在儲存盒的輸出過渡的末尾，以獲得以下圖：

   ![](assets/s_ncs_admin_survey_end.png)

## 步驟4 —— 建立頁面內容{#step-4---creating-the-page-content}

在以下範例中，我們使用&#x200B;**[!UICONTROL Page (v5 compatibility)]**&#x200B;類型頁面。 此類型的頁面可透過&#x200B;**[!UICONTROL Edit]**&#x200B;標籤的進階功能表存取。

![](assets/s_ncs_admin_survey_pagev5.png)

* 新增輸入欄位

   若要建立頁面內容，您必須加以編輯：要執行此操作，請按兩下&#x200B;**[!UICONTROL Page]**&#x200B;對象。 按一下工具列中的第一個圖示，以開啟欄位建立精靈。 要為要儲存在收件人配置檔案的匹配欄位中的用戶名建立條目欄位，請選擇&#x200B;**[!UICONTROL Edit a recipient]**。

   ![](assets/s_ncs_admin_survey_add_field_menu.png)

   按一下&#x200B;**[!UICONTROL Next]**&#x200B;按鈕以選擇資料庫中資料儲存的欄位。 在本例中，為「姓氏」欄位。

   ![](assets/s_ncs_admin_survey_choose_field.png)

   按一下&#x200B;**[!UICONTROL Finish]**&#x200B;確認欄位建立。

   預設情況下，當資訊儲存在資料庫中已存在的欄位中時，該欄位將使用選定欄位的名稱，即：在此範例中為「姓氏」。 您可以修改此標籤，如下所示：

   ![](assets/s_ncs_admin_survey_change_label.png)

   現在，請為使用者帳號建立參加項目欄位。 重複該操作，並選擇「帳戶號」。 欄位。

   請套用相同的程式，為使用者新增欄位以輸入電子郵件地址。

* 要建立問題，請按一下右鍵樹中的最後一個元素，然後選擇&#x200B;**[!UICONTROL Containers > Question]** ，或按一下&#x200B;**[!UICONTROL Containers]**&#x200B;表徵圖並選擇&#x200B;**[!UICONTROL Question]**。

   ![](assets/s_ncs_admin_survey_add_qu.png)

   輸入問題的標籤，並將答案欄位插入為問題的子分支。 若要這麼做，在建立答案欄位時，必須選取連結至問題的節點。 使用&#x200B;**[!UICONTROL Selection controls]**&#x200B;圖示或按一下滑鼠右鍵，新增&#x200B;**[!UICONTROL drop-down listx]**，如下所示：

   ![](assets/s_ncs_admin_survey_add_list.png)

   選擇儲存空間：選擇枚舉欄位以自動檢索值（在本例中為電子郵件格式）。

   ![](assets/s_ncs_admin_survey_add_itz_list.png)

   在&#x200B;**[!UICONTROL General]**&#x200B;標籤中，按一下&#x200B;**[!UICONTROL Initialize the list of values from the database]**&#x200B;連結：值表會自動輸入。

   ![](assets/s_ncs_admin_survey_add_value.png)

   按一下&#x200B;**[!UICONTROL OK]**&#x200B;關閉編輯器，按一下&#x200B;**[!UICONTROL Save]**&#x200B;保存更改。

   >[!NOTE]
   >
   >由於&#x200B;**[!UICONTROL Advanced]**&#x200B;標籤中的選項，您可以針對每個欄位或問題調整頁面版面以符合您的需求。 調查畫面的版面配置詳見[本節](../../web/using/about-web-forms.md)。

   在詳細資料畫面中，按一下&#x200B;**[!UICONTROL Preview]**&#x200B;標籤，以檢視您剛建立之調查的轉譯。

   ![](assets/s_ncs_admin_survey_preview.png)

## 步驟5 —— 儲存調查資料{#step-5---storing-the-survey-data-}

儲存方塊可讓您將使用者回應儲存在資料庫中。 必須選擇協調鍵以標識資料庫中已有的配置檔案。

要執行此操作，請編輯該框並選擇儲存資料時將用作協調鍵的欄位。

在以下範例中，在儲存（確認）時，如果描述檔儲存在與表單中輸入的帳戶號碼相同的資料庫中，描述檔將會更新。 如果配置檔案不存在，則將建立該配置檔案。

![](assets/s_ncs_admin_survey_save_edit.png)

按一下&#x200B;**[!UICONTROL OK]**&#x200B;以確認，然後按一下&#x200B;**[!UICONTROL Save]**&#x200B;以儲存調查

## 步驟6 —— 發佈頁面{#step-6---publishing-the-pages}

若要讓使用者能夠存取HTML頁面，應用程式必須可供使用。 它不再必須處於編輯階段，而是在生產階段。 若要將調查放在生產中，您必須發佈調查。 操作步驟：

* 按一下調查控制面板上方的&#x200B;**[!UICONTROL Publish]**&#x200B;按鈕。
* 按一下&#x200B;**[!UICONTROL Start]**&#x200B;啟動出版物並關閉嚮導。

   ![](assets/s_ncs_admin_survey_start_publ.png)

   調查的狀態會變更為：**Online**。

   ![](assets/survey_published.png)

## 步驟7 —— 分享您的線上調查{#step-7---sharing-your-online-survey}

調查投入生產後，即可從伺服器存取，而您也可以提供。 存取調查的URL會顯示在控制面板上。

![](assets/survey_url_from_dashboard.png)

若要傳送調查，您可以傳送包含目標人口之存取連結的訊息，或將調查存取URL放在網頁上。

然後，您可以透過報表和記錄來監控使用者回應。 請參閱[回應追蹤](../../web/using/publish--track-and-use-collected-data.md#response-tracking)。

>[!CAUTION]
>
>公開URL包含調查的內部名稱。 修改內部名稱時，URL會自動更新：調查的所有連結也必須更新。
>
>如果已傳送包含表單連結的傳送，此連結將不再有效。

