---
title: 定義Web表單版面
seo-title: 定義Web表單版面
description: 定義Web表單版面
seo-description: null
page-status-flag: never-activated
uuid: ae8659d0-3608-44dd-93ec-33c418a66ad0
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: web
content-type: reference
topic-tags: web-forms
discoiquuid: 67d1d39b-3a5f-4ed6-8fcf-570891043b10
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: 209ac4d81d2d27c264ee6b288bcb7fcb1900ffc5

---


# 定義Web表單版面{#defining-web-forms-layout}

## 建立容器 {#creating-containers}

容器可讓您結合頁面的欄位並設定其版面配置；來組織頁面中的元素。

對於表單的每個頁面，容器都會透過工具列 **[!UICONTROL Containers]** 的按鈕建立。

![](assets/s_ncs_admin_survey_containers_add.png)

使用容器將頁面元素分組，而不需將標籤新增至最終演算。 元素會分組到容器子樹中。 標準容器可讓您管理版面。

例如：

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

標籤的位置會套用至階層中容器下方的元素。 如有必要，可以對每個元素進行過載。 新增或移除欄以變更版面。 請參 [閱定位頁面上的欄位](#positioning-the-fields-on-the-page)。

在上述範例中，演算方式如下：

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## 定位頁面上的欄位 {#positioning-the-fields-on-the-page}

Web表單的版面配置是在每個容器中依頁面定義，而且每個檢查都會超載。

頁面會劃分為多欄：每個頁面都包含特定數目的欄。 頁面的每個欄位都佔有 **n個儲存格** 。 容器也佔用一定數目的欄，而容器所包含的欄位則佔用一定數目的儲存格

依預設，頁面是建置在單一欄上，而每個元素會佔用一個儲存格。 這表示欄位會一併顯示在另一個下方，每個欄位會佔據一行，如下所示：

![](assets/s_ncs_admin_survey_container_ex.png)

在下例中，保留了預設配置。 頁面會佔據一欄，其中包含4個容器。

![](assets/s_ncs_admin_survey_container_ex0.png)

每個容器佔用一欄，每個元素佔用一個儲存格：

![](assets/s_ncs_admin_survey_container_ex0a.png)

轉換如下：

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

您可以調整顯示參數，以獲得以下渲染：

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

在上述演算範例中，每個輸入欄位、標題和影像會佔據容器欄中的一個儲存格。

您可以修改每個容器中的格式。 在我們的範例中，您可以將容器4的內容分佈至兩欄，並分佈元素。

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

標題和清單各佔用一個儲存格（以及容器的整行），核取方塊延伸至兩個儲存格。 根據欄位類型，在標籤或標籤中定 **[!UICONTROL General]** 義屬於輸 **[!UICONTROL Advanced]** 入欄位的儲存格數：

![](assets/s_ncs_admin_survey_container_ex2.png)

## 定義標籤的位置 {#defining-the-position-of-labels}

您可以定義表單中欄位和標籤的對齊方式。

依預設，頁面的欄位和其他內容的顯示參數會繼承自表單的一般設定、頁面的設定或父容器的設定（如果存在）。

整個表單的全局顯示參數在表單屬性框中指定。 此標 **[!UICONTROL Rendering]** 簽可讓您選取標籤的位置。

![](assets/s_ncs_admin_survey_label_position.png)

此位置可透過標籤，為每個頁面、每個容器和每個欄位超載 **[!UICONTROL Advanced]** 。

支援下列對齊：

* 繼承：對齊方式繼承自父元素（預設值），即父容器（如果有），或頁面。
* 左／右：標籤位於欄位的右側或左側，
* 上／下：標籤位於欄位上方或下方，
* 隱藏：不顯示標籤。

