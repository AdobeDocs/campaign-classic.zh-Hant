---
product: campaign
title: 內容管理
description: 內容管理
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 2%

---

# 內容管理{#content-management}

**內容管理**&#x200B;活動可讓您建立和操控內容，並根據此內容產生檔案。 然後，此內容便可透過「傳送」活動傳送。

>[!CAUTION]
>
>內容管理是選用的Adobe Campaign模組。 請檢查您的授權合約。

活動的屬性分為三個步驟：

* **內容選取**:內容可以先前建立過，也可以透過活動建立。
* **內容更新**:該任務可以修改內容的主題或導入所有XML內容。
* **動作**:可儲存或產生產生的內容。

   ![](assets/content_mgmt_edit.png)

   如需在Adobe Campaign中設定和使用內容管理的詳細資訊，請參閱此[區段](../../delivery/using/about-content-management.md)。

1. **內容**

   * **[!UICONTROL Specified in the transition]**

      此選項可讓您使用轉變中指定的內容，亦即啟用內容管理的事件必須包含&#x200B;**[!UICONTROL contentId]**&#x200B;變數。 此變數可由先前的內容管理或任何指令碼設定。

   * **[!UICONTROL Explicit]**

      此選項可讓您透過&#x200B;**[!UICONTROL Content]**&#x200B;欄位選取已建立的內容。 只有在選取&#x200B;**[!UICONTROL Explicit]**&#x200B;選項時，此欄位才會顯示。

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      內容識別碼由指令碼計算。 **[!UICONTROL Script]**&#x200B;欄位可讓您定義評估內容識別碼（主要索引鍵）的JavaScript範本。 只有在選取&#x200B;**[!UICONTROL Calculated by a script]**&#x200B;選項時，此欄位才會顯示。

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      從發佈範本建立新內容。 此新內容將保存在&#x200B;**[!UICONTROL String]**&#x200B;欄位中指定的檔案中。 **[!UICONTROL Template]**&#x200B;欄位指定用於建立內容的發佈模板。

      ![](assets/content_mgmt_new.png)

1. **更新內容**

   * **[!UICONTROL Subject]**

      此欄位可讓您修改內容的主題。

   * **[!UICONTROL Access to data from an XML feed]**

      此選項允許從通過XSL樣式表下載的XML文檔構建內容。 選取此選項時，**[!UICONTROL URL]**&#x200B;欄位會指定下載URL的XML內容。 **[!UICONTROL XSL stylesheet]**&#x200B;允許您指定用於轉換下載的XML文檔的樣式表。 此屬性為選用。

      ![](assets/content_mgmt_xmlcontent.png)

1. **要執行的動作**

   * **[!UICONTROL Save]**

      此選項會儲存已建立或修改的內容。

      出站轉變只啟動一次，內容以&#x200B;**[!UICONTROL contentId]**&#x200B;變數中的參數形式儲存。

   * **[!UICONTROL Generate]**

      此選項保存內容，然後為每個轉換模板生成帶有「檔案」類型發佈的輸出檔案。

      ![](assets/content_mgmt_generate.png)

      系統會為每個產生的檔案啟動出站轉變，這些檔案的識別碼儲存在&#x200B;**[!UICONTROL contentId]**&#x200B;變數中，作為其參數，檔案名位於&#x200B;**[!UICONTROL filename]**&#x200B;變數中。

## 輸入參數{#input-parameters}

* contentId

啟用&#x200B;**[!UICONTROL Specified in the transition]**&#x200B;選項時要使用的內容識別碼。

## 輸出參數{#output-parameters}

* contentId

   內容識別碼。

* 檔案名

   如果所選操作為&#x200B;**[!UICONTROL Generate]**，則生成檔案的完整名稱。

## 範例 {#examples}

[section](../../delivery/using/automating-via-workflows.md#examples)中提供了示例。
