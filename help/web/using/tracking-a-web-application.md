---
product: campaign
title: 追蹤 Web 應用程式
description: 追蹤 Web 應用程式
audience: web
content-type: reference
topic-tags: web-applications
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: 20509f44c5b8e0827a09f44dffdf2ec9d11652a1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---

# 追蹤網站應用程式的瀏覽次數{#tracking-a-web-application}

![](../../assets/common.svg)

Adobe Campaign可讓您透過插入追蹤標籤來追蹤和測量網頁上的造訪次數。 此功能可用於所有Web應用程式類型（表單、網頁等）。

因此，您可以定義數個導覽路徑並評估其成功。 然後，每個應用程式的報告中都會提供恢復的資料。

此版本主要的改善項目如下：

* 可在同一頁面上插入數個追蹤標籤，以便輕鬆定義導覽路徑（例如購買、訂閱、回訪等）。
* 檢視Web應用程式控制面板中不同頁面的導覽路徑和追蹤標籤。

   ![](assets/trackers_1.png)

* 產生完整追蹤報表。

   ![](assets/trackers_5.png)

   主要指標如下：

   * **轉換率**:顯示導航路徑的所有步驟的人數。
   * **反彈率**:僅顯示第一步的人數
   * **轉換漏斗**:每個步驟之間的丟失率。

   此外， **部門** 類型圖表會根據其來源顯示母體。

## 識別流量來源 {#identifying-the-traffic-source}

可使用兩種不同模式來識別訪客存取網頁應用程式時來自何處：

1. 傳送特定傳送以授與Web應用程式頁面的存取權：在此情況下，流量來源就是這個傳送，
1. 將Web應用程式與專用流量源關聯：在此情況下，它必須是外部「流量來源」類型的傳送。 可從Web應用程式屬性或目標映射中選擇它。

   ![](assets/trackers_6.png)

為了識別Web應用程式中的流量來源，Adobe Campaign會先後尋找下列資訊：

1. 來源傳送識別碼（如果存在）(nlId cookie),
1. 在Web應用程式屬性中定義的外部傳送的標識符（如果存在）,
1. 目標對應中定義的外部傳送識別碼（如果存在）。

>[!NOTE]
>
>只有在安裝Campaign時在部署精靈中啟動了選項時，才可使用匿名追蹤。

## 使用數字內容編輯器(DCE)設計的Web應用程式 {#web-applications-designed-with-digital-content-editor--dce-}

使用HTML內容編輯器建立Web應用程式時 —  **數位內容編輯器(DCE)**  — 從 **[!UICONTROL Properties]** 頁簽。 有關數字內容編輯器(DCE)的詳細資訊，請參閱 [本節](about-campaign-html-editor.md).

![](assets/trackers_2.png)

使用Web介面時，必須從頁面屬性插入追蹤標籤。

![](assets/trackers_3.png)

此 **[!UICONTROL Display blocks]** 圖示可讓您檢視為頁面定義的追蹤標籤數。

![](assets/trackers_4.png)
