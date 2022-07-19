---
product: campaign
title: 讀取清單
description: 瞭解有關「讀取」清單工作流活動的詳細資訊
feature: Workflows, Targeting Activity
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 讀取清單{#read-list}

![](../../assets/v7-only.svg)

在工作流中處理的資料可以來自這樣的清單，即資料已預先準備或結構化（在先前的分段或檔案上載之後）。

的 **[!UICONTROL Read list]** 「活動」(Activity)允許您從工作流工作表的清單中複製資料，如查詢中的資料。 然後，可以在整個工作流中訪問它。

可以根據所選選項和在 **[!UICONTROL Read list]** 的子菜單。

![](assets/list_edit_select_option_01.png)

如果未明確指定清單，則必須提供一個清單作為模板來查找其結構。

![](assets/s_advuser_list_template_select.png)

配置清單選擇後，可以使用 **[!UICONTROL Edit query]** 的子菜單。

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>要能夠在讀取清單活動中建立篩選器，相關清單必須是「檔案」類型。

這些清單可通過 **[!UICONTROL Profiles and Targets > Lists]** 的子菜單。 也可以在工作流中使用 **[!UICONTROL List update]** 的子菜單。

**示例：排除發送地址清單**

以下示例允許您使用電子郵件地址清單從電子郵件傳遞目標中排除。

![](assets/s_advuser_list_read_sample_1.png)

包含在 **新建聯繫人** 資料夾必須由傳遞操作作為目標。 要從目標中排除的電子郵件地址儲存在外部清單中。 在我們的示例中，排除時只需要有關電子郵件地址的資訊。

1. 的 **新建聯繫人** 資料夾選擇查詢必須允許您載入所選配置檔案的電子郵件地址，以便能夠與清單中的資訊對齊。

   ![](assets/s_advuser_list_read_sample_0.png)

1. 此時，清單儲存在 **清單** 資料夾及其標籤將被計算。

   ![](assets/s_advuser_list_read_sample_2.png)

1. 要從主目標中排除外部清單的電子郵件地址，必須配置排除活動並指定 **新建聯繫人** 資料夾包含要保留的資料。 將從目標中刪除此集與來自排除活動的任何其他入站集之間的聯合資料。

   ![](assets/s_advuser_list_read_sample_3.png)

   排除規則在編輯工具的中心部分中配置。 按一下 **[!UICONTROL Add]** 按鈕來定義要應用的排除類型。

   您可以根據活動的傳入轉換數定義多個排除項。

1. 在 **[!UICONTROL Exclusion set]** ，選擇 **[!UICONTROL Read list]** 活動：此活動中的資料將從主集中排除。

   在我們的示例中，我們在連接上有一個排除：清單中包含的資料將通過包含電子郵件地址的欄位與主集的資料進行協調。 要配置聯接，請選擇 **[!UICONTROL Joins]** 的 **[!UICONTROL Change dimension]** 的子菜單。

   ![](assets/s_advuser_list_read_sample_4.png)

1. 然後，選擇與兩個集（源和目標）中的電子郵件地址對應的欄位。 然後，這些列將被連結，其電子郵件地址位於導入地址清單中的收件人將從目標中排除。
