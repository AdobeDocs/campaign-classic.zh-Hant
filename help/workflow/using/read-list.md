---
product: campaign
title: 讀取清單
description: 深入了解讀取清單工作流程活動
audience: workflow
content-type: reference
topic-tags: targeting-activities
exl-id: 99f82e91-45cd-4dff-b8a4-3ad87f2f9639
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# 讀取清單{#read-list}

在工作流程中處理的資料可來自清單，其中資料已預先準備或結構化（在先前的細分或檔案上傳後）。

**[!UICONTROL Read list]**&#x200B;活動可讓您從工作流程工作表中的清單複製資料，如從查詢複製資料。 接著，便可在整個工作流程中存取。

可根據&#x200B;**[!UICONTROL Read list]**&#x200B;活動中定義的選項和參數，顯式指定要處理的清單，由指令碼計算或動態本地化。

![](assets/list_edit_select_option_01.png)

如果未明確指定該清單，則必須提供要用作模板的清單以查找其結構。

![](assets/s_advuser_list_template_select.png)

配置清單選擇後，可以使用&#x200B;**[!UICONTROL Edit query]**&#x200B;選項添加篩選器，以保留下一個工作流的一部分母體。

![](assets/wf_readlist_1.png)

>[!CAUTION]
>
>若要在讀取清單活動中建立篩選器，相關清單必須是「檔案」類型。

清單可透過首頁的&#x200B;**[!UICONTROL Profiles and Targets > Lists]**&#x200B;連結直接在Adobe Campaign中建立。 您也可以使用&#x200B;**[!UICONTROL List update]**&#x200B;活動在工作流程中建立這些變數。

**範例：排除傳送位址清單**

下列範例可讓您使用要從電子郵件傳送目標中排除的電子郵件地址清單。

![](assets/s_advuser_list_read_sample_1.png)

**新聯繫人**&#x200B;資料夾中包含的配置檔案必須由傳送操作定位。 要從目標中排除的電子郵件地址會儲存在外部清單中。 在我們的範例中，排除項目只需要電子郵件地址的資訊。

1. **新聯繫人**&#x200B;資料夾選擇查詢必須使您能夠載入所選配置檔案的電子郵件地址，以便與清單中的資訊保持一致。

   ![](assets/s_advuser_list_read_sample_0.png)

1. 在此，清單儲存在&#x200B;**Lists**&#x200B;資料夾中，並計算其標籤。

   ![](assets/s_advuser_list_read_sample_2.png)

1. 若要從主要目標中排除外部清單的電子郵件地址，您必須設定排除活動並指定&#x200B;**New Contacts**&#x200B;資料夾包含要保留的資料。 此集與排除活動中任何其他入站集之間的聯合資料將從目標中刪除。

   ![](assets/s_advuser_list_read_sample_3.png)

   排除規則是在編輯工具的中央區段中設定。 按一下&#x200B;**[!UICONTROL Add]**&#x200B;按鈕以定義要套用的排除類型。

   您可以根據活動的傳入轉變數量來定義數個排除。

1. 在&#x200B;**[!UICONTROL Exclusion set]**&#x200B;欄位中，選取&#x200B;**[!UICONTROL Read list]**&#x200B;活動：將從主集中排除此活動中的資料。

   在我們的範例中，我們在連接上有一個排除：清單中包含的資料會透過包含電子郵件地址的欄位，與主要集的資料協調。 要配置聯接，請在&#x200B;**[!UICONTROL Change dimension]**&#x200B;欄位中選擇&#x200B;**[!UICONTROL Joins]**。

   ![](assets/s_advuser_list_read_sample_4.png)

1. 然後選取兩組（來源和目的地）中與電子郵件地址對應的欄位。 然後，會連結這些欄，而目標中將排除其電子郵件地址位於已匯入地址清單中的收件者。
