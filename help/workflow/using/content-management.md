---
title: 內容管理
seo-title: 內容管理
description: 內容管理
seo-description: null
page-status-flag: never-activated
uuid: 8d1bf84b-96e5-4d3d-9d77-42d2027a74db
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: workflow
content-type: reference
topic-tags: action-activities
discoiquuid: 13b72aa1-de40-4548-835b-97e765e04e95
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: c10a0a11c6e9952aa47da1f7a15188c79c62508d

---


# 內容管理{#content-management}

「內 **容管理** 」活動可讓您建立和控制內容，並根據此內容產生檔案。 然後，此內容可透過「傳送」活動傳送。

>[!CAUTION]
>
>內容管理是選用的Adobe Campaign模組。 請檢查您的授權合約。

活動的屬性分為三個步驟：

* **內容選擇**:內容可以是先前建立的，也可以透過活動建立。
* **內容更新**:該任務可以修改內容的主題或導入所有XML內容。
* **動作**:可儲存或產生產生的內容。

   ![](assets/content_mgmt_edit.png)

   如需在Adobe Campaign中設定和使用內容管理的詳細資訊，請參閱本 [節](../../delivery/using/about-content-management.md)。

1. **內容**

   * **[!UICONTROL Specified in the transition]**

      此選項可讓您使用轉場中指定的內容，即啟動內容管理的事件必須包含變 **[!UICONTROL contentId]** 數。 此變數可由先前的內容管理或任何指令碼設定。

   * **[!UICONTROL Explicit]**

      此選項可讓您透過欄位選取已建立的 **[!UICONTROL Content]** 內容。 此欄位僅在選取選項 **[!UICONTROL Explicit]** 時顯示。

      ![](assets/content_mgmt_explicit.png)

   * **[!UICONTROL Calculated by a script]**

      內容識別碼由指令碼計算。 欄位 **[!UICONTROL Script]** 可讓您定義JavaScript範本，以評估內容的識別碼（主鍵）。 此欄位僅在選取選項 **[!UICONTROL Calculated by a script]** 時顯示。

      ![](assets/content_mgmt_script.png)

   * **[!UICONTROL New, created from a publication template]**

      從出版物範本建立新內容。 此新內容將儲存在欄位中指定的檔 **[!UICONTROL String]** 案中。 該 **[!UICONTROL Template]** 欄位指定要用於建立內容的發佈模板。

      ![](assets/content_mgmt_new.png)

1. **更新內容**

   * **[!UICONTROL Subject]**

      此欄位可讓您修改內容的主題。

   * **[!UICONTROL Access to data from an XML feed]**

      此選項可讓您從透過XSL樣式表下載的XML檔案建構內容。 選取此選項時，欄位會 **[!UICONTROL URL]** 指定XML內容下載URL。 可 **[!UICONTROL XSL stylesheet]** 以指定用於轉換已下載XML文檔的樣式表。 此屬性為可選屬性。

      ![](assets/content_mgmt_xmlcontent.png)

1. **執行動作**

   * **[!UICONTROL Save]**

      此選項會儲存已建立或修改的內容。

      對外轉場只會啟動一次，而內容會以參數 **[!UICONTROL contentId]** 的形式儲存在變數中。

   * **[!UICONTROL Generate]**

      此選項保存內容，然後為每個具有「檔案」類型發佈的轉換模板生成輸出檔案。

      ![](assets/content_mgmt_generate.png)

      對於以變數中儲存的內容識別碼作為參數和變數中的檔案名稱而產生的每 **[!UICONTROL contentId]** 個檔案，都會啟用出站轉 **[!UICONTROL filename]** 場。

## 輸入參數 {#input-parameters}

* contentId

啟用選項時要使用的內容 **[!UICONTROL Specified in the transition]** 識別碼。

## 輸出參數 {#output-parameters}

* contentId

   內容識別碼。

* 檔案名

   如果所選操作為，則生成檔案的完整名 **[!UICONTROL Generate]**&#x200B;稱。

## 範例 {#examples}

本節提供範例 [](../../delivery/using/automating-via-workflows.md#examples)。
