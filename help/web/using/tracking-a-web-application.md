---
solution: Campaign Classic
product: campaign
title: 追蹤 Web 應用程式
description: 追蹤 Web 應用程式
audience: web
content-type: reference
topic-tags: web-applications
translation-type: tm+mt
source-git-commit: 11ff62238a8fb73658f2263c25dbeb27d2e0fb23
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# 追蹤Web應用程式上的瀏覽{#tracking-a-web-application}

Adobe Campaign可讓您透過插入追蹤標籤來追蹤和測量網頁上的瀏覽。 此功能可用於所有Web應用程式類型（表單、線上調查、使用DCE建立的Web頁等）。

因此，您可以定義數個導覽路徑並評估其成功。 然後，每個應用程式的報表中都會提供復原的資料。

本版本的主要改進如下：

* 可能在同一頁面上插入數個追蹤標籤，以簡化導覽路徑定義（例如購買、訂閱、退貨等）。
* 在Web應用程式控制面板中檢視不同頁面的導覽路徑和追蹤標籤。

   ![](assets/trackers_1.png)

* 產生完整追蹤報表。

   ![](assets/trackers_5.png)

   主要指標如下：

   * **轉換率**:顯示導航路徑所有步驟的人數。
   * **反彈率**:僅顯示第一步的人數
   * **轉換漏斗**:每個步驟之間的丟失率。

   此外，**扇區**&#x200B;類型圖表根據人口來源顯示人口。

## 識別流量來源{#identifying-the-traffic-source}

可使用兩種不同的模式來識別訪客在存取Web應用程式時的出處：

1. 傳送特定傳送以授與Web應用程式頁面的存取權：在這種情況下，流量來源是這個傳送，
1. 將Web應用程式與專用流量源關聯：在此情況下，它必須是外部「流量來源」類型的傳送。 它可從Web應用程式屬性或目標映射中選擇。

   ![](assets/trackers_6.png)

為了識別Web應用程式中的流量來源，Adobe Campaign先後尋找下列資訊：

1. 來源傳送識別碼（如果存在）(nlId Cookie),
1. 在Web應用程式屬性中定義的外部傳送識別碼（如果存在）,
1. 目標映射中定義的外部傳送的標識符（如果存在）。

>[!NOTE]
>
>請記住，只有在部署精靈中啟動了對應的選項時，才能進行匿名追蹤。
>
>有關詳細資訊，請參閱[《安裝指南》](../../installation/using/deploying-an-instance.md)。

## 使用數位內容編輯器(DCE){#web-applications-designed-with-digital-content-editor--dce-}設計的Web應用程式

使用HTML內容編輯器- **數位內容編輯器(DCE)**&#x200B;建立Web應用程式時，會從編輯器的&#x200B;**[!UICONTROL Properties]**&#x200B;頁籤插入跟蹤標籤。 有關數字內容編輯器(DCE)的詳細資訊，請參閱[本節](../../web/using/about-campaign-html-editor.md)。

![](assets/trackers_2.png)

使用Web介面時，必須從頁面屬性插入追蹤標籤。

![](assets/trackers_3.png)

**[!UICONTROL Display blocks]**&#x200B;圖示可讓您檢視為頁面定義的追蹤標籤數。

![](assets/trackers_4.png)

