---
product: campaign
title: 使用Adobe Campaign瀏覽器
description: 瞭解如何使用市場活動瀏覽器
audience: platform
content-type: reference
topic-tags: starting-with-adobe-campaign
exl-id: f91d69a4-b794-40f0-b450-de862d7333e2
source-git-commit: fdb840a9e6349f074378899e07f794b62fb5b054
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 34%

---

# 使用Adobe Campaign瀏覽器 {#using-adobe-campaign-explorer}

![](../../assets/v7-only.svg)

可透過工具列圖示存取 Adobe Campaign 探索器。使用工具列圖示，您可以存取 Adobe Campaign、所有 Adobe Campaign 功能、設定畫面以及部分平台元素的更詳細視圖。

**[!UICONTROL Explorer]** 工作區分成三個區域：

![](assets/s_ncs_user_navigation.png)

**1 - 樹狀結構清單**：您可以個人化樹狀結構的內容 (新增、移動或刪除節點)。此程序僅適用於資深使用者。有關此內容的詳細資訊，請參閱  [此部分](#about-navigation-hierarchy)。)

**2 - 清單**：您可以篩選清單、執行搜尋、新增資訊或排序資料。[了解更多資訊](adobe-campaign-ui-lists.md)。

**3 - 詳情**：您可以顯示所選元素的詳細資訊。透過右上角的圖示，您可以全螢幕顯示這項資訊。

## 資料夾和導航樹{#about-navigation-hierarchy}

導航樹的工作方式與檔案瀏覽器（如Windows資源管理器）類似。 資料夾可能包含子資料夾。 選擇節點時，將顯示與該節點對應的視圖。

顯示的視圖是與方案關聯的清單和用於編輯選定行的輸入表單。

![](assets/d_ncs_integration_navigation.png)

要將新資料夾添加到樹中，請在要插入資料夾的分支中按一下右鍵該資料夾，然後選擇 **[!UICONTROL Add new folder]** 。 在快捷菜單中，選擇要建立的檔案類型。

![](assets/d_ncs_integration_navigation_create.png)

瞭解如何配置市場活動導航樹 [此部分](../../configuration/using/configuration.md)。

瞭解如何設定資料夾的權限 [此部分](access-management-folders.md)。

## 資料夾配置最佳實踐

* **使用內置資料夾**

   使用內置資料夾使未參與項目的人員更容易使用、維護和排除應用程式故障。 您不應為收件人、清單、交貨等建立自定義資料夾結構，而應使用標準資料夾，如「管理」、「配置檔案和目標」、「市場活動管理」。

* **建立子資料夾**

   將技術工作流置於標準資料夾下：管理/生產/技術工作流，並按工作流類型建立子目錄。

* **設定命名約定**

   例如，您可以按字母順序命名工作流，以便它們按執行順序顯示。

   例如：

   * A1 — 導入收件人，從10:00開始；
   * A2 — 導入票證，11:00開始。

* **為用戶建立模板以開始**

   建立特定於用戶的交貨模板、工作流模板、促銷活動模板。 此結構可以節省時間，並確保每個用戶都使用正確的傳遞映射和類型。

## 螢幕解析度 {#screen-resolution}

為了獲得最佳導覽和可用性，Adobe 建議最少使用像素 1600x900 的螢幕解析度。

>[!CAUTION]
>
>Adobe Campaign不支援1600x900像素以下的解析度。

在 **[!UICONTROL Explorer]** 工作區中，如果出現部分 **[!UICONTROL Details]** 區域被截斷，請透過區域頂端的箭頭加以展開或按一下 **[!UICONTROL Enlarge]** 按鈕。

![](assets/s_ncs_user_resolution.png)

## 瀏覽及自訂清單 {#browsing-lists}

瞭解如何瀏覽、管理和自定義清單 [此部分](adobe-campaign-ui-lists.md)。
