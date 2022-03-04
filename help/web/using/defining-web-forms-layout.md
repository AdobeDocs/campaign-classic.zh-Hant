---
product: campaign
title: 定義網路表單版面
description: 定義網路表單版面
feature: Web Forms
exl-id: 23ca17f8-de1a-4f9c-8357-3965dc3329b1
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# 定義網路表單版面{#defining-web-forms-layout}

![](../../assets/common.svg)

## 建立容器 {#creating-containers}

容器允許您組合頁面的欄位並配置其佈局；來組織頁面中的元素。

對於表單的每頁，通過 **[!UICONTROL Containers]** 按鈕

![](assets/s_ncs_admin_survey_containers_add.png)

使用容器對頁面的元素進行分組，而不向最終呈現添加標籤。 元素被分組到容器子樹中。 使用標準容器可以管理佈局。

例如：

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

標籤的位置將應用於層次中容器下方的元素。 如有必要，可以為每個元素重載。 添加或刪除列以更改佈局。 請參閱 [定位頁面上的欄位](#positioning-the-fields-on-the-page)。

在上例中，渲染如下所示：

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## 定位頁面上的欄位 {#positioning-the-fields-on-the-page}

Web表單的佈局是在每個容器中逐頁定義的，如果需要，可能會超載。

頁面分為以下列：每頁都包含一定數量的列。 頁面的每個欄位都佔用 **n** 的子菜單。 容器還佔用一定數量的列，而容器中包含的欄位佔用一定數量的單元格。

預設情況下，頁面是在單個列上構建的，每個元素佔用一個單元格。 這表示欄位在下方顯示，每個欄位佔據一行，如下所示：

![](assets/s_ncs_admin_survey_container_ex.png)

在以下示例中，已保留預設配置。 該頁佔用一列，該列包括四個容器。

![](assets/s_ncs_admin_survey_container_ex0.png)

每個容器佔一列，每個元素佔一個單元：

![](assets/s_ncs_admin_survey_container_ex0a.png)

渲染如下：

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

可以調整顯示參數以獲得以下渲染：

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

在上述渲染示例中，每個輸入欄位、標題和影像在容器的列中佔據一個單元。

可以修改每個容器中的格式。 在本例中，可以將容器4的內容分佈到兩列上並分佈元素。

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

標題和清單分別佔用一個單元格（因此佔用容器的整行），複選框延伸到兩個單元格上。 輸入欄位所屬的單元格數在 **[!UICONTROL General]** 頁籤 **[!UICONTROL Advanced]** 頁籤，根據欄位類型：

![](assets/s_ncs_admin_survey_container_ex2.png)

## 定義標籤的位置 {#defining-the-position-of-labels}

您可以定義表單中欄位和標籤的對齊方式。

預設情況下，欄位和頁面其他內容的顯示參數會從表單的常規配置、頁面的配置或父容器的配置中繼承（如果存在）。

整個窗體的全局顯示參數在窗體屬性框中指定。 的 **[!UICONTROL Rendering]** 頁籤中。

![](assets/s_ncs_admin_survey_label_position.png)

此位置可通過 **[!UICONTROL Advanced]** 頁籤。

支援以下對齊：

* 繼承：對齊方式是從父元素（預設值）繼承的，即父容器（如果有），或頁面。
* 左/右：標籤位於欄位的右側或左側，
* 上/下：標籤位於欄位的上方或下方，
* 隱藏：不顯示標籤。
