---
product: campaign
title: 設計網站應用程式
description: 設計網站應用程式
feature: Web Apps
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 0ad183ae68faf41ac0b14bb37639a4b1da9d8776
workflow-type: tm+mt
source-wordcount: '277'
ht-degree: 4%

---

# 設計網站應用程式{#designing-a-web-application}

![](../../assets/common.svg)

Web應用程式是根據與 [網路表單](about-web-forms.md).

>[!CAUTION]
>
>使用 **[!UICONTROL Preview]** 頁簽，以檢查web應用程式設計期間的錯誤。 請注意，用來預覽Web應用程式的設定檔測試必須位於包含 **[!UICONTROL Access rights]** 針對 **[!UICONTROL Web application agent]** 運算元。 </br>在發佈Web應用程式之前，不向最終用戶公開更改。

## 在Web應用程式中插入圖表 {#inserting-charts-in-a-web-application}

可以在Web應用程式中包括圖表。 要執行此操作，請使用任務欄中的圖表下拉清單選擇要插入的圖表類型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您也可以選取 **[!UICONTROL Add a chart]** 功能表。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web應用程式中插入表 {#inserting-tables-in-a-web-application}

要添加表，請使用任務欄中的表的下拉清單來選擇要使用的表的類型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您也可以在下拉式功能表中選取表格類型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述類型的Web應用程式 {#overview-type-web-applications}

Adobe Campaign介面使用許多網頁應用程式來存取、管理收件者、傳遞、行銷活動、股票等項目，並與之互動。

在介面中，控制面板只會顯示一個頁面。

現成可用的Web應用程式儲存在 **[!UICONTROL Administration > Configuration > Web applications]** 節點。

## 編輯表單類型Web應用程式 {#edit-forms-type-web-applications}

編輯外聯網的表單Web應用程式的特點是：

* 預載盒

   在大多數情況下，必須預先載入要顯示的資料。 因為會識別存取這些表單的使用者（透過存取控制），預先載入不一定會加密。

* 儲存方塊
* 新增頁面

   雖然「概述」類型的Web應用程式都有單頁，但編輯表單可以根據特定條件（測試、選擇、連接運算子的配置檔案等）提供一系列頁面。

