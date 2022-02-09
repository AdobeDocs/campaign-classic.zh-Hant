---
product: campaign
title: 設定報告存取權
description: 設定報告存取權
exl-id: 1e5ab922-481c-4dce-a05e-a58408002e24
source-git-commit: 81716a30a57d3ed8542b329d5fb9b0443fd4bf31
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 1%

---

# 設定報告存取權{#configuring-access-to-the-report}

![](../../assets/common.svg)

## 報表顯示上下文 {#report-display-context}

使用 **[!UICONTROL Display]** 頁籤。 訪問報告取決於其選擇類型、顯示條件和訪問授權。

### 選擇類型 {#selection-type}

對報告的訪問可限於特定上下文或提供空間，例如遞送、收件人、選擇的收件人等。 此訪問在 **[!UICONTROL Selection type]** 的下界 **[!UICONTROL Display]** 頁籤。

![](assets/s_ncs_advuser_report_visibility_4.png)

* **[!UICONTROL Single selection]** :僅當選擇特定實體時，才可訪問報告。
* **[!UICONTROL Multiple selection]** :選擇多個實體時，將訪問報告。
* **[!UICONTROL Global]** :可通過 **[!UICONTROL Reports]** 頁籤。

### 顯示順序 {#display-sequence}

的 **[!UICONTROL Sequence]** 欄位中，您可以輸入指定清單中報表顯示順序的數字值。

預設情況下，報告按相關性顯示：在此欄位中輸入的值允許您將報表從最大（最高值）排序為與最小（最小值）相關。

您可以根據需要選擇要使用的比例：1到10,0到100,-10到10等。

### 顯示條件 {#display-conditions}

您還可以通過查詢條件顯示報告。

![](assets/s_ncs_advuser_report_visibility_5.png)

在以下示例中，如果主市場活動渠道是電子郵件，則將顯示報表。

![](assets/s_ncs_advuser_report_visibility_6.png)

這意味著，如果市場活動的主要渠道是直郵，則市場活動報告中將不提供此報告。

### 訪問授權 {#access-authorization}

報告可以與其他運算子共用。

要使報告可訪問，請選擇 **[!UICONTROL Report shared with other operators]** 的雙曲餘切值。 如果未選擇此選項，則只有建立報告的操作員才能訪問報告。

還可以與通過授權窗口添加的特定運算子或運算子組共用報告。

![](assets/s_ncs_advuser_report_visibility_8.png)

### 定義篩選選項 {#defining-the-filtering-options}

的 **[!UICONTROL Reports]** 頁籤顯示平台中所有可用的報告，並且連接的操作員對其具有訪問權限。

預設情況下，它們按相關性排序，但可以應用其他類型的篩選器：按年齡等按字母順序排列。

您還可以根據報告類別篩選顯示：

![](assets/report_ovv_select_type.png)

要定義報表的類別，請通過 **[!UICONTROL Display]** 頁籤，如下所示：

![](assets/report_select_category.png)

您可以在此處輸入新類別，並將其添加到可用類別清單中。 匹配枚舉將自動更新。

## 建立指向報表的連結 {#creating-a-link-to-a-report-}

可以通過樹的特定節點（如清單、收件人、傳遞等）訪問報告。 為此，只需建立一個指向相關報告的連結，並指定要使其可用的實體。

例如，我們將建立指向報告的連結，以便通過收件人清單訪問報告。

1. 按一下 **[!UICONTROL New]** 選擇 **[!UICONTROL Create a link to an existing report]** 的子菜單。

   ![](assets/s_ncs_advuser_report_wizard_link_01.png)

1. 選擇要建立連結以使用下拉清單的報表。 在此示例中，我們將選擇 **按國家分列** 報告。

   ![](assets/s_ncs_advuser_report_wizard_link_02.png)

1. 輸入標籤並選擇方案。 在此示例中，我們將選擇收件人清單表。

   ![](assets/s_ncs_advuser_report_wizard_link_03.png)

   這意味著可以通過任何收件人清單訪問報告，並且統計資訊將與選定清單中的收件人有關。

1. 保存並顯示報告。
1. 輸入連結鍵。 在這種情況下，「資料夾」連結的外鍵。

   ![](assets/s_ncs_advuser_report_wizard_link_04.png)

1. 發佈報告。
1. 轉到您的收件人清單之一，然後按一下 **[!UICONTROL Reports]** 連結：您剛建立的報告可訪問。

   ![](assets/s_ncs_advuser_report_wizard_link_05.png)

## 預覽報表 {#preview-of-the-report}

在發佈報告之前，請確保在 **[!UICONTROL Preview]** 頁籤。

![](assets/s_ncs_advuser_report_preview_01.png)

要顯示報表的預覽，請選擇 **[!UICONTROL Global]** 或 **[!UICONTROL Selection]** 的雙曲餘切值。

根據報告的顯示設定選擇這兩個選項。 如果顯示設定為 **[!UICONTROL Global]**，需要選擇 **[!UICONTROL Global]** 的下界。 如果顯示設定為 **[!UICONTROL Single selection]** 或 **[!UICONTROL Multiple selection]**，也請參見Wiki頁。 **[!UICONTROL Selection]** 必須選擇預覽選項。

有關此內容的詳細資訊，請參閱 [報表顯示上下文](#report-display-context)。

特定設定使您能夠控制錯誤。 的 **_uuid** 在報表的URL中找到。 可以添加 **&amp;預覽** 或 **&amp;調試** 的子菜單。

要瞭解有關這些設定的詳細資訊，請參閱 **定義Web窗體屬性** 的下界 [Web表單](../../web/using/about-web-forms.md) 一章。

## 發佈報表 {#publishing-the-report}

必須發佈報告，以便與其他操作員共用這些報告並將其顯示在可用報告清單中(另請參閱 [報表顯示上下文](#report-display-context))。 每次更改報告時，必須再次執行此操作。

1. 通過按一下 **[!UICONTROL Publish]** 的子菜單。

   ![](assets/s_ncs_advuser_report_publish_01.png)

1. 按一下 **[!UICONTROL Start]** 的子菜單。

   ![](assets/s_ncs_advuser_report_publish_02.png)

1. 按一下 **[!UICONTROL Enlarge]** 表徵圖以在Web瀏覽器中開啟報表。
