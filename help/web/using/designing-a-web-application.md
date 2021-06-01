---
product: campaign
title: 設計 Web 應用程式
description: 設計 Web 應用程式
audience: web
content-type: reference
topic-tags: web-applications
exl-id: dcdf6afc-321e-4027-a350-fff6bbf22e71
source-git-commit: 98d646919fedc66ee9145522ad0c5f15b25dbf2e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 3%

---

# 設計網站應用程式{#designing-a-web-application}

根據與[線上調查](../../web/using/about-surveys.md)相同的原則建立和管理Web應用程式。

然而，功能差異如下：

* Web應用程式不使用已存檔的欄位。 因此，資料只能儲存在資料庫欄位或本機變數中。
* Web應用程式上沒有內建報告。
* 提供其他欄位，主要用於建立表格和圖表。

>[!CAUTION]
>
>強烈建議持續檢查套用的設定，以便在Web應用程式建構程式早期偵測任何錯誤。 要檢查修改的呈現，請保存應用程式，然後按一下&#x200B;**[!UICONTROL Preview]**&#x200B;子頁簽。
>
>在發佈Web應用程式之前，最終用戶無法看到更改。

## 在Web應用程式{#inserting-charts-in-a-web-application}中插入圖表

可以在Web應用程式中包括圖表。 要執行此操作，請使用任務欄中的圖表下拉清單選擇要插入的圖表類型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您也可以選取&#x200B;**[!UICONTROL Add a chart]**&#x200B;功能表。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web應用程式{#inserting-tables-in-a-web-application}中插入表

要添加表，請使用任務欄中的表的下拉清單來選擇要使用的表的類型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您也可以在下拉式功能表中選取表格類型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述類型Web應用程式{#overview-type-web-applications}

Adobe Campaign介面使用許多網頁應用程式來存取、管理收件者、傳遞、行銷活動、股票等項目，並與之互動。

在介面中，控制面板只會顯示一個頁面。

現成的Web應用程式儲存在&#x200B;**[!UICONTROL Administration > Configuration > Web applications]**&#x200B;節點中。

## 編輯表單類型Web應用程式{#edit-forms-type-web-applications}

編輯外聯網的表單Web應用程式的特點是：

* 預載盒

   在大多數情況下，必須預先載入要顯示的資料。 因為會識別存取這些表單的使用者（透過存取控制），預先載入不一定會加密。

* 儲存方塊
* 新增頁面

   雖然「概述」類型的Web應用程式都有單頁，但編輯表單可以根據特定條件（測試、選擇、連接運算子的配置檔案等）提供一系列頁面。

此類Web應用程式的操作與&#x200B;**調查**&#x200B;類似，但沒有歷史記錄管理或欄位存檔。 使用者通常透過登入頁面存取，且必須自行識別。
