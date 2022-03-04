---
product: campaign
title: 設計網站應用程式
description: 設計網站應用程式
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 4%

---

# 設計網站應用程式{#designing-a-web-application}

![](../../assets/common.svg)

Web應用程式是按照與 [Web表單](about-web-forms.md)。

>[!CAUTION]
>
>使用 **[!UICONTROL Preview]** 的子菜單。
>
>在發佈Web應用程式之前，不向最終用戶公開更改。

## 在Web應用程式中插入圖表 {#inserting-charts-in-a-web-application}

可以在Web應用程式中包括圖表。 為此，請使用任務欄中圖表的下拉清單選擇要插入的圖表類型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

也可以選擇 **[!UICONTROL Add a chart]** 的子菜單。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web應用程式中插入表 {#inserting-tables-in-a-web-application}

要添加表，請使用任務欄中表的下拉清單選擇要使用的表類型。

![](assets/s_ncs_admin_webapps_bar_table.png)

也可以在下拉菜單中選擇表的類型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述類型Web應用程式 {#overview-type-web-applications}

Adobe Campaign介面使用許多Web應用程式來訪問、管理和與收件人、遞送、市場活動、庫存等進行交互。

在介面中，它們以僅包含一頁的儀表板的形式顯示。

現成的Web應用程式儲存在 **[!UICONTROL Administration > Configuration > Web applications]** 的下界。

## 編輯表單類型Web應用程式 {#edit-forms-type-web-applications}

編輯外聯網的表單Web應用程式的特徵是：

* 預載箱

   在大多數情況下，必須預載要顯示的資料。 因為訪問這些表單的用戶是被識別的（通過訪問控制），所以預載入不一定是加密的。

* 保存框
* 添加頁面

   雖然「概述」類型的Web應用程式都有一個頁面，但編輯表單可以根據特定條件(test、選擇、連接運算子的配置檔案等)提供一系列頁面。

