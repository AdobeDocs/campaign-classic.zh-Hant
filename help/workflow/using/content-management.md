---
product: campaign
title: 內容管理
description: 內容管理
audience: workflow
content-type: reference
topic-tags: action-activities
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 2%

---

# 內容管理{#content-management}

![](../../assets/common.svg)

A **內容管理** 活動可讓您建立和操控內容，以及根據此內容產生檔案。 然後，此內容便可透過「傳送」活動傳送。

>[!CAUTION]
>
>內容管理是選用的Adobe Campaign模組。 請檢查您的授權合約。

活動的屬性分為三個步驟：

* **內容選取**:內容可以先前建立過，也可以透過活動建立。
* **內容更新**:該任務可以修改內容的主題或導入所有XML內容。
* **動作**:可儲存或產生產生的內容。

   ![](assets/content_mgmt_edit.png)

   如需在Adobe Campaign中設定及使用內容管理的詳細資訊，請參閱 [節](../../delivery/using/about-content-management.md).

1. **內容**

   * **[!UICONTROL Specified in the transition]**

      此選項可讓您使用轉變中指定的內容，亦即啟用內容管理的事件必須包含 **[!UICONTROL contentId]** 變數。 此變數可由先前的內容管理或任何指令碼設定。

   * **[!UICONTROL Explicit]**

      此選項可讓您透過 **[!UICONTROL Content]** 欄位。 只有在 **[!UICONTROL Explicit]** 選項。

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      內容識別碼由指令碼計算。 此 **[!UICONTROL Script]** 欄位可讓您定義評估內容識別碼（主索引鍵）的JavaScript範本。 只有在 **[!UICONTROL Calculated by a script]** 選項。

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      從發佈範本建立新內容。 此新內容將儲存在 **[!UICONTROL String]** 欄位。 此 **[!UICONTROL Template]** 欄位會指定用來建立內容的發佈範本。

      ![](assets/content_mgmt_new.png)

1. **更新內容**

   * **[!UICONTROL Subject]**

      此欄位可讓您修改內容的主題。

   * **[!UICONTROL Access to data from an XML feed]**

      此選項允許從通過XSL樣式表下載的XML文檔構建內容。 選取此選項時， **[!UICONTROL URL]** 欄位指定XML內容下載URL。 此 **[!UICONTROL XSL stylesheet]** 可指定用於轉換下載的XML文檔的樣式表。 此屬性為選用。

      ![](assets/content_mgmt_xmlcontent.png)

1. **要執行的動作**

   * **[!UICONTROL Save]**

      此選項會儲存已建立或修改的內容。

      出站轉變只會啟動一次，而內容會儲存在 **[!UICONTROL contentId]** 變數。

   * **[!UICONTROL Generate]**

      此選項保存內容，然後為每個轉換模板生成帶有「檔案」類型發佈的輸出檔案。

      ![](assets/content_mgmt_generate.png)

      會針對以儲存於 **[!UICONTROL contentId]** 變數作為其參數，且檔案名稱位於 **[!UICONTROL filename]** 變數。

## 輸入參數 {#input-parameters}

* contentId

要使用的內容識別碼(若 **[!UICONTROL Specified in the transition]** 選項。

## 輸出參數 {#output-parameters}

* contentId

   內容識別碼。

* 檔案名

   如果所選操作為，則生成檔案的完整名稱 **[!UICONTROL Generate]**.

## 範例 {#examples}

本文提供範例 [節](../../delivery/using/automating-via-workflows.md#examples).
