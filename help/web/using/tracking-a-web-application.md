---
product: campaign
title: 追蹤網站應用程式的瀏覽次數
description: 追蹤網站應用程式的瀏覽次數
feature: Web Apps
exl-id: 07bd36ce-c701-4998-974f-81fd4fac22a0
source-git-commit: b6f1556cf49492cefaf61c29a058584b0ccee16a
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 4%

---

# 追蹤網站應用程式的瀏覽次數{#tracking-a-web-application}

![](../../assets/common.svg)

Adobe Campaign允許您通過插入跟蹤標籤來跟蹤和測量Web應用程式頁面上的訪問。 此功能可用於所有Web應用程式類型（表單、Web頁等）。

因此，您可以定義多個導航路徑並評估其成功。 然後，恢復的資料可在每個應用程式的報告中找到。

本版本的主要改進如下：

* 可能在同一頁上插入多個跟蹤標籤，以便簡化導航路徑定義（例如購買、訂閱、返回等）。
* 在Web應用程式儀表板中查看不同頁面的導航路徑和跟蹤標籤。

   ![](assets/trackers_1.png)

* 正在生成完整跟蹤報告。

   ![](assets/trackers_5.png)

   主要指標如下：

   * **轉換率**:顯示導航路徑所有步驟的人員數。
   * **彈跳率**:僅顯示第一步的人數
   * **轉換漏斗**:每個步驟之間的丟失率。

   此外， **部門** 類型圖根據人口來源顯示人口。

## 標識通信源 {#identifying-the-traffic-source}

訪問Web應用程式時，可以使用兩種不同的模式來識別訪問者來自何處：

1. 發送特定傳遞以授予對Web應用程式頁的訪問權：在這種情況下，交通來源是這個交付，
1. 將Web應用程式與專用通信源關聯：在這種情況下，它必須是外部「通信源」類型的傳遞。 可以從Web應用程式屬性或目標映射中選擇它。

   ![](assets/trackers_6.png)

為了識別Web應用程式中的通信源，Adobe Campaign先後查找以下資訊：

1. 源傳遞標識符（如果存在）(nlId cookie),
1. 在Web應用程式屬性中定義的外部傳遞的標識符（如果存在）,
1. 目標映射中定義的外部傳遞的標識符（如果存在）。

>[!NOTE]
>
>僅當在安裝市場活動時在部署嚮導中激活了該選項時，匿名跟蹤才可用。

## 使用數字內容編輯器(DCE)設計的Web應用程式 {#web-applications-designed-with-digital-content-editor--dce-}

使用HTML內容編輯器建立Web應用程式時 —  **數字內容編輯器(DCE)**  — 從 **[!UICONTROL Properties]** 的子菜單。 有關數字內容編輯器(DCE)的詳細資訊，請參閱 [此部分](about-campaign-html-editor.md)。

![](assets/trackers_2.png)

使用Web介面時，必須從頁面屬性中插入跟蹤標籤。

![](assets/trackers_3.png)

的 **[!UICONTROL Display blocks]** 表徵圖，用於查看為頁面定義的跟蹤標籤數。

![](assets/trackers_4.png)
