---
product: campaign
title: 定義網路表單版面
description: 定義網路表單版面
badge-v7: label="v7" type="Informative" tooltip="Applies to Campaign Classic v7"
badge-v8: label="v8" type="Positive" tooltip="Also applies to Campaign v8"
feature: Web Forms
exl-id: 23ca17f8-de1a-4f9c-8357-3965dc3329b1
source-git-commit: 6dc6aeb5adeb82d527b39a05ee70a9926205ea0b
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 2%

---

# 定義網路表單版面{#defining-web-forms-layout}



## 建立容器 {#creating-containers}

容器可讓您合併頁面的欄位並設定其版面；以組織頁面中的元素。

對於表單的每個頁面，容器都是透過以下方式建立： **[!UICONTROL Containers]** 工具列的「 」按鈕。

![](assets/s_ncs_admin_survey_containers_add.png)

使用容器將頁面的元素分組，而不需在最終轉譯中新增標籤。 元素會分組到容器子樹狀結構中。 標準容器可讓您管理版面。

例如：

![](assets/s_ncs_admin_survey_containers_std_arbo.png)

標籤的位置會套用至位於階層中容器下方的元素。 如有必要，可針對每個元素將其多載。 新增或移除欄以變更版面。 另請參閱 [定位頁面上的欄位](#positioning-the-fields-on-the-page).

在上述範例中，演算方式如下：

![](assets/s_ncs_admin_survey_containers_std_ex.png)

## 定位頁面上的欄位 {#positioning-the-fields-on-the-page}

Web表單的版面配置是在每個容器中逐頁定義，如有需要，可以多載。

頁面會劃分為欄：每個頁面都包含特定數量的欄。 頁面佔用的每個欄位 **n** 儲存格。 容器也會佔用特定數目的欄，而且容器包含的欄位會佔用特定數目的儲存格。

依預設，頁面會建置在單一欄上，而每個元素會佔用一個儲存格。 這表示欄位會一個顯示在另一個欄位下，每個欄位佔據一整行，如下所示：

![](assets/s_ncs_admin_survey_container_ex.png)

在下列範例中，已保留預設設定。 此頁面佔據一欄，其中包含四個容器。

![](assets/s_ncs_admin_survey_container_ex0.png)

每個容器佔用一欄，而每個元素佔用一個儲存格：

![](assets/s_ncs_admin_survey_container_ex0a.png)

演算方式如下：

![](assets/s_ncs_admin_survey_container_ex0_rend.png)

您可以調整顯示引數以獲得下列演算：

![](assets/s_ncs_admin_survey_container_ex1_rend.png)

在上述演算範例中，每個輸入欄位、標題和影像會佔用容器欄中的一個儲存格。

您可以修改每個容器中的格式。 在我們的範例中，您可以將容器4的內容分散到兩欄上並分散元素。

![](assets/s_ncs_admin_survey_container_ex2_rend.png)

標題和清單各佔一個儲存格（因此是容器的整行），而核取方塊會延伸至兩個儲存格。 歸因至輸入欄位的儲存格數會定義於 **[!UICONTROL General]** 標籤或 **[!UICONTROL Advanced]** 索引標籤中，根據欄位型別：

![](assets/s_ncs_admin_survey_container_ex2.png)

## 定義標籤位置 {#defining-the-position-of-labels}

您可以定義表單中欄位和標籤的對齊方式。

依預設，欄位和頁面其他內容的顯示引數繼承自表單的一般設定、頁面的設定或父容器的設定（如果存在）。

在表單屬性方塊中指定整個表單的全域顯示引數。 此 **[!UICONTROL Rendering]** 索引標籤可讓您選取標籤的位置。

![](assets/s_ncs_admin_survey_label_position.png)

您可以透過「 」，為每個頁面、每個容器和每個欄位多載此位置 **[!UICONTROL Advanced]** 標籤。

支援下列對齊：

* 繼承：對齊方式繼承自父元素（預設值），即父容器（如果有）或頁面。
* 左/右：標籤位於欄位的右側或左側，
* 上/下：標籤位於欄位上方或下方，
* 隱藏：不顯示標籤。
