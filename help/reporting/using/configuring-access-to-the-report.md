---
title: 設定報表存取權
seo-title: 設定報表存取權
description: 設定報表存取權
seo-description: null
page-status-flag: never-activated
uuid: d32d9805-f84f-457f-b37b-a8278642336a
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: reporting
content-type: reference
topic-tags: creating-new-reports
discoiquuid: dd50ca25-8fa2-48fa-84cc-a63e476701a0
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 1c86322fa95aee024f6c691b61a10c21a9a22eb7

---


# 設定報表存取權{#configuring-access-to-the-report}

## 報表顯示內容 {#report-display-context}

使用標籤定義Adobe Campaign平台中報表的顯示內 **[!UICONTROL Display]** 容。 報表的存取權視其選擇類型、顯示條件及存取授權而定。

### 選擇類型 {#selection-type}

對報表的存取權限可限定為特定內容或選件空間，例如傳送、收件者、選擇的收件者等。 此訪問在頁籤的 **[!UICONTROL Selection type]** 部分中配 **[!UICONTROL Display]** 置。

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** :只有在選取特定實體時，才可存取報表。
* **[!UICONTROL Multiple selection]** :選取數個實體時，即可存取報表。
* **[!UICONTROL Global]** :報表可透過「報表」宇宙中可用報表的清單存取。

### 顯示順序 {#display-sequence}

欄位 **[!UICONTROL Sequence]** 可讓您輸入數值，指定清單中報表的顯示順序。

依預設，報表會依相關性顯示：在此欄位中輸入的值可讓您將報表從最高（最高值）排序至最小（最小值）相關。

您可以根據需求選擇要使用的比例：1到10、0到100、-10到10等。

### 顯示條件 {#display-conditions}

您也可以透過查詢來限制報表的顯示。

![](assets/s_ncs_advuser_report_visibility_5.png)

在下列範例中，如果主要促銷活動渠道是電子郵件，則會顯示報表。

![](assets/s_ncs_advuser_report_visibility_6.png)

這表示如果促銷活動的主渠道是直接郵件，則促銷活動報表中將無法使用報表。

### 存取授權 {#access-authorization}

報表可與其他運算子共用。

若要讓報表可供存取，請選取 **[!UICONTROL Report shared with other operators]** 選項。 如果未選取此選項，則只有建立報表的運算子才能存取報表。

您也可以將報表共用給透過授權視窗新增的特定運算元或運算元群組。

![](assets/s_ncs_advuser_report_visibility_8.png)

### 定義篩選選項 {#defining-the-filtering-options}

宇宙 **[!UICONTROL Reports]** 會顯示平台中所有可用的報表，且連線的營運商擁有存取權。

依預設，這些篩選依相關性排序，但您可以套用其他類型的篩選：字母順序，依年齡等

您也可以根據報表類別篩選顯示：

![](assets/report_ovv_select_type.png)

要定義報表的類別，請通過頁籤選 **[!UICONTROL Display]** 擇它，如下所示：

![](assets/report_select_category.png)

您可以在此處輸入新類別，並將其添加到可用類別的清單中。 匹配枚舉會自動更新。

## 建立報表連結 {#creating-a-link-to-a-report-}

可讓報表透過樹狀結構的特定節點存取，例如清單、收件者、傳送等。 若要這麼做，只需建立相關報表的連結，並指定要提供該報表的實體。

例如，我們將建立報表的連結，以便透過收件者清單加以存取。

1. 按一 **[!UICONTROL New]** 下並選 **[!UICONTROL Create a link to an existing report]** 取報表建立精靈。

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. 選擇您要建立使用下拉式清單之連結的報表。 在此範例中，我們將選取「依國家／地 **區劃分** 」報表。

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. 輸入標籤並選擇方案。 在此範例中，我們將選取收件者清單表格。

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   這表示報表可透過任何收件者清單存取，而統計資料將與選定清單中的收件者有關。

1. 儲存和顯示報表。
1. 輸入連結鍵。 在此情況下，「資料夾」連結的外鍵。

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. 發佈您的報表。
1. 前往其中一個收件者清單，然後按一下 **[!UICONTROL Reports]** 連結：您剛建立的報表可供存取。

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## 預覽報表 {#preview-of-the-report}

發佈報表之前，請確定報表已正確顯示在標 **[!UICONTROL Preview]** 簽中。

![](assets/s_ncs_advuser_report_preview_01.png)

若要顯示報表的預覽，請選取 **[!UICONTROL Global]** 或選 **[!UICONTROL Selection]** 項。

這兩個選項會根據報表的顯示設定而選取。 如果顯示設 **[!UICONTROL Global]**&#x200B;定為，則需要選取預 **[!UICONTROL Global]** 覽選項。 如果顯示設定為 **[!UICONTROL Single selection]** 或 **[!UICONTROL Multiple selection]**，則必 **[!UICONTROL Selection]** 須選擇預覽選項。

如需詳細資訊，請參閱報 [告顯示內容](#report-display-context)。

特定設定可讓您控制錯誤。 在報 **表的URL中可找到_uuid** 設定。 您可以新 **增&amp;_preview****或&amp;_debug** 設定。

若要進一步瞭解這些設定，請參閱「 **Web表格」一章的「定義Web表格屬性** 」 [一節](../../web/using/about-web-forms.md) 。

## 發佈報表 {#publishing-the-report}

發佈報表是必備的，以便與其他運算子共用並顯示在可用報表清單中(也請參閱報 [表顯示內容](#report-display-context))。 每次變更報表時，都必須重新執行此操作。

1. 按一下工具列中的，以開 **[!UICONTROL Publish]** 啟發佈精靈。

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. 按一 **[!UICONTROL Start]** 下以發佈。

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. 按一下 **[!UICONTROL Enlarge]** 圖示，在網頁瀏覽器中開啟報表。

