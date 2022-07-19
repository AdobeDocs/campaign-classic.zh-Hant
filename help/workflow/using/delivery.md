---
product: campaign
title: 傳遞
description: 瞭解有關「交貨類型」工作流活動的詳細資訊
feature: Workflows, Channels Activity
exl-id: 72fbdd1d-a105-4e9f-9e17-2e9d62d2bb80
source-git-commit: 381538fac319dfa075cac3db2252a9cc80b31e0f
workflow-type: tm+mt
source-wordcount: '917'
ht-degree: 1%

---

# 傳遞{#delivery}

![](../../assets/v7-only.svg)

A **交貨**-type活動允許您建立交貨操作。 可使用輸入元素來建構。

要配置它，請編輯活動並輸入交貨選項。

![](assets/edit_diffusion.png)

1. **傳送**

   您可以：

   * 對入站轉換中指定的交貨執行操作。 為此，請選擇 **[!UICONTROL Delivery]** 的子菜單。

      當以前的工作流活動已建立或指定了交貨時，可以使用此選項。 可以通過生成出站轉移的同一類型的活動來完成此操作，如下例所示。

      在以下示例中，首次建立了交貨。 後面定義了人口和內容。 接下來，使用入站轉換將這三個要素的資訊重新輸入到新的傳遞活動中，以便發送該資訊。

      ![](assets/specified_transition_option_exemple.png)

   * 直接選擇相關的交貨。 要執行此操作，請選擇 **[!UICONTROL Explicit]** ，然後從 **[!UICONTROL Delivery]** 的子菜單。

      清單顯示包含在 **交貨** 資料夾。 要訪問其他市場活動，請按一下 **[!UICONTROL Select link]** 表徵圖

      ![](assets/diffusion_edit_1.png)

      從市場活動的下拉清單中選擇市場活動 **[!UICONTROL Folder]** 或按一下 **[!UICONTROL Display sub-levels]** 要顯示子資料夾中包含的所有交貨，請執行以下操作：

      ![](assets/diffusion_edit_2.png)

      選擇傳送操作後，可通過按一下 **[!UICONTROL Edit link]** 表徵圖

   * 建立用於計算傳遞的指令碼。 要執行此操作，請選擇 **[!UICONTROL Computed by a script]** 的子菜單。 通過按一下 **[!UICONTROL Edit...]** 的雙曲餘切值。 以下示例恢復交貨的標識符：

      ![](assets/diffusion_edit_3.png)

   * 建立新交貨。 要執行此操作，請選擇 **[!UICONTROL New, created from a template]** ，然後選擇交貨所基於的交貨模板。

      ![](assets/diffusion_edit_4.png)

      按一下 **[!UICONTROL Select link]** 表徵圖以瀏覽資料夾，然後按一下 **[!UICONTROL Edit link]** 表徵圖。

1. **收件者**

   收件人可以由入站事件指定，例如在檔案導入後指定，或在傳遞操作中指定。 它們也可以儲存在一個或多個檔案中。

   ![](assets/diffusion_edit_5.png)

1. **內容**

   消息的內容可以在傳遞或入站事件中定義。

   ![](assets/diffusion_edit_6.png)

