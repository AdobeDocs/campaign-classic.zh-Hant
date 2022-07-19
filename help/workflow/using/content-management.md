---
product: campaign
title: 內容管理
description: 內容管理
feature: Workflows, Data Management
exl-id: eb92a7c7-edfa-4062-b473-6d8b50d35e5f
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 3%

---

# 內容管理{#content-management}

![](../../assets/v7-only.svg)

A **內容管理** 活動，您可以建立和操作內容並基於此內容生成檔案。 然後，可以通過「交付」活動交付此內容。

>[!CAUTION]
>
>內容管理是可選的Adobe Campaign模組。 請檢查您的授權合約。

活動的屬性分為三個步驟：

* **內容選擇**:內容可以先前建立，也可以通過活動建立。
* **內容更新**:任務可以修改內容的主題或導入所有XML內容。
* **操作**:可以保存或生成生成的內容。

   ![](assets/content_mgmt_edit.png)

   有關在Adobe Campaign配置和使用內容管理的詳細資訊，請參閱此 [節](../../delivery/using/about-content-management.md)。

1. **內容**

   * **[!UICONTROL Specified in the transition]**

      此選項允許您使用在轉換中指定的內容，即激活內容管理的事件必須包含 **[!UICONTROL contentId]** 變數。 此變數可由先前的內容管理或任何指令碼設定。

   * **[!UICONTROL Explicit]**

      此選項允許您通過 **[!UICONTROL Content]** 的子菜單。 僅當 **[!UICONTROL Explicit]** 的雙曲餘切值。

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      內容標識符由指令碼計算。 的 **[!UICONTROL Script]** 欄位，用於定義評估內容標識符（主鍵）的JavaScript模板。 僅當 **[!UICONTROL Calculated by a script]** 的雙曲餘切值。

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      從發佈模板建立新內容。 此新內容將保存在 **[!UICONTROL String]** 的子菜單。 的 **[!UICONTROL Template]** 欄位指定用於建立內容的發佈模板。

      ![](assets/content_mgmt_new.png)

1. **更新內容**

   * **[!UICONTROL Subject]**

      此欄位允許您修改內容的主題。

   * **[!UICONTROL Access to data from an XML feed]**

      此選項允許從通過XSL樣式表下載的XML文檔構建內容。 選中此選項時， **[!UICONTROL URL]** 欄位指定下載URL的XML內容。 的 **[!UICONTROL XSL stylesheet]** 用於指定用於轉換下載的XML文檔的樣式表。 此屬性是可選的。

      ![](assets/content_mgmt_xmlcontent.png)

1. **要執行的操作**

   * **[!UICONTROL Save]**

      此選項保存建立或修改的內容。

      只激活一次出站轉換，內容保存在 **[!UICONTROL contentId]** 變數。

   * **[!UICONTROL Generate]**

      此選項保存內容，然後為每個轉換模板生成帶有「檔案」類型發佈的輸出檔案。

      ![](assets/content_mgmt_generate.png)

      對於使用保存在中的內容的標識符生成的每個檔案，激活出站轉換 **[!UICONTROL contentId]** 變數，以及 **[!UICONTROL filename]** 變數。

## 輸入參數 {#input-parameters}

* 內容ID

在 **[!UICONTROL Specified in the transition]** 選項。

## 輸出參數 {#output-parameters}

* 內容ID

   內容標識符。

* 檔案名

   如果所選操作為 **[!UICONTROL Generate]**。

## 範例 {#examples}

本中提供了示例 [節](../../delivery/using/automating-via-workflows.md#examples)。
