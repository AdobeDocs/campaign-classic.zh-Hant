---
product: campaign
title: 讀取清單
description: 深入瞭解閱讀清單工作流程活動
badge-v7-only: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7 only"
feature: Workflows, Targeting Activity
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 8debcd3d8fb883b3316cf75187a86bebf15a1d31
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 讀取清單{#read-list}



在工作流程中處理的資料可能來自已預先準備資料或預先結構化資料的清單（在先前的細分或檔案上傳後）。

此 **[!UICONTROL Read list]** 活動可讓您從工作流程工作表格的清單複製資料，例如來自查詢的資料。 然後便可在整個工作流程中存取。

要處理的清單可以明確指定、由指令碼計算或根據所選選項和中定義的引數動態本地化。 **[!UICONTROL Read list]** 活動。

![](assets/list_edit_select_option_01.png)

如果未明確指定清單，您必須提供清單作為範本使用，才能找出其結構。

![](assets/s_advuser_list_template_select.png)

設定清單選取範圍後，您就可以使用 **[!UICONTROL Edit query]** 保留一部分母體以供下一個工作流程使用的選項。

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>若要在讀取清單活動中建立篩選器，相關清單必須是「檔案」型別。

清單可直接在Adobe Campaign中建立，方法是透過 **[!UICONTROL Profiles and Targets > Lists]** 首頁的連結。 您也可以在工作流程中使用 **[!UICONTROL List update]** 活動。

**範例：排除傳送位址清單**

下列範例可讓您使用要排除在電子郵件傳遞目標之外的電子郵件地址清單。

![](assets/s_advuser_list_read_sample_1.png)

包含在以下的設定檔 **新連絡人** 資料夾必須是傳遞動作的目標。 要從目標中排除的電子郵件地址會儲存在外部清單中。 在我們的範例中，排除只需要電子郵件地址上的資訊。

1. 此 **新連絡人** 資料夾選擇查詢必須讓您載入所選設定檔的電子郵件地址，以便啟用與清單中資訊的對齊。

   ![](assets/s_advuser_list_read_sample_0.png)

1. 在此，清單儲存在 **清單** 會計算資料夾及其標籤。

   ![](assets/s_advuser_list_read_sample_2.png)

1. 若要從主要目標中排除外部清單的電子郵件地址，您必須設定排除活動並指定 **新連絡人** 資料夾中包含要保留的資料。 此集與排除活動之任何其他入站集之間的聯合資料將從目標中刪除。

   ![](assets/s_advuser_list_read_sample_3.png)

   排除規則是在編輯工具的中央區段中設定。 按一下 **[!UICONTROL Add]** 按鈕來定義要套用的排除型別。

   您可以根據活動傳入轉變的數量，定義數個排除專案。

1. 在 **[!UICONTROL Exclusion set]** 欄位中，選取 **[!UICONTROL Read list]** 活動：此活動中的資料將從主要集中排除。

   在我們的範例中，加入時會有排除專案：清單中包含的資料會透過包含電子郵件地址的欄位，與主要集的資料進行調解。 若要設定聯結，請選取 **[!UICONTROL Joins]** 在 **[!UICONTROL Change dimension]** 欄位。

   ![](assets/s_advuser_list_read_sample_4.png)

1. 然後，選取與兩組（「來源」和「目的地」）中電子郵件地址相對應的欄位。 然後會連結欄，而且其電子郵件地址在匯入地址清單中的收件者將從目標中排除。