1. **要執行的操作**

   您可以建立交付、準備、啟動、評估目標或發送證據。

   ![](assets/diffusion_edit_7.png)

   選擇要執行的操作類型：

   * **[!UICONTROL Save]**:此選項允許您建立交貨並保存。 它不會分析或傳遞它。
   * **[!UICONTROL Estimate the target]**:此選項允許您計算交付目標以評估其潛力（第一個分析階段）。 此操作等效於選擇 **[!UICONTROL Estimate the population to be targeted]** 按鈕 **[!UICONTROL Analyze]** 將交貨發送到主目標時，通過 **交貨**。
   * **[!UICONTROL Prepare]**:此選項允許您運行完整分析過程（目標計算和內容準備）。 未發送交貨。 此操作等效於選擇 **[!UICONTROL Deliver as soon as possible]** 按鈕 **[!UICONTROL Analyze]** 向主目標發送交貨時 **交貨**。
   * **[!UICONTROL Send a proof]**:此選項允許您發送交貨的證明。 此操作相當於按一下 **[!UICONTROL Send a proof]** 按鈕 **交貨**
   * **[!UICONTROL Prepare and start]**:此選項啟動完整分析過程（目標計算和內容準備）併發送交付。 此操作相當於按一下 **[!UICONTROL Deliver as soon as possible]**。 **[!UICONTROL Analyze]**, **[!UICONTROL Confirm delivery]** 選項向主目標發送傳遞時 **交貨**。

   的 **[!UICONTROL Act on a delivery]** 工作流中進一步使用的活動允許您啟動啟動交付所需的所有剩餘步驟（目標計算、內容準備和交付）。 有關此內容的詳細資訊，請參閱 [交貨控制](delivery-control.md)。

   還提供以下選項：

   * **[!UICONTROL Generate an outbound transition]**

      建立將在執行結束時激活的出站轉換。 您可以選擇是否檢索出站傳遞的目標。

   * **[!UICONTROL Do not recover target]**

      不恢復傳出傳遞操作的目標。

   * **[!UICONTROL Processing errors]**

      請參閱 [交貨控制](delivery-control.md)。
   的 **指令碼** 頁籤中，您可以修改交貨參數。

   ![](assets/edit_diffusion_fil_script.png)

## 示例：交付工作流 {#example--delivery-workflow}

建立新工作流並添加活動，如下圖所示：

![](assets/new-workflow-5.png)

開啟 **交貨** 定義屬性：

* 在 **[!UICONTROL Delivery]** 選擇 **[!UICONTROL New, created from a template]** 並選擇交貨模板。
* 在 **[!UICONTROL Recipients]** 選擇 **[!UICONTROL Specified in the delivery]**。
* 在 **[!UICONTROL Action to execute]** 部分，保留 **[!UICONTROL Prepare]** 的雙曲餘切值。

![](assets/new-workflow-param-delivery.png)

按一下 **[!UICONTROL OK]** 按鈕關閉屬性窗口。 您剛剛配置了一個活動，該活動包括基於將在其中指定目標的傳遞模板建立和準備新傳遞。

開啟 **批准** 定義屬性：

1. 在 **[!UICONTROL Assignment type]** 欄位中，選擇要在其中註冊的組。 如果使用「admin」帳戶連接，請選擇「管理」組。
1. 接下來，輸入標題並在消息正文中插入以下文本：

   ```
   Do you wish to approve delivery (<%= vars.recCount %> recipient(s))?
   ```

   此消息包含用JavaScript編寫的表達式： **[!UICONTROL vars.recCount]** 表示上一任務的傳遞所針對的收件人數。 有關JavaScript表達式的詳細資訊，請參閱 [JavaScript指令碼和模板](javascript-scripts-and-templates.md)。

   ![](assets/new-workflow-param-validation.png)

   「批准」任務的詳細資訊 [批准](approval.md)。

## 輸入參數 {#input-parameters}

交貨標識符(如果 **[!UICONTROL Specified in the transition]** 的子菜單。 **[!UICONTROL Delivery]** 的子菜單。

* 交貨ID
* 表名
* 架構

每個入站事件都必須指定由這些參數定義的目標。

>[!NOTE]
>
>僅當 **[!UICONTROL Specified by inbound event(s)]** 的子菜單。 **[!UICONTROL Recipients]** 的子菜單。

* 檔案名

   在 **[!UICONTROL File(s) specified by inbound event(s)]** 的子菜單。 **[!UICONTROL Recipients]** 的子菜單。

* 內容ID

   內容標識符(如果 **[!UICONTROL Specified by inbound events]** 的子菜單。 **[!UICONTROL Content]** 的子菜單。

## 輸出參數 {#output-parameters}

* 表名
* 架構
* 記錄計數

這組三個值標識由傳遞產生的目標。 **[!UICONTROL tableName]** 是保存目標標識符的表的名稱， **[!UICONTROL schema]** 是人口的模式（通常為nms:recipient）, **[!UICONTROL recCount]** 是表中的元素數。

與補碼相關聯的過渡具有相同的參數。

>[!NOTE]
>
>在 **[!UICONTROL Do not recover target]** 的雙曲餘切值。
