---
solution: Campaign Classic
product: campaign
title: 設計 Web 應用程式
description: 設計 Web 應用程式
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 2%

---


# 設計Web應用程式{#designing-a-web-application}

Web應用程式是根據與[線上調查](../../web/using/about-surveys.md)相同的原則建立和管理。

但功能差異如下：

* Web應用程式不使用已封存的欄位。 因此，資料只能儲存在資料庫欄位或本機變數中。
* Web應用程式上沒有內建報表。
* 另外還提供其他欄位，主要用於建立表格和圖表。

>[!CAUTION]
>
>強烈建議您持續檢查套用的組態，以便在Web應用程式建構程式早期偵測任何錯誤。 要檢查修改的呈現，請保存應用程式，然後按一下&#x200B;**[!UICONTROL Preview]**&#x200B;子頁籤。
>
>在發佈Web應用程式之前，使用者無法看到這些變更。

## 在Web應用程式{#inserting-charts-in-a-web-application}中插入圖表

您可以在Web應用程式中加入圖表。 要執行此操作，請使用任務欄中的圖表下拉清單選擇要插入的圖表類型。

![](assets/s_ncs_admin_webapps_bar_graph.png)

您也可以選取&#x200B;**[!UICONTROL Add a chart]**&#x200B;功能表。

![](assets/s_ncs_admin_webapps_graph.png)

## 在Web應用程式{#inserting-tables-in-a-web-application}中插入表

要添加表，請使用任務欄中表的下拉清單選擇要使用的表類型。

![](assets/s_ncs_admin_webapps_bar_table.png)

您也可以在下拉式選單中選取表格類型。

![](assets/s_ncs_admin_webapps_table.png)

## 概述類型的Web應用程式{#overview-type-web-applications}

Adobe Campaign介面使用許多Web應用程式來存取、管理並與收件者、傳送、促銷活動、股票等互動。

在介面中，只有一個頁面的控制面板就會顯示它們。

現成可用的Web應用程式儲存在&#x200B;**[!UICONTROL Administration > Configuration > Web applications]**&#x200B;節點中。

## 編輯表單類型的Web應用程式{#edit-forms-type-web-applications}

為外部網編輯表單Web應用程式的特點：

* 預載箱

   在大多數情況下，必須預先載入要顯示的資料。 由於存取這些表單的使用者是經過識別的（透過存取控制），因此預載不一定會加密。

* 儲存方塊
* 新增頁面

   雖然「概述」類型的Web應用程式都有單一頁面，但編輯表單可以根據特定條件（測試、選擇、連線運算子的設定檔等）提供一系列的頁面。

此類型Web應用程式的運作類似於&#x200B;**Surveys**，但沒有歷史管理或欄位封存。 使用者通常透過登入頁面加以存取，在登入頁面中必須自行識別。
